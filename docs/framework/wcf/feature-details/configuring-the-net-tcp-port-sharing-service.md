---
title: "Konfigurowanie usługi współużytkowania portów Net.TCP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 942b48ff6887e079beb7c0c24c6542a774eafe33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-the-nettcp-port-sharing-service"></a>Konfigurowanie usługi współużytkowania portów Net.TCP
Hostowanie Samoobsługowe usługom transportu Net.TCP można kontrolować kilka ustawień zaawansowanych, takich jak `ListenBacklog` i `MaxPendingAccepts`, które sterują zachowaniem podstawowej gniazda TCP używany do komunikacji sieciowej. Jednak te ustawienia dla każdego gniazda mają zastosowanie tylko na poziomie powiązanie wyłączenie powiązania transportu jest udostępnianie portów, co jest domyślnie włączona.  
  
 Po powiązaniu net.tcp umożliwia udostępnianie portów (przez ustawienie `portSharingEnabled =true` w elemencie powiązania transportu), niejawnie umożliwia procesu zewnętrznego (to znaczy SMSvcHost.exe, który obsługuje usługi udostępniania portów Net.TCP) do zarządzania gniazda TCP w jej imieniu. Na przykład podczas korzystania z protokołu TCP, określ:  
  
```xml  
    <tcpTransport   
        portSharingEnabled="true"  
/>  
```  
  
 Po skonfigurowaniu w ten sposób wszystkie ustawienia gniazda określonej w elemencie powiązania transportu usługi są zignorowany na rzecz gniazda ustawieniami SMSvcHost.exe.  
  
 Aby skonfigurować SMSvcHost.exe, Utwórz plik konfiguracyjny XML o nazwie pliku konfiguracji SmSvcHost.exe.config i umieść go w tym samym katalogu fizycznym jako plik wykonywalny SMSvcHost.exe (na przykład C:\Windows\Microsoft.NET\Framework\v4.5).  
  
 Poniższy przykład przedstawia przykład pliku konfiguracji SMSvcHost.exe.config, przy użyciu ustawień domyślnych dla wszystkich wartości można skonfigurować określone jawnie.  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="16" <!—16 * # of processors -->  
          maxPendingAccepts="4"<!— 4 * # of processors -->  
          maxPendingConnections="100"  
          receiveTimeout="00:00:30" <!—30 seconds -->  
          teredoEnabled="false">  
          <allowAccounts>  
             <!-- LocalSystem account -->  
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->  
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Administrators account -->  
             <add securityIdentifier="S-1-5-20"/>  
             <!-- Network Service account -->  
             <add securityIdentifier="S-1-5-32-544" />  
             <!-- IIS_IUSRS account (Vista only) -->  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.tcp>  
</configuration>  
```  
  
## <a name="when-to-modify-smsvchostexeconfig"></a>Podczas modyfikowania pliku konfiguracji SMSvcHost.exe.config  
 Ogólnie rzecz biorąc ostrożność podczas modyfikowania zawartości pliku pliku konfiguracji SMSvcHost.exe.config, ponieważ wszystkie ustawienia konfiguracji określone w tym pliku wpływ na wszystkie usługi na komputerze, który korzysta z usługi udostępniania portów Net.TCP. Obejmuje to aplikacje [!INCLUDE[wv](../../../../includes/wv-md.md)] korzystające z funkcji aktywacji TCP usługi aktywacji procesów systemu Windows (WAS).  
  
 Jednak czasami może być konieczne zmienić konfigurację domyślną dla usługi udostępniania portów Net.TCP. Na przykład, wartością domyślną dla `maxPendingAccepts` to 4 * liczba procesorów. Serwery obsługujące wiele usług korzystających z Udostępnianie portów może zwiększyć tę wartość, aby osiągnąć maksymalną przepustowość. Wartość domyślna dla `maxPendingConnections` to 100. Należy rozważyć również zwiększenie tej wartości, jeśli istnieje wielu klientów równoczesnych wywoływania usługi i usługa odrzuca połączenia klientów.  
  
 Pliku konfiguracji SMSvcHost.exe.config zawiera także informacje o używanych tożsamości, które mogą spowodować, że proces usługi współużytkowania portów. Podczas procesu nawiązanie połączenia usługi, aby korzystać z udostępnionego TCP współużytkowania portów portu, tożsamość procesu łączenia procesu jest sprawdzany względem listy tożsamości, które zezwala korzystanie z usługi współużytkowania portów. Tymi tożsamościami są określone jako identyfikatory zabezpieczeń (SID) w \<allowAccounts > sekcji pliku pliku konfiguracji SMSvcHost.exe.config. Domyślnie uprawnienia do używania usługi współużytkowania portów otrzymuje do kont systemowych (Usługa lokalna, system lokalny i Usługa sieciowa) oraz członkom grupy Administratorzy. Aplikacje, które umożliwiają procesu uruchomionego jako tożsamość (na przykład tożsamości użytkownika) do nawiązania połączenia usługi współużytkowania portów należy jawnie dodać odpowiedni identyfikator SID pliku konfiguracji SMSvcHost.exe.config (te zmiany nie zostaną zastosowane do czasu ukończenia procesu SMSvc.exe ponowne uruchomienie).  
  
> [!NOTE]
>  Na [!INCLUDE[wv](../../../../includes/wv-md.md)] systemów z (Kontrola konta) włączony, lokalnych użytkowników wymagają podniesionych uprawnień, nawet jeśli ich konto jest członkiem grupy Administratorzy. Do tych użytkowników umożliwić korzystanie z usługi bez podniesienia uprawnień, identyfikator SID użytkownika (lub identyfikator SID grupy, w którym użytkownik jest członkiem) współużytkowania portów należy jawnie dodać do \<allowAccounts > sekcji pliku konfiguracji SMSvcHost.exe.config.  
  
> [!WARNING]
>  Domyślny plik pliku konfiguracji SMSvcHost.exe.config określa niestandardowy `etwProviderId` zapobiegające śledzenia SMSvcHost.exe zakłócać ślady usługi.  
  
## <a name="see-also"></a>Zobacz też  
 [\<NET.TCP >](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
