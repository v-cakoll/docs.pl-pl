---
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: 69f3c70514fc2bcab1b4ef6a45036de98d1af7b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936527"
---
# <a name="service"></a><span data-ttu-id="e6212-101">\<service></span><span class="sxs-lookup"><span data-stu-id="e6212-101">\<service></span></span>
<span data-ttu-id="e6212-102">`service` Element zawiera ustawienia dla usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e6212-102">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="e6212-103">Zawiera również punkty końcowe, które uwidaczniają usługę.</span><span class="sxs-lookup"><span data-stu-id="e6212-103">It also contains endpoints that expose the service.</span></span>  
  
 <span data-ttu-id="e6212-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e6212-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e6212-105">\<> usług</span><span class="sxs-lookup"><span data-stu-id="e6212-105">\<services></span></span>  
<span data-ttu-id="e6212-106">\<service></span><span class="sxs-lookup"><span data-stu-id="e6212-106">\<service></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6212-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e6212-107">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6212-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e6212-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e6212-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e6212-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6212-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e6212-110">Attributes</span></span>  
  
|<span data-ttu-id="e6212-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e6212-111">Attribute</span></span>|<span data-ttu-id="e6212-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e6212-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e6212-113">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="e6212-113">behaviorConfiguration</span></span>|<span data-ttu-id="e6212-114">Ciąg zawierający nazwę zachowania zachowania do użycia w celu utworzenia wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="e6212-114">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="e6212-115">Nazwa zachowania musi znajdować się w zakresie, w którym jest zdefiniowana usługa.</span><span class="sxs-lookup"><span data-stu-id="e6212-115">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="e6212-116">Wartością domyślną jest ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="e6212-116">The default value is an empty string.</span></span>|  
|<span data-ttu-id="e6212-117">nazwa</span><span class="sxs-lookup"><span data-stu-id="e6212-117">name</span></span>|<span data-ttu-id="e6212-118">Wymagany atrybut ciągu, który określa typ usługi do wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e6212-118">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="e6212-119">To ustawienie musi być równe prawidłowemu typowi.</span><span class="sxs-lookup"><span data-stu-id="e6212-119">This setting must equate to a valid type.</span></span> <span data-ttu-id="e6212-120">Format powinien być`Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="e6212-120">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6212-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e6212-121">Child Elements</span></span>  
  
|<span data-ttu-id="e6212-122">Element</span><span class="sxs-lookup"><span data-stu-id="e6212-122">Element</span></span>|<span data-ttu-id="e6212-123">Opis</span><span class="sxs-lookup"><span data-stu-id="e6212-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6212-124">\<> punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="e6212-124">\<endpoint></span></span>](endpoint-element.md)|<span data-ttu-id="e6212-125">Kolekcja `endpoint` elementów, które uwidaczniają tę usługę.</span><span class="sxs-lookup"><span data-stu-id="e6212-125">A collection of `endpoint` elements that expose this service.</span></span>|  
|[<span data-ttu-id="e6212-126">\<host></span><span class="sxs-lookup"><span data-stu-id="e6212-126">\<host></span></span>](host.md)|<span data-ttu-id="e6212-127">Określa hosta tego wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="e6212-127">Specifies the host of this service instance.</span></span> <span data-ttu-id="e6212-128">Ten element jest typu <xref:System.ServiceModel.Configuration.HostElement>.</span><span class="sxs-lookup"><span data-stu-id="e6212-128">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e6212-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e6212-129">Parent Elements</span></span>  
  
|<span data-ttu-id="e6212-130">Element</span><span class="sxs-lookup"><span data-stu-id="e6212-130">Element</span></span>|<span data-ttu-id="e6212-131">Opis</span><span class="sxs-lookup"><span data-stu-id="e6212-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6212-132">\<> usług</span><span class="sxs-lookup"><span data-stu-id="e6212-132">\<services></span></span>](services.md)|<span data-ttu-id="e6212-133">Element główny wszystkich elementów konfiguracji WCF.</span><span class="sxs-lookup"><span data-stu-id="e6212-133">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6212-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e6212-134">Remarks</span></span>  
 <span data-ttu-id="e6212-135">Usługi są zdefiniowane w `services` sekcji pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e6212-135">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="e6212-136">Zestaw może zawierać dowolną liczbę usług.</span><span class="sxs-lookup"><span data-stu-id="e6212-136">An assembly can contain any number of services.</span></span> <span data-ttu-id="e6212-137">Każda usługa ma swoją własną `service` sekcję konfiguracyjną.</span><span class="sxs-lookup"><span data-stu-id="e6212-137">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="e6212-138">Ta sekcja i jej zawartość definiują kontrakt usługi, zachowanie i punkty końcowe określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="e6212-138">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="e6212-139">`behaviorConfiguration` Element jest również opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e6212-139">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="e6212-140">Identyfikuje zachowanie wykorzystywane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="e6212-140">It identifies the behavior the service uses.</span></span> <span data-ttu-id="e6212-141">Zachowanie określone w tym atrybucie musi łączyć się z zachowaniem w zakresie w tym samym pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="e6212-141">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="e6212-142">Każda usługa ujawnia jeden lub więcej punktów końcowych, które mają własne adresy i powiązania.</span><span class="sxs-lookup"><span data-stu-id="e6212-142">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="e6212-143">Wszystkie powiązania używane w pliku konfiguracji muszą być zdefiniowane w zakresie pliku.</span><span class="sxs-lookup"><span data-stu-id="e6212-143">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="e6212-144">Powiązanie jest połączone z punktami końcowymi przez kombinację `name` atrybutów `bindingConfiguration`i.</span><span class="sxs-lookup"><span data-stu-id="e6212-144">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="e6212-145">Ten `name` atrybut opisuje sekcję, w której jest zdefiniowane powiązanie.</span><span class="sxs-lookup"><span data-stu-id="e6212-145">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="e6212-146">Ten `bindingConfiguration` atrybut określa, która konfiguracja w sekcji powiązania jest używana.</span><span class="sxs-lookup"><span data-stu-id="e6212-146">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="e6212-147">Sekcja powiązania może definiować kilka konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e6212-147">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6212-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="e6212-148">Example</span></span>  
 <span data-ttu-id="e6212-149">Jest to przykład konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="e6212-149">This is an example of a service configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e6212-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6212-150">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceElement>
- [<span data-ttu-id="e6212-151">Konfigurowanie usług</span><span class="sxs-lookup"><span data-stu-id="e6212-151">Configuring Services</span></span>](../../../wcf/configuring-services.md)
