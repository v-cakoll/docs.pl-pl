---
title: <endpoint> dla <client>
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: 2bf59972ff2f75995e94a3c1934e88944d65fcc7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919098"
---
# <a name="endpoint-of-client"></a><span data-ttu-id="892b9-102">\<> punktu końcowego \<> klienta</span><span class="sxs-lookup"><span data-stu-id="892b9-102">\<endpoint> of \<client></span></span>
<span data-ttu-id="892b9-103">Określa właściwości kontraktu, powiązania i adresu punktu końcowego kanału, który jest używany przez klientów do łączenia się z punktami końcowymi usługi na serwerze.</span><span class="sxs-lookup"><span data-stu-id="892b9-103">Specifies contract, binding, and address properties of the channel endpoint, which is used by clients to connect to service endpoints on the server.</span></span>  
  
 <span data-ttu-id="892b9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="892b9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="892b9-105">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="892b9-105">\<client></span></span>  
<span data-ttu-id="892b9-106">\<> punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="892b9-106">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="892b9-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="892b9-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="892b9-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="892b9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="892b9-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="892b9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="892b9-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="892b9-110">Attributes</span></span>  
  
|<span data-ttu-id="892b9-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="892b9-111">Attribute</span></span>|<span data-ttu-id="892b9-112">Opis</span><span class="sxs-lookup"><span data-stu-id="892b9-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="892b9-113">adres</span><span class="sxs-lookup"><span data-stu-id="892b9-113">address</span></span>|<span data-ttu-id="892b9-114">Atrybut wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="892b9-114">Required string attribute.</span></span><br /><br /> <span data-ttu-id="892b9-115">Określa adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="892b9-115">Specifies the address of the endpoint.</span></span> <span data-ttu-id="892b9-116">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="892b9-116">The default is an empty string.</span></span> <span data-ttu-id="892b9-117">Adres musi być bezwzględnym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="892b9-117">The address must be an absolute URI.</span></span>|  
|<span data-ttu-id="892b9-118">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="892b9-118">behaviorConfiguration</span></span>|<span data-ttu-id="892b9-119">Ciąg zawierający nazwę zachowania zachowania do użycia w celu utworzenia wystąpienia punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="892b9-119">A string that contains the behavior name of the behavior to be used to instantiate the endpoint.</span></span> <span data-ttu-id="892b9-120">Nazwa zachowania musi znajdować się w zakresie, w którym jest zdefiniowana usługa.</span><span class="sxs-lookup"><span data-stu-id="892b9-120">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="892b9-121">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="892b9-121">The default is an empty string.</span></span>|  
|<span data-ttu-id="892b9-122">powiązanie</span><span class="sxs-lookup"><span data-stu-id="892b9-122">binding</span></span>|<span data-ttu-id="892b9-123">Atrybut wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="892b9-123">Required string attribute.</span></span><br /><br /> <span data-ttu-id="892b9-124">Ciąg określający typ powiązania do użycia.</span><span class="sxs-lookup"><span data-stu-id="892b9-124">A string that indicates the type of binding to use.</span></span> <span data-ttu-id="892b9-125">Aby można było odwołać, typ musi mieć zarejestrowaną sekcję konfiguracyjną.</span><span class="sxs-lookup"><span data-stu-id="892b9-125">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="892b9-126">Typ jest zarejestrowany przez nazwę sekcji, a nie nazwę typu powiązania.</span><span class="sxs-lookup"><span data-stu-id="892b9-126">The type is registered by section name, instead of by the type name of the binding.</span></span>|  
|<span data-ttu-id="892b9-127">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="892b9-127">bindingConfiguration</span></span>|<span data-ttu-id="892b9-128">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="892b9-128">Optional.</span></span> <span data-ttu-id="892b9-129">Ciąg zawierający nazwę konfiguracji powiązania, która ma być używana podczas tworzenia wystąpienia punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="892b9-129">A string that contains the name of the binding configuration to be used when the endpoint is instantiated.</span></span> <span data-ttu-id="892b9-130">Konfiguracja powiązania musi znajdować się w zakresie w punkcie, w którym jest zdefiniowany punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="892b9-130">The binding configuration must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="892b9-131">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="892b9-131">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="892b9-132">Ten atrybut jest używany w połączeniu z `binding` programem w celu odwoływania się do określonej konfiguracji powiązań w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="892b9-132">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="892b9-133">Ustaw ten atrybut, jeśli próbujesz użyć niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="892b9-133">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="892b9-134">W przeciwnym razie może zostać zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="892b9-134">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="892b9-135">przedsiębiorc</span><span class="sxs-lookup"><span data-stu-id="892b9-135">contract</span></span>|<span data-ttu-id="892b9-136">Atrybut wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="892b9-136">Required string attribute.</span></span><br /><br /> <span data-ttu-id="892b9-137">Ciąg wskazujący, który kontrakt jest ujawniany przez ten punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="892b9-137">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="892b9-138">Zestaw musi implementować typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="892b9-138">The assembly must implement the contract type.</span></span>|  
|<span data-ttu-id="892b9-139">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="892b9-139">endpointConfiguration</span></span>|<span data-ttu-id="892b9-140">Ciąg określający nazwę standardowego punktu końcowego, który jest ustawiany przez `kind` atrybut, który odwołuje się do dodatkowych informacji konfiguracyjnych tego standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="892b9-140">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="892b9-141">Ta sama nazwa musi być zdefiniowana w `<standardEndpoints>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="892b9-141">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="892b9-142">Natur</span><span class="sxs-lookup"><span data-stu-id="892b9-142">kind</span></span>|<span data-ttu-id="892b9-143">Ciąg określający typ stosowanego standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="892b9-143">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="892b9-144">Typ musi być zarejestrowany w `<extensions>` sekcji lub pliku Machine. config. Jeśli nic nie jest określone, tworzony jest wspólny punkt końcowy kanału.</span><span class="sxs-lookup"><span data-stu-id="892b9-144">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common channel endpoint is created.</span></span>|  
|<span data-ttu-id="892b9-145">nazwa</span><span class="sxs-lookup"><span data-stu-id="892b9-145">name</span></span>|<span data-ttu-id="892b9-146">Atrybut opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="892b9-146">Optional string attribute.</span></span> <span data-ttu-id="892b9-147">Ten atrybut jednoznacznie identyfikuje punkt końcowy dla danego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="892b9-147">This attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="892b9-148">Można zdefiniować wielu klientów dla danego typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="892b9-148">You can define multiple clients for a given Contract type.</span></span> <span data-ttu-id="892b9-149">Każda definicja musi być zróżnicowana przy użyciu unikatowej nazwy konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="892b9-149">Each definition must be differentiated by a unique configuration name.</span></span> <span data-ttu-id="892b9-150">Jeśli ten atrybut zostanie pominięty, odpowiadający mu punkt końcowy jest używany jako domyślny punkt końcowy skojarzony z określonym typem kontraktu.</span><span class="sxs-lookup"><span data-stu-id="892b9-150">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified Contract type.</span></span> <span data-ttu-id="892b9-151">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="892b9-151">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="892b9-152">`name` Atrybut powiązania służy do eksportowania definicji za pomocą języka WSDL.</span><span class="sxs-lookup"><span data-stu-id="892b9-152">The `name` attribute of a binding is used for definition export through WSDL.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="892b9-153">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="892b9-153">Child Elements</span></span>  
  
|<span data-ttu-id="892b9-154">Element</span><span class="sxs-lookup"><span data-stu-id="892b9-154">Element</span></span>|<span data-ttu-id="892b9-155">Opis</span><span class="sxs-lookup"><span data-stu-id="892b9-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="892b9-156">\<nagłówki ></span><span class="sxs-lookup"><span data-stu-id="892b9-156">\<headers></span></span>](headers.md)|<span data-ttu-id="892b9-157">Kolekcja nagłówków adresów.</span><span class="sxs-lookup"><span data-stu-id="892b9-157">A collection of address headers.</span></span>|  
|[<span data-ttu-id="892b9-158">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="892b9-158">\<identity></span></span>](identity.md)|<span data-ttu-id="892b9-159">Tożsamość, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe wymieniające z nim komunikaty.</span><span class="sxs-lookup"><span data-stu-id="892b9-159">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="892b9-160">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="892b9-160">Parent Elements</span></span>  
  
|<span data-ttu-id="892b9-161">Element</span><span class="sxs-lookup"><span data-stu-id="892b9-161">Element</span></span>|<span data-ttu-id="892b9-162">Opis</span><span class="sxs-lookup"><span data-stu-id="892b9-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="892b9-163">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="892b9-163">\<client></span></span>](client.md)|<span data-ttu-id="892b9-164">Sekcja konfiguracji, która definiuje listę punktów końcowych, z którymi klient może się połączyć.</span><span class="sxs-lookup"><span data-stu-id="892b9-164">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="892b9-165">Przykład</span><span class="sxs-lookup"><span data-stu-id="892b9-165">Example</span></span>  
 <span data-ttu-id="892b9-166">Jest to przykład konfiguracji punktu końcowego kanału.</span><span class="sxs-lookup"><span data-stu-id="892b9-166">This is an example of a channel endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          name="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="892b9-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="892b9-167">See also</span></span>

- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>
- <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- [<span data-ttu-id="892b9-168">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="892b9-168">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="892b9-169">Klienci</span><span class="sxs-lookup"><span data-stu-id="892b9-169">Clients</span></span>](../../../wcf/feature-details/clients.md)
