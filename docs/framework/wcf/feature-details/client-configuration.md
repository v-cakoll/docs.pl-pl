---
title: Konfiguracja klienta
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ece2585287f6e2767e64c2ec03c75adcfe161c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="client-configuration"></a><span data-ttu-id="ed8a1-102">Konfiguracja klienta</span><span class="sxs-lookup"><span data-stu-id="ed8a1-102">Client Configuration</span></span>
<span data-ttu-id="ed8a1-103">Można użyć [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] konfiguracji klienta, aby określić adres powiązania zachowania i kontraktu, właściwości "ABC" punktu końcowego klienta, której klienci używają do nawiązywania punktów końcowych usługi.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-103">You can use the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client configuration to specify the address, binding, behavior, and contract, the "ABC" properties of the client endpoint, which clients use to connect to service endpoints.</span></span> <span data-ttu-id="ed8a1-104">[ \<Klienta >](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) element ma [ \<punktu końcowego >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) elementu, którego atrybuty służą do konfigurowania punktu końcowego podstaw.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-104">The [\<client>](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) element has an [\<endpoint>](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) element whose attributes are used to configure the endpoint ABCs.</span></span> <span data-ttu-id="ed8a1-105">W sekcji "Konfigurowanie punktów końcowych" w tym temacie omówiono te atrybuty.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-105">These attributes are discussed in the "Configuring Endpoints" section of this topic.</span></span>  
  
 <span data-ttu-id="ed8a1-106">[ \<Punktu końcowego >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) zawiera również element [ \<metadanych >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element, który służy do określania ustawień do importowania i eksportowania metadanych, [ \<nagłówki >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element, który zawiera kolekcję nagłówków niestandardowy adres i [ \<tożsamości >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elementu, który umożliwia uwierzytelnianie punkt końcowy przez inne punkty końcowe wymiana wiadomości z nim.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-106">The [\<endpoint>](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) element also contains a [\<metadata>](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element that is used to specify settings for importing and exporting metadata , a [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element that contains a collection of custom address headers, and an [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span> <span data-ttu-id="ed8a1-107">[ \<Nagłówki >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) i [ \<tożsamości >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elementy są częścią <xref:System.ServiceModel.EndpointAddress> i zostały omówione w [adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-107">The [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are discussed in the [Addresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) topic.</span></span> <span data-ttu-id="ed8a1-108">Linki do tematów, które opisują korzystanie z rozszerzeń metadanych znajdują się w sekcji Konfigurowanie metadane podrzędne tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-108">Links to topics that explain the use of metadata extensions are provided in the Configuring Metadata sub-section of this topic.</span></span>  
  
## <a name="configuring-endpoints"></a><span data-ttu-id="ed8a1-109">Konfigurowanie punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="ed8a1-109">Configuring Endpoints</span></span>  
 <span data-ttu-id="ed8a1-110">Konfiguracja klienta umożliwia klientowi określić jedną lub więcej punktów końcowych, każdy z własną nazwę adresów, a kontraktu z każdym wywoływanym [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) i [ \< zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementów w konfiguracji klienta, który ma być używany do konfigurowania tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-110">The client configuration is designed to allow the client to specify one or more endpoints, each with its own name, address, and contract, with each referencing the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) and [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elements in the client configuration to be used to configure that endpoint.</span></span> <span data-ttu-id="ed8a1-111">Plik konfiguracji klienta powinien nosić nazwy "App.config", ponieważ jest to nazwa, która [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] środowisko uruchomieniowe oczekuje.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-111">The client configuration file should be named "App.config" because this is the name that the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime expects.</span></span> <span data-ttu-id="ed8a1-112">W poniższym przykładzie przedstawiono klienta pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-112">The following example shows a client configuration file.</span></span>  
  
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
// Add another endpoint by adding another <endpoint> element.  
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
        //Configure this binding here.  
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
  
 <span data-ttu-id="ed8a1-113">Opcjonalny `name` atrybutu unikatowo identyfikuje punkt końcowy dla danego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-113">The optional `name` attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="ed8a1-114">Jest on używany przez <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> lub <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> do określenia, które punkt końcowy w konfiguracji klienta docelowej i musi być załadowany po utworzeniu kanału do usługi.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-114">It is used by the <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> or by the <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> to specify which endpoint in the client configuration is being targeted and must be loaded when a channel is created to service.</span></span> <span data-ttu-id="ed8a1-115">Nazwy konfiguracji punktu końcowego symbol wieloznaczny "*" jest dostępny i wskazuje <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> metody, czy należy go załadować żadnej konfiguracji punktu końcowego w pliku, pod warunkiem, że dokładnie jeden dostępny, a w przeciwnym razie zwraca wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-115">A wildcard endpoint configuration name "*" is available and indicates to the <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> method that it should load any endpoint configuration in the file, provided there is precisely one available, and otherwise throws an exception.</span></span> <span data-ttu-id="ed8a1-116">W przypadku pominięcia tego atrybutu odpowiedniego punkt końcowy jest używany jako domyślny punkt końcowy skojarzone z typem określonym kontraktu.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-116">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified contract type.</span></span> <span data-ttu-id="ed8a1-117">Wartość domyślna dla `name` atrybut jest pusty ciąg, który jest takie samo jak dowolnej innej nazwy.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-117">The default value for the `name` attribute is an empty string which is matched like any other name.</span></span>  
  
 <span data-ttu-id="ed8a1-118">Każdy punkt końcowy musi mieć adres skojarzony z nim do lokalizowania i identyfikowania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-118">Every endpoint must have an address associated with it to locate and identify the endpoint.</span></span> <span data-ttu-id="ed8a1-119">`address` Atrybut może służyć do określenia adresu URL, który określa lokalizację punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-119">The `address` attribute can be used to specify the URL that provides the location of the endpoint.</span></span> <span data-ttu-id="ed8a1-120">Jednak adres punktu końcowego usługi można również określić w kodzie, tworząc jednolity identyfikator zasobów (URI) i jest dodawany do <xref:System.ServiceModel.ServiceHost> przy użyciu jednej z <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-120">But the address for a service endpoint can also be specified in code by creating a Uniform Resource Identifier (URI) and is added to the <xref:System.ServiceModel.ServiceHost> using one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="ed8a1-121">[Adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md).</span><span class="sxs-lookup"><span data-stu-id="ed8a1-121"> [Addresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md).</span></span> <span data-ttu-id="ed8a1-122">Jak wskazuje wprowadzenie, [ \<nagłówki >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) i [ \<tożsamości >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elementy są częścią <xref:System.ServiceModel.EndpointAddress> i omówiono także w [ Adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-122">As the introduction indicates, the [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are also discussed in the [Addresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) topic.</span></span>  
  
 <span data-ttu-id="ed8a1-123">`binding` Atrybut wskazuje typ powiązania punktu końcowego oczekuje do użycia podczas połączenia z usługą.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-123">The `binding` attribute indicates the type of binding the endpoint expects to use when connecting to a service.</span></span> <span data-ttu-id="ed8a1-124">Typ musi mieć sekcję konfiguracji zarejestrowane, aby odwoływać się.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-124">The type must have a registered configuration section if it is to be referenced.</span></span> <span data-ttu-id="ed8a1-125">W poprzednim przykładzie jest to [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) sekcję, co oznacza, że punkt końcowy używa <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-125">In the previous example, this is the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) section, which indicates that the endpoint uses a <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="ed8a1-126">Mogą jednak istnieć więcej niż jedno powiązanie danego typu punktu końcowego można użyć.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-126">But there may be more than one binding of a given type that the endpoint can use.</span></span> <span data-ttu-id="ed8a1-127">Każdy z nich ma własną [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu w elemencie type (powiązanie).</span><span class="sxs-lookup"><span data-stu-id="ed8a1-127">Each of these has its own [\<binding>](../../../../docs/framework/misc/binding.md) element within the (binding) type element.</span></span> <span data-ttu-id="ed8a1-128">`bindingconfiguration` Atrybut służy do rozróżnienia powiązania tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-128">The `bindingconfiguration` attribute is used to distinguish between bindings of the same type.</span></span> <span data-ttu-id="ed8a1-129">Wartość jest dopasowywany `name` atrybutu [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-129">Its value is matched with the `name` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) element.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ed8a1-130">jak skonfigurować klienta powiązania za pomocą konfiguracji, zobacz [porady: Określanie wiązania klienta w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="ed8a1-130"> how to configure a client binding using configuration, see [How to: Specify a Client Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).</span></span>  
  
 <span data-ttu-id="ed8a1-131">`behaviorConfiguration` Atrybut służy do określania, które [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) z [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) należy używać punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-131">The `behaviorConfiguration` attribute is used to specify which [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) of the [\<endpointBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) the endpoint should use.</span></span> <span data-ttu-id="ed8a1-132">Wartość jest dopasowywany `name` atrybutu [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-132">Its value is matched with the `name` attribute of the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element.</span></span> <span data-ttu-id="ed8a1-133">Na przykład za pomocą konfiguracji do określania zachowania klienta, zobacz [Konfigurowanie zachowań klienta](../../../../docs/framework/wcf/configuring-client-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="ed8a1-133">For an example of using configuration to specify client behaviors, see [Configuring Client Behaviors](../../../../docs/framework/wcf/configuring-client-behaviors.md).</span></span>  
  
 <span data-ttu-id="ed8a1-134">`contract` Określa atrybut, który kontrakt jest ujawniany przez punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-134">The `contract` attribute specifies which contract the endpoint is exposing.</span></span> <span data-ttu-id="ed8a1-135">Ta wartość jest mapowany na <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> z <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-135">This value maps to the <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> of the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="ed8a1-136">Wartość domyślna to pełna nazwa typu klasy, która implementuje usługę.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-136">The default value is the full type name of the class that implements the service.</span></span>  
  
### <a name="configuring-metadata"></a><span data-ttu-id="ed8a1-137">Konfigurowanie metadanych</span><span class="sxs-lookup"><span data-stu-id="ed8a1-137">Configuring Metadata</span></span>  
 <span data-ttu-id="ed8a1-138">[ \<Metadanych >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element jest używany do określenia, ustawienia używane do rejestrowania metadanych zaimportować rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="ed8a1-138">The [\<metadata>](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element is used to specify settings used to register metadata import extensions.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ed8a1-139">rozszerzanie systemu metadanych, zobacz[rozszerzanie systemu metadanych](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).</span><span class="sxs-lookup"><span data-stu-id="ed8a1-139"> extending the metadata system, see[Extending the Metadata System](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed8a1-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ed8a1-140">See Also</span></span>  
 [<span data-ttu-id="ed8a1-141">Punkty końcowe: adresy, powiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="ed8a1-141">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [<span data-ttu-id="ed8a1-142">Konfigurowanie zachowań klienta</span><span class="sxs-lookup"><span data-stu-id="ed8a1-142">Configuring Client Behaviors</span></span>](../../../../docs/framework/wcf/configuring-client-behaviors.md)
