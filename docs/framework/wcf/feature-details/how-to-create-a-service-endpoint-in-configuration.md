---
title: 'Instrukcje: tworzenie punktu końcowego usługi w konfiguracji'
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: 56b29da0c147eb9e73a08e2875e33e384da729ed
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598921"
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a><span data-ttu-id="5aa23-102">Instrukcje: tworzenie punktu końcowego usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5aa23-102">How to: Create a Service Endpoint in Configuration</span></span>
<span data-ttu-id="5aa23-103">Punkty końcowe zapewniają klientom dostęp do funkcji oferowanych przez usługę Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5aa23-103">Endpoints provide clients with access to the functionality a Windows Communication Foundation (WCF) service offers.</span></span> <span data-ttu-id="5aa23-104">Można zdefiniować jeden lub więcej punktów końcowych dla usługi przy użyciu kombinacji względnych i bezwzględnych adresów punktów końcowych lub jeśli nie zdefiniowano żadnych punktów końcowych usługi, środowisko uruchomieniowe domyślnie udostępnia niektóre.</span><span class="sxs-lookup"><span data-stu-id="5aa23-104">You can define one or more endpoints for a service by using a combination of relative and absolute endpoint addresses, or if you do not define any service endpoints, the runtime provides some by default for you.</span></span> <span data-ttu-id="5aa23-105">W tym temacie pokazano, jak dodać punkty końcowe przy użyciu pliku konfiguracji, który zawiera adresy względne i bezwzględne.</span><span class="sxs-lookup"><span data-stu-id="5aa23-105">This topic shows how to add endpoints using a configuration file that contain both relative and absolute addresses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5aa23-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="5aa23-106">Example</span></span>  
 <span data-ttu-id="5aa23-107">Poniższa konfiguracja usługi określa adres podstawowy i pięć punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="5aa23-107">The following service configuration specifies a base address and five endpoints.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="5aa23-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="5aa23-108">Example</span></span>  
 <span data-ttu-id="5aa23-109">Adres podstawowy jest określany za pomocą `add` elementu, w obszarze Service/Host/baseAddresses, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5aa23-109">The base address is specified using the `add` element, under service/host/baseAddresses, as shown in the following sample.</span></span>  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a><span data-ttu-id="5aa23-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="5aa23-110">Example</span></span>  
 <span data-ttu-id="5aa23-111">Definicja pierwszego punktu końcowego pokazana w poniższym przykładzie określa adres względny, co oznacza, że adres punktu końcowego jest kombinacją adresu podstawowego i adresu względnego, zgodnie z regułami składu Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="5aa23-111">The first endpoint definition shown in the following sample specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of Uniform Resource Identifier (URI) composition.</span></span> <span data-ttu-id="5aa23-112">Adres względny jest pusty (""), więc adres punktu końcowego jest taki sam jak adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="5aa23-112">The relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="5aa23-113">Rzeczywisty adres punktu końcowego to `http://localhost:8000/servicemodelsamples/service` .</span><span class="sxs-lookup"><span data-stu-id="5aa23-113">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>  
  
```xml  
<endpoint address=""
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="5aa23-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="5aa23-114">Example</span></span>  
 <span data-ttu-id="5aa23-115">Druga definicja punktu końcowego określa adres względny, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="5aa23-115">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span> <span data-ttu-id="5aa23-116">Adres względny "test" jest dołączany do adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="5aa23-116">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="5aa23-117">Rzeczywisty adres punktu końcowego to `http://localhost:8000/servicemodelsamples/service/test` .</span><span class="sxs-lookup"><span data-stu-id="5aa23-117">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="5aa23-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="5aa23-118">Example</span></span>  
 <span data-ttu-id="5aa23-119">Definicja trzeciego punktu końcowego określa adres bezwzględny, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="5aa23-119">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span> <span data-ttu-id="5aa23-120">Adres podstawowy nie pełni żadnej roli w adresie.</span><span class="sxs-lookup"><span data-stu-id="5aa23-120">The base address plays no role in the address.</span></span> <span data-ttu-id="5aa23-121">Rzeczywisty adres punktu końcowego to `http://localhost:8001/hello/servicemodelsamples` .</span><span class="sxs-lookup"><span data-stu-id="5aa23-121">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="5aa23-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="5aa23-122">Example</span></span>  
 <span data-ttu-id="5aa23-123">Czwarty adres punktu końcowego określa adres bezwzględny i inny transport — TCP.</span><span class="sxs-lookup"><span data-stu-id="5aa23-123">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="5aa23-124">Adres podstawowy nie pełni żadnej roli w adresie.</span><span class="sxs-lookup"><span data-stu-id="5aa23-124">The base address plays no role in the address.</span></span> <span data-ttu-id="5aa23-125">Rzeczywisty adres punktu końcowego to net. TCP://localhost: 9000/ServiceModelSamples/Service.</span><span class="sxs-lookup"><span data-stu-id="5aa23-125">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="5aa23-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="5aa23-126">Example</span></span>  
 <span data-ttu-id="5aa23-127">Aby użyć domyślnych punktów końcowych dostarczonych przez środowisko uruchomieniowe, nie należy określać żadnych punktów końcowych usługi w kodzie lub pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5aa23-127">To use the default endpoints provided by the runtime, do not specify any service endpoints in either the code or the configuration file.</span></span> <span data-ttu-id="5aa23-128">W tym przykładzie środowisko uruchomieniowe tworzy domyślne punkty końcowe podczas otwierania usługi.</span><span class="sxs-lookup"><span data-stu-id="5aa23-128">In this example, the runtime creates the default endpoints when the service is opened.</span></span> <span data-ttu-id="5aa23-129">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](../simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="5aa23-129">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
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
