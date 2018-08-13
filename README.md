### donation_form
A Drupal 8 module for accepting donations; leverages Stripe for payment processing.
___

# User Instructions
## Installation:
* Clone repo into local dev environment or server
* Run 'composer install --ignore-platform-reqs' to install dependencies
* Copy default.settings.php as settings.php and edit as appropriate
* Enable the donation_form module and answer yes to installing dependencies
___
# Development Documentation
## Requirements

    
#### Installation requirements: 

The donation form should ideally work with two installation steps: 1) installing Drupal (including composer install) 2) enabling one custom module containing your configuration and custom code.
1. Stripe PHP library is a requirement make sure that the installation is easy and documented in User Instructions
**Discussion:**  I'm not initially sure what the best approach to this requirement is.  I believe that the approach used by stripe_checkout is what's envisioned as it calls for running 'composer install' in the module root before enabling.
Need to make sure I link those requirements into my module.
2. Include config within the module so everything's ready to go when module is enabled
3. Make sure Drupal module dependencies are also documented.

##### Selected approaches
1. I think I misinterpreted this first requirement.  I was picturing my repo being a standalone module that could use it's own composer.json file to install dependencies.  I tried this but I can't get it to work.  It could work if this module were installed with 'composer require' but I'm not sure how it would be done for a custom module.  Rereading the requirements statement, I'm not thinking that the repos should be an entire basic D8 site with the custom module's requirements declared in composer.json.
2. Move pertinent config files into modules/custom/donation_form/config/install
3. Document Drupal dependencies in donation_form.info.yml
#### Use requirements:

Need to collect who is making the donation, how much it’s for and of course collect the credit card payment.
1. Drupal will collect this user identity and donation ammount in addition to integrating with Stripe to process payment.

**It would be nice to also**: 
2. Allow the user to select from a list of donation amounts or enter a custom value.
3. Track the status of the transaction from Stripe in Drupal with a record of the donation.  A view might also be nice
4. Realtime validation of inputs.
But I simply ran out of time.

### Module selection
  There are a number of Stripe module for Drupal, I want to pick one that is stable, suits this use case well, and can be implemented fairly quickly.

  This is my first time working with Atripe so my initial thought was 'hey look, theres a D8 contrib module called Stripe'.  It's not covered by Drupal’s security advisory policy though, which I'm not too comfortable with especially for handling users' credit card info.

  I then found this comparison chart https://drupalintegration.com/app/stripe which layed out the (somewhat limited) choices for D8.  stripe_checkout and commerce_stripe stood out as promising options.  They are both in beta and commerce_stripe has the edge in D8 installs.  commerce_stripe extends the commerce module, though, which doesn't feel like a great fit for this fairly straightforward use case.  stripe_checkout provides a special field type for submitting payments to Stripe that can be added to entities - seems simple and flexible.  


___