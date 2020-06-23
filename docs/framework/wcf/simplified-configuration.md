---
title: Uproszczona konfiguracja
description: Zapoznaj się z uproszczoną konfiguracją usług WCF. .NET Framework 4.6.1 zapewnia sposób zmniejszenia rozmiaru i złożoności konfiguracji usługi.
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: defaf536d5a5b9f1479271c0976b43e9b1eb5bc4
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246041"
---
# <a name="simplified-configuration"></a>Uproszczona konfiguracja
Konfigurowanie usług Windows Communication Foundation (WCF) może być złożonym zadaniem. Istnieje wiele różnych opcji i nie zawsze można łatwo określić, które ustawienia są wymagane. Pliki konfiguracji zwiększają elastyczność usług WCF, ale również są źródłem wielu trudno znaleźć problemy. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]rozwiązuje te problemy i zapewnia sposób zmniejszenia rozmiaru i złożoności konfiguracji usługi.  
  
## <a name="simplified-configuration"></a>Uproszczona konfiguracja  
 W obszarze pliki konfiguracji usługi WCF sekcja <`system.serviceModel`> zawiera `service` element> <dla każdej hostowanej usługi. Element <`service`> zawiera kolekcję <`endpoint` elementów>, które określają punkty końcowe uwidocznione dla każdej usługi i opcjonalnie zestaw zachowań usługi. <`endpoint` elementy> określają adres, powiązanie i kontrakt udostępniane przez punkt końcowy oraz opcjonalnie powiązania konfiguracji i punktu końcowego. Sekcja <`system.serviceModel`> zawiera również `behaviors` element> <, który umożliwia określenie zachowań usługi lub punktów końcowych. W poniższym przykładzie przedstawiono `system.serviceModel` sekcję> <w pliku konfiguracji.  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true" />  
        <serviceDebug includeExceptionDetailInFaults="false" />  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]ułatwia skonfigurowanie usługi WCF poprzez usunięcie wymagania dotyczącego `service` elementu> <. Jeśli nie dodasz `service` sekcji> <ani nie dodasz żadnych punktów końcowych w `service` sekcji <> i Twoja usługa nie będzie programowo definiować żadnych punktów końcowych, zestaw domyślnych punktów końcowych zostanie automatycznie dodany do usługi, po jednej dla każdego adresu podstawowego usługi i dla każdego kontraktu zaimplementowanego przez usługę. W każdym z tych punktów końcowych adres punktu końcowego odpowiada adresowi bazowemu, powiązanie jest określane przez schemat adresów bazowych, a kontrakt jest zaimplementowany przez usługę. Jeśli nie musisz określać żadnych punktów końcowych lub zachowań usług lub wprowadzić żadnych zmian w ustawieniach powiązania, nie musisz określać w ogóle pliku konfiguracji usługi. Jeśli usługa implementuje dwie kontrakty, a host włącza transporty HTTP i TCP hosta usługi, program tworzy cztery domyślne punkty końcowe, po jednym dla każdego kontraktu przy użyciu poszczególnych transportów. Aby utworzyć domyślne punkty końcowe, Host usługi musi wiedzieć, jakie powiązania mają być używane. Te ustawienia są określone w sekcji <`protocolMappings`> w `system.serviceModel` sekcji <>. `protocolMappings`Sekcja> <zawiera listę schematów protokołu transportowego mapowanych na typy powiązań. Host usługi korzysta z adresów bazowych, które są do niego przesyłane, aby określić, które powiązanie ma być używane. Poniższy przykład używa `protocolMappings` elementu> <.  
  
> [!WARNING]
> Zmiana domyślnych elementów konfiguracji, takich jak powiązania lub zachowania, może mieć wpływ na usługi zdefiniowane na niższych poziomach w hierarchii konfiguracji, ponieważ mogą one korzystać z tych domyślnych powiązań i zachowań. Z tego względu, inne zmiany powiązań domyślnych i zachowań muszą mieć świadomość, że te zmiany mogą wpływać na inne usługi w hierarchii.  
  
> [!NOTE]
> Usługi hostowane w usłudze Internet Information Services (IIS) lub Windows Process Activation Service (WAS) używają katalogu wirtualnego jako adresu podstawowego.  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 W poprzednim przykładzie punkt końcowy o adresie podstawowym rozpoczynającym się od schematu "http" używa <xref:System.ServiceModel.BasicHttpBinding> . Punkt końcowy o adresie podstawowym rozpoczynającym się od schematu "net. TCP" używa <xref:System.ServiceModel.NetTcpBinding> . Możesz przesłonić ustawienia w lokalnym pliku App.config lub Web.config.  
  
 Każdy element w `protocolMappings` sekcji> <musi określać schemat i powiązanie. Opcjonalnie można określić `bindingConfiguration` atrybut określający konfigurację powiązania w `bindings` sekcji <> pliku konfiguracji. Jeśli nie `bindingConfiguration` zostanie określona, zostanie użyta Konfiguracja powiązania anonimowego dla odpowiedniego typu powiązania.  
  
 Zachowania usługi są skonfigurowane dla domyślnych punktów końcowych przy użyciu <anonimowe `behavior`> sekcje w `serviceBehaviors` sekcji <>. Wszystkie nienazwane <`behavior` elementy> w <`serviceBehaviors`> są używane do konfigurowania zachowań usługi. Na przykład następujący plik konfiguracji umożliwia Publikowanie metadanych usługi dla wszystkich usług na hoście.  
  
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
  
 Zachowania punktów końcowych konfiguruje się za pomocą <anonimowe> sekcjach `behavior` w `serviceBehaviors` sekcji <>.  
  
 Poniższy przykład to plik konfiguracji odpowiadający pierwszemu na początku tego tematu, który korzysta z uproszczonego modelu konfiguracji.  
  
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
> Ta funkcja odnosi się tylko do konfiguracji usługi WCF, a nie konfiguracji klienta. W większości przypadków konfiguracja klienta WCF zostanie wygenerowana przez narzędzie, takie jak svcutil.exe lub dodanie odwołania do usługi z programu Visual Studio. W przypadku ręcznego konfigurowania klienta WCF należy dodać \<client> element do konfiguracji i określić wszystkie punkty końcowe, które chcesz wywołać.  
  
## <a name="see-also"></a>Zobacz też

- [Konfigurowanie usług za pomocą plików konfiguracji](configuring-services-using-configuration-files.md)
- [Konfigurowanie powiązań dla usług](configuring-bindings-for-wcf-services.md)
- [Konfigurowanie powiązań dostarczanych przez system](./feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług](configuring-services.md)
- [Konfigurowanie usług WCF](configuring-services.md)
- [Konfigurowanie usług WCF w kodzie](configuring-wcf-services-in-code.md)
