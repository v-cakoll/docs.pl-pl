---
title: Konfigurowanie usługi współużytkowania portów Net.TCP
ms.date: 03/30/2017
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
ms.openlocfilehash: dbc27f0f15be41c5384d8a1f73f0226c3f0f83ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206814"
---
# <a name="configuring-the-nettcp-port-sharing-service"></a>Konfigurowanie usługi współużytkowania portów Net.TCP
Użyj transportu Net.TCP własnym obsługiwanych usług można kontrolować kilka ustawień zaawansowanych, takich jak `ListenBacklog` i `MaxPendingAccepts`, które sterują zachowaniem bazowego gniazda TCP, używana do komunikacji sieciowej. Jednak te ustawienia dla każdego gniazda stosowane tylko wtedy na poziomie powiązania Jeśli powiązania transportu wyłączył możliwość współużytkowania portów, co jest domyślnie włączona.  
  
 Po powiązaniu net.tcp umożliwia udostępnianie portów (przez ustawienie `portSharingEnabled =true` na element powiązania transportu), niejawnie zezwala procesie zewnętrznym (czyli SMSvcHost.exe, który hostuje usługi udostępniania portów Net.TCP) do zarządzania gniazda TCP w jej imieniu. Na przykład korzystając z protokołu TCP, należy określić:  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 Po skonfigurowaniu w ten sposób wszystkie ustawienia gniazda określonego dla elementu powiązania transportu usługi są ignorowane na rzecz ustawień gniazda określonego przez SMSvcHost.exe.  
  
 Aby skonfigurować SMSvcHost.exe, Utwórz plik konfiguracyjny XML o nazwie pliku konfiguracyjnego SmSvcHost.exe.config i umieść go w tym samym katalogu fizycznego SMSvcHost.exe plik wykonywalny (na przykład C:\Windows\Microsoft.NET\Framework\v4.5).  
  
 W poniższym przykładzie pokazano próbkę pliku konfiguracyjnego SMSvcHost.exe.config, używając ustawień domyślnych dla wszystkich wartości można skonfigurować określone jawnie.  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="16" <!--16 * # of processors -->  
          maxPendingAccepts="4"<!-- 4 * # of processors -->  
          maxPendingConnections="100"  
          receiveTimeout="00:00:30" <!--30 seconds -->  
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
  
## <a name="when-to-modify-smsvchostexeconfig"></a>Podczas modyfikowania pliku konfiguracyjnego SMSvcHost.exe.config  
 Ogólnie rzecz biorąc należy zachować ostrożność podczas modyfikowania zawartości pliku pliku konfiguracyjnego SMSvcHost.exe.config, ponieważ wszystkie ustawienia konfiguracji określone w tym pliku mają wpływ na wszystkie usługi na komputerze, który używa usługi udostępniania portów Net.TCP. Obejmuje to aplikacje [!INCLUDE[wv](../../../../includes/wv-md.md)] korzystające z funkcji aktywacji TCP Windows Process Activation Service (WAS).  
  
 Jednak czasami trzeba zmienić konfigurację domyślną dla usługi udostępniania portów Net.TCP. Na przykład, wartość domyślna dla `maxPendingAccepts` wynosi 4 * liczba procesorów. Serwery obsługujące dużej liczby usług korzystających z współużytkowania portów może zwiększyć tę wartość, aby osiągnąć maksymalną przepustowość. Wartością domyślną dla `maxPendingConnections` wynosi 100. Należy rozważyć zwiększenie tej wartości również, jeśli istnieje wielu klientów jednocześnie wywoływania usługi, a usługa odrzuca połączenia klientów.  
  
 Pliku konfiguracyjnego SMSvcHost.exe.config zawiera także informacje o tożsamości, które mogą używać procesu współużytkowania portów. Gdy proces, który nawiązuje połączenie z port udostępnianej usługi do korzystania z tych udostępnionych TCP port, tożsamość procesu nawiązywania połączenia z procesu jest sprawdzana względem listę tożsamości, które zezwala użytkowania współużytkowania portów. Te tożsamości są określane jako identyfikatory zabezpieczeń (SID) w \<allowAccounts > sekcja pliku pliku konfiguracyjnego SMSvcHost.exe.config. Domyślnie uprawnienia do korzystania z usługi udostępniania portów zostanie ustanowione konta systemowe (Usługa lokalna, system lokalny i Usługa sieciowa) oraz członków grupy Administratorzy. Aplikacji, które umożliwiają procesu uruchomionego w innej tożsamości (na przykład, tożsamość użytkownika) do połączenia z współużytkowania portów należy jawnie dodać odpowiedni identyfikator SID do pliku konfiguracyjnego SMSvcHost.exe.config (te zmiany nie są stosowane do procesu SMSvc.exe ponownego uruchomienia).  
  
> [!NOTE]
>  Na [!INCLUDE[wv](../../../../includes/wv-md.md)] systemów z (Kontrola konta) włączone, lokalnych użytkowników wymagane podniesione uprawnienia, nawet jeśli ich konto jest członkiem grupy Administratorzy. Aby umożliwić użytkownikom tych użytkowania port udostępnianej usługi bez podniesienia uprawnień, identyfikator SID użytkownika (lub identyfikatora SID grupy, w którym użytkownik jest członkiem), które muszą zostać jawnie dodane do \<allowAccounts > części pliku konfiguracyjnego SMSvcHost.exe.config.  
  
> [!WARNING]
>  Domyślny plik pliku konfiguracyjnego SMSvcHost.exe.config określa niestandardowy `etwProviderId` zapobiegające śledzenie SMSvcHost.exe od wchodzenia w konflikt ze śledzenia usługi.  
  
## <a name="see-also"></a>Zobacz także

- [\<net.tcp>](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
