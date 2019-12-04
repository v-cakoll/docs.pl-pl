---
title: Obsługa błędów w działaniu schematu blokowego przy użyciu działania TryCatch
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: 8e3ca59bc9743300a230877a6fbcbed5468a1589
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74710837"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a><span data-ttu-id="bb666-102">Obsługa błędów w działaniu schematu blokowego przy użyciu działania TryCatch</span><span class="sxs-lookup"><span data-stu-id="bb666-102">Fault Handling in a Flowchart Activity Using TryCatch</span></span>

<span data-ttu-id="bb666-103">Ten przykład pokazuje, jak aktywność <xref:System.Activities.Statements.TryCatch> może być używana w działaniu przepływu sterowania złożonego.</span><span class="sxs-lookup"><span data-stu-id="bb666-103">This sample shows how the <xref:System.Activities.Statements.TryCatch> activity can be used within a complex control flow activity.</span></span>

<span data-ttu-id="bb666-104">W tym przykładzie kod promocyjny i liczba elementów podrzędnych są przesyłane jako zmienne do działania <xref:System.Activities.Statements.Flowchart>, które oblicza rabat na podstawie formuły odpowiadającej kodowi promocji.</span><span class="sxs-lookup"><span data-stu-id="bb666-104">In this sample, a promotion code and number of children are passed as variables to a <xref:System.Activities.Statements.Flowchart> activity that calculates a discount based on formulae that correspond to the promotion code.</span></span> <span data-ttu-id="bb666-105">Przykład obejmuje bezwzględny kod i wersje projektanta przepływu pracy dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="bb666-105">The sample includes imperative code and workflow designer versions of the sample.</span></span>

<span data-ttu-id="bb666-106">W poniższej tabeli przedstawiono zmienne działania `CreateFlowchartWithFaults`.</span><span class="sxs-lookup"><span data-stu-id="bb666-106">The following table details the variables for the `CreateFlowchartWithFaults` activity.</span></span>

|<span data-ttu-id="bb666-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb666-107">Parameters</span></span>|<span data-ttu-id="bb666-108">Opis</span><span class="sxs-lookup"><span data-stu-id="bb666-108">Description</span></span>|
|----------------|-----------------|
|<span data-ttu-id="bb666-109">promoCode</span><span class="sxs-lookup"><span data-stu-id="bb666-109">promoCode</span></span>|<span data-ttu-id="bb666-110">Kod promocyjny.</span><span class="sxs-lookup"><span data-stu-id="bb666-110">The promotion code.</span></span> <span data-ttu-id="bb666-111">Typ: ciąg</span><span class="sxs-lookup"><span data-stu-id="bb666-111">Type: String</span></span><br /><br /> <span data-ttu-id="bb666-112">Możliwe wartości z opisem w nawiasach:</span><span class="sxs-lookup"><span data-stu-id="bb666-112">The possible values with description in parentheses:</span></span><br /><br /> <span data-ttu-id="bb666-113">-Pojedyncza (pojedyncza)</span><span class="sxs-lookup"><span data-stu-id="bb666-113">-   Single (Single)</span></span><br /><span data-ttu-id="bb666-114">-MNK (ślub bez dzieci)</span><span class="sxs-lookup"><span data-stu-id="bb666-114">-   MNK (Married with no kids.)</span></span><br /><span data-ttu-id="bb666-115">-MWK (ślub z dziecięcymi).</span><span class="sxs-lookup"><span data-stu-id="bb666-115">-   MWK (Married with kids.)</span></span>|
|<span data-ttu-id="bb666-116">numKids</span><span class="sxs-lookup"><span data-stu-id="bb666-116">numKids</span></span>|<span data-ttu-id="bb666-117">Liczba elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="bb666-117">The number of children.</span></span> <span data-ttu-id="bb666-118">Typ: int</span><span class="sxs-lookup"><span data-stu-id="bb666-118">Type: int</span></span>|

<span data-ttu-id="bb666-119">Działanie `CreateFlowchartWithFaults` używa działania <xref:System.Activities.Statements.FlowSwitch%601>, które przełącza `promoCode` argument i oblicza rabat przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="bb666-119">The `CreateFlowchartWithFaults` activity uses a <xref:System.Activities.Statements.FlowSwitch%601> activity that switches on the `promoCode` argument and calculates the discount using the following formula.</span></span>

|<span data-ttu-id="bb666-120">Wartość `promoCode`</span><span class="sxs-lookup"><span data-stu-id="bb666-120">Value of `promoCode`</span></span>|<span data-ttu-id="bb666-121">Rabat (%)</span><span class="sxs-lookup"><span data-stu-id="bb666-121">Discount (%)</span></span>|
|--------------------------|--------------------|
|<span data-ttu-id="bb666-122">Single</span><span class="sxs-lookup"><span data-stu-id="bb666-122">Single</span></span>|<span data-ttu-id="bb666-123">10</span><span class="sxs-lookup"><span data-stu-id="bb666-123">10</span></span>|
|<span data-ttu-id="bb666-124">MNK</span><span class="sxs-lookup"><span data-stu-id="bb666-124">MNK</span></span>|<span data-ttu-id="bb666-125">15</span><span class="sxs-lookup"><span data-stu-id="bb666-125">15</span></span>|
|<span data-ttu-id="bb666-126">MWK</span><span class="sxs-lookup"><span data-stu-id="bb666-126">MWK</span></span>|<span data-ttu-id="bb666-127">15 + (1 – 1/`numberOfKids`)\*10 **Uwaga:** potencjalnie to obliczenie może zgłosić <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="bb666-127">15 + (1 – 1/`numberOfKids`)\*10 **Note:**  Potentially, this calculation can throw a <xref:System.DivideByZeroException>.</span></span> <span data-ttu-id="bb666-128">W związku z tym obliczanie rabatu jest opakowane w <xref:System.Activities.Statements.TryCatch> działanie, które przechwytuje wyjątek <xref:System.DivideByZeroException> i ustawia rabat na zero.</span><span class="sxs-lookup"><span data-stu-id="bb666-128">So, the discount calculation is wrapped in a <xref:System.Activities.Statements.TryCatch> activity that catches the <xref:System.DivideByZeroException> exception and sets the discount to zero.</span></span>|

#### <a name="to-use-this-sample"></a><span data-ttu-id="bb666-129">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="bb666-129">To use this sample</span></span>

1. <span data-ttu-id="bb666-130">Za pomocą programu Visual Studio 2010 Otwórz plik rozwiązania FlowchartWithFaultHandling. sln.</span><span class="sxs-lookup"><span data-stu-id="bb666-130">Using Visual Studio 2010, open the FlowchartWithFaultHandling.sln solution file.</span></span>

2. <span data-ttu-id="bb666-131">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="bb666-131">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="bb666-132">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="bb666-132">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bb666-133">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="bb666-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="bb666-134">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="bb666-134">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="bb666-135">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb666-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bb666-136">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="bb666-136">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`

## <a name="see-also"></a><span data-ttu-id="bb666-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb666-137">See also</span></span>

- [<span data-ttu-id="bb666-138">Przepływy pracy schematów blokowych</span><span class="sxs-lookup"><span data-stu-id="bb666-138">Flowchart Workflows</span></span>](../flowchart-workflows.md)
- [<span data-ttu-id="bb666-139">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="bb666-139">Exceptions</span></span>](../exceptions.md)
