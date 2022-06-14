![Captura de tela de 2022-06-13 23-44-53](https://user-images.githubusercontent.com/102430464/173482533-9bc4d975-f2ce-4dab-8c6a-178fe6cd9da3.png)
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

![Captura de tela de 2022-06-13 23-44-53](https://user-images.githubusercontent.com/102430464/173482560-9487a7e3-2bf0-43df-8125-86d5f5570396.png)



