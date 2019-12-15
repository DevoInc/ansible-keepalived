ansible-keepalived: Ansible role for setting up keepalived 
============================================================
Keepalived can watch processes to influence on which node should be the master. Setting
variable "keepalived_check_process" to the name of the process will do. I use keepalived
to give high availability to haproxy, so I use.

keepalived_check_process: "haproxy"

Dependencies
------------
  debops.sysctl


Role Variables
--------------
	keepalived_auth_pass: "1111"
	keepalived_role: "MASTER"
	keepalived_router_id: "52"
	keepalived_shared_iface: "virtual machine local interface"
	keepalived_shared_ip: "virtual machine local ip with last octet equal 252"
	keepalived_check_process: "keepalived"
	keepalived_priority: "100"
	keepalived_backup_priority: "50"


Example Playbook
-------------------------

    ansible-playbook --vault-password-file ~/.vault_pass.txt -u vagrant --sudo ansible/playbooks/keepalived.yml -i ansible/environments/aws/eu/int -e host=127.0.0.1 -e ansible_port=2222 -e ansible_ssh_pass=vagrant -e keepalived_shared_ip=10.0.2.252 -e keepalived_unicast_peer_ip=10.0.2.16
