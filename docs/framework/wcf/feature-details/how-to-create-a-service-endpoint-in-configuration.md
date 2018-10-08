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
# <a name="how-to-create-a-service-endpoint-in-configuration"></a><span data-ttu-id="9015a-102">Porady: Tworzenie punktu końcowego usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9015a-102">How to: Create a Service Endpoint in Configuration</span></span>
<span data-ttu-id="9015a-103">Punkty końcowe udostępniać klientom dostęp do funkcji, które oferuje usługa Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9015a-103">Endpoints provide clients with access to the functionality a Windows Communication Foundation (WCF) service offers.</span></span> <span data-ttu-id="9015a-104">Można zdefiniować jeden lub więcej punktów końcowych usługi za pomocą kombinacji adresy punktów końcowych względnych i bezwzględnych lub jeśli nie zdefiniowano żadnych punktów końcowych usługi, środowisko wykonawcze zapewnia niektóre domyślnie dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="9015a-104">You can define one or more endpoints for a service by using a combination of relative and absolute endpoint addresses, or if you do not define any service endpoints, the runtime provides some by default for you.</span></span> <span data-ttu-id="9015a-105">W tym temacie przedstawiono sposób dodawania punktów końcowych przy użyciu pliku konfiguracji, które zawierają zarówno względnych i bezwzględnych adresów.</span><span class="sxs-lookup"><span data-stu-id="9015a-105">This topic shows how to add endpoints using a configuration file that contain both relative and absolute addresses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9015a-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="9015a-106">Example</span></span>  
 <span data-ttu-id="9015a-107">Następująca konfiguracja usługi Określa adres bazowy i pięć punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="9015a-107">The following service configuration specifies a base address and five endpoints.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="9015a-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="9015a-108">Example</span></span>  
 <span data-ttu-id="9015a-109">Adres podstawowy jest określony, przy użyciu `add` elementu, w ramach usługi/host/baseAddresses, jak pokazano w następującym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9015a-109">The base address is specified using the `add` element, under service/host/baseAddresses, as shown in the following sample.</span></span>  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a><span data-ttu-id="9015a-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="9015a-110">Example</span></span>  
 <span data-ttu-id="9015a-111">Pierwszy definicji punktu końcowego pokazano w następującym przykładzie określa adres względny, co oznacza, że adres punktu końcowego jest kombinacją adresu podstawowego i adres względny, zgodnie z regułami kompozycji identyfikator (URI).</span><span class="sxs-lookup"><span data-stu-id="9015a-111">The first endpoint definition shown in the following sample specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of Uniform Resource Identifier (URI) composition.</span></span> <span data-ttu-id="9015a-112">Względny adres jest pusty (""), więc adres punktu końcowego jest taka sama jak adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="9015a-112">The relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="9015a-113">Adres istniejący punkt końcowy jest `http://localhost:8000/servicemodelsamples/service`.</span><span class="sxs-lookup"><span data-stu-id="9015a-113">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>  
  
```xml  
<endpoint address=""   
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="9015a-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="9015a-114">Example</span></span>  
 <span data-ttu-id="9015a-115">Drugi definicji punktu końcowego określa również adres względny, jak pokazano w poniższym Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="9015a-115">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span> <span data-ttu-id="9015a-116">Adres względny "test", jest dołączana do podstawowego adresu.</span><span class="sxs-lookup"><span data-stu-id="9015a-116">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="9015a-117">Adres istniejący punkt końcowy jest `http://localhost:8000/servicemodelsamples/service/test`.</span><span class="sxs-lookup"><span data-stu-id="9015a-117">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="9015a-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="9015a-118">Example</span></span>  
 <span data-ttu-id="9015a-119">Trzeci definicji punktu końcowego określa adresem bezwzględnym, jak pokazano w poniższym Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="9015a-119">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span> <span data-ttu-id="9015a-120">Adres podstawowy odgrywa żadnej roli w adresie.</span><span class="sxs-lookup"><span data-stu-id="9015a-120">The base address plays no role in the address.</span></span> <span data-ttu-id="9015a-121">Adres istniejący punkt końcowy jest `http://localhost:8001/hello/servicemodelsamples`.</span><span class="sxs-lookup"><span data-stu-id="9015a-121">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="9015a-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="9015a-122">Example</span></span>  
 <span data-ttu-id="9015a-123">Adres punktu końcowego czwarty określa adresem bezwzględnym i innego transportu — TCP.</span><span class="sxs-lookup"><span data-stu-id="9015a-123">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="9015a-124">Adres podstawowy odgrywa żadnej roli w adresie.</span><span class="sxs-lookup"><span data-stu-id="9015a-124">The base address plays no role in the address.</span></span> <span data-ttu-id="9015a-125">Adres istniejący punkt końcowy jest NET.TCP://localhost: 9000/servicemodelsamples/usługi.</span><span class="sxs-lookup"><span data-stu-id="9015a-125">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="9015a-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="9015a-126">Example</span></span>  
 <span data-ttu-id="9015a-127">Aby użyć domyślnych punktów końcowych, udostępniane przez środowisko uruchomieniowe, nie określaj żadnych punktów końcowych usługi w kodzie i pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9015a-127">To use the default endpoints provided by the runtime, do not specify any service endpoints in either the code or the configuration file.</span></span> <span data-ttu-id="9015a-128">W tym przykładzie środowisko uruchomieniowe tworzy domyślne punkty końcowe po otwarciu usługi.</span><span class="sxs-lookup"><span data-stu-id="9015a-128">In this example, the runtime creates the default endpoints when the service is opened.</span></span> <span data-ttu-id="9015a-129">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązania i zachowań, zobacz [uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="9015a-129">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
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
