---
title: Obsługa błędów w działaniu schematu blokowego przy użyciu działania TryCatch
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: 42eb660aff01c7e29227c28a6ad0d47d4370eb91
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016018"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a><span data-ttu-id="79a62-102">Obsługa błędów w działaniu schematu blokowego przy użyciu działania TryCatch</span><span class="sxs-lookup"><span data-stu-id="79a62-102">Fault Handling in a Flowchart Activity Using TryCatch</span></span>

<span data-ttu-id="79a62-103">Ten przykład pokazuje, <xref:System.Activities.Statements.TryCatch> jak działanie może być używane w ramach działania przepływu sterowania złożonego.</span><span class="sxs-lookup"><span data-stu-id="79a62-103">This sample shows how the <xref:System.Activities.Statements.TryCatch> activity can be used within a complex control flow activity.</span></span>

<span data-ttu-id="79a62-104">W tym przykładzie kod promocyjny i liczba elementów podrzędnych są przesyłane jako zmienne do <xref:System.Activities.Statements.Flowchart> działania, które oblicza rabat na podstawie formuły odpowiadającej kodowi promocji.</span><span class="sxs-lookup"><span data-stu-id="79a62-104">In this sample, a promotion code and number of children are passed as variables to a <xref:System.Activities.Statements.Flowchart> activity that calculates a discount based on formulae that correspond to the promotion code.</span></span> <span data-ttu-id="79a62-105">Przykład obejmuje bezwzględny kod i wersje projektanta przepływu pracy dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="79a62-105">The sample includes imperative code and workflow designer versions of the sample.</span></span>

<span data-ttu-id="79a62-106">W poniższej tabeli przedstawiono zmienne dla `CreateFlowchartWithFaults` działania.</span><span class="sxs-lookup"><span data-stu-id="79a62-106">The following table details the variables for the `CreateFlowchartWithFaults` activity.</span></span>

|<span data-ttu-id="79a62-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="79a62-107">Parameters</span></span>|<span data-ttu-id="79a62-108">Opis</span><span class="sxs-lookup"><span data-stu-id="79a62-108">Description</span></span>|
|----------------|-----------------|
|<span data-ttu-id="79a62-109">promoCode</span><span class="sxs-lookup"><span data-stu-id="79a62-109">promoCode</span></span>|<span data-ttu-id="79a62-110">Kod promocyjny.</span><span class="sxs-lookup"><span data-stu-id="79a62-110">The promotion code.</span></span> <span data-ttu-id="79a62-111">Wpisz: String</span><span class="sxs-lookup"><span data-stu-id="79a62-111">Type: String</span></span><br /><br /> <span data-ttu-id="79a62-112">Możliwe wartości z opisem w nawiasach:</span><span class="sxs-lookup"><span data-stu-id="79a62-112">The possible values with description in parentheses:</span></span><br /><br /> <span data-ttu-id="79a62-113">-Pojedyncza (pojedyncza)</span><span class="sxs-lookup"><span data-stu-id="79a62-113">-   Single (Single)</span></span><br /><span data-ttu-id="79a62-114">-MNK (ślub bez dzieci)</span><span class="sxs-lookup"><span data-stu-id="79a62-114">-   MNK (Married with no kids.)</span></span><br /><span data-ttu-id="79a62-115">-MWK (ślub z dziecięcymi).</span><span class="sxs-lookup"><span data-stu-id="79a62-115">-   MWK (Married with kids.)</span></span>|
|<span data-ttu-id="79a62-116">numKids</span><span class="sxs-lookup"><span data-stu-id="79a62-116">numKids</span></span>|<span data-ttu-id="79a62-117">Liczba elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="79a62-117">The number of children.</span></span> <span data-ttu-id="79a62-118">Typ: int</span><span class="sxs-lookup"><span data-stu-id="79a62-118">Type: int</span></span>|

<span data-ttu-id="79a62-119">`CreateFlowchartWithFaults` Działanie używa`promoCode` działania, które przełącza argument i oblicza rabat przy użyciu następującej formuły. <xref:System.Activities.Statements.FlowSwitch%601></span><span class="sxs-lookup"><span data-stu-id="79a62-119">The `CreateFlowchartWithFaults` activity uses a <xref:System.Activities.Statements.FlowSwitch%601> activity that switches on the `promoCode` argument and calculates the discount using the following formula.</span></span>

|<span data-ttu-id="79a62-120">Wartość`promoCode`</span><span class="sxs-lookup"><span data-stu-id="79a62-120">Value of `promoCode`</span></span>|<span data-ttu-id="79a62-121">Rabat (%)</span><span class="sxs-lookup"><span data-stu-id="79a62-121">Discount (%)</span></span>|
|--------------------------|--------------------|
|<span data-ttu-id="79a62-122">Single</span><span class="sxs-lookup"><span data-stu-id="79a62-122">Single</span></span>|<span data-ttu-id="79a62-123">10</span><span class="sxs-lookup"><span data-stu-id="79a62-123">10</span></span>|
|<span data-ttu-id="79a62-124">MNK</span><span class="sxs-lookup"><span data-stu-id="79a62-124">MNK</span></span>|<span data-ttu-id="79a62-125">15</span><span class="sxs-lookup"><span data-stu-id="79a62-125">15</span></span>|
|<span data-ttu-id="79a62-126">MWK</span><span class="sxs-lookup"><span data-stu-id="79a62-126">MWK</span></span>|<span data-ttu-id="79a62-127">15 + (1 – 1/`numberOfKids`)\*10 **Uwaga:**  Może to spowodować wygenerowanie <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="79a62-127">15 + (1 – 1/`numberOfKids`)\*10 **Note:**  Potentially, this calculation can throw a <xref:System.DivideByZeroException>.</span></span> <span data-ttu-id="79a62-128">W związku z tym obliczanie rabatu jest opakowane w <xref:System.Activities.Statements.TryCatch> działanie, które przechwytuje <xref:System.DivideByZeroException> wyjątek i ustawia rabat na zero.</span><span class="sxs-lookup"><span data-stu-id="79a62-128">So, the discount calculation is wrapped in a <xref:System.Activities.Statements.TryCatch> activity that catches the <xref:System.DivideByZeroException> exception and sets the discount to zero.</span></span>|

#### <a name="to-use-this-sample"></a><span data-ttu-id="79a62-129">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="79a62-129">To use this sample</span></span>

1. <span data-ttu-id="79a62-130">Za pomocą programu Visual Studio 2010 Otwórz plik rozwiązania FlowchartWithFaultHandling. sln.</span><span class="sxs-lookup"><span data-stu-id="79a62-130">Using Visual Studio 2010, open the FlowchartWithFaultHandling.sln solution file.</span></span>

2. <span data-ttu-id="79a62-131">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="79a62-131">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="79a62-132">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="79a62-132">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="79a62-133">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="79a62-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="79a62-134">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="79a62-134">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="79a62-135">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="79a62-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="79a62-136">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="79a62-136">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`

## <a name="see-also"></a><span data-ttu-id="79a62-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="79a62-137">See also</span></span>

- [<span data-ttu-id="79a62-138">Przepływy pracy schematów blokowych</span><span class="sxs-lookup"><span data-stu-id="79a62-138">Flowchart Workflows</span></span>](../flowchart-workflows.md)
- [<span data-ttu-id="79a62-139">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="79a62-139">Exceptions</span></span>](../exceptions.md)
