---
title: Konfiguracja klienta
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: 141b7f7fc04f98f267ce520544fb89451beac7b6
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463868"
---
# <a name="client-configuration"></a>Konfiguracja klienta
Za pomocą konfiguracji klienta Programu Windows Communication Foundation (WCF) można określić adres, powiązanie, zachowanie i kontrakt, właściwości "ABC" punktu końcowego klienta, których klienci używają do łączenia się z punktami końcowymi usługi. Element [ \<>klienta](../../configure-apps/file-schema/wcf/client.md) ma [ \<element>punktu końcowego,](../../configure-apps/file-schema/wcf/endpoint-of-client.md) którego atrybuty są używane do konfigurowania abc punktu końcowego. Te atrybuty zostały omówione w sekcji [Konfigurowanie punktów końcowych.](#configuring-endpoints)  
  
 Element [ \<>punktu końcowego](../../configure-apps/file-schema/wcf/endpoint-of-client.md) [ \<](../../configure-apps/file-schema/wcf/headers.md) [ \<](../../configure-apps/file-schema/wcf/metadata.md) zawiera również metadane>element, który jest używany do określania ustawień importowania i eksportowania metadanych, nagłówki>element, który zawiera zbiór nagłówków adresów niestandardowych i element [ \<>tożsamości,](../../configure-apps/file-schema/wcf/identity.md) który umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe wymiany wiadomości z nim. [ \<Nagłówki>](../../configure-apps/file-schema/wcf/headers.md) i [ \<tożsamości>](../../configure-apps/file-schema/wcf/identity.md) elementy są częścią <xref:System.ServiceModel.EndpointAddress> i są omówione w [adresy](../../wcf/feature-details/endpoint-addresses.md) artykułu. Łącza do tematów, które wyjaśniają użycie rozszerzeń metadanych znajdują się w sekcji [Konfigurowanie metadanych.](#configuring-metadata)  
  
## <a name="configuring-endpoints"></a>Konfigurowanie punktów końcowych  
 Konfiguracja klienta jest przeznaczony do umożliwienia klientowi określić jeden lub więcej punktów końcowych, każdy z własną nazwą, adres i umowy, z każdego odwoływania się do [ \<powiązań>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) i [ \<zachowania>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementy w konfiguracji klienta, które mają być używane do konfigurowania tego punktu końcowego. Plik konfiguracji klienta powinien mieć nazwę "App.config", ponieważ jest to nazwa oczekiwana przez środowisko uruchomieniowe WCF. W poniższym przykładzie przedstawiono plik konfiguracji klienta.  
  
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
  
 Atrybut `name` opcjonalny jednoznacznie identyfikuje punkt końcowy dla danego kontraktu. Jest on używany <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> przez <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> lub przez określić, który punkt końcowy w konfiguracji klienta jest przeznaczony i musi być ładowany, gdy kanał jest tworzony do usługi. Nazwa konfiguracji punktu końcowego\*symbolu wieloznacznego <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> " jest dostępna i wskazuje do metody, że należy załadować dowolną konfigurację punktu końcowego w pliku, pod warunkiem, że jest dokładnie jeden dostępny i w przeciwnym razie zgłasza wyjątek. Jeśli ten atrybut zostanie pominięty, odpowiedni punkt końcowy jest używany jako domyślny punkt końcowy skojarzony z określonym typem kontraktu. Wartość domyślna `name` dla atrybutu jest pusty ciąg, który jest dopasowany jak każda inna nazwa.  
  
 Każdy punkt końcowy musi mieć adres skojarzony z nim, aby zlokalizować i zidentyfikować punkt końcowy. Atrybut `address` może służyć do określenia adresu URL, który zapewnia lokalizację punktu końcowego. Ale adres punktu końcowego usługi można również określić w kodzie, tworząc jednolity identyfikator <xref:System.ServiceModel.ServiceHost> zasobu (URI) i jest dodawany do przy użyciu jednej z <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metod. Aby uzyskać więcej informacji, zobacz [Adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md). Jak wskazuje wprowadzenie, [ \<nagłówki>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) i [ \<tożsamości>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elementy są częścią <xref:System.ServiceModel.EndpointAddress> i są również omówione w [adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) tematu.  
  
 Atrybut `binding` wskazuje typ powiązania punkt końcowy oczekuje się używać podczas łączenia się z usługą. Typ musi mieć sekcję konfiguracji zarejestrowanej, jeśli ma się do niej odwoływać. W poprzednim przykładzie <xref:System.ServiceModel.WSHttpBinding>jest [ \<to wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) sekcji, która wskazuje, że punkt końcowy używa . Ale może istnieć więcej niż jedno powiązanie danego typu, który można użyć punktu końcowego. Każdy z nich [ \<](../../configure-apps/file-schema/wcf/bindings.md) ma swój własny element wiązania>w ramach elementu typu (binding). Atrybut `bindingconfiguration` jest używany do rozróżniania powiązań tego samego typu. Jego wartość jest dopasowywała się do `name` atrybutu [ \<elementu wiązania>.](../../configure-apps/file-schema/wcf/bindings.md) Aby uzyskać więcej informacji na temat konfigurowania powiązania klienta przy użyciu konfiguracji, zobacz [Jak: Określanie powiązania klienta w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).  
  
 Atrybut `behaviorConfiguration` jest używany do [ \<określenia,](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) które zachowanie>[ \<endpointBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) punkt końcowy powinien używać. Jego wartość jest dopasowywała się do `name` atrybutu [ \<zachowania>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu. Na przykład użycia konfiguracji do określania zachowań klientów zobacz [Konfigurowanie zachowań klientów](../../../../docs/framework/wcf/configuring-client-behaviors.md).  
  
 Atrybut `contract` określa, który kontrakt punkt końcowy jest uwidacznianie. Ta wartość jest <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> mapowana na wartość <xref:System.ServiceModel.ServiceContractAttribute>. Wartość domyślna to pełna nazwa typu klasy, która implementuje usługę.  
  
### <a name="configuring-metadata"></a>Konfigurowanie metadanych  
 [ \<Metadane>](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element jest używany do określania ustawień używanych do rejestrowania rozszerzeń importu metadanych. Aby uzyskać więcej informacji na temat rozszerzania systemu metadanych, zobacz [Rozszerzanie systemu metadanych](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).  
  
## <a name="see-also"></a>Zobacz też

- [Punkty końcowe: Adresy, powiązania i kontrakty](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [Konfigurowanie zachowań klienta](../../../../docs/framework/wcf/configuring-client-behaviors.md)
