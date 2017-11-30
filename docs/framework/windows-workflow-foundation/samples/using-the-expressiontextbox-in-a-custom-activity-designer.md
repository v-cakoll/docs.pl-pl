---
title: "Przy użyciu ExpressionTextBox w Projektancie działań niestandardowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 41a5d5645f66f69fd267b75359d0c74952b7b4bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a><span data-ttu-id="a121e-102">Przy użyciu ExpressionTextBox w Projektancie działań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="a121e-102">Using the ExpressionTextBox in a Custom Activity Designer</span></span>
<span data-ttu-id="a121e-103">Ten przykład przedstawia sposób użycia <xref:System.Activities.Presentation.View.ExpressionTextBox> w Projektancie działania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="a121e-103">This sample shows how to use the <xref:System.Activities.Presentation.View.ExpressionTextBox> in a custom activity designer.</span></span> <span data-ttu-id="a121e-104">To niestandardowe działanie `MultiAssign`, przypisuje dwóch wartości ciągu do dwóch zmiennych ciągu.</span><span class="sxs-lookup"><span data-stu-id="a121e-104">The custom activity, `MultiAssign`, assigns two string values to two string variables.</span></span> <span data-ttu-id="a121e-105">Niektóre <xref:System.Activities.Presentation.View.ExpressionTextBox> powiązania kontrolki <xref:System.Activities.InArgument>s, a niektóre powiązać <xref:System.Activities.OutArgument>s.</span><span class="sxs-lookup"><span data-stu-id="a121e-105">Some <xref:System.Activities.Presentation.View.ExpressionTextBox> controls bind to <xref:System.Activities.InArgument>s and some bind to <xref:System.Activities.OutArgument>s.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="a121e-106">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="a121e-106">Sample details</span></span>  
 <span data-ttu-id="a121e-107">`ArgumentToExpressionConverter` Jest używany podczas tworzenia wiązania wyrażenia argumentów konwerter typów.</span><span class="sxs-lookup"><span data-stu-id="a121e-107">The `ArgumentToExpressionConverter` is the type converter used when binding expressions to arguments.</span></span> <span data-ttu-id="a121e-108">`ConverterParameter` Musi mieć ustawioną `In` lub `Out` odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="a121e-108">The `ConverterParameter` must be set to `In` or `Out` as appropriate.</span></span> <span data-ttu-id="a121e-109">`InOut`nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="a121e-109">`InOut` is not supported.</span></span>  
  
 <span data-ttu-id="a121e-110">`UseLocationExpression` Atrybut jest stosowany na `OutArgument`s, aby określić, czy wyrażenie powinno być wyrażeniem L-wartość ("po lewej stronie" lub "lokalizacji wartości").</span><span class="sxs-lookup"><span data-stu-id="a121e-110">The `UseLocationExpression` attribute is used on `OutArgument`s to specify that the expression should be an L-value ("left value" or "location value") expression.</span></span> <span data-ttu-id="a121e-111">W większości przypadków wyrażenia wartości L jest prawidłowym identyfikatorem języka Visual Basic, używany w celu wskazania, że `OutArgument` zwracana jest nazwa zmiennej lub argumentu.</span><span class="sxs-lookup"><span data-stu-id="a121e-111">In most cases, an L-value expression is a valid Visual Basic identifier used to indicate that the `OutArgument` being returned is a variable or argument name.</span></span>  
  
 <span data-ttu-id="a121e-112">`MaxLines` Atrybut ma ustawioną w tym przykładzie i `MinLines` nie jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="a121e-112">The `MaxLines` attribute is set to one in this example and `MinLines` is not set.</span></span> <span data-ttu-id="a121e-113">Oznacza to, że <xref:System.Activities.Presentation.View.ExpressionTextBox> ma stały rozmiar jednej linii, niezależnie od ilości tekstu przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a121e-113">This indicates that the <xref:System.Activities.Presentation.View.ExpressionTextBox> is a fixed size of one line regardless of the amount of text typed by the user.</span></span> <span data-ttu-id="a121e-114">Aby umożliwić <xref:System.Activities.Presentation.View.ExpressionTextBox> aby dopasowany do wprowadzenia danych przez użytkownika, należy ustawić `MaxLines` większa niż `MinLines`.</span><span class="sxs-lookup"><span data-stu-id="a121e-114">To allow the <xref:System.Activities.Presentation.View.ExpressionTextBox> to grow to fit user input, set `MaxLines` greater than `MinLines`.</span></span>  
  
 <span data-ttu-id="a121e-115">ExpressionTextBox może być powiązana tylko z argumentów i nie można powiązać właściwości CLR.</span><span class="sxs-lookup"><span data-stu-id="a121e-115">An ExpressionTextBox can only be bound to arguments, and cannot be bound to CLR properties.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a121e-116">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="a121e-116">To use this sample</span></span>  
  
1.  <span data-ttu-id="a121e-117">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik ExpressionTextBoxSample.sln.</span><span class="sxs-lookup"><span data-stu-id="a121e-117">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ExpressionTextBoxSample.sln file.</span></span>  
  
2.  <span data-ttu-id="a121e-118">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="a121e-118">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="a121e-119">Aby uruchomić ten przykład</span><span class="sxs-lookup"><span data-stu-id="a121e-119">To run this sample</span></span>  
  
1.  <span data-ttu-id="a121e-120">Dodaj nową aplikację konsoli przepływu pracy do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="a121e-120">Add a new Workflow Console Application to the solution.</span></span>  
  
2.  <span data-ttu-id="a121e-121">Dodaj odwołanie do **ExpressionTextBoxSample** projektu z nowego projektu aplikacji Konsolowej przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a121e-121">Add a reference to the **ExpressionTextBoxSample** project from the new Workflow Console Application project.</span></span>  
  
3.  <span data-ttu-id="a121e-122">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="a121e-122">Build the solution.</span></span>  
  
4.  <span data-ttu-id="a121e-123">Przeciągnij **MultiAssign** działania z przybornika i upuść ją do przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a121e-123">Drag the **MultiAssign** activity from the toolbox and drop it into the workflow.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a121e-124">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="a121e-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a121e-125">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="a121e-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a121e-126">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="a121e-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a121e-127">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a121e-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a><span data-ttu-id="a121e-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a121e-128">See Also</span></span>  
 <xref:System.Activities.Presentation.View.ExpressionTextBox>  
 [<span data-ttu-id="a121e-129">Tworzenie aplikacji za pomocą projektanta przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="a121e-129">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
