# git2consul 

Forked from https://github.com/Cimpress-MCP/git2consul, see there for full docs and details.

Our config file lives in the root, its called `config.json`.

## First time setup of a Consul cluster
 
To setup git2consul, run this once: `node utils/config_seeder.js --endpoint consul.mbst.tv --port 8500 config.json`

That stores the contents of config.json in Consul under the key /git2consul/config


## Standard operation 
From that point on `node . --endpoint consul.mbst.tv --port 8500 -n` should be run perodically or when changes are detected in the infra repo.

`-n` means no-daemonize, this project _can_ track the infra repo and update Consul itself.

Preferably though, CI is in charge of deciding when to execute git2consul. This is because git2consul's resiliency and quality of change tracking is unknown, CI's is not.