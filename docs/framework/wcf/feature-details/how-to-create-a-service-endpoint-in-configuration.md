---
title: "Porady: Tworzenie punktu końcowego usługi w konfiguracji"
ms.custom: 
ms.date: 06/16/2016
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8e60708ecf5ae7ed15b42e982b9ae40c00d72ecc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a><span data-ttu-id="c077b-102">Porady: Tworzenie punktu końcowego usługi w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c077b-102">How to: Create a Service Endpoint in Configuration</span></span>
<span data-ttu-id="c077b-103">Punkty końcowe udostępniać klientom dostęp do funkcji [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] oferty usługi.</span><span class="sxs-lookup"><span data-stu-id="c077b-103">Endpoints provide clients with access to the functionality a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service offers.</span></span> <span data-ttu-id="c077b-104">Można określić jedną lub więcej punktów końcowych dla usługi przy użyciu kombinacji adresy punktów końcowych względne i bezwzględne lub jeśli żadnych punktów końcowych usługi nie jest zdefiniowana, środowiska uruchomieniowego zawiera niektóre domyślnie dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="c077b-104">You can define one or more endpoints for a service by using a combination of relative and absolute endpoint addresses, or if you do not define any service endpoints, the runtime provides some by default for you.</span></span> <span data-ttu-id="c077b-105">W tym temacie przedstawiono sposób dodawania punktów końcowych przy użyciu pliku konfiguracji, które zawierają zarówno względnych i bezwzględnych adresów.</span><span class="sxs-lookup"><span data-stu-id="c077b-105">This topic shows how to add endpoints using a configuration file that contain both relative and absolute addresses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c077b-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="c077b-106">Example</span></span>  
 <span data-ttu-id="c077b-107">Następująca konfiguracja usługi Określa adres bazowy i pięć punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="c077b-107">The following service configuration specifies a base address and five endpoints.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="c077b-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="c077b-108">Example</span></span>  
 <span data-ttu-id="c077b-109">Adres podstawowy jest określona za pomocą `add` elementu w obszarze usługi/hosta/baseAddress, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c077b-109">The base address is specified using the `add` element, under service/host/baseAddresses, as shown in the following sample.</span></span>  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a><span data-ttu-id="c077b-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="c077b-110">Example</span></span>  
 <span data-ttu-id="c077b-111">Pierwszy definicji punktu końcowego pokazano w poniższym przykładzie określa adres względny, co oznacza, że adres punktu końcowego jest kombinacją adresu podstawowego i adres względny zgodnie z regułami kompozycji jednolity identyfikator zasobów (URI).</span><span class="sxs-lookup"><span data-stu-id="c077b-111">The first endpoint definition shown in the following sample specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of Uniform Resource Identifier (URI) composition.</span></span> <span data-ttu-id="c077b-112">Adres względny jest pusty (""), więc adres punktu końcowego jest taki sam jak adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="c077b-112">The relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="c077b-113">Adres rzeczywisty punkt końcowy jest http://localhost: 8000/servicemodelsamples/usług.</span><span class="sxs-lookup"><span data-stu-id="c077b-113">The actual endpoint address is http://localhost:8000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address=""   
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="c077b-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="c077b-114">Example</span></span>  
 <span data-ttu-id="c077b-115">Druga definicja punkt końcowy określa również adresem względnym, jak pokazano w poniższych Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="c077b-115">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span> <span data-ttu-id="c077b-116">Adres względny "test", jest dołączany do adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="c077b-116">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="c077b-117">Adres rzeczywisty punkt końcowy jest http://localhost: 8000/servicemodelsamples/service/testowanie oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="c077b-117">The actual endpoint address is http://localhost:8000/servicemodelsamples/service/test.</span></span>  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="c077b-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="c077b-118">Example</span></span>  
 <span data-ttu-id="c077b-119">Trzeci definicji punktu końcowego określa adresu bezwzględnego, jak pokazano w poniższych Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="c077b-119">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span> <span data-ttu-id="c077b-120">Adres podstawowy pełni żadnej roli w adresie.</span><span class="sxs-lookup"><span data-stu-id="c077b-120">The base address plays no role in the address.</span></span> <span data-ttu-id="c077b-121">Adres rzeczywisty punkt końcowy jest http://localhost:8001/hello/servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="c077b-121">The actual endpoint address is http://localhost:8001/hello/servicemodelsamples.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="c077b-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="c077b-122">Example</span></span>  
 <span data-ttu-id="c077b-123">Adres punktu końcowego czwarty Określa adres bezwzględny i innego transportu — TCP.</span><span class="sxs-lookup"><span data-stu-id="c077b-123">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="c077b-124">Adres podstawowy pełni żadnej roli w adresie.</span><span class="sxs-lookup"><span data-stu-id="c077b-124">The base address plays no role in the address.</span></span> <span data-ttu-id="c077b-125">Adres rzeczywisty punkt końcowy jest NET.TCP://localhost: 9000/servicemodelsamples/usług.</span><span class="sxs-lookup"><span data-stu-id="c077b-125">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="c077b-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="c077b-126">Example</span></span>  
 <span data-ttu-id="c077b-127">Aby użyć domyślnych punktów końcowych dostarczonym w czasie wykonywania, nie określaj żadnych punktów końcowych usługi w kodzie i pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c077b-127">To use the default endpoints provided by the runtime, do not specify any service endpoints in either the code or the configuration file.</span></span> <span data-ttu-id="c077b-128">W tym przykładzie środowiska uruchomieniowego tworzy domyślne punkty końcowe po otwarciu usługi.</span><span class="sxs-lookup"><span data-stu-id="c077b-128">In this example, the runtime creates the default endpoints when the service is opened.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="c077b-129">domyślne punkty końcowe, powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="c077b-129"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
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
