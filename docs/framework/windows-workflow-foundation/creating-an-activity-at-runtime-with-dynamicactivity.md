---
title: Tworzenie działania w czasie wykonywania z dynamiczną
description: Dynamiczna jest klasą zapieczętowana z konstruktorem publicznym. Użyj klasy, aby złożyć funkcję działania w czasie wykonywania przy użyciu modelu DOM działania.
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: 17ee14be7df4801018c7afd2e91f1fb07c34e8e1
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421543"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="bd41d-104">Tworzenie działania w czasie wykonywania z dynamiczną</span><span class="sxs-lookup"><span data-stu-id="bd41d-104">Creating an Activity at Runtime with DynamicActivity</span></span>
<span data-ttu-id="bd41d-105"><xref:System.Activities.DynamicActivity>jest konkretną klasą zapieczętowana z konstruktorem publicznym.</span><span class="sxs-lookup"><span data-stu-id="bd41d-105"><xref:System.Activities.DynamicActivity> is a concrete, sealed class with a public constructor.</span></span> <span data-ttu-id="bd41d-106"><xref:System.Activities.DynamicActivity>może służyć do łączenia funkcji działania w środowisku uruchomieniowym przy użyciu modelu DOM działania.</span><span class="sxs-lookup"><span data-stu-id="bd41d-106"><xref:System.Activities.DynamicActivity> can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="bd41d-107">Funkcje dynamiczne</span><span class="sxs-lookup"><span data-stu-id="bd41d-107">DynamicActivity Features</span></span>  
 <span data-ttu-id="bd41d-108"><xref:System.Activities.DynamicActivity>ma dostęp do właściwości wykonywania, argumentów i zmiennych, ale nie ma dostępu do usług czasu wykonywania, takich jak planowanie działań podrzędnych lub śledzenie.</span><span class="sxs-lookup"><span data-stu-id="bd41d-108"><xref:System.Activities.DynamicActivity> has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="bd41d-109">Właściwości najwyższego poziomu można ustawić za pomocą <xref:System.Activities.Argument> obiektów przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bd41d-109">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="bd41d-110">W kodzie bezwzględnym te argumenty są tworzone przy użyciu właściwości CLR dla nowego typu.</span><span class="sxs-lookup"><span data-stu-id="bd41d-110">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="bd41d-111">W języku XAML są one deklarowane przy użyciu `x:Class` `x:Member` tagów i.</span><span class="sxs-lookup"><span data-stu-id="bd41d-111">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="bd41d-112">Działania skonstruowane przy użyciu <xref:System.Activities.DynamicActivity> interfejsu z projektantem przy użyciu <xref:System.ComponentModel.ICustomTypeDescriptor> .</span><span class="sxs-lookup"><span data-stu-id="bd41d-112">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="bd41d-113">Działania utworzone w projektancie mogą być ładowane dynamicznie przy użyciu <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> , jak pokazano w poniższej procedurze.</span><span class="sxs-lookup"><span data-stu-id="bd41d-113">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="bd41d-114">Aby utworzyć działanie w czasie wykonywania przy użyciu kodu bezwzględnego</span><span class="sxs-lookup"><span data-stu-id="bd41d-114">To create an activity at runtime using imperative code</span></span>  
  
1. <span data-ttu-id="bd41d-115">Otwórz Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="bd41d-115">OpenVisual Studio 2010.</span></span>  
  
2. <span data-ttu-id="bd41d-116">Wybierz **plik**, **Nowy**, **projekt**.</span><span class="sxs-lookup"><span data-stu-id="bd41d-116">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="bd41d-117">Wybierz pozycję **Workflow 4,0** w obszarze **Visual C#** w oknie **typy projektów** , a następnie wybierz węzeł **V2010** .</span><span class="sxs-lookup"><span data-stu-id="bd41d-117">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="bd41d-118">W oknie **Szablony** wybierz **kolejno pozycje sekwencyjna aplikacja konsoli przepływu pracy** .</span><span class="sxs-lookup"><span data-stu-id="bd41d-118">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="bd41d-119">Nazwij nowy projekt DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="bd41d-119">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="bd41d-120">Kliknij prawym przyciskiem myszy pozycję Workflow1. XAML w projekcie Hello i wybierz polecenie **Usuń**.</span><span class="sxs-lookup"><span data-stu-id="bd41d-120">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4. <span data-ttu-id="bd41d-121">Otwórz Program.cs.</span><span class="sxs-lookup"><span data-stu-id="bd41d-121">Open Program.cs.</span></span> <span data-ttu-id="bd41d-122">Dodaj następującą dyrektywę na początku pliku.</span><span class="sxs-lookup"><span data-stu-id="bd41d-122">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
5. <span data-ttu-id="bd41d-123">Zamień zawartość `Main` metody na następujący kod, który tworzy <xref:System.Activities.Statements.Sequence> działanie zawierające pojedyncze <xref:System.Activities.Statements.WriteLine> działanie i przypisuje je do <xref:System.Activities.DynamicActivity.Implementation%2A> właściwości nowego działania dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="bd41d-123">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
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
  
6. <span data-ttu-id="bd41d-124">Wykonaj aplikację.</span><span class="sxs-lookup"><span data-stu-id="bd41d-124">Execute the application.</span></span> <span data-ttu-id="bd41d-125">Okno konsoli z tekstem "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="bd41d-125">A console window with the text "Hello World!"</span></span> <span data-ttu-id="bd41d-126">listę.</span><span class="sxs-lookup"><span data-stu-id="bd41d-126">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="bd41d-127">Aby utworzyć działanie w środowisku uruchomieniowym przy użyciu języka XAML</span><span class="sxs-lookup"><span data-stu-id="bd41d-127">To create an activity at runtime using XAML</span></span>  
  
1. <span data-ttu-id="bd41d-128">Otwórz program Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="bd41d-128">Open Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="bd41d-129">Wybierz **plik**, **Nowy**, **projekt**.</span><span class="sxs-lookup"><span data-stu-id="bd41d-129">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="bd41d-130">Wybierz pozycję **Workflow 4,0** w obszarze **Visual C#** w oknie **typy projektów** , a następnie wybierz węzeł **V2010** .</span><span class="sxs-lookup"><span data-stu-id="bd41d-130">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="bd41d-131">W oknie **Szablony** wybierz pozycję **aplikacja konsoli przepływu pracy** .</span><span class="sxs-lookup"><span data-stu-id="bd41d-131">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="bd41d-132">Nazwij nowy projekt DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="bd41d-132">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="bd41d-133">Otwórz Workflow1. XAML w projekcie Hello.</span><span class="sxs-lookup"><span data-stu-id="bd41d-133">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="bd41d-134">Kliknij opcję **argumenty** u dołu okna projektanta.</span><span class="sxs-lookup"><span data-stu-id="bd41d-134">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="bd41d-135">Utwórz nowy `In` argument o nazwie `TextToWrite` typu `String` .</span><span class="sxs-lookup"><span data-stu-id="bd41d-135">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4. <span data-ttu-id="bd41d-136">Przeciągnij działanie **WriteLine** z sekcji elementy **pierwotne** przybornika na powierzchnię projektanta.</span><span class="sxs-lookup"><span data-stu-id="bd41d-136">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="bd41d-137">Przypisz wartość `TextToWrite` do właściwości **Text** działania.</span><span class="sxs-lookup"><span data-stu-id="bd41d-137">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5. <span data-ttu-id="bd41d-138">Otwórz Program.cs.</span><span class="sxs-lookup"><span data-stu-id="bd41d-138">Open Program.cs.</span></span> <span data-ttu-id="bd41d-139">Dodaj następującą dyrektywę na początku pliku.</span><span class="sxs-lookup"><span data-stu-id="bd41d-139">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Activities.XamlIntegration;  
    ```  
  
6. <span data-ttu-id="bd41d-140">Zastąp zawartość metody `Main` następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="bd41d-140">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```csharp  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. <span data-ttu-id="bd41d-141">Wykonaj aplikację.</span><span class="sxs-lookup"><span data-stu-id="bd41d-141">Execute the application.</span></span> <span data-ttu-id="bd41d-142">Okno konsoli z tekstem "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="bd41d-142">A console window with the text "Hello World!"</span></span> <span data-ttu-id="bd41d-143">się.</span><span class="sxs-lookup"><span data-stu-id="bd41d-143">appears.</span></span>  
  
8. <span data-ttu-id="bd41d-144">Kliknij prawym przyciskiem myszy plik Workflow1. XAML w **Eksplorator rozwiązań** i wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="bd41d-144">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="bd41d-145">Należy zauważyć, że Klasa Activity jest tworzona z `x:Class` i właściwość jest tworzona przy użyciu `x:Property` .</span><span class="sxs-lookup"><span data-stu-id="bd41d-145">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd41d-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd41d-146">See also</span></span>

- [<span data-ttu-id="bd41d-147">Tworzenie przepływów pracy, działań i wyrażeń przy użyciu kodu imperatywnego</span><span class="sxs-lookup"><span data-stu-id="bd41d-147">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](authoring-workflows-activities-and-expressions-using-imperative-code.md)
