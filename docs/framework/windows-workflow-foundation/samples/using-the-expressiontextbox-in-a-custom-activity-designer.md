---
title: Używanie elementu ExpressionTextBox w projektancie działań niestandardowych
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: 6d3df9e18c7239f0e4695509d80edfd02e9a9d6f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182768"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a><span data-ttu-id="87905-102">Używanie elementu ExpressionTextBox w projektancie działań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="87905-102">Using the ExpressionTextBox in a Custom Activity Designer</span></span>
<span data-ttu-id="87905-103">W tym przykładzie <xref:System.Activities.Presentation.View.ExpressionTextBox> pokazano, jak używać w projektancie działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="87905-103">This sample shows how to use the <xref:System.Activities.Presentation.View.ExpressionTextBox> in a custom activity designer.</span></span> <span data-ttu-id="87905-104">Działanie niestandardowe `MultiAssign`, przypisuje dwie wartości ciągu do dwóch zmiennych ciągu.</span><span class="sxs-lookup"><span data-stu-id="87905-104">The custom activity, `MultiAssign`, assigns two string values to two string variables.</span></span> <span data-ttu-id="87905-105">Niektóre <xref:System.Activities.Presentation.View.ExpressionTextBox> formanty wiążą się z <xref:System.Activities.InArgument>s, a niektóre wiążą się z <xref:System.Activities.OutArgument>s.</span><span class="sxs-lookup"><span data-stu-id="87905-105">Some <xref:System.Activities.Presentation.View.ExpressionTextBox> controls bind to <xref:System.Activities.InArgument>s and some bind to <xref:System.Activities.OutArgument>s.</span></span>

## <a name="sample-details"></a><span data-ttu-id="87905-106">Przykładowe szczegóły</span><span class="sxs-lookup"><span data-stu-id="87905-106">Sample details</span></span>
 <span data-ttu-id="87905-107">Jest `ArgumentToExpressionConverter` konwerterem typu używanym podczas wiązania wyrażeń z argumentami.</span><span class="sxs-lookup"><span data-stu-id="87905-107">The `ArgumentToExpressionConverter` is the type converter used when binding expressions to arguments.</span></span> <span data-ttu-id="87905-108">Musi `ConverterParameter` być `In` ustawiona `Out` lub w stosownych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="87905-108">The `ConverterParameter` must be set to `In` or `Out` as appropriate.</span></span> <span data-ttu-id="87905-109">`InOut`nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="87905-109">`InOut` is not supported.</span></span>

 <span data-ttu-id="87905-110">Atrybut `UseLocationExpression` jest używany `OutArgument`na s, aby określić, że wyrażenie powinno być wyrażeniem wartości L ("wartość lewa" lub "wartość lokalizacji").</span><span class="sxs-lookup"><span data-stu-id="87905-110">The `UseLocationExpression` attribute is used on `OutArgument`s to specify that the expression should be an L-value ("left value" or "location value") expression.</span></span> <span data-ttu-id="87905-111">W większości przypadków wyrażenie wartości L jest prawidłowym identyfikatorem języka `OutArgument` Visual Basic używanym do wskazania, że zwracana jest nazwa zmiennej lub argumentu.</span><span class="sxs-lookup"><span data-stu-id="87905-111">In most cases, an L-value expression is a valid Visual Basic identifier used to indicate that the `OutArgument` being returned is a variable or argument name.</span></span>

 <span data-ttu-id="87905-112">Atrybut `MaxLines` jest ustawiony na jeden w `MinLines` tym przykładzie i nie jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="87905-112">The `MaxLines` attribute is set to one in this example and `MinLines` is not set.</span></span> <span data-ttu-id="87905-113">Oznacza to, <xref:System.Activities.Presentation.View.ExpressionTextBox> że jest to stały rozmiar jednego wiersza, niezależnie od ilości tekstu wpisanego przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="87905-113">This indicates that the <xref:System.Activities.Presentation.View.ExpressionTextBox> is a fixed size of one line regardless of the amount of text typed by the user.</span></span> <span data-ttu-id="87905-114">Aby umożliwić <xref:System.Activities.Presentation.View.ExpressionTextBox> wzrost, aby dopasować `MaxLines` dane `MinLines`wejściowe użytkownika, ustaw więcej niż .</span><span class="sxs-lookup"><span data-stu-id="87905-114">To allow the <xref:System.Activities.Presentation.View.ExpressionTextBox> to grow to fit user input, set `MaxLines` greater than `MinLines`.</span></span>

 <span data-ttu-id="87905-115">ExpressionTextBox może być powiązany tylko z argumentami i nie może być powiązany z właściwościami CLR.</span><span class="sxs-lookup"><span data-stu-id="87905-115">An ExpressionTextBox can only be bound to arguments, and cannot be bound to CLR properties.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="87905-116">Aby użyć tej próbki</span><span class="sxs-lookup"><span data-stu-id="87905-116">To use this sample</span></span>

1. <span data-ttu-id="87905-117">Za pomocą programu Visual Studio 2010 otwórz plik ExpressionTextBoxSample.sln.</span><span class="sxs-lookup"><span data-stu-id="87905-117">Using Visual Studio 2010, open the ExpressionTextBoxSample.sln file.</span></span>

2. <span data-ttu-id="87905-118">Aby utworzyć rozwiązanie, naciśnij klawisze CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="87905-118">To build the solution, press CTRL+SHIFT+B.</span></span>

#### <a name="to-run-this-sample"></a><span data-ttu-id="87905-119">Aby uruchomić ten przykład</span><span class="sxs-lookup"><span data-stu-id="87905-119">To run this sample</span></span>

1. <span data-ttu-id="87905-120">Dodaj nową aplikację konsoli przepływu pracy do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="87905-120">Add a new Workflow Console Application to the solution.</span></span>

2. <span data-ttu-id="87905-121">Dodaj odwołanie do projektu **ExpressionTextBoxSample** z nowego projektu aplikacji konsoli przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="87905-121">Add a reference to the **ExpressionTextBoxSample** project from the new Workflow Console Application project.</span></span>

3. <span data-ttu-id="87905-122">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="87905-122">Build the solution.</span></span>

4. <span data-ttu-id="87905-123">Przeciągnij działanie **MultiAssign** z przybornika i upuść je do przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="87905-123">Drag the **MultiAssign** activity from the toolbox and drop it into the workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="87905-124">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="87905-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="87905-125">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="87905-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="87905-126">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="87905-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="87905-127">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="87905-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a><span data-ttu-id="87905-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87905-128">See also</span></span>

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [<span data-ttu-id="87905-129">Tworzenie aplikacji przy użyciu Projektanta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="87905-129">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
