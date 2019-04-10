---
title: Tworzenie działań przepływu pracy przy użyciu klasy CodeActivity
ms.date: 03/30/2017
ms.assetid: cfe315c1-f86d-43ec-b9ce-2f8c469b1106
ms.openlocfilehash: 549acec8b8101312d48bd20e63a4a988b798ff38
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331289"
---
# <a name="workflow-activity-authoring-using-the-codeactivity-class"></a><span data-ttu-id="a9de5-102">Tworzenie działań przepływu pracy przy użyciu klasy CodeActivity</span><span class="sxs-lookup"><span data-stu-id="a9de5-102">Workflow Activity Authoring Using the CodeActivity Class</span></span>
<span data-ttu-id="a9de5-103">Działania utworzone przez dziedziczenie z <xref:System.Activities.CodeActivity> można zaimplementować podstawowe zachowanie imperatywne przez zastąpienie <xref:System.Activities.CodeActivity.Execute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a9de5-103">Activities created by inheriting from <xref:System.Activities.CodeActivity> can implement basic imperative behavior by overriding the <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>

## <a name="using-codeactivitycontext"></a><span data-ttu-id="a9de5-104">Za pomocą CodeActivityContext</span><span class="sxs-lookup"><span data-stu-id="a9de5-104">Using CodeActivityContext</span></span>
 <span data-ttu-id="a9de5-105">Funkcje środowiska wykonawczego przepływów pracy są dostępne z poziomu <xref:System.Activities.CodeActivity.Execute%2A> metody za pomocą elementów członkowskich `context` parametr typu <xref:System.Activities.CodeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="a9de5-105">Features of the workflow runtime can be accessed from within the <xref:System.Activities.CodeActivity.Execute%2A> method by using members of the `context` parameter, of type <xref:System.Activities.CodeActivityContext>.</span></span> <span data-ttu-id="a9de5-106">Funkcje dostępne za pośrednictwem <xref:System.Activities.CodeActivityContext> obejmują następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="a9de5-106">The features available through <xref:System.Activities.CodeActivityContext> include the following:</span></span>

-   <span data-ttu-id="a9de5-107">Pobieranie i ustawianie wartości zmiennych i argumentów.</span><span class="sxs-lookup"><span data-stu-id="a9de5-107">Getting and setting the values of variables and arguments.</span></span>

-   <span data-ttu-id="a9de5-108">Niestandardowe śledzenia funkcji przy użyciu <xref:System.Activities.CodeActivityContext.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="a9de5-108">Custom tracking features using <xref:System.Activities.CodeActivityContext.Track%2A>.</span></span>

-   <span data-ttu-id="a9de5-109">Dostęp do właściwości wykonania działania przy użyciu <xref:System.Activities.CodeActivityContext.GetProperty%2A>.</span><span class="sxs-lookup"><span data-stu-id="a9de5-109">Access to the activity’s execution properties using <xref:System.Activities.CodeActivityContext.GetProperty%2A>.</span></span>

#### <a name="to-create-a-custom-activity-that-inherits-from-codeactivity"></a><span data-ttu-id="a9de5-110">Aby utworzyć niestandardowe działanie, która dziedziczy z elementu CodeActivity</span><span class="sxs-lookup"><span data-stu-id="a9de5-110">To create a custom activity that inherits from CodeActivity</span></span>

1. <span data-ttu-id="a9de5-111">Open Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="a9de5-111">Open Visual Studio 2010.</span></span>

2. <span data-ttu-id="a9de5-112">Wybierz **pliku**, **nowe**, a następnie **projektu**.</span><span class="sxs-lookup"><span data-stu-id="a9de5-112">Select **File**, **New**, and then **Project**.</span></span> <span data-ttu-id="a9de5-113">Wybierz **Workflow 4.0** w obszarze **Visual C#** w **typów projektów** okna, a następnie wybierz **v2010** węzła.</span><span class="sxs-lookup"><span data-stu-id="a9de5-113">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="a9de5-114">Wybierz **Biblioteka działań** w **szablony** okna.</span><span class="sxs-lookup"><span data-stu-id="a9de5-114">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="a9de5-115">Nazwa nowego projektu HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="a9de5-115">Name the new project HelloActivity.</span></span>

3. <span data-ttu-id="a9de5-116">Kliknij prawym przyciskiem myszy Activity1.xaml w projekcie HelloActivity, a następnie wybierz pozycję **Usuń**.</span><span class="sxs-lookup"><span data-stu-id="a9de5-116">Right-click Activity1.xaml in the HelloActivity project and select **Delete**.</span></span>

4. <span data-ttu-id="a9de5-117">Kliknij prawym przyciskiem myszy projekt HelloActivity, a następnie wybierz pozycję **Dodaj** , a następnie **klasy**.</span><span class="sxs-lookup"><span data-stu-id="a9de5-117">Right-click the HelloActivity project and select **Add** , and then **Class**.</span></span> <span data-ttu-id="a9de5-118">Nazwa nowej klasy HelloActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="a9de5-118">Name the new class HelloActivity.cs.</span></span>

5. <span data-ttu-id="a9de5-119">W pliku HelloActivity.cs, Dodaj następujący kod `using` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="a9de5-119">In the HelloActivity.cs file, add the following `using` directives.</span></span>

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. <span data-ttu-id="a9de5-120">Wprowadź nowy dziedziczyć z klasy <xref:System.Activities.CodeActivity> przez dodanie klasy bazowej do deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="a9de5-120">Make the new class inherit from <xref:System.Activities.CodeActivity> by adding a base class to the class declaration.</span></span>

    ```csharp
    class HelloActivity : CodeActivity
    ```

7. <span data-ttu-id="a9de5-121">Dodawanie funkcji do klasy, dodając <xref:System.Activities.CodeActivity.Execute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a9de5-121">Add functionality to the class by adding an <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. <span data-ttu-id="a9de5-122">Użyj <xref:System.Activities.CodeActivityContext> do tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a9de5-122">Use the <xref:System.Activities.CodeActivityContext> to create a tracking record.</span></span>

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
        CustomTrackingRecord record = new CustomTrackingRecord("MyRecord");
        record.Data.Add(new KeyValuePair<String, Object>("ExecutionTime", DateTime.Now));
        context.Track(record);
    }
    ```
