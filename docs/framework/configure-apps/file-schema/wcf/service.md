---
title: '&lt;service&gt;'
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: e91e04c602fd867e329477015fc0a8354ae26a05
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535011"
---
# <a name="ltservicegt"></a><span data-ttu-id="cd26a-102">&lt;service&gt;</span><span class="sxs-lookup"><span data-stu-id="cd26a-102">&lt;service&gt;</span></span>
<span data-ttu-id="cd26a-103">`service` Element zawiera ustawienia usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="cd26a-103">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="cd26a-104">Zawiera ona także punktów końcowych, które udostępniają usługi.</span><span class="sxs-lookup"><span data-stu-id="cd26a-104">It also contains endpoints that expose the service.</span></span>  
  
 <span data-ttu-id="cd26a-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cd26a-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="cd26a-106">\<services></span><span class="sxs-lookup"><span data-stu-id="cd26a-106">\<services></span></span>  
<span data-ttu-id="cd26a-107">\<service></span><span class="sxs-lookup"><span data-stu-id="cd26a-107">\<service></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd26a-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd26a-108">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd26a-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cd26a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cd26a-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cd26a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd26a-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cd26a-111">Attributes</span></span>  
  
|<span data-ttu-id="cd26a-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cd26a-112">Attribute</span></span>|<span data-ttu-id="cd26a-113">Opis</span><span class="sxs-lookup"><span data-stu-id="cd26a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cd26a-114">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="cd26a-114">behaviorConfiguration</span></span>|<span data-ttu-id="cd26a-115">Ciąg zawierający nazwę zachowania użytego do utworzenia wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="cd26a-115">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="cd26a-116">Nazwa zachowania musi być w zakresie w punkcie, który jest zdefiniowany przez usługę.</span><span class="sxs-lookup"><span data-stu-id="cd26a-116">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="cd26a-117">Wartością domyślną jest ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="cd26a-117">The default value is an empty string.</span></span>|  
|<span data-ttu-id="cd26a-118">nazwa</span><span class="sxs-lookup"><span data-stu-id="cd26a-118">name</span></span>|<span data-ttu-id="cd26a-119">Wymagany atrybut ciągu określający typ usługi, należy utworzyć wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="cd26a-119">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="cd26a-120">To ustawienie musi równoważne do prawidłowego typu.</span><span class="sxs-lookup"><span data-stu-id="cd26a-120">This setting must equate to a valid type.</span></span> <span data-ttu-id="cd26a-121">Powinna być w formacie `Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="cd26a-121">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd26a-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cd26a-122">Child Elements</span></span>  
  
|<span data-ttu-id="cd26a-123">Element</span><span class="sxs-lookup"><span data-stu-id="cd26a-123">Element</span></span>|<span data-ttu-id="cd26a-124">Opis</span><span class="sxs-lookup"><span data-stu-id="cd26a-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd26a-125">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="cd26a-125">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)|<span data-ttu-id="cd26a-126">Kolekcja `endpoint` elementy, które uwidaczniają tej usługi.</span><span class="sxs-lookup"><span data-stu-id="cd26a-126">A collection of `endpoint` elements that expose this service.</span></span>|  
|[<span data-ttu-id="cd26a-127">\<host></span><span class="sxs-lookup"><span data-stu-id="cd26a-127">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="cd26a-128">Określa host to wystąpienie usługi.</span><span class="sxs-lookup"><span data-stu-id="cd26a-128">Specifies the host of this service instance.</span></span> <span data-ttu-id="cd26a-129">Ten element jest typu <xref:System.ServiceModel.Configuration.HostElement>.</span><span class="sxs-lookup"><span data-stu-id="cd26a-129">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cd26a-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cd26a-130">Parent Elements</span></span>  
  
|<span data-ttu-id="cd26a-131">Element</span><span class="sxs-lookup"><span data-stu-id="cd26a-131">Element</span></span>|<span data-ttu-id="cd26a-132">Opis</span><span class="sxs-lookup"><span data-stu-id="cd26a-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd26a-133">\<services></span><span class="sxs-lookup"><span data-stu-id="cd26a-133">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|<span data-ttu-id="cd26a-134">Element główny wszystkich elementów konfiguracji programu WCF.</span><span class="sxs-lookup"><span data-stu-id="cd26a-134">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd26a-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd26a-135">Remarks</span></span>  
 <span data-ttu-id="cd26a-136">Usługi są zdefiniowane w `services` sekcję pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cd26a-136">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="cd26a-137">Zestaw może zawierać dowolną liczbę usług.</span><span class="sxs-lookup"><span data-stu-id="cd26a-137">An assembly can contain any number of services.</span></span> <span data-ttu-id="cd26a-138">Każda usługa ma swoje własne `service` sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cd26a-138">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="cd26a-139">W tej sekcji, a jego zawartością definiowanie kontraktu usługi, zachowanie i punktów końcowych określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="cd26a-139">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="cd26a-140">`behaviorConfiguration` Element jest również opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="cd26a-140">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="cd26a-141">Identyfikuje zachowanie usługi używa.</span><span class="sxs-lookup"><span data-stu-id="cd26a-141">It identifies the behavior the service uses.</span></span> <span data-ttu-id="cd26a-142">Zachowanie określone w tym atrybucie należy połączyć zachowania w zakresie tego samego pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cd26a-142">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="cd26a-143">Każda usługa udostępnia jeden lub więcej punktów końcowych, która ma swój własny adres i powiązanie.</span><span class="sxs-lookup"><span data-stu-id="cd26a-143">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="cd26a-144">Wszystkie powiązania używane w pliku konfiguracyjnym musi być zdefiniowany w zakresie pliku.</span><span class="sxs-lookup"><span data-stu-id="cd26a-144">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="cd26a-145">Powiązania są połączone z punktów końcowych za pomocą kombinacji atrybutów `name` i `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="cd26a-145">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="cd26a-146">`name` Atrybutu w tym artykule opisano sekcji powiązania jest zdefiniowany w.</span><span class="sxs-lookup"><span data-stu-id="cd26a-146">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="cd26a-147">`bindingConfiguration` Atrybut definiuje konfigurację, która w ramach sekcji powiązania jest używany.</span><span class="sxs-lookup"><span data-stu-id="cd26a-147">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="cd26a-148">Sekcja powiązania można zdefiniować kilka konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cd26a-148">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd26a-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="cd26a-149">Example</span></span>  
 <span data-ttu-id="cd26a-150">Jest to przykład konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="cd26a-150">This is an example of a service configuration.</span></span>  
  
```xml  
<service behaviorConfiguration="testChannelBehavior"
         name="HelloWorld">
  <endpoint address="/HelloWorld2/"
            name="test"
            bindingNamespace="http://www.cohowinery.com/"
            binding="basicHttpBinding"
            contract="IHelloWorld" />
</service>
```  
  
## <a name="see-also"></a><span data-ttu-id="cd26a-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd26a-151">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceElement>
- [<span data-ttu-id="cd26a-152">Konfigurowanie usług</span><span class="sxs-lookup"><span data-stu-id="cd26a-152">Configuring Services</span></span>](../../../../../docs/framework/wcf/configuring-services.md)
