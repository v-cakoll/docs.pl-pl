---
title: 'Instrukcje: tworzenie punktu końcowego usługi w konfiguracji'
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: 9687d9537d6f166a02b79261743050168f677261
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184998"
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a><span data-ttu-id="2aea3-102">Instrukcje: tworzenie punktu końcowego usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2aea3-102">How to: Create a Service Endpoint in Configuration</span></span>
<span data-ttu-id="2aea3-103">Punkty końcowe zapewniają klientom dostęp do funkcji, które oferuje usługa Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2aea3-103">Endpoints provide clients with access to the functionality a Windows Communication Foundation (WCF) service offers.</span></span> <span data-ttu-id="2aea3-104">Można zdefiniować jeden lub więcej punktów końcowych dla usługi przy użyciu kombinacji względnych i bezwzględnych adresów końcowych lub jeśli nie zdefiniowano żadnych punktów końcowych usługi, środowisko wykonawcze zapewnia niektóre domyślnie dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="2aea3-104">You can define one or more endpoints for a service by using a combination of relative and absolute endpoint addresses, or if you do not define any service endpoints, the runtime provides some by default for you.</span></span> <span data-ttu-id="2aea3-105">W tym temacie pokazano, jak dodać punkty końcowe przy użyciu pliku konfiguracji, który zawiera adresy względne i bezwzględne.</span><span class="sxs-lookup"><span data-stu-id="2aea3-105">This topic shows how to add endpoints using a configuration file that contain both relative and absolute addresses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2aea3-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="2aea3-106">Example</span></span>  
 <span data-ttu-id="2aea3-107">Następująca konfiguracja usługi określa adres podstawowy i pięć punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="2aea3-107">The following service configuration specifies a base address and five endpoints.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="2aea3-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="2aea3-108">Example</span></span>  
 <span data-ttu-id="2aea3-109">Adres podstawowy jest określony `add` przy użyciu elementu, w obszarze service/host/baseAddresses, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2aea3-109">The base address is specified using the `add` element, under service/host/baseAddresses, as shown in the following sample.</span></span>  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a><span data-ttu-id="2aea3-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="2aea3-110">Example</span></span>  
 <span data-ttu-id="2aea3-111">Pierwsza definicja punktu końcowego pokazana w poniższym przykładzie określa adres względny, co oznacza, że adres punktu końcowego jest kombinacją adresu bazowego i adresu względnego zgodnie z regułami składu jednolitego identyfikatora zasobów (URI).</span><span class="sxs-lookup"><span data-stu-id="2aea3-111">The first endpoint definition shown in the following sample specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of Uniform Resource Identifier (URI) composition.</span></span> <span data-ttu-id="2aea3-112">Adres względny jest pusty (""), więc adres punktu końcowego jest taki sam jak adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="2aea3-112">The relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="2aea3-113">Rzeczywisty adres punktu `http://localhost:8000/servicemodelsamples/service`końcowego to .</span><span class="sxs-lookup"><span data-stu-id="2aea3-113">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>  
  
```xml  
<endpoint address=""
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="2aea3-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="2aea3-114">Example</span></span>  
 <span data-ttu-id="2aea3-115">Druga definicja punktu końcowego określa również adres względny, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="2aea3-115">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span> <span data-ttu-id="2aea3-116">Adres względny ,,test", jest dołączany do adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="2aea3-116">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="2aea3-117">Rzeczywisty adres punktu `http://localhost:8000/servicemodelsamples/service/test`końcowego to .</span><span class="sxs-lookup"><span data-stu-id="2aea3-117">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="2aea3-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="2aea3-118">Example</span></span>  
 <span data-ttu-id="2aea3-119">Trzecia definicja punktu końcowego określa adres bezwzględny, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="2aea3-119">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span> <span data-ttu-id="2aea3-120">Adres podstawowy nie odgrywa żadnej roli w adresie.</span><span class="sxs-lookup"><span data-stu-id="2aea3-120">The base address plays no role in the address.</span></span> <span data-ttu-id="2aea3-121">Rzeczywisty adres punktu `http://localhost:8001/hello/servicemodelsamples`końcowego to .</span><span class="sxs-lookup"><span data-stu-id="2aea3-121">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="2aea3-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="2aea3-122">Example</span></span>  
 <span data-ttu-id="2aea3-123">Czwarty adres punktu końcowego określa adres bezwzględny i inny transport — TCP.</span><span class="sxs-lookup"><span data-stu-id="2aea3-123">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="2aea3-124">Adres podstawowy nie odgrywa żadnej roli w adresie.</span><span class="sxs-lookup"><span data-stu-id="2aea3-124">The base address plays no role in the address.</span></span> <span data-ttu-id="2aea3-125">Rzeczywisty adres punktu końcowego to net.tcp://localhost:9000/servicemodelsamples/service.</span><span class="sxs-lookup"><span data-stu-id="2aea3-125">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="2aea3-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="2aea3-126">Example</span></span>  
 <span data-ttu-id="2aea3-127">Aby użyć domyślnych punktów końcowych dostarczonych przez środowisko wykonawcze, nie należy określać żadnych punktów końcowych usługi w kodzie lub pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2aea3-127">To use the default endpoints provided by the runtime, do not specify any service endpoints in either the code or the configuration file.</span></span> <span data-ttu-id="2aea3-128">W tym przykładzie środowisko wykonawcze tworzy domyślne punkty końcowe po otwarciu usługi.</span><span class="sxs-lookup"><span data-stu-id="2aea3-128">In this example, the runtime creates the default endpoints when the service is opened.</span></span> <span data-ttu-id="2aea3-129">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="2aea3-129">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
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
