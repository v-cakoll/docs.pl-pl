---
title: Uproszczona konfiguracja
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 4e316290c045b75896c61e36c1646440c18678e2
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249633"
---
# <a name="simplified-configuration"></a>Uproszczona konfiguracja
Konfigurowanie usług Windows Communication Foundation (WCF) może być złożonym zadaniem. Istnieje wiele różnych opcji i nie zawsze jest łatwo określić, jakie ustawienia są wymagane. Podczas gdy pliki konfiguracyjne zwiększają elastyczność usług WCF, są one również źródłem wielu trudnych do znalezienia problemów. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]rozwiązuje te problemy i zapewnia sposób zmniejszenia rozmiaru i złożoności konfiguracji usługi.  
  
## <a name="simplified-configuration"></a>Uproszczona konfiguracja  
 W plikach konfiguracyjnych usługi WCF sekcja <`system.serviceModel`> zawiera <`service`> element dla każdej hostowanej usługi. <`service`> element zawiera kolekcję <`endpoint`> elementów, które określają punkty końcowe udostępniane dla każdej usługi i opcjonalnie zestaw zachowań usługi. Elementy <`endpoint`> określają adres, powiązanie i kontrakt udostępniane przez punkt końcowy oraz opcjonalnie powiązanie zachowań konfiguracji i punktu końcowego. Sekcja `system.serviceModel` <> zawiera również element `behaviors`> <, który umożliwia określenie zachowań usługi lub punktu końcowego. W poniższym przykładzie przedstawiono sekcję `system.serviceModel`> <pliku konfiguracyjnego.  
  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]ułatwia konfigurowanie usługi WCF przez usunięcie wymagań dotyczących elementu `service` <>. Jeśli nie dodasz <`service` sekcji> lub nie dodasz żadnych punktów końcowych `service` w sekcji <>, a usługa nie definiuje programowo żadnych punktów końcowych, zestaw domyślnych punktów końcowych zostanie automatycznie dodany do usługi, po jednym dla każdego adresu podstawowego usługi i dla każdej umowy zaimplementowanej przez usługę. W każdym z tych punktów końcowych adres punktu końcowego odpowiada adres podstawowy, powiązanie jest określana przez schemat adresów podstawowych i umowy jest zaimplementowane przez usługę. Jeśli nie trzeba określić żadnych punktów końcowych lub zachowań usługi lub wprowadzić żadnych zmian ustawień powiązania, nie trzeba w ogóle określić plik konfiguracji usługi. Jeśli usługa implementuje dwa kontrakty i hosta włącza transporty HTTP i TCP hosta usługi tworzy cztery domyślne punkty końcowe, po jednym dla każdego kontraktu przy użyciu każdego transportu. Aby utworzyć domyślne punkty końcowe hosta usługi musi wiedzieć, jakie powiązania do użycia. Te ustawienia są określone w `protocolMappings` sekcji> <w sekcji `system.serviceModel` <>. Sekcja <`protocolMappings`> zawiera listę schematów protokołu transportu mapowanych na typy powiązań. Host usługi używa adresów podstawowych przekazanych do niego, aby określić, które powiązanie do użycia. W poniższym przykładzie użyto <`protocolMappings`> elementu.  
  
> [!WARNING]
> Zmiana domyślnych elementów konfiguracji, takich jak powiązania lub zachowania, może mieć wpływ na usługi zdefiniowane na niższych poziomach hierarchii konfiguracji, ponieważ mogą one używać tych domyślnych powiązań i zachowań. W związku z tym kto zmienia domyślne powiązania i zachowania musi mieć świadomość, że te zmiany mogą mieć wpływ na inne usługi w hierarchii.  
  
> [!NOTE]
> Usługi hostowane w ramach internetowych usług informacyjnych (IIS) lub usługi aktywacji procesów systemu Windows (WAS) używają katalogu wirtualnego jako adresu podstawowego.  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 W poprzednim przykładzie punkt końcowy z adresem podstawowym, który rozpoczyna się <xref:System.ServiceModel.BasicHttpBinding>od schematu "http", używa programu . Punkt końcowy z adresem podstawowym rozpoczynającym się od schematu "net.tcp" używa schematu <xref:System.ServiceModel.NetTcpBinding>. Ustawienia można zastąpić w lokalnym pliku App.config lub Web.config.  
  
 Każdy element w sekcji `protocolMappings` <> musi określać schemat i powiązanie. Opcjonalnie można określić `bindingConfiguration` atrybut, który określa konfigurację powiązania `bindings` w <> sekcji pliku konfiguracji. Jeśli `bindingConfiguration` nie jest określony, używana jest konfiguracja powiązania anonimowego odpowiedniego typu powiązania.  
  
 Zachowania usługi są konfigurowane dla domyślnych punktów końcowych `behavior` przy użyciu anonimowych <sekcji `serviceBehaviors`> w <> sekcjach. Wszystkie nienazwane <`behavior`> elementy w <`serviceBehaviors`> są używane do konfigurowania zachowań usługi. Na przykład następujący plik konfiguracji umożliwia publikowanie metadanych usługi dla wszystkich usług w hoście.  
  
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
  
 Zachowania punktów końcowych są konfigurowane przy `behavior` użyciu anonimowych <> sekcje `serviceBehaviors` w <> sekcjach.  
  
 Poniższy przykład jest plikiem konfiguracji równoważnym z plikiem na początku tego tematu, który używa uproszczonego modelu konfiguracji.  
  
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
> Ta funkcja dotyczy tylko konfiguracji usługi WCF, a nie konfiguracji klienta. W większości razy konfiguracja klienta WCF zostanie wygenerowana przez narzędzie, takie jak svcutil.exe lub dodanie odwołania do usługi z programu Visual Studio. Jeśli ręcznie konfigurujesz klienta WCF, musisz dodać \<element> klienta do konfiguracji i określić wszystkie punkty końcowe, które chcesz wywołać.  
  
## <a name="see-also"></a>Zobacz też

- [Konfigurowanie usług za pomocą plików konfiguracji](configuring-services-using-configuration-files.md)
- [Konfigurowanie powiązań dla usług](configuring-bindings-for-wcf-services.md)
- [Konfigurowanie powiązań dostarczanych przez system](./feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług](configuring-services.md)
- [Konfigurowanie usług WCF](configuring-services.md)
- [Konfigurowanie usług WCF w kodzie](configuring-wcf-services-in-code.md)
