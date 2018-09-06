---
title: Obsługa błędów w schematu blokowego przy użyciu działania TryCatch
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: e89c80ecfa8ec93fdde82b5638c504ded681a4fc
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864696"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a><span data-ttu-id="2d678-102">Obsługa błędów w schematu blokowego przy użyciu działania TryCatch</span><span class="sxs-lookup"><span data-stu-id="2d678-102">Fault Handling in a Flowchart Activity Using TryCatch</span></span>
<span data-ttu-id="2d678-103">W tym przykładzie pokazano sposób, w jaki <xref:System.Activities.Statements.TryCatch> działanie może być używane w ramach działania przepływu sterowania złożonego.</span><span class="sxs-lookup"><span data-stu-id="2d678-103">This sample shows how the <xref:System.Activities.Statements.TryCatch> activity can be used within a complex control flow activity.</span></span>  
  
 <span data-ttu-id="2d678-104">W tym przykładzie kodu promocyjnego, a liczba elementów podrzędnych są przekazywane jako zmienne <xref:System.Activities.Statements.Flowchart> działania, który oblicza rabat w wysokości oparte na formuł, które odpowiadają kodu promocyjnego.</span><span class="sxs-lookup"><span data-stu-id="2d678-104">In this sample, a promotion code and number of children are passed as variables to a <xref:System.Activities.Statements.Flowchart> activity that calculates a discount based on formulae that correspond to the promotion code.</span></span> <span data-ttu-id="2d678-105">Przykład obejmuje imperatywne wersje projektanta kodu i przepływ pracy próbki.</span><span class="sxs-lookup"><span data-stu-id="2d678-105">The sample includes imperative code and workflow designer versions of the sample.</span></span>  
  
 <span data-ttu-id="2d678-106">W poniższej tabeli przedstawiono zmienne `CreateFlowchartWithFaults` działania.</span><span class="sxs-lookup"><span data-stu-id="2d678-106">The following table details the variables for the `CreateFlowchartWithFaults` activity.</span></span>  
  
|<span data-ttu-id="2d678-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="2d678-107">Parameters</span></span>|<span data-ttu-id="2d678-108">Opis</span><span class="sxs-lookup"><span data-stu-id="2d678-108">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="2d678-109">promoCode</span><span class="sxs-lookup"><span data-stu-id="2d678-109">promoCode</span></span>|<span data-ttu-id="2d678-110">Kod promocyjny.</span><span class="sxs-lookup"><span data-stu-id="2d678-110">The promotion code.</span></span> <span data-ttu-id="2d678-111">Typ: ciąg</span><span class="sxs-lookup"><span data-stu-id="2d678-111">Type: String</span></span><br /><br /> <span data-ttu-id="2d678-112">Możliwe wartości z opisem w nawiasach:</span><span class="sxs-lookup"><span data-stu-id="2d678-112">The possible values with description in parentheses:</span></span><br /><br /> <span data-ttu-id="2d678-113">-Pojedynczy (pojedynczo)</span><span class="sxs-lookup"><span data-stu-id="2d678-113">-   Single (Single)</span></span><br /><span data-ttu-id="2d678-114">-MNK (małżeństwa z nie dzieci).</span><span class="sxs-lookup"><span data-stu-id="2d678-114">-   MNK (Married with no kids.)</span></span><br /><span data-ttu-id="2d678-115">-MWK (małżeństwa dla dzieci.)</span><span class="sxs-lookup"><span data-stu-id="2d678-115">-   MWK (Married with kids.)</span></span>|  
|<span data-ttu-id="2d678-116">numKids</span><span class="sxs-lookup"><span data-stu-id="2d678-116">numKids</span></span>|<span data-ttu-id="2d678-117">Liczba elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="2d678-117">The number of children.</span></span> <span data-ttu-id="2d678-118">Typ: int</span><span class="sxs-lookup"><span data-stu-id="2d678-118">Type: int</span></span>|  
  
 <span data-ttu-id="2d678-119">`CreateFlowchartWithFaults` Używa działania <xref:System.Activities.Statements.FlowSwitch%601> działanie, które zmienia się na `promoCode` argumentu i oblicza rabat, korzystając z następującego wzoru.</span><span class="sxs-lookup"><span data-stu-id="2d678-119">The `CreateFlowchartWithFaults` activity uses a <xref:System.Activities.Statements.FlowSwitch%601> activity that switches on the `promoCode` argument and calculates the discount using the following formula.</span></span>  
  
|<span data-ttu-id="2d678-120">Wartość `promoCode`</span><span class="sxs-lookup"><span data-stu-id="2d678-120">Value of `promoCode`</span></span>|<span data-ttu-id="2d678-121">Rabat na wersję (%)</span><span class="sxs-lookup"><span data-stu-id="2d678-121">Discount (%)</span></span>|  
|--------------------------|--------------------|  
|<span data-ttu-id="2d678-122">Single</span><span class="sxs-lookup"><span data-stu-id="2d678-122">Single</span></span>|<span data-ttu-id="2d678-123">10</span><span class="sxs-lookup"><span data-stu-id="2d678-123">10</span></span>|  
|<span data-ttu-id="2d678-124">MNK</span><span class="sxs-lookup"><span data-stu-id="2d678-124">MNK</span></span>|<span data-ttu-id="2d678-125">15</span><span class="sxs-lookup"><span data-stu-id="2d678-125">15</span></span>|  
|<span data-ttu-id="2d678-126">MWK</span><span class="sxs-lookup"><span data-stu-id="2d678-126">MWK</span></span>|<span data-ttu-id="2d678-127">15 + (1 – 1 /`numberOfKids`)\*10 **Uwaga:** potencjalnie może zgłosić to obliczenie <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="2d678-127">15 + (1 – 1/`numberOfKids`)\*10 **Note:**  Potentially, this calculation can throw a <xref:System.DivideByZeroException>.</span></span> <span data-ttu-id="2d678-128">Dlatego obliczeń rabatu jest opakowana w <xref:System.Activities.Statements.TryCatch> działanie, które przechwytuje <xref:System.DivideByZeroException> wyjątek i ustawia rabat na zero.</span><span class="sxs-lookup"><span data-stu-id="2d678-128">So, the discount calculation is wrapped in a <xref:System.Activities.Statements.TryCatch> activity that catches the <xref:System.DivideByZeroException> exception and sets the discount to zero.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="2d678-129">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="2d678-129">To use this sample</span></span>  
  
1.  <span data-ttu-id="2d678-130">Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania FlowchartWithFaultHandling.sln.</span><span class="sxs-lookup"><span data-stu-id="2d678-130">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the FlowchartWithFaultHandling.sln solution file.</span></span>  
  
2.  <span data-ttu-id="2d678-131">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="2d678-131">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="2d678-132">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="2d678-132">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2d678-133">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="2d678-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2d678-134">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="2d678-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2d678-135">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="2d678-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2d678-136">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d678-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`  
  
## <a name="see-also"></a><span data-ttu-id="2d678-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d678-137">See Also</span></span>  
 [<span data-ttu-id="2d678-138">Przepływy pracy schematów blokowych</span><span class="sxs-lookup"><span data-stu-id="2d678-138">Flowchart Workflows</span></span>](../../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)  
 [<span data-ttu-id="2d678-139">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="2d678-139">Exceptions</span></span>](../../../../docs/framework/windows-workflow-foundation/exceptions.md)
