
## Playbook to deploy my personal website
https://joshtdun.com
https://github.com/joshtdun/joshtdun.com2.0

This is a playbook to deploy a django based blog running on debian served by nginx, proxy gunicorn,
backing database postgresql on DigitalOcean.

While this is made specifically for my site I tried to keep it as adaptable as possible.

run `ansible-playbook create-droplet-role.yml` then
`ansible-playbook jostdun-with-roles.yml`

### Somethings to Note
* I kept the droplet creation in a separate playbook (just a personal preference).

* This requires a DigitalOcean API key to create the droplet you can export it as an environmental .

* If roles require any extra information I have mentioned in the comments at the top of their respective
`tasks/main.yml`.  I would recommend that you read through those to get a general idea of what this does or what you will need to provide.

* You will have to manually setup an ssl certificate if you deploy this and require one.

* This allows passwordless sudo access you might want to change that depending on you security needs.

* The following are config values in ansible.cfg that I use
 
  * define the user (line 111) 
  * the ssh key (line 140) 
    * they have been commented out 
for the upload to this repo (default behavior) but it's how I run it myself.

  * inventory is the inventory in the root of this repo

  * line 32
allow_world_readable_tmpfiles = yes
     * This had to be done for sudo -u postgres psql in the postgres role

This is my first Ansible playbook so any feedback would be greatly appreciated you can shoot me an email at josh@joshtdun.com
