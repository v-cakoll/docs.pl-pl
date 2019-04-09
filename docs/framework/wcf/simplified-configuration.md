---
title: Uproszczona konfiguracja
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 13cf8bd46ef3aabb011cb2ddd207963235468662
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184057"
---
# <a name="simplified-configuration"></a>Uproszczona konfiguracja
Konfigurowanie usług Windows Communication Foundation (WCF) może być złożonym zadaniem. Istnieje wiele różnych opcji, a nie zawsze jest łatwo określić, jakie ustawienia są wymagane. Gdy pliki konfiguracyjne zwiększyć elastyczność usługi WCF, są również źródła dla wielu trudno znaleźć problemy. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] te problemy zostały rozwiązane i zapewnia sposób, aby zmniejszyć rozmiar i złożoność konfiguracji usługi.  
  
## <a name="simplified-configuration"></a>Uproszczona konfiguracja  
 W plikach konfiguracji usługi WCF <`system.serviceModel`> zawiera sekcja <`service`>, element dla każdej usługi hostowanej. <`service`> Element zawiera zbiór <`endpoint`> elementy, które określają punktów końcowych udostępniane dla każdej usługi i opcjonalnie zestaw zachowań usługi. <`endpoint`> Elementy Określ adres, powiązania i kontrakt udostępnianych przez punkt końcowy i, opcjonalnie, Konfiguracja powiązania i zachowań punktu końcowego. <`system.serviceModel`> Sekcja zawiera również <`behaviors`> element, który służy do określania zachowania usługi lub punktu końcowego. W poniższym przykładzie przedstawiono <`system.serviceModel`> sekcji w pliku konfiguracji.  
  
```  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true">  
        <serviceDebug includeExceptionDetailInFaults="false">  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <bindings>  
   <basicHttpBinding>  
      <binding name=MyBindingConfig"  
               maxBufferSize="100"  
               maxReceiveBufferSize="100" />  
   </basicHttpBinding>  
   </bindings>   <services>  
    <service behaviorConfiguration="MyServiceBehavior"  
             name="MyService">  
      <endpoint address=""  
                binding="basicHttpBinding"  
                contract="ICalculator"  
                bindingConfiguration="MyBindingConfig" />  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange"/>  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Umożliwia konfigurowanie usługi WCF, łatwiej, usuwając konieczność <`service`> element. Jeśli nie dodasz <`service`> sekcji, lub dodać żadnych punktów końcowych w <`service`> sekcja i usługi programistyczne definiuje żadnych punktów końcowych, a następnie zestaw domyślnych punktów końcowych są automatycznie dodawane do usługi, jednej dla każdego adres podstawowy usługi i dla każdej umowy implementowane przez usługę. W każdym z tych punktów końcowych adres punktu końcowego odpowiada adres podstawowy, powiązanie jest określana przez schemat adresu podstawowego i kontrakt jest implementowany przez usługi. Jeśli nie trzeba określać żadnych punktów końcowych lub zachowania usługi lub wprowadzone zmiany ustawień powiązania, nie musisz określić plik konfiguracji usługi na wszystkich. Jeśli zaimplementowano dwa kontrakty i host włącza transportu protokołów HTTP i TCP hosta usługi tworzy cztery domyślne punkty końcowe, jeden dla każdej umowy, za pomocą każdego transportu. W celu utworzenia domyślnych punktów końcowych hosta usług musi wiedzieć, jakie powiązania do użycia. Te ustawienia są określone w <`protocolMappings`> sekcji w ramach <`system.serviceModel`> sekcji. <`protocolMappings`> Sekcja zawiera listę mapowany do typów powiązań schematami protokołu transportu. Host usługi używa przekazany adres podstawowy, aby określić które powiązania do użycia. W poniższym przykładzie użyto <`protocolMappings`> element.  
  
> [!WARNING]
>  Zmiana domyślnego elementów konfiguracji, takich jak powiązania lub zachowań, mogą mieć wpływ na usługi zdefiniowane w niższych poziomach hierarchii konfiguracji, ponieważ mogą one używać te domyślne powiązania i zachowania. W związku z tym, kto zmienia domyślne powiązania i zachowania musi należy pamiętać, że te zmiany mogą wpłynąć na inne usługi w hierarchii.  
  
> [!NOTE]
>  Usług hostowanych w ramach usług Internet Information Services (IIS) lub Windows Process Activation Service (WAS) Użyj wirtualnego katalogu jako ich adres podstawowy.  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 W poprzednim przykładzie używa się punkt końcowy z adres podstawowy, który rozpoczyna się od schematu "http" <xref:System.ServiceModel.BasicHttpBinding>. Punkt końcowy z adres podstawowy, który rozpoczyna się od schematu "net.tcp" używa <xref:System.ServiceModel.NetTcpBinding>. Możesz przesłonić ustawienia w lokalnym pliku App.config lub Web.config.  
  
 Każdy element w obrębie <`protocolMappings`> sekcji, należy określić schemat i powiązania. Opcjonalnie można określić `bindingConfiguration` atrybut, który określa konfigurację powiązania w ramach <`bindings`> sekcji w pliku konfiguracji. Jeśli nie `bindingConfiguration` jest określona, używana jest Konfiguracja tworzenie anonimowych powiązań typu odpowiednie powiązanie.  
  
 Zachowania usług są skonfigurowane dla domyślnych punktów końcowych przy użyciu anonimowego <`behavior`> sekcje w ramach <`serviceBehaviors`> sekcji. Dowolny nienazwane <`behavior`> elementów w obrębie <`serviceBehaviors`> są używane do konfigurowania zachowania usługi. Na przykład następujący plik konfiguracji umożliwia publikowanie metadanych usługi dla wszystkich usług w ramach hosta.  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <!-- No <service> tag is necessary. Default endpoints are added to the service -->  
    <!-- The service behavior with name="" is picked up by the service -->  
 </system.serviceModel>  
```  
  
 Zachowań punktu końcowego są konfigurowane przy użyciu anonimowego <`behavior`> sekcje w ramach <`serviceBehaviors`> sekcji.  
  
 Poniższy przykład jest równoważny do przedstawionego na początku tego tematu, który używa modelu uproszczona konfiguracja pliku konfiguracji.  
  
```xml  
<system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <serviceMetadata httpGetEnabled="true" />
          <serviceDebug includeExceptionDetailInFaults="false" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <bindings>
       <basicHttpBinding>
          <binding maxBufferSize="100"
                   maxReceiveBufferSize="100" />
       </basicHttpBinding>
    </bindings>
    <!-- No <service> tag is necessary. Default endpoints will be added to the service -->
    <!-- The service behavior with name="" will be picked up by the service -->
    <protocolMapping>
      <add scheme="http" binding="basicHttpBinding" />
  </protocolMapping>
  </system.serviceModel>
```  
  
> [!IMPORTANT]
>  Ta funkcja dotyczy tylko do konfiguracji usługi WCF nie konfiguracji klienta. Większości przypadków Konfiguracja klienta programu WCF będą generowane przez narzędzia, takiego jak svcutil.exe lub dodanie odwołania do usługi w programie Visual Studio. W przypadku ręcznego konfigurowania klienta programu WCF należy dodać \<klienta > element do konfiguracji i określ żadnych punktów końcowych, które chcesz wywołać.  
  
## <a name="see-also"></a>Zobacz także

- [Konfigurowanie usług za pomocą plików konfiguracji](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)
- [Konfigurowanie powiązań dla usług](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług](../../../docs/framework/wcf/configuring-services.md)
- [Konfigurowanie usług WCF](configuring-services.md)
- [Konfigurowanie usług WCF w kodzie](../../../docs/framework/wcf/configuring-wcf-services-in-code.md)
