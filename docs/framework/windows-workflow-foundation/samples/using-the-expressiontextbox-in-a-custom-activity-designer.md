---
title: Używanie elementu ExpressionTextBox w projektancie działań niestandardowych
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: bfac07d64cd5e30c3475d4e269c16597905ea829
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045357"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a><span data-ttu-id="e1635-102">Używanie elementu ExpressionTextBox w projektancie działań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="e1635-102">Using the ExpressionTextBox in a Custom Activity Designer</span></span>
<span data-ttu-id="e1635-103">Ten przykład pokazuje, <xref:System.Activities.Presentation.View.ExpressionTextBox> jak używać w niestandardowym projektancie działań.</span><span class="sxs-lookup"><span data-stu-id="e1635-103">This sample shows how to use the <xref:System.Activities.Presentation.View.ExpressionTextBox> in a custom activity designer.</span></span> <span data-ttu-id="e1635-104">Działanie niestandardowe, `MultiAssign`, przypisuje dwie wartości ciągu do dwóch zmiennych ciągu.</span><span class="sxs-lookup"><span data-stu-id="e1635-104">The custom activity, `MultiAssign`, assigns two string values to two string variables.</span></span> <span data-ttu-id="e1635-105">Niektóre <xref:System.Activities.Presentation.View.ExpressionTextBox> formanty są powiązane <xref:System.Activities.InArgument>z s i z pewnymi powiązaniami z <xref:System.Activities.OutArgument>.</span><span class="sxs-lookup"><span data-stu-id="e1635-105">Some <xref:System.Activities.Presentation.View.ExpressionTextBox> controls bind to <xref:System.Activities.InArgument>s and some bind to <xref:System.Activities.OutArgument>s.</span></span>

## <a name="sample-details"></a><span data-ttu-id="e1635-106">Przykładowe szczegóły</span><span class="sxs-lookup"><span data-stu-id="e1635-106">Sample details</span></span>
 <span data-ttu-id="e1635-107">`ArgumentToExpressionConverter` Jest konwerterem typów używanym podczas wiązania wyrażeń z argumentami.</span><span class="sxs-lookup"><span data-stu-id="e1635-107">The `ArgumentToExpressionConverter` is the type converter used when binding expressions to arguments.</span></span> <span data-ttu-id="e1635-108">Wartość musi być ustawiona na `In` lub `Out` odpowiednio. `ConverterParameter`</span><span class="sxs-lookup"><span data-stu-id="e1635-108">The `ConverterParameter` must be set to `In` or `Out` as appropriate.</span></span> <span data-ttu-id="e1635-109">`InOut`nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="e1635-109">`InOut` is not supported.</span></span>

 <span data-ttu-id="e1635-110">Ten `UseLocationExpression` atrybut jest używany w `OutArgument`s, aby określić, że wyrażenie powinno być wyrażeniem L-wartości ("lewa wartość" lub "wartość lokalizacji").</span><span class="sxs-lookup"><span data-stu-id="e1635-110">The `UseLocationExpression` attribute is used on `OutArgument`s to specify that the expression should be an L-value ("left value" or "location value") expression.</span></span> <span data-ttu-id="e1635-111">W większości przypadków wyrażenie L-wartości jest prawidłowym identyfikatorem Visual Basic używanym do wskazania, że `OutArgument` zwracana jest nazwa zmiennej lub argumentu.</span><span class="sxs-lookup"><span data-stu-id="e1635-111">In most cases, an L-value expression is a valid Visual Basic identifier used to indicate that the `OutArgument` being returned is a variable or argument name.</span></span>

 <span data-ttu-id="e1635-112">Atrybut jest ustawiony na jeden w tym przykładzie i `MinLines` nie jest ustawiony. `MaxLines`</span><span class="sxs-lookup"><span data-stu-id="e1635-112">The `MaxLines` attribute is set to one in this example and `MinLines` is not set.</span></span> <span data-ttu-id="e1635-113">Oznacza to, że <xref:System.Activities.Presentation.View.ExpressionTextBox> jest to stały rozmiar jednego wiersza niezależnie od ilości tekstu wpisanego przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e1635-113">This indicates that the <xref:System.Activities.Presentation.View.ExpressionTextBox> is a fixed size of one line regardless of the amount of text typed by the user.</span></span> <span data-ttu-id="e1635-114">Aby umożliwić <xref:System.Activities.Presentation.View.ExpressionTextBox> powiększanie się w celu dopasowania danych przez użytkownika, `MinLines`ustaw wartość `MaxLines` większą niż.</span><span class="sxs-lookup"><span data-stu-id="e1635-114">To allow the <xref:System.Activities.Presentation.View.ExpressionTextBox> to grow to fit user input, set `MaxLines` greater than `MinLines`.</span></span>

 <span data-ttu-id="e1635-115">Element ExpressionTextBox może być powiązany tylko z argumentami i nie można go powiązać z właściwościami środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="e1635-115">An ExpressionTextBox can only be bound to arguments, and cannot be bound to CLR properties.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="e1635-116">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="e1635-116">To use this sample</span></span>

1. <span data-ttu-id="e1635-117">Za pomocą programu Visual Studio 2010 Otwórz plik ExpressionTextBoxSample. sln.</span><span class="sxs-lookup"><span data-stu-id="e1635-117">Using Visual Studio 2010, open the ExpressionTextBoxSample.sln file.</span></span>

2. <span data-ttu-id="e1635-118">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="e1635-118">To build the solution, press CTRL+SHIFT+B.</span></span>

#### <a name="to-run-this-sample"></a><span data-ttu-id="e1635-119">Aby uruchomić ten przykład</span><span class="sxs-lookup"><span data-stu-id="e1635-119">To run this sample</span></span>

1. <span data-ttu-id="e1635-120">Dodaj nową aplikację konsoli przepływu pracy do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="e1635-120">Add a new Workflow Console Application to the solution.</span></span>

2. <span data-ttu-id="e1635-121">Dodaj odwołanie do projektu **ExpressionTextBoxSample** z nowego projektu aplikacji konsolowej przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e1635-121">Add a reference to the **ExpressionTextBoxSample** project from the new Workflow Console Application project.</span></span>

3. <span data-ttu-id="e1635-122">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="e1635-122">Build the solution.</span></span>

4. <span data-ttu-id="e1635-123">Przeciągnij działanie **wieloprzypisane** z przybornika i upuść je w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="e1635-123">Drag the **MultiAssign** activity from the toolbox and drop it into the workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1635-124">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e1635-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e1635-125">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="e1635-125">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="e1635-126">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="e1635-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e1635-127">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e1635-127">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a><span data-ttu-id="e1635-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1635-128">See also</span></span>

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [<span data-ttu-id="e1635-129">Tworzenie aplikacji przy użyciu Projektanta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e1635-129">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
