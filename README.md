# Vsftpd

An Ansible role for installing and configuring vsftpd on CentOS/RHEL 7.  

## Tasks
tasks/main.yml is het belangrijkste bestand. Dit is de eigenlijke playbook waarin alle acties beschreven worden die
moeten uitgevoerd worden.

## defaults
• defaults/main.yml en vars/main.yml bevatten variabelen. In defaults vind je standaardwaarden voor variabelen
die door de gebruiker kunnen aangepast worden. In vars komen die variabelen die in principe niet moeten veranderd
worden, bijvoorbeeld de namen van te installeren packages.
## Handlers
handlers/main.yml bevat taken die moeten uitgevoerd worden in reactie op een gebeurtenis. Het typische voorbeeld
is een service herstarten als je het configuratiebestand hebt aangepast.
• meta/main.yml bevat meta-informatie over de rol, bv. auteursnaam en licentie. Dit moet je zeker aanpassen als je je
rol publiceert.
##Test
• tests/ bevat een kleine testomgeving met een eigen Vagrantfile en playbook
## Links
- <http://vsftpd.beasts.org/vsftpd_conf.html>
- <https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/System_Administrators_Guide/s1-FTP.html> 

## License

MIT
