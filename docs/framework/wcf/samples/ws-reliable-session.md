---
title: Sesja niezawodna WS
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: 604eaf9dc2ef506214969826ee7f38ee85690a0e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942171"
---
# <a name="ws-reliable-session"></a><span data-ttu-id="7afae-102">Sesja niezawodna WS</span><span class="sxs-lookup"><span data-stu-id="7afae-102">WS Reliable Session</span></span>
<span data-ttu-id="7afae-103">Ten przykład pokazuje użycie niezawodnych sesji.</span><span class="sxs-lookup"><span data-stu-id="7afae-103">This sample demonstrates the use of reliable sessions.</span></span> <span data-ttu-id="7afae-104">Niezawodne sesje zapewniają obsługę niezawodnej obsługi komunikatów i sesji.</span><span class="sxs-lookup"><span data-stu-id="7afae-104">Reliable sessions provide support for reliable messaging and sessions.</span></span> <span data-ttu-id="7afae-105">Niezawodna ponowna próba komunikacji przy niepowodzeń i pozwala określić gwarancje dostarczania, takie jak wysyłanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="7afae-105">Reliable messaging retries communication on failure and allows delivery assurances to be specified, such as in-order arrival of messages.</span></span> <span data-ttu-id="7afae-106">Sesje utrzymują stan dla klientów między wywołaniami.</span><span class="sxs-lookup"><span data-stu-id="7afae-106">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="7afae-107">Przykład implementuje sesje do obsługi stanu klienta i określa gwarancje dostarczania w kolejności.</span><span class="sxs-lookup"><span data-stu-id="7afae-107">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7afae-108">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="7afae-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7afae-109">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="7afae-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7afae-110">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="7afae-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7afae-111">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7afae-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 <span data-ttu-id="7afae-112">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) , który implementuje usługę kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="7afae-112">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="7afae-113">Funkcje niezawodnej sesji są włączane i konfigurowane w plikach konfiguracji aplikacji dla klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="7afae-113">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>  
  
 <span data-ttu-id="7afae-114">W tym przykładzie usługa jest hostowana w Internet Information Services (IIS), a klient jest aplikacją konsolową (. exe).</span><span class="sxs-lookup"><span data-stu-id="7afae-114">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7afae-115">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="7afae-115">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7afae-116">Przykład używa `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="7afae-116">The sample uses the `wsHttpBinding`.</span></span> <span data-ttu-id="7afae-117">Powiązanie jest określone w plikach konfiguracji zarówno dla klienta, jak i usługi.</span><span class="sxs-lookup"><span data-stu-id="7afae-117">The binding is specified in the configuration files for both the client and service.</span></span> <span data-ttu-id="7afae-118">Typ powiązania jest określony w `binding` atrybucie elementu punktu końcowego, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="7afae-118">The binding type is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="7afae-119">Punkt końcowy zawiera `bindingConfiguration` atrybut odwołujący się do konfiguracji powiązania o nazwie "Binding1".</span><span class="sxs-lookup"><span data-stu-id="7afae-119">The endpoint contains a `bindingConfiguration` attribute that references a binding configuration named "Binding1."</span></span> <span data-ttu-id="7afae-120">Konfiguracja powiązania umożliwia niezawodne sesje przez ustawienie `enabled` atrybutu [ \<> ReliableSession](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) na. `true`</span><span class="sxs-lookup"><span data-stu-id="7afae-120">The binding configuration enables reliable sessions by setting the `enabled` attribute of the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) to `true`.</span></span> <span data-ttu-id="7afae-121">Gwarancje dostarczania dla uporządkowanych sesji są kontrolowane przez ustawienie atrybutu uporządkowane `true` na `false`lub.</span><span class="sxs-lookup"><span data-stu-id="7afae-121">Delivery assurances for ordered sessions are controlled by setting the ordered attribute to `true` or `false`.</span></span> <span data-ttu-id="7afae-122">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="7afae-122">The default is `true`.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="7afae-123">Klasa implementacji usługi implementuje <xref:System.ServiceModel.InstanceContextMode.PerSession> Tworzenie wystąpień dla każdego klienta, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="7afae-123">The service implementation class implements <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing to maintain a separate class instance for each client, as shown in the following sample code.</span></span>  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 <span data-ttu-id="7afae-124">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="7afae-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="7afae-125">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="7afae-125">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7afae-126">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="7afae-126">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7afae-127">Zainstaluj ASP.NET 4,0 przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="7afae-127">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="7afae-128">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7afae-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="7afae-129">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7afae-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="7afae-130">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7afae-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
