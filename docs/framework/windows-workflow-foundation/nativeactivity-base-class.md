---
title: NativeActivity, klasa bazowa
ms.date: 03/30/2017
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
ms.openlocfilehash: f718d247e7110b46cdd13038c7c93c1e45612c75
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009984"
---
# <a name="nativeactivity-base-class"></a><span data-ttu-id="61871-102">NativeActivity, klasa bazowa</span><span class="sxs-lookup"><span data-stu-id="61871-102">NativeActivity Base Class</span></span>

<span data-ttu-id="61871-103"><xref:System.Activities.NativeActivity> jest klasą abstrakcyjną, przy użyciu Konstruktor chroniony.</span><span class="sxs-lookup"><span data-stu-id="61871-103"><xref:System.Activities.NativeActivity> is an abstract class with a protected constructor.</span></span> <span data-ttu-id="61871-104">Podobnie jak <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> służy do zapisywania imperatywne zachowanie przez zaimplementowanie <xref:System.Activities.NativeActivity.Execute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="61871-104">Like <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> is used for writing imperative behavior by implementing an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span> <span data-ttu-id="61871-105">W odróżnieniu od <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> ma dostęp do wszystkich funkcji narażonych środowiska uruchomieniowego przepływu pracy za pośrednictwem <xref:System.Activities.NativeActivityContext> obiekt przekazany do <xref:System.Activities.NativeActivity.Execute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="61871-105">Unlike <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> has access to all of the exposed features of the workflow runtime through the <xref:System.Activities.NativeActivityContext> object passed to the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>

## <a name="using-nativeactivitycontext"></a><span data-ttu-id="61871-106">Za pomocą NativeActivityContext</span><span class="sxs-lookup"><span data-stu-id="61871-106">Using NativeActivityContext</span></span>
 <span data-ttu-id="61871-107">Funkcje środowiska wykonawczego przepływów pracy są dostępne z poziomu <xref:System.Activities.NativeActivity.Execute%2A> metody za pomocą elementów członkowskich `context` parametr typu <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="61871-107">Features of the workflow runtime can be accessed from within the <xref:System.Activities.NativeActivity.Execute%2A> method by using members of the `context` parameter, of type <xref:System.Activities.NativeActivityContext>.</span></span> <span data-ttu-id="61871-108">Funkcje dostępne za pośrednictwem <xref:System.Activities.NativeActivityContext> obejmują następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="61871-108">The features available through <xref:System.Activities.NativeActivityContext> include the following:</span></span>

- <span data-ttu-id="61871-109">Pobieranie i Ustawianie zmiennych i argumentów.</span><span class="sxs-lookup"><span data-stu-id="61871-109">Getting and setting of arguments and variables.</span></span>

- <span data-ttu-id="61871-110">Planowanie działań podrzędnych za pomocą <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A></span><span class="sxs-lookup"><span data-stu-id="61871-110">Scheduling child activities with <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A></span></span>

- <span data-ttu-id="61871-111">Trwa przerywanie wykonywania czynności za pomocą <xref:System.Activities.NativeActivityContext.Abort%2A>.</span><span class="sxs-lookup"><span data-stu-id="61871-111">Aborting activity execution using <xref:System.Activities.NativeActivityContext.Abort%2A>.</span></span>

- <span data-ttu-id="61871-112">Anulowania wykonywania podrzędnych za pomocą <xref:System.Activities.NativeActivityContext.CancelChild%2A> i <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.</span><span class="sxs-lookup"><span data-stu-id="61871-112">Canceling child execution using <xref:System.Activities.NativeActivityContext.CancelChild%2A> and <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.</span></span>

- <span data-ttu-id="61871-113">Dostęp do zakładki działania przy użyciu metody, takie jak <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, i <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.</span><span class="sxs-lookup"><span data-stu-id="61871-113">Access to activity bookmarks using such methods as <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, and <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.</span></span>

- <span data-ttu-id="61871-114">Niestandardowe śledzenia funkcji przy użyciu <xref:System.Activities.CodeActivityContext.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="61871-114">Custom tracking features using <xref:System.Activities.CodeActivityContext.Track%2A>.</span></span>

- <span data-ttu-id="61871-115">Dostęp do właściwości wykonania tego działania i wartości właściwości, za pomocą <xref:System.Activities.CodeActivityContext.GetProperty%2A> i <xref:System.Activities.NativeActivityContext.GetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="61871-115">Access to the activity’s execution properties and value properties using <xref:System.Activities.CodeActivityContext.GetProperty%2A> and <xref:System.Activities.NativeActivityContext.GetValue%2A>.</span></span>

- <span data-ttu-id="61871-116">Planowanie akcji działania i funkcji przy użyciu <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> i <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.</span><span class="sxs-lookup"><span data-stu-id="61871-116">Scheduling activity actions and functions using <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> and <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.</span></span>

### <a name="to-create-a-custom-activity-that-inherits-from-nativeactivity"></a><span data-ttu-id="61871-117">Aby utworzyć niestandardowe działanie, która dziedziczy z elementu NativeActivity</span><span class="sxs-lookup"><span data-stu-id="61871-117">To create a custom activity that inherits from NativeActivity</span></span>

1. <span data-ttu-id="61871-118">OpenVisual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="61871-118">OpenVisual Studio 2010.</span></span>

2. <span data-ttu-id="61871-119">Wybierz **pliku**, **nowe**, a następnie **projektu**.</span><span class="sxs-lookup"><span data-stu-id="61871-119">Select **File**, **New**, and then **Project**.</span></span> <span data-ttu-id="61871-120">Wybierz **Workflow 4.0** w obszarze **Visual C#** w **typów projektów** okna, a następnie wybierz **v2010** węzła.</span><span class="sxs-lookup"><span data-stu-id="61871-120">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="61871-121">Wybierz **Biblioteka działań** w **szablony** okna.</span><span class="sxs-lookup"><span data-stu-id="61871-121">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="61871-122">Nazwa nowego projektu HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="61871-122">Name the new project HelloActivity.</span></span>

3. <span data-ttu-id="61871-123">Kliknij prawym przyciskiem myszy Activity1.xaml w projekcie HelloActivity, a następnie wybierz pozycję **Usuń**.</span><span class="sxs-lookup"><span data-stu-id="61871-123">Right-click Activity1.xaml in the HelloActivity project and select **Delete**.</span></span>

4. <span data-ttu-id="61871-124">Kliknij prawym przyciskiem myszy projekt HelloActivity, a następnie wybierz pozycję **Dodaj**, a następnie **klasy**.</span><span class="sxs-lookup"><span data-stu-id="61871-124">Right-click the HelloActivity project and select **Add**, and then **Class**.</span></span> <span data-ttu-id="61871-125">Nazwa nowej klasy HelloActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="61871-125">Name the new class HelloActivity.cs.</span></span>

5. <span data-ttu-id="61871-126">W pliku HelloActivity.cs, Dodaj następujący kod `using` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="61871-126">In the HelloActivity.cs file, add the following `using` directives.</span></span>

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. <span data-ttu-id="61871-127">Wprowadź nowy dziedziczyć z klasy <xref:System.Activities.NativeActivity> przez dodanie klasy bazowej do deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="61871-127">Make the new class inherit from <xref:System.Activities.NativeActivity> by adding a base class to the class declaration.</span></span>

    ```csharp
    class HelloActivity : NativeActivity
    ```

7. <span data-ttu-id="61871-128">Dodawanie funkcji do klasy, dodając <xref:System.Activities.NativeActivity.Execute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="61871-128">Add functionality to the class by adding an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>

    ```csharp
    protected override void Execute(NativeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. <span data-ttu-id="61871-129">Zastąp <xref:System.Activities.NativeActivity.CacheMetadata%2A> metody i wywołanie odpowiedniej metody Add umożliwiające wiedzieć o zmienne, argumenty, elementy podrzędne i delegatów działania niestandardowego środowiska uruchomieniowego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="61871-129">Override the <xref:System.Activities.NativeActivity.CacheMetadata%2A> method and call the appropriate Add method to let the workflow runtime know about the custom activity’s variables, arguments, children, and delegates.</span></span> <span data-ttu-id="61871-130">Aby uzyskać więcej informacji, zobacz <xref:System.Activities.NativeActivityMetadata> klasy.</span><span class="sxs-lookup"><span data-stu-id="61871-130">For more information see the <xref:System.Activities.NativeActivityMetadata> class.</span></span>

9. <span data-ttu-id="61871-131">Użyj <xref:System.Activities.NativeActivityContext> obiektu, aby zaplanować zakładki.</span><span class="sxs-lookup"><span data-stu-id="61871-131">Use the <xref:System.Activities.NativeActivityContext> object to schedule a bookmark.</span></span> <span data-ttu-id="61871-132">Zobacz <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> Aby uzyskać szczegółowe informacje dotyczące sposobu tworzenia, planowanie i wznowienie zakładki.</span><span class="sxs-lookup"><span data-stu-id="61871-132">See <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> for details on how to create, schedule, and resume a bookmark.</span></span>

    ```
    protected override void Execute(NativeActivityContext context)
        {
            // Create a Bookmark and wait for it to be resumed.
            context.CreateBookmark(BookmarkName.Get(context),
                new BookmarkCallback(OnResumeBookmark));
        }
    ```