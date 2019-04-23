---
title: <endpoint> dla <client>
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: 3af41ad5b5681b08aac44d984372ab5ac66caf5e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59231204"
---
# <a name="endpoint-of-client"></a><span data-ttu-id="e4139-102">\<punkt końcowy > z \<klienta ></span><span class="sxs-lookup"><span data-stu-id="e4139-102">\<endpoint> of \<client></span></span>
<span data-ttu-id="e4139-103">Określa kontrakt, powiązanie i właściwości adresu punktu końcowego kanału, który jest używany przez klientów do łączenia się z punktami końcowymi usługi na serwerze.</span><span class="sxs-lookup"><span data-stu-id="e4139-103">Specifies contract, binding, and address properties of the channel endpoint, which is used by clients to connect to service endpoints on the server.</span></span>  
  
 <span data-ttu-id="e4139-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e4139-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e4139-105">\<client></span><span class="sxs-lookup"><span data-stu-id="e4139-105">\<client></span></span>  
<span data-ttu-id="e4139-106">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="e4139-106">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4139-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e4139-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4139-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e4139-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e4139-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e4139-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4139-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e4139-110">Attributes</span></span>  
  
|<span data-ttu-id="e4139-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e4139-111">Attribute</span></span>|<span data-ttu-id="e4139-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e4139-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e4139-113">adres</span><span class="sxs-lookup"><span data-stu-id="e4139-113">address</span></span>|<span data-ttu-id="e4139-114">Atrybut wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="e4139-114">Required string attribute.</span></span><br /><br /> <span data-ttu-id="e4139-115">Określa adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e4139-115">Specifies the address of the endpoint.</span></span> <span data-ttu-id="e4139-116">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="e4139-116">The default is an empty string.</span></span> <span data-ttu-id="e4139-117">Adres musi być bezwzględnym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="e4139-117">The address must be an absolute URI.</span></span>|  
|<span data-ttu-id="e4139-118">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="e4139-118">behaviorConfiguration</span></span>|<span data-ttu-id="e4139-119">Ciąg zawierający nazwę zachowania użytego do utworzenia wystąpienia punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e4139-119">A string that contains the behavior name of the behavior to be used to instantiate the endpoint.</span></span> <span data-ttu-id="e4139-120">Nazwa zachowania musi być w zakresie w punkcie, który jest zdefiniowany przez usługę.</span><span class="sxs-lookup"><span data-stu-id="e4139-120">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="e4139-121">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="e4139-121">The default is an empty string.</span></span>|  
|<span data-ttu-id="e4139-122">powiązanie</span><span class="sxs-lookup"><span data-stu-id="e4139-122">binding</span></span>|<span data-ttu-id="e4139-123">Atrybut wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="e4139-123">Required string attribute.</span></span><br /><br /> <span data-ttu-id="e4139-124">Ciąg, który określa typ powiązania do użycia.</span><span class="sxs-lookup"><span data-stu-id="e4139-124">A string that indicates the type of binding to use.</span></span> <span data-ttu-id="e4139-125">Typ musi mieć sekcję zarejestrowanych konfiguracji, aby odwoływać się.</span><span class="sxs-lookup"><span data-stu-id="e4139-125">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="e4139-126">Ten typ jest zarejestrowany przy użyciu nazwy sekcji, a nie przez nazwę typu powiązania.</span><span class="sxs-lookup"><span data-stu-id="e4139-126">The type is registered by section name, instead of by the type name of the binding.</span></span>|  
|<span data-ttu-id="e4139-127">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="e4139-127">bindingConfiguration</span></span>|<span data-ttu-id="e4139-128">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="e4139-128">Optional.</span></span> <span data-ttu-id="e4139-129">Ciąg zawierający nazwę konfiguracji powiązania, który ma być używany, gdy punkt końcowy zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="e4139-129">A string that contains the name of the binding configuration to be used when the endpoint is instantiated.</span></span> <span data-ttu-id="e4139-130">Konfiguracja powiązania musi być w zakresie w punkcie, który jest zdefiniowany punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="e4139-130">The binding configuration must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="e4139-131">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="e4139-131">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="e4139-132">Ten atrybut jest używany w połączeniu z `binding` można odwoływać się do konfiguracji powiązania określone w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e4139-132">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="e4139-133">Ustaw ten atrybut, jeśli chcesz użyć niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="e4139-133">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="e4139-134">W przeciwnym razie może być wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e4139-134">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="e4139-135">kontrakt</span><span class="sxs-lookup"><span data-stu-id="e4139-135">contract</span></span>|<span data-ttu-id="e4139-136">Atrybut wymagany ciąg.</span><span class="sxs-lookup"><span data-stu-id="e4139-136">Required string attribute.</span></span><br /><br /> <span data-ttu-id="e4139-137">Ciąg wskazujący, który kontrakt tego punktu końcowego jest uwidaczniany.</span><span class="sxs-lookup"><span data-stu-id="e4139-137">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="e4139-138">Zestaw musi implementować typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e4139-138">The assembly must implement the contract type.</span></span>|  
|<span data-ttu-id="e4139-139">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="e4139-139">endpointConfiguration</span></span>|<span data-ttu-id="e4139-140">Ciąg określający nazwę standardowego punktu końcowego, który jest uporządkowany według `kind` atrybut, który odwołuje się do informacji dodatkowej konfiguracji tego standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e4139-140">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="e4139-141">Taką samą nazwę muszą być zdefiniowane w `<standardEndpoints>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="e4139-141">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="e4139-142">rodzaj</span><span class="sxs-lookup"><span data-stu-id="e4139-142">kind</span></span>|<span data-ttu-id="e4139-143">Ciąg określający typ stosowanego standardowego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e4139-143">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="e4139-144">Typ musi być zarejestrowana w `<extensions>` sekcji lub w pliku machine.config. Jeśli nic nie zostanie określony, zostanie utworzony wspólnego punktu końcowego kanału.</span><span class="sxs-lookup"><span data-stu-id="e4139-144">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common channel endpoint is created.</span></span>|  
|<span data-ttu-id="e4139-145">nazwa</span><span class="sxs-lookup"><span data-stu-id="e4139-145">name</span></span>|<span data-ttu-id="e4139-146">Atrybut opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="e4139-146">Optional string attribute.</span></span> <span data-ttu-id="e4139-147">Ten atrybut jest jednoznacznie identyfikuje punkt końcowy dla danego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e4139-147">This attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="e4139-148">Można zdefiniować wielu klientach na potrzeby danego typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e4139-148">You can define multiple clients for a given Contract type.</span></span> <span data-ttu-id="e4139-149">Każda definicja musi być rozróżniane przez unikatową nazwę.</span><span class="sxs-lookup"><span data-stu-id="e4139-149">Each definition must be differentiated by a unique configuration name.</span></span> <span data-ttu-id="e4139-150">Jeśli ten atrybut zostanie pominięty, odpowiedni punkt końcowy jest używany jako domyślny punkt końcowy skojarzony z określonym typem umowy.</span><span class="sxs-lookup"><span data-stu-id="e4139-150">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified Contract type.</span></span> <span data-ttu-id="e4139-151">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="e4139-151">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="e4139-152">`name` Atrybut powiązania jest używany w celu eksportu definicji za pośrednictwem WSDL.</span><span class="sxs-lookup"><span data-stu-id="e4139-152">The `name` attribute of a binding is used for definition export through WSDL.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4139-153">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e4139-153">Child Elements</span></span>  
  
|<span data-ttu-id="e4139-154">Element</span><span class="sxs-lookup"><span data-stu-id="e4139-154">Element</span></span>|<span data-ttu-id="e4139-155">Opis</span><span class="sxs-lookup"><span data-stu-id="e4139-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4139-156">\<headers></span><span class="sxs-lookup"><span data-stu-id="e4139-156">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="e4139-157">Kolekcję nagłówków adresowych.</span><span class="sxs-lookup"><span data-stu-id="e4139-157">A collection of address headers.</span></span>|  
|[<span data-ttu-id="e4139-158">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="e4139-158">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="e4139-159">Tożsamość, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe, wymiana wiadomości z nim.</span><span class="sxs-lookup"><span data-stu-id="e4139-159">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e4139-160">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e4139-160">Parent Elements</span></span>  
  
|<span data-ttu-id="e4139-161">Element</span><span class="sxs-lookup"><span data-stu-id="e4139-161">Element</span></span>|<span data-ttu-id="e4139-162">Opis</span><span class="sxs-lookup"><span data-stu-id="e4139-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4139-163">\<Klient ></span><span class="sxs-lookup"><span data-stu-id="e4139-163">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="e4139-164">Sekcja konfiguracji, który definiuje listę punktów końcowych, które klient może połączyć się z.</span><span class="sxs-lookup"><span data-stu-id="e4139-164">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e4139-165">Przykład</span><span class="sxs-lookup"><span data-stu-id="e4139-165">Example</span></span>  
 <span data-ttu-id="e4139-166">Jest to przykład konfiguracji punktu końcowego kanału.</span><span class="sxs-lookup"><span data-stu-id="e4139-166">This is an example of a channel endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          name="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="e4139-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4139-167">See also</span></span>

- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>
- <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- [<span data-ttu-id="e4139-168">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="e4139-168">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="e4139-169">Klienci</span><span class="sxs-lookup"><span data-stu-id="e4139-169">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
