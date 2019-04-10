---
title: Sesja niezawodna WS
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: c682db98ac72019d434e06ae79d87b69c85c275e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310294"
---
# <a name="ws-reliable-session"></a><span data-ttu-id="2544a-102">Sesja niezawodna WS</span><span class="sxs-lookup"><span data-stu-id="2544a-102">WS Reliable Session</span></span>
<span data-ttu-id="2544a-103">Niniejszy przykład pokazuje użycie niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="2544a-103">This sample demonstrates the use of reliable sessions.</span></span> <span data-ttu-id="2544a-104">Sesje niezawodnej obsługi niezawodna obsługa komunikatów i sesji.</span><span class="sxs-lookup"><span data-stu-id="2544a-104">Reliable sessions provide support for reliable messaging and sessions.</span></span> <span data-ttu-id="2544a-105">Niezawodna obsługa komunikatów ponawia próbę komunikacji w przypadku niepowodzenia i umożliwia gwarancje dostarczenia, należy określić, takich jak otrzymanie wiadomości w kolejności.</span><span class="sxs-lookup"><span data-stu-id="2544a-105">Reliable messaging retries communication on failure and allows delivery assurances to be specified, such as in-order arrival of messages.</span></span> <span data-ttu-id="2544a-106">Sesje zarządzania stanem dla klientów między wywołaniami.</span><span class="sxs-lookup"><span data-stu-id="2544a-106">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="2544a-107">Przykład implementuje sesje dotyczące utrzymania Stan klienta i określa gwarancje dostarczenia w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="2544a-107">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2544a-108">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="2544a-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2544a-109">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="2544a-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2544a-110">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="2544a-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2544a-111">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2544a-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 <span data-ttu-id="2544a-112">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="2544a-112">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="2544a-113">Funkcje niezawodnej sesji są włączone i skonfigurowane w plikach konfiguracji aplikacji dla klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="2544a-113">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>  
  
 <span data-ttu-id="2544a-114">W tym przykładzie usługa jest hostowana w Internet Information Services (IIS), a klient to aplikacja konsoli (.exe).</span><span class="sxs-lookup"><span data-stu-id="2544a-114">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2544a-115">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="2544a-115">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2544a-116">W przykładzie użyto `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="2544a-116">The sample uses the `wsHttpBinding`.</span></span> <span data-ttu-id="2544a-117">Powiązanie jest określona w plikach konfiguracyjnych dla klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="2544a-117">The binding is specified in the configuration files for both the client and service.</span></span> <span data-ttu-id="2544a-118">Typ powiązania jest określony w elemencie punktu końcowego `binding` atrybutu, jak pokazano w poniższym Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="2544a-118">The binding type is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="2544a-119">Punkt końcowy zawiera `bindingConfiguration` atrybut, który odwołuje się do konfiguracji powiązania o nazwie "Binding1."</span><span class="sxs-lookup"><span data-stu-id="2544a-119">The endpoint contains a `bindingConfiguration` attribute that references a binding configuration named "Binding1."</span></span> <span data-ttu-id="2544a-120">Konfiguracja powiązania umożliwia niezawodne sesje, ustawiając `enabled` atrybutu [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) do `true`.</span><span class="sxs-lookup"><span data-stu-id="2544a-120">The binding configuration enables reliable sessions by setting the `enabled` attribute of the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) to `true`.</span></span> <span data-ttu-id="2544a-121">Gwarancje dostarczenia sesjach uporządkowanym są kontrolowane przez ustawienie atrybutu uporządkowane na `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="2544a-121">Delivery assurances for ordered sessions are controlled by setting the ordered attribute to `true` or `false`.</span></span> <span data-ttu-id="2544a-122">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="2544a-122">The default is `true`.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="2544a-123">Klasa implementuje implementacji usługi <xref:System.ServiceModel.InstanceContextMode.PerSession> wystąpień do obsługi wystąpienia osobnej klasy dla każdego klienta, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="2544a-123">The service implementation class implements <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing to maintain a separate class instance for each client, as shown in the following sample code.</span></span>  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 <span data-ttu-id="2544a-124">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="2544a-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="2544a-125">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="2544a-125">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2544a-126">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="2544a-126">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2544a-127">Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0, używając następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="2544a-127">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="2544a-128">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2544a-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="2544a-129">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2544a-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="2544a-130">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2544a-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
