---
title: Konfigurowanie usługi współużytkowania portów Net.TCP
ms.date: 03/30/2017
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
ms.openlocfilehash: 70ebaeb8b41b0191e0352b5ef6a4b1913994100c
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988220"
---
# <a name="configuring-the-nettcp-port-sharing-service"></a>Konfigurowanie usługi współużytkowania portów Net.TCP
Samoobsługowe usługi korzystające z transportu net. TCP mogą kontrolować kilka ustawień zaawansowanych, takich jak `ListenBacklog` i `MaxPendingAccepts`, które określają zachowanie bazowego gniazda TCP używanego do komunikacji sieciowej. Jednak te ustawienia dla każdego gniazda są stosowane tylko na poziomie powiązania, Jeśli powiązanie transportowe ma wyłączone Udostępnianie portów, które jest domyślnie włączone.  
  
 Gdy powiązanie net. TCP włącza Udostępnianie portów (przez ustawienie `portSharingEnabled =true` elementu powiązania transportu), niejawnie zezwala na proces zewnętrzny (tj. SMSvcHost. exe, który hostuje usługę udostępniania portów Net. TCP) do zarządzania gniazdem TCP w jego imieniu. Na przykład w przypadku używania protokołu TCP należy określić:  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 Po skonfigurowaniu w ten sposób wszystkie ustawienia gniazda określone w elemencie powiązania transportowego usługi są ignorowane na korzyść ustawień gniazda określonych przez SMSvcHost. exe.  
  
 Aby skonfigurować SMSvcHost. exe, Utwórz plik konfiguracji XML o nazwie SmSvcHost. exe. config i umieść go w tym samym katalogu fizycznym, co plik wykonywalny SMSvcHost. exe (na przykład C:\Windows\Microsoft.NET\Framework\v4.5).  
  
 Poniższy przykład ilustruje przykład SMSvcHost. exe. config z domyślnymi ustawieniami wszystkich konfigurowalnych wartości jawnie.  
  
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
  
## <a name="when-to-modify-smsvchostexeconfig"></a>Kiedy należy zmodyfikować plik SMSvcHost. exe. config  
 Ogólnie rzecz biorąc należy zachować ostrożność przy modyfikowaniu zawartości pliku SMSvcHost. exe. config, ponieważ wszystkie ustawienia konfiguracji określone w tym pliku mają wpływ na wszystkie usługi na komputerze, który używa usługi udostępniania portów Net. TCP. Obejmuje to aplikacje [!INCLUDE[wv](../../../../includes/wv-md.md)] , które korzystają z funkcji aktywacji TCP usługi aktywacji procesów systemu Windows (was).  
  
 Czasami jednak może zajść potrzeba zmiany konfiguracji domyślnej dla usługi udostępniania portów Net. TCP. Na przykład wartość `maxPendingAccepts` domyślna to 4 * liczba procesorów. Serwery obsługujące dużą liczbę usług korzystających z udostępniania portów mogą zwiększyć tę wartość, aby osiągnąć maksymalną przepływność. Wartość `maxPendingConnections` domyślna to 100. Należy rozważyć zwiększenie tej wartości także wtedy, gdy istnieje wielu współbieżnych klientów wywołujących usługę, a usługa porzuca połączenia klientów.  
  
 SMSvcHost. exe. config zawiera również informacje o tożsamościach procesów, które mogą korzystać z usługi udostępniania portów. Gdy proces nawiązuje połączenie z usługą udostępniania portów w celu korzystania ze współużytkowanego portu TCP, tożsamość procesu łączącego jest sprawdzana pod kątem listy tożsamości, które mogą korzystać z usługi udostępniania portów. Te tożsamości są określone jako identyfikatory zabezpieczeń (SID) w \<sekcji allowAccounts > pliku SMSvcHost. exe. config. Domyślnie uprawnienia do korzystania z usługi udostępniania portów są przyznawane kontom systemowym (LocalService, LocalSystem i NetworkService), a także członkami grupy Administratorzy. Aplikacje, które zezwalają na proces uruchomiony jako inna tożsamość (na przykład tożsamość użytkownika) w celu nawiązania połączenia z usługą udostępniania portów, muszą jawnie dodać odpowiedni identyfikator SID do pliku SMSvcHost. exe. config (te zmiany nie są stosowane, dopóki proces SMSvc. exe nie będzie uruchomione ponownie).  
  
> [!NOTE]
> W [!INCLUDE[wv](../../../../includes/wv-md.md)] systemach z włączoną funkcją kontroli konta użytkownika (UAC) Użytkownicy lokalni wymagają podwyższonego poziomu uprawnień nawet wtedy, gdy ich konto jest członkiem grupy Administratorzy. Aby umożliwić tym użytkownikom korzystanie z usługi udostępniania portów bez podniesienia uprawnień, identyfikator SID użytkownika (lub identyfikator SID grupy, w której użytkownik jest członkiem) musi zostać jawnie dodany do \<sekcji allowAccounts > pliku SMSvcHost. exe. config.  
  
> [!WARNING]
> Domyślny plik SMSvcHost. exe. config określa niestandardową `etwProviderId` , aby zapobiec zakłócaniu śledzenia przez program SMSvcHost. exe.  
  
## <a name="see-also"></a>Zobacz także

- [\<net.tcp>](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
