---
title: Konfiguracja klienta
description: Dowiedz się, jak za pomocą konfiguracji klienta WCF określić adres, powiązanie, zachowanie i kontrakt dla punktu końcowego, który jest używany do nawiązywania połączenia z usługą.
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: c3e3d4904bad39e951e8ba69013ac95894130489
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245378"
---
# <a name="client-configuration"></a><span data-ttu-id="fb1e4-103">Konfiguracja klienta</span><span class="sxs-lookup"><span data-stu-id="fb1e4-103">Client Configuration</span></span>
<span data-ttu-id="fb1e4-104">Za pomocą konfiguracji klienta Windows Communication Foundation (WCF) można określić adres, powiązanie, zachowanie i kontrakt, czyli właściwości "ABC" punktu końcowego klienta używanego przez klientów do łączenia się z punktami końcowymi usługi.</span><span class="sxs-lookup"><span data-stu-id="fb1e4-104">You can use the Windows Communication Foundation (WCF) client configuration to specify the address, binding, behavior, and contract, the "ABC" properties of the client endpoint, which clients use to connect to service endpoints.</span></span> <span data-ttu-id="fb1e4-105">[\<client>](../../configure-apps/file-schema/wcf/client.md)Element ma element, [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) którego atrybuty są używane do konfigurowania punktu końcowego ABCs.</span><span class="sxs-lookup"><span data-stu-id="fb1e4-105">The [\<client>](../../configure-apps/file-schema/wcf/client.md) element has an [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element whose attributes are used to configure the endpoint ABCs.</span></span> <span data-ttu-id="fb1e4-106">Te atrybuty zostały omówione w sekcji [Konfigurowanie punktów końcowych](#configuring-endpoints) .</span><span class="sxs-lookup"><span data-stu-id="fb1e4-106">These attributes are discussed in the [Configuring Endpoints](#configuring-endpoints) section.</span></span>  
  
 <span data-ttu-id="fb1e4-107">[\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md)Element zawiera również [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) element, który jest używany do określania ustawień importowania i eksportowania metadanych, [\<headers>](../../configure-apps/file-schema/wcf/headers.md) element, który zawiera kolekcję niestandardowych nagłówków adresów i [\<identity>](../../configure-apps/file-schema/wcf/identity.md) element, który umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe wymieniające z nim wiadomości.</span><span class="sxs-lookup"><span data-stu-id="fb1e4-107">The [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element also contains a [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) element that is used to specify settings for importing and exporting metadata, a [\<headers>](../../configure-apps/file-schema/wcf/headers.md) element that contains a collection of custom address headers, and an [\<identity>](../../configure-apps/file-schema/wcf/identity.md) element that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span> <span data-ttu-id="fb1e4-108">[\<headers>](../../configure-apps/file-schema/wcf/headers.md)Elementy i są [\<identity>](../../configure-apps/file-schema/wcf/identity.md) częścią <xref:System.ServiceModel.EndpointAddress> i zostały omówione w artykule dotyczącej [adresów](endpoint-addresses.md) .</span><span class="sxs-lookup"><span data-stu-id="fb1e4-108">The [\<headers>](../../configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are discussed in the [Addresses](endpoint-addresses.md) article.</span></span> <span data-ttu-id="fb1e4-109">Linki do tematów, które wyjaśniają korzystanie z rozszerzeń metadanych, znajdują się w sekcji [Konfigurowanie metadanych](#configuring-metadata) .</span><span class="sxs-lookup"><span data-stu-id="fb1e4-109">Links to topics that explain the use of metadata extensions are provided in the [Configuring Metadata](#configuring-metadata) section.</span></span>  
  
## <a name="configuring-endpoints"></a><span data-ttu-id="fb1e4-110">Konfigurowanie punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="fb1e4-110">Configuring Endpoints</span></span>  
 <span data-ttu-id="fb1e4-111">Konfiguracja klienta została zaprojektowana tak, aby umożliwić klientowi określenie co najmniej jednego punktu końcowego, z każdą nazwą, adresem i umową, przy czym każdy odwołuje się do [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) elementów i w konfiguracji klienta, aby można było użyć ich do skonfigurowania tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="fb1e4-111">The client configuration is designed to allow the client to specify one or more endpoints, each with its own name, address, and contract, with each referencing the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) and [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) elements in the client configuration to be used to configure that endpoint.</span></span> <span data-ttu-id="fb1e4-112">Plik konfiguracji klienta powinien mieć nazwę "App.config", ponieważ jest to nazwa, której oczekuje środowisko uruchomieniowe WCF.</span><span class="sxs-lookup"><span data-stu-id="fb1e4-112">The client configuration file should be named "App.config" because this is the name that the WCF runtime expects.</span></span> <span data-ttu-id="fb1e4-113">Poniższy przykład przedstawia plik konfiguracji klienta.</span><span class="sxs-lookup"><span data-stu-id="fb1e4-113">The following example shows a client configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
        <client>  
          <endpoint  
            name="endpoint1"  
            address="http://localhost/ServiceModelSamples/service.svc"  
            binding="wsHttpBinding"  
            bindingConfiguration="WSHttpBinding_IHello"  
            behaviorConfiguration="IHello_Behavior"  
            contract="IHello" >  
  
            <metadata>  
              <wsdlImporters>  
                <extension  
                  type="Microsoft.ServiceModel.Samples.WsdlDocumentationImporter, WsdlDocumentation"/>  
              </wsdlImporters>  
            </metadata>  
  
            <identity>  
              <servicePrincipalName value="host/localhost" />  
            </identity>  
          </endpoint>  
            <!-- Add another endpoint by adding another <endpoint> element. -->
          <endpoint  
            name="endpoint2">  
           //Configure another endpoint here.  
          </endpoint>  
        </client>  
  
//The bindings section references by the bindingConfiguration endpoint attribute.  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_IHello"
                 bypassProxyOnLocal="false"
                 hostNameComparisonMode="StrongWildcard">  
          <readerQuotas maxDepth="32"/>  
          <reliableSession ordered="true"
                           enabled="false" />  
          <security mode="Message">  
           //Security settings go here.  
          </security>  
        </binding>  
        <binding name="Another Binding"  
          <!-- Configure this binding here. -->  
        </binding>  
          </wsHttpBinding>  
     </bindings>  
  
//The behavior section references by the behaviorConfiguration endpoint attribute.  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name=" IHello_Behavior ">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="fb1e4-114">Opcjonalny `name` atrybut jednoznacznie identyfikuje punkt końcowy danego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="fb1e4-114">The optional `name` attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="fb1e4-115">Jest on używany przez <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> lub przez program, <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> Aby określić, który punkt końcowy w konfiguracji klienta jest ukierunkowany i musi być załadowany podczas tworzenia kanału do obsługi.</span><span class="sxs-lookup"><span data-stu-id="fb1e4-115">It is used by the <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> or by the <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> to specify which endpoint in the client configuration is being targeted and must be loaded when a channel is created to service.</span></span> <span data-ttu-id="fb1e4-116">Nazwa konfiguracji wieloznacznego punktu końcowego " \* " jest dostępna i wskazuje <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> metodę, która powinna ładować każdą konfigurację punktu końcowego w pliku, pod warunkiem, że jest to dokładnie jedna dostępna i w przeciwnym razie zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="fb1e4-116">A wildcard endpoint configuration name "\*" is available and indicates to the <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> method that it should load any endpoint configuration in the file, provided there is precisely one available, and otherwise throws an exception.</span></span> <span data-ttu-id="fb1e4-117">Jeśli ten atrybut zostanie pominięty, odpowiadający mu punkt końcowy jest używany jako domyślny punkt końcowy skojarzony z określonym typem kontraktu.</span><span class="sxs-lookup"><span data-stu-id="fb1e4-117">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified contract type.</span></span> <span data-ttu-id="fb1e4-118">Wartość domyślna dla `name` atrybutu jest pustym ciągiem, który jest dopasowany jak dowolną inną nazwę.</span><span class="sxs-lookup"><span data-stu-id="fb1e4-118">The default value for the `name` attribute is an empty string which is matched like any other name.</span></span>  
  
 <span data-ttu-id="fb1e4-119">Każdy punkt końcowy musi mieć skojarzony z nim adres, aby zlokalizować i zidentyfikować punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="fb1e4-119">Every endpoint must have an address associated with it to locate and identify the endpoint.</span></span> <span data-ttu-id="fb1e4-120">Ten `address` atrybut może służyć do określania adresu URL, który zawiera lokalizację punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="fb1e4-120">The `address` attribute can be used to specify the URL that provides the location of the endpoint.</span></span> <span data-ttu-id="fb1e4-121">Ale adres punktu końcowego usługi można także określić w kodzie, tworząc Uniform Resource Identifier (URI) i jest dodawany do <xref:System.ServiceModel.ServiceHost> metody przy użyciu jednej z <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metod.</span><span class="sxs-lookup"><span data-stu-id="fb1e4-121">But the address for a service endpoint can also be specified in code by creating a Uniform Resource Identifier (URI) and is added to the <xref:System.ServiceModel.ServiceHost> using one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods.</span></span> <span data-ttu-id="fb1e4-122">Aby uzyskać więcej informacji, zobacz [Addressing](endpoint-addresses.md).</span><span class="sxs-lookup"><span data-stu-id="fb1e4-122">For more information, see [Addresses](endpoint-addresses.md).</span></span> <span data-ttu-id="fb1e4-123">Ponieważ wprowadzenie wskazuje, [\<headers>](../../configure-apps/file-schema/wcf/headers.md) [\<identity>](../../configure-apps/file-schema/wcf/identity.md) elementy i są częścią <xref:System.ServiceModel.EndpointAddress> i są również omówione w temacie [addresss (adresy](endpoint-addresses.md) ).</span><span class="sxs-lookup"><span data-stu-id="fb1e4-123">As the introduction indicates, the [\<headers>](../../configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are also discussed in the [Addresses](endpoint-addresses.md) topic.</span></span>  
  
 <span data-ttu-id="fb1e4-124">Ten `binding` atrybut wskazuje typ powiązania, którego punkt końcowy ma używać podczas łączenia się z usługą.</span><span class="sxs-lookup"><span data-stu-id="fb1e4-124">The `binding` attribute indicates the type of binding the endpoint expects to use when connecting to a service.</span></span> <span data-ttu-id="fb1e4-125">Aby można było odwołać, typ musi mieć zarejestrowaną sekcję konfiguracyjną.</span><span class="sxs-lookup"><span data-stu-id="fb1e4-125">The type must have a registered configuration section if it is to be referenced.</span></span> <span data-ttu-id="fb1e4-126">W poprzednim przykładzie jest to [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) sekcja, która wskazuje, że punkt końcowy używa <xref:System.ServiceModel.WSHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="fb1e4-126">In the previous example, this is the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) section, which indicates that the endpoint uses a <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="fb1e4-127">Może jednak istnieć więcej niż jedno powiązanie danego typu, które może być używane przez punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="fb1e4-127">But there may be more than one binding of a given type that the endpoint can use.</span></span> <span data-ttu-id="fb1e4-128">Każdy z nich ma swój własny [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element w elemencie typu (Binding).</span><span class="sxs-lookup"><span data-stu-id="fb1e4-128">Each of these has its own [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element within the (binding) type element.</span></span> <span data-ttu-id="fb1e4-129">Ten `bindingconfiguration` atrybut służy do rozróżniania powiązań tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="fb1e4-129">The `bindingconfiguration` attribute is used to distinguish between bindings of the same type.</span></span> <span data-ttu-id="fb1e4-130">Jego wartość jest zgodna z `name` atrybutem [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="fb1e4-130">Its value is matched with the `name` attribute of the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span> <span data-ttu-id="fb1e4-131">Aby uzyskać więcej informacji o konfigurowaniu powiązania klienta przy użyciu konfiguracji, zobacz [How to: Określanie powiązania klienta w konfiguracji](../how-to-specify-a-client-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="fb1e4-131">For more information about how to configure a client binding using configuration, see [How to: Specify a Client Binding in Configuration](../how-to-specify-a-client-binding-in-configuration.md).</span></span>  
  
 <span data-ttu-id="fb1e4-132">Ten `behaviorConfiguration` atrybut służy do określania, który [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) z [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) punktów końcowych ma być używany.</span><span class="sxs-lookup"><span data-stu-id="fb1e4-132">The `behaviorConfiguration` attribute is used to specify which [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) of the [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) the endpoint should use.</span></span> <span data-ttu-id="fb1e4-133">Jego wartość jest zgodna z `name` atrybutem [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="fb1e4-133">Its value is matched with the `name` attribute of the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element.</span></span> <span data-ttu-id="fb1e4-134">Przykład korzystania z konfiguracji w celu określenia zachowań klienta można znaleźć w temacie [Configuring Client Behaviors](../configuring-client-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="fb1e4-134">For an example of using configuration to specify client behaviors, see [Configuring Client Behaviors](../configuring-client-behaviors.md).</span></span>  
  
 <span data-ttu-id="fb1e4-135">Ten `contract` atrybut określa, który kontrakt jest ujawniany przez punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="fb1e4-135">The `contract` attribute specifies which contract the endpoint is exposing.</span></span> <span data-ttu-id="fb1e4-136">Ta wartość jest mapowana na <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> <xref:System.ServiceModel.ServiceContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="fb1e4-136">This value maps to the <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> of the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="fb1e4-137">Wartość domyślna to pełna nazwa typu klasy implementującej usługę.</span><span class="sxs-lookup"><span data-stu-id="fb1e4-137">The default value is the full type name of the class that implements the service.</span></span>  
  
### <a name="configuring-metadata"></a><span data-ttu-id="fb1e4-138">Konfigurowanie metadanych</span><span class="sxs-lookup"><span data-stu-id="fb1e4-138">Configuring Metadata</span></span>  
 <span data-ttu-id="fb1e4-139">[\<metadata>](../../configure-apps/file-schema/wcf/metadata.md)Element służy do określania ustawień używanych do rejestrowania rozszerzeń importu metadanych.</span><span class="sxs-lookup"><span data-stu-id="fb1e4-139">The [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) element is used to specify settings used to register metadata import extensions.</span></span> <span data-ttu-id="fb1e4-140">Aby uzyskać więcej informacji na temat rozszerzania systemu metadanych, zobacz [Rozszerzanie systemu metadanych](../extending/extending-the-metadata-system.md).</span><span class="sxs-lookup"><span data-stu-id="fb1e4-140">For more information about extending the metadata system, see [Extending the Metadata System](../extending/extending-the-metadata-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb1e4-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fb1e4-141">See also</span></span>

- [<span data-ttu-id="fb1e4-142">Punkty końcowe: Adresy, powiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="fb1e4-142">Endpoints: Addresses, Bindings, and Contracts</span></span>](endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="fb1e4-143">Konfigurowanie zachowań klienta</span><span class="sxs-lookup"><span data-stu-id="fb1e4-143">Configuring Client Behaviors</span></span>](../configuring-client-behaviors.md)
