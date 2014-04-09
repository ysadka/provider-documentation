Mongo
=====

Mongo is an add-on for providing quick access to a Modulus hosted MongoDB
database in your project.

Administrative tools, user management, and data export is available directly
through the Modulus Web Portal. All data stored in our Mongo databases is saved
in triplicate and backed up offsite to maximize reliability and durability.

## Provisioning the add-on

Mongo can be configured for a Modulus application via the
[Modulus CLI](https://modulus.io/codex/cli/using_the_cli):

    $ modulus addons add mongo:base

Or from the [web interface](https://addons.modulus.io/mongo).

_Note that the Mongo add-on [billing](https://modulus.io/pricing) works the same
as the standard Modulus hosted MongoDB solution._

Once Mongo has been provisioned, the `MONGO_URL` environment variable will be
available in the project environment and will contain the credentials used to
access the newly provisioned MongoDB instance. This can be confirmed using the
`modulus addons list` command.

After installing the add-on, the application will be configured to fully
integrate with MongoDB.

## Using the database

You may use any MongoDB driver with the Mongo add-on. We suggest
[mongoose](http://mongoosejs.com).

```js
var mongoose = require('mongoose');

// Connect to your database using the MONGO_URL environment variable.
mongoose.connect(process.env.MONGO_URL);

var Cat = mongoose.model('Cat', { name: String });

var kitty = new Cat({ name: 'Zildjian' });

kitty.save(function (err) {
  if (err) // ...
  console.log('meow');
});
```

The Mongo add-on also works with [Meteor](https://www.meteor.com) projects
hosted on Modulus.

## Dashboard

Modulus MongoDB has a rich metrics dashboard full of amazing stats and useful
information.

![Dashboard](http://blog.modulus.io/img/posts/introducing-mongodb-stats/dashboard.png)

The dashboard is accessible from your project dashboard. Click on the Add-Ons
menu item to see all provisioned add-ons for your project and click on the
add-on name.

## Removing the add-on

Mongo can be removed from the add-ons section of your project dashboard.

## Support

[Contact](https://modulus.io/contact) Modulus directly for support related to
your provisioned Mongo add-on.

## Additional Resources
