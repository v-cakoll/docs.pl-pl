---
title: Sesja niezawodna powiązania niestandardowego
ms.date: 03/30/2017
ms.assetid: c5fcd409-246f-4f3e-b3f1-629506ca4c04
ms.openlocfilehash: 76c701aaae368171bc7047784e1dc126937c84f0
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463938"
---
# <a name="custom-binding-reliable-session"></a><span data-ttu-id="e0e4b-102">Sesja niezawodna powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="e0e4b-102">Custom Binding Reliable Session</span></span>

<span data-ttu-id="e0e4b-103">Powiązanie niestandardowe jest definiowane przez uporządkowaną listę dyskretnych elementów wiązania.</span><span class="sxs-lookup"><span data-stu-id="e0e4b-103">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="e0e4b-104">W tym przykładzie pokazano, jak skonfigurować niestandardowe powiązanie z różnych elementów kodowania transportu i wiadomości, szczególnie włączenie niezawodne sesje.</span><span class="sxs-lookup"><span data-stu-id="e0e4b-104">This sample demonstrates how to configure a custom binding with various transport and message encoding elements, especially enabling reliable sessions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e0e4b-105">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e0e4b-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e0e4b-106">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="e0e4b-106">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="e0e4b-107">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="e0e4b-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e0e4b-108">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e0e4b-108">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSession`

## <a name="sample-details"></a><span data-ttu-id="e0e4b-109">Przykładowe szczegóły</span><span class="sxs-lookup"><span data-stu-id="e0e4b-109">Sample Details</span></span>

<span data-ttu-id="e0e4b-110">Niezawodne sesje zapewniają funkcje niezawodnej obsługi wiadomości i sesji.</span><span class="sxs-lookup"><span data-stu-id="e0e4b-110">Reliable sessions provide features for reliable messaging and sessions.</span></span> <span data-ttu-id="e0e4b-111">Niezawodne wiadomości ponawia komunikację na niepowodzenie i umożliwia zapewnienie dostarczania, takie jak nastawy wiadomości w kolejności, które mają być określone.</span><span class="sxs-lookup"><span data-stu-id="e0e4b-111">Reliable messaging retries communication on failure and allows delivery assurances such as in-order arrival of messages to be specified.</span></span> <span data-ttu-id="e0e4b-112">Sesje utrzymują stan dla klientów między wywołaniami.</span><span class="sxs-lookup"><span data-stu-id="e0e4b-112">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="e0e4b-113">Przykład implementuje sesje do utrzymania stanu klienta i określa gwarancje dostarczania w kolejności.</span><span class="sxs-lookup"><span data-stu-id="e0e4b-113">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span> <span data-ttu-id="e0e4b-114">Przykład jest oparty na [wprowadzenie,](../../../../docs/framework/wcf/samples/getting-started-sample.md) który implementuje usługę kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="e0e4b-114">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="e0e4b-115">Niezawodne funkcje sesji są włączone i konfigurowane w plikach konfiguracyjnych aplikacji dla klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="e0e4b-115">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>

> [!NOTE]
> <span data-ttu-id="e0e4b-116">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="e0e4b-116">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="e0e4b-117">Kolejność elementów wiązania jest ważna przy definiowaniu niestandardowego powiązania, ponieważ każdy reprezentuje warstwę w stosie kanałów (zobacz [Powiązania niestandardowe).](../../../../docs/framework/wcf/extending/custom-bindings.md)</span><span class="sxs-lookup"><span data-stu-id="e0e4b-117">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span>

<span data-ttu-id="e0e4b-118">Konfiguracja usługi dla przykładu jest zdefiniowana w sposób pokazany w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="e0e4b-118">The service configuration for the sample is defined as shown in the following code example.</span></span>

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

<span data-ttu-id="e0e4b-119">Podczas uruchamiania w scenariuszu między komputerami, należy zmienić adres punktu końcowego klienta, aby odzwierciedlić nazwę hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="e0e4b-119">When running in a cross-machine scenario, you must change client's endpoint address to reflect the host name of the service.</span></span>

<span data-ttu-id="e0e4b-120">Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="e0e4b-120">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e0e4b-121">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="e0e4b-121">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e0e4b-122">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="e0e4b-122">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="e0e4b-123">Zainstaluj ASP.NET 4.0 za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="e0e4b-123">Install ASP.NET 4.0 using the following command:</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="e0e4b-124">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e0e4b-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="e0e4b-125">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e0e4b-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="e0e4b-126">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e0e4b-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="e0e4b-127">Podczas uruchamiania klienta w konfiguracji między komputerami, należy zastąpić "localhost" w obu `address` [ \<atrybutu elementu>punktu końcowego](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) i `clientBaseAddress` atrybut [ \<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) z nazwą odpowiedniego komputera, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e0e4b-127">When running the client in a cross-machine configuration, be sure to replace "localhost" in both the `address` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element and the `clientBaseAddress` attribute of the [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) with the name of the appropriate machine, as shown in the following example.</span></span>

    ```xml
    <endpoint name = ""
    address="http://service_machine_name/servicemodelsamples/service.svc" />
    <compositeDuplex clientBaseAddress="http://client_machine_name:8000/myClient/" />
    ```
