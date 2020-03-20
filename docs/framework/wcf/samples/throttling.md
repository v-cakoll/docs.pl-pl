---
title: Ograniczanie przepływności
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, throttling sample
- Throttling Sample [Windows Communication Foundation]
ms.assetid: 40bb3582-8ae9-4410-96f0-6c515bfaf47c
ms.openlocfilehash: 9428fe13e529c3ce8feb59c0a3c5afc5f23c0229
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143840"
---
# <a name="throttling"></a><span data-ttu-id="c2757-102">Ograniczanie przepływności</span><span class="sxs-lookup"><span data-stu-id="c2757-102">Throttling</span></span>
<span data-ttu-id="c2757-103">Throttling przykładu pokazuje użycie kontroli ograniczania przepustowości.</span><span class="sxs-lookup"><span data-stu-id="c2757-103">The Throttling sample demonstrates the use of throttling controls.</span></span> <span data-ttu-id="c2757-104">Formanty ograniczania umieścić limity liczby równoczesnych wywołań, wystąpień lub sesji, aby zapobiec nadmiernemu zużyciu zasobów.</span><span class="sxs-lookup"><span data-stu-id="c2757-104">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span> <span data-ttu-id="c2757-105">Zachowanie ograniczania jest określone w ustawieniach pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="c2757-105">Throttling behavior is specified in service configuration file settings.</span></span> <span data-ttu-id="c2757-106">Ten przykład jest oparty na [wprowadzenie,](../../../../docs/framework/wcf/samples/getting-started-sample.md) który implementuje usługę kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="c2757-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
 <span data-ttu-id="c2757-107">W tym przykładzie klient jest aplikacją konsoli (.exe), a usługa jest obsługiwana przez internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="c2757-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2757-108">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="c2757-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c2757-109">Plik konfiguracji usługi określa formanty ograniczania [ \<przepustowości ](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md)w>usługi, jak pokazano w poniższej przykładowej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c2757-109">The service configuration file specifies throttling controls in a [\<serviceThrottling>](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md), as shown in the following sample configuration.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceDebug includeExceptionDetailInFaults="False" />  
      <serviceMetadata httpGetEnabled="True"/>  
      <!-- Specify throttling behavior -->  
    <serviceThrottling maxConcurrentCalls="2"  
                       maxConcurrentInstances="10"/>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="c2757-110">Zgodnie z konfiguracją usługa ogranicza maksymalną liczbę równoczesnych wywołań do 2 i maksymalną liczbę równoczesnych wystąpień do 10.</span><span class="sxs-lookup"><span data-stu-id="c2757-110">As configured, the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span>  
  
 <span data-ttu-id="c2757-111">W celu zademonstrowania ograniczania przepustowości definiujemy czas uśpienia w metodach usługi w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c2757-111">In order to demonstrate throttling we define a sleep time on the service methods as follows:</span></span>  
  
```csharp
public double Add(double n1, double n2)  
{  
    System.Threading.Thread.Sleep(2000);  
    return n1 + n2;  
}  
```  
  
 <span data-ttu-id="c2757-112">Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="c2757-112">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c2757-113">Add i Odejmij metody są wykonywane jednocześnie i Multiply i Divide metody są wykonywane jednocześnie potwierdzające, że nie więcej niż 2 metody mogą być wykonywane jednocześnie w ten sposób demonstrując ograniczanie przepustowości.</span><span class="sxs-lookup"><span data-stu-id="c2757-113">The Add and Subtract methods are executed concurrently and the Multiply and Divide methods are executed concurrently proving that not more than 2 methods can be executed concurrently thus demonstrating throttling.</span></span>  
  
```console  
Press <ENTER> to terminate client.  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Add Result: 115.99  
Subtract Result: 68.46  
Multiply Result: 731.25  
Divide Result: 3.14285714285714  
  
Press any key to continue . . .  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c2757-114">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="c2757-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c2757-115">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c2757-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c2757-116">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c2757-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="c2757-117">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c2757-117">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c2757-118">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="c2757-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c2757-119">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="c2757-119">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c2757-120">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="c2757-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c2757-121">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c2757-121">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Throttling`  
