---
title: "&lt;usługi&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 61c8d8451e271e756fce6f83a4f8b8fd4c8b9f77
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltservicegt"></a><span data-ttu-id="3ebd0-102">&lt;usługi&gt;</span><span class="sxs-lookup"><span data-stu-id="3ebd0-102">&lt;service&gt;</span></span>
<span data-ttu-id="3ebd0-103">`service` Element zawiera ustawienia usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3ebd0-103">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="3ebd0-104">Zawiera ona także punkty końcowe, które udostępniają usługi.</span><span class="sxs-lookup"><span data-stu-id="3ebd0-104">It also contains endpoints that expose the service.</span></span>  
  
 <span data-ttu-id="3ebd0-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="3ebd0-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="3ebd0-106">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="3ebd0-106">\<services></span></span>  
<span data-ttu-id="3ebd0-107">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="3ebd0-107">\<service></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ebd0-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ebd0-108">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration=String"  
        name="String"  
</service>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ebd0-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3ebd0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3ebd0-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3ebd0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ebd0-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3ebd0-111">Attributes</span></span>  
  
|<span data-ttu-id="3ebd0-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3ebd0-112">Attribute</span></span>|<span data-ttu-id="3ebd0-113">Opis</span><span class="sxs-lookup"><span data-stu-id="3ebd0-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3ebd0-114">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="3ebd0-114">behaviorConfiguration</span></span>|<span data-ttu-id="3ebd0-115">Ciąg zawierający nazwę zachowania zachowania, które ma być używany do utworzenia wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="3ebd0-115">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="3ebd0-116">Nazwa zachowania musi być w zakresie w punkcie, który usługa została zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="3ebd0-116">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="3ebd0-117">Wartością domyślną jest ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="3ebd0-117">The default value is an empty string.</span></span>|  
|<span data-ttu-id="3ebd0-118">nazwa</span><span class="sxs-lookup"><span data-stu-id="3ebd0-118">name</span></span>|<span data-ttu-id="3ebd0-119">Wymagany atrybut ciągu określający typ usługi zostać utworzone.</span><span class="sxs-lookup"><span data-stu-id="3ebd0-119">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="3ebd0-120">To ustawienie musi są równoważne do prawidłowego typu.</span><span class="sxs-lookup"><span data-stu-id="3ebd0-120">This setting must equate to a valid type.</span></span> <span data-ttu-id="3ebd0-121">Format powinien być`Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="3ebd0-121">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ebd0-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3ebd0-122">Child Elements</span></span>  
  
|<span data-ttu-id="3ebd0-123">Element</span><span class="sxs-lookup"><span data-stu-id="3ebd0-123">Element</span></span>|<span data-ttu-id="3ebd0-124">Opis</span><span class="sxs-lookup"><span data-stu-id="3ebd0-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ebd0-125">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="3ebd0-125">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)|<span data-ttu-id="3ebd0-126">Kolekcja `endpoint` elementy, które udostępniają tej usługi.</span><span class="sxs-lookup"><span data-stu-id="3ebd0-126">A collection of `endpoint` elements that expose this service.</span></span>|  
|[<span data-ttu-id="3ebd0-127">\<host ></span><span class="sxs-lookup"><span data-stu-id="3ebd0-127">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="3ebd0-128">Określa hosta tego wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="3ebd0-128">Specifies the host of this service instance.</span></span> <span data-ttu-id="3ebd0-129">Ten element jest typu <xref:System.ServiceModel.Configuration.HostElement>.</span><span class="sxs-lookup"><span data-stu-id="3ebd0-129">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3ebd0-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3ebd0-130">Parent Elements</span></span>  
  
|<span data-ttu-id="3ebd0-131">Element</span><span class="sxs-lookup"><span data-stu-id="3ebd0-131">Element</span></span>|<span data-ttu-id="3ebd0-132">Opis</span><span class="sxs-lookup"><span data-stu-id="3ebd0-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ebd0-133">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="3ebd0-133">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|<span data-ttu-id="3ebd0-134">Element główny wszystkich elementów konfiguracji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="3ebd0-134">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ebd0-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3ebd0-135">Remarks</span></span>  
 <span data-ttu-id="3ebd0-136">Usługi są zdefiniowane w `services` sekcji pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3ebd0-136">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="3ebd0-137">Zestaw może zawierać dowolną liczbę usług.</span><span class="sxs-lookup"><span data-stu-id="3ebd0-137">An assembly can contain any number of services.</span></span> <span data-ttu-id="3ebd0-138">Każda usługa ma własną `service` sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3ebd0-138">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="3ebd0-139">W tej sekcji i jego zawartości definiowanie kontraktu usługi, zachowania i punkty końcowe określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="3ebd0-139">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="3ebd0-140">`behaviorConfiguration` Element również jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="3ebd0-140">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="3ebd0-141">Identyfikuje zachowanie usługi używa.</span><span class="sxs-lookup"><span data-stu-id="3ebd0-141">It identifies the behavior the service uses.</span></span> <span data-ttu-id="3ebd0-142">Zachowanie określone w tym atrybucie należy połączyć zachowania w zakresie, w tym samym pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3ebd0-142">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="3ebd0-143">Każda usługa przedstawia jeden lub więcej punktów końcowych, które ma swój własny adres i powiązanie.</span><span class="sxs-lookup"><span data-stu-id="3ebd0-143">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="3ebd0-144">Wszystkie powiązania używane w pliku konfiguracji musi być zdefiniowana w zakresie pliku.</span><span class="sxs-lookup"><span data-stu-id="3ebd0-144">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="3ebd0-145">Powiązania są połączone z punktów końcowych za pomocą kombinacji atrybutów `name` i `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="3ebd0-145">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="3ebd0-146">`name` Atrybut opisuje powiązania jest zdefiniowany w sekcji.</span><span class="sxs-lookup"><span data-stu-id="3ebd0-146">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="3ebd0-147">`bindingConfiguration` Atrybut definiuje konfigurację w sekcji binding, która jest używana.</span><span class="sxs-lookup"><span data-stu-id="3ebd0-147">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="3ebd0-148">Powiązania sekcji można określić kilka konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3ebd0-148">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ebd0-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="3ebd0-149">Example</span></span>  
 <span data-ttu-id="3ebd0-150">Jest to przykład konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="3ebd0-150">This is an example of a service configuration.</span></span>  
  
```xml  
<service behaviorConfiguration="testChannelBehavior"   
     name="HelloWorld">  
     <endpoint   
        address="/HelloWorld2/"  
        name="test"  
        bindingNamespace="http://www.cohowinery.com/"  
        binding="basicHttpBinding"  
        contract="IHelloWorld" />  
</service>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ebd0-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ebd0-151">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceElement>  
 [<span data-ttu-id="3ebd0-152">Konfigurowanie usług</span><span class="sxs-lookup"><span data-stu-id="3ebd0-152">Configuring Services</span></span>](../../../../../docs/framework/wcf/configuring-services.md)
