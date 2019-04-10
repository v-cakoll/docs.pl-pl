---
title: Używanie elementu ExpressionTextBox w projektancie działań niestandardowych
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: c85254f1ae7ba8a269568cf1a14acf367b595e33
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344978"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a><span data-ttu-id="adc82-102">Używanie elementu ExpressionTextBox w projektancie działań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="adc82-102">Using the ExpressionTextBox in a Custom Activity Designer</span></span>
<span data-ttu-id="adc82-103">Ten przykład ilustruje sposób używania <xref:System.Activities.Presentation.View.ExpressionTextBox> w Projektancie działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="adc82-103">This sample shows how to use the <xref:System.Activities.Presentation.View.ExpressionTextBox> in a custom activity designer.</span></span> <span data-ttu-id="adc82-104">Niestandardowe działanie `MultiAssign`, przypisuje dwóch wartości ciągu do dwóch zmiennych ciągu.</span><span class="sxs-lookup"><span data-stu-id="adc82-104">The custom activity, `MultiAssign`, assigns two string values to two string variables.</span></span> <span data-ttu-id="adc82-105">Niektóre <xref:System.Activities.Presentation.View.ExpressionTextBox> powiązać formanty <xref:System.Activities.InArgument>s, a niektóre powiązać <xref:System.Activities.OutArgument>s.</span><span class="sxs-lookup"><span data-stu-id="adc82-105">Some <xref:System.Activities.Presentation.View.ExpressionTextBox> controls bind to <xref:System.Activities.InArgument>s and some bind to <xref:System.Activities.OutArgument>s.</span></span>

## <a name="sample-details"></a><span data-ttu-id="adc82-106">Przykład szczegółów</span><span class="sxs-lookup"><span data-stu-id="adc82-106">Sample details</span></span>
 <span data-ttu-id="adc82-107">`ArgumentToExpressionConverter` Jest konwertera typów używane podczas tworzenia powiązania wyrażeń do argumentów.</span><span class="sxs-lookup"><span data-stu-id="adc82-107">The `ArgumentToExpressionConverter` is the type converter used when binding expressions to arguments.</span></span> <span data-ttu-id="adc82-108">`ConverterParameter` Musi być równa `In` lub `Out` odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="adc82-108">The `ConverterParameter` must be set to `In` or `Out` as appropriate.</span></span> `InOut` <span data-ttu-id="adc82-109">nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="adc82-109">is not supported.</span></span>

 <span data-ttu-id="adc82-110">`UseLocationExpression` Atrybut jest używany na `OutArgument`s, aby określić, że wyrażenie powinny być wyrażenie L-wartość ("po lewej stronie wartość" lub "lokalizacji wartość").</span><span class="sxs-lookup"><span data-stu-id="adc82-110">The `UseLocationExpression` attribute is used on `OutArgument`s to specify that the expression should be an L-value ("left value" or "location value") expression.</span></span> <span data-ttu-id="adc82-111">W większości przypadków wyrażenie L-wartością jest prawidłowym identyfikatorem języka Visual Basic, używany do wskazania, że `OutArgument` zwracana jest nazwa zmiennej lub argumentu.</span><span class="sxs-lookup"><span data-stu-id="adc82-111">In most cases, an L-value expression is a valid Visual Basic identifier used to indicate that the `OutArgument` being returned is a variable or argument name.</span></span>

 <span data-ttu-id="adc82-112">`MaxLines` Ma ustawioną wartość atrybutu w tym przykładzie i `MinLines` nie jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="adc82-112">The `MaxLines` attribute is set to one in this example and `MinLines` is not set.</span></span> <span data-ttu-id="adc82-113">Oznacza to, że <xref:System.Activities.Presentation.View.ExpressionTextBox> ma stały rozmiar jeden wiersz, niezależnie od ilości tekst wpisany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="adc82-113">This indicates that the <xref:System.Activities.Presentation.View.ExpressionTextBox> is a fixed size of one line regardless of the amount of text typed by the user.</span></span> <span data-ttu-id="adc82-114">Aby umożliwić <xref:System.Activities.Presentation.View.ExpressionTextBox> się zwiększać w celu dopasowania danych wejściowych użytkownika, ustaw `MaxLines` większa `MinLines`.</span><span class="sxs-lookup"><span data-stu-id="adc82-114">To allow the <xref:System.Activities.Presentation.View.ExpressionTextBox> to grow to fit user input, set `MaxLines` greater than `MinLines`.</span></span>

 <span data-ttu-id="adc82-115">Elementu ExpressionTextBox może być powiązana tylko z argumentów i nie można powiązać z właściwości aparatu CLR.</span><span class="sxs-lookup"><span data-stu-id="adc82-115">An ExpressionTextBox can only be bound to arguments, and cannot be bound to CLR properties.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="adc82-116">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="adc82-116">To use this sample</span></span>

1. <span data-ttu-id="adc82-117">Za pomocą programu Visual Studio 2010, otwórz plik ExpressionTextBoxSample.sln.</span><span class="sxs-lookup"><span data-stu-id="adc82-117">Using Visual Studio 2010, open the ExpressionTextBoxSample.sln file.</span></span>

2. <span data-ttu-id="adc82-118">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="adc82-118">To build the solution, press CTRL+SHIFT+B.</span></span>

#### <a name="to-run-this-sample"></a><span data-ttu-id="adc82-119">Aby uruchomić ten przykład</span><span class="sxs-lookup"><span data-stu-id="adc82-119">To run this sample</span></span>

1. <span data-ttu-id="adc82-120">Dodaj nową aplikację konsoli przepływu pracy do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="adc82-120">Add a new Workflow Console Application to the solution.</span></span>

2. <span data-ttu-id="adc82-121">Dodaj odwołanie do **ExpressionTextBoxSample** projektu z nowy projekt aplikacji konsoli przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="adc82-121">Add a reference to the **ExpressionTextBoxSample** project from the new Workflow Console Application project.</span></span>

3. <span data-ttu-id="adc82-122">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="adc82-122">Build the solution.</span></span>

4. <span data-ttu-id="adc82-123">Przeciągnij **MultiAssign** działania z przybornika i upuść go w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="adc82-123">Drag the **MultiAssign** activity from the toolbox and drop it into the workflow.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="adc82-124">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="adc82-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="adc82-125">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="adc82-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="adc82-126">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="adc82-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="adc82-127">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="adc82-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a><span data-ttu-id="adc82-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="adc82-128">See also</span></span>

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [<span data-ttu-id="adc82-129">Tworzenie aplikacji za pomocą projektanta przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="adc82-129">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
