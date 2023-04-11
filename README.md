# Setup env
```shell
python3 -m venv _venv
source _venv/bin/activate
python -m pip install --upgrade pip
python -m pip install ansible-core
ansible-galaxy install -r ./requirements.yml
ansible-galaxy collection list
```

# Run infra
```shell
docker-compose up -d
```

# encrypt secrets (set password: secret)
```shell
ansible-vault encrypt inventory/group_vars/all/original.values.yaml --output inventory/group_vars/all/values.yaml 
```

# Test infra
```shell
ansible --ask-vault-pass -m ping -i inventory/inventory.yaml all
```

# generate certificates (password: secret)
```shell
 ansible-playbook --ask-vault-pass certs/cert-playbook.yaml -i inventory/inventory.yaml
```
