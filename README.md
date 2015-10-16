# ansible-munin
An ansible role to configure a munin server. There are a number of role variables available, check `defaults/main.yml`
for the complete list, but here's the important stuff:

  * **munin_replace_default_vhost** (default yes) is a boolean variable that, if set to false, will not touch the default nginx and just make `/etc/nginx/munin.conf`, which you should include in your vhost
  * **munin_nodes_group** is the name of the group of all your munin nodes. It'll loop through all of them and put them in `munin.conf`. If unset it won't be used.
  * **munin_extra_hosts** is a list of other hosts that munin should poll. It should contain a list of dicts, with the key being the name of the host, and the value being another dict which has the key/value pairs that would go in the munin config. There's an example below.
  
```
  munin_extra_hosts:
    ap-1:
      address: 127.0.0.1
      use_node_name: "no"
```

results in:

```
[ap-1]
  address 127.0.0.1
  use_node_name no
```
