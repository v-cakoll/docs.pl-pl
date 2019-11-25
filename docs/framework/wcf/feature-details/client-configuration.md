---
title: Konfiguracja klienta
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: 6a5cbf5d536af8649b0b8bb93600e94a48c507c1
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141771"
---
# <a name="client-configuration"></a>Konfiguracja klienta
Za pomocą konfiguracji klienta Windows Communication Foundation (WCF) można określić adres, powiązanie, zachowanie i kontrakt, czyli właściwości "ABC" punktu końcowego klienta używanego przez klientów do łączenia się z punktami końcowymi usługi. [\<klienta >](../../configure-apps/file-schema/wcf/client.md) element ma [\<punkt końcowy >](../../configure-apps/file-schema/wcf/endpoint-of-client.md) elementu, którego atrybuty są używane do konfigurowania punktu końcowego ABCs. Te atrybuty zostały omówione w sekcji [Konfigurowanie punktów końcowych](#configuring-endpoints) .  
  
 Element [\<Endpoint](../../configure-apps/file-schema/wcf/endpoint-of-client.md) zawiera również element [> metadanych\<](../../configure-apps/file-schema/wcf/metadata.md) , który jest używany do określania ustawień importowania i eksportowania metadanych,\<nagłówków, [>](../../configure-apps/file-schema/wcf/headers.md) element, który zawiera kolekcję niestandardowych nagłówków adresów oraz [\<> tożsamości](../../configure-apps/file-schema/wcf/identity.md) , który umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe wymieniające z nim wiadomości. [\<nagłówki >](../../configure-apps/file-schema/wcf/headers.md) i [\<](../../configure-apps/file-schema/wcf/identity.md) elementów są częścią <xref:System.ServiceModel.EndpointAddress> i zostały omówione w artykule [adresy](../../wcf/feature-details/endpoint-addresses.md) . Linki do tematów, które wyjaśniają korzystanie z rozszerzeń metadanych, znajdują się w sekcji [Konfigurowanie metadanych](#configuring-metadata) .  
  
## <a name="configuring-endpoints"></a>Konfigurowanie punktów końcowych  
 Konfiguracja klienta została zaprojektowana tak, aby umożliwić klientowi określenie co najmniej jednego punktu końcowego, z którego każdy ma własną nazwę, adres i kontrakt, z każdą odwołującą się do [\<powiązań >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) i [zachowania\<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementów w konfiguracji klienta, które będą używane do konfigurowania tego punktu końcowego. Plik konfiguracji klienta powinien mieć nazwę "App. config", ponieważ jest to nazwa, której oczekuje środowisko uruchomieniowe WCF. Poniższy przykład przedstawia plik konfiguracji klienta.  
  
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
  
 Opcjonalny atrybut `name` jednoznacznie identyfikuje punkt końcowy danego kontraktu. Jest on używany przez <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> lub przez <xref:System.ServiceModel.ClientBase%601.%23ctor%2A>, aby określić, który punkt końcowy w konfiguracji klienta jest ukierunkowany i musi być załadowany w przypadku utworzenia kanału do obsługi. Nazwa konfiguracji wieloznacznego punktu końcowego "\*" jest dostępna i wskazuje na metodę <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A>, która powinna ładować dowolną konfigurację punktu końcowego w pliku, pod warunkiem, że jest ona dokładnie dostępna i w przeciwnym razie zgłasza wyjątek. Jeśli ten atrybut zostanie pominięty, odpowiadający mu punkt końcowy jest używany jako domyślny punkt końcowy skojarzony z określonym typem kontraktu. Wartość domyślna atrybutu `name` jest pustym ciągiem, który jest dopasowany jak jakakolwiek inna nazwa.  
  
 Każdy punkt końcowy musi mieć skojarzony z nim adres, aby zlokalizować i zidentyfikować punkt końcowy. Atrybutu `address` można użyć, aby określić adres URL, który zawiera lokalizację punktu końcowego. Ale adres punktu końcowego usługi można także określić w kodzie, tworząc Uniform Resource Identifier (URI) i jest dodawany do <xref:System.ServiceModel.ServiceHost> przy użyciu jednej z metod <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>. Aby uzyskać więcej informacji, zobacz [Addressing](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md). Ponieważ wprowadzenie wskazuje, [nagłówki\<](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) i [\<](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elementów są częścią <xref:System.ServiceModel.EndpointAddress> i zostały omówione w temacie [addresss (adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) ).  
  
 Atrybut `binding` wskazuje typ powiązania, którego punkt końcowy ma używać podczas łączenia się z usługą. Aby można było odwołać, typ musi mieć zarejestrowaną sekcję konfiguracyjną. W poprzednim przykładzie jest to [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) , co oznacza, że punkt końcowy używa <xref:System.ServiceModel.WSHttpBinding>. Może jednak istnieć więcej niż jedno powiązanie danego typu, które może być używane przez punkt końcowy. Każdy z nich ma swoje własne [\<powiązania >](../../configure-apps/file-schema/wcf/bindings.md) elementu w elemencie typu (Binding). Atrybut `bindingconfiguration` jest używany do rozróżniania powiązań tego samego typu. Jego wartość jest zgodna z atrybutem `name` elementu [\<powiązania >](../../configure-apps/file-schema/wcf/bindings.md) . Aby uzyskać więcej informacji o konfigurowaniu powiązania klienta przy użyciu konfiguracji, zobacz [How to: Określanie powiązania klienta w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).  
  
 Atrybut `behaviorConfiguration` służy do określania, które [\<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) [\<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) punkt końcowy powinien używać. Jego wartość jest zgodna z atrybutem `name` [\<zachowań >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) . Przykład korzystania z konfiguracji w celu określenia zachowań klienta można znaleźć w temacie [Configuring Client Behaviors](../../../../docs/framework/wcf/configuring-client-behaviors.md).  
  
 Atrybut `contract` określa, który kontrakt jest ujawniany przez punkt końcowy. Ta wartość jest mapowana na <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> <xref:System.ServiceModel.ServiceContractAttribute>. Wartość domyślna to pełna nazwa typu klasy implementującej usługę.  
  
### <a name="configuring-metadata"></a>Konfigurowanie metadanych  
 Element [> metadata\<](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) służy do określania ustawień używanych do rejestrowania rozszerzeń importu metadanych. Aby uzyskać więcej informacji na temat rozszerzania systemu metadanych, zobacz [Rozszerzanie systemu metadanych](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).  
  
## <a name="see-also"></a>Zobacz także

- [Punkty końcowe: adresy, powiązania i kontrakty](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [Konfigurowanie zachowań klienta](../../../../docs/framework/wcf/configuring-client-behaviors.md)
