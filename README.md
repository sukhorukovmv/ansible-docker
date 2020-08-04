#### Edition

Do you want to use "ce" (community edition) or "ee" (enterprise edition)?

```yml
docker__edition: "ce"
```

#### Channel

Do you want to use the "stable", "edge", "testing" or "nightly" channels? You
can add more than one (order matters).

```yml
docker__channel: ["stable"]
```

#### Version

- When set to "", the current latest version of Docker will be installed
- When set to a specific version, that version of Docker will be installed and pinned

```yml
docker__version: ""

# For example, pin it to 18.06.
docker__version: "18.06"

# For example, pin it to a more precise version of 18.06.
docker__version: "18.06.1"
```

*Pins are set with `*` at the end of the package version so you will end up
getting minor and security patches unless you pin an exact version.*

##### Upgrade strategy

- When set to `"present"`, running this role in the future won't install newer
versions (if available)
- When set to `"latest"`, running this role in the future will install newer
versions (if available)

```yml
docker__state: "present"
```

### Installing Docker Compose

Docker Compose will get PIP installed inside of a Virtualenv. This is covered
in detail in another section of this README file.

#### Version

- When set to "", the current latest version of Docker Compose will be installed
- When set to a specific version, that version of Docker Compose will be installed
and pinned

```yml
docker__compose_version: ""

# For example, pin it to 1.23.
docker__compose_version: "1.23"

# For example, pin it to a more precise version of 1.23.
docker__compose_version: "1.23.2"
```

### Configuring users to run Docker without root

A list of users to be added to the `docker` group.

Keep in mind this user needs to already exist, this role will not create it. 

```yml
# Try to use the sudo user by default, but fall back to root.
docker__users: ["{{ ansible_env.SUDO_USER | d('root') }}"]

# For example, if the user you want to set is different than the sudo user.
docker__users: ["admin"]
```

