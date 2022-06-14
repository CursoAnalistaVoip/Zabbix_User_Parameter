
# Zabbix_User_Parameter
Como utilizar o **UserParameter** para monitorar o Asterisk.
> Às vezes você pode querer executar uma verificação  que não vem pré definido no Zabbix
> Com o UserParameter é possivél realizar esse tipo de verificação.



A sintaxe do **UserParameter** é  :eyes:


> **UserParameter=< chave_do_item >,< comando >**
>  
> 
  Exemplo:
  
  UserParameter=linha.voip,sudo /usr/sbin/asterisk -rx "pjsip show registrations" | grep 5857658 | grep Registered | wc -l
  
  ![Captura de tela de 2022-06-13 23-49-20](https://user-images.githubusercontent.com/102430464/173483024-f7f47b01-a261-47b1-b69f-616ff9dfe8aa.png)
  
  ![Captura de tela de 2022-06-13 23-50-15](https://user-images.githubusercontent.com/102430464/173483121-55c7ca12-8166-4bd4-a9e2-b92fc71f730d.png)
  
  ![Captura de tela de 2022-06-13 23-51-49](https://user-images.githubusercontent.com/102430464/173483327-bc015137-8a9d-4622-8caa-cba616514876.png)


  Esse comando nos trouxe o resultado **0** , poís a conta SIP 5857658 não está registrada.
  
  
  


Agora se faz necessario dar permissão no sudoers do Linux:


mkdir -p etc/sudoers.d/user_zabbix


> #Allow the user zabbix to execute any command without password
> 
> Defaults:zabbix !requiretty
> 
> zabbix  ALL=(ALL:ALL) NOPASSWD:/usr/sbin/asterisk

![Captura de tela de 2022-06-13 23-44-53](https://user-images.githubusercontent.com/102430464/173482560-9487a7e3-2bf0-43df-8125-86d5f5570396.png)

 #Reinicie o serviço do Zabbix Agent: :+1: 
> **systemctl restart zabbix-agent**


> Agora vamos criar nosso item no Zabbix   :clap:



