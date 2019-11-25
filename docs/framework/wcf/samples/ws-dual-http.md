---
title: WS Dual Http
ms.date: 03/30/2017
ms.assetid: 9997eba5-29ec-48db-86f3-fa77b241fb1a
ms.openlocfilehash: 44fdf6f0b27e15c486afa32f67668e9fd6eeac10
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74138678"
---
# <a name="ws-dual-http"></a><span data-ttu-id="60e09-102">WS Dual Http</span><span class="sxs-lookup"><span data-stu-id="60e09-102">WS Dual Http</span></span>

<span data-ttu-id="60e09-103">Podwójny przykład http demonstruje sposób konfigurowania powiązania `WSDualHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="60e09-103">The Dual Http sample demonstrates how to configure the `WSDualHttpBinding` binding.</span></span> <span data-ttu-id="60e09-104">Ten przykład składa się z programu konsolowego klienta (exe) i biblioteki usług (. dll) hostowanej przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="60e09-104">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="60e09-105">Usługa implementuje kontrakt dupleksowy.</span><span class="sxs-lookup"><span data-stu-id="60e09-105">The service implements a duplex contract.</span></span> <span data-ttu-id="60e09-106">Kontrakt jest definiowany przez interfejs `ICalculatorDuplex`, który udostępnia operacje matematyczne (Dodawanie, odejmowanie, mnożenie i dzielenie).</span><span class="sxs-lookup"><span data-stu-id="60e09-106">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="60e09-107">W tym przykładzie interfejs `ICalculatorDuplex` pozwala klientowi wykonywać operacje matematyczne, obliczając wynik działania w ramach sesji.</span><span class="sxs-lookup"><span data-stu-id="60e09-107">In this sample, the `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over the session.</span></span> <span data-ttu-id="60e09-108">Niezależnie usługa zwraca wyniki na interfejsie `ICalculatorDuplexCallback`.</span><span class="sxs-lookup"><span data-stu-id="60e09-108">Independently, the service returns results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="60e09-109">Kontrakt dupleksowy wymaga sesji, ponieważ należy ustanowić kontekst w celu skorelowania zestawu komunikatów przesyłanych między klientem i usługą.</span><span class="sxs-lookup"><span data-stu-id="60e09-109">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between client and service.</span></span> <span data-ttu-id="60e09-110">Powiązanie `WSDualHttpBinding` obsługuje komunikację dupleksową.</span><span class="sxs-lookup"><span data-stu-id="60e09-110">The `WSDualHttpBinding` binding supports duplex communication.</span></span>

> [!NOTE]
> <span data-ttu-id="60e09-111">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="60e09-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="60e09-112">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="60e09-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="60e09-113">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="60e09-113">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="60e09-114">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="60e09-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="60e09-115">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="60e09-115">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\DualHttp`

<span data-ttu-id="60e09-116">Aby skonfigurować punkt końcowy usługi przy użyciu `WSDualHttpBinding`, określ powiązanie w konfiguracji punktu końcowego, jak pokazano.</span><span class="sxs-lookup"><span data-stu-id="60e09-116">To configure a service endpoint with the `WSDualHttpBinding`, specify the binding in the endpoint configuration as shown.</span></span>

```xml
<endpoint address=""
         binding="wsDualHttpBinding"
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />
```

<span data-ttu-id="60e09-117">Na kliencie należy skonfigurować adres, który może być używany przez serwer do łączenia się z klientem, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="60e09-117">On the client, you must configure an address that the server can use to connect to the client as shown in the following sample configuration.</span></span>

```xml
<system.serviceModel>
  <client>
    <endpoint address=
         "http://localhost/servicemodelsamples/service.svc"
         binding="wsDualHttpBinding"
         bindingConfiguration="Binding1"
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />
  </client>

  <bindings>
    <!-- Configure a WSDualHttpBinding that supports duplex -->
    <!-- communication. -->
    <wsDualHttpBinding>
      <binding name="Binding1"
               clientBaseAddress="http://localhost:8000/myClient/"
               useDefaultWebProxy="true"
               bypassProxyOnLocal="false">
      </binding>
    </wsDualHttpBinding>
  </bindings>
</system.serviceModel>
```

<span data-ttu-id="60e09-118">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="60e09-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="60e09-119">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="60e09-119">Press ENTER in the client window to shut down the client.</span></span>

```console
Press <ENTER> to terminate client once the output is displayed.

Result(100)
Result(50)
Result(882.5)
Result(441.25)
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)
```

<span data-ttu-id="60e09-120">Po uruchomieniu przykładu komunikaty zwrócone do klienta są wyświetlane w interfejsie wywołania zwrotnego wysyłanego z usługi.</span><span class="sxs-lookup"><span data-stu-id="60e09-120">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="60e09-121">Zostanie wyświetlony każdy wynik pośredni, po którym następuje całe równanie po zakończeniu wszystkich operacji.</span><span class="sxs-lookup"><span data-stu-id="60e09-121">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="60e09-122">Naciśnij klawisz ENTER, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="60e09-122">Press ENTER to shut down the client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="60e09-123">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="60e09-123">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="60e09-124">Zainstaluj ASP.NET 4,0 przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="60e09-124">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="60e09-125">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="60e09-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="60e09-126">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="60e09-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="60e09-127">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="60e09-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="60e09-128">W przypadku uruchamiania klienta programu w konfiguracji obejmującej wiele komputerów Pamiętaj, aby zamienić wartość localhost zarówno w atrybucie `address` [\<punktu końcowego > elementu \<klienta >](../../configure-apps/file-schema/wcf/endpoint-of-client.md) [`clientBaseAddress`](../../configure-apps/file-schema/wcf/bindings.md) elementu [\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) elementu o nazwie odpowiedniej maszyny, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="60e09-128">When running the client in a cross-machine configuration, be sure to replace localhost in both the `address` attribute of the [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element and the `clientBaseAddress` attribute of the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element of the [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element with the name of the appropriate machine, as shown:</span></span>

    ```xml
    <client>
        <endpoint name = ""
          address=
         "http://service_machine_name/servicemodelsamples/service.svc"
        />
    </client>
    ...
    <wsDualHttpBinding>
        <binding name="DuplexBinding" clientBaseAddress=
            "http://client_machine_name:8000/myClient/">
        </binding>
    </wsDualHttpBinding>
    ```
