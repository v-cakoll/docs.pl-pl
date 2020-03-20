---
title: Domyślne zachowanie usługi
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: 798231cbfddf17dd63a61f3e2a07a6490289e56f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183750"
---
# <a name="default-service-behavior"></a><span data-ttu-id="a5a9c-102">Domyślne zachowanie usługi</span><span class="sxs-lookup"><span data-stu-id="a5a9c-102">Default Service Behavior</span></span>
<span data-ttu-id="a5a9c-103">W tym przykładzie pokazano, jak można skonfigurować ustawienia zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-103">This sample demonstrates how service behavior settings can be configured.</span></span> <span data-ttu-id="a5a9c-104">Próbka jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), `ICalculator` który implementuje umowy serwisowej.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="a5a9c-105">Ten przykład jawnie definiuje zachowania usługi i <xref:System.ServiceModel.ServiceBehaviorAttribute> zachowania <xref:System.ServiceModel.OperationBehaviorAttribute> operacji przy użyciu i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-105">This sample explicitly defines service behaviors and operation behaviors using the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes.</span></span> <span data-ttu-id="a5a9c-106">Można skonfigurować zachowania w plikach konfiguracyjnych lub w trybie pilnym w kodzie (jak pokazuje ten przykład).</span><span class="sxs-lookup"><span data-stu-id="a5a9c-106">You can configure behaviors in configuration files or imperatively in code (as this sample demonstrates).</span></span>  
  
 <span data-ttu-id="a5a9c-107">W tym przykładzie klient jest aplikacją konsoli (.exe), a usługa jest obsługiwana przez internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="a5a9c-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a5a9c-108">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a5a9c-109">Klasa usługi określa zachowania z <xref:System.ServiceModel.ServiceBehaviorAttribute> i <xref:System.ServiceModel.OperationBehaviorAttribute> jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-109">The service class specifies behaviors with the <xref:System.ServiceModel.ServiceBehaviorAttribute> and the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following code sample.</span></span> <span data-ttu-id="a5a9c-110">Wszystkie określone wartości są wartościami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-110">All values specified are the defaults.</span></span>  
  
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
  
 <span data-ttu-id="a5a9c-111">Zachowania usługi są określone <xref:System.ServiceModel.ServiceBehaviorAttribute> za pomocą atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-111">Service behaviors are specified with the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span> <span data-ttu-id="a5a9c-112">W poniższej tabeli opisano niektóre z tych zachowań.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-112">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="a5a9c-113">Zachowanie usługi</span><span class="sxs-lookup"><span data-stu-id="a5a9c-113">Service behavior</span></span>|<span data-ttu-id="a5a9c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a5a9c-114">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|<span data-ttu-id="a5a9c-115">Automatycznie zamyka sesję na żądanie klienta.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-115">Automatically shuts down a session at the client's request.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|<span data-ttu-id="a5a9c-116">Określa tryb współbieżności dla każdego wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-116">Specifies the concurrency mode for each service instance.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|<span data-ttu-id="a5a9c-117">Określa tryb kontekstu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-117">Specifies the instance context mode.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|<span data-ttu-id="a5a9c-118">Określa, czy należy użyć podanego kontekstu synchronizacji, jeśli jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-118">Determines whether to use the provided synchronization context, if one is set.</span></span> <span data-ttu-id="a5a9c-119">Użyj tego, aby kontrolować, czy `WindowsFormsSynchronizationContext` w aplikacjach Windows Forms ma być używana aplikacja Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-119">Use this when you want to control whether to use a `WindowsFormsSynchronizationContext` in Windows Forms applications.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|<span data-ttu-id="a5a9c-120">Określa, czy ogólne nieobsługiwać wyjątki wykonywania `Fault<string>` mają być konwertowane na a i wysyłane jako komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-120">Determines whether general unhandled execution exceptions are to be converted into a `Fault<string>` and sent as a fault message.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|<span data-ttu-id="a5a9c-121">Określa poziom izolacji dla transakcji.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-121">Specifies the isolation level for transactions.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|<span data-ttu-id="a5a9c-122">Określa, czy nieoczekiwane nagłówki wiadomości powodują stan błędu.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-122">Determines whether unexpected message headers cause an error condition.</span></span>|  
  
 <span data-ttu-id="a5a9c-123">Zachowania operacji są określane <xref:System.ServiceModel.OperationBehaviorAttribute> przy użyciu atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-123">Operation behaviors are specified by using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="a5a9c-124">W poniższej tabeli opisano niektóre z tych zachowań.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-124">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="a5a9c-125">Zachowanie operacji</span><span class="sxs-lookup"><span data-stu-id="a5a9c-125">Operation Behavior</span></span>|<span data-ttu-id="a5a9c-126">Opis</span><span class="sxs-lookup"><span data-stu-id="a5a9c-126">Description</span></span>|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|<span data-ttu-id="a5a9c-127">Określa, czy zakończenie operacji usługi zatwierdza bieżącą transakcję.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-127">Determines whether service operation completion commits the current transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|<span data-ttu-id="a5a9c-128">Określa, czy operacja usługi rejestruje się w transakcji przepływanych przez klienta.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-128">Determines whether the service operation enlists in a client-flowed transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|<span data-ttu-id="a5a9c-129">Określa, czy operacja usługi personifikuje tożsamość wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-129">Determines whether the service operation impersonates the caller's identity.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|<span data-ttu-id="a5a9c-130">Określa, czy wystąpienia usługi są odtwo cenach odtworzyć na początku lub na końcu wywołania operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-130">Determines whether service instances are recycled at the start or end of the service operation call.</span></span>|  
  
 <span data-ttu-id="a5a9c-131">Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-131">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a5a9c-132">Opóźnienie między wywołaniami jest wynikiem `System.Threading.Thread.Sleep()` wywołań w operacjach usługi.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-132">The delay between the calls is the result of the calls to `System.Threading.Thread.Sleep()` made in the service operations.</span></span> <span data-ttu-id="a5a9c-133">Pozostałe przykłady zachowania wyjaśnić te zachowania bardziej szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-133">The rest of the behavior samples explain these behaviors in more detail.</span></span> <span data-ttu-id="a5a9c-134">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-134">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a5a9c-135">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="a5a9c-135">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a5a9c-136">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a5a9c-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a5a9c-137">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a5a9c-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a5a9c-138">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a5a9c-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a5a9c-139">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a5a9c-140">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-140">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a5a9c-141">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a5a9c-142">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a5a9c-142">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
