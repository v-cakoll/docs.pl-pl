---
title: Domyślne zachowanie usługi
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: 3728d9808eb0ad90d24a894b18857e414906f9f3
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045021"
---
# <a name="default-service-behavior"></a><span data-ttu-id="f5df9-102">Domyślne zachowanie usługi</span><span class="sxs-lookup"><span data-stu-id="f5df9-102">Default Service Behavior</span></span>
<span data-ttu-id="f5df9-103">Ten przykład pokazuje, jak można skonfigurować ustawienia zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="f5df9-103">This sample demonstrates how service behavior settings can be configured.</span></span> <span data-ttu-id="f5df9-104">Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje `ICalculator` kontrakt usługi.</span><span class="sxs-lookup"><span data-stu-id="f5df9-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="f5df9-105">Ten przykład jawnie definiuje zachowania usługi i zachowania operacji przy użyciu <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutów <xref:System.ServiceModel.OperationBehaviorAttribute> i.</span><span class="sxs-lookup"><span data-stu-id="f5df9-105">This sample explicitly defines service behaviors and operation behaviors using the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes.</span></span> <span data-ttu-id="f5df9-106">Można skonfigurować zachowania w plikach konfiguracyjnych lub w sposób niezależny w kodzie (jak pokazano w tym przykładzie).</span><span class="sxs-lookup"><span data-stu-id="f5df9-106">You can configure behaviors in configuration files or imperatively in code (as this sample demonstrates).</span></span>  
  
 <span data-ttu-id="f5df9-107">W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="f5df9-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5df9-108">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="f5df9-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f5df9-109">Klasa usługi określa zachowania z <xref:System.ServiceModel.ServiceBehaviorAttribute> i, <xref:System.ServiceModel.OperationBehaviorAttribute> jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="f5df9-109">The service class specifies behaviors with the <xref:System.ServiceModel.ServiceBehaviorAttribute> and the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following code sample.</span></span> <span data-ttu-id="f5df9-110">Wszystkie określone wartości są wartościami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="f5df9-110">All values specified are the defaults.</span></span>  
  
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
  
 <span data-ttu-id="f5df9-111">Zachowania usługi są określane przy użyciu <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f5df9-111">Service behaviors are specified with the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span> <span data-ttu-id="f5df9-112">W poniższej tabeli opisano niektóre z tych zachowań.</span><span class="sxs-lookup"><span data-stu-id="f5df9-112">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="f5df9-113">Zachowanie usługi</span><span class="sxs-lookup"><span data-stu-id="f5df9-113">Service behavior</span></span>|<span data-ttu-id="f5df9-114">Opis</span><span class="sxs-lookup"><span data-stu-id="f5df9-114">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|<span data-ttu-id="f5df9-115">Automatycznie zamyka sesję na żądanie klienta.</span><span class="sxs-lookup"><span data-stu-id="f5df9-115">Automatically shuts down a session at the client's request.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|<span data-ttu-id="f5df9-116">Określa tryb współbieżności dla każdego wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="f5df9-116">Specifies the concurrency mode for each service instance.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|<span data-ttu-id="f5df9-117">Określa tryb kontekstu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f5df9-117">Specifies the instance context mode.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|<span data-ttu-id="f5df9-118">Określa, czy należy użyć podanego kontekstu synchronizacji, jeśli został ustawiony.</span><span class="sxs-lookup"><span data-stu-id="f5df9-118">Determines whether to use the provided synchronization context, if one is set.</span></span> <span data-ttu-id="f5df9-119">Użyj tego, jeśli chcesz kontrolować, czy należy używać `WindowsFormsSynchronizationContext` w Windows Forms aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f5df9-119">Use this when you want to control whether to use a `WindowsFormsSynchronizationContext` in Windows Forms applications.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|<span data-ttu-id="f5df9-120">Określa, czy ogólne Nieobsłużone wyjątki wykonywania mają być konwertowane do `Fault<string>` i wysyłane jako komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="f5df9-120">Determines whether general unhandled execution exceptions are to be converted into a `Fault<string>` and sent as a fault message.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|<span data-ttu-id="f5df9-121">Określa poziom izolacji dla transakcji.</span><span class="sxs-lookup"><span data-stu-id="f5df9-121">Specifies the isolation level for transactions.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|<span data-ttu-id="f5df9-122">Określa, czy nieoczekiwane nagłówki komunikatów powodują wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="f5df9-122">Determines whether unexpected message headers cause an error condition.</span></span>|  
  
 <span data-ttu-id="f5df9-123">Zachowania operacji są określane przy użyciu <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f5df9-123">Operation behaviors are specified by using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="f5df9-124">W poniższej tabeli opisano niektóre z tych zachowań.</span><span class="sxs-lookup"><span data-stu-id="f5df9-124">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="f5df9-125">Zachowanie operacji</span><span class="sxs-lookup"><span data-stu-id="f5df9-125">Operation Behavior</span></span>|<span data-ttu-id="f5df9-126">Opis</span><span class="sxs-lookup"><span data-stu-id="f5df9-126">Description</span></span>|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|<span data-ttu-id="f5df9-127">Określa, czy zakończenie operacji usługi zatwierdza bieżącą transakcję.</span><span class="sxs-lookup"><span data-stu-id="f5df9-127">Determines whether service operation completion commits the current transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|<span data-ttu-id="f5df9-128">Określa, czy operacja usługi jest rejestrowana w transakcji przepływającej przez klienta.</span><span class="sxs-lookup"><span data-stu-id="f5df9-128">Determines whether the service operation enlists in a client-flowed transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|<span data-ttu-id="f5df9-129">Określa, czy operacja usługi personifikuje tożsamość obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="f5df9-129">Determines whether the service operation impersonates the caller's identity.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|<span data-ttu-id="f5df9-130">Określa, czy wystąpienia usługi są odtwarzane na początku, czy na końcu wywołania operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="f5df9-130">Determines whether service instances are recycled at the start or end of the service operation call.</span></span>|  
  
 <span data-ttu-id="f5df9-131">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="f5df9-131">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="f5df9-132">Opóźnienie między wywołaniami to wynik wywołań `System.Threading.Thread.Sleep()` wykonanych w operacjach usługi.</span><span class="sxs-lookup"><span data-stu-id="f5df9-132">The delay between the calls is the result of the calls to `System.Threading.Thread.Sleep()` made in the service operations.</span></span> <span data-ttu-id="f5df9-133">Pozostałe przykłady zachowania wyjaśniają te zachowania bardziej szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="f5df9-133">The rest of the behavior samples explain these behaviors in more detail.</span></span> <span data-ttu-id="f5df9-134">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="f5df9-134">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f5df9-135">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="f5df9-135">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f5df9-136">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f5df9-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="f5df9-137">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f5df9-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="f5df9-138">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f5df9-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f5df9-139">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="f5df9-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f5df9-140">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="f5df9-140">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="f5df9-141">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="f5df9-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f5df9-142">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="f5df9-142">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
