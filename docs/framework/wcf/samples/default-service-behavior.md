---
title: "Domyślne zachowanie usługi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 57d534a1af16790aa6c3477629f0d4b6e2604179
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="default-service-behavior"></a><span data-ttu-id="fcba4-102">Domyślne zachowanie usługi</span><span class="sxs-lookup"><span data-stu-id="fcba4-102">Default Service Behavior</span></span>
<span data-ttu-id="fcba4-103">W przykładzie pokazano, jak można skonfigurować ustawienia zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="fcba4-103">This sample demonstrates how service behavior settings can be configured.</span></span> <span data-ttu-id="fcba4-104">Próbki jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), który implementuje `ICalculator` kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="fcba4-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="fcba4-105">W tym przykładzie jawnie definiuje zachowania usługi i zachowania operację przy użyciu <xref:System.ServiceModel.ServiceBehaviorAttribute> i <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutów.</span><span class="sxs-lookup"><span data-stu-id="fcba4-105">This sample explicitly defines service behaviors and operation behaviors using the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes.</span></span> <span data-ttu-id="fcba4-106">Zachowania można skonfigurować w plikach konfiguracji lub imperatively w kodzie (jak pokazano w przykładzie).</span><span class="sxs-lookup"><span data-stu-id="fcba4-106">You can configure behaviors in configuration files or imperatively in code (as this sample demonstrates).</span></span>  
  
 <span data-ttu-id="fcba4-107">W tym przykładzie klient jest aplikacji konsoli (.exe), a usługa jest obsługiwana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="fcba4-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fcba4-108">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="fcba4-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="fcba4-109">Klasa usługi określa zachowania z <xref:System.ServiceModel.ServiceBehaviorAttribute> i <xref:System.ServiceModel.OperationBehaviorAttribute> jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="fcba4-109">The service class specifies behaviors with the <xref:System.ServiceModel.ServiceBehaviorAttribute> and the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following code sample.</span></span> <span data-ttu-id="fcba4-110">Wszystkie wartości są ustawienia domyślne.</span><span class="sxs-lookup"><span data-stu-id="fcba4-110">All values specified are the defaults.</span></span>  
  
```  
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
  
 <span data-ttu-id="fcba4-111">Zachowania usług są określane za pomocą <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="fcba4-111">Service behaviors are specified with the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span> <span data-ttu-id="fcba4-112">W poniższej tabeli opisano niektóre z tych zachowań.</span><span class="sxs-lookup"><span data-stu-id="fcba4-112">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="fcba4-113">Zachowanie usługi</span><span class="sxs-lookup"><span data-stu-id="fcba4-113">Service behavior</span></span>|<span data-ttu-id="fcba4-114">Opis</span><span class="sxs-lookup"><span data-stu-id="fcba4-114">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|<span data-ttu-id="fcba4-115">Automatycznie zamknięty sesji w żądaniu klienta.</span><span class="sxs-lookup"><span data-stu-id="fcba4-115">Automatically shuts down a session at the client's request.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|<span data-ttu-id="fcba4-116">Określa tryb współbieżności dla każdego wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="fcba4-116">Specifies the concurrency mode for each service instance.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|<span data-ttu-id="fcba4-117">Określa tryb kontekstu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="fcba4-117">Specifies the instance context mode.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|<span data-ttu-id="fcba4-118">Określa, czy używać kontekstu synchronizacji podany, jeśli jest on ustawiony.</span><span class="sxs-lookup"><span data-stu-id="fcba4-118">Determines whether to use the provided synchronization context, if one is set.</span></span> <span data-ttu-id="fcba4-119">Użyj go, jeśli chcesz określić, czy używać `WindowsFormsSynchronizationContext` w aplikacjach formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="fcba4-119">Use this when you want to control whether to use a `WindowsFormsSynchronizationContext` in Windows Forms applications.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|<span data-ttu-id="fcba4-120">Określa, czy Wyjątki ogólne nieobsłużonego są do przekonwertowania na `Fault<string>` i wysłany jako komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="fcba4-120">Determines whether general unhandled execution exceptions are to be converted into a `Fault<string>` and sent as a fault message.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|<span data-ttu-id="fcba4-121">Określa poziom izolacji transakcji.</span><span class="sxs-lookup"><span data-stu-id="fcba4-121">Specifies the isolation level for transactions.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|<span data-ttu-id="fcba4-122">Określa, czy nagłówki nieoczekiwany komunikat spowodować wystąpienie stanu błędu.</span><span class="sxs-lookup"><span data-stu-id="fcba4-122">Determines whether unexpected message headers cause an error condition.</span></span>|  
  
 <span data-ttu-id="fcba4-123">Operacja zachowania są określane przy użyciu <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="fcba4-123">Operation behaviors are specified by using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="fcba4-124">W poniższej tabeli opisano niektóre z tych zachowań.</span><span class="sxs-lookup"><span data-stu-id="fcba4-124">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="fcba4-125">Zachowanie działania</span><span class="sxs-lookup"><span data-stu-id="fcba4-125">Operation Behavior</span></span>|<span data-ttu-id="fcba4-126">Opis</span><span class="sxs-lookup"><span data-stu-id="fcba4-126">Description</span></span>|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|<span data-ttu-id="fcba4-127">Określa, czy zakończenie operacji usługi zatwierdza bieżącej transakcji.</span><span class="sxs-lookup"><span data-stu-id="fcba4-127">Determines whether service operation completion commits the current transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|<span data-ttu-id="fcba4-128">Określa, czy operacja usługi powoduje zarejestrowanie w transakcji przepływ klienta.</span><span class="sxs-lookup"><span data-stu-id="fcba4-128">Determines whether the service operation enlists in a client-flowed transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|<span data-ttu-id="fcba4-129">Określa, czy operacja usługi personifikuje tożsamości obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="fcba4-129">Determines whether the service operation impersonates the caller's identity.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|<span data-ttu-id="fcba4-130">Określa, czy wystąpienie usługi są odtwarzania początek lub koniec wywołania operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="fcba4-130">Determines whether service instances are recycled at the start or end of the service operation call.</span></span>|  
  
 <span data-ttu-id="fcba4-131">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="fcba4-131">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="fcba4-132">Opóźnienie między wywołaniami jest wynikiem wywołania `System.Threading.Thread.Sleep()` w operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="fcba4-132">The delay between the calls is the result of the calls to `System.Threading.Thread.Sleep()` made in the service operations.</span></span> <span data-ttu-id="fcba4-133">Pozostałe przykłady zachowanie opisano te zachowania bardziej szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="fcba4-133">The rest of the behavior samples explain these behaviors in more detail.</span></span> <span data-ttu-id="fcba4-134">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="fcba4-134">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fcba4-135">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="fcba4-135">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="fcba4-136">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fcba4-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="fcba4-137">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fcba4-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="fcba4-138">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fcba4-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fcba4-139">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="fcba4-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fcba4-140">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="fcba4-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fcba4-141">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="fcba4-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fcba4-142">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="fcba4-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
  
## <a name="see-also"></a><span data-ttu-id="fcba4-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fcba4-143">See Also</span></span>
