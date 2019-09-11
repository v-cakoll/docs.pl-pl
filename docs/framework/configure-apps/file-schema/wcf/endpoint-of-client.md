---
title: <endpoint> dla <client>
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: f1ffbc1e8efac70523d7f631c8cf9ba9a1622bfc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855319"
---
# <a name="endpoint-of-client"></a><span data-ttu-id="9498c-102">\<> punktu końcowego \<> klienta</span><span class="sxs-lookup"><span data-stu-id="9498c-102">\<endpoint> of \<client></span></span>
<span data-ttu-id="9498c-103">Określa właściwości kontraktu, powiązania i adresu punktu końcowego kanału, który jest używany przez klientów do łączenia się z punktami końcowymi usługi na serwerze.</span><span class="sxs-lookup"><span data-stu-id="9498c-103">Specifies contract, binding, and address properties of the channel endpoint, which is used by clients to connect to service endpoints on the server.</span></span>  
  
<span data-ttu-id="9498c-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9498c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9498c-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9498c-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9498c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)</span><span class="sxs-lookup"><span data-stu-id="9498c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="9498c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> punktu końcowego**</span><span class="sxs-lookup"><span data-stu-id="9498c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9498c-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="9498c-108">Syntax</span></span>  
  
```xml  
<endpoint address="String"
          behaviorConfiguration="String"
          binding="String"
          bindingConfiguration="String"
          contract="String"
          endpointConfiguration="String"
          kind="String"
          name="String">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9498c-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9498c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9498c-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9498c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9498c-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9498c-111">Attributes</span></span>  
  
|<span data-ttu-id="9498c-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9498c-112">Attribute</span></span>|<span data-ttu-id="9498c-113">Opis</span><span class="sxs-lookup"><span data-stu-id="9498c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9498c-114">adres</span><span class="sxs-lookup"><span data-stu-id="9498c-114">address</span></span>|<span data-ttu-id="9498c-115">Atrybut wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="9498c-115">Required string attribute.</span></span><br /><br /> <span data-ttu-id="9498c-116">Określa adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="9498c-116">Specifies the address of the endpoint.</span></span> <span data-ttu-id="9498c-117">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="9498c-117">The default is an empty string.</span></span> <span data-ttu-id="9498c-118">Adres musi być bezwzględnym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="9498c-118">The address must be an absolute URI.</span></span>|  
|<span data-ttu-id="9498c-119">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="9498c-119">behaviorConfiguration</span></span>|<span data-ttu-id="9498c-120">Ciąg zawierający nazwę zachowania zachowania do użycia w celu utworzenia wystąpienia punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="9498c-120">A string that contains the behavior name of the behavior to be used to instantiate the endpoint.</span></span> <span data-ttu-id="9498c-121">Nazwa zachowania musi znajdować się w zakresie, w którym jest zdefiniowana usługa.</span><span class="sxs-lookup"><span data-stu-id="9498c-121">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="9498c-122">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="9498c-122">The default is an empty string.</span></span>|  
|<span data-ttu-id="9498c-123">powiązanie</span><span class="sxs-lookup"><span data-stu-id="9498c-123">binding</span></span>|<span data-ttu-id="9498c-124">Atrybut wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="9498c-124">Required string attribute.</span></span><br /><br /> <span data-ttu-id="9498c-125">Ciąg określający typ powiązania do użycia.</span><span class="sxs-lookup"><span data-stu-id="9498c-125">A string that indicates the type of binding to use.</span></span> <span data-ttu-id="9498c-126">Aby można było odwołać, typ musi mieć zarejestrowaną sekcję konfiguracyjną.</span><span class="sxs-lookup"><span data-stu-id="9498c-126">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="9498c-127">Typ jest zarejestrowany przez nazwę sekcji, a nie nazwę typu powiązania.</span><span class="sxs-lookup"><span data-stu-id="9498c-127">The type is registered by section name, instead of by the type name of the binding.</span></span>|  
|<span data-ttu-id="9498c-128">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="9498c-128">bindingConfiguration</span></span>|<span data-ttu-id="9498c-129">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9498c-129">Optional.</span></span> <span data-ttu-id="9498c-130">Ciąg zawierający nazwę konfiguracji powiązania, która ma być używana podczas tworzenia wystąpienia punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="9498c-130">A string that contains the name of the binding configuration to be used when the endpoint is instantiated.</span></span> <span data-ttu-id="9498c-131">Konfiguracja powiązania musi znajdować się w zakresie w punkcie, w którym jest zdefiniowany punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="9498c-131">The binding configuration must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="9498c-132">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="9498c-132">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="9498c-133">Ten atrybut jest używany w połączeniu z `binding` programem w celu odwoływania się do określonej konfiguracji powiązań w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9498c-133">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="9498c-134">Ustaw ten atrybut, jeśli próbujesz użyć niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="9498c-134">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="9498c-135">W przeciwnym razie może zostać zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="9498c-135">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="9498c-136">Przedsiębiorc</span><span class="sxs-lookup"><span data-stu-id="9498c-136">contract</span></span>|<span data-ttu-id="9498c-137">Atrybut wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="9498c-137">Required string attribute.</span></span><br /><br /> <span data-ttu-id="9498c-138">Ciąg wskazujący, który kontrakt jest ujawniany przez ten punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="9498c-138">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="9498c-139">Zestaw musi implementować typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="9498c-139">The assembly must implement the contract type.</span></span>|  
|<span data-ttu-id="9498c-140">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="9498c-140">endpointConfiguration</span></span>|<span data-ttu-id="9498c-141">Ciąg określający nazwę standardowego punktu końcowego, który jest ustawiany przez `kind` atrybut, który odwołuje się do dodatkowych informacji konfiguracyjnych tego standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="9498c-141">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="9498c-142">Ta sama nazwa musi być zdefiniowana w `<standardEndpoints>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="9498c-142">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="9498c-143">Natur</span><span class="sxs-lookup"><span data-stu-id="9498c-143">kind</span></span>|<span data-ttu-id="9498c-144">Ciąg określający typ stosowanego standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="9498c-144">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="9498c-145">Typ musi być zarejestrowany w `<extensions>` sekcji lub pliku Machine. config. Jeśli nic nie jest określone, tworzony jest wspólny punkt końcowy kanału.</span><span class="sxs-lookup"><span data-stu-id="9498c-145">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common channel endpoint is created.</span></span>|  
|<span data-ttu-id="9498c-146">nazwa</span><span class="sxs-lookup"><span data-stu-id="9498c-146">name</span></span>|<span data-ttu-id="9498c-147">Atrybut opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="9498c-147">Optional string attribute.</span></span> <span data-ttu-id="9498c-148">Ten atrybut jednoznacznie identyfikuje punkt końcowy dla danego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="9498c-148">This attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="9498c-149">Można zdefiniować wielu klientów dla danego typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="9498c-149">You can define multiple clients for a given Contract type.</span></span> <span data-ttu-id="9498c-150">Każda definicja musi być zróżnicowana przy użyciu unikatowej nazwy konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9498c-150">Each definition must be differentiated by a unique configuration name.</span></span> <span data-ttu-id="9498c-151">Jeśli ten atrybut zostanie pominięty, odpowiadający mu punkt końcowy jest używany jako domyślny punkt końcowy skojarzony z określonym typem kontraktu.</span><span class="sxs-lookup"><span data-stu-id="9498c-151">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified Contract type.</span></span> <span data-ttu-id="9498c-152">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="9498c-152">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="9498c-153">`name` Atrybut powiązania służy do eksportowania definicji za pomocą języka WSDL.</span><span class="sxs-lookup"><span data-stu-id="9498c-153">The `name` attribute of a binding is used for definition export through WSDL.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9498c-154">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9498c-154">Child Elements</span></span>  
  
|<span data-ttu-id="9498c-155">Element</span><span class="sxs-lookup"><span data-stu-id="9498c-155">Element</span></span>|<span data-ttu-id="9498c-156">Opis</span><span class="sxs-lookup"><span data-stu-id="9498c-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9498c-157">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="9498c-157">\<headers></span></span>](headers.md)|<span data-ttu-id="9498c-158">Kolekcja nagłówków adresów.</span><span class="sxs-lookup"><span data-stu-id="9498c-158">A collection of address headers.</span></span>|  
|[<span data-ttu-id="9498c-159">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="9498c-159">\<identity></span></span>](identity.md)|<span data-ttu-id="9498c-160">Tożsamość, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe wymieniające z nim komunikaty.</span><span class="sxs-lookup"><span data-stu-id="9498c-160">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9498c-161">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9498c-161">Parent Elements</span></span>  
  
|<span data-ttu-id="9498c-162">Element</span><span class="sxs-lookup"><span data-stu-id="9498c-162">Element</span></span>|<span data-ttu-id="9498c-163">Opis</span><span class="sxs-lookup"><span data-stu-id="9498c-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9498c-164">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="9498c-164">\<client></span></span>](client.md)|<span data-ttu-id="9498c-165">Sekcja konfiguracji, która definiuje listę punktów końcowych, z którymi klient może się połączyć.</span><span class="sxs-lookup"><span data-stu-id="9498c-165">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9498c-166">Przykład</span><span class="sxs-lookup"><span data-stu-id="9498c-166">Example</span></span>  
 <span data-ttu-id="9498c-167">Jest to przykład konfiguracji punktu końcowego kanału.</span><span class="sxs-lookup"><span data-stu-id="9498c-167">This is an example of a channel endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          name="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="9498c-168">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9498c-168">See also</span></span>

- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>
- <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- [<span data-ttu-id="9498c-169">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="9498c-169">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="9498c-170">Klienci</span><span class="sxs-lookup"><span data-stu-id="9498c-170">Clients</span></span>](../../../wcf/feature-details/clients.md)
