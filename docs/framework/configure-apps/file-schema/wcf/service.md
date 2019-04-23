---
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: 68bddc01b02d9885b3f0fc4c2cbc5c3249de03f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197961"
---
# <a name="service"></a><span data-ttu-id="0407d-101">\<service></span><span class="sxs-lookup"><span data-stu-id="0407d-101">\<service></span></span>
<span data-ttu-id="0407d-102">`service` Element zawiera ustawienia usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0407d-102">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="0407d-103">Zawiera ona także punktów końcowych, które udostępniają usługi.</span><span class="sxs-lookup"><span data-stu-id="0407d-103">It also contains endpoints that expose the service.</span></span>  
  
 <span data-ttu-id="0407d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0407d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0407d-105">\<services></span><span class="sxs-lookup"><span data-stu-id="0407d-105">\<services></span></span>  
<span data-ttu-id="0407d-106">\<service></span><span class="sxs-lookup"><span data-stu-id="0407d-106">\<service></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0407d-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="0407d-107">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0407d-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0407d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0407d-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0407d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0407d-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0407d-110">Attributes</span></span>  
  
|<span data-ttu-id="0407d-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0407d-111">Attribute</span></span>|<span data-ttu-id="0407d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="0407d-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0407d-113">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="0407d-113">behaviorConfiguration</span></span>|<span data-ttu-id="0407d-114">Ciąg zawierający nazwę zachowania użytego do utworzenia wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="0407d-114">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="0407d-115">Nazwa zachowania musi być w zakresie w punkcie, który jest zdefiniowany przez usługę.</span><span class="sxs-lookup"><span data-stu-id="0407d-115">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="0407d-116">Wartością domyślną jest ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="0407d-116">The default value is an empty string.</span></span>|  
|<span data-ttu-id="0407d-117">nazwa</span><span class="sxs-lookup"><span data-stu-id="0407d-117">name</span></span>|<span data-ttu-id="0407d-118">Wymagany atrybut ciągu określający typ usługi, należy utworzyć wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="0407d-118">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="0407d-119">To ustawienie musi równoważne do prawidłowego typu.</span><span class="sxs-lookup"><span data-stu-id="0407d-119">This setting must equate to a valid type.</span></span> <span data-ttu-id="0407d-120">Powinna być w formacie `Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="0407d-120">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0407d-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0407d-121">Child Elements</span></span>  
  
|<span data-ttu-id="0407d-122">Element</span><span class="sxs-lookup"><span data-stu-id="0407d-122">Element</span></span>|<span data-ttu-id="0407d-123">Opis</span><span class="sxs-lookup"><span data-stu-id="0407d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0407d-124">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="0407d-124">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)|<span data-ttu-id="0407d-125">Kolekcja `endpoint` elementy, które uwidaczniają tej usługi.</span><span class="sxs-lookup"><span data-stu-id="0407d-125">A collection of `endpoint` elements that expose this service.</span></span>|  
|[<span data-ttu-id="0407d-126">\<host></span><span class="sxs-lookup"><span data-stu-id="0407d-126">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="0407d-127">Określa host to wystąpienie usługi.</span><span class="sxs-lookup"><span data-stu-id="0407d-127">Specifies the host of this service instance.</span></span> <span data-ttu-id="0407d-128">Ten element jest typu <xref:System.ServiceModel.Configuration.HostElement>.</span><span class="sxs-lookup"><span data-stu-id="0407d-128">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0407d-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0407d-129">Parent Elements</span></span>  
  
|<span data-ttu-id="0407d-130">Element</span><span class="sxs-lookup"><span data-stu-id="0407d-130">Element</span></span>|<span data-ttu-id="0407d-131">Opis</span><span class="sxs-lookup"><span data-stu-id="0407d-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0407d-132">\<services></span><span class="sxs-lookup"><span data-stu-id="0407d-132">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|<span data-ttu-id="0407d-133">Element główny wszystkich elementów konfiguracji programu WCF.</span><span class="sxs-lookup"><span data-stu-id="0407d-133">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0407d-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0407d-134">Remarks</span></span>  
 <span data-ttu-id="0407d-135">Usługi są zdefiniowane w `services` sekcję pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0407d-135">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="0407d-136">Zestaw może zawierać dowolną liczbę usług.</span><span class="sxs-lookup"><span data-stu-id="0407d-136">An assembly can contain any number of services.</span></span> <span data-ttu-id="0407d-137">Każda usługa ma swoje własne `service` sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0407d-137">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="0407d-138">W tej sekcji, a jego zawartością definiowanie kontraktu usługi, zachowanie i punktów końcowych określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="0407d-138">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="0407d-139">`behaviorConfiguration` Element jest również opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="0407d-139">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="0407d-140">Identyfikuje zachowanie usługi używa.</span><span class="sxs-lookup"><span data-stu-id="0407d-140">It identifies the behavior the service uses.</span></span> <span data-ttu-id="0407d-141">Zachowanie określone w tym atrybucie należy połączyć zachowania w zakresie tego samego pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0407d-141">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="0407d-142">Każda usługa udostępnia jeden lub więcej punktów końcowych, która ma swój własny adres i powiązanie.</span><span class="sxs-lookup"><span data-stu-id="0407d-142">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="0407d-143">Wszystkie powiązania używane w pliku konfiguracyjnym musi być zdefiniowany w zakresie pliku.</span><span class="sxs-lookup"><span data-stu-id="0407d-143">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="0407d-144">Powiązania są połączone z punktów końcowych za pomocą kombinacji atrybutów `name` i `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="0407d-144">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="0407d-145">`name` Atrybutu w tym artykule opisano sekcji powiązania jest zdefiniowany w.</span><span class="sxs-lookup"><span data-stu-id="0407d-145">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="0407d-146">`bindingConfiguration` Atrybut definiuje konfigurację, która w ramach sekcji powiązania jest używany.</span><span class="sxs-lookup"><span data-stu-id="0407d-146">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="0407d-147">Sekcja powiązania można zdefiniować kilka konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0407d-147">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0407d-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="0407d-148">Example</span></span>  
 <span data-ttu-id="0407d-149">Jest to przykład konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="0407d-149">This is an example of a service configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0407d-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0407d-150">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceElement>
- [<span data-ttu-id="0407d-151">Konfigurowanie usług</span><span class="sxs-lookup"><span data-stu-id="0407d-151">Configuring Services</span></span>](../../../../../docs/framework/wcf/configuring-services.md)
