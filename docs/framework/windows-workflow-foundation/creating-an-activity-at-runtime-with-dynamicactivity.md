---
title: Tworzenie działania w czasie wykonywania za pomocą działania DynamicActivity
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: 17dda5643f86690c25067e70680a6b797dd172d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733210"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="27c4e-102">Tworzenie działania w czasie wykonywania za pomocą działania DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="27c4e-102">Creating an Activity at Runtime with DynamicActivity</span></span>
<span data-ttu-id="27c4e-103"><xref:System.Activities.DynamicActivity> jest klasą konkretną, sealed przy użyciu publicznego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="27c4e-103"><xref:System.Activities.DynamicActivity> is a concrete, sealed class with a public constructor.</span></span> <span data-ttu-id="27c4e-104"><xref:System.Activities.DynamicActivity> może służyć do włączenia funkcji działania w czasie wykonywania za pomocą działania modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="27c4e-104"><xref:System.Activities.DynamicActivity> can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="27c4e-105">Funkcje DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="27c4e-105">DynamicActivity Features</span></span>  
 <span data-ttu-id="27c4e-106"><xref:System.Activities.DynamicActivity> ma dostęp do właściwości wykonywania, argumentów i zmiennych, ale nie dostęp do usług czasu wykonywania, takich jak planowanie działania podrzędne lub śledzenia.</span><span class="sxs-lookup"><span data-stu-id="27c4e-106"><xref:System.Activities.DynamicActivity> has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="27c4e-107">Można ustawić właściwości najwyższego poziomu za pomocą przepływu pracy <xref:System.Activities.Argument> obiektów.</span><span class="sxs-lookup"><span data-stu-id="27c4e-107">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="27c4e-108">Kodu imperatywnego tych argumentów tworzonych za pomocą właściwości CLR dla nowego typu.</span><span class="sxs-lookup"><span data-stu-id="27c4e-108">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="27c4e-109">W XAML, są deklarowane za pomocą `x:Class` i `x:Member` tagów.</span><span class="sxs-lookup"><span data-stu-id="27c4e-109">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="27c4e-110">Tworzony przy użyciu działań <xref:System.Activities.DynamicActivity> interfejs za pomocą projektanta przy użyciu <xref:System.ComponentModel.ICustomTypeDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="27c4e-110">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="27c4e-111">Działania utworzone w Projektancie można załadować dynamicznie przy użyciu <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, jak pokazano w poniższej procedurze.</span><span class="sxs-lookup"><span data-stu-id="27c4e-111">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="27c4e-112">Aby utworzyć działanie w czasie wykonywania przy użyciu kodu imperatywnego</span><span class="sxs-lookup"><span data-stu-id="27c4e-112">To create an activity at runtime using imperative code</span></span>  
  
1.  <span data-ttu-id="27c4e-113">OpenVisual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="27c4e-113">OpenVisual Studio 2010.</span></span>  
  
2.  <span data-ttu-id="27c4e-114">Wybierz **pliku**, **nowe**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="27c4e-114">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="27c4e-115">Wybierz **Workflow 4.0** w obszarze **Visual C#** w **typów projektów** okna, a następnie wybierz **v2010** węzła.</span><span class="sxs-lookup"><span data-stu-id="27c4e-115">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="27c4e-116">Wybierz **sekwencyjne Aplikacja konsoli przepływu pracy** w **szablony** okna.</span><span class="sxs-lookup"><span data-stu-id="27c4e-116">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="27c4e-117">Nazwa nowego projektu DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="27c4e-117">Name the new project DynamicActivitySample.</span></span>  
  
3.  <span data-ttu-id="27c4e-118">Kliknij prawym przyciskiem myszy Workflow1.xaml w projekcie HelloActivity, a następnie wybierz pozycję **Usuń**.</span><span class="sxs-lookup"><span data-stu-id="27c4e-118">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="27c4e-119">Otwórz plik Program.cs.</span><span class="sxs-lookup"><span data-stu-id="27c4e-119">Open Program.cs.</span></span> <span data-ttu-id="27c4e-120">Dodaj następującą dyrektywę na początku pliku.</span><span class="sxs-lookup"><span data-stu-id="27c4e-120">Add the following directive to the top of the file.</span></span>  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
5.  <span data-ttu-id="27c4e-121">Zastąp zawartość `Main` metoda poniższym kodem, który tworzy <xref:System.Activities.Statements.Sequence> działania, który zawiera jeden <xref:System.Activities.Statements.WriteLine> działania i przypisuje go do <xref:System.Activities.DynamicActivity.Implementation%2A> właściwość nowe działanie dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="27c4e-121">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
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
  
6.  <span data-ttu-id="27c4e-122">Wykonania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="27c4e-122">Execute the application.</span></span> <span data-ttu-id="27c4e-123">Okno konsoli z tekstu "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="27c4e-123">A console window with the text "Hello World!"</span></span> <span data-ttu-id="27c4e-124">Wyświetla.</span><span class="sxs-lookup"><span data-stu-id="27c4e-124">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="27c4e-125">Aby utworzyć działanie w czasie wykonywania przy użyciu XAML</span><span class="sxs-lookup"><span data-stu-id="27c4e-125">To create an activity at runtime using XAML</span></span>  
  
1.  <span data-ttu-id="27c4e-126">Open Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="27c4e-126">Open Visual Studio 2010.</span></span>  
  
2.  <span data-ttu-id="27c4e-127">Wybierz **pliku**, **nowe**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="27c4e-127">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="27c4e-128">Wybierz **Workflow 4.0** w obszarze **Visual C#** w **typów projektów** okna, a następnie wybierz **v2010** węzła.</span><span class="sxs-lookup"><span data-stu-id="27c4e-128">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="27c4e-129">Wybierz **Aplikacja konsoli przepływu pracy** w **szablony** okna.</span><span class="sxs-lookup"><span data-stu-id="27c4e-129">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="27c4e-130">Nazwa nowego projektu DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="27c4e-130">Name the new project DynamicActivitySample.</span></span>  
  
3.  <span data-ttu-id="27c4e-131">Otwórz Workflow1.xaml w projekcie HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="27c4e-131">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="27c4e-132">Kliknij przycisk **argumenty** opcję w dolnej części projektanta.</span><span class="sxs-lookup"><span data-stu-id="27c4e-132">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="27c4e-133">Utwórz nową `In` argument o nazwie `TextToWrite` typu `String`.</span><span class="sxs-lookup"><span data-stu-id="27c4e-133">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4.  <span data-ttu-id="27c4e-134">Przeciągnij **WriteLine** działanie z **podstawowych** sekcji przybornika na powierzchni projektowej.</span><span class="sxs-lookup"><span data-stu-id="27c4e-134">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="27c4e-135">Przypisz wartość `TextToWrite` do **tekstu** właściwości działania.</span><span class="sxs-lookup"><span data-stu-id="27c4e-135">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5.  <span data-ttu-id="27c4e-136">Otwórz plik Program.cs.</span><span class="sxs-lookup"><span data-stu-id="27c4e-136">Open Program.cs.</span></span> <span data-ttu-id="27c4e-137">Dodaj następującą dyrektywę na początku pliku.</span><span class="sxs-lookup"><span data-stu-id="27c4e-137">Add the following directive to the top of the file.</span></span>  
  
    ```  
    using System.Activities.XamlIntegration;  
    ```  
  
6.  <span data-ttu-id="27c4e-138">Zastąp zawartość `Main` metoda następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="27c4e-138">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7.  <span data-ttu-id="27c4e-139">Wykonania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="27c4e-139">Execute the application.</span></span> <span data-ttu-id="27c4e-140">Okno konsoli z tekstu "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="27c4e-140">A console window with the text "Hello World!"</span></span> <span data-ttu-id="27c4e-141">zostanie wyświetlone.</span><span class="sxs-lookup"><span data-stu-id="27c4e-141">appears.</span></span>  
  
8.  <span data-ttu-id="27c4e-142">Kliknij prawym przyciskiem myszy plik Workflow1.xaml **Eksploratora rozwiązań** i wybierz **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="27c4e-142">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="27c4e-143">Należy zauważyć, że klasa działania jest tworzona z `x:Class` , a właściwość jest tworzony przy użyciu `x:Property`.</span><span class="sxs-lookup"><span data-stu-id="27c4e-143">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27c4e-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27c4e-144">See also</span></span>

- [<span data-ttu-id="27c4e-145">Tworzenie przepływów pracy, działań i wyrażeń przy użyciu kodu imperatywnego</span><span class="sxs-lookup"><span data-stu-id="27c4e-145">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)
