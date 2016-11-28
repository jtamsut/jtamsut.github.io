# Action Controller

# Active Record

     ActiveRecord::Base
             |
     ApplicationRecord



     ActionController
           |
  ApplicationController

Models contain business logic

Bussiness logic is the real-world rules that determines how data can be manipulated. It is entirely determined by 
the real-world application of the application.

Views take care of how the applcation will be presented

### Controllers

The naming convention for controllers is to pluralize the last word of the controller name.

For a controller that corresponds to a user resoure we would name this `UsersController`.

Following this convention will allow you to follow default route generator conventions.

A Rails controller is a Ruby Class the inherits from ApplicationController

class UsersController < ApplicationController
  def action
  end
end

ApplicationController inherits from ActionController::Base
```
ActionController::Base
         |
         v
ApplicationController
         |
         v
   Your Controller
 ```  

 Every time a controller is hit a new instance of that controller is created (this is what's happening in Ruby

 only public methods are callable as actions

 Rails does not make any distinctio between query string parameters and POST data
  1. query string parameters: data after the "?" in a URL
  2. POST data: data sent from a form

the params has

```
params

