| This module will no longer receive updates. |
|---------------------------------------------|
| ⚠️ As of Puppet 7.27 and 8.3, the built in `puppet ssl` command now supports bootstrapping an offline agent. Instead of this module, you should use `puppet ssl generate_request`. |




Puppet Agent Bootstrap
=======

This is a Puppet App that provides the `puppet bootstrap` command used to generate and validate a Puppet Agent's certificate signing request that isn't being sent directly to a Puppet Server Certificate Authority. And example use case for this would be for generating a CSR that would be submitted to a service that can communicate with the CA and then validating the signed request when it was returned before proceeding with the rest of the agent configuration.

> This module is maintained by Puppet and used by our OpsWorks integration, but we have no plans for future feature development. We will keep it working with current versions of Puppet, but new feature development will come from community contributions. It does not qualify for Puppet Support plans.
>
> [tier:maintenance-mode]

## Commands

`puppet bootstrap purge`

Deletes the agent's certificate, csr, and the Puppet Servers CA. A more graceful version of rm -rf /etc/puppetlabs/puppet/ssl/*.

Useful to run as even with a lockfile present, the Puppet Daemon may attempt to generate a CSR before you want it to.

`puppet bootstrap csr`

Performs the CSR generation function and returns the fingerprint and name of the CSR. What this app was written to perform.

`puppet bootstrap verify`

Validates that the returned certificate and private key work together, and can connect successfully to the Puppet Server. This is saner step towards validating one has the right certificate before unlocking the agent and performing a full Puppet run.

## Limitations
This is working in the SSL handling components of the Puppet system and behavior could change in the future. This module should go away once above features are added to core Puppet.

## Contributors
Original Author: [Adrien Thebo](https://github.com/adrienthebo/)

Maintainers: Puppet

