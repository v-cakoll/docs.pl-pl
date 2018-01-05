---
title: '&lt;endpoint&gt;, element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7175cf55df6bb735367effa8f806a472b9ce5ea6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltendpointgt-element"></a><span data-ttu-id="abf3d-102">&lt;endpoint&gt;, element</span><span class="sxs-lookup"><span data-stu-id="abf3d-102">&lt;endpoint&gt; element</span></span>
<span data-ttu-id="abf3d-103">Określa powiązanie, kontrakt i właściwości adresu punktu końcowego usługi, który jest używany do udostępnienia usług.</span><span class="sxs-lookup"><span data-stu-id="abf3d-103">Specifies binding, contract, and address properties for a service endpoint, which is used to expose services.</span></span>  
  
 <span data-ttu-id="abf3d-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="abf3d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="abf3d-105">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="abf3d-105">\<service></span></span>  
<span data-ttu-id="abf3d-106">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="abf3d-106">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abf3d-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="abf3d-107">Syntax</span></span>  
  
```xml  
<endpoint address="String"  
   behaviorConfiguration="String"  
   binding="String"  
   bindingConfiguration="String"  
   bindingName="String"  
   bindingNamespace="String"  
   contract="String"  
   endpointConfiguration="String"   isSystemEndpoint="Boolean"   kind="String"   listenUriMode="Explicit/Unique"  
   listenUri="Uri"  
</endpoint>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="abf3d-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="abf3d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="abf3d-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="abf3d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="abf3d-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="abf3d-110">Attributes</span></span>  
  
|<span data-ttu-id="abf3d-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="abf3d-111">Attribute</span></span>|<span data-ttu-id="abf3d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="abf3d-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="abf3d-113">adres</span><span class="sxs-lookup"><span data-stu-id="abf3d-113">address</span></span>|<span data-ttu-id="abf3d-114">Ciąg zawierający adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="abf3d-114">A string that contains the address of the endpoint.</span></span> <span data-ttu-id="abf3d-115">Adres można określić jako adres bezwzględny lub względny.</span><span class="sxs-lookup"><span data-stu-id="abf3d-115">The address can be specified as an absolute or relative address.</span></span> <span data-ttu-id="abf3d-116">Jeśli zostanie podany adres względny, hosta powinien zapewniać odpowiednie dla schemat transportu używane powiązanie adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="abf3d-116">If a relative address is provided, the host is expected to provide a base address appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="abf3d-117">Jeśli nie skonfigurowano adres podstawowy adres zakłada się, że adres dla tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="abf3d-117">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span><br /><br /> <span data-ttu-id="abf3d-118">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="abf3d-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="abf3d-119">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="abf3d-119">behaviorConfiguration</span></span>|<span data-ttu-id="abf3d-120">Ciąg zawierający nazwę zachowania do użycia w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="abf3d-120">A string that contains the name of the behavior to be used in the endpoint.</span></span>|  
|<span data-ttu-id="abf3d-121">powiązanie</span><span class="sxs-lookup"><span data-stu-id="abf3d-121">binding</span></span>|<span data-ttu-id="abf3d-122">Wymagany atrybut ciągu określający typ powiązania do użycia.</span><span class="sxs-lookup"><span data-stu-id="abf3d-122">Required string attribute that specifies the type of binding to use.</span></span> <span data-ttu-id="abf3d-123">Typ musi mieć sekcję konfiguracji zarejestrowanych, aby można było odwoływać się.</span><span class="sxs-lookup"><span data-stu-id="abf3d-123">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="abf3d-124">Typ jest zarejestrowaną nazwę sekcji, a nie nazwa typu powiązania.</span><span class="sxs-lookup"><span data-stu-id="abf3d-124">The type is the registered by section name, rather than by the type name of the binding.</span></span>|  
|<span data-ttu-id="abf3d-125">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="abf3d-125">bindingConfiguration</span></span>|<span data-ttu-id="abf3d-126">Ciąg określający nazwę powiązania w celu użycia podczas tworzenia wystąpienia klasy punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="abf3d-126">A string that specifies the binding name of the binding to use when the endpoint is instantiated.</span></span> <span data-ttu-id="abf3d-127">Nazwa powiązania musi być w zakresie w punkcie, który zdefiniowano punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="abf3d-127">The binding name must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="abf3d-128">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="abf3d-128">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="abf3d-129">Ten atrybut jest używany w połączeniu z `binding` do odwołania konfigurację powiązania określonych w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="abf3d-129">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="abf3d-130">Ustaw ten atrybut, jeśli chcesz użyć niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="abf3d-130">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="abf3d-131">W przeciwnym razie może być wyjątek.</span><span class="sxs-lookup"><span data-stu-id="abf3d-131">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="abf3d-132">bindingName</span><span class="sxs-lookup"><span data-stu-id="abf3d-132">bindingName</span></span>|<span data-ttu-id="abf3d-133">Ciąg określający unikalną kwalifikowaną nazwę powiązania w celu eksportu definicji za pośrednictwem WSDL.</span><span class="sxs-lookup"><span data-stu-id="abf3d-133">A string that specifies the unique qualified name of the binding for definition export through WSDL.</span></span> <span data-ttu-id="abf3d-134">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="abf3d-134">The default is an empty string.</span></span>|  
|<span data-ttu-id="abf3d-135">bindingNamespace</span><span class="sxs-lookup"><span data-stu-id="abf3d-135">bindingNamespace</span></span>|<span data-ttu-id="abf3d-136">Ciąg określający kwalifikowaną nazwę przestrzeni nazw powiązania dla definicji eksportowania za pośrednictwem WSDL.</span><span class="sxs-lookup"><span data-stu-id="abf3d-136">A string that specifies the qualified name of the namespace of the binding for definition export through WSDL.</span></span> <span data-ttu-id="abf3d-137">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="abf3d-137">The default is an empty string.</span></span>|  
|<span data-ttu-id="abf3d-138">kontrakt</span><span class="sxs-lookup"><span data-stu-id="abf3d-138">contract</span></span>|<span data-ttu-id="abf3d-139">Ciąg znaków wskazujący, który kontrakt jest ujawniany ten punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="abf3d-139">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="abf3d-140">Zestaw musi implementować typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="abf3d-140">The assembly must implement the contract type.</span></span> <span data-ttu-id="abf3d-141">Jeśli implementacji usługi implementuje typu jeden kontrakt, tej właściwości można pominąć.</span><span class="sxs-lookup"><span data-stu-id="abf3d-141">If a service implementation implements a single contract type, then this property can be omitted.</span></span> <span data-ttu-id="abf3d-142">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="abf3d-142">The default is an empty string.</span></span>|  
|<span data-ttu-id="abf3d-143">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="abf3d-143">endpointConfiguration</span></span>|<span data-ttu-id="abf3d-144">Ciąg określający nazwę standardowego punktu końcowego, który jest uporządkowany według `kind` atrybut, który odwołuje się do informacji dodatkowej konfiguracji tego standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="abf3d-144">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="abf3d-145">Taką samą nazwę, muszą być zdefiniowane w `<standardEndpoints>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="abf3d-145">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="abf3d-146">isSystemEndpoint</span><span class="sxs-lookup"><span data-stu-id="abf3d-146">isSystemEndpoint</span></span>|<span data-ttu-id="abf3d-147">Wartość logiczna określająca, czy punkt końcowy jest punktem końcowym infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="abf3d-147">A Boolean value that specifies whether an endpoint is an infrastructure endpoint.</span></span>|  
|<span data-ttu-id="abf3d-148">rodzaj</span><span class="sxs-lookup"><span data-stu-id="abf3d-148">kind</span></span>|<span data-ttu-id="abf3d-149">Ciąg określający typ stosowanego standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="abf3d-149">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="abf3d-150">Typ musi być zarejestrowana w `<extensions>` sekcji lub w pliku machine.config. Jeśli nie określono żadnej wartości, jest tworzona wspólnego punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="abf3d-150">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common service endpoint is created.</span></span>|  
|<span data-ttu-id="abf3d-151">listenUriMode</span><span class="sxs-lookup"><span data-stu-id="abf3d-151">listenUriMode</span></span>|<span data-ttu-id="abf3d-152">Określa, jak warstwa transportu traktuje `ListenUri` dostarczony dla usługi do nasłuchiwania.</span><span class="sxs-lookup"><span data-stu-id="abf3d-152">Specifies how the transport treats the `ListenUri` provided for the service to listen on.</span></span> <span data-ttu-id="abf3d-153">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="abf3d-153">Valid values are</span></span><br /><br /> <span data-ttu-id="abf3d-154">-Jawne</span><span class="sxs-lookup"><span data-stu-id="abf3d-154">-   Explicit</span></span><br /><span data-ttu-id="abf3d-155">— Unikatowe</span><span class="sxs-lookup"><span data-stu-id="abf3d-155">-   Unique</span></span><br /><br /> <span data-ttu-id="abf3d-156">Wartość domyślna to Explicit.</span><span class="sxs-lookup"><span data-stu-id="abf3d-156">The default value is Explicit.</span></span>|  
|<span data-ttu-id="abf3d-157">Identyfikator ListenUri</span><span class="sxs-lookup"><span data-stu-id="abf3d-157">listenUri</span></span>|<span data-ttu-id="abf3d-158">Ciąg określający URI, na którym nasłuchuje usługa punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="abf3d-158">A string that specifies the URI at which the service endpoint listens.</span></span> <span data-ttu-id="abf3d-159">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="abf3d-159">The default is an empty string.</span></span>|  
|<span data-ttu-id="abf3d-160">nazwa</span><span class="sxs-lookup"><span data-stu-id="abf3d-160">name</span></span>|<span data-ttu-id="abf3d-161">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="abf3d-161">Optional attribute.</span></span> <span data-ttu-id="abf3d-162">Ciąg określający nazwę punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="abf3d-162">A string that specifies the name the service endpoint.</span></span> <span data-ttu-id="abf3d-163">Wartość domyślna to łączenia nazwę i opis nazwy kontraktu.</span><span class="sxs-lookup"><span data-stu-id="abf3d-163">The default value is the concatenation of the binding name and the contract description name.</span></span> <span data-ttu-id="abf3d-164">Usługi mogą mieć wiele punktów końcowych, więc punktu końcowego `name` atrybut różni się od nazwy usługi.</span><span class="sxs-lookup"><span data-stu-id="abf3d-164">Services may have multiple endpoints, so the endpoint’s `name` attribute is distinct from the name of the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="abf3d-165">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="abf3d-165">Child Elements</span></span>  
  
|<span data-ttu-id="abf3d-166">Element</span><span class="sxs-lookup"><span data-stu-id="abf3d-166">Element</span></span>|<span data-ttu-id="abf3d-167">Opis</span><span class="sxs-lookup"><span data-stu-id="abf3d-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="abf3d-168">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="abf3d-168">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="abf3d-169">Kolekcja nagłówków adresu.</span><span class="sxs-lookup"><span data-stu-id="abf3d-169">A collection of address headers.</span></span>|  
|[<span data-ttu-id="abf3d-170">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="abf3d-170">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="abf3d-171">Tożsamości, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe, wymiana wiadomości z nim.</span><span class="sxs-lookup"><span data-stu-id="abf3d-171">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="abf3d-172">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="abf3d-172">Parent Elements</span></span>  
  
|<span data-ttu-id="abf3d-173">Element</span><span class="sxs-lookup"><span data-stu-id="abf3d-173">Element</span></span>|<span data-ttu-id="abf3d-174">Opis</span><span class="sxs-lookup"><span data-stu-id="abf3d-174">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="abf3d-175">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="abf3d-175">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="abf3d-176">Sekcja konfiguracyjna, który definiuje listę punktów końcowych, które klient może połączyć się.</span><span class="sxs-lookup"><span data-stu-id="abf3d-176">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="abf3d-177">Przykład</span><span class="sxs-lookup"><span data-stu-id="abf3d-177">Example</span></span>  
 <span data-ttu-id="abf3d-178">Jest to przykład konfiguracji punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="abf3d-178">This is an example of a service endpoint configuration.</span></span>  
  
```xml  
<endpoint   
    address="/HelloWorld/"  
    bindingConfiguration="usingDefaults"  
    bindingName="MyBinding"  
    binding="customBinding"  
    contract="HelloWorld">  
    <Headers>  
       <Region xmlns="http://tempuri.org/">EastCoast</Region>  
       <Member xmlns="http://tempuri.org/">Gold</Member>  
    </Headers>  
</endpoint>  
```  
  
## <a name="see-also"></a><span data-ttu-id="abf3d-179">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="abf3d-179">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceEndpointElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.Description.ServiceEndpoint>  
 [<span data-ttu-id="abf3d-180">Punkty końcowe: adresy, powiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="abf3d-180">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [<span data-ttu-id="abf3d-181">Instrukcje: tworzenie punktu końcowego usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="abf3d-181">How to: Create a Service Endpoint in Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
