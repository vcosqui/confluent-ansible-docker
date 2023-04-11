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

# Test infra
```shell
ansible -m ping -i hosts.yaml all
```

# run west playbook (password: secret)
```shell
ansible-playbook --ask-vault-pass playbook_west.yaml -i hosts.yaml
```

# run all playbook (password: secret)
```shell
ansible-playbook --ask-vault-pass playbook.yaml -i hosts.yaml
```
