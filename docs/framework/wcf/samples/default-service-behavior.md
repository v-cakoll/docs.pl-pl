---
title: Domyślne zachowanie usługi
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: 2c49c28d99bb3d300fd4589a088b2f086bdfd45d
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50184481"
---
# <a name="default-service-behavior"></a><span data-ttu-id="3d38f-102">Domyślne zachowanie usługi</span><span class="sxs-lookup"><span data-stu-id="3d38f-102">Default Service Behavior</span></span>
<span data-ttu-id="3d38f-103">Niniejszy przykład pokazuje, jak można skonfigurować ustawienia zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="3d38f-103">This sample demonstrates how service behavior settings can be configured.</span></span> <span data-ttu-id="3d38f-104">Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje `ICalculator` kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="3d38f-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="3d38f-105">W tym przykładzie jawnie definiuje zachowania usługi i zachowania operacji za pomocą <xref:System.ServiceModel.ServiceBehaviorAttribute> i <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutów.</span><span class="sxs-lookup"><span data-stu-id="3d38f-105">This sample explicitly defines service behaviors and operation behaviors using the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes.</span></span> <span data-ttu-id="3d38f-106">Zachowania można skonfigurować w plikach konfiguracyjnych lub obowiązkowo w kodzie (tak jak w przykładzie pokazano).</span><span class="sxs-lookup"><span data-stu-id="3d38f-106">You can configure behaviors in configuration files or imperatively in code (as this sample demonstrates).</span></span>  
  
 <span data-ttu-id="3d38f-107">W tym przykładzie klient to aplikacja konsoli (.exe), a usługa jest hostowana przez Internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="3d38f-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d38f-108">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="3d38f-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3d38f-109">Klasa usługi określa zachowania <xref:System.ServiceModel.ServiceBehaviorAttribute> i <xref:System.ServiceModel.OperationBehaviorAttribute> jak pokazano w następującym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="3d38f-109">The service class specifies behaviors with the <xref:System.ServiceModel.ServiceBehaviorAttribute> and the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following code sample.</span></span> <span data-ttu-id="3d38f-110">Wszystkie wartości są wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="3d38f-110">All values specified are the defaults.</span></span>  
  
```csharp
[ServiceBehavior(  
    AutomaticSessionShutdown=true,  
    ConcurrencyMode=ConcurrencyMode.Single,  
    InstanceContextMode=InstanceContextMode.PerSession,  
    IncludeExceptionDetailInFaults=false,  
    UseSynchronizationContext=true,  
    ValidateMustUnderstand=true)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(  
        TransactionAutoComplete=true,  
        TransactionScopeRequired=false,  
        Impersonation=ImpersonationOption.NotAllowed)]  
    public double Add(double n1, double n2)  
    {  
        System.Threading.Thread.Sleep(1600);  
        return n1 + n2;  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="3d38f-111">Zachowania usług są określane za pomocą <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="3d38f-111">Service behaviors are specified with the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span> <span data-ttu-id="3d38f-112">W poniższej tabeli opisano niektóre z tych zachowań.</span><span class="sxs-lookup"><span data-stu-id="3d38f-112">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="3d38f-113">Zachowanie usługi</span><span class="sxs-lookup"><span data-stu-id="3d38f-113">Service behavior</span></span>|<span data-ttu-id="3d38f-114">Opis</span><span class="sxs-lookup"><span data-stu-id="3d38f-114">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|<span data-ttu-id="3d38f-115">Automatycznie zamyka sesję na żądanie klienta.</span><span class="sxs-lookup"><span data-stu-id="3d38f-115">Automatically shuts down a session at the client's request.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|<span data-ttu-id="3d38f-116">Określa tryb współbieżności dla każdego wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="3d38f-116">Specifies the concurrency mode for each service instance.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|<span data-ttu-id="3d38f-117">Określa tryb kontekstu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3d38f-117">Specifies the instance context mode.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|<span data-ttu-id="3d38f-118">Określa, czy używać kontekstu synchronizacji podany, jeśli jest on ustawiony.</span><span class="sxs-lookup"><span data-stu-id="3d38f-118">Determines whether to use the provided synchronization context, if one is set.</span></span> <span data-ttu-id="3d38f-119">Użyj go, jeśli chcesz kontrolować, czy ma być używany `WindowsFormsSynchronizationContext` w aplikacjach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3d38f-119">Use this when you want to control whether to use a `WindowsFormsSynchronizationContext` in Windows Forms applications.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|<span data-ttu-id="3d38f-120">Określa, czy Wyjątki ogólne nieobsłużonego są do przekonwertowania na `Fault<string>` i wysyłane jako komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="3d38f-120">Determines whether general unhandled execution exceptions are to be converted into a `Fault<string>` and sent as a fault message.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|<span data-ttu-id="3d38f-121">Określa poziom izolacji transakcji.</span><span class="sxs-lookup"><span data-stu-id="3d38f-121">Specifies the isolation level for transactions.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|<span data-ttu-id="3d38f-122">Określa, czy nagłówki nieoczekiwany komunikat, że jest w stanie błędu.</span><span class="sxs-lookup"><span data-stu-id="3d38f-122">Determines whether unexpected message headers cause an error condition.</span></span>|  
  
 <span data-ttu-id="3d38f-123">Operacja zachowania są określane za pomocą <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="3d38f-123">Operation behaviors are specified by using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="3d38f-124">W poniższej tabeli opisano niektóre z tych zachowań.</span><span class="sxs-lookup"><span data-stu-id="3d38f-124">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="3d38f-125">Zachowanie działania</span><span class="sxs-lookup"><span data-stu-id="3d38f-125">Operation Behavior</span></span>|<span data-ttu-id="3d38f-126">Opis</span><span class="sxs-lookup"><span data-stu-id="3d38f-126">Description</span></span>|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|<span data-ttu-id="3d38f-127">Określa, czy zakończenie operacji usługi zatwierdzenia bieżącej transakcji.</span><span class="sxs-lookup"><span data-stu-id="3d38f-127">Determines whether service operation completion commits the current transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|<span data-ttu-id="3d38f-128">Określa, czy operacja usługi pozyskuje w ramach transakcji przekazane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="3d38f-128">Determines whether the service operation enlists in a client-flowed transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|<span data-ttu-id="3d38f-129">Określa, czy operacja usługi personifikuje tożsamości elementu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="3d38f-129">Determines whether the service operation impersonates the caller's identity.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|<span data-ttu-id="3d38f-130">Określa, czy wystąpienia usługi są odtwarzania na początku lub końcu wywołania operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="3d38f-130">Determines whether service instances are recycled at the start or end of the service operation call.</span></span>|  
  
 <span data-ttu-id="3d38f-131">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="3d38f-131">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="3d38f-132">Opóźnienie między wywołania jest wynikiem wywołania `System.Threading.Thread.Sleep()` w operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="3d38f-132">The delay between the calls is the result of the calls to `System.Threading.Thread.Sleep()` made in the service operations.</span></span> <span data-ttu-id="3d38f-133">Pozostałe przykłady zachowanie wyjaśnić te zachowania bardziej szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="3d38f-133">The rest of the behavior samples explain these behaviors in more detail.</span></span> <span data-ttu-id="3d38f-134">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="3d38f-134">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3d38f-135">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="3d38f-135">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3d38f-136">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3d38f-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="3d38f-137">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3d38f-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="3d38f-138">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3d38f-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3d38f-139">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="3d38f-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3d38f-140">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="3d38f-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3d38f-141">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="3d38f-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3d38f-142">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="3d38f-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
  
## <a name="see-also"></a><span data-ttu-id="3d38f-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3d38f-143">See Also</span></span>
