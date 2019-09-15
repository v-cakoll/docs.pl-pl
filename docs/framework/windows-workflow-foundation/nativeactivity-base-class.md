---
title: NativeActivity, klasa bazowa
ms.date: 03/30/2017
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
ms.openlocfilehash: 604535e39937a75c6d268cf1abbc90dbcd506a16
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989552"
---
# <a name="nativeactivity-base-class"></a><span data-ttu-id="01dc7-102">NativeActivity, klasa bazowa</span><span class="sxs-lookup"><span data-stu-id="01dc7-102">NativeActivity Base Class</span></span>

<span data-ttu-id="01dc7-103"><xref:System.Activities.NativeActivity>jest klasą abstrakcyjną z chronionym konstruktorem.</span><span class="sxs-lookup"><span data-stu-id="01dc7-103"><xref:System.Activities.NativeActivity> is an abstract class with a protected constructor.</span></span> <span data-ttu-id="01dc7-104">Na przykład, <xref:System.Activities.NativeActivity> jest używany do pisania bezwzględnego zachowania <xref:System.Activities.NativeActivity.Execute%2A> przez implementację metody. <xref:System.Activities.CodeActivity></span><span class="sxs-lookup"><span data-stu-id="01dc7-104">Like <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> is used for writing imperative behavior by implementing an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span> <span data-ttu-id="01dc7-105">W <xref:System.Activities.CodeActivity>przeciwieństwie <xref:System.Activities.NativeActivity> do, ma dostęp do wszystkich narażonych funkcji środowiska uruchomieniowego przepływu pracy <xref:System.Activities.NativeActivityContext> za pomocą obiektu przesłanego do <xref:System.Activities.NativeActivity.Execute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="01dc7-105">Unlike <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> has access to all of the exposed features of the workflow runtime through the <xref:System.Activities.NativeActivityContext> object passed to the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>

## <a name="using-nativeactivitycontext"></a><span data-ttu-id="01dc7-106">Korzystanie z NativeActivityContext</span><span class="sxs-lookup"><span data-stu-id="01dc7-106">Using NativeActivityContext</span></span>
 <span data-ttu-id="01dc7-107">Dostęp do funkcji środowiska uruchomieniowego przepływu pracy można uzyskać z <xref:System.Activities.NativeActivity.Execute%2A> poziomu metody przy użyciu elementów członkowskich `context` parametru typu <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="01dc7-107">Features of the workflow runtime can be accessed from within the <xref:System.Activities.NativeActivity.Execute%2A> method by using members of the `context` parameter, of type <xref:System.Activities.NativeActivityContext>.</span></span> <span data-ttu-id="01dc7-108">Dostępne <xref:System.Activities.NativeActivityContext> są następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="01dc7-108">The features available through <xref:System.Activities.NativeActivityContext> include the following:</span></span>

- <span data-ttu-id="01dc7-109">Pobieranie i określanie argumentów i zmiennych.</span><span class="sxs-lookup"><span data-stu-id="01dc7-109">Getting and setting of arguments and variables.</span></span>

- <span data-ttu-id="01dc7-110">Planowanie działań podrzędnych przy użyciu<xref:System.Activities.NativeActivityContext.ScheduleActivity%2A></span><span class="sxs-lookup"><span data-stu-id="01dc7-110">Scheduling child activities with <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A></span></span>

- <span data-ttu-id="01dc7-111">Przerywanie wykonywania działania przy <xref:System.Activities.NativeActivityContext.Abort%2A>użyciu.</span><span class="sxs-lookup"><span data-stu-id="01dc7-111">Aborting activity execution using <xref:System.Activities.NativeActivityContext.Abort%2A>.</span></span>

- <span data-ttu-id="01dc7-112">Anulowanie wykonywania elementu podrzędnego <xref:System.Activities.NativeActivityContext.CancelChild%2A> za <xref:System.Activities.NativeActivityContext.CancelChildren%2A>pomocą i.</span><span class="sxs-lookup"><span data-stu-id="01dc7-112">Canceling child execution using <xref:System.Activities.NativeActivityContext.CancelChild%2A> and <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.</span></span>

- <span data-ttu-id="01dc7-113">Dostęp do zakładek aktywności przy użyciu takich <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>metod <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>jak, <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>i.</span><span class="sxs-lookup"><span data-stu-id="01dc7-113">Access to activity bookmarks using such methods as <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, and <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.</span></span>

- <span data-ttu-id="01dc7-114">Niestandardowe funkcje śledzenia przy <xref:System.Activities.CodeActivityContext.Track%2A>użyciu programu.</span><span class="sxs-lookup"><span data-stu-id="01dc7-114">Custom tracking features using <xref:System.Activities.CodeActivityContext.Track%2A>.</span></span>

- <span data-ttu-id="01dc7-115">Dostęp do właściwości wykonywania działania i właściwości wartości przy użyciu <xref:System.Activities.CodeActivityContext.GetProperty%2A> i. <xref:System.Activities.NativeActivityContext.GetValue%2A></span><span class="sxs-lookup"><span data-stu-id="01dc7-115">Access to the activity’s execution properties and value properties using <xref:System.Activities.CodeActivityContext.GetProperty%2A> and <xref:System.Activities.NativeActivityContext.GetValue%2A>.</span></span>

- <span data-ttu-id="01dc7-116">Planowanie akcji i funkcji działania przy <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> użyciu <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>i.</span><span class="sxs-lookup"><span data-stu-id="01dc7-116">Scheduling activity actions and functions using <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> and <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.</span></span>

### <a name="to-create-a-custom-activity-that-inherits-from-nativeactivity"></a><span data-ttu-id="01dc7-117">Aby utworzyć niestandardowe działanie, które dziedziczy z natywnego</span><span class="sxs-lookup"><span data-stu-id="01dc7-117">To create a custom activity that inherits from NativeActivity</span></span>

1. <span data-ttu-id="01dc7-118">OpenVisual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="01dc7-118">OpenVisual Studio 2010.</span></span>

2. <span data-ttu-id="01dc7-119">Wybierz kolejno opcje **plik**, **Nowy**i **projekt**.</span><span class="sxs-lookup"><span data-stu-id="01dc7-119">Select **File**, **New**, and then **Project**.</span></span> <span data-ttu-id="01dc7-120">Wybierz pozycję **Workflow 4,0** w obszarze **Wizualizacja C#**  w oknie **typy projektów** , a następnie wybierz węzeł **V2010** .</span><span class="sxs-lookup"><span data-stu-id="01dc7-120">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="01dc7-121">Wybierz pozycję **Biblioteka działań** w oknie **Szablony** .</span><span class="sxs-lookup"><span data-stu-id="01dc7-121">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="01dc7-122">Nadaj nazwę nowej powitaniu projektu.</span><span class="sxs-lookup"><span data-stu-id="01dc7-122">Name the new project HelloActivity.</span></span>

3. <span data-ttu-id="01dc7-123">Kliknij prawym przyciskiem myszy pozycję zakończeniu. XAML w projekcie Hello i wybierz polecenie **Usuń**.</span><span class="sxs-lookup"><span data-stu-id="01dc7-123">Right-click Activity1.xaml in the HelloActivity project and select **Delete**.</span></span>

4. <span data-ttu-id="01dc7-124">Kliknij prawym przyciskiem myszy projekt Hello i wybierz polecenie **Dodaj**, a następnie **klasy**.</span><span class="sxs-lookup"><span data-stu-id="01dc7-124">Right-click the HelloActivity project and select **Add**, and then **Class**.</span></span> <span data-ttu-id="01dc7-125">Nadaj nowej klasie nazwę HelloActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="01dc7-125">Name the new class HelloActivity.cs.</span></span>

5. <span data-ttu-id="01dc7-126">W pliku HelloActivity.cs Dodaj następujące `using` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="01dc7-126">In the HelloActivity.cs file, add the following `using` directives.</span></span>

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. <span data-ttu-id="01dc7-127">Uczyń nową klasę dziedziczą <xref:System.Activities.NativeActivity> przez dodanie klasy bazowej do deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="01dc7-127">Make the new class inherit from <xref:System.Activities.NativeActivity> by adding a base class to the class declaration.</span></span>

    ```csharp
    class HelloActivity : NativeActivity
    ```

7. <span data-ttu-id="01dc7-128">Dodaj funkcję do klasy, <xref:System.Activities.NativeActivity.Execute%2A> dodając metodę.</span><span class="sxs-lookup"><span data-stu-id="01dc7-128">Add functionality to the class by adding an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>

    ```csharp
    protected override void Execute(NativeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. <span data-ttu-id="01dc7-129">Zastąp <xref:System.Activities.NativeActivity.CacheMetadata%2A> metodę i Wywołaj odpowiednią metodę Add, aby umożliwić środowisko uruchomieniowe przepływu pracy znać zmienne, argumenty, elementy podrzędne i Delegaty działania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="01dc7-129">Override the <xref:System.Activities.NativeActivity.CacheMetadata%2A> method and call the appropriate Add method to let the workflow runtime know about the custom activity’s variables, arguments, children, and delegates.</span></span> <span data-ttu-id="01dc7-130">Aby uzyskać więcej informacji, <xref:System.Activities.NativeActivityMetadata> zobacz Klasa.</span><span class="sxs-lookup"><span data-stu-id="01dc7-130">For more information see the <xref:System.Activities.NativeActivityMetadata> class.</span></span>

9. <span data-ttu-id="01dc7-131">Użyj obiektu <xref:System.Activities.NativeActivityContext> , aby zaplanować zakładkę.</span><span class="sxs-lookup"><span data-stu-id="01dc7-131">Use the <xref:System.Activities.NativeActivityContext> object to schedule a bookmark.</span></span> <span data-ttu-id="01dc7-132">Zobacz <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> , aby uzyskać szczegółowe informacje na temat tworzenia, planowania i wznawiania zakładki.</span><span class="sxs-lookup"><span data-stu-id="01dc7-132">See <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> for details on how to create, schedule, and resume a bookmark.</span></span>

    ```csharp
    protected override void Execute(NativeActivityContext context)
        {
            // Create a Bookmark and wait for it to be resumed.
            context.CreateBookmark(BookmarkName.Get(context),
                new BookmarkCallback(OnResumeBookmark));
        }
    ```
