---
title: Tworzenie działania w czasie wykonywania z dynamiczną
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: de67fdd71f28bc0f4b16017d253682ca2615f854
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989740"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="f1c5a-102">Tworzenie działania w czasie wykonywania z dynamiczną</span><span class="sxs-lookup"><span data-stu-id="f1c5a-102">Creating an Activity at Runtime with DynamicActivity</span></span>
<span data-ttu-id="f1c5a-103"><xref:System.Activities.DynamicActivity>jest konkretną klasą zapieczętowana z konstruktorem publicznym.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-103"><xref:System.Activities.DynamicActivity> is a concrete, sealed class with a public constructor.</span></span> <span data-ttu-id="f1c5a-104"><xref:System.Activities.DynamicActivity>może służyć do łączenia funkcji działania w środowisku uruchomieniowym przy użyciu modelu DOM działania.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-104"><xref:System.Activities.DynamicActivity> can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="f1c5a-105">Funkcje dynamiczne</span><span class="sxs-lookup"><span data-stu-id="f1c5a-105">DynamicActivity Features</span></span>  
 <span data-ttu-id="f1c5a-106"><xref:System.Activities.DynamicActivity>ma dostęp do właściwości wykonywania, argumentów i zmiennych, ale nie ma dostępu do usług czasu wykonywania, takich jak planowanie działań podrzędnych lub śledzenie.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-106"><xref:System.Activities.DynamicActivity> has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="f1c5a-107">Właściwości najwyższego poziomu można ustawić za pomocą <xref:System.Activities.Argument> obiektów przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-107">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="f1c5a-108">W kodzie bezwzględnym te argumenty są tworzone przy użyciu właściwości CLR dla nowego typu.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-108">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="f1c5a-109">W języku XAML są one deklarowane `x:Class` przy `x:Member` użyciu tagów i.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-109">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="f1c5a-110">Działania skonstruowane przy <xref:System.Activities.DynamicActivity> użyciu interfejsu z projektantem <xref:System.ComponentModel.ICustomTypeDescriptor>przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-110">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="f1c5a-111">Działania utworzone w projektancie mogą być ładowane dynamicznie przy użyciu <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, jak pokazano w poniższej procedurze.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-111">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="f1c5a-112">Aby utworzyć działanie w czasie wykonywania przy użyciu kodu bezwzględnego</span><span class="sxs-lookup"><span data-stu-id="f1c5a-112">To create an activity at runtime using imperative code</span></span>  
  
1. <span data-ttu-id="f1c5a-113">OpenVisual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-113">OpenVisual Studio 2010.</span></span>  
  
2. <span data-ttu-id="f1c5a-114">Wybierz **plik**, **Nowy**, **projekt**.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-114">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="f1c5a-115">Wybierz pozycję **Workflow 4,0** w obszarze **Wizualizacja C#**  w oknie **typy projektów** , a następnie wybierz węzeł **V2010** .</span><span class="sxs-lookup"><span data-stu-id="f1c5a-115">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="f1c5a-116">W oknie **Szablony** wybierz **kolejno pozycje sekwencyjna aplikacja konsoli przepływu pracy** .</span><span class="sxs-lookup"><span data-stu-id="f1c5a-116">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="f1c5a-117">Nazwij nowy projekt DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-117">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="f1c5a-118">Kliknij prawym przyciskiem myszy pozycję Workflow1. XAML w projekcie Hello i wybierz polecenie **Usuń**.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-118">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4. <span data-ttu-id="f1c5a-119">Otwórz Program.cs.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-119">Open Program.cs.</span></span> <span data-ttu-id="f1c5a-120">Dodaj następującą dyrektywę na początku pliku.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-120">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
5. <span data-ttu-id="f1c5a-121">Zamień zawartość `Main` metody na następujący kod, który <xref:System.Activities.Statements.Sequence> tworzy działanie zawierające pojedyncze <xref:System.Activities.Statements.WriteLine> działanie i przypisuje je do <xref:System.Activities.DynamicActivity.Implementation%2A> właściwości nowego działania dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-121">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
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
  
6. <span data-ttu-id="f1c5a-122">Wykonaj aplikację.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-122">Execute the application.</span></span> <span data-ttu-id="f1c5a-123">Okno konsoli z tekstem "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="f1c5a-123">A console window with the text "Hello World!"</span></span> <span data-ttu-id="f1c5a-124">listę.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-124">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="f1c5a-125">Aby utworzyć działanie w środowisku uruchomieniowym przy użyciu języka XAML</span><span class="sxs-lookup"><span data-stu-id="f1c5a-125">To create an activity at runtime using XAML</span></span>  
  
1. <span data-ttu-id="f1c5a-126">Open Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-126">Open Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="f1c5a-127">Wybierz **plik**, **Nowy**, **projekt**.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-127">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="f1c5a-128">Wybierz pozycję **Workflow 4,0** w obszarze **Wizualizacja C#**  w oknie **typy projektów** , a następnie wybierz węzeł **V2010** .</span><span class="sxs-lookup"><span data-stu-id="f1c5a-128">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="f1c5a-129">W oknie **Szablony** wybierz pozycję **aplikacja konsoli przepływu pracy** .</span><span class="sxs-lookup"><span data-stu-id="f1c5a-129">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="f1c5a-130">Nazwij nowy projekt DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-130">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="f1c5a-131">Otwórz Workflow1. XAML w projekcie Hello.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-131">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="f1c5a-132">Kliknij opcję **argumenty** u dołu okna projektanta.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-132">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="f1c5a-133">Utwórz nowy `In` argument o nazwie `TextToWrite` typu. `String`</span><span class="sxs-lookup"><span data-stu-id="f1c5a-133">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4. <span data-ttu-id="f1c5a-134">Przeciągnij działanie **WriteLine** z sekcji elementy **pierwotne** przybornika na powierzchnię projektanta.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-134">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="f1c5a-135">Przypisz wartość `TextToWrite` do właściwości **Text** działania.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-135">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5. <span data-ttu-id="f1c5a-136">Otwórz Program.cs.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-136">Open Program.cs.</span></span> <span data-ttu-id="f1c5a-137">Dodaj następującą dyrektywę na początku pliku.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-137">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Activities.XamlIntegration;  
    ```  
  
6. <span data-ttu-id="f1c5a-138">Zamień zawartość `Main` metody na następujący kod.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-138">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```csharp  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. <span data-ttu-id="f1c5a-139">Wykonaj aplikację.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-139">Execute the application.</span></span> <span data-ttu-id="f1c5a-140">Okno konsoli z tekstem "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="f1c5a-140">A console window with the text "Hello World!"</span></span> <span data-ttu-id="f1c5a-141">się.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-141">appears.</span></span>  
  
8. <span data-ttu-id="f1c5a-142">Kliknij prawym przyciskiem myszy plik Workflow1. XAML w **Eksplorator rozwiązań** i wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-142">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="f1c5a-143">Należy zauważyć, że Klasa Activity jest tworzona `x:Class` z i właściwość jest tworzona przy `x:Property`użyciu.</span><span class="sxs-lookup"><span data-stu-id="f1c5a-143">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1c5a-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1c5a-144">See also</span></span>

- [<span data-ttu-id="f1c5a-145">Tworzenie przepływów pracy, działań i wyrażeń przy użyciu kodu imperatywnego</span><span class="sxs-lookup"><span data-stu-id="f1c5a-145">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](authoring-workflows-activities-and-expressions-using-imperative-code.md)
