---
title: "Tworzenie w czasie wykonywania z DynamicActivity działania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ebbd6e77c2c47754054a81f4b07d3d845cdcac00
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="786cc-102">Tworzenie w czasie wykonywania z DynamicActivity działania</span><span class="sxs-lookup"><span data-stu-id="786cc-102">Creating an Activity at Runtime with DynamicActivity</span></span>
<span data-ttu-id="786cc-103"><xref:System.Activities.DynamicActivity>jest klasą konkretną, sealed z publicznym konstruktorem.</span><span class="sxs-lookup"><span data-stu-id="786cc-103"><xref:System.Activities.DynamicActivity> is a concrete, sealed class with a public constructor.</span></span> <span data-ttu-id="786cc-104"><xref:System.Activities.DynamicActivity>można użyć do włączenia funkcji działania w czasie wykonywania za pomocą działania modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="786cc-104"><xref:System.Activities.DynamicActivity> can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="786cc-105">Funkcje DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="786cc-105">DynamicActivity Features</span></span>  
 <span data-ttu-id="786cc-106"><xref:System.Activities.DynamicActivity>ma dostęp do właściwości wykonania, argumentów i zmienne, ale brak dostępu do usługi czasu wykonywania, takie jak planowania działań podrzędnych lub śledzenia.</span><span class="sxs-lookup"><span data-stu-id="786cc-106"><xref:System.Activities.DynamicActivity> has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="786cc-107">Można ustawić właściwości najwyższego poziomu za pomocą przepływu pracy <xref:System.Activities.Argument> obiektów.</span><span class="sxs-lookup"><span data-stu-id="786cc-107">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="786cc-108">W kodzie imperatywnych tych argumentów są tworzone przy użyciu właściwości CLR dla nowego typu.</span><span class="sxs-lookup"><span data-stu-id="786cc-108">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="786cc-109">W języku XAML, są one uznane za pomocą `x:Class` i `x:Member` tagów.</span><span class="sxs-lookup"><span data-stu-id="786cc-109">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="786cc-110">Działania utworzone za pomocą <xref:System.Activities.DynamicActivity> interfejsu przy użyciu projektanta <xref:System.ComponentModel.ICustomTypeDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="786cc-110">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="786cc-111">Działania utworzone w Projektancie mogą być ładowane dynamicznie za pomocą <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, jak to pokazano w poniższej procedurze.</span><span class="sxs-lookup"><span data-stu-id="786cc-111">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="786cc-112">Aby utworzyć działanie w czasie wykonywania za pomocą kodu imperatywne</span><span class="sxs-lookup"><span data-stu-id="786cc-112">To create an activity at runtime using imperative code</span></span>  
  
1.  <span data-ttu-id="786cc-113">Otwórz[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="786cc-113">Open[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="786cc-114">Wybierz **pliku**, **nowe**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="786cc-114">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="786cc-115">Wybierz **Workflow 4.0** w obszarze **Visual C#** w **typów projektów** okna, a następnie wybierz **v2010** węzła.</span><span class="sxs-lookup"><span data-stu-id="786cc-115">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="786cc-116">Wybierz **sekwencyjnych Aplikacja konsoli przepływu pracy** w **szablony** okna.</span><span class="sxs-lookup"><span data-stu-id="786cc-116">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="786cc-117">Nazwa nowego projektu DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="786cc-117">Name the new project DynamicActivitySample.</span></span>  
  
3.  <span data-ttu-id="786cc-118">Kliknij prawym przyciskiem myszy Workflow1.xaml w projekcie HelloActivity i wybierz **usunąć**.</span><span class="sxs-lookup"><span data-stu-id="786cc-118">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="786cc-119">Otwórz plik Program.cs.</span><span class="sxs-lookup"><span data-stu-id="786cc-119">Open Program.cs.</span></span> <span data-ttu-id="786cc-120">Dodaj następujące dyrektywy do początku pliku.</span><span class="sxs-lookup"><span data-stu-id="786cc-120">Add the following directive to the top of the file.</span></span>  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
5.  <span data-ttu-id="786cc-121">Zastąp zawartość `Main` metodę z następującym kodem, który tworzy <xref:System.Activities.Statements.Sequence> działania, która zawiera jedną <xref:System.Activities.Statements.WriteLine> działania i przypisuje go do <xref:System.Activities.DynamicActivity.Implementation%2A> właściwości dynamicznych nowe działanie.</span><span class="sxs-lookup"><span data-stu-id="786cc-121">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
    ```csharp  
    //Define the input argument for the activity  
    var textOut = new InArgument<string>();  
    //Create the activity, property, and implementation  
                Activity dynamicWorkflow = new DynamicActivity()  
                {  
                    Properties =   
                    {  
                        new DynamicActivityProperty  
                        {  
                            Name = "Text",  
                            Type = typeof(InArgument<String>),  
                            Value = textOut  
                        }  
                    },  
                    Implementation = () => new Sequence()  
                    {  
                        Activities =   
                        {  
                            new WriteLine()  
                            {  
                                Text = new InArgument<string>(env => textOut.Get(env))  
                            }  
                        }  
                    }  
                };  
    //Execute the activity with a parameter dictionary  
                WorkflowInvoker.Invoke(dynamicWorkflow, new Dictionary<string, object> { { "Text", "Hello World!" } });  
                Console.ReadLine();  
    ```  
  
6.  <span data-ttu-id="786cc-122">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="786cc-122">Execute the application.</span></span> <span data-ttu-id="786cc-123">Okno konsoli na tekst "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="786cc-123">A console window with the text "Hello World!"</span></span> <span data-ttu-id="786cc-124">Wyświetla.</span><span class="sxs-lookup"><span data-stu-id="786cc-124">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="786cc-125">Aby utworzyć działanie w środowisku uruchomieniowym przy użyciu kodu XAML</span><span class="sxs-lookup"><span data-stu-id="786cc-125">To create an activity at runtime using XAML</span></span>  
  
1.  <span data-ttu-id="786cc-126">Otwórz [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="786cc-126">Open [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="786cc-127">Wybierz **pliku**, **nowe**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="786cc-127">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="786cc-128">Wybierz **Workflow 4.0** w obszarze **Visual C#** w **typów projektów** okna, a następnie wybierz **v2010** węzła.</span><span class="sxs-lookup"><span data-stu-id="786cc-128">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="786cc-129">Wybierz **Aplikacja konsoli przepływu pracy** w **szablony** okna.</span><span class="sxs-lookup"><span data-stu-id="786cc-129">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="786cc-130">Nazwa nowego projektu DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="786cc-130">Name the new project DynamicActivitySample.</span></span>  
  
3.  <span data-ttu-id="786cc-131">Otwórz Workflow1.xaml w projekcie HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="786cc-131">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="786cc-132">Kliknij przycisk **argumenty** opcji w dolnej części projektanta.</span><span class="sxs-lookup"><span data-stu-id="786cc-132">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="786cc-133">Utwórz nową `In` argument o nazwie `TextToWrite` typu `String`.</span><span class="sxs-lookup"><span data-stu-id="786cc-133">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4.  <span data-ttu-id="786cc-134">Przeciągnij **WriteLine** działania z **podstawowych** sekcji przybornika na powierzchnię projektanta.</span><span class="sxs-lookup"><span data-stu-id="786cc-134">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="786cc-135">Przypisuje wartość `TextToWrite` do **tekst** właściwości działania.</span><span class="sxs-lookup"><span data-stu-id="786cc-135">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5.  <span data-ttu-id="786cc-136">Otwórz plik Program.cs.</span><span class="sxs-lookup"><span data-stu-id="786cc-136">Open Program.cs.</span></span> <span data-ttu-id="786cc-137">Dodaj następujące dyrektywy do początku pliku.</span><span class="sxs-lookup"><span data-stu-id="786cc-137">Add the following directive to the top of the file.</span></span>  
  
    ```  
    using System.Activities.XamlIntegration;  
    ```  
  
6.  <span data-ttu-id="786cc-138">Zastąp zawartość `Main` metodę z następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="786cc-138">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7.  <span data-ttu-id="786cc-139">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="786cc-139">Execute the application.</span></span> <span data-ttu-id="786cc-140">Okno konsoli na tekst "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="786cc-140">A console window with the text "Hello World!"</span></span> <span data-ttu-id="786cc-141">zostanie wyświetlone.</span><span class="sxs-lookup"><span data-stu-id="786cc-141">appears.</span></span>  
  
8.  <span data-ttu-id="786cc-142">Kliknij prawym przyciskiem myszy plik Workflow1.xaml **Eksploratora rozwiązań** i wybierz **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="786cc-142">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="786cc-143">Należy pamiętać, że klasa działania jest tworzona z `x:Class` i właściwość zostanie utworzona z `x:Property`.</span><span class="sxs-lookup"><span data-stu-id="786cc-143">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="786cc-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="786cc-144">See Also</span></span>  
 [<span data-ttu-id="786cc-145">Tworzenie przepływów pracy, działań i wyrażeń przy użyciu kodu imperatywnego</span><span class="sxs-lookup"><span data-stu-id="786cc-145">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)  
 [<span data-ttu-id="786cc-146">Tworzenie działania DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="786cc-146">DynamicActivity Creation</span></span>](../../../docs/framework/windows-workflow-foundation/samples/dynamicactivity-creation.md)
