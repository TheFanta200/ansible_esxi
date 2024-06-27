# Déploiement Automatique ESXi

1. Copie de l'intégralité du fichier Ansible dans `/etc/ansible`.

2. Création du fichier vault pour sécuriser tous les comptes utilisés :

    ```bash
    ansible-vault create global_vars/esxi_vault.yml
    ```

3. Saisie et modification des informations suivantes dans le fichier vault :

    ```yaml
    # Connexion à ESXi
    esxi_hostname: "192.168.1.253"
    esxi_username: "ansible"
    esxi_password: "Password2024!"
    inventory_hostname: "192.168.1.253"

    # Groupe de ports
    vlans:
      - portgroup_name: "XXXXXX"
        vlan_id: 100
      - portgroup_name: "XXXXXXXX"
        vlan_id: 197

    ##### vCenter #####
    vcenter_hostname: "192.168.30.150"
    vcenter_username: "pentabyte.fr\\Svc_Ansible"
    vcenter_password: "Password2024!"
    datacenter_name: "Datacenter"
    cluster_name: "Paris"
    template_name: "Template_DEBIAN_12"
    vm_name: "PA-TEST"
    virtual_machine_datastore: "SAN-DATASTORE"

    ##### Networks #####
    GROUPE_PORTS: "Serveur"
    DNS1: "192.168.40.200"
    DNS2: "192.168.140.200"

    ##### Hardware #####
    RAM: 4096  # 4 GB
    CPU: 4     # 4 Core
    ```

4. Configuration des hôtes dans le fichier `hosts`.

5. Lancement du playbook :

    ```bash
    ansible-playbook playbook.yml 
    ```
