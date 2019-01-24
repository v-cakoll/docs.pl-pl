---
title: Sesja niezawodna powiązania niestandardowego
ms.date: 03/30/2017
ms.assetid: c5fcd409-246f-4f3e-b3f1-629506ca4c04
ms.openlocfilehash: d8f58a425fd2cef078954f9805f47fc1376889d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623988"
---
# <a name="custom-binding-reliable-session"></a><span data-ttu-id="381db-102">Sesja niezawodna powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="381db-102">Custom Binding Reliable Session</span></span>
<span data-ttu-id="381db-103">Powiązanie niestandardowe jest definiowany przez uporządkowaną listą elementy powiązania dyskretnych.</span><span class="sxs-lookup"><span data-stu-id="381db-103">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="381db-104">Niniejszy przykład pokazuje, jak skonfigurować powiązania niestandardowego z różnymi transportu i komunikatu kodowanie elementów, szczególnie Włączanie niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="381db-104">This sample demonstrates how to configure a custom binding with various transport and message encoding elements, especially enabling reliable sessions.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="381db-105">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="381db-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="381db-106">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="381db-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="381db-107">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="381db-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="381db-108">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="381db-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSession`  
  
## <a name="sample-details"></a><span data-ttu-id="381db-109">Przykład szczegółów</span><span class="sxs-lookup"><span data-stu-id="381db-109">Sample Details</span></span>  
 <span data-ttu-id="381db-110">Niezawodne sesje oferują funkcje dla niezawodna obsługa komunikatów i sesji.</span><span class="sxs-lookup"><span data-stu-id="381db-110">Reliable sessions provide features for reliable messaging and sessions.</span></span> <span data-ttu-id="381db-111">Niezawodna obsługa komunikatów ponawia próbę komunikacji w przypadku niepowodzenia i umożliwia gwarancje dostarczenia, np. w kolejności przybycia komunikaty, aby określić.</span><span class="sxs-lookup"><span data-stu-id="381db-111">Reliable messaging retries communication on failure and allows delivery assurances such as in-order arrival of messages to be specified.</span></span> <span data-ttu-id="381db-112">Sesje zarządzania stanem dla klientów między wywołaniami.</span><span class="sxs-lookup"><span data-stu-id="381db-112">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="381db-113">Przykład implementuje sesje dotyczące utrzymania Stan klienta i określa gwarancje dostarczenia w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="381db-113">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span> <span data-ttu-id="381db-114">Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="381db-114">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="381db-115">Funkcje niezawodnej sesji są włączone i skonfigurowane w plikach konfiguracji aplikacji dla klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="381db-115">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="381db-116">Procedury i kompilacja instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="381db-116">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="381db-117">Określanie kolejności elementów wiązania jest ważny w celu definiowania niestandardowego powiązania, ponieważ każdy z nich reprezentuje warstwę w stosie kanału (zobacz [powiązań niestandardowych](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="381db-117">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span>  
  
 <span data-ttu-id="381db-118">Konfiguracja usługi na potrzeby przykładu jest zdefiniowany jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="381db-118">The service configuration for the sample is defined as shown in the following code example.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->  
        <!-- specify customBinding binding and a binding configuration to use -->  
        <endpoint address=""  
                  binding="customBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <!-- custom binding configuration - configures HTTP transport, reliable sessions -->  
    <bindings>  
      <customBinding>  
        <binding name="Binding1">  
          <reliableSession />  
          <security authenticationMode="SecureConversation"  
                     requireSecurityContextCancellation="true">  
          </security>  
          <compositeDuplex />  
          <oneWay />  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8" />  
          <httpTransport authenticationScheme="Anonymous" bypassProxyOnLocal="false"  
                        hostNameComparisonMode="StrongWildcard"   
                        proxyAuthenticationScheme="Anonymous" realm=""   
                        useDefaultWebProxy="true" />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="381db-119">Podczas uruchamiania w scenariuszu między komputerami, musisz zmienić adres punktu końcowego klienta w celu uwzględnienia nazwy hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="381db-119">When running in a cross-machine scenario, you must change client's endpoint address to reflect the host name of the service.</span></span>  
  
 <span data-ttu-id="381db-120">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="381db-120">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="381db-121">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="381db-121">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="381db-122">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="381db-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="381db-123">Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0, używając następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="381db-123">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command:</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="381db-124">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="381db-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="381db-125">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="381db-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="381db-126">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="381db-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="381db-127">Podczas uruchamiania klienta w konfiguracji między komputerami, należy zastąpić "localhost", w obu `address` atrybutu [ \<punktu końcowego >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elementu i `clientBaseAddress` atrybutu [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) nazwą odpowiedniej maszyny, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="381db-127">When running the client in a cross-machine configuration, be sure to replace "localhost" in both the `address` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element and the `clientBaseAddress` attribute of the [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) with the name of the appropriate machine, as shown in the following example.</span></span>  
  
    ```xml  
    <endpoint name = ""  
    address="http://service_machine_name/servicemodelsamples/service.svc"  
    ... />  
    <compositeDuplex clientBaseAddress="http://client_machine_name:8000/myClient/" />  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="381db-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="381db-128">See also</span></span>
