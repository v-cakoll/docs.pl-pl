---
title: Konfiguracja klienta
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: 0fd3d1a15164447275ef488ac91b9a8bd240032d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493134"
---
# <a name="client-configuration"></a>Konfiguracja klienta
Konfiguracja klienta Windows Communication Foundation (WCF) służy do określania adresu, powiązania zachowania i kontraktu, właściwości "ABC" punktu końcowego klienta, których klienci używają do nawiązywania punktów końcowych usługi. [ \<Klienta >](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) element ma [ \<punktu końcowego >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) elementu, którego atrybuty służą do konfigurowania punktu końcowego podstaw. W sekcji "Konfigurowanie punktów końcowych" w tym temacie omówiono te atrybuty.  
  
 [ \<Punktu końcowego >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) zawiera również element [ \<metadanych >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element, który służy do określania ustawień do importowania i eksportowania metadanych, [ \<nagłówki >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element, który zawiera kolekcję nagłówków niestandardowy adres i [ \<tożsamości >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elementu, który umożliwia uwierzytelnianie punkt końcowy przez inne punkty końcowe wymiana wiadomości z nim. [ \<Nagłówki >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) i [ \<tożsamości >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elementy są częścią <xref:System.ServiceModel.EndpointAddress> i zostały omówione w [adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) tematu. Linki do tematów, które opisują korzystanie z rozszerzeń metadanych znajdują się w sekcji Konfigurowanie metadane podrzędne tego tematu.  
  
## <a name="configuring-endpoints"></a>Konfigurowanie punktów końcowych  
 Konfiguracja klienta umożliwia klientowi określić jedną lub więcej punktów końcowych, każdy z własną nazwę adresów, a kontraktu z każdym wywoływanym [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) i [ \< zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementów w konfiguracji klienta, który ma być używany do konfigurowania tego punktu końcowego. Plik konfiguracji klienta powinny mieć nazwę "App.config", ponieważ jest to nazwa, która oczekuje środowiska uruchomieniowego usługi WCF. W poniższym przykładzie przedstawiono klienta pliku konfiguracji.  
  
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
  
 Opcjonalny `name` atrybutu unikatowo identyfikuje punkt końcowy dla danego kontraktu. Jest on używany przez <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> lub <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> do określenia, które punkt końcowy w konfiguracji klienta docelowej i musi być załadowany po utworzeniu kanału do usługi. Nazwy konfiguracji punktu końcowego symbol wieloznaczny "*" jest dostępny i wskazuje <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> metody, czy należy go załadować żadnej konfiguracji punktu końcowego w pliku, pod warunkiem, że dokładnie jeden dostępny, a w przeciwnym razie zwraca wyjątek. W przypadku pominięcia tego atrybutu odpowiedniego punkt końcowy jest używany jako domyślny punkt końcowy skojarzone z typem określonym kontraktu. Wartość domyślna dla `name` atrybut jest pusty ciąg, który jest takie samo jak dowolnej innej nazwy.  
  
 Każdy punkt końcowy musi mieć adres skojarzony z nim do lokalizowania i identyfikowania punktu końcowego. `address` Atrybut może służyć do określenia adresu URL, który określa lokalizację punktu końcowego. Jednak adres punktu końcowego usługi można również określić w kodzie, tworząc jednolity identyfikator zasobów (URI) i jest dodawany do <xref:System.ServiceModel.ServiceHost> przy użyciu jednej z <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody. Aby uzyskać więcej informacji, zobacz [adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md). Jak wskazuje wprowadzenie, [ \<nagłówki >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) i [ \<tożsamości >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elementy są częścią <xref:System.ServiceModel.EndpointAddress> i omówiono także w [ Adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) tematu.  
  
 `binding` Atrybut wskazuje typ powiązania punktu końcowego oczekuje do użycia podczas połączenia z usługą. Typ musi mieć sekcję konfiguracji zarejestrowane, aby odwoływać się. W poprzednim przykładzie jest to [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) sekcję, co oznacza, że punkt końcowy używa <xref:System.ServiceModel.WSHttpBinding>. Mogą jednak istnieć więcej niż jedno powiązanie danego typu punktu końcowego można użyć. Każdy z nich ma własną [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu w elemencie type (powiązanie). `bindingconfiguration` Atrybut służy do rozróżnienia powiązania tego samego typu. Wartość jest dopasowywany `name` atrybutu [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu. Aby uzyskać więcej informacji o sposobie konfigurowania klienta powiązania za pomocą konfiguracji, zobacz [porady: Określanie wiązania klienta w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).  
  
 `behaviorConfiguration` Atrybut służy do określania, które [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) z [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) należy używać punktu końcowego. Wartość jest dopasowywany `name` atrybutu [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu. Na przykład za pomocą konfiguracji do określania zachowania klienta, zobacz [Konfigurowanie zachowań klienta](../../../../docs/framework/wcf/configuring-client-behaviors.md).  
  
 `contract` Określa atrybut, który kontrakt jest ujawniany przez punkt końcowy. Ta wartość jest mapowany na <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> z <xref:System.ServiceModel.ServiceContractAttribute>. Wartość domyślna to pełna nazwa typu klasy, która implementuje usługę.  
  
### <a name="configuring-metadata"></a>Konfigurowanie metadanych  
 [ \<Metadanych >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element jest używany do określenia, ustawienia używane do rejestrowania metadanych zaimportować rozszerzenia. Aby uzyskać więcej informacji na temat rozszerzanie systemu metadanych, zobacz[rozszerzanie systemu metadanych](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Punkty końcowe: adresy, powiązania i kontrakty](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [Konfigurowanie zachowań klienta](../../../../docs/framework/wcf/configuring-client-behaviors.md)
