---
title: Konfigurowanie usługi współużytkowania portów Net.TCP
ms.date: 03/30/2017
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
ms.openlocfilehash: dbc27f0f15be41c5384d8a1f73f0226c3f0f83ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62040186"
---
# <a name="configuring-the-nettcp-port-sharing-service"></a><span data-ttu-id="9c1af-102">Konfigurowanie usługi współużytkowania portów Net.TCP</span><span class="sxs-lookup"><span data-stu-id="9c1af-102">Configuring the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="9c1af-103">Użyj transportu Net.TCP własnym obsługiwanych usług można kontrolować kilka ustawień zaawansowanych, takich jak `ListenBacklog` i `MaxPendingAccepts`, które sterują zachowaniem bazowego gniazda TCP, używana do komunikacji sieciowej.</span><span class="sxs-lookup"><span data-stu-id="9c1af-103">Self-hosted services that use the Net.TCP transport can control several advanced settings, such as `ListenBacklog` and `MaxPendingAccepts`, which govern the behavior of the underlying TCP socket used for network communication.</span></span> <span data-ttu-id="9c1af-104">Jednak te ustawienia dla każdego gniazda stosowane tylko wtedy na poziomie powiązania Jeśli powiązania transportu wyłączył możliwość współużytkowania portów, co jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="9c1af-104">However, these settings for each socket only apply at the binding level if the transport binding has disabled port sharing, which is enabled by default.</span></span>  
  
 <span data-ttu-id="9c1af-105">Po powiązaniu net.tcp umożliwia udostępnianie portów (przez ustawienie `portSharingEnabled =true` na element powiązania transportu), niejawnie zezwala procesie zewnętrznym (czyli SMSvcHost.exe, który hostuje usługi udostępniania portów Net.TCP) do zarządzania gniazda TCP w jej imieniu.</span><span class="sxs-lookup"><span data-stu-id="9c1af-105">When a net.tcp binding enables port sharing (by setting `portSharingEnabled =true` on the transport binding element), it implicitly allows an external process (namely the SMSvcHost.exe, which hosts the Net.TCP Port Sharing Service) to manage the TCP socket on its behalf.</span></span> <span data-ttu-id="9c1af-106">Na przykład korzystając z protokołu TCP, należy określić:</span><span class="sxs-lookup"><span data-stu-id="9c1af-106">For example, when using TCP, specify:</span></span>  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 <span data-ttu-id="9c1af-107">Po skonfigurowaniu w ten sposób wszystkie ustawienia gniazda określonego dla elementu powiązania transportu usługi są ignorowane na rzecz ustawień gniazda określonego przez SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="9c1af-107">When configured in this way, any socket settings specified on the service's transport binding element are ignored in favor of the socket settings specified by SMSvcHost.exe.</span></span>  
  
 <span data-ttu-id="9c1af-108">Aby skonfigurować SMSvcHost.exe, Utwórz plik konfiguracyjny XML o nazwie pliku konfiguracyjnego SmSvcHost.exe.config i umieść go w tym samym katalogu fizycznego SMSvcHost.exe plik wykonywalny (na przykład C:\Windows\Microsoft.NET\Framework\v4.5).</span><span class="sxs-lookup"><span data-stu-id="9c1af-108">To configure the SMSvcHost.exe, create an XML configuration file named SmSvcHost.exe.config and place it in the same physical directory as the SMSvcHost.exe executable (for example, C:\Windows\Microsoft.NET\Framework\v4.5).</span></span>  
  
 <span data-ttu-id="9c1af-109">W poniższym przykładzie pokazano próbkę pliku konfiguracyjnego SMSvcHost.exe.config, używając ustawień domyślnych dla wszystkich wartości można skonfigurować określone jawnie.</span><span class="sxs-lookup"><span data-stu-id="9c1af-109">The following example illustrates a sample SMSvcHost.exe.config, with the default settings for all configurable values stated explicitly.</span></span>  
  
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
  
## <a name="when-to-modify-smsvchostexeconfig"></a><span data-ttu-id="9c1af-110">Podczas modyfikowania pliku konfiguracyjnego SMSvcHost.exe.config</span><span class="sxs-lookup"><span data-stu-id="9c1af-110">When to Modify SMSvcHost.exe.config</span></span>  
 <span data-ttu-id="9c1af-111">Ogólnie rzecz biorąc należy zachować ostrożność podczas modyfikowania zawartości pliku pliku konfiguracyjnego SMSvcHost.exe.config, ponieważ wszystkie ustawienia konfiguracji określone w tym pliku mają wpływ na wszystkie usługi na komputerze, który używa usługi udostępniania portów Net.TCP.</span><span class="sxs-lookup"><span data-stu-id="9c1af-111">In general, care should be taken when modifying the contents of the SMSvcHost.exe.config file, because any configuration settings specified in this file affect all of the services on a computer that uses the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="9c1af-112">Obejmuje to aplikacje [!INCLUDE[wv](../../../../includes/wv-md.md)] korzystające z funkcji aktywacji TCP Windows Process Activation Service (WAS).</span><span class="sxs-lookup"><span data-stu-id="9c1af-112">This includes applications on [!INCLUDE[wv](../../../../includes/wv-md.md)] that use the TCP Activation features of the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="9c1af-113">Jednak czasami trzeba zmienić konfigurację domyślną dla usługi udostępniania portów Net.TCP.</span><span class="sxs-lookup"><span data-stu-id="9c1af-113">However, sometimes you may need to change the default configuration for the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="9c1af-114">Na przykład, wartość domyślna dla `maxPendingAccepts` wynosi 4 \* liczba procesorów.</span><span class="sxs-lookup"><span data-stu-id="9c1af-114">For example, the default value for `maxPendingAccepts` is 4 \* number of processors.</span></span> <span data-ttu-id="9c1af-115">Serwery obsługujące dużej liczby usług korzystających z współużytkowania portów może zwiększyć tę wartość, aby osiągnąć maksymalną przepustowość.</span><span class="sxs-lookup"><span data-stu-id="9c1af-115">Servers that host a large number of services that use port sharing may increase this value to achieve maximum throughput.</span></span> <span data-ttu-id="9c1af-116">Wartością domyślną dla `maxPendingConnections` wynosi 100.</span><span class="sxs-lookup"><span data-stu-id="9c1af-116">The default value for `maxPendingConnections` is 100.</span></span> <span data-ttu-id="9c1af-117">Należy rozważyć zwiększenie tej wartości również, jeśli istnieje wielu klientów jednocześnie wywoływania usługi, a usługa odrzuca połączenia klientów.</span><span class="sxs-lookup"><span data-stu-id="9c1af-117">You should consider increasing this value also if there are multiple concurrent clients calling the service and the service is dropping client connections.</span></span>  
  
 <span data-ttu-id="9c1af-118">Pliku konfiguracyjnego SMSvcHost.exe.config zawiera także informacje o tożsamości, które mogą używać procesu współużytkowania portów.</span><span class="sxs-lookup"><span data-stu-id="9c1af-118">SMSvcHost.exe.config also contains information about the process identities that may make use of the port sharing service.</span></span> <span data-ttu-id="9c1af-119">Gdy proces, który nawiązuje połączenie z port udostępnianej usługi do korzystania z tych udostępnionych TCP port, tożsamość procesu nawiązywania połączenia z procesu jest sprawdzana względem listę tożsamości, które zezwala użytkowania współużytkowania portów.</span><span class="sxs-lookup"><span data-stu-id="9c1af-119">When a process connects to the port sharing service to make use of a shared TCP port, the process identity of the connecting process is checked against a list of identities that are permitted to make use of the port sharing service.</span></span> <span data-ttu-id="9c1af-120">Te tożsamości są określane jako identyfikatory zabezpieczeń (SID) w \<allowAccounts > sekcja pliku pliku konfiguracyjnego SMSvcHost.exe.config.</span><span class="sxs-lookup"><span data-stu-id="9c1af-120">These identities are specified as security identifiers (SIDs) in the \<allowAccounts> section of the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="9c1af-121">Domyślnie uprawnienia do korzystania z usługi udostępniania portów zostanie ustanowione konta systemowe (Usługa lokalna, system lokalny i Usługa sieciowa) oraz członków grupy Administratorzy.</span><span class="sxs-lookup"><span data-stu-id="9c1af-121">By default, permission to use the port sharing service is granted to system accounts (LocalService, LocalSystem, and NetworkService) as well as members of the Administrators group.</span></span> <span data-ttu-id="9c1af-122">Aplikacji, które umożliwiają procesu uruchomionego w innej tożsamości (na przykład, tożsamość użytkownika) do połączenia z współużytkowania portów należy jawnie dodać odpowiedni identyfikator SID do pliku konfiguracyjnego SMSvcHost.exe.config (te zmiany nie są stosowane do procesu SMSvc.exe ponownego uruchomienia).</span><span class="sxs-lookup"><span data-stu-id="9c1af-122">Applications that allow a process running as another identity (for example, a user identity) to connect to the port sharing service must explicitly add the appropriate SID to the SMSvcHost.exe.config (these changes are not applied until the SMSvc.exe process is restarted).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c1af-123">Na [!INCLUDE[wv](../../../../includes/wv-md.md)] systemów z (Kontrola konta) włączone, lokalnych użytkowników wymagane podniesione uprawnienia, nawet jeśli ich konto jest członkiem grupy Administratorzy.</span><span class="sxs-lookup"><span data-stu-id="9c1af-123">On [!INCLUDE[wv](../../../../includes/wv-md.md)] systems with User Account Control (UAC) enabled, local users require elevated permissions even if their account is a member of the Administrators group.</span></span> <span data-ttu-id="9c1af-124">Aby umożliwić użytkownikom tych użytkowania port udostępnianej usługi bez podniesienia uprawnień, identyfikator SID użytkownika (lub identyfikatora SID grupy, w którym użytkownik jest członkiem), które muszą zostać jawnie dodane do \<allowAccounts > części pliku konfiguracyjnego SMSvcHost.exe.config.</span><span class="sxs-lookup"><span data-stu-id="9c1af-124">To allow these users to make use of the port sharing service without elevation, the user's SID (or the SID of a group in which the user is a member) must be explicitly added to the \<allowAccounts> section of SMSvcHost.exe.config.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="9c1af-125">Domyślny plik pliku konfiguracyjnego SMSvcHost.exe.config określa niestandardowy `etwProviderId` zapobiegające śledzenie SMSvcHost.exe od wchodzenia w konflikt ze śledzenia usługi.</span><span class="sxs-lookup"><span data-stu-id="9c1af-125">The default SMSvcHost.exe.config file specifies a custom `etwProviderId` to prevent SMSvcHost.exe tracing from interfering with service traces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c1af-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9c1af-126">See also</span></span>

- [<span data-ttu-id="9c1af-127">\<net.tcp></span><span class="sxs-lookup"><span data-stu-id="9c1af-127">\<net.tcp></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
