# playbooks

Ansible playbooks for MUON backend infrastructure.

## Layout
```bash
.
├── README.md
├── ansible.cfg    # Global ansible config
├── collections
├── inventories    # Contains all the host/ group specific vars 
│   └── nyc01
├── playbooks      # All playbooks and roles
│   ├── files
│   ├── install-nomad.yml
│   ├── requirements.yml      # roles requirements that needs to be installed
│   ├── roles                 # directory for roles
│   ├── setup_hypervisor.yml
│   ├── tasks                 # directory containing import/ include - able tasks
│   └── templates
└── roles -> playbooks/roles  # Roles symlink
```

## Use
- Make sure you have the decryption password for vault encrypted files
stored in the path specified in [`ansible.cfg`](ansible.cfg)

- To run a playbook (for adding/removing SDNs from hypervisor, for e.g.), you can run:
```bash
ansible-playbook -i inventories/nyc01/hosts -l hypervisors playbooks/setup_hypervisor.yml -t sdn
```

## Development

### Setup
```bash
pip install -r requirements-dev.txt
```
