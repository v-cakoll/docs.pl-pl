---
title: <endpoint> dla <client>
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: f1ffbc1e8efac70523d7f631c8cf9ba9a1622bfc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855319"
---
# <a name="endpoint-of-client"></a><span data-ttu-id="f37c9-102">\<endpoint> dla \<client></span><span class="sxs-lookup"><span data-stu-id="f37c9-102">\<endpoint> of \<client></span></span>
<span data-ttu-id="f37c9-103">Określa właściwości kontraktu, powiązania i adresu punktu końcowego kanału, który jest używany przez klientów do łączenia się z punktami końcowymi usługi na serwerze.</span><span class="sxs-lookup"><span data-stu-id="f37c9-103">Specifies contract, binding, and address properties of the channel endpoint, which is used by clients to connect to service endpoints on the server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="f37c9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f37c9-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f37c9-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f37c9-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f37c9-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f37c9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f37c9-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f37c9-107">Attributes</span></span>  
  
|<span data-ttu-id="f37c9-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f37c9-108">Attribute</span></span>|<span data-ttu-id="f37c9-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f37c9-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f37c9-110">adres</span><span class="sxs-lookup"><span data-stu-id="f37c9-110">address</span></span>|<span data-ttu-id="f37c9-111">Wymagany atrybut ciągu.</span><span class="sxs-lookup"><span data-stu-id="f37c9-111">Required string attribute.</span></span><br /><br /> <span data-ttu-id="f37c9-112">Określa adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f37c9-112">Specifies the address of the endpoint.</span></span> <span data-ttu-id="f37c9-113">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="f37c9-113">The default is an empty string.</span></span> <span data-ttu-id="f37c9-114">Adres musi być bezwzględnym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="f37c9-114">The address must be an absolute URI.</span></span>|  
|<span data-ttu-id="f37c9-115">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="f37c9-115">behaviorConfiguration</span></span>|<span data-ttu-id="f37c9-116">Ciąg zawierający nazwę zachowania zachowania do użycia w celu utworzenia wystąpienia punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f37c9-116">A string that contains the behavior name of the behavior to be used to instantiate the endpoint.</span></span> <span data-ttu-id="f37c9-117">Nazwa zachowania musi znajdować się w zakresie, w którym jest zdefiniowana usługa.</span><span class="sxs-lookup"><span data-stu-id="f37c9-117">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="f37c9-118">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="f37c9-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="f37c9-119">powiązanie</span><span class="sxs-lookup"><span data-stu-id="f37c9-119">binding</span></span>|<span data-ttu-id="f37c9-120">Wymagany atrybut ciągu.</span><span class="sxs-lookup"><span data-stu-id="f37c9-120">Required string attribute.</span></span><br /><br /> <span data-ttu-id="f37c9-121">Ciąg określający typ powiązania do użycia.</span><span class="sxs-lookup"><span data-stu-id="f37c9-121">A string that indicates the type of binding to use.</span></span> <span data-ttu-id="f37c9-122">Aby można było odwołać, typ musi mieć zarejestrowaną sekcję konfiguracyjną.</span><span class="sxs-lookup"><span data-stu-id="f37c9-122">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="f37c9-123">Typ jest zarejestrowany przez nazwę sekcji, a nie nazwę typu powiązania.</span><span class="sxs-lookup"><span data-stu-id="f37c9-123">The type is registered by section name, instead of by the type name of the binding.</span></span>|  
|<span data-ttu-id="f37c9-124">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="f37c9-124">bindingConfiguration</span></span>|<span data-ttu-id="f37c9-125">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f37c9-125">Optional.</span></span> <span data-ttu-id="f37c9-126">Ciąg zawierający nazwę konfiguracji powiązania, która ma być używana podczas tworzenia wystąpienia punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f37c9-126">A string that contains the name of the binding configuration to be used when the endpoint is instantiated.</span></span> <span data-ttu-id="f37c9-127">Konfiguracja powiązania musi znajdować się w zakresie w punkcie, w którym jest zdefiniowany punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="f37c9-127">The binding configuration must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="f37c9-128">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="f37c9-128">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="f37c9-129">Ten atrybut jest używany w połączeniu z programem w `binding` celu odwoływania się do określonej konfiguracji powiązań w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f37c9-129">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="f37c9-130">Ustaw ten atrybut, jeśli próbujesz użyć niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f37c9-130">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="f37c9-131">W przeciwnym razie może zostać zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f37c9-131">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="f37c9-132">przedsiębiorc</span><span class="sxs-lookup"><span data-stu-id="f37c9-132">contract</span></span>|<span data-ttu-id="f37c9-133">Wymagany atrybut ciągu.</span><span class="sxs-lookup"><span data-stu-id="f37c9-133">Required string attribute.</span></span><br /><br /> <span data-ttu-id="f37c9-134">Ciąg wskazujący, który kontrakt jest ujawniany przez ten punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="f37c9-134">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="f37c9-135">Zestaw musi implementować typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="f37c9-135">The assembly must implement the contract type.</span></span>|  
|<span data-ttu-id="f37c9-136">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="f37c9-136">endpointConfiguration</span></span>|<span data-ttu-id="f37c9-137">Ciąg określający nazwę standardowego punktu końcowego, który jest ustawiany przez `kind` atrybut, który odwołuje się do dodatkowych informacji konfiguracyjnych tego standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f37c9-137">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="f37c9-138">Ta sama nazwa musi być zdefiniowana w `<standardEndpoints>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="f37c9-138">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="f37c9-139">Natur</span><span class="sxs-lookup"><span data-stu-id="f37c9-139">kind</span></span>|<span data-ttu-id="f37c9-140">Ciąg określający typ stosowanego standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f37c9-140">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="f37c9-141">Typ musi być zarejestrowany w `<extensions>` sekcji lub pliku Machine. config. Jeśli nic nie jest określone, tworzony jest wspólny punkt końcowy kanału.</span><span class="sxs-lookup"><span data-stu-id="f37c9-141">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common channel endpoint is created.</span></span>|  
|<span data-ttu-id="f37c9-142">name</span><span class="sxs-lookup"><span data-stu-id="f37c9-142">name</span></span>|<span data-ttu-id="f37c9-143">Opcjonalny atrybut ciągu.</span><span class="sxs-lookup"><span data-stu-id="f37c9-143">Optional string attribute.</span></span> <span data-ttu-id="f37c9-144">Ten atrybut jednoznacznie identyfikuje punkt końcowy dla danego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="f37c9-144">This attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="f37c9-145">Można zdefiniować wielu klientów dla danego typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="f37c9-145">You can define multiple clients for a given Contract type.</span></span> <span data-ttu-id="f37c9-146">Każda definicja musi być zróżnicowana przy użyciu unikatowej nazwy konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f37c9-146">Each definition must be differentiated by a unique configuration name.</span></span> <span data-ttu-id="f37c9-147">Jeśli ten atrybut zostanie pominięty, odpowiadający mu punkt końcowy jest używany jako domyślny punkt końcowy skojarzony z określonym typem kontraktu.</span><span class="sxs-lookup"><span data-stu-id="f37c9-147">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified Contract type.</span></span> <span data-ttu-id="f37c9-148">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="f37c9-148">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="f37c9-149">`name`Atrybut powiązania służy do eksportowania definicji za pomocą języka WSDL.</span><span class="sxs-lookup"><span data-stu-id="f37c9-149">The `name` attribute of a binding is used for definition export through WSDL.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f37c9-150">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f37c9-150">Child Elements</span></span>  
  
|<span data-ttu-id="f37c9-151">Element</span><span class="sxs-lookup"><span data-stu-id="f37c9-151">Element</span></span>|<span data-ttu-id="f37c9-152">Opis</span><span class="sxs-lookup"><span data-stu-id="f37c9-152">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers.md)|<span data-ttu-id="f37c9-153">Kolekcja nagłówków adresów.</span><span class="sxs-lookup"><span data-stu-id="f37c9-153">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="f37c9-154">Tożsamość, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe wymieniające z nim komunikaty.</span><span class="sxs-lookup"><span data-stu-id="f37c9-154">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f37c9-155">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f37c9-155">Parent Elements</span></span>  
  
|<span data-ttu-id="f37c9-156">Element</span><span class="sxs-lookup"><span data-stu-id="f37c9-156">Element</span></span>|<span data-ttu-id="f37c9-157">Opis</span><span class="sxs-lookup"><span data-stu-id="f37c9-157">Description</span></span>|  
|-------------|-----------------|  
|[\<client>](client.md)|<span data-ttu-id="f37c9-158">Sekcja konfiguracji, która definiuje listę punktów końcowych, z którymi klient może się połączyć.</span><span class="sxs-lookup"><span data-stu-id="f37c9-158">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f37c9-159">Przykład</span><span class="sxs-lookup"><span data-stu-id="f37c9-159">Example</span></span>  
 <span data-ttu-id="f37c9-160">Jest to przykład konfiguracji punktu końcowego kanału.</span><span class="sxs-lookup"><span data-stu-id="f37c9-160">This is an example of a channel endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          name="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="f37c9-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f37c9-161">See also</span></span>

- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>
- <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- [<span data-ttu-id="f37c9-162">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="f37c9-162">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="f37c9-163">Klienci</span><span class="sxs-lookup"><span data-stu-id="f37c9-163">Clients</span></span>](../../../wcf/feature-details/clients.md)
