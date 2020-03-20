---
title: Sesja niezawodna WS
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: 8898dfedc6ba7deceb5a6e6856b7c7e6ad79d047
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143502"
---
# <a name="ws-reliable-session"></a><span data-ttu-id="f05ea-102">Sesja niezawodna WS</span><span class="sxs-lookup"><span data-stu-id="f05ea-102">WS Reliable Session</span></span>
<span data-ttu-id="f05ea-103">W tym przykładzie pokazano użycie niezawodnych sesji.</span><span class="sxs-lookup"><span data-stu-id="f05ea-103">This sample demonstrates the use of reliable sessions.</span></span> <span data-ttu-id="f05ea-104">Niezawodne sesje zapewniają obsługę niezawodnych wiadomości i sesji.</span><span class="sxs-lookup"><span data-stu-id="f05ea-104">Reliable sessions provide support for reliable messaging and sessions.</span></span> <span data-ttu-id="f05ea-105">Niezawodne wiadomości ponawia komunikację w przypadku awarii i umożliwia zapewnienie dostarczania, takie jak najaśledzenie wiadomości w kolejności.</span><span class="sxs-lookup"><span data-stu-id="f05ea-105">Reliable messaging retries communication on failure and allows delivery assurances to be specified, such as in-order arrival of messages.</span></span> <span data-ttu-id="f05ea-106">Sesje utrzymują stan dla klientów między wywołaniami.</span><span class="sxs-lookup"><span data-stu-id="f05ea-106">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="f05ea-107">Przykład implementuje sesje do utrzymania stanu klienta i określa gwarancje dostarczania w kolejności.</span><span class="sxs-lookup"><span data-stu-id="f05ea-107">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f05ea-108">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="f05ea-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f05ea-109">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="f05ea-109">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f05ea-110">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="f05ea-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f05ea-111">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="f05ea-111">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 <span data-ttu-id="f05ea-112">Ten przykład jest oparty na [wprowadzenie,](../../../../docs/framework/wcf/samples/getting-started-sample.md) który implementuje usługę kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="f05ea-112">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="f05ea-113">Niezawodne funkcje sesji są włączone i konfigurowane w plikach konfiguracyjnych aplikacji dla klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="f05ea-113">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>  
  
 <span data-ttu-id="f05ea-114">W tym przykładzie usługa jest hostowana w internetowych usługach informacyjnych (IIS), a klient jest aplikacją konsoli (.exe).</span><span class="sxs-lookup"><span data-stu-id="f05ea-114">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f05ea-115">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="f05ea-115">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f05ea-116">W próbce `wsHttpBinding`użyto pliku .</span><span class="sxs-lookup"><span data-stu-id="f05ea-116">The sample uses the `wsHttpBinding`.</span></span> <span data-ttu-id="f05ea-117">Powiązanie jest określone w plikach konfiguracyjnych dla klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="f05ea-117">The binding is specified in the configuration files for both the client and service.</span></span> <span data-ttu-id="f05ea-118">Typ powiązania jest określony w atrybucie elementu punktu końcowego, `binding` jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="f05ea-118">The binding type is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="f05ea-119">Punkt końcowy zawiera `bindingConfiguration` atrybut, który odwołuje się do konfiguracji powiązania o nazwie "Binding1".</span><span class="sxs-lookup"><span data-stu-id="f05ea-119">The endpoint contains a `bindingConfiguration` attribute that references a binding configuration named "Binding1."</span></span> <span data-ttu-id="f05ea-120">Konfiguracja wiązania umożliwia niezawodne `enabled` sesje, ustawiając atrybut [ \<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) do `true`.</span><span class="sxs-lookup"><span data-stu-id="f05ea-120">The binding configuration enables reliable sessions by setting the `enabled` attribute of the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) to `true`.</span></span> <span data-ttu-id="f05ea-121">Gwarancje dostawy dla zamówionych sesji są kontrolowane `true` `false`przez ustawienie zamówionego atrybutu na lub .</span><span class="sxs-lookup"><span data-stu-id="f05ea-121">Delivery assurances for ordered sessions are controlled by setting the ordered attribute to `true` or `false`.</span></span> <span data-ttu-id="f05ea-122">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="f05ea-122">The default is `true`.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="f05ea-123">Klasa implementacji usługi <xref:System.ServiceModel.InstanceContextMode.PerSession> implementuje instancing do obsługi wystąpienia klasy oddzielne dla każdego klienta, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f05ea-123">The service implementation class implements <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing to maintain a separate class instance for each client, as shown in the following sample code.</span></span>  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 <span data-ttu-id="f05ea-124">Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="f05ea-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="f05ea-125">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="f05ea-125">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f05ea-126">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="f05ea-126">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f05ea-127">Zainstaluj ASP.NET 4.0 za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="f05ea-127">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="f05ea-128">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f05ea-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="f05ea-129">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f05ea-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="f05ea-130">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f05ea-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
