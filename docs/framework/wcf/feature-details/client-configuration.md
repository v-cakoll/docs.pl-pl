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
# <a name="client-configuration"></a>Konfiguracja klienta
Za pomocą konfiguracji klienta Windows Communication Foundation (WCF) można określić adres, powiązanie, zachowanie i kontrakt, czyli właściwości "ABC" punktu końcowego klienta używanego przez klientów do łączenia się z punktami końcowymi usługi. [\<client>](../../configure-apps/file-schema/wcf/client.md)Element ma element, [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) którego atrybuty są używane do konfigurowania punktu końcowego ABCs. Te atrybuty zostały omówione w sekcji [Konfigurowanie punktów końcowych](#configuring-endpoints) .  
  
 [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md)Element zawiera również [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) element, który jest używany do określania ustawień importowania i eksportowania metadanych, [\<headers>](../../configure-apps/file-schema/wcf/headers.md) element, który zawiera kolekcję niestandardowych nagłówków adresów i [\<identity>](../../configure-apps/file-schema/wcf/identity.md) element, który umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe wymieniające z nim wiadomości. [\<headers>](../../configure-apps/file-schema/wcf/headers.md)Elementy i są [\<identity>](../../configure-apps/file-schema/wcf/identity.md) częścią <xref:System.ServiceModel.EndpointAddress> i zostały omówione w artykule dotyczącej [adresów](endpoint-addresses.md) . Linki do tematów, które wyjaśniają korzystanie z rozszerzeń metadanych, znajdują się w sekcji [Konfigurowanie metadanych](#configuring-metadata) .  
  
## <a name="configuring-endpoints"></a>Konfigurowanie punktów końcowych  
 Konfiguracja klienta została zaprojektowana tak, aby umożliwić klientowi określenie co najmniej jednego punktu końcowego, z każdą nazwą, adresem i umową, przy czym każdy odwołuje się do [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) elementów i w konfiguracji klienta, aby można było użyć ich do skonfigurowania tego punktu końcowego. Plik konfiguracji klienta powinien mieć nazwę "App.config", ponieważ jest to nazwa, której oczekuje środowisko uruchomieniowe WCF. Poniższy przykład przedstawia plik konfiguracji klienta.  
  
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
  
 Opcjonalny `name` atrybut jednoznacznie identyfikuje punkt końcowy danego kontraktu. Jest on używany przez <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> lub przez program, <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> Aby określić, który punkt końcowy w konfiguracji klienta jest ukierunkowany i musi być załadowany podczas tworzenia kanału do obsługi. Nazwa konfiguracji wieloznacznego punktu końcowego " \* " jest dostępna i wskazuje <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> metodę, która powinna ładować każdą konfigurację punktu końcowego w pliku, pod warunkiem, że jest to dokładnie jedna dostępna i w przeciwnym razie zgłasza wyjątek. Jeśli ten atrybut zostanie pominięty, odpowiadający mu punkt końcowy jest używany jako domyślny punkt końcowy skojarzony z określonym typem kontraktu. Wartość domyślna dla `name` atrybutu jest pustym ciągiem, który jest dopasowany jak dowolną inną nazwę.  
  
 Każdy punkt końcowy musi mieć skojarzony z nim adres, aby zlokalizować i zidentyfikować punkt końcowy. Ten `address` atrybut może służyć do określania adresu URL, który zawiera lokalizację punktu końcowego. Ale adres punktu końcowego usługi można także określić w kodzie, tworząc Uniform Resource Identifier (URI) i jest dodawany do <xref:System.ServiceModel.ServiceHost> metody przy użyciu jednej z <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metod. Aby uzyskać więcej informacji, zobacz [Addressing](endpoint-addresses.md). Ponieważ wprowadzenie wskazuje, [\<headers>](../../configure-apps/file-schema/wcf/headers.md) [\<identity>](../../configure-apps/file-schema/wcf/identity.md) elementy i są częścią <xref:System.ServiceModel.EndpointAddress> i są również omówione w temacie [addresss (adresy](endpoint-addresses.md) ).  
  
 Ten `binding` atrybut wskazuje typ powiązania, którego punkt końcowy ma używać podczas łączenia się z usługą. Aby można było odwołać, typ musi mieć zarejestrowaną sekcję konfiguracyjną. W poprzednim przykładzie jest to [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) sekcja, która wskazuje, że punkt końcowy używa <xref:System.ServiceModel.WSHttpBinding> . Może jednak istnieć więcej niż jedno powiązanie danego typu, które może być używane przez punkt końcowy. Każdy z nich ma swój własny [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element w elemencie typu (Binding). Ten `bindingconfiguration` atrybut służy do rozróżniania powiązań tego samego typu. Jego wartość jest zgodna z `name` atrybutem [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elementu. Aby uzyskać więcej informacji o konfigurowaniu powiązania klienta przy użyciu konfiguracji, zobacz [How to: Określanie powiązania klienta w konfiguracji](../how-to-specify-a-client-binding-in-configuration.md).  
  
 Ten `behaviorConfiguration` atrybut służy do określania, który [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) z [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) punktów końcowych ma być używany. Jego wartość jest zgodna z `name` atrybutem [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu. Przykład korzystania z konfiguracji w celu określenia zachowań klienta można znaleźć w temacie [Configuring Client Behaviors](../configuring-client-behaviors.md).  
  
 Ten `contract` atrybut określa, który kontrakt jest ujawniany przez punkt końcowy. Ta wartość jest mapowana na <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> <xref:System.ServiceModel.ServiceContractAttribute> . Wartość domyślna to pełna nazwa typu klasy implementującej usługę.  
  
### <a name="configuring-metadata"></a>Konfigurowanie metadanych  
 [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md)Element służy do określania ustawień używanych do rejestrowania rozszerzeń importu metadanych. Aby uzyskać więcej informacji na temat rozszerzania systemu metadanych, zobacz [Rozszerzanie systemu metadanych](../extending/extending-the-metadata-system.md).  
  
## <a name="see-also"></a>Zobacz też

- [Punkty końcowe: Adresy, powiązania i kontrakty](endpoints-addresses-bindings-and-contracts.md)
- [Konfigurowanie zachowań klienta](../configuring-client-behaviors.md)
