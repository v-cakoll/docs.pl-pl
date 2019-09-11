---
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: c12f57d68de870123d92c8a101e2999c24bb988f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855018"
---
# <a name="service"></a><span data-ttu-id="e3e45-101">\<service></span><span class="sxs-lookup"><span data-stu-id="e3e45-101">\<service></span></span>
<span data-ttu-id="e3e45-102">`service` Element zawiera ustawienia dla usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e3e45-102">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="e3e45-103">Zawiera również punkty końcowe, które uwidaczniają usługę.</span><span class="sxs-lookup"><span data-stu-id="e3e45-103">It also contains endpoints that expose the service.</span></span>  
  
<span data-ttu-id="e3e45-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e3e45-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e3e45-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e3e45-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e3e45-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> usług**](services.md)</span><span class="sxs-lookup"><span data-stu-id="e3e45-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="e3e45-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> usługi**</span><span class="sxs-lookup"><span data-stu-id="e3e45-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<service>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3e45-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3e45-108">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3e45-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e3e45-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e3e45-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e3e45-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3e45-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e3e45-111">Attributes</span></span>  
  
|<span data-ttu-id="e3e45-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e3e45-112">Attribute</span></span>|<span data-ttu-id="e3e45-113">Opis</span><span class="sxs-lookup"><span data-stu-id="e3e45-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e3e45-114">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="e3e45-114">behaviorConfiguration</span></span>|<span data-ttu-id="e3e45-115">Ciąg zawierający nazwę zachowania zachowania do użycia w celu utworzenia wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="e3e45-115">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="e3e45-116">Nazwa zachowania musi znajdować się w zakresie, w którym jest zdefiniowana usługa.</span><span class="sxs-lookup"><span data-stu-id="e3e45-116">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="e3e45-117">Wartością domyślną jest ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="e3e45-117">The default value is an empty string.</span></span>|  
|<span data-ttu-id="e3e45-118">nazwa</span><span class="sxs-lookup"><span data-stu-id="e3e45-118">name</span></span>|<span data-ttu-id="e3e45-119">Wymagany atrybut ciągu, który określa typ usługi do wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e3e45-119">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="e3e45-120">To ustawienie musi być równe prawidłowemu typowi.</span><span class="sxs-lookup"><span data-stu-id="e3e45-120">This setting must equate to a valid type.</span></span> <span data-ttu-id="e3e45-121">Format powinien być`Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="e3e45-121">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3e45-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e3e45-122">Child Elements</span></span>  
  
|<span data-ttu-id="e3e45-123">Element</span><span class="sxs-lookup"><span data-stu-id="e3e45-123">Element</span></span>|<span data-ttu-id="e3e45-124">Opis</span><span class="sxs-lookup"><span data-stu-id="e3e45-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3e45-125">\<> punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="e3e45-125">\<endpoint></span></span>](endpoint-element.md)|<span data-ttu-id="e3e45-126">Kolekcja `endpoint` elementów, które uwidaczniają tę usługę.</span><span class="sxs-lookup"><span data-stu-id="e3e45-126">A collection of `endpoint` elements that expose this service.</span></span>|  
|[<span data-ttu-id="e3e45-127">\<host></span><span class="sxs-lookup"><span data-stu-id="e3e45-127">\<host></span></span>](host.md)|<span data-ttu-id="e3e45-128">Określa hosta tego wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="e3e45-128">Specifies the host of this service instance.</span></span> <span data-ttu-id="e3e45-129">Ten element jest typu <xref:System.ServiceModel.Configuration.HostElement>.</span><span class="sxs-lookup"><span data-stu-id="e3e45-129">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e3e45-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e3e45-130">Parent Elements</span></span>  
  
|<span data-ttu-id="e3e45-131">Element</span><span class="sxs-lookup"><span data-stu-id="e3e45-131">Element</span></span>|<span data-ttu-id="e3e45-132">Opis</span><span class="sxs-lookup"><span data-stu-id="e3e45-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3e45-133">\<> usług</span><span class="sxs-lookup"><span data-stu-id="e3e45-133">\<services></span></span>](services.md)|<span data-ttu-id="e3e45-134">Element główny wszystkich elementów konfiguracji WCF.</span><span class="sxs-lookup"><span data-stu-id="e3e45-134">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3e45-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3e45-135">Remarks</span></span>  
 <span data-ttu-id="e3e45-136">Usługi są zdefiniowane w `services` sekcji pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e3e45-136">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="e3e45-137">Zestaw może zawierać dowolną liczbę usług.</span><span class="sxs-lookup"><span data-stu-id="e3e45-137">An assembly can contain any number of services.</span></span> <span data-ttu-id="e3e45-138">Każda usługa ma swoją własną `service` sekcję konfiguracyjną.</span><span class="sxs-lookup"><span data-stu-id="e3e45-138">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="e3e45-139">Ta sekcja i jej zawartość definiują kontrakt usługi, zachowanie i punkty końcowe określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="e3e45-139">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="e3e45-140">`behaviorConfiguration` Element jest również opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e3e45-140">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="e3e45-141">Identyfikuje zachowanie wykorzystywane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="e3e45-141">It identifies the behavior the service uses.</span></span> <span data-ttu-id="e3e45-142">Zachowanie określone w tym atrybucie musi łączyć się z zachowaniem w zakresie w tym samym pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="e3e45-142">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="e3e45-143">Każda usługa ujawnia jeden lub więcej punktów końcowych, które mają własne adresy i powiązania.</span><span class="sxs-lookup"><span data-stu-id="e3e45-143">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="e3e45-144">Wszystkie powiązania używane w pliku konfiguracji muszą być zdefiniowane w zakresie pliku.</span><span class="sxs-lookup"><span data-stu-id="e3e45-144">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="e3e45-145">Powiązanie jest połączone z punktami końcowymi przez kombinację `name` atrybutów `bindingConfiguration`i.</span><span class="sxs-lookup"><span data-stu-id="e3e45-145">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="e3e45-146">Ten `name` atrybut opisuje sekcję, w której jest zdefiniowane powiązanie.</span><span class="sxs-lookup"><span data-stu-id="e3e45-146">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="e3e45-147">Ten `bindingConfiguration` atrybut określa, która konfiguracja w sekcji powiązania jest używana.</span><span class="sxs-lookup"><span data-stu-id="e3e45-147">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="e3e45-148">Sekcja powiązania może definiować kilka konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e3e45-148">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3e45-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="e3e45-149">Example</span></span>  
 <span data-ttu-id="e3e45-150">Jest to przykład konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="e3e45-150">This is an example of a service configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e3e45-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3e45-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceElement>
- [<span data-ttu-id="e3e45-152">Konfigurowanie usług</span><span class="sxs-lookup"><span data-stu-id="e3e45-152">Configuring Services</span></span>](../../../wcf/configuring-services.md)
