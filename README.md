# Déployer Automatique ESXI

1. Copier l'intégralité du fichier Ansible dans `/etc/ansible`.

2. Créer le fichier vault permettant de stocker de manière sécurisée tous les comptes utilisés :

    ```bash
    ansible-vault create global_vars/esxi_vault.yml
    ```

3. Saisir et modifier les informations suivantes dans le fichier vault :

    ```yaml
    # Connexion to ESXI
    esxi_hostname: "XXXXXXX"
    esxi_username: "XXXXX"
    esxi_password: "XXXXXXXX"
    inventory_hostname: "XXXXXX"

    # Groupe de port
    vlans:
      - portgroup_name: 'XXXXXX'
        vlan_id: 100
      - portgroup_name: 'XXXXXXXX'
        vlan_id: 198
    ```

4. Configurer vos hôtes dans le fichier `hosts`.

5. Lancer le playbook :

    ```bash
    ansible-playbook playbook.yml 
    ```
