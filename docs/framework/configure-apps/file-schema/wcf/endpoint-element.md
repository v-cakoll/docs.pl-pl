---
title: <endpoint>, element
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: 71ddb3b860870ee8feeeb36c3f64fa7bfebb0f10
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925826"
---
# <a name="endpoint-element"></a><span data-ttu-id="ddc41-102">\<Element > punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="ddc41-102">\<endpoint> element</span></span>
<span data-ttu-id="ddc41-103">Określa powiązanie, kontrakt i właściwości adresu dla punktu końcowego usługi, który jest używany do udostępniania usług.</span><span class="sxs-lookup"><span data-stu-id="ddc41-103">Specifies binding, contract, and address properties for a service endpoint, which is used to expose services.</span></span>  
  
 <span data-ttu-id="ddc41-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ddc41-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ddc41-105">\<service></span><span class="sxs-lookup"><span data-stu-id="ddc41-105">\<service></span></span>  
<span data-ttu-id="ddc41-106">\<> punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="ddc41-106">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddc41-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ddc41-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ddc41-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ddc41-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ddc41-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ddc41-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ddc41-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ddc41-110">Attributes</span></span>  
  
|<span data-ttu-id="ddc41-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ddc41-111">Attribute</span></span>|<span data-ttu-id="ddc41-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ddc41-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ddc41-113">adres</span><span class="sxs-lookup"><span data-stu-id="ddc41-113">address</span></span>|<span data-ttu-id="ddc41-114">Ciąg zawierający adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ddc41-114">A string that contains the address of the endpoint.</span></span> <span data-ttu-id="ddc41-115">Adres może być określony jako adres bezwzględny lub względny.</span><span class="sxs-lookup"><span data-stu-id="ddc41-115">The address can be specified as an absolute or relative address.</span></span> <span data-ttu-id="ddc41-116">Jeśli zostanie podany adres względny, host powinien podać adres podstawowy odpowiedni dla schematu transportu używanego w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="ddc41-116">If a relative address is provided, the host is expected to provide a base address appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="ddc41-117">Jeśli adres nie jest skonfigurowany, zakłada się, że adres podstawowy jest adresem dla tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ddc41-117">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span><br /><br /> <span data-ttu-id="ddc41-118">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="ddc41-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="ddc41-119">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="ddc41-119">behaviorConfiguration</span></span>|<span data-ttu-id="ddc41-120">Ciąg zawierający nazwę zachowania do użycia w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="ddc41-120">A string that contains the name of the behavior to be used in the endpoint.</span></span>|  
|<span data-ttu-id="ddc41-121">powiązanie</span><span class="sxs-lookup"><span data-stu-id="ddc41-121">binding</span></span>|<span data-ttu-id="ddc41-122">Wymagany atrybut ciągu, który określa typ powiązania do użycia.</span><span class="sxs-lookup"><span data-stu-id="ddc41-122">Required string attribute that specifies the type of binding to use.</span></span> <span data-ttu-id="ddc41-123">Aby można było odwołać, typ musi mieć zarejestrowaną sekcję konfiguracyjną.</span><span class="sxs-lookup"><span data-stu-id="ddc41-123">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="ddc41-124">Typ jest typem zarejestrowanym według nazwy sekcji, a nie nazwą typu powiązania.</span><span class="sxs-lookup"><span data-stu-id="ddc41-124">The type is the registered by section name, rather than by the type name of the binding.</span></span>|  
|<span data-ttu-id="ddc41-125">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="ddc41-125">bindingConfiguration</span></span>|<span data-ttu-id="ddc41-126">Ciąg określający nazwę powiązania powiązania do użycia podczas tworzenia wystąpienia punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ddc41-126">A string that specifies the binding name of the binding to use when the endpoint is instantiated.</span></span> <span data-ttu-id="ddc41-127">Nazwa powiązania musi znajdować się w zakresie w punkcie, w którym jest zdefiniowany punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="ddc41-127">The binding name must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="ddc41-128">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="ddc41-128">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="ddc41-129">Ten atrybut jest używany w połączeniu z `binding` programem w celu odwoływania się do określonej konfiguracji powiązań w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ddc41-129">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="ddc41-130">Ustaw ten atrybut, jeśli próbujesz użyć niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="ddc41-130">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="ddc41-131">W przeciwnym razie może zostać zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ddc41-131">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="ddc41-132">powiązaniename</span><span class="sxs-lookup"><span data-stu-id="ddc41-132">bindingName</span></span>|<span data-ttu-id="ddc41-133">Ciąg określający unikalną kwalifikowaną nazwę powiązania w celu eksportu definicji za pomocą WSDL.</span><span class="sxs-lookup"><span data-stu-id="ddc41-133">A string that specifies the unique qualified name of the binding for definition export through WSDL.</span></span> <span data-ttu-id="ddc41-134">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="ddc41-134">The default is an empty string.</span></span>|  
|<span data-ttu-id="ddc41-135">bindingNamespace</span><span class="sxs-lookup"><span data-stu-id="ddc41-135">bindingNamespace</span></span>|<span data-ttu-id="ddc41-136">Ciąg określający kwalifikowaną nazwę przestrzeni nazw powiązania w celu eksportu definicji za pomocą WSDL.</span><span class="sxs-lookup"><span data-stu-id="ddc41-136">A string that specifies the qualified name of the namespace of the binding for definition export through WSDL.</span></span> <span data-ttu-id="ddc41-137">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="ddc41-137">The default is an empty string.</span></span>|  
|<span data-ttu-id="ddc41-138">przedsiębiorc</span><span class="sxs-lookup"><span data-stu-id="ddc41-138">contract</span></span>|<span data-ttu-id="ddc41-139">Ciąg wskazujący, który kontrakt jest ujawniany przez ten punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="ddc41-139">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="ddc41-140">Zestaw musi implementować typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="ddc41-140">The assembly must implement the contract type.</span></span> <span data-ttu-id="ddc41-141">Jeśli implementacja usługi implementuje pojedynczy typ kontraktu, ta właściwość może zostać pominięta.</span><span class="sxs-lookup"><span data-stu-id="ddc41-141">If a service implementation implements a single contract type, then this property can be omitted.</span></span> <span data-ttu-id="ddc41-142">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="ddc41-142">The default is an empty string.</span></span>|  
|<span data-ttu-id="ddc41-143">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="ddc41-143">endpointConfiguration</span></span>|<span data-ttu-id="ddc41-144">Ciąg określający nazwę standardowego punktu końcowego, który jest ustawiany przez `kind` atrybut, który odwołuje się do dodatkowych informacji konfiguracyjnych tego standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ddc41-144">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="ddc41-145">Ta sama nazwa musi być zdefiniowana w `<standardEndpoints>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="ddc41-145">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="ddc41-146">isSystemEndpoint</span><span class="sxs-lookup"><span data-stu-id="ddc41-146">isSystemEndpoint</span></span>|<span data-ttu-id="ddc41-147">Wartość logiczna określająca, czy punkt końcowy jest punktem końcowym infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="ddc41-147">A Boolean value that specifies whether an endpoint is an infrastructure endpoint.</span></span>|  
|<span data-ttu-id="ddc41-148">Natur</span><span class="sxs-lookup"><span data-stu-id="ddc41-148">kind</span></span>|<span data-ttu-id="ddc41-149">Ciąg określający typ stosowanego standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ddc41-149">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="ddc41-150">Typ musi być zarejestrowany w `<extensions>` sekcji lub pliku Machine. config. Jeśli nic nie zostanie określone, tworzony jest wspólny punkt końcowy usługi.</span><span class="sxs-lookup"><span data-stu-id="ddc41-150">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common service endpoint is created.</span></span>|  
|<span data-ttu-id="ddc41-151">listenUriMode</span><span class="sxs-lookup"><span data-stu-id="ddc41-151">listenUriMode</span></span>|<span data-ttu-id="ddc41-152">Określa sposób, w jaki transport `ListenUri` traktuje podany na potrzeby nasłuchiwania usługi.</span><span class="sxs-lookup"><span data-stu-id="ddc41-152">Specifies how the transport treats the `ListenUri` provided for the service to listen on.</span></span> <span data-ttu-id="ddc41-153">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="ddc41-153">Valid values are</span></span><br /><br /> <span data-ttu-id="ddc41-154">-Jawne</span><span class="sxs-lookup"><span data-stu-id="ddc41-154">-   Explicit</span></span><br /><span data-ttu-id="ddc41-155">-Unikatowy</span><span class="sxs-lookup"><span data-stu-id="ddc41-155">-   Unique</span></span><br /><br /> <span data-ttu-id="ddc41-156">Wartość domyślna to explicit.</span><span class="sxs-lookup"><span data-stu-id="ddc41-156">The default value is Explicit.</span></span>|  
|<span data-ttu-id="ddc41-157">listenUri</span><span class="sxs-lookup"><span data-stu-id="ddc41-157">listenUri</span></span>|<span data-ttu-id="ddc41-158">Ciąg określający identyfikator URI, z którego nasłuchuje punkt końcowy usługi.</span><span class="sxs-lookup"><span data-stu-id="ddc41-158">A string that specifies the URI at which the service endpoint listens.</span></span> <span data-ttu-id="ddc41-159">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="ddc41-159">The default is an empty string.</span></span>|  
|<span data-ttu-id="ddc41-160">nazwa</span><span class="sxs-lookup"><span data-stu-id="ddc41-160">name</span></span>|<span data-ttu-id="ddc41-161">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ddc41-161">Optional attribute.</span></span> <span data-ttu-id="ddc41-162">Ciąg określający nazwę punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="ddc41-162">A string that specifies the name the service endpoint.</span></span> <span data-ttu-id="ddc41-163">Wartość domyślna to połączenie nazwy powiązania i nazwy opisu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="ddc41-163">The default value is the concatenation of the binding name and the contract description name.</span></span> <span data-ttu-id="ddc41-164">Usługi mogą mieć wiele punktów końcowych, więc `name` atrybut punktu końcowego różni się od nazwy usługi.</span><span class="sxs-lookup"><span data-stu-id="ddc41-164">Services may have multiple endpoints, so the endpoint’s `name` attribute is distinct from the name of the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ddc41-165">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ddc41-165">Child Elements</span></span>  
  
|<span data-ttu-id="ddc41-166">Element</span><span class="sxs-lookup"><span data-stu-id="ddc41-166">Element</span></span>|<span data-ttu-id="ddc41-167">Opis</span><span class="sxs-lookup"><span data-stu-id="ddc41-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ddc41-168">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="ddc41-168">\<headers></span></span>](headers.md)|<span data-ttu-id="ddc41-169">Kolekcja nagłówków adresów.</span><span class="sxs-lookup"><span data-stu-id="ddc41-169">A collection of address headers.</span></span>|  
|[<span data-ttu-id="ddc41-170">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="ddc41-170">\<identity></span></span>](identity.md)|<span data-ttu-id="ddc41-171">Tożsamość, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe wymieniające z nim komunikaty.</span><span class="sxs-lookup"><span data-stu-id="ddc41-171">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ddc41-172">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ddc41-172">Parent Elements</span></span>  
  
|<span data-ttu-id="ddc41-173">Element</span><span class="sxs-lookup"><span data-stu-id="ddc41-173">Element</span></span>|<span data-ttu-id="ddc41-174">Opis</span><span class="sxs-lookup"><span data-stu-id="ddc41-174">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ddc41-175">\<> usługi</span><span class="sxs-lookup"><span data-stu-id="ddc41-175">\<service></span></span>](service.md)|<span data-ttu-id="ddc41-176">Sekcja konfiguracji, która definiuje listę punktów końcowych, z którymi klient może się połączyć.</span><span class="sxs-lookup"><span data-stu-id="ddc41-176">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ddc41-177">Przykład</span><span class="sxs-lookup"><span data-stu-id="ddc41-177">Example</span></span>  
 <span data-ttu-id="ddc41-178">Jest to przykład konfiguracji punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="ddc41-178">This is an example of a service endpoint configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ddc41-179">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ddc41-179">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [<span data-ttu-id="ddc41-180">Punktów końcowych Adresy, powiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="ddc41-180">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="ddc41-181">Instrukcje: Tworzenie punktu końcowego usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ddc41-181">How to: Create a Service Endpoint in Configuration</span></span>](../../../wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
