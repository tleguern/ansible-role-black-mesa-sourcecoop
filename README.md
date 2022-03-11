# Ansible Role: Black Mesa SourceCoop

[![builds.sr.ht status](https://builds.sr.ht/~tleguern/ansible-role-black-mesa-sourcecoop.svg)](https://builds.sr.ht/~tleguern/ansible-role-black-mesa-sourcecoop?)

An Ansible role that installs and upgrades the SourceCoop plugin for Black Mesa.

There is no automatic testing for this role as because a Black Mesa dedicated server is roughly 27Go of data and exceed the capacity of SourceHut's build servers.

For more information about SourceCoop please take a look at the [official repository](https://github.com/ampreeT/SourceCoop).

## Requirements

An ansible role dedicated to the installation of SteamCMD such as [tleguern.steamcmd](https://github.com/tleguern/ansible-steamcmd) or any role providing the `steamcmd_user` variable.

An ansible role dedicated to the Installation of Metamod:Source such as [tleguern.metamod_source](https://github.com/tleguern/ansible-role-metamod-source).

An ansible role dedicated to the Installation of Sourcemod such as [tleguern.sourcemod](https://github.com/tleguern/ansible-role-sourcemod).

An ansible role dedicated to the installation of Black Mesa such as [tleguern.black_mesa](https://github.com/tleguern/ansible-role-black-mesa) or any role providing the `Restart black-mesa` handler.

## Role Variables

Variables inherited from other roles:

| Variable        | Description            | Suggestion |
|-----------------|------------------------|------------|
| `steamcmd_user` | User name for steamcmd | `steam`    |

Native variables:

| Variable                  | Description            | Default |
|---------------------------|------------------------|---------|
| `sourcecoop_url`          | Download mirror        | `https://github.com/ampreeT/SourceCoop/releases/download/v{{ sourcecoop_version }}/sourcecoop-{{ sourcecoop_version }}.zip` |
| `sourcecoop_version`      | Desired version        | `1.0.4` |
| `sourcecoop_target`       | Archive name           | `sourcecoop-{{ sourcecoop_version }}.zip` |
| `sourcecoop_install_path` | Installation directory | `/home/{{ steamcmd_user }}/black-mesa/bms` |

## Dependencies

None.

## Example Playbook

```yaml
- hosts: game
  pre_tasks:
    - package:
        name: acl
        state: present
  roles:
    - role: tleguern.steamcmd
    - role: tleguern.black_mesa
    - role: tleguern.metamod_source
    - role: tleguern.sourcemod
    - role: tleguern.black_mesa_sourcecoop
```

## License

ISC

## Contributing

Either send [send GitHub pull requests](https://github.com/tleguern/ansible-role-black-mesa-sourcecoop) or [send patches on SourceHut](https://lists.sr.ht/~tleguern/misc).

## Author Information

Tristan Le Guern <tleguern@bouledef.eu>
