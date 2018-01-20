---
title: Uproszczona konfiguracja
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 334dfce44b1f0a7b6b38f509f2f0a346ef90630f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="simplified-configuration"></a>Uproszczona konfiguracja
Konfigurowanie [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] usługi może być złożonym zadaniem. Istnieje wiele różnych opcji, a nie zawsze jest łatwa do ustalenia, jakie ustawienia są wymagane. Podczas konfiguracji plików zwiększyć elastyczność [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usług, również są źródła dla wielu trudne do znalezienia problemów. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]te problemy zostały rozwiązane oraz przedstawiono sposób, aby zmniejszyć rozmiar i złożoność konfiguracji usługi.  
  
## <a name="simplified-configuration"></a>Uproszczona konfiguracja  
 W [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] pliki konfiguracji usługi <`system.serviceModel`> zawiera sekcji <`service`> element dla każdej usługi hostowanej. <`service`> Kolekcja zawiera element <`endpoint`> elementy, które określ punkty końcowe udostępniane dla każdej usługi i opcjonalnie zestaw zachowań usługi. <`endpoint`> Elementy Podaj adres, powiązanie, i kontraktu udostępniane przez punkt końcowy i opcjonalnie powiązania konfiguracji i zachowania punktu końcowego. <`system.serviceModel`> Sekcja zawiera również <`behaviors`> element, który pozwala na określenie zachowania usługi lub punktu końcowego. W poniższym przykładzie przedstawiono <`system.serviceModel`> pliku konfiguracji.  
  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]Umożliwia konfigurowanie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługę, łatwiejsze usuwając konieczność <`service`> elementu. Jeśli nie dodasz <`service`> sekcji lub dodać żadnych punktów końcowych w <`service`> sekcji, a usługą nie programowo definiuje żadnych punktów końcowych, a następnie zestaw domyślnych punktów końcowych są automatycznie dodawane do usługi, po jednej dla każdego adres podstawowy usługi i dla każdej umowy zaimplementowana przez usługę. W każdym z tych punktów końcowych odpowiada adres podstawowy adres punktu końcowego, powiązania jest określany przez adres podstawowy schemat i kontrakt jest implementowany przez usługę. Nie trzeba określać żadnych punktów końcowych lub zachowania usługi lub zmiany ustawienia powiązania, nie trzeba określić cały plik konfiguracji usługi. Jeśli zaimplementowano dwa kontrakty i hosta umożliwia transportu HTTP i TCP hosta usługi tworzy cztery domyślne punkty końcowe, jeden dla każdej umowy każdego transportu. Aby utworzyć domyślne punkty końcowe usługi hosta musi znać jakie powiązania do użycia. Te ustawienia są określone w <`protocolMappings`> sekcji w <`system.serviceModel`> sekcji. <`protocolMappings`> Sekcja zawiera listę zamapowane na typy powiązanie schematami protokołu transportu. Host usługi używa adres podstawowy przekazywania w celu określenia powiązania, które do użycia. W poniższym przykładzie użyto <`protocolMappings`> elementu.  
  
> [!WARNING]
>  Zmiana domyślnego elementów konfiguracji, takich jak powiązania lub zachowania, może mieć wpływ na usługi zdefiniowane w niższych poziomach hierarchii konfiguracji, ponieważ może korzystać z tych powiązań domyślne i zachowania. W związku z tym, kto zmiany domyślnego powiązania i zachowania musi należy pamiętać, że te zmiany mogą mieć wpływ na inne usługi w hierarchii.  
  
> [!NOTE]
>  Usługi hostowanej przez usługi Internet Information Services (IIS) lub usługi aktywacji procesów systemu Windows (WAS) Użyj katalogu wirtualnego jako ich adres podstawowy.  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 W poprzednim przykładzie, punkt końcowy z adres podstawowy, który rozpoczyna się od schematu "http" używa <xref:System.ServiceModel.BasicHttpBinding>. Punkt końcowy z adres podstawowy, który rozpoczyna się od schematu "net.tcp" używa <xref:System.ServiceModel.NetTcpBinding>. Można zastąpić ustawienia w lokalnym pliku App.config lub Web.config.  
  
 Każdy element <`protocolMappings`> sekcji, należy określić schemat i powiązania. Opcjonalnie można określić `bindingConfiguration` atrybut, który określa konfigurację powiązania w <`bindings`> pliku konfiguracji. Jeśli nie `bindingConfiguration` jest określony, używana jest Konfiguracja wiązań anonimowych typu odpowiednie powiązania.  
  
 Zachowania usług są skonfigurowane dla domyślnych punktów końcowych przy użyciu anonimowego <`behavior`> sekcje w <`serviceBehaviors`> sekcji. Wszelkie nienazwane <`behavior`> elementów w obrębie <`serviceBehaviors`> są używane do konfigurowania zachowań usługi. Na przykład następujący plik konfiguracji umożliwia publikowanie metadanych usługi dla wszystkich usług w ramach hosta.  
  
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
  
 Zachowania punktu końcowego są konfigurowane przy użyciu anonimowego <`behavior`> sekcje w <`serviceBehaviors`> sekcji.  
  
 Poniższy przykład jest odpowiednikiem jeden na początku tego tematu, który korzysta z modelu uproszczona konfiguracja pliku konfiguracji.  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="false"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <bindings>  
       <basicHttpBinding>  
          <binding maxBufferSize="100"  
                   maxReceiveBufferSize="100" />  
       </basicHttpBinding>  
    </bindings>    <!-- No <service> tag is necessary. Default endpoints will be added to the service -->  
    <!-- The service behavior with name="" will be picked up by the service -->  
    <protocolMapping>  
      <add scheme="http"     binding="basicHttpBinding" / </protocolMapping>  
  </system.serviceModel>  
```  
  
> [!IMPORTANT]
>  Ta funkcja odnosi się tylko do konfiguracji usługi WCF nie konfiguracji klienta. Większość razy Konfiguracja klienta WCF będą generowane przez narzędzia, takiego jak svcutil.exe lub dodanie odwołania do usługi z programu Visual Studio. W przypadku ręcznego konfigurowania klienta programu WCF należy dodać \<klienta > elementu konfiguracji i określ żadnych punktów końcowych, które chcesz wywołać.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie usług za pomocą plików konfiguracji](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [Konfigurowanie powiązań dla usług](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług](../../../docs/framework/wcf/configuring-services.md)  
 [Konfigurowanie systemu Windows Communication Foundation aplikacji](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 [Konfigurowanie usług WCF w kodzie](../../../docs/framework/wcf/configuring-wcf-services-in-code.md)
