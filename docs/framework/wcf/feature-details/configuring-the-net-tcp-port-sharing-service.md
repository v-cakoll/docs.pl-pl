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
# <a name="configuring-the-nettcp-port-sharing-service"></a><span data-ttu-id="788e9-102">Konfigurowanie usługi współużytkowania portów Net.TCP</span><span class="sxs-lookup"><span data-stu-id="788e9-102">Configuring the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="788e9-103">Usługi hostowane samodzielnie, które używają transportu Net.TCP, mogą `ListenBacklog` `MaxPendingAccepts`kontrolować kilka zaawansowanych ustawień, takich jak i , które regulują zachowanie bazowego gniazda TCP używanego do komunikacji sieciowej.</span><span class="sxs-lookup"><span data-stu-id="788e9-103">Self-hosted services that use the Net.TCP transport can control several advanced settings, such as `ListenBacklog` and `MaxPendingAccepts`, which govern the behavior of the underlying TCP socket used for network communication.</span></span> <span data-ttu-id="788e9-104">Jednak te ustawienia dla każdego gniazda mają zastosowanie tylko na poziomie powiązania, jeśli powiązanie transportu ma wyłączone udostępnianie portów, które jest domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="788e9-104">However, these settings for each socket only apply at the binding level if the transport binding has disabled port sharing, which is enabled by default.</span></span>  
  
 <span data-ttu-id="788e9-105">Gdy powiązanie net.tcp umożliwia udostępnianie `portSharingEnabled =true` portów (przez ustawienie elementu wiązania transportu), niejawnie zezwala na proces zewnętrzny (a mianowicie program SMSvcHost.exe, w którym jest obsługiwana usługa udostępniania portów Net.TCP) do zarządzania gniazdem TCP w jego imieniu.</span><span class="sxs-lookup"><span data-stu-id="788e9-105">When a net.tcp binding enables port sharing (by setting `portSharingEnabled =true` on the transport binding element), it implicitly allows an external process (namely the SMSvcHost.exe, which hosts the Net.TCP Port Sharing Service) to manage the TCP socket on its behalf.</span></span> <span data-ttu-id="788e9-106">Na przykład podczas korzystania z protokołu TCP określ:</span><span class="sxs-lookup"><span data-stu-id="788e9-106">For example, when using TCP, specify:</span></span>  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 <span data-ttu-id="788e9-107">Po skonfigurowaniu w ten sposób wszystkie ustawienia gniazda określone w elemencie wiązania transportu usługi są ignorowane na rzecz ustawień gniazda określonych przez program SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="788e9-107">When configured in this way, any socket settings specified on the service's transport binding element are ignored in favor of the socket settings specified by SMSvcHost.exe.</span></span>  
  
 <span data-ttu-id="788e9-108">Aby skonfigurować program SMSvcHost.exe, należy utworzyć plik konfiguracyjny XML o nazwie SmSvcHost.exe.config i umieścić go w tym samym katalogu fizycznym, co plik wykonywalny programu SMSvcHost.exe (na przykład C:\Windows\Microsoft.NET\Framework\v4.5).</span><span class="sxs-lookup"><span data-stu-id="788e9-108">To configure the SMSvcHost.exe, create an XML configuration file named SmSvcHost.exe.config and place it in the same physical directory as the SMSvcHost.exe executable (for example, C:\Windows\Microsoft.NET\Framework\v4.5).</span></span>  
  
 <span data-ttu-id="788e9-109">Poniższy przykład ilustruje przykładowy plik SMSvcHost.exe.config z domyślnymi ustawieniami dla wszystkich konfigurowalnych wartości podanych jawnie.</span><span class="sxs-lookup"><span data-stu-id="788e9-109">The following example illustrates a sample SMSvcHost.exe.config, with the default settings for all configurable values stated explicitly.</span></span>  
  
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
  
## <a name="when-to-modify-smsvchostexeconfig"></a><span data-ttu-id="788e9-110">Kiedy zmodyfikować plik SMSvcHost.exe.config</span><span class="sxs-lookup"><span data-stu-id="788e9-110">When to Modify SMSvcHost.exe.config</span></span>  
 <span data-ttu-id="788e9-111">Ogólnie rzecz biorąc, należy zwrócić uwagę podczas modyfikowania zawartości pliku SMSvcHost.exe.config, ponieważ wszelkie ustawienia konfiguracji określone w tym pliku wpływają na wszystkie usługi na komputerze korzystającym z usługi udostępniania portów Net.TCP.</span><span class="sxs-lookup"><span data-stu-id="788e9-111">In general, care should be taken when modifying the contents of the SMSvcHost.exe.config file, because any configuration settings specified in this file affect all of the services on a computer that uses the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="788e9-112">Obejmuje to aplikacje w systemie Windows Vista korzystające z funkcji aktywacji TCP usługi aktywacji procesów systemu Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="788e9-112">This includes applications on Windows Vista that use the TCP Activation features of the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="788e9-113">Czasami jednak może być konieczna zmiana domyślnej konfiguracji usługi udostępniania portów Net.TCP.</span><span class="sxs-lookup"><span data-stu-id="788e9-113">However, sometimes you may need to change the default configuration for the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="788e9-114">Na przykład wartość domyślna dla `maxPendingAccepts` to 4 \* liczba procesorów.</span><span class="sxs-lookup"><span data-stu-id="788e9-114">For example, the default value for `maxPendingAccepts` is 4 \* number of processors.</span></span> <span data-ttu-id="788e9-115">Serwery obsługujące dużą liczbę usług korzystających z udostępniania portów mogą zwiększyć tę wartość, aby osiągnąć maksymalną przepływność.</span><span class="sxs-lookup"><span data-stu-id="788e9-115">Servers that host a large number of services that use port sharing may increase this value to achieve maximum throughput.</span></span> <span data-ttu-id="788e9-116">Wartość domyślna `maxPendingConnections` to 100.</span><span class="sxs-lookup"><span data-stu-id="788e9-116">The default value for `maxPendingConnections` is 100.</span></span> <span data-ttu-id="788e9-117">Należy rozważyć zwiększenie tej wartości również wtedy, gdy istnieje wiele równoczesnych klientów wywołujących usługę i usługa jest upuszczanie połączeń klienta.</span><span class="sxs-lookup"><span data-stu-id="788e9-117">You should consider increasing this value also if there are multiple concurrent clients calling the service and the service is dropping client connections.</span></span>  
  
 <span data-ttu-id="788e9-118">Plik SMSvcHost.exe.config zawiera również informacje o tożsamościach procesu, które mogą korzystać z usługi udostępniania portów.</span><span class="sxs-lookup"><span data-stu-id="788e9-118">SMSvcHost.exe.config also contains information about the process identities that may make use of the port sharing service.</span></span> <span data-ttu-id="788e9-119">Gdy proces łączy się z usługą udostępniania portów w celu korzystania z udostępnionego portu TCP, tożsamość procesu połączenia jest sprawdzana względem listy tożsamości, które mogą korzystać z usługi udostępniania portów.</span><span class="sxs-lookup"><span data-stu-id="788e9-119">When a process connects to the port sharing service to make use of a shared TCP port, the process identity of the connecting process is checked against a list of identities that are permitted to make use of the port sharing service.</span></span> <span data-ttu-id="788e9-120">Tożsamości te są określone jako identyfikatory zabezpieczeń (IDENTYFIKATORY) w \<allowAccounts> sekcji pliku SMSvcHost.exe.config.</span><span class="sxs-lookup"><span data-stu-id="788e9-120">These identities are specified as security identifiers (SIDs) in the \<allowAccounts> section of the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="788e9-121">Domyślnie uprawnienia do korzystania z usługi udostępniania portów są przyznawane kontom systemowym (LocalService, LocalSystem i NetworkService) oraz członkom grupy Administratorzy.</span><span class="sxs-lookup"><span data-stu-id="788e9-121">By default, permission to use the port sharing service is granted to system accounts (LocalService, LocalSystem, and NetworkService) as well as members of the Administrators group.</span></span> <span data-ttu-id="788e9-122">Aplikacje, które zezwalają na proces uruchomiony jako inna tożsamość (na przykład tożsamość użytkownika) do łączenia się z usługą udostępniania portów, muszą jawnie dodać odpowiedni identyfikator SID do pliku SMSvcHost.exe.config (zmiany te nie są stosowane do czasu ponownego uruchomienia procesu SMSvc.exe).</span><span class="sxs-lookup"><span data-stu-id="788e9-122">Applications that allow a process running as another identity (for example, a user identity) to connect to the port sharing service must explicitly add the appropriate SID to the SMSvcHost.exe.config (these changes are not applied until the SMSvc.exe process is restarted).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="788e9-123">W systemach Windows Vista z włączoną kontrolą konta użytkownika użytkownicy lokalni wymagają podwyższonych uprawnień, nawet jeśli ich konto jest członkiem grupy Administratorzy.</span><span class="sxs-lookup"><span data-stu-id="788e9-123">On Windows Vista systems with User Account Control (UAC) enabled, local users require elevated permissions even if their account is a member of the Administrators group.</span></span> <span data-ttu-id="788e9-124">Aby umożliwić tym użytkownikom korzystanie z usługi udostępniania portów bez podniesienia poziomu, identyfikator SID użytkownika (lub identyfikator SID grupy, w \<której użytkownik jest członkiem) musi zostać jawnie dodany do sekcji allowAccounts> smSvcHost.exe.config.</span><span class="sxs-lookup"><span data-stu-id="788e9-124">To allow these users to make use of the port sharing service without elevation, the user's SID (or the SID of a group in which the user is a member) must be explicitly added to the \<allowAccounts> section of SMSvcHost.exe.config.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="788e9-125">Domyślny plik SMSvcHost.exe.config określa `etwProviderId` niestandardowe, aby zapobiec śledzeniu SMSvcHost.exe zakłócania śledzenia usług.</span><span class="sxs-lookup"><span data-stu-id="788e9-125">The default SMSvcHost.exe.config file specifies a custom `etwProviderId` to prevent SMSvcHost.exe tracing from interfering with service traces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="788e9-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="788e9-126">See also</span></span>

- [<span data-ttu-id="788e9-127">\<net.tcp></span><span class="sxs-lookup"><span data-stu-id="788e9-127">\<net.tcp></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
