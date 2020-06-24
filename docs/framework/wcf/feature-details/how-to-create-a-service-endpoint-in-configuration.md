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
# <a name="how-to-create-a-service-endpoint-in-configuration"></a><span data-ttu-id="4ac56-103">Instrukcje: tworzenie punktu końcowego usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4ac56-103">How to: Create a Service Endpoint in Configuration</span></span>
<span data-ttu-id="4ac56-104">Punkty końcowe zapewniają klientom dostęp do funkcji oferowanych przez usługę Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4ac56-104">Endpoints provide clients with access to the functionality a Windows Communication Foundation (WCF) service offers.</span></span> <span data-ttu-id="4ac56-105">Można zdefiniować jeden lub więcej punktów końcowych dla usługi przy użyciu kombinacji względnych i bezwzględnych adresów punktów końcowych lub jeśli nie zdefiniowano żadnych punktów końcowych usługi, środowisko uruchomieniowe domyślnie udostępnia niektóre.</span><span class="sxs-lookup"><span data-stu-id="4ac56-105">You can define one or more endpoints for a service by using a combination of relative and absolute endpoint addresses, or if you do not define any service endpoints, the runtime provides some by default for you.</span></span> <span data-ttu-id="4ac56-106">W tym temacie pokazano, jak dodać punkty końcowe przy użyciu pliku konfiguracji, który zawiera adresy względne i bezwzględne.</span><span class="sxs-lookup"><span data-stu-id="4ac56-106">This topic shows how to add endpoints using a configuration file that contain both relative and absolute addresses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ac56-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ac56-107">Example</span></span>  
 <span data-ttu-id="4ac56-108">Poniższa konfiguracja usługi określa adres podstawowy i pięć punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="4ac56-108">The following service configuration specifies a base address and five endpoints.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="4ac56-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ac56-109">Example</span></span>  
 <span data-ttu-id="4ac56-110">Adres podstawowy jest określany za pomocą `add` elementu, w obszarze Service/Host/baseAddresses, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4ac56-110">The base address is specified using the `add` element, under service/host/baseAddresses, as shown in the following sample.</span></span>  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a><span data-ttu-id="4ac56-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ac56-111">Example</span></span>  
 <span data-ttu-id="4ac56-112">Definicja pierwszego punktu końcowego pokazana w poniższym przykładzie określa adres względny, co oznacza, że adres punktu końcowego jest kombinacją adresu podstawowego i adresu względnego, zgodnie z regułami składu Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="4ac56-112">The first endpoint definition shown in the following sample specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of Uniform Resource Identifier (URI) composition.</span></span> <span data-ttu-id="4ac56-113">Adres względny jest pusty (""), więc adres punktu końcowego jest taki sam jak adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="4ac56-113">The relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="4ac56-114">Rzeczywisty adres punktu końcowego to `http://localhost:8000/servicemodelsamples/service` .</span><span class="sxs-lookup"><span data-stu-id="4ac56-114">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>  
  
```xml  
<endpoint address=""
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="4ac56-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ac56-115">Example</span></span>  
 <span data-ttu-id="4ac56-116">Druga definicja punktu końcowego określa adres względny, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="4ac56-116">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span> <span data-ttu-id="4ac56-117">Adres względny "test" jest dołączany do adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="4ac56-117">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="4ac56-118">Rzeczywisty adres punktu końcowego to `http://localhost:8000/servicemodelsamples/service/test` .</span><span class="sxs-lookup"><span data-stu-id="4ac56-118">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="4ac56-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ac56-119">Example</span></span>  
 <span data-ttu-id="4ac56-120">Definicja trzeciego punktu końcowego określa adres bezwzględny, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="4ac56-120">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span> <span data-ttu-id="4ac56-121">Adres podstawowy nie pełni żadnej roli w adresie.</span><span class="sxs-lookup"><span data-stu-id="4ac56-121">The base address plays no role in the address.</span></span> <span data-ttu-id="4ac56-122">Rzeczywisty adres punktu końcowego to `http://localhost:8001/hello/servicemodelsamples` .</span><span class="sxs-lookup"><span data-stu-id="4ac56-122">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="4ac56-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ac56-123">Example</span></span>  
 <span data-ttu-id="4ac56-124">Czwarty adres punktu końcowego określa adres bezwzględny i inny transport — TCP.</span><span class="sxs-lookup"><span data-stu-id="4ac56-124">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="4ac56-125">Adres podstawowy nie pełni żadnej roli w adresie.</span><span class="sxs-lookup"><span data-stu-id="4ac56-125">The base address plays no role in the address.</span></span> <span data-ttu-id="4ac56-126">Rzeczywisty adres punktu końcowego to net. TCP://localhost: 9000/ServiceModelSamples/Service.</span><span class="sxs-lookup"><span data-stu-id="4ac56-126">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="4ac56-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ac56-127">Example</span></span>  
 <span data-ttu-id="4ac56-128">Aby użyć domyślnych punktów końcowych dostarczonych przez środowisko uruchomieniowe, nie należy określać żadnych punktów końcowych usługi w kodzie lub pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4ac56-128">To use the default endpoints provided by the runtime, do not specify any service endpoints in either the code or the configuration file.</span></span> <span data-ttu-id="4ac56-129">W tym przykładzie środowisko uruchomieniowe tworzy domyślne punkty końcowe podczas otwierania usługi.</span><span class="sxs-lookup"><span data-stu-id="4ac56-129">In this example, the runtime creates the default endpoints when the service is opened.</span></span> <span data-ttu-id="4ac56-130">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](../simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="4ac56-130">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
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
