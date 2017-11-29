---
title: '&lt;add&gt; w &lt;serviceActivations&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5166f7859bb3e914de8313de08427cda9bc06d6f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltserviceactivationsgt"></a><span data-ttu-id="6536a-102">&lt;add&gt; w &lt;serviceActivations&gt;</span><span class="sxs-lookup"><span data-stu-id="6536a-102">&lt;add&gt; of &lt;serviceActivations&gt;</span></span>
<span data-ttu-id="6536a-103">Element konfiguracji, który można zdefiniować ustawienia Aktywacja usług wirtualnych mapowane na Twojej [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] typów usług.</span><span class="sxs-lookup"><span data-stu-id="6536a-103">A configuration element that allows you to define virtual service activation settings that map to your [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service types.</span></span> <span data-ttu-id="6536a-104">Dzięki temu można aktywować usługi hostowane w WAS / usług IIS bez pliku svc.</span><span class="sxs-lookup"><span data-stu-id="6536a-104">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>  
  
 <span data-ttu-id="6536a-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="6536a-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="6536a-106">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="6536a-106">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6536a-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="6536a-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>   
   <serviceActivations>  
      <add factory="String"  
           service="String"/>  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6536a-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6536a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6536a-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6536a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6536a-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6536a-110">Attributes</span></span>  
  
|<span data-ttu-id="6536a-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6536a-111">Attribute</span></span>|<span data-ttu-id="6536a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="6536a-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6536a-113">Fabryka</span><span class="sxs-lookup"><span data-stu-id="6536a-113">factory</span></span>|<span data-ttu-id="6536a-114">Ciąg określający nazwę typu CLR fabryki, która generuje element aktywacji usługi.</span><span class="sxs-lookup"><span data-stu-id="6536a-114">A string that specifies the CLR type name of the factory that generates a service activation element.</span></span>|  
|<span data-ttu-id="6536a-115">usługa</span><span class="sxs-lookup"><span data-stu-id="6536a-115">service</span></span>|<span data-ttu-id="6536a-116">Typ ServiceType, który implementuje usługę (pełna kwalifikowana nazwa typu lub krótkich Typename (gdy jest on umieszczany w folderze App_Code).</span><span class="sxs-lookup"><span data-stu-id="6536a-116">The ServiceType that implements the service (either the full qualified Typename or the short Typename (when it is placed in the App_Code folder).</span></span>|  
|<span data-ttu-id="6536a-117">Element relativeAddress</span><span class="sxs-lookup"><span data-stu-id="6536a-117">relativeAddress</span></span>|<span data-ttu-id="6536a-118">Adres względny w bieżącej aplikacji usług IIS — na przykład "Service.svc".</span><span class="sxs-lookup"><span data-stu-id="6536a-118">The relative address within the current IIS application - for example "Service.svc".</span></span> <span data-ttu-id="6536a-119">Ten adres względny WCF 4.0 musi zawierać jedno z rozszerzeń plików znanych (SVC, .xamlx,...). Nie pliku fizycznego musi istnieć dla relativeUrl</span><span class="sxs-lookup"><span data-stu-id="6536a-119">In WCF 4.0 this relative address has to contain one of the known file extensions (.svc, .xamlx, ...). No physical file has to exist for the relativeUrl</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6536a-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6536a-120">Child Elements</span></span>  
 <span data-ttu-id="6536a-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="6536a-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6536a-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6536a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="6536a-123">Element</span><span class="sxs-lookup"><span data-stu-id="6536a-123">Element</span></span>|<span data-ttu-id="6536a-124">Opis</span><span class="sxs-lookup"><span data-stu-id="6536a-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6536a-125">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="6536a-125">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="6536a-126">Sekcja konfiguracyjna, który opisuje ustawienia aktywacji.</span><span class="sxs-lookup"><span data-stu-id="6536a-126">A configuration section that describes activation settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6536a-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6536a-127">Remarks</span></span>  
 <span data-ttu-id="6536a-128">Poniższy przykład przedstawia sposób konfigurowania ustawień aktywacji w pliku web.config.</span><span class="sxs-lookup"><span data-stu-id="6536a-128">The following example shows how to configure activation settings within your web.config file.</span></span>  
  
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
  
 <span data-ttu-id="6536a-129">Za pomocą tej konfiguracji, można uaktywnić GreetingService bez użycia pliku svc.</span><span class="sxs-lookup"><span data-stu-id="6536a-129">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>  
  
 <span data-ttu-id="6536a-130">Należy pamiętać, że `<serviceHostingEnvironment>` jest konfiguracji na poziomie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6536a-130">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="6536a-131">Należy umieścić `web.config` zawierający konfigurację w katalogu głównym aplikacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="6536a-131">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="6536a-132">Ponadto `serviceHostingEnvironment` jest sekcją dziedziczne machinetoApplication.</span><span class="sxs-lookup"><span data-stu-id="6536a-132">In addition, `serviceHostingEnvironment` is a machinetoApplication inheritable section.</span></span> <span data-ttu-id="6536a-133">Jeśli zarejestrujesz pojedynczą usługę w katalogu głównym komputera każdej usługi w aplikacji będzie dziedziczyć tej usługi.</span><span class="sxs-lookup"><span data-stu-id="6536a-133">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>  
  
 <span data-ttu-id="6536a-134">Aktywacja oparta na konfiguracji obsługuje aktywacji za pośrednictwem protokołu http i innych niż http.</span><span class="sxs-lookup"><span data-stu-id="6536a-134">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="6536a-135">Wymaga to rozszerzenia w relatativeAddress, tj. SVC, xoml lub .xamlx.</span><span class="sxs-lookup"><span data-stu-id="6536a-135">It requires extensions in the relatativeAddress, i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="6536a-136">Należy mapować własne rozszerzenia buildProviders wiedzieć, który następnie umożliwi aktywowania usługi przez dowolnego rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="6536a-136">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="6536a-137">Po konflikt `<serviceActivations>` sekcji zastępuje .svc rejestracji.</span><span class="sxs-lookup"><span data-stu-id="6536a-137">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6536a-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6536a-138">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceActivationElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>
