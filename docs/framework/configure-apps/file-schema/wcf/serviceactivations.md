---
title: '&lt;serviceActivations&gt;'
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: 5da05c7b6a9685b9e34b3181ce8e0bd31ccd052b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704959"
---
# <a name="ltserviceactivationsgt"></a><span data-ttu-id="1719b-102">&lt;serviceActivations&gt;</span><span class="sxs-lookup"><span data-stu-id="1719b-102">&lt;serviceActivations&gt;</span></span>
<span data-ttu-id="1719b-103">Element konfiguracji, który pozwala Tobie dodać ustawienia, które definiują ustawienia aktywacji usług wirtualnych mapowane odpowiadają typom usług Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1719b-103">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="1719b-104">Dzięki temu można aktywować usługi hostowane w WAS / IIS bez pliku .svc.</span><span class="sxs-lookup"><span data-stu-id="1719b-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>  
  
 <span data-ttu-id="1719b-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1719b-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="1719b-106">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="1719b-106">\<serviceHostingEnvironment></span></span>  
<span data-ttu-id="1719b-107">\<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="1719b-107">\<serviceActivations></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1719b-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="1719b-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1719b-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1719b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1719b-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1719b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1719b-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1719b-111">Attributes</span></span>  
 <span data-ttu-id="1719b-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="1719b-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1719b-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1719b-113">Child Elements</span></span>  
  
|<span data-ttu-id="1719b-114">Element</span><span class="sxs-lookup"><span data-stu-id="1719b-114">Element</span></span>|<span data-ttu-id="1719b-115">Opis</span><span class="sxs-lookup"><span data-stu-id="1719b-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1719b-116">\<add></span><span class="sxs-lookup"><span data-stu-id="1719b-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-serviceactivations.md)|<span data-ttu-id="1719b-117">Dodaje element konfiguracji, który określa aktywacji aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="1719b-117">Adds a configuration element that specifies the activation of a service application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1719b-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1719b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="1719b-119">Element</span><span class="sxs-lookup"><span data-stu-id="1719b-119">Element</span></span>|<span data-ttu-id="1719b-120">Opis</span><span class="sxs-lookup"><span data-stu-id="1719b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1719b-121">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="1719b-121">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="1719b-122">Definiuje typ, który usługę hostingu środowiskowego dla danego transportu.</span><span class="sxs-lookup"><span data-stu-id="1719b-122">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1719b-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1719b-123">Remarks</span></span>  
 <span data-ttu-id="1719b-124">Poniższy przykład pokazuje, jak skonfigurować ustawienia aktywacji w pliku web.config.</span><span class="sxs-lookup"><span data-stu-id="1719b-124">The following example shows how to configure activation settings within your web.config file.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <serviceHostingEnvironment>
      <serviceActivations>
        <add service="GreetingService" />
      </serviceActivations>
    </serviceHostingEnvironment>
  </system.serviceModel>
</configuration>
```  
  
 <span data-ttu-id="1719b-125">Za pomocą tej konfiguracji, możesz aktywować GreetingService bez użycia pliku .svc.</span><span class="sxs-lookup"><span data-stu-id="1719b-125">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>  
  
 <span data-ttu-id="1719b-126">Należy pamiętać, że `<serviceHostingEnvironment>` jest konfiguracji na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1719b-126">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="1719b-127">Musisz umieszczać `web.config` zawierający konfigurację w katalogu głównym aplikacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="1719b-127">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="1719b-128">Ponadto `serviceHostingEnvironment` to sekcja dziedziczne machinetoApplication.</span><span class="sxs-lookup"><span data-stu-id="1719b-128">In addition, `serviceHostingEnvironment` is a machinetoApplication inheritable section.</span></span> <span data-ttu-id="1719b-129">Jeśli zarejestrujesz jednej usługi w katalogu głównym maszyny do każdej usługi w aplikacji będą dziedziczyć tę usługę.</span><span class="sxs-lookup"><span data-stu-id="1719b-129">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>  
  
 <span data-ttu-id="1719b-130">Aktywacja oparta na konfiguracji obsługuje aktywacji za pośrednictwem protokołu http i innych niż http.</span><span class="sxs-lookup"><span data-stu-id="1719b-130">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="1719b-131">Wymaga rozszerzenia w relatativeAddress, czyli .svc xoml oraz .xamlx.</span><span class="sxs-lookup"><span data-stu-id="1719b-131">It requires extensions in the relatativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="1719b-132">Własne rozszerzenia można zamapować na buildProviders wie, który następnie umożliwi Aktywuj usługę za pośrednictwem dowolnego rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="1719b-132">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="1719b-133">Po konfliktu `<serviceActivations>` sekcji zastępuje .svc rejestracji.</span><span class="sxs-lookup"><span data-stu-id="1719b-133">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1719b-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1719b-134">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
