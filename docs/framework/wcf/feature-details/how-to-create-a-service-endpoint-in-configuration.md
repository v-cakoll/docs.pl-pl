---
title: 'Porady: Tworzenie punktu końcowego usługi w konfiguracji'
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: 63a40576b805952197cec5af2f89a5dc4b5d3545
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850599"
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a>Porady: Tworzenie punktu końcowego usługi w konfiguracji
Punkty końcowe udostępniać klientom dostęp do funkcji, które oferuje usługa Windows Communication Foundation (WCF). Można zdefiniować jeden lub więcej punktów końcowych usługi za pomocą kombinacji adresy punktów końcowych względnych i bezwzględnych lub jeśli nie zdefiniowano żadnych punktów końcowych usługi, środowisko wykonawcze zapewnia niektóre domyślnie dla Ciebie. W tym temacie przedstawiono sposób dodawania punktów końcowych przy użyciu pliku konfiguracji, które zawierają zarówno względnych i bezwzględnych adresów.  
  
## <a name="example"></a>Przykład  
 Następująca konfiguracja usługi Określa adres bazowy i pięć punktów końcowych.  
  
```xml  
<configuration>  
  
  <appSettings>  
    <!-- use appSetting to configure base address provided by host -->  
    <add key="baseAddress" value="http://localhost:8000/servicemodelsamples/service" />  
  </appSettings>  
  
  <system.serviceModel>  
    <services>  
    <!-- This section is optional with the default configuration introduced  
         in .NET Framework 4. -->  
      <service  
          name="Microsoft.ServiceModel.Samples.CalculatorService">  
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
 Adres podstawowy jest określony, przy użyciu `add` elementu, w ramach usługi/host/baseAddresses, jak pokazano w następującym przykładzie.  
  
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
 Pierwszy definicji punktu końcowego pokazano w następującym przykładzie określa adres względny, co oznacza, że adres punktu końcowego jest kombinacją adresu podstawowego i adres względny, zgodnie z regułami kompozycji identyfikator (URI). Względny adres jest pusty (""), więc adres punktu końcowego jest taka sama jak adres podstawowy. Adres istniejący punkt końcowy jest `http://localhost:8000/servicemodelsamples/service`.  
  
```xml  
<endpoint address=""   
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Przykład  
 Drugi definicji punktu końcowego określa również adres względny, jak pokazano w poniższym Przykładowa konfiguracja. Adres względny "test", jest dołączana do podstawowego adresu. Adres istniejący punkt końcowy jest `http://localhost:8000/servicemodelsamples/service/test`.  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Przykład  
 Trzeci definicji punktu końcowego określa adresem bezwzględnym, jak pokazano w poniższym Przykładowa konfiguracja. Adres podstawowy odgrywa żadnej roli w adresie. Adres istniejący punkt końcowy jest `http://localhost:8001/hello/servicemodelsamples`.  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Przykład  
 Adres punktu końcowego czwarty określa adresem bezwzględnym i innego transportu — TCP. Adres podstawowy odgrywa żadnej roli w adresie. Adres istniejący punkt końcowy jest NET.TCP://localhost: 9000/servicemodelsamples/usługi.  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Przykład  
 Aby użyć domyślnych punktów końcowych, udostępniane przez środowisko uruchomieniowe, nie określaj żadnych punktów końcowych usługi w kodzie i pliku konfiguracji. W tym przykładzie środowisko uruchomieniowe tworzy domyślne punkty końcowe po otwarciu usługi. Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązania i zachowań, zobacz [uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
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
