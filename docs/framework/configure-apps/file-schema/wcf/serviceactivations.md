---
title: '&lt;serviceActivations&gt;'
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: c62f2bd1a34aca31ea9f9d5de17840f2967b269c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltserviceactivationsgt"></a><span data-ttu-id="cfff5-102">&lt;serviceActivations&gt;</span><span class="sxs-lookup"><span data-stu-id="cfff5-102">&lt;serviceActivations&gt;</span></span>
<span data-ttu-id="cfff5-103">Element konfiguracji, który umożliwia Tobie dodać ustawienia, które definiują ustawienia aktywacji usług wirtualnych, które odpowiadają typom usług Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="cfff5-103">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="cfff5-104">Dzięki temu można aktywować usługi hostowane w WAS / usług IIS bez pliku svc.</span><span class="sxs-lookup"><span data-stu-id="cfff5-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>  
  
 <span data-ttu-id="cfff5-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cfff5-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="cfff5-106">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="cfff5-106">\<serviceHostingEnvironment></span></span>  
<span data-ttu-id="cfff5-107">\<serviceActivations ></span><span class="sxs-lookup"><span data-stu-id="cfff5-107">\<serviceActivations></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfff5-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="cfff5-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <serviceActivations>  
      <add factory="String"  
           service="String"/>  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cfff5-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cfff5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cfff5-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cfff5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cfff5-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cfff5-111">Attributes</span></span>  
 <span data-ttu-id="cfff5-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="cfff5-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cfff5-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cfff5-113">Child Elements</span></span>  
  
|<span data-ttu-id="cfff5-114">Element</span><span class="sxs-lookup"><span data-stu-id="cfff5-114">Element</span></span>|<span data-ttu-id="cfff5-115">Opis</span><span class="sxs-lookup"><span data-stu-id="cfff5-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cfff5-116">\<add></span><span class="sxs-lookup"><span data-stu-id="cfff5-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-serviceactivations.md)|<span data-ttu-id="cfff5-117">Dodaje element konfiguracji, który określa aktywacji aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="cfff5-117">Adds a configuration element that specifies the activation of a service application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cfff5-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cfff5-118">Parent Elements</span></span>  
  
|<span data-ttu-id="cfff5-119">Element</span><span class="sxs-lookup"><span data-stu-id="cfff5-119">Element</span></span>|<span data-ttu-id="cfff5-120">Opis</span><span class="sxs-lookup"><span data-stu-id="cfff5-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cfff5-121">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="cfff5-121">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="cfff5-122">Definiuje typ, który usługę hostingu środowiskowego dla danego transportu.</span><span class="sxs-lookup"><span data-stu-id="cfff5-122">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfff5-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cfff5-123">Remarks</span></span>  
 <span data-ttu-id="cfff5-124">Poniższy przykład przedstawia sposób konfigurowania ustawień aktywacji w pliku web.config.</span><span class="sxs-lookup"><span data-stu-id="cfff5-124">The following example shows how to configure activation settings within your web.config file.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <serviceHostingEnvironment>  
      <serviceActivations>  
        <add service="GreetingService"/>  
      </serviceActivations>  
    </serviceHostingEnvironment>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="cfff5-125">Za pomocą tej konfiguracji, można uaktywnić GreetingService bez użycia pliku svc.</span><span class="sxs-lookup"><span data-stu-id="cfff5-125">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>  
  
 <span data-ttu-id="cfff5-126">Należy pamiętać, że `<serviceHostingEnvironment>` jest konfiguracji na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cfff5-126">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="cfff5-127">Należy umieścić `web.config` zawierający konfigurację w katalogu głównym aplikacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="cfff5-127">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="cfff5-128">Ponadto `serviceHostingEnvironment` jest sekcją dziedziczne machinetoApplication.</span><span class="sxs-lookup"><span data-stu-id="cfff5-128">In addition, `serviceHostingEnvironment` is a machinetoApplication inheritable section.</span></span> <span data-ttu-id="cfff5-129">Jeśli zarejestrujesz pojedynczą usługę w katalogu głównym komputera każdej usługi w aplikacji będzie dziedziczyć tej usługi.</span><span class="sxs-lookup"><span data-stu-id="cfff5-129">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>  
  
 <span data-ttu-id="cfff5-130">Aktywacja oparta na konfiguracji obsługuje aktywacji za pośrednictwem protokołu http i innych niż http.</span><span class="sxs-lookup"><span data-stu-id="cfff5-130">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="cfff5-131">Wymaga to rozszerzenia w relatativeAddress, tj. SVC, xoml lub .xamlx.</span><span class="sxs-lookup"><span data-stu-id="cfff5-131">It requires extensions in the relatativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="cfff5-132">Należy mapować własne rozszerzenia buildProviders wiedzieć, który następnie umożliwi aktywowania usługi przez dowolnego rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="cfff5-132">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="cfff5-133">Po konflikt `<serviceActivations>` sekcji zastępuje .svc rejestracji.</span><span class="sxs-lookup"><span data-stu-id="cfff5-133">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfff5-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cfff5-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>
