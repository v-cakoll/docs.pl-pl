---
title: <endpoint>, element
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: 667086cda010daf51cb92116d636b9b526b4b34b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163413"
---
# <a name="endpoint-element"></a><span data-ttu-id="3fb4e-102">\<punkt końcowy > element</span><span class="sxs-lookup"><span data-stu-id="3fb4e-102">\<endpoint> element</span></span>
<span data-ttu-id="3fb4e-103">Określa powiązanie, kontrakt i właściwości adresu punktu końcowego usługi, który jest używany do udostępnienia usług.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-103">Specifies binding, contract, and address properties for a service endpoint, which is used to expose services.</span></span>  
  
 <span data-ttu-id="3fb4e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3fb4e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3fb4e-105">\<service></span><span class="sxs-lookup"><span data-stu-id="3fb4e-105">\<service></span></span>  
<span data-ttu-id="3fb4e-106">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="3fb4e-106">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fb4e-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="3fb4e-107">Syntax</span></span>  
  
```xml  
<endpoint address="String"
          behaviorConfiguration="String"
          binding="String"
          bindingConfiguration="String"
          bindingName="String"
          bindingNamespace="String"
          contract="String"
          endpointConfiguration="String"
          isSystemEndpoint="Boolean"
          kind="String"
          listenUriMode="Explicit/Unique"
          listenUri="Uri">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3fb4e-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3fb4e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3fb4e-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3fb4e-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3fb4e-110">Attributes</span></span>  
  
|<span data-ttu-id="3fb4e-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3fb4e-111">Attribute</span></span>|<span data-ttu-id="3fb4e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="3fb4e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3fb4e-113">adres</span><span class="sxs-lookup"><span data-stu-id="3fb4e-113">address</span></span>|<span data-ttu-id="3fb4e-114">Ciąg, który zawiera adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-114">A string that contains the address of the endpoint.</span></span> <span data-ttu-id="3fb4e-115">Adres można określić jako bezwzględny lub względny adres.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-115">The address can be specified as an absolute or relative address.</span></span> <span data-ttu-id="3fb4e-116">Jeśli nie podano adresu względnego, host powinien zapewniać odpowiedni dla używany w wiązaniu schemat transportu adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-116">If a relative address is provided, the host is expected to provide a base address appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="3fb4e-117">Jeśli adres nie jest skonfigurowany, adres bazowy zakłada się, że adres dla tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-117">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span><br /><br /> <span data-ttu-id="3fb4e-118">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="3fb4e-119">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="3fb4e-119">behaviorConfiguration</span></span>|<span data-ttu-id="3fb4e-120">Ciąg zawierający nazwę zachowania użytego w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-120">A string that contains the name of the behavior to be used in the endpoint.</span></span>|  
|<span data-ttu-id="3fb4e-121">powiązanie</span><span class="sxs-lookup"><span data-stu-id="3fb4e-121">binding</span></span>|<span data-ttu-id="3fb4e-122">Wymagany atrybut ciągu określający typ powiązania do użycia.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-122">Required string attribute that specifies the type of binding to use.</span></span> <span data-ttu-id="3fb4e-123">Typ musi mieć sekcję zarejestrowanych konfiguracji, aby odwoływać się.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-123">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="3fb4e-124">Typ jest zarejestrowaną nazwę sekcji, a nie nazwa typu powiązania.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-124">The type is the registered by section name, rather than by the type name of the binding.</span></span>|  
|<span data-ttu-id="3fb4e-125">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="3fb4e-125">bindingConfiguration</span></span>|<span data-ttu-id="3fb4e-126">Ciąg określający nazwę powiązania w celu użycia podczas tworzenia wystąpienia punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-126">A string that specifies the binding name of the binding to use when the endpoint is instantiated.</span></span> <span data-ttu-id="3fb4e-127">Nazwa powiązania musi być w zakresie w punkcie, który jest zdefiniowany punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-127">The binding name must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="3fb4e-128">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-128">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="3fb4e-129">Ten atrybut jest używany w połączeniu z `binding` można odwoływać się do konfiguracji powiązania określone w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-129">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="3fb4e-130">Ustaw ten atrybut, jeśli chcesz użyć niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-130">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="3fb4e-131">W przeciwnym razie może być wyjątek.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-131">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="3fb4e-132">bindingName</span><span class="sxs-lookup"><span data-stu-id="3fb4e-132">bindingName</span></span>|<span data-ttu-id="3fb4e-133">Ciąg określający unikalną kwalifikowaną nazwę powiązania w celu eksportu definicji za pośrednictwem WSDL.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-133">A string that specifies the unique qualified name of the binding for definition export through WSDL.</span></span> <span data-ttu-id="3fb4e-134">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-134">The default is an empty string.</span></span>|  
|<span data-ttu-id="3fb4e-135">bindingNamespace</span><span class="sxs-lookup"><span data-stu-id="3fb4e-135">bindingNamespace</span></span>|<span data-ttu-id="3fb4e-136">Ciąg określający kwalifikowaną nazwę przestrzeni nazw powiązania dla definicji eksportowania za pośrednictwem WSDL.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-136">A string that specifies the qualified name of the namespace of the binding for definition export through WSDL.</span></span> <span data-ttu-id="3fb4e-137">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-137">The default is an empty string.</span></span>|  
|<span data-ttu-id="3fb4e-138">kontrakt</span><span class="sxs-lookup"><span data-stu-id="3fb4e-138">contract</span></span>|<span data-ttu-id="3fb4e-139">Ciąg wskazujący, który kontrakt tego punktu końcowego jest uwidaczniany.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-139">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="3fb4e-140">Zestaw musi implementować typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-140">The assembly must implement the contract type.</span></span> <span data-ttu-id="3fb4e-141">Jeśli implementacji usługi implementuje typ kontraktu pojedynczego, tej właściwości można pominąć.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-141">If a service implementation implements a single contract type, then this property can be omitted.</span></span> <span data-ttu-id="3fb4e-142">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-142">The default is an empty string.</span></span>|  
|<span data-ttu-id="3fb4e-143">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="3fb4e-143">endpointConfiguration</span></span>|<span data-ttu-id="3fb4e-144">Ciąg określający nazwę standardowego punktu końcowego, który jest uporządkowany według `kind` atrybut, który odwołuje się do informacji dodatkowej konfiguracji tego standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-144">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="3fb4e-145">Taką samą nazwę muszą być zdefiniowane w `<standardEndpoints>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-145">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="3fb4e-146">isSystemEndpoint</span><span class="sxs-lookup"><span data-stu-id="3fb4e-146">isSystemEndpoint</span></span>|<span data-ttu-id="3fb4e-147">Wartość logiczna określająca, czy punkt końcowy jest punktem końcowym infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-147">A Boolean value that specifies whether an endpoint is an infrastructure endpoint.</span></span>|  
|<span data-ttu-id="3fb4e-148">rodzaj</span><span class="sxs-lookup"><span data-stu-id="3fb4e-148">kind</span></span>|<span data-ttu-id="3fb4e-149">Ciąg określający typ stosowanego standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-149">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="3fb4e-150">Typ musi być zarejestrowana w `<extensions>` sekcji lub w pliku machine.config. Jeśli nic nie zostanie określony, zostanie utworzony wspólnego punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-150">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common service endpoint is created.</span></span>|  
|<span data-ttu-id="3fb4e-151">listenUriMode</span><span class="sxs-lookup"><span data-stu-id="3fb4e-151">listenUriMode</span></span>|<span data-ttu-id="3fb4e-152">Określa, jak warstwa transportu traktuje `ListenUri` określone usługi do nasłuchiwania.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-152">Specifies how the transport treats the `ListenUri` provided for the service to listen on.</span></span> <span data-ttu-id="3fb4e-153">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="3fb4e-153">Valid values are</span></span><br /><br /> <span data-ttu-id="3fb4e-154">-Jawne</span><span class="sxs-lookup"><span data-stu-id="3fb4e-154">-   Explicit</span></span><br /><span data-ttu-id="3fb4e-155">— Unikatowe</span><span class="sxs-lookup"><span data-stu-id="3fb4e-155">-   Unique</span></span><br /><br /> <span data-ttu-id="3fb4e-156">Wartość domyślna to jawne.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-156">The default value is Explicit.</span></span>|  
|<span data-ttu-id="3fb4e-157">listenUri</span><span class="sxs-lookup"><span data-stu-id="3fb4e-157">listenUri</span></span>|<span data-ttu-id="3fb4e-158">Ciąg określający URI, na którym nasłuchuje punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-158">A string that specifies the URI at which the service endpoint listens.</span></span> <span data-ttu-id="3fb4e-159">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-159">The default is an empty string.</span></span>|  
|<span data-ttu-id="3fb4e-160">nazwa</span><span class="sxs-lookup"><span data-stu-id="3fb4e-160">name</span></span>|<span data-ttu-id="3fb4e-161">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-161">Optional attribute.</span></span> <span data-ttu-id="3fb4e-162">Ciąg określający nazwę punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-162">A string that specifies the name the service endpoint.</span></span> <span data-ttu-id="3fb4e-163">Wartość domyślna to łączenie nazwę i opis nazwy kontraktu.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-163">The default value is the concatenation of the binding name and the contract description name.</span></span> <span data-ttu-id="3fb4e-164">Usługi mogą mieć wiele punktów końcowych, więc punktu końcowego `name` atrybut różni się od nazwy usługi.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-164">Services may have multiple endpoints, so the endpoint’s `name` attribute is distinct from the name of the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3fb4e-165">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3fb4e-165">Child Elements</span></span>  
  
|<span data-ttu-id="3fb4e-166">Element</span><span class="sxs-lookup"><span data-stu-id="3fb4e-166">Element</span></span>|<span data-ttu-id="3fb4e-167">Opis</span><span class="sxs-lookup"><span data-stu-id="3fb4e-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3fb4e-168">\<headers></span><span class="sxs-lookup"><span data-stu-id="3fb4e-168">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="3fb4e-169">Kolekcję nagłówków adresowych.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-169">A collection of address headers.</span></span>|  
|[<span data-ttu-id="3fb4e-170">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="3fb4e-170">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="3fb4e-171">Tożsamość, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe, wymiana wiadomości z nim.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-171">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3fb4e-172">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3fb4e-172">Parent Elements</span></span>  
  
|<span data-ttu-id="3fb4e-173">Element</span><span class="sxs-lookup"><span data-stu-id="3fb4e-173">Element</span></span>|<span data-ttu-id="3fb4e-174">Opis</span><span class="sxs-lookup"><span data-stu-id="3fb4e-174">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3fb4e-175">\<service></span><span class="sxs-lookup"><span data-stu-id="3fb4e-175">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="3fb4e-176">Sekcja konfiguracji, który definiuje listę punktów końcowych, które klient może połączyć się z.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-176">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3fb4e-177">Przykład</span><span class="sxs-lookup"><span data-stu-id="3fb4e-177">Example</span></span>  
 <span data-ttu-id="3fb4e-178">Jest to przykład konfiguracji punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="3fb4e-178">This is an example of a service endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          bindingName="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
  <headers>
    <region xmlns="http://tempuri.org/">EastCoast</region>
    <member xmlns="http://tempuri.org/">Gold</member>
  </headers>
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="3fb4e-179">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3fb4e-179">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [<span data-ttu-id="3fb4e-180">Punkty końcowe: Adresy, powiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="3fb4e-180">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="3fb4e-181">Instrukcje: Tworzenie punktu końcowego usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="3fb4e-181">How to: Create a Service Endpoint in Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
