---
title: <endpoint>, element
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: fb9d3bf9b5f1a742abcc70d78af026c179ec4c4d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855378"
---
# <a name="endpoint-element"></a><span data-ttu-id="3f3f4-102">\<Element > punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="3f3f4-102">\<endpoint> element</span></span>
<span data-ttu-id="3f3f4-103">Określa powiązanie, kontrakt i właściwości adresu dla punktu końcowego usługi, który jest używany do udostępniania usług.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-103">Specifies binding, contract, and address properties for a service endpoint, which is used to expose services.</span></span>  
  
<span data-ttu-id="3f3f4-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3f3f4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3f3f4-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="3f3f4-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3f3f4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> usług**](services.md)</span><span class="sxs-lookup"><span data-stu-id="3f3f4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="3f3f4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> usługi**](service.md)</span><span class="sxs-lookup"><span data-stu-id="3f3f4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="3f3f4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> punktu końcowego**</span><span class="sxs-lookup"><span data-stu-id="3f3f4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f3f4-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="3f3f4-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f3f4-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3f3f4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3f3f4-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f3f4-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3f3f4-112">Attributes</span></span>  
  
|<span data-ttu-id="3f3f4-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3f3f4-113">Attribute</span></span>|<span data-ttu-id="3f3f4-114">Opis</span><span class="sxs-lookup"><span data-stu-id="3f3f4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3f3f4-115">adres</span><span class="sxs-lookup"><span data-stu-id="3f3f4-115">address</span></span>|<span data-ttu-id="3f3f4-116">Ciąg zawierający adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-116">A string that contains the address of the endpoint.</span></span> <span data-ttu-id="3f3f4-117">Adres może być określony jako adres bezwzględny lub względny.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-117">The address can be specified as an absolute or relative address.</span></span> <span data-ttu-id="3f3f4-118">Jeśli zostanie podany adres względny, host powinien podać adres podstawowy odpowiedni dla schematu transportu używanego w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-118">If a relative address is provided, the host is expected to provide a base address appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="3f3f4-119">Jeśli adres nie jest skonfigurowany, zakłada się, że adres podstawowy jest adresem dla tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-119">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span><br /><br /> <span data-ttu-id="3f3f4-120">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-120">The default is an empty string.</span></span>|  
|<span data-ttu-id="3f3f4-121">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="3f3f4-121">behaviorConfiguration</span></span>|<span data-ttu-id="3f3f4-122">Ciąg zawierający nazwę zachowania do użycia w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-122">A string that contains the name of the behavior to be used in the endpoint.</span></span>|  
|<span data-ttu-id="3f3f4-123">powiązanie</span><span class="sxs-lookup"><span data-stu-id="3f3f4-123">binding</span></span>|<span data-ttu-id="3f3f4-124">Wymagany atrybut ciągu, który określa typ powiązania do użycia.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-124">Required string attribute that specifies the type of binding to use.</span></span> <span data-ttu-id="3f3f4-125">Aby można było odwołać, typ musi mieć zarejestrowaną sekcję konfiguracyjną.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-125">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="3f3f4-126">Typ jest typem zarejestrowanym według nazwy sekcji, a nie nazwą typu powiązania.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-126">The type is the registered by section name, rather than by the type name of the binding.</span></span>|  
|<span data-ttu-id="3f3f4-127">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="3f3f4-127">bindingConfiguration</span></span>|<span data-ttu-id="3f3f4-128">Ciąg określający nazwę powiązania powiązania do użycia podczas tworzenia wystąpienia punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-128">A string that specifies the binding name of the binding to use when the endpoint is instantiated.</span></span> <span data-ttu-id="3f3f4-129">Nazwa powiązania musi znajdować się w zakresie w punkcie, w którym jest zdefiniowany punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-129">The binding name must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="3f3f4-130">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-130">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="3f3f4-131">Ten atrybut jest używany w połączeniu z `binding` programem w celu odwoływania się do określonej konfiguracji powiązań w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-131">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="3f3f4-132">Ustaw ten atrybut, jeśli próbujesz użyć niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-132">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="3f3f4-133">W przeciwnym razie może zostać zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-133">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="3f3f4-134">powiązaniename</span><span class="sxs-lookup"><span data-stu-id="3f3f4-134">bindingName</span></span>|<span data-ttu-id="3f3f4-135">Ciąg określający unikalną kwalifikowaną nazwę powiązania w celu eksportu definicji za pomocą WSDL.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-135">A string that specifies the unique qualified name of the binding for definition export through WSDL.</span></span> <span data-ttu-id="3f3f4-136">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-136">The default is an empty string.</span></span>|  
|<span data-ttu-id="3f3f4-137">bindingNamespace</span><span class="sxs-lookup"><span data-stu-id="3f3f4-137">bindingNamespace</span></span>|<span data-ttu-id="3f3f4-138">Ciąg określający kwalifikowaną nazwę przestrzeni nazw powiązania w celu eksportu definicji za pomocą WSDL.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-138">A string that specifies the qualified name of the namespace of the binding for definition export through WSDL.</span></span> <span data-ttu-id="3f3f4-139">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-139">The default is an empty string.</span></span>|  
|<span data-ttu-id="3f3f4-140">Przedsiębiorc</span><span class="sxs-lookup"><span data-stu-id="3f3f4-140">contract</span></span>|<span data-ttu-id="3f3f4-141">Ciąg wskazujący, który kontrakt jest ujawniany przez ten punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-141">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="3f3f4-142">Zestaw musi implementować typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-142">The assembly must implement the contract type.</span></span> <span data-ttu-id="3f3f4-143">Jeśli implementacja usługi implementuje pojedynczy typ kontraktu, ta właściwość może zostać pominięta.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-143">If a service implementation implements a single contract type, then this property can be omitted.</span></span> <span data-ttu-id="3f3f4-144">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-144">The default is an empty string.</span></span>|  
|<span data-ttu-id="3f3f4-145">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="3f3f4-145">endpointConfiguration</span></span>|<span data-ttu-id="3f3f4-146">Ciąg określający nazwę standardowego punktu końcowego, który jest ustawiany przez `kind` atrybut, który odwołuje się do dodatkowych informacji konfiguracyjnych tego standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-146">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="3f3f4-147">Ta sama nazwa musi być zdefiniowana w `<standardEndpoints>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-147">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="3f3f4-148">isSystemEndpoint</span><span class="sxs-lookup"><span data-stu-id="3f3f4-148">isSystemEndpoint</span></span>|<span data-ttu-id="3f3f4-149">Wartość logiczna określająca, czy punkt końcowy jest punktem końcowym infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-149">A Boolean value that specifies whether an endpoint is an infrastructure endpoint.</span></span>|  
|<span data-ttu-id="3f3f4-150">Natur</span><span class="sxs-lookup"><span data-stu-id="3f3f4-150">kind</span></span>|<span data-ttu-id="3f3f4-151">Ciąg określający typ stosowanego standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-151">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="3f3f4-152">Typ musi być zarejestrowany w `<extensions>` sekcji lub pliku Machine. config. Jeśli nic nie zostanie określone, tworzony jest wspólny punkt końcowy usługi.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-152">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common service endpoint is created.</span></span>|  
|<span data-ttu-id="3f3f4-153">listenUriMode</span><span class="sxs-lookup"><span data-stu-id="3f3f4-153">listenUriMode</span></span>|<span data-ttu-id="3f3f4-154">Określa sposób, w jaki transport `ListenUri` traktuje podany na potrzeby nasłuchiwania usługi.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-154">Specifies how the transport treats the `ListenUri` provided for the service to listen on.</span></span> <span data-ttu-id="3f3f4-155">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="3f3f4-155">Valid values are</span></span><br /><br /> <span data-ttu-id="3f3f4-156">-Jawne</span><span class="sxs-lookup"><span data-stu-id="3f3f4-156">-   Explicit</span></span><br /><span data-ttu-id="3f3f4-157">-Unikatowy</span><span class="sxs-lookup"><span data-stu-id="3f3f4-157">-   Unique</span></span><br /><br /> <span data-ttu-id="3f3f4-158">Wartość domyślna to explicit.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-158">The default value is Explicit.</span></span>|  
|<span data-ttu-id="3f3f4-159">listenUri</span><span class="sxs-lookup"><span data-stu-id="3f3f4-159">listenUri</span></span>|<span data-ttu-id="3f3f4-160">Ciąg określający identyfikator URI, z którego nasłuchuje punkt końcowy usługi.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-160">A string that specifies the URI at which the service endpoint listens.</span></span> <span data-ttu-id="3f3f4-161">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-161">The default is an empty string.</span></span>|  
|<span data-ttu-id="3f3f4-162">nazwa</span><span class="sxs-lookup"><span data-stu-id="3f3f4-162">name</span></span>|<span data-ttu-id="3f3f4-163">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-163">Optional attribute.</span></span> <span data-ttu-id="3f3f4-164">Ciąg określający nazwę punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-164">A string that specifies the name the service endpoint.</span></span> <span data-ttu-id="3f3f4-165">Wartość domyślna to połączenie nazwy powiązania i nazwy opisu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-165">The default value is the concatenation of the binding name and the contract description name.</span></span> <span data-ttu-id="3f3f4-166">Usługi mogą mieć wiele punktów końcowych, więc `name` atrybut punktu końcowego różni się od nazwy usługi.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-166">Services may have multiple endpoints, so the endpoint’s `name` attribute is distinct from the name of the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3f3f4-167">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3f3f4-167">Child Elements</span></span>  
  
|<span data-ttu-id="3f3f4-168">Element</span><span class="sxs-lookup"><span data-stu-id="3f3f4-168">Element</span></span>|<span data-ttu-id="3f3f4-169">Opis</span><span class="sxs-lookup"><span data-stu-id="3f3f4-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f3f4-170">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="3f3f4-170">\<headers></span></span>](headers.md)|<span data-ttu-id="3f3f4-171">Kolekcja nagłówków adresów.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-171">A collection of address headers.</span></span>|  
|[<span data-ttu-id="3f3f4-172">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="3f3f4-172">\<identity></span></span>](identity.md)|<span data-ttu-id="3f3f4-173">Tożsamość, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe wymieniające z nim komunikaty.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-173">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3f3f4-174">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3f3f4-174">Parent Elements</span></span>  
  
|<span data-ttu-id="3f3f4-175">Element</span><span class="sxs-lookup"><span data-stu-id="3f3f4-175">Element</span></span>|<span data-ttu-id="3f3f4-176">Opis</span><span class="sxs-lookup"><span data-stu-id="3f3f4-176">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f3f4-177">\<> usługi</span><span class="sxs-lookup"><span data-stu-id="3f3f4-177">\<service></span></span>](service.md)|<span data-ttu-id="3f3f4-178">Sekcja konfiguracji, która definiuje listę punktów końcowych, z którymi klient może się połączyć.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-178">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3f3f4-179">Przykład</span><span class="sxs-lookup"><span data-stu-id="3f3f4-179">Example</span></span>  
 <span data-ttu-id="3f3f4-180">Jest to przykład konfiguracji punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="3f3f4-180">This is an example of a service endpoint configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3f3f4-181">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f3f4-181">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [<span data-ttu-id="3f3f4-182">Punktów końcowych Adresy, powiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="3f3f4-182">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="3f3f4-183">Instrukcje: Tworzenie punktu końcowego usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="3f3f4-183">How to: Create a Service Endpoint in Configuration</span></span>](../../../wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
