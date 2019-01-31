---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: 7a091ecfbc0f4773ece620f93a9f21c219fcccb6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55256707"
---
# <a name="serviceactivations"></a><span data-ttu-id="e4740-101">\<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="e4740-101">\<serviceActivations></span></span>
<span data-ttu-id="e4740-102">Element konfiguracji, który pozwala Tobie dodać ustawienia, które definiują ustawienia aktywacji usług wirtualnych mapowane odpowiadają typom usług Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e4740-102">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="e4740-103">Dzięki temu można aktywować usługi hostowane w WAS / IIS bez pliku .svc.</span><span class="sxs-lookup"><span data-stu-id="e4740-103">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>  
  
 <span data-ttu-id="e4740-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e4740-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e4740-105">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="e4740-105">\<serviceHostingEnvironment></span></span>  
<span data-ttu-id="e4740-106">\<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="e4740-106">\<serviceActivations></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4740-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e4740-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4740-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e4740-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e4740-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e4740-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4740-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e4740-110">Attributes</span></span>  
 <span data-ttu-id="e4740-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="e4740-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e4740-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e4740-112">Child Elements</span></span>  
  
|<span data-ttu-id="e4740-113">Element</span><span class="sxs-lookup"><span data-stu-id="e4740-113">Element</span></span>|<span data-ttu-id="e4740-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e4740-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4740-115">\<add></span><span class="sxs-lookup"><span data-stu-id="e4740-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-serviceactivations.md)|<span data-ttu-id="e4740-116">Dodaje element konfiguracji, który określa aktywacji aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="e4740-116">Adds a configuration element that specifies the activation of a service application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e4740-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e4740-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e4740-118">Element</span><span class="sxs-lookup"><span data-stu-id="e4740-118">Element</span></span>|<span data-ttu-id="e4740-119">Opis</span><span class="sxs-lookup"><span data-stu-id="e4740-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4740-120">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="e4740-120">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="e4740-121">Definiuje typ, który usługę hostingu środowiskowego dla danego transportu.</span><span class="sxs-lookup"><span data-stu-id="e4740-121">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4740-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e4740-122">Remarks</span></span>  
 <span data-ttu-id="e4740-123">Poniższy przykład pokazuje, jak skonfigurować ustawienia aktywacji w pliku web.config.</span><span class="sxs-lookup"><span data-stu-id="e4740-123">The following example shows how to configure activation settings within your web.config file.</span></span>  
  
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
  
 <span data-ttu-id="e4740-124">Za pomocą tej konfiguracji, możesz aktywować GreetingService bez użycia pliku .svc.</span><span class="sxs-lookup"><span data-stu-id="e4740-124">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>  
  
 <span data-ttu-id="e4740-125">Należy pamiętać, że `<serviceHostingEnvironment>` jest konfiguracji na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e4740-125">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="e4740-126">Musisz umieszczać `web.config` zawierający konfigurację w katalogu głównym aplikacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="e4740-126">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="e4740-127">Ponadto `serviceHostingEnvironment` to sekcja dziedziczne machinetoApplication.</span><span class="sxs-lookup"><span data-stu-id="e4740-127">In addition, `serviceHostingEnvironment` is a machinetoApplication inheritable section.</span></span> <span data-ttu-id="e4740-128">Jeśli zarejestrujesz jednej usługi w katalogu głównym maszyny do każdej usługi w aplikacji będą dziedziczyć tę usługę.</span><span class="sxs-lookup"><span data-stu-id="e4740-128">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>  
  
 <span data-ttu-id="e4740-129">Aktywacja oparta na konfiguracji obsługuje aktywacji za pośrednictwem protokołu http i innych niż http.</span><span class="sxs-lookup"><span data-stu-id="e4740-129">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="e4740-130">Wymaga rozszerzenia w relatativeAddress, czyli .svc xoml oraz .xamlx.</span><span class="sxs-lookup"><span data-stu-id="e4740-130">It requires extensions in the relatativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="e4740-131">Własne rozszerzenia można zamapować na buildProviders wie, który następnie umożliwi Aktywuj usługę za pośrednictwem dowolnego rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="e4740-131">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="e4740-132">Po konfliktu `<serviceActivations>` sekcji zastępuje .svc rejestracji.</span><span class="sxs-lookup"><span data-stu-id="e4740-132">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4740-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4740-133">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
