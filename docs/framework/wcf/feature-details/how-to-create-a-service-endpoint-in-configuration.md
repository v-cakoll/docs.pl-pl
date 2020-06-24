---
title: 'Instrukcje: tworzenie punktu końcowego usługi w konfiguracji'
description: Dowiedz się, jak dodać punkty końcowe dla usługi WCF przy użyciu pliku konfiguracji zawierającego zarówno adresy względne, jak i bezwzględne.
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: 184bcb5f7f3e83f12608757b55bbb4d57be58f7d
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247068"
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a>Instrukcje: tworzenie punktu końcowego usługi w konfiguracji
Punkty końcowe zapewniają klientom dostęp do funkcji oferowanych przez usługę Windows Communication Foundation (WCF). Można zdefiniować jeden lub więcej punktów końcowych dla usługi przy użyciu kombinacji względnych i bezwzględnych adresów punktów końcowych lub jeśli nie zdefiniowano żadnych punktów końcowych usługi, środowisko uruchomieniowe domyślnie udostępnia niektóre. W tym temacie pokazano, jak dodać punkty końcowe przy użyciu pliku konfiguracji, który zawiera adresy względne i bezwzględne.  
  
## <a name="example"></a>Przykład  
 Poniższa konfiguracja usługi określa adres podstawowy i pięć punktów końcowych.  
  
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
 Adres podstawowy jest określany za pomocą `add` elementu, w obszarze Service/Host/baseAddresses, jak pokazano w poniższym przykładzie.  
  
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
 Definicja pierwszego punktu końcowego pokazana w poniższym przykładzie określa adres względny, co oznacza, że adres punktu końcowego jest kombinacją adresu podstawowego i adresu względnego, zgodnie z regułami składu Uniform Resource Identifier (URI). Adres względny jest pusty (""), więc adres punktu końcowego jest taki sam jak adres podstawowy. Rzeczywisty adres punktu końcowego to `http://localhost:8000/servicemodelsamples/service` .  
  
```xml  
<endpoint address=""
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Przykład  
 Druga definicja punktu końcowego określa adres względny, jak pokazano w poniższej konfiguracji przykładowej. Adres względny "test" jest dołączany do adresu podstawowego. Rzeczywisty adres punktu końcowego to `http://localhost:8000/servicemodelsamples/service/test` .  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Przykład  
 Definicja trzeciego punktu końcowego określa adres bezwzględny, jak pokazano w poniższej konfiguracji przykładowej. Adres podstawowy nie pełni żadnej roli w adresie. Rzeczywisty adres punktu końcowego to `http://localhost:8001/hello/servicemodelsamples` .  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Przykład  
 Czwarty adres punktu końcowego określa adres bezwzględny i inny transport — TCP. Adres podstawowy nie pełni żadnej roli w adresie. Rzeczywisty adres punktu końcowego to net. TCP://localhost: 9000/ServiceModelSamples/Service.  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Przykład  
 Aby użyć domyślnych punktów końcowych dostarczonych przez środowisko uruchomieniowe, nie należy określać żadnych punktów końcowych usługi w kodzie lub pliku konfiguracji. W tym przykładzie środowisko uruchomieniowe tworzy domyślne punkty końcowe podczas otwierania usługi. Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](../simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../samples/simplified-configuration-for-wcf-services.md).  
  
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
