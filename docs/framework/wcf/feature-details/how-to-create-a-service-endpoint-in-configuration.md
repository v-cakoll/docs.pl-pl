---
title: 'Instrukcje: tworzenie punktu końcowego usługi w konfiguracji'
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: 5935f798004de3ec049b9c9f0300675e1660f462
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464128"
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a>Instrukcje: tworzenie punktu końcowego usługi w konfiguracji
Punkty końcowe zapewniają klientom dostęp do funkcji, które oferuje usługa Windows Communication Foundation (WCF). Można zdefiniować jeden lub więcej punktów końcowych dla usługi przy użyciu kombinacji względnych i bezwzględnych adresów końcowych lub jeśli nie zdefiniowano żadnych punktów końcowych usługi, środowisko wykonawcze zapewnia niektóre domyślnie dla Ciebie. W tym temacie pokazano, jak dodać punkty końcowe przy użyciu pliku konfiguracji, który zawiera adresy względne i bezwzględne.  
  
## <a name="example"></a>Przykład  
 Następująca konfiguracja usługi określa adres podstawowy i pięć punktów końcowych.  
  
```xml  
<configuration>  
  
  <appSettings>  
    <!-- use appSetting to configure base address provided by host -->  
    <add key="baseAddress" value="http://localhost:8000/servicemodelsamples/service" />  
  </appSettings>  
  
  <system.serviceModel>  
    <services>  
    <!-- This section is optional with the default configuration introduced in .NET Framework 4. -->  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="/test"  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="http://localhost:8001/hello/servicemodelsamples"  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
                  binding="netTcpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is another relative address exposed at   
             http://localhost:8000/ServiceModelSamples/service/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
## <a name="example"></a>Przykład  
 Adres podstawowy jest określony `add` przy użyciu elementu, w obszarze service/host/baseAddresses, jak pokazano w poniższym przykładzie.  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a>Przykład  
 Pierwsza definicja punktu końcowego pokazana w poniższym przykładzie określa adres względny, co oznacza, że adres punktu końcowego jest kombinacją adresu bazowego i adresu względnego zgodnie z regułami składu jednolitego identyfikatora zasobów (URI). Adres względny jest pusty (""), więc adres punktu końcowego jest taki sam jak adres podstawowy. Rzeczywisty adres punktu `http://localhost:8000/servicemodelsamples/service`końcowego to .  
  
```xml  
<endpoint address=""
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Przykład  
 Druga definicja punktu końcowego określa również adres względny, jak pokazano w poniższej konfiguracji przykładowej. Adres względny ,,test", jest dołączany do adresu podstawowego. Rzeczywisty adres punktu `http://localhost:8000/servicemodelsamples/service/test`końcowego to .  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Przykład  
 Trzecia definicja punktu końcowego określa adres bezwzględny, jak pokazano w poniższej konfiguracji przykładowej. Adres podstawowy nie odgrywa żadnej roli w adresie. Rzeczywisty adres punktu `http://localhost:8001/hello/servicemodelsamples`końcowego to .  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Przykład  
 Czwarty adres punktu końcowego określa adres bezwzględny i inny transport — TCP. Adres podstawowy nie odgrywa żadnej roli w adresie. Rzeczywisty adres punktu końcowego to net.tcp://localhost:9000/servicemodelsamples/service.  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Przykład  
 Aby użyć domyślnych punktów końcowych dostarczonych przez środowisko wykonawcze, nie należy określać żadnych punktów końcowych usługi w kodzie lub pliku konfiguracji. W tym przykładzie środowisko wykonawcze tworzy domyślne punkty końcowe po otwarciu usługi. Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
```xml  
<configuration>  
  
  <appSettings>  
    <!-- use appSetting to configure base address provided by host -->  
    <add key="baseAddress" value="http://localhost:8000/servicemodelsamples/service" />  
  </appSettings>  
  
  <system.serviceModel>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```
