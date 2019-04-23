---
title: WS Dual Http
ms.date: 03/30/2017
ms.assetid: 9997eba5-29ec-48db-86f3-fa77b241fb1a
ms.openlocfilehash: 8141ee85fa1d38c3f190688981ce66a9dd9c88f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59974493"
---
# <a name="ws-dual-http"></a><span data-ttu-id="7193c-102">WS Dual Http</span><span class="sxs-lookup"><span data-stu-id="7193c-102">WS Dual Http</span></span>
<span data-ttu-id="7193c-103">Przykład podwójnego Http pokazuje, jak skonfigurować `WSDualHttpBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="7193c-103">The Dual Http sample demonstrates how to configure the `WSDualHttpBinding` binding.</span></span> <span data-ttu-id="7193c-104">W tym przykładzie składa się z konsoli programu klienckiego (.exe) i usługi biblioteki (.dll), hostowanej przez Internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="7193c-104">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="7193c-105">Usługa implementuje kontraktu dwukierunkowego.</span><span class="sxs-lookup"><span data-stu-id="7193c-105">The service implements a duplex contract.</span></span> <span data-ttu-id="7193c-106">Kontrakt jest definiowany przez `ICalculatorDuplex` interfejs, który udostępnia operacje matematyczne (dodawania, odejmowania, mnożenia i dzielenia).</span><span class="sxs-lookup"><span data-stu-id="7193c-106">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="7193c-107">W tym przykładzie `ICalculatorDuplex` interfejs umożliwia klientowi do wykonywania operacji matematycznych obliczania wyniku uruchomionych za pośrednictwem sesji.</span><span class="sxs-lookup"><span data-stu-id="7193c-107">In this sample, the `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over the session.</span></span> <span data-ttu-id="7193c-108">Niezależnie od siebie, usługa zwraca wyniki w `ICalculatorDuplexCallback` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="7193c-108">Independently, the service returns results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="7193c-109">Kontrakt dupleksowy wymaga elementu session, ponieważ kontekst muszą być ustalane do skorelowania zestaw komunikatów przesyłanych między klientem a usługą.</span><span class="sxs-lookup"><span data-stu-id="7193c-109">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between client and service.</span></span> <span data-ttu-id="7193c-110">`WSDualHttpBinding` Powiązania obsługującego komunikację dupleksową.</span><span class="sxs-lookup"><span data-stu-id="7193c-110">The `WSDualHttpBinding` binding supports duplex communication.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7193c-111">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="7193c-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7193c-112">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="7193c-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7193c-113">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="7193c-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7193c-114">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="7193c-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7193c-115">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7193c-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\DualHttp`  
  
 <span data-ttu-id="7193c-116">Aby skonfigurować punktu końcowego usługi za pomocą `WSDualHttpBinding`, określić powiązanie w konfiguracji punktu końcowego, jak pokazano.</span><span class="sxs-lookup"><span data-stu-id="7193c-116">To configure a service endpoint with the `WSDualHttpBinding`, specify the binding in the endpoint configuration as shown.</span></span>  
  
```xml  
<endpoint address=""  
         binding="wsDualHttpBinding"  
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />  
```  
  
 <span data-ttu-id="7193c-117">Na komputerze klienckim należy skonfigurować adres który umożliwia Podłącz do klienta, jak pokazano na poniższym Przykładowa konfiguracja serwera.</span><span class="sxs-lookup"><span data-stu-id="7193c-117">On the client, you must configure an address that the server can use to connect to the client as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="7193c-118">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="7193c-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="7193c-119">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="7193c-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate client once the output is displayed.  
  
Result(100)  
Result(50)  
Result(882.5)  
Result(441.25)  
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)  
```  
  
 <span data-ttu-id="7193c-120">Po uruchomieniu przykładu, zobacz komunikaty zwracane do klienta na interfejs wywołania zwrotnego wysyłane z usługi.</span><span class="sxs-lookup"><span data-stu-id="7193c-120">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="7193c-121">Jest wyświetlany wynik każdego pośrednich następuje całe równanie po ukończeniu wszystkich operacji.</span><span class="sxs-lookup"><span data-stu-id="7193c-121">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="7193c-122">Naciśnij klawisz ENTER, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="7193c-122">Press ENTER to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7193c-123">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="7193c-123">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7193c-124">Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0, używając następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="7193c-124">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="7193c-125">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7193c-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="7193c-126">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7193c-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="7193c-127">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7193c-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="7193c-128">Podczas uruchamiania klienta w konfiguracji między komputerami, koniecznie Zastąp ciąg localhost w obu `address` atrybutu [ \<punktu końcowego > z \<klienta >](../../configure-apps/file-schema/wcf/endpoint-of-client.md) elementu i `clientBaseAddress` atrybut [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu [ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element z nazwą odpowiedniej maszyny, jak pokazano:</span><span class="sxs-lookup"><span data-stu-id="7193c-128">When running the client in a cross-machine configuration, be sure to replace localhost in both the `address` attribute of the [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element and the `clientBaseAddress` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) element of the [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element with the name of the appropriate machine, as shown:</span></span>  
  
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
