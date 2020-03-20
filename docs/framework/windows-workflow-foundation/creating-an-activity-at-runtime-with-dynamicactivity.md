---
title: Tworzenie działania w czasie wykonywania za pomocą dynamicactivity
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: 871108fd09e9127b3f9e06174f05a47c7fd7682c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182991"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="56b69-102">Tworzenie działania w czasie wykonywania za pomocą dynamicactivity</span><span class="sxs-lookup"><span data-stu-id="56b69-102">Creating an Activity at Runtime with DynamicActivity</span></span>
<span data-ttu-id="56b69-103"><xref:System.Activities.DynamicActivity>jest betonową, uszczelnioną klasą z konstruktorem publicznym.</span><span class="sxs-lookup"><span data-stu-id="56b69-103"><xref:System.Activities.DynamicActivity> is a concrete, sealed class with a public constructor.</span></span> <span data-ttu-id="56b69-104"><xref:System.Activities.DynamicActivity>może służyć do montażu funkcji działania w czasie wykonywania przy użyciu działania DOM.</span><span class="sxs-lookup"><span data-stu-id="56b69-104"><xref:System.Activities.DynamicActivity> can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="56b69-105">Funkcje DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="56b69-105">DynamicActivity Features</span></span>  
 <span data-ttu-id="56b69-106"><xref:System.Activities.DynamicActivity>ma dostęp do właściwości wykonywania, argumentów i zmiennych, ale nie ma dostępu do usług w czasie wykonywania, takich jak planowanie działań podrzędnych lub śledzenia.</span><span class="sxs-lookup"><span data-stu-id="56b69-106"><xref:System.Activities.DynamicActivity> has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="56b69-107">Właściwości najwyższego poziomu można ustawić <xref:System.Activities.Argument> za pomocą obiektów przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="56b69-107">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="56b69-108">W kodzie imperatywnym te argumenty są tworzone przy użyciu właściwości CLR na nowy typ.</span><span class="sxs-lookup"><span data-stu-id="56b69-108">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="56b69-109">W języku XAML są `x:Class` `x:Member` one zadeklarowane przy użyciu i tagi.</span><span class="sxs-lookup"><span data-stu-id="56b69-109">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="56b69-110">Działania skonstruowane <xref:System.Activities.DynamicActivity> przy użyciu interfejsu <xref:System.ComponentModel.ICustomTypeDescriptor>z projektantem przy użyciu .</span><span class="sxs-lookup"><span data-stu-id="56b69-110">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="56b69-111">Działania utworzone w projektancie można ładować dynamicznie przy użyciu <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, jak pokazano w poniższej procedurze.</span><span class="sxs-lookup"><span data-stu-id="56b69-111">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="56b69-112">Aby utworzyć działanie w czasie wykonywania przy użyciu kodu imperatywu</span><span class="sxs-lookup"><span data-stu-id="56b69-112">To create an activity at runtime using imperative code</span></span>  
  
1. <span data-ttu-id="56b69-113">OpenVisual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="56b69-113">OpenVisual Studio 2010.</span></span>  
  
2. <span data-ttu-id="56b69-114">Wybierz **pozycję Plik**, **Nowy**, **Projekt**.</span><span class="sxs-lookup"><span data-stu-id="56b69-114">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="56b69-115">Wybierz **przepływ pracy 4.0** w obszarze **Visual C#** w oknie **Typy projektu** i wybierz węzeł w wersji **2010.**</span><span class="sxs-lookup"><span data-stu-id="56b69-115">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="56b69-116">Wybierz **kolejną aplikację konsoli przepływu pracy** w oknie **Szablony.**</span><span class="sxs-lookup"><span data-stu-id="56b69-116">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="56b69-117">Nazwij nowy projekt DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="56b69-117">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="56b69-118">Kliknij prawym przyciskiem myszy pozycję Przepływ pracy1.xaml w projekcie HelloActivity i wybierz polecenie **Usuń**.</span><span class="sxs-lookup"><span data-stu-id="56b69-118">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4. <span data-ttu-id="56b69-119">Otwórz Program.cs.</span><span class="sxs-lookup"><span data-stu-id="56b69-119">Open Program.cs.</span></span> <span data-ttu-id="56b69-120">Dodaj następującą dyrektywę do górnej części pliku.</span><span class="sxs-lookup"><span data-stu-id="56b69-120">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
5. <span data-ttu-id="56b69-121">Zastąp `Main` zawartość metody następującym kodem, który <xref:System.Activities.Statements.Sequence> tworzy <xref:System.Activities.Statements.WriteLine> działanie, które zawiera <xref:System.Activities.DynamicActivity.Implementation%2A> pojedyncze działanie i przypisuje je do właściwości nowego działania dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="56b69-121">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
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
  
6. <span data-ttu-id="56b69-122">Wykonaj aplikację.</span><span class="sxs-lookup"><span data-stu-id="56b69-122">Execute the application.</span></span> <span data-ttu-id="56b69-123">Okno konsoli z tekstem "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="56b69-123">A console window with the text "Hello World!"</span></span> <span data-ttu-id="56b69-124">Wyświetla.</span><span class="sxs-lookup"><span data-stu-id="56b69-124">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="56b69-125">Aby utworzyć działanie w czasie wykonywania przy użyciu języka XAML</span><span class="sxs-lookup"><span data-stu-id="56b69-125">To create an activity at runtime using XAML</span></span>  
  
1. <span data-ttu-id="56b69-126">Otwórz program Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="56b69-126">Open Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="56b69-127">Wybierz **pozycję Plik**, **Nowy**, **Projekt**.</span><span class="sxs-lookup"><span data-stu-id="56b69-127">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="56b69-128">Wybierz **przepływ pracy 4.0** w obszarze **Visual C#** w oknie **Typy projektu** i wybierz węzeł w wersji **2010.**</span><span class="sxs-lookup"><span data-stu-id="56b69-128">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="56b69-129">Wybierz pozycję **Aplikacja konsoli przepływu pracy** w oknie **Szablony.**</span><span class="sxs-lookup"><span data-stu-id="56b69-129">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="56b69-130">Nazwij nowy projekt DynamicActivitySample.</span><span class="sxs-lookup"><span data-stu-id="56b69-130">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="56b69-131">Otwórz plik Workflow1.xaml w projekcie HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="56b69-131">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="56b69-132">Kliknij opcję **Argumenty** u dołu projektanta.</span><span class="sxs-lookup"><span data-stu-id="56b69-132">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="56b69-133">Utwórz `In` nowy `TextToWrite` argument `String`o nazwie typu .</span><span class="sxs-lookup"><span data-stu-id="56b69-133">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4. <span data-ttu-id="56b69-134">Przeciągnij działanie **WriteLine** z sekcji **Podstawowe przybornika** na powierzchnię projektanta.</span><span class="sxs-lookup"><span data-stu-id="56b69-134">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="56b69-135">Przypisz `TextToWrite` wartość do **właściwości Text** działania.</span><span class="sxs-lookup"><span data-stu-id="56b69-135">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5. <span data-ttu-id="56b69-136">Otwórz Program.cs.</span><span class="sxs-lookup"><span data-stu-id="56b69-136">Open Program.cs.</span></span> <span data-ttu-id="56b69-137">Dodaj następującą dyrektywę do górnej części pliku.</span><span class="sxs-lookup"><span data-stu-id="56b69-137">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Activities.XamlIntegration;  
    ```  
  
6. <span data-ttu-id="56b69-138">Zastąp zawartość metody `Main` następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="56b69-138">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```csharp  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. <span data-ttu-id="56b69-139">Wykonaj aplikację.</span><span class="sxs-lookup"><span data-stu-id="56b69-139">Execute the application.</span></span> <span data-ttu-id="56b69-140">Okno konsoli z tekstem "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="56b69-140">A console window with the text "Hello World!"</span></span> <span data-ttu-id="56b69-141">Pojawia się.</span><span class="sxs-lookup"><span data-stu-id="56b69-141">appears.</span></span>  
  
8. <span data-ttu-id="56b69-142">Kliknij prawym przyciskiem myszy plik Workflow1.xaml w **Eksploratorze rozwiązań** i wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="56b69-142">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="56b69-143">Należy zauważyć, że klasa `x:Class` działania jest tworzona z i właściwość jest tworzona z `x:Property`.</span><span class="sxs-lookup"><span data-stu-id="56b69-143">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56b69-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56b69-144">See also</span></span>

- [<span data-ttu-id="56b69-145">Tworzenie przepływów pracy, działań i wyrażeń przy użyciu kodu imperatywnego</span><span class="sxs-lookup"><span data-stu-id="56b69-145">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](authoring-workflows-activities-and-expressions-using-imperative-code.md)
