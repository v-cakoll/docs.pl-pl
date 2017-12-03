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
ms.openlocfilehash: 0932494e1d64192070db0177c35b4eb03496bebb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-the-nettcp-port-sharing-service"></a><span data-ttu-id="4b930-102">Konfigurowanie usługi współużytkowania portów Net.TCP</span><span class="sxs-lookup"><span data-stu-id="4b930-102">Configuring the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="4b930-103">Hostowanie Samoobsługowe usługom transportu Net.TCP można kontrolować kilka ustawień zaawansowanych, takich jak `ListenBacklog` i `MaxPendingAccepts`, które sterują zachowaniem podstawowej gniazda TCP używany do komunikacji sieciowej.</span><span class="sxs-lookup"><span data-stu-id="4b930-103">Self-hosted services that use the Net.TCP transport can control several advanced settings, such as `ListenBacklog` and `MaxPendingAccepts`, which govern the behavior of the underlying TCP socket used for network communication.</span></span> <span data-ttu-id="4b930-104">Jednak te ustawienia dla każdego gniazda mają zastosowanie tylko na poziomie powiązanie wyłączenie powiązania transportu jest udostępnianie portów, co jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="4b930-104">However, these settings for each socket only apply at the binding level if the transport binding has disabled port sharing, which is enabled by default.</span></span>  
  
 <span data-ttu-id="4b930-105">Po powiązaniu net.tcp umożliwia udostępnianie portów (przez ustawienie `portSharingEnabled =true` w elemencie powiązania transportu), niejawnie umożliwia procesu zewnętrznego (to znaczy SMSvcHost.exe, który obsługuje usługi udostępniania portów Net.TCP) do zarządzania gniazda TCP w jej imieniu.</span><span class="sxs-lookup"><span data-stu-id="4b930-105">When a net.tcp binding enables port sharing (by setting `portSharingEnabled =true` on the transport binding element), it implicitly allows an external process (namely the SMSvcHost.exe, which hosts the Net.TCP Port Sharing Service) to manage the TCP socket on its behalf.</span></span> <span data-ttu-id="4b930-106">Na przykład podczas korzystania z protokołu TCP, określ:</span><span class="sxs-lookup"><span data-stu-id="4b930-106">For example, when using TCP, specify:</span></span>  
  
```xml  
    <tcpTransport   
        portSharingEnabled="true"  
/>  
```  
  
 <span data-ttu-id="4b930-107">Po skonfigurowaniu w ten sposób wszystkie ustawienia gniazda określonej w elemencie powiązania transportu usługi są zignorowany na rzecz gniazda ustawieniami SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="4b930-107">When configured in this way, any socket settings specified on the service's transport binding element are ignored in favor of the socket settings specified by SMSvcHost.exe.</span></span>  
  
 <span data-ttu-id="4b930-108">Aby skonfigurować SMSvcHost.exe, Utwórz plik konfiguracyjny XML o nazwie pliku konfiguracji SmSvcHost.exe.config i umieść go w tym samym katalogu fizycznym jako plik wykonywalny SMSvcHost.exe (na przykład C:\Windows\Microsoft.NET\Framework\v4.5).</span><span class="sxs-lookup"><span data-stu-id="4b930-108">To configure the SMSvcHost.exe, create an XML configuration file named SmSvcHost.exe.config and place it in the same physical directory as the SMSvcHost.exe executable (for example, C:\Windows\Microsoft.NET\Framework\v4.5).</span></span>  
  
 <span data-ttu-id="4b930-109">Poniższy przykład przedstawia przykład pliku konfiguracji SMSvcHost.exe.config, przy użyciu ustawień domyślnych dla wszystkich wartości można skonfigurować określone jawnie.</span><span class="sxs-lookup"><span data-stu-id="4b930-109">The following example illustrates a sample SMSvcHost.exe.config, with the default settings for all configurable values stated explicitly.</span></span>  
  
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
  
## <a name="when-to-modify-smsvchostexeconfig"></a><span data-ttu-id="4b930-110">Podczas modyfikowania pliku konfiguracji SMSvcHost.exe.config</span><span class="sxs-lookup"><span data-stu-id="4b930-110">When to Modify SMSvcHost.exe.config</span></span>  
 <span data-ttu-id="4b930-111">Ogólnie rzecz biorąc ostrożność podczas modyfikowania zawartości pliku pliku konfiguracji SMSvcHost.exe.config, ponieważ wszystkie ustawienia konfiguracji określone w tym pliku wpływ na wszystkie usługi na komputerze, który korzysta z usługi udostępniania portów Net.TCP.</span><span class="sxs-lookup"><span data-stu-id="4b930-111">In general, care should be taken when modifying the contents of the SMSvcHost.exe.config file, because any configuration settings specified in this file affect all of the services on a computer that uses the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="4b930-112">Obejmuje to aplikacje [!INCLUDE[wv](../../../../includes/wv-md.md)] korzystające z funkcji aktywacji TCP usługi aktywacji procesów systemu Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="4b930-112">This includes applications on [!INCLUDE[wv](../../../../includes/wv-md.md)] that use the TCP Activation features of the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="4b930-113">Jednak czasami może być konieczne zmienić konfigurację domyślną dla usługi udostępniania portów Net.TCP.</span><span class="sxs-lookup"><span data-stu-id="4b930-113">However, sometimes you may need to change the default configuration for the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="4b930-114">Na przykład, wartością domyślną dla `maxPendingAccepts` to 4 * liczba procesorów.</span><span class="sxs-lookup"><span data-stu-id="4b930-114">For example, the default value for `maxPendingAccepts` is 4 * number of processors.</span></span> <span data-ttu-id="4b930-115">Serwery obsługujące wiele usług korzystających z Udostępnianie portów może zwiększyć tę wartość, aby osiągnąć maksymalną przepustowość.</span><span class="sxs-lookup"><span data-stu-id="4b930-115">Servers that host a large number of services that use port sharing may increase this value to achieve maximum throughput.</span></span> <span data-ttu-id="4b930-116">Wartość domyślna dla `maxPendingConnections` to 100.</span><span class="sxs-lookup"><span data-stu-id="4b930-116">The default value for `maxPendingConnections` is 100.</span></span> <span data-ttu-id="4b930-117">Należy rozważyć również zwiększenie tej wartości, jeśli istnieje wielu klientów równoczesnych wywoływania usługi i usługa odrzuca połączenia klientów.</span><span class="sxs-lookup"><span data-stu-id="4b930-117">You should consider increasing this value also if there are multiple concurrent clients calling the service and the service is dropping client connections.</span></span>  
  
 <span data-ttu-id="4b930-118">Pliku konfiguracji SMSvcHost.exe.config zawiera także informacje o używanych tożsamości, które mogą spowodować, że proces usługi współużytkowania portów.</span><span class="sxs-lookup"><span data-stu-id="4b930-118">SMSvcHost.exe.config also contains information about the process identities that may make use of the port sharing service.</span></span> <span data-ttu-id="4b930-119">Podczas procesu nawiązanie połączenia usługi, aby korzystać z udostępnionego TCP współużytkowania portów portu, tożsamość procesu łączenia procesu jest sprawdzany względem listy tożsamości, które zezwala korzystanie z usługi współużytkowania portów.</span><span class="sxs-lookup"><span data-stu-id="4b930-119">When a process connects to the port sharing service to make use of a shared TCP port, the process identity of the connecting process is checked against a list of identities that are permitted to make use of the port sharing service.</span></span> <span data-ttu-id="4b930-120">Tymi tożsamościami są określone jako identyfikatory zabezpieczeń (SID) w \<allowAccounts > sekcji pliku pliku konfiguracji SMSvcHost.exe.config.</span><span class="sxs-lookup"><span data-stu-id="4b930-120">These identities are specified as security identifiers (SIDs) in the \<allowAccounts> section of the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="4b930-121">Domyślnie uprawnienia do używania usługi współużytkowania portów otrzymuje do kont systemowych (Usługa lokalna, system lokalny i Usługa sieciowa) oraz członkom grupy Administratorzy.</span><span class="sxs-lookup"><span data-stu-id="4b930-121">By default, permission to use the port sharing service is granted to system accounts (LocalService, LocalSystem, and NetworkService) as well as members of the Administrators group.</span></span> <span data-ttu-id="4b930-122">Aplikacje, które umożliwiają procesu uruchomionego jako tożsamość (na przykład tożsamości użytkownika) do nawiązania połączenia usługi współużytkowania portów należy jawnie dodać odpowiedni identyfikator SID pliku konfiguracji SMSvcHost.exe.config (te zmiany nie zostaną zastosowane do czasu ukończenia procesu SMSvc.exe ponowne uruchomienie).</span><span class="sxs-lookup"><span data-stu-id="4b930-122">Applications that allow a process running as another identity (for example, a user identity) to connect to the port sharing service must explicitly add the appropriate SID to the SMSvcHost.exe.config (these changes are not applied until the SMSvc.exe process is restarted).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b930-123">Na [!INCLUDE[wv](../../../../includes/wv-md.md)] systemów z (Kontrola konta) włączony, lokalnych użytkowników wymagają podniesionych uprawnień, nawet jeśli ich konto jest członkiem grupy Administratorzy.</span><span class="sxs-lookup"><span data-stu-id="4b930-123">On [!INCLUDE[wv](../../../../includes/wv-md.md)] systems with User Account Control (UAC) enabled, local users require elevated permissions even if their account is a member of the Administrators group.</span></span> <span data-ttu-id="4b930-124">Do tych użytkowników umożliwić korzystanie z usługi bez podniesienia uprawnień, identyfikator SID użytkownika (lub identyfikator SID grupy, w którym użytkownik jest członkiem) współużytkowania portów należy jawnie dodać do \<allowAccounts > sekcji pliku konfiguracji SMSvcHost.exe.config.</span><span class="sxs-lookup"><span data-stu-id="4b930-124">To allow these users to make use of the port sharing service without elevation, the user's SID (or the SID of a group in which the user is a member) must be explicitly added to the \<allowAccounts> section of SMSvcHost.exe.config.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="4b930-125">Domyślny plik pliku konfiguracji SMSvcHost.exe.config określa niestandardowy `etwProviderId` zapobiegające śledzenia SMSvcHost.exe zakłócać ślady usługi.</span><span class="sxs-lookup"><span data-stu-id="4b930-125">The default SMSvcHost.exe.config file specifies a custom `etwProviderId` to prevent SMSvcHost.exe tracing from interfering with service traces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b930-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b930-126">See Also</span></span>  
 [<span data-ttu-id="4b930-127">\<NET.TCP ></span><span class="sxs-lookup"><span data-stu-id="4b930-127">\<net.tcp></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
