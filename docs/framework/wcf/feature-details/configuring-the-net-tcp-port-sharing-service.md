---
title: Konfigurowanie usługi współużytkowania portów Net.TCP
ms.date: 03/30/2017
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
ms.openlocfilehash: fea2e734099c4c623dcde2a37f4c164cf9ce61ac
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464196"
---
# <a name="configuring-the-nettcp-port-sharing-service"></a>Konfigurowanie usługi współużytkowania portów Net.TCP
Usługi hostowane samodzielnie, które używają transportu Net.TCP, mogą `ListenBacklog` `MaxPendingAccepts`kontrolować kilka zaawansowanych ustawień, takich jak i , które regulują zachowanie bazowego gniazda TCP używanego do komunikacji sieciowej. Jednak te ustawienia dla każdego gniazda mają zastosowanie tylko na poziomie powiązania, jeśli powiązanie transportu ma wyłączone udostępnianie portów, które jest domyślnie włączone.  
  
 Gdy powiązanie net.tcp umożliwia udostępnianie `portSharingEnabled =true` portów (przez ustawienie elementu wiązania transportu), niejawnie zezwala na proces zewnętrzny (a mianowicie program SMSvcHost.exe, w którym jest obsługiwana usługa udostępniania portów Net.TCP) do zarządzania gniazdem TCP w jego imieniu. Na przykład podczas korzystania z protokołu TCP określ:  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 Po skonfigurowaniu w ten sposób wszystkie ustawienia gniazda określone w elemencie wiązania transportu usługi są ignorowane na rzecz ustawień gniazda określonych przez program SMSvcHost.exe.  
  
 Aby skonfigurować program SMSvcHost.exe, należy utworzyć plik konfiguracyjny XML o nazwie SmSvcHost.exe.config i umieścić go w tym samym katalogu fizycznym, co plik wykonywalny programu SMSvcHost.exe (na przykład C:\Windows\Microsoft.NET\Framework\v4.5).  
  
 Poniższy przykład ilustruje przykładowy plik SMSvcHost.exe.config z domyślnymi ustawieniami dla wszystkich konfigurowalnych wartości podanych jawnie.  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="16" <!-- 16 * # of processors -->  
          maxPendingAccepts="4"<!-- 4 * # of processors -->  
          maxPendingConnections="100"  
          receiveTimeout="00:00:30" <!-- 30 seconds -->  
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
    </system.serviceModel.activation>
</configuration>  
```  
  
## <a name="when-to-modify-smsvchostexeconfig"></a>Kiedy zmodyfikować plik SMSvcHost.exe.config  
 Ogólnie rzecz biorąc, należy zwrócić uwagę podczas modyfikowania zawartości pliku SMSvcHost.exe.config, ponieważ wszelkie ustawienia konfiguracji określone w tym pliku wpływają na wszystkie usługi na komputerze korzystającym z usługi udostępniania portów Net.TCP. Obejmuje to aplikacje w systemie Windows Vista korzystające z funkcji aktywacji TCP usługi aktywacji procesów systemu Windows (WAS).  
  
 Czasami jednak może być konieczna zmiana domyślnej konfiguracji usługi udostępniania portów Net.TCP. Na przykład wartość domyślna dla `maxPendingAccepts` to 4 * liczba procesorów. Serwery obsługujące dużą liczbę usług korzystających z udostępniania portów mogą zwiększyć tę wartość, aby osiągnąć maksymalną przepływność. Wartość domyślna `maxPendingConnections` to 100. Należy rozważyć zwiększenie tej wartości również wtedy, gdy istnieje wiele równoczesnych klientów wywołujących usługę i usługa jest upuszczanie połączeń klienta.  
  
 Plik SMSvcHost.exe.config zawiera również informacje o tożsamościach procesu, które mogą korzystać z usługi udostępniania portów. Gdy proces łączy się z usługą udostępniania portów w celu korzystania z udostępnionego portu TCP, tożsamość procesu połączenia jest sprawdzana względem listy tożsamości, które mogą korzystać z usługi udostępniania portów. Tożsamości te są określone jako identyfikatory zabezpieczeń (IDENTYFIKATORY) w \<allowAccounts> sekcji pliku SMSvcHost.exe.config. Domyślnie uprawnienia do korzystania z usługi udostępniania portów są przyznawane kontom systemowym (LocalService, LocalSystem i NetworkService) oraz członkom grupy Administratorzy. Aplikacje, które zezwalają na proces uruchomiony jako inna tożsamość (na przykład tożsamość użytkownika) do łączenia się z usługą udostępniania portów, muszą jawnie dodać odpowiedni identyfikator SID do pliku SMSvcHost.exe.config (zmiany te nie są stosowane do czasu ponownego uruchomienia procesu SMSvc.exe).  
  
> [!NOTE]
> W systemach Windows Vista z włączoną kontrolą konta użytkownika użytkownicy lokalni wymagają podwyższonych uprawnień, nawet jeśli ich konto jest członkiem grupy Administratorzy. Aby umożliwić tym użytkownikom korzystanie z usługi udostępniania portów bez podniesienia poziomu, identyfikator SID użytkownika (lub identyfikator SID grupy, w \<której użytkownik jest członkiem) musi zostać jawnie dodany do sekcji allowAccounts> smSvcHost.exe.config.  
  
> [!WARNING]
> Domyślny plik SMSvcHost.exe.config określa `etwProviderId` niestandardowe, aby zapobiec śledzeniu SMSvcHost.exe zakłócania śledzenia usług.  
  
## <a name="see-also"></a>Zobacz też

- [\<net.tcp>](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
