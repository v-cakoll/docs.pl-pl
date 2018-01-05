---
title: "Aktywacja oparta na konfiguracji w usługach IIS i WAS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc0e954ae5cadbe7e70cd8a83d3d5841f4e0d142
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="configuration-based-activation-in-iis-and-was"></a><span data-ttu-id="50583-102">Aktywacja oparta na konfiguracji w usługach IIS i WAS</span><span class="sxs-lookup"><span data-stu-id="50583-102">Configuration-Based Activation in IIS and WAS</span></span>
<span data-ttu-id="50583-103">Zwykle odnośnie do hostowania [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi Internet Information Services (IIS) lub usługi aktywacji procesów systemu Windows (WAS), należy podać pliku svc.</span><span class="sxs-lookup"><span data-stu-id="50583-103">Normally when hosting a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service under Internet Information Services (IIS) or Windows Process Activation Service (WAS), you must provide a .svc file.</span></span> <span data-ttu-id="50583-104">W pliku svc zawiera nazwę usługi i opcjonalne niestandardowe usługi fabryka hostów.</span><span class="sxs-lookup"><span data-stu-id="50583-104">The .svc file contains the name of the service and an optional custom service host factory.</span></span> <span data-ttu-id="50583-105">Ten plik dodatkowe zwiększa możliwości zarządzania obciążenia.</span><span class="sxs-lookup"><span data-stu-id="50583-105">This additional file adds manageability overhead.</span></span> <span data-ttu-id="50583-106">Aktywacja oparta na konfiguracji funkcji eliminuje konieczność pliku svc i w związku z tym skojarzone koszty.</span><span class="sxs-lookup"><span data-stu-id="50583-106">The configuration-based activation feature removes the requirement to have a .svc file and therefore the associated overhead.</span></span>  
  
## <a name="configuration-based-activation"></a><span data-ttu-id="50583-107">Aktywacja oparta na konfiguracji</span><span class="sxs-lookup"><span data-stu-id="50583-107">Configuration-Based Activation</span></span>  
 <span data-ttu-id="50583-108">Aktywacja oparta na konfiguracji ma metadane używane do umieszczenia w pliku svc i umieszcza je w pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="50583-108">Configuration-based activation takes the metadata that used to be placed in the .svc file and places it in the Web.config file.</span></span> <span data-ttu-id="50583-109">W ramach <`serviceHostingEnvironment`> istnieje element <`serviceActivations`> elementu.</span><span class="sxs-lookup"><span data-stu-id="50583-109">Within the<`serviceHostingEnvironment`> element there is a <`serviceActivations`> element.</span></span> <span data-ttu-id="50583-110">W ramach <`serviceActivations`> elementu są co najmniej jeden <`add`> elementy, dla każdej usługi hostowanej.</span><span class="sxs-lookup"><span data-stu-id="50583-110">Within the <`serviceActivations`> element are one or more <`add`> elements, one for each hosted service.</span></span> <span data-ttu-id="50583-111"><`add`> Element zawiera atrybuty, które pozwalają na ustawienie adres względny dla typu usługi i fabryki hostów usług lub usługi.</span><span class="sxs-lookup"><span data-stu-id="50583-111">The <`add`> element contains attributes that let you set the relative address for the service and the service type or a service host factory.</span></span> <span data-ttu-id="50583-112">Poniższy przykładowy kod konfiguracji pokazuje, jak jest używany w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="50583-112">The following configuration example code shows how this section is used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50583-113">Każdy <`add`> element musi określać usługi lub atrybut factory.</span><span class="sxs-lookup"><span data-stu-id="50583-113">Each <`add`> element must specify a service or a factory attribute.</span></span> <span data-ttu-id="50583-114">Określenie zarówno usługi i fabryki atrybutów jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="50583-114">Specifying both service and factory attributes is allowed.</span></span>  
  
```xml  
<serviceHostingEnvironment>  
  <serviceActivations>  
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>  
  </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
 <span data-ttu-id="50583-115">Z tym w pliku Web.config można umieścić usługi kodu źródłowego w katalogu App_Code aplikacji lub skompilowane zestawu w katalogu Bin aplikacji.</span><span class="sxs-lookup"><span data-stu-id="50583-115">With this in the Web.config file, you can place the service source code in the App_Code directory of the application or a complied assembly in the Bin directory of the application.</span></span>  
  
> [!NOTE]
>  -   <span data-ttu-id="50583-116">Korzystając z aktywację w oparciu o konfiguracji, wbudowanego kodu w plikach SVC nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="50583-116">When using configuration-based activation, inline code in .svc files is not supported.</span></span>  
> -   <span data-ttu-id="50583-117">`relativeAddress` Atrybut musi być ustawiony na adres względny takich jak "\<podkatalogu > / service.svc" lub "~ /\<podrzędne directory/service.svc".</span><span class="sxs-lookup"><span data-stu-id="50583-117">The `relativeAddress` attribute must be set to a relative address such as "\<sub-directory>/service.svc" or "~/\<sub-directory/service.svc".</span></span>  
> -   <span data-ttu-id="50583-118">Wyjątek konfiguracji jest generowany, jeśli zarejestrujesz adresem względnym, który nie ma znane rozszerzenie skojarzone z programem WCF.</span><span class="sxs-lookup"><span data-stu-id="50583-118">A configuration exception is thrown if you register a relative address that does not have a known extension associated with WCF.</span></span>  
> -   <span data-ttu-id="50583-119">Podany adres względny jest względem katalogu głównego aplikacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="50583-119">The relative address specified is relative to the root of the virtual application.</span></span>  
> -   <span data-ttu-id="50583-120">Z powodu hierarchiczny model konfiguracji względne adresy zarejestrowane na poziomie maszyny i lokacji są dziedziczone przez aplikacje wirtualne.</span><span class="sxs-lookup"><span data-stu-id="50583-120">Due to the hierarchical model of configuration, the registered relative addresses at machine and site level are inherited by virtual applications.</span></span>  
> -   <span data-ttu-id="50583-121">Rejestracje w pliku konfiguracji mają pierwszeństwo przed ustawienia w SVC, .xamlx, xoml lub innego pliku.</span><span class="sxs-lookup"><span data-stu-id="50583-121">Registrations in a configuration file take precedence over settings in a .svc, .xamlx, .xoml, or other file.</span></span>  
> -   <span data-ttu-id="50583-122">Wszelkie "\" (Używanie ukośników odwrotnych) w identyfikatorze URI wysyłane do usług IIS / WAS automatycznie są konwertowane na "/" (ukośnik).</span><span class="sxs-lookup"><span data-stu-id="50583-122">Any ‘\’ (backslashes) in a URI sent to IIS/WAS are automatically converted to a ‘/’ (forward slash).</span></span> <span data-ttu-id="50583-123">Jeśli adres względny zostanie dodany, który zawiera "\" i wysyłanie IIS identyfikator URI, który używa adres względny, kreska ułamkowa odwrócona jest konwertowana na ukośnik, oraz usług IIS nie może być zgodny z jego adres względny.</span><span class="sxs-lookup"><span data-stu-id="50583-123">If a relative address is added that contains a ‘\’ and you send IIS a URI that uses the relative address, the backslash is converted to a forward slash and IIS cannot match it to the relative address.</span></span> <span data-ttu-id="50583-124">Usługi IIS wysyła informacje o śledzeniu, która wskazuje, że nie ma żadnych dopasowań.</span><span class="sxs-lookup"><span data-stu-id="50583-124">IIS sends out trace information that indicates that there are no matches found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50583-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50583-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>  
 [<span data-ttu-id="50583-126">Usługi hostingowe</span><span class="sxs-lookup"><span data-stu-id="50583-126">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="50583-127">Przegląd hostowania usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="50583-127">Hosting Workflow Services Overview</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 [<span data-ttu-id="50583-128">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="50583-128">\<serviceHostingEnvironment></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)  
 [<span data-ttu-id="50583-129">Windows Server AppFabric funkcje hostingu</span><span class="sxs-lookup"><span data-stu-id="50583-129">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
