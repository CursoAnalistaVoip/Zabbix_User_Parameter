# Zabbix_User_Parameter
Como utilizar o **UserParameter** para monitorar o Asterisk.
> Às vezes você pode querer executar uma verificação  que não vem pré definido no Zabbix
> Com o UserParameter é possivél realizar esse tipo de verificação.



A sintaxe do UserParameter é  :eyes:


> **UserParameter=< chave_do_item >,< comando >**
>  
> 
  Exemplo:
  
  




Agora se faz necessario dar permissão no sudoers do Linux:


mkdir -p etc/sudoers.d/user_zabbix


> #Allow the user zabbix to execute any command without password
> 
> Defaults:zabbix !requiretty
> 
> zabbix  ALL=(ALL:ALL) NOPASSWD:/usr/sbin/asterisk
