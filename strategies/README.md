# Strategies

[http://docs.ansible.com/ansible/playbooks_strategies.html]

Example contents:
- [demo playbook](strategy_example.yml)
- [sample inventory](inventory)

Example of a linear strategy (default):
```sh
strategy:linear
```
```sh
$ ansible-playbook strategy_example.yml -i inventory
```
```sh
PLAY [all] ******************************************************************************************

TASK [Gathering Facts] ******************************************************************************
ok: [host3]
ok: [host1]
ok: [host2]

TASK [First step] ***********************************************************************************
ok: [host1] => {
    "msg": "Step 1. Something is done here"
}
ok: [host2] => {
    "msg": "Step 1. Something is done here"
}
ok: [host3] => {
    "msg": "Step 1. Something is done here"
}

TASK [Second step] **********************************************************************************
ok: [host1] => {
    "msg": "Step 2. Something is done here"
}
ok: [host2] => {
    "msg": "Step 2. Something is done here"
}
ok: [host3] => {
    "msg": "Step 2. Something is done here"
}

TASK [Third step] ***********************************************************************************
ok: [host1] => {
    "msg": "Step 3. Something is done here"
}
ok: [host2] => {
    "msg": "Step 3. Something is done here"
}
ok: [host3] => {
    "msg": "Step 3. Something is done here"
}

PLAY RECAP ******************************************************************************************
host1                      : ok=4    changed=0    unreachable=0    failed=0   
host2                      : ok=4    changed=0    unreachable=0    failed=0   
host3                      : ok=4    changed=0    unreachable=0    failed=0   

```

Example of a free strategy, which allows each host to run until the end
 of the play as fast as it can.
```sh
strategy:free
```
```sh
$ ansible-playbook strategy_example.yml -i inventory
```
```sh
PLAY [all] ******************************************************************************************

TASK [Gathering Facts] ******************************************************************************
ok: [host2]
ok: [host1]
ok: [host3]

TASK [First step] ***********************************************************************************
ok: [host2] => {
    "msg": "Step 1. Something is done here"
}
ok: [host1] => {
    "msg": "Step 1. Something is done here"
}
ok: [host3] => {
    "msg": "Step 1. Something is done here"
}

TASK [Second step] **********************************************************************************
ok: [host2] => {
    "msg": "Step 2. Something is done here"
}
ok: [host1] => {
    "msg": "Step 2. Something is done here"
}
ok: [host3] => {
    "msg": "Step 2. Something is done here"
}

TASK [Third step] ***********************************************************************************
ok: [host2] => {
    "msg": "Step 3. Something is done here"
}
ok: [host1] => {
    "msg": "Step 3. Something is done here"
}
ok: [host3] => {
    "msg": "Step 3. Something is done here"
}

PLAY RECAP ******************************************************************************************
host1                      : ok=4    changed=0    unreachable=0    failed=0   
host2                      : ok=4    changed=0    unreachable=0    failed=0   
host3                      : ok=4    changed=0    unreachable=0    failed=0   

```
