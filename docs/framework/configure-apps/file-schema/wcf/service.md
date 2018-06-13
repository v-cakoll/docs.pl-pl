---
title: '&lt;Usługi&gt;'
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: 6e83e988920d24c6fe7615e40334919caf21652e
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
ms.locfileid: "34059033"
---
# <a name="ltservicegt"></a><span data-ttu-id="e8f2d-102">&lt;Usługi&gt;</span><span class="sxs-lookup"><span data-stu-id="e8f2d-102">&lt;service&gt;</span></span>
<span data-ttu-id="e8f2d-103">`service` Element zawiera ustawienia usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e8f2d-103">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="e8f2d-104">Zawiera ona także punkty końcowe, które udostępniają usługi.</span><span class="sxs-lookup"><span data-stu-id="e8f2d-104">It also contains endpoints that expose the service.</span></span>  
  
 <span data-ttu-id="e8f2d-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e8f2d-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="e8f2d-106">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="e8f2d-106">\<services></span></span>  
<span data-ttu-id="e8f2d-107">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="e8f2d-107">\<service></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8f2d-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8f2d-108">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration=String"  
        name="String">  
</service>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8f2d-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e8f2d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e8f2d-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e8f2d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8f2d-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e8f2d-111">Attributes</span></span>  
  
|<span data-ttu-id="e8f2d-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e8f2d-112">Attribute</span></span>|<span data-ttu-id="e8f2d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="e8f2d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e8f2d-114">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="e8f2d-114">behaviorConfiguration</span></span>|<span data-ttu-id="e8f2d-115">Ciąg zawierający nazwę zachowania zachowania, które ma być używany do utworzenia wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="e8f2d-115">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="e8f2d-116">Nazwa zachowania musi być w zakresie w punkcie, który usługa została zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="e8f2d-116">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="e8f2d-117">Wartością domyślną jest ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="e8f2d-117">The default value is an empty string.</span></span>|  
|<span data-ttu-id="e8f2d-118">nazwa</span><span class="sxs-lookup"><span data-stu-id="e8f2d-118">name</span></span>|<span data-ttu-id="e8f2d-119">Wymagany atrybut ciągu określający typ usługi zostać utworzone.</span><span class="sxs-lookup"><span data-stu-id="e8f2d-119">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="e8f2d-120">To ustawienie musi są równoważne do prawidłowego typu.</span><span class="sxs-lookup"><span data-stu-id="e8f2d-120">This setting must equate to a valid type.</span></span> <span data-ttu-id="e8f2d-121">Format powinien być `Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="e8f2d-121">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e8f2d-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e8f2d-122">Child Elements</span></span>  
  
|<span data-ttu-id="e8f2d-123">Element</span><span class="sxs-lookup"><span data-stu-id="e8f2d-123">Element</span></span>|<span data-ttu-id="e8f2d-124">Opis</span><span class="sxs-lookup"><span data-stu-id="e8f2d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8f2d-125">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="e8f2d-125">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)|<span data-ttu-id="e8f2d-126">Kolekcja `endpoint` elementy, które udostępniają tej usługi.</span><span class="sxs-lookup"><span data-stu-id="e8f2d-126">A collection of `endpoint` elements that expose this service.</span></span>|  
|[<span data-ttu-id="e8f2d-127">\<host ></span><span class="sxs-lookup"><span data-stu-id="e8f2d-127">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="e8f2d-128">Określa hosta tego wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="e8f2d-128">Specifies the host of this service instance.</span></span> <span data-ttu-id="e8f2d-129">Ten element jest typu <xref:System.ServiceModel.Configuration.HostElement>.</span><span class="sxs-lookup"><span data-stu-id="e8f2d-129">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e8f2d-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e8f2d-130">Parent Elements</span></span>  
  
|<span data-ttu-id="e8f2d-131">Element</span><span class="sxs-lookup"><span data-stu-id="e8f2d-131">Element</span></span>|<span data-ttu-id="e8f2d-132">Opis</span><span class="sxs-lookup"><span data-stu-id="e8f2d-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8f2d-133">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="e8f2d-133">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|<span data-ttu-id="e8f2d-134">Element główny wszystkich elementów konfiguracji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="e8f2d-134">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8f2d-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e8f2d-135">Remarks</span></span>  
 <span data-ttu-id="e8f2d-136">Usługi są zdefiniowane w `services` sekcji pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e8f2d-136">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="e8f2d-137">Zestaw może zawierać dowolną liczbę usług.</span><span class="sxs-lookup"><span data-stu-id="e8f2d-137">An assembly can contain any number of services.</span></span> <span data-ttu-id="e8f2d-138">Każda usługa ma własną `service` sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e8f2d-138">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="e8f2d-139">W tej sekcji i jego zawartości definiowanie kontraktu usługi, zachowania i punkty końcowe określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="e8f2d-139">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="e8f2d-140">`behaviorConfiguration` Element również jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="e8f2d-140">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="e8f2d-141">Identyfikuje zachowanie usługi używa.</span><span class="sxs-lookup"><span data-stu-id="e8f2d-141">It identifies the behavior the service uses.</span></span> <span data-ttu-id="e8f2d-142">Zachowanie określone w tym atrybucie należy połączyć zachowania w zakresie, w tym samym pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e8f2d-142">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="e8f2d-143">Każda usługa przedstawia jeden lub więcej punktów końcowych, które ma swój własny adres i powiązanie.</span><span class="sxs-lookup"><span data-stu-id="e8f2d-143">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="e8f2d-144">Wszystkie powiązania używane w pliku konfiguracji musi być zdefiniowana w zakresie pliku.</span><span class="sxs-lookup"><span data-stu-id="e8f2d-144">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="e8f2d-145">Powiązania są połączone z punktów końcowych za pomocą kombinacji atrybutów `name` i `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="e8f2d-145">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="e8f2d-146">`name` Atrybut opisuje powiązania jest zdefiniowany w sekcji.</span><span class="sxs-lookup"><span data-stu-id="e8f2d-146">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="e8f2d-147">`bindingConfiguration` Atrybut definiuje konfigurację w sekcji binding, która jest używana.</span><span class="sxs-lookup"><span data-stu-id="e8f2d-147">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="e8f2d-148">Powiązania sekcji można określić kilka konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e8f2d-148">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8f2d-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="e8f2d-149">Example</span></span>  
 <span data-ttu-id="e8f2d-150">Jest to przykład konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="e8f2d-150">This is an example of a service configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e8f2d-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8f2d-151">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceElement>  
 [<span data-ttu-id="e8f2d-152">Konfigurowanie usług</span><span class="sxs-lookup"><span data-stu-id="e8f2d-152">Configuring Services</span></span>](../../../../../docs/framework/wcf/configuring-services.md)
