---
title: Konfiguracja klienta
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: 2e178f8b08fbadbb5549fa10631d3a57f71a7e0d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54503225"
---
# <a name="client-configuration"></a>Konfiguracja klienta
Konfiguracja klienta usługi Windows Communication Foundation (WCF) można użyć, aby określić adres, powiązanie, zachowanie i umowy, właściwości "ABC" punkt końcowy klienta, w których klienci używają połączyć się z punktami końcowymi usługi. [ \<Klienta >](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) element ma [ \<punktu końcowego >](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) elementu, w których atrybuty są używane do konfigurowania punktu końcowego podstawy. Te atrybuty są omówione w sekcji "Konfigurowanie punkty końcowe" tego tematu.  
  
 [ \<Punktu końcowego >](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) zawiera również element [ \<metadanych >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element, który służy do określania ustawień do importowania i eksportowania metadanych, [ \<nagłówki >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element, który zawiera kolekcję nagłówków adresowych niestandardowe, a [ \<tożsamości >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elementu, który umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe wymiana komunikatów z nim. [ \<Nagłówki >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) i [ \<tożsamości >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elementy są częścią <xref:System.ServiceModel.EndpointAddress> zostały one omówione w [adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) tematu. Łącza do tematów, które opisują korzystanie z rozszerzenia metadanych znajdują się w podsekcji Konfigurowanie metadanych tego tematu.  
  
## <a name="configuring-endpoints"></a>Konfigurowanie punktów końcowych  
 Konfiguracja klienta jest przeznaczona do Zezwalaj na klienta określić jedną lub więcej punktów końcowych, każdy z własną nazwę adresów, a także kontaktować się z każdym odwołujące się do [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) i [ \< zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementów w konfiguracji klienta, który ma być używany do konfigurowania tego punktu końcowego. Plik konfiguracji klienta powinny mieć nazwę "W pliku App.config", ponieważ jest to nazwa, która oczekuje, że środowisko wykonawcze programu WCF. Poniższy przykład pokazuje klienta pliku konfiguracji.  
  
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
  
 Opcjonalny `name` atrybut unikatowo identyfikuje punkt końcowy dla danego kontraktu. Jest on używany przez <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> lub <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> do określenia docelowej którym punktem końcowym w konfiguracji klienta, a musi być załadowany po utworzeniu kanału do usługi. Nazwę konfiguracji punktu końcowego symbol wieloznaczny "*" jest dostępny i wskazuje <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> , należy go załadować żadnej konfiguracji punktu końcowego w pliku, pod warunkiem, że dokładnie jeden dostępny, a w przeciwnym razie metoda zgłasza wyjątek. Jeśli ten atrybut zostanie pominięty, odpowiedni punkt końcowy jest używany jako domyślny punkt końcowy skojarzony z typem określonym kontraktu. Wartością domyślną dla `name` atrybut jest pusty ciąg, który jest dopasowywany jak dowolnej innej nazwy.  
  
 Każdy punkt końcowy musi mieć adres skojarzony z nim, aby zlokalizować i zidentyfikować punkt końcowy. `address` Atrybut może służyć do określenia adresu URL, który zapewnia lokalizacji punktu końcowego. Jednak adres punktu końcowego usługi można również określić w kodzie, tworząc jednolity identyfikator zasobów (URI) i jest dodawany do <xref:System.ServiceModel.ServiceHost> przy użyciu jednej z <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody. Aby uzyskać więcej informacji, zobacz [adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md). Jak wskazuje wprowadzenie, [ \<nagłówki >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) i [ \<tożsamości >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elementy są częścią <xref:System.ServiceModel.EndpointAddress> i zostały również omówione w [ Adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) tematu.  
  
 `binding` Atrybut wskazuje typ powiązania punktu końcowego do użycia podczas łączenia z usługą. Typ musi mieć sekcję konfiguracji zarejestrowane, jeśli można się odwoływać. W poprzednim przykładzie jest to [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) sekcję, co oznacza, że punkt końcowy korzysta z <xref:System.ServiceModel.WSHttpBinding>. Mogą jednak istnieć więcej niż jedno powiązanie punktu końcowego można użyć danego typu. Każdy z nich ma swoje własne [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu w elemencie typu (powiązanie). `bindingconfiguration` Atrybut służy do rozróżnienia powiązania tego samego typu. Jego wartość jest dopasowywany `name` atrybutu [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu. Aby uzyskać więcej informacji o sposobie konfigurowania klienta powiązania, za pomocą konfiguracji, zobacz [jak: Określanie wiązania klienta w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).  
  
 `behaviorConfiguration` Atrybut jest używany, aby określić, które [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) z [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) należy używać punktu końcowego. Jego wartość jest dopasowywany `name` atrybutu [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu. Przykład za pomocą konfiguracji do określania zachowania klienta, zobacz [Konfigurowanie zachowań klienta](../../../../docs/framework/wcf/configuring-client-behaviors.md).  
  
 `contract` Atrybut określa, który kontrakt jest ujawniany przez punkt końcowy. Ta wartość jest mapowany na <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> z <xref:System.ServiceModel.ServiceContractAttribute>. Wartość domyślna to pełna nazwa typu klasy, która implementuje usługę.  
  
### <a name="configuring-metadata"></a>Konfigurowanie metadanych  
 [ \<Metadanych >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element jest używany do określania ustawień rejestracji metadane zaimportowanie rozszerzeń. Aby uzyskać więcej informacji na temat rozszerzanie systemu metadanych zobacz [rozszerzanie systemu metadanych](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).  
  
## <a name="see-also"></a>Zobacz także
- [Punkty końcowe: Adresy, powiązania i kontrakty](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [Konfigurowanie zachowań klienta](../../../../docs/framework/wcf/configuring-client-behaviors.md)
