# Ansible Role tests

All credit goes to [@geerlingguy] for his amazing work with Ansible.

To run the test playbook(s) in this directory:

1. Install and start Docker.
1. Download the test shim into `tests/test.sh`:
    - `wget -O tests/test.sh https://gist.githubusercontent.com/noplanman/40e96f31ee2301469769d4236aff40e2/raw/`
1. Make the test shim executable:
    - `chmod +x tests/test.sh`.
1. Run (from the role root directory)
    - `distro=[distro] tests/test.sh` or
    - `distro=[distro] cleanup=false tests/test.sh` to keep container

[@geerlingguy]: https://www.jeffgeerling.com/ "Jeff Geerling"
