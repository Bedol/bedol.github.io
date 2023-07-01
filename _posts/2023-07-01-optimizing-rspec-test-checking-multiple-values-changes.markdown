---
layout: post
title: "Optimizing Tests with RSpec: Efficiently Checking Multiple Value Changes"
date: 2023-07-01 23:02:01 +0200
categories: rspec rails ruby test matchers
---

For many years, as a Ruby developer, I have been using RSpec to write tests for Ruby applications.
I often relied on the popular [RSpec change matcher](https://rspec.info/features/3-12/rspec-expectations/built-in-matchers/change/) to verify if a specific value in an object had changed.
However, recently I learned a new approach to its usage. But let's start from the beginning.

Many people check if a value has changed using the following approach:

```ruby
let(:user) { create(:user, first_name: "John") }

it "changes a user's first name" do
  user.update!(first_name: "Bob")

  expect(user.first_name).to eq("Bob")
end
```

To check whether a value has been modified in an object, we can utilize the [RSpec change matcher](https://rspec.info/features/3-12/rspec-expectations/built-in-matchers/change/).

```ruby
let(:user) { create(:user, first_name: "John") }

it "changes a user's first name" do
  expect { user.update!(first_name: "Bob") }
    .to change { user.reload.first_name }
    .from("John")
    .to("Bob")
end
```

With this change, we can be certain that the object has changed its value from the initial state to the desired one.

But what if the object has multiple changed values? In such cases, I used to write separate tests to verify each value.

```ruby
subject(:update_user) { user.update!(first_name: "Bob", last_name: "Doe") }

let(:user) { create(:user, first_name: "John", last_name: "Smith") }

it "changes a user's first name" do
  expect { update_user }
    .to change { user.reload.first_name }
    .from("John")
    .to("Bob")
end

it "changes a user's last name" do
  expect { update_user }
    .to change { user.reload.last_name }
    .from("Smith")
    .to("Doe")
end
```

One could argue that each test should focus on one thing. However, when we need to check multiple values within a single object (indicating a more complex service or action), we would end up writing a substantial amount of code to verify all those values.

Recently, I learned a clever trick that allows us to check multiple values within a single test (using a single expect statement).

```ruby
subject(:update_user) { user.update!(first_name: "Bob", last_name: "Doe") }

let(:user) { create(:user, first_name: "John", last_name: "Smith") }

it "changes a user's first name and last name" do
  expect { update_user }
    .to change { user.reload.first_name }.from("John").to("Bob")
    .and change { user.reload.last_name }.from("Smith").to("Doe")
end
```

As you can see, we are now able to verify multiple values for a single action (in this case, a simple data update using ActiveRecord).

There is no limitation to checking values in other objects within the same test if the service/action modifies multiple objects.

I hope you find this trick useful.
