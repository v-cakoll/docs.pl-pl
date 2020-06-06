---
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: c12f57d68de870123d92c8a101e2999c24bb988f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855018"
---
# \<service>
<span data-ttu-id="5bd31-101">`service`Element zawiera ustawienia dla usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5bd31-101">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="5bd31-102">Zawiera również punkty końcowe, które uwidaczniają usługę.</span><span class="sxs-lookup"><span data-stu-id="5bd31-102">It also contains endpoints that expose the service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<service>**  
  
## <a name="syntax"></a><span data-ttu-id="5bd31-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="5bd31-103">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5bd31-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5bd31-104">Attributes and Elements</span></span>  
 <span data-ttu-id="5bd31-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5bd31-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5bd31-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5bd31-106">Attributes</span></span>  
  
|<span data-ttu-id="5bd31-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5bd31-107">Attribute</span></span>|<span data-ttu-id="5bd31-108">Opis</span><span class="sxs-lookup"><span data-stu-id="5bd31-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5bd31-109">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="5bd31-109">behaviorConfiguration</span></span>|<span data-ttu-id="5bd31-110">Ciąg zawierający nazwę zachowania zachowania do użycia w celu utworzenia wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="5bd31-110">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="5bd31-111">Nazwa zachowania musi znajdować się w zakresie, w którym jest zdefiniowana usługa.</span><span class="sxs-lookup"><span data-stu-id="5bd31-111">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="5bd31-112">Wartością domyślną jest ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="5bd31-112">The default value is an empty string.</span></span>|  
|<span data-ttu-id="5bd31-113">name</span><span class="sxs-lookup"><span data-stu-id="5bd31-113">name</span></span>|<span data-ttu-id="5bd31-114">Wymagany atrybut ciągu, który określa typ usługi do wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="5bd31-114">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="5bd31-115">To ustawienie musi być równe prawidłowemu typowi.</span><span class="sxs-lookup"><span data-stu-id="5bd31-115">This setting must equate to a valid type.</span></span> <span data-ttu-id="5bd31-116">Format powinien być`Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="5bd31-116">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5bd31-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5bd31-117">Child Elements</span></span>  
  
|<span data-ttu-id="5bd31-118">Element</span><span class="sxs-lookup"><span data-stu-id="5bd31-118">Element</span></span>|<span data-ttu-id="5bd31-119">Opis</span><span class="sxs-lookup"><span data-stu-id="5bd31-119">Description</span></span>|  
|-------------|-----------------|  
|[\<endpoint>](endpoint-element.md)|<span data-ttu-id="5bd31-120">Kolekcja `endpoint` elementów, które uwidaczniają tę usługę.</span><span class="sxs-lookup"><span data-stu-id="5bd31-120">A collection of `endpoint` elements that expose this service.</span></span>|  
|[\<host>](host.md)|<span data-ttu-id="5bd31-121">Określa hosta tego wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="5bd31-121">Specifies the host of this service instance.</span></span> <span data-ttu-id="5bd31-122">Ten element jest typu <xref:System.ServiceModel.Configuration.HostElement> .</span><span class="sxs-lookup"><span data-stu-id="5bd31-122">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5bd31-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5bd31-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5bd31-124">Element</span><span class="sxs-lookup"><span data-stu-id="5bd31-124">Element</span></span>|<span data-ttu-id="5bd31-125">Opis</span><span class="sxs-lookup"><span data-stu-id="5bd31-125">Description</span></span>|  
|-------------|-----------------|  
|[\<services>](services.md)|<span data-ttu-id="5bd31-126">Element główny wszystkich elementów konfiguracji WCF.</span><span class="sxs-lookup"><span data-stu-id="5bd31-126">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bd31-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5bd31-127">Remarks</span></span>  
 <span data-ttu-id="5bd31-128">Usługi są zdefiniowane w `services` sekcji pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5bd31-128">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="5bd31-129">Zestaw może zawierać dowolną liczbę usług.</span><span class="sxs-lookup"><span data-stu-id="5bd31-129">An assembly can contain any number of services.</span></span> <span data-ttu-id="5bd31-130">Każda usługa ma swoją własną `service` sekcję konfiguracyjną.</span><span class="sxs-lookup"><span data-stu-id="5bd31-130">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="5bd31-131">Ta sekcja i jej zawartość definiują kontrakt usługi, zachowanie i punkty końcowe określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="5bd31-131">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="5bd31-132">`behaviorConfiguration`Element jest również opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5bd31-132">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="5bd31-133">Identyfikuje zachowanie wykorzystywane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="5bd31-133">It identifies the behavior the service uses.</span></span> <span data-ttu-id="5bd31-134">Zachowanie określone w tym atrybucie musi łączyć się z zachowaniem w zakresie w tym samym pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="5bd31-134">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="5bd31-135">Każda usługa ujawnia jeden lub więcej punktów końcowych, które mają własne adresy i powiązania.</span><span class="sxs-lookup"><span data-stu-id="5bd31-135">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="5bd31-136">Wszystkie powiązania używane w pliku konfiguracji muszą być zdefiniowane w zakresie pliku.</span><span class="sxs-lookup"><span data-stu-id="5bd31-136">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="5bd31-137">Powiązanie jest połączone z punktami końcowymi przez kombinację atrybutów `name` i `bindingConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="5bd31-137">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="5bd31-138">Ten `name` atrybut opisuje sekcję, w której jest zdefiniowane powiązanie.</span><span class="sxs-lookup"><span data-stu-id="5bd31-138">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="5bd31-139">Ten `bindingConfiguration` atrybut określa, która konfiguracja w sekcji powiązania jest używana.</span><span class="sxs-lookup"><span data-stu-id="5bd31-139">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="5bd31-140">Sekcja powiązania może definiować kilka konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5bd31-140">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bd31-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="5bd31-141">Example</span></span>  
 <span data-ttu-id="5bd31-142">Jest to przykład konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="5bd31-142">This is an example of a service configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5bd31-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5bd31-143">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceElement>
- [<span data-ttu-id="5bd31-144">Konfigurowanie usług</span><span class="sxs-lookup"><span data-stu-id="5bd31-144">Configuring Services</span></span>](../../../wcf/configuring-services.md)
