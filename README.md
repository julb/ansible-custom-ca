# custom-ca

This role enables to install custom CA certificates on a system.

## Requirements

No requirements.

## Role Variables

| Name                  | Type   | Location            | Description                                                                                                                                               |
| --------------------- | ------ | ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| custom_cas            | cas[]  | `defaults/main.yml` | The custom CA configurations to install on the machine. Defaults to `[]`.                                                                                 |
| custom_ca_file_prefix | string | `defaults/vars.yml` | A file name prefix to add to each created `crt` file. The prefix is also used to detect CA to remove from the filesystem. Defaults to `mngd-by-ansible-`. |

The `cas` type is a dictionary with one of the following attributes:

- `url`: a remote URL to download and install on the machine
- `inline_content`: a x509 base64 inline content to install on a machine.

Example:

```yaml
custom_cas:
  - url: https://some-host/ca.crt
  - inline_content: |
      -----BEGIN CERTIFICATE-----
      [.....]
      -----END CERTIFICATE-----
```

## Dependencies

No dependencies.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- hosts: servers
  roles:
    - { role: julb.custom_ca }
```

## License

MIT

## Author Information

More to find on my [Github](https://github.com/julb).

## Contributing

This project is totally open source and contributors are welcome.

When you submit a PR, please ensure that the syntax has been checked.
