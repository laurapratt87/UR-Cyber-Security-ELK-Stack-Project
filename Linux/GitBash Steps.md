## Elk Commands and Steps

This guide should help with step-by-step commands to SSH, start and attach containers, and ultimately navigate to the Kibana Dashboard for the ELK server.

- GitBash

  - ssh redadmin@168.62.165.226

  - sudo docker container list -a

  - sudo docker container start relaxed_kapitsa

  - sudo docker container attach relaxed_kapitsa

  - cd /etc/ansible 

  - ls

    - ELK_Playbook.yml	ansible.cfg	filebeat-config.yml	hosts	metricbeat-config.yml	metricbeat-playbook.yml	my-playbook.yml

  - ssh sysadmin@10.2.0.4

  - sudo docker container start elk

  - http://13.83.81.121:5601/app/kibana#/home

# Troubleshooting:
  - Re-run playbooks
  - Double check IP listed in URL
  - Make sure it is http not https

