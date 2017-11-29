---
title: "Obsługa w działaniu Flowchart przy użyciu TryCatch błędów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 490647f8ea3662f046cadecf5a97761c43b357f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a><span data-ttu-id="c5e57-102">Obsługa w działaniu Flowchart przy użyciu TryCatch błędów</span><span class="sxs-lookup"><span data-stu-id="c5e57-102">Fault Handling in a Flowchart Activity Using TryCatch</span></span>
<span data-ttu-id="c5e57-103">W tym przykładzie pokazano sposób <xref:System.Activities.Statements.TryCatch> działanie może być używane w ramach działania przepływu sterowania złożonego.</span><span class="sxs-lookup"><span data-stu-id="c5e57-103">This sample shows how the <xref:System.Activities.Statements.TryCatch> activity can be used within a complex control flow activity.</span></span>  
  
 <span data-ttu-id="c5e57-104">W tym przykładzie kodu podwyższenia poziomu i liczbę elementów podrzędnych są przekazywane jako zmienne <xref:System.Activities.Statements.Flowchart> działanie, które oblicza rabat oparte na pochodnych, które odnoszą się do kodu podwyższenia poziomu.</span><span class="sxs-lookup"><span data-stu-id="c5e57-104">In this sample, a promotion code and number of children are passed as variables to a <xref:System.Activities.Statements.Flowchart> activity that calculates a discount based on formulae that correspond to the promotion code.</span></span> <span data-ttu-id="c5e57-105">Przykład obejmuje konieczne wersje projektanta kodu i przepływ pracy próbki.</span><span class="sxs-lookup"><span data-stu-id="c5e57-105">The sample includes imperative code and workflow designer versions of the sample.</span></span>  
  
 <span data-ttu-id="c5e57-106">W poniższej tabeli przedstawiono zmienne `CreateFlowchartWithFaults` działania.</span><span class="sxs-lookup"><span data-stu-id="c5e57-106">The following table details the variables for the `CreateFlowchartWithFaults` activity.</span></span>  
  
|<span data-ttu-id="c5e57-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5e57-107">Parameters</span></span>|<span data-ttu-id="c5e57-108">Opis</span><span class="sxs-lookup"><span data-stu-id="c5e57-108">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="c5e57-109">promoCode</span><span class="sxs-lookup"><span data-stu-id="c5e57-109">promoCode</span></span>|<span data-ttu-id="c5e57-110">Kod promocji.</span><span class="sxs-lookup"><span data-stu-id="c5e57-110">The promotion code.</span></span> <span data-ttu-id="c5e57-111">Typ: ciąg</span><span class="sxs-lookup"><span data-stu-id="c5e57-111">Type: String</span></span><br /><br /> <span data-ttu-id="c5e57-112">Możliwe wartości z opisem w nawiasach:</span><span class="sxs-lookup"><span data-stu-id="c5e57-112">The possible values with description in parentheses:</span></span><br /><br /> <span data-ttu-id="c5e57-113">-Pojedynczy (jeden)</span><span class="sxs-lookup"><span data-stu-id="c5e57-113">-   Single (Single)</span></span><br /><span data-ttu-id="c5e57-114">-MNK (zamężna z nie dzieci).</span><span class="sxs-lookup"><span data-stu-id="c5e57-114">-   MNK (Married with no kids.)</span></span><br /><span data-ttu-id="c5e57-115">-MWK (zamężna dla dzieci).</span><span class="sxs-lookup"><span data-stu-id="c5e57-115">-   MWK (Married with kids.)</span></span>|  
|<span data-ttu-id="c5e57-116">numKids</span><span class="sxs-lookup"><span data-stu-id="c5e57-116">numKids</span></span>|<span data-ttu-id="c5e57-117">Liczba elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="c5e57-117">The number of children.</span></span> <span data-ttu-id="c5e57-118">Typ: int</span><span class="sxs-lookup"><span data-stu-id="c5e57-118">Type: int</span></span>|  
  
 <span data-ttu-id="c5e57-119">`CreateFlowchartWithFaults` Używa działania <xref:System.Activities.Statements.FlowSwitch%601> działanie, które zmienia się na `promoCode` argumentu i obliczanie rabatu przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="c5e57-119">The `CreateFlowchartWithFaults` activity uses a <xref:System.Activities.Statements.FlowSwitch%601> activity that switches on the `promoCode` argument and calculates the discount using the following formula.</span></span>  
  
|<span data-ttu-id="c5e57-120">Wartość`promoCode`</span><span class="sxs-lookup"><span data-stu-id="c5e57-120">Value of `promoCode`</span></span>|<span data-ttu-id="c5e57-121">Rabat (%)</span><span class="sxs-lookup"><span data-stu-id="c5e57-121">Discount (%)</span></span>|  
|--------------------------|--------------------|  
|<span data-ttu-id="c5e57-122">Single</span><span class="sxs-lookup"><span data-stu-id="c5e57-122">Single</span></span>|<span data-ttu-id="c5e57-123">10</span><span class="sxs-lookup"><span data-stu-id="c5e57-123">10</span></span>|  
|<span data-ttu-id="c5e57-124">MNK</span><span class="sxs-lookup"><span data-stu-id="c5e57-124">MNK</span></span>|<span data-ttu-id="c5e57-125">15</span><span class="sxs-lookup"><span data-stu-id="c5e57-125">15</span></span>|  
|<span data-ttu-id="c5e57-126">MWK</span><span class="sxs-lookup"><span data-stu-id="c5e57-126">MWK</span></span>|<span data-ttu-id="c5e57-127">15 + (1 – 1 /`numberOfKids`)\*10 **Uwaga:** potencjalnie może zgłosić tego obliczenia <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="c5e57-127">15 + (1 – 1/`numberOfKids`)\*10 **Note:**  Potentially, this calculation can throw a <xref:System.DivideByZeroException>.</span></span> <span data-ttu-id="c5e57-128">Tak, otoczona obliczeń rabatu <xref:System.Activities.Statements.TryCatch> działania, który przechwytuje <xref:System.DivideByZeroException> wyjątku i ustawia rabat na zero.</span><span class="sxs-lookup"><span data-stu-id="c5e57-128">So, the discount calculation is wrapped in a <xref:System.Activities.Statements.TryCatch> activity that catches the <xref:System.DivideByZeroException> exception and sets the discount to zero.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="c5e57-129">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="c5e57-129">To use this sample</span></span>  
  
1.  <span data-ttu-id="c5e57-130">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania FlowchartWithFaultHandling.sln.</span><span class="sxs-lookup"><span data-stu-id="c5e57-130">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the FlowchartWithFaultHandling.sln solution file.</span></span>  
  
2.  <span data-ttu-id="c5e57-131">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="c5e57-131">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="c5e57-132">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="c5e57-132">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c5e57-133">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="c5e57-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c5e57-134">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="c5e57-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c5e57-135">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="c5e57-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c5e57-136">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c5e57-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`  
  
## <a name="see-also"></a><span data-ttu-id="c5e57-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5e57-137">See Also</span></span>  
 [<span data-ttu-id="c5e57-138">Schemat blokowy przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="c5e57-138">Flowchart Workflows</span></span>](../../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)  
 [<span data-ttu-id="c5e57-139">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="c5e57-139">Exceptions</span></span>](../../../../docs/framework/windows-workflow-foundation/exceptions.md)
