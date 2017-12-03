---
title: "Klasa podstawowa działania NativeActivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5f5a925aa9fc14c370c50ab0877742b207461c1d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="nativeactivity-base-class"></a><span data-ttu-id="0aeba-102">Klasa podstawowa działania NativeActivity</span><span class="sxs-lookup"><span data-stu-id="0aeba-102">NativeActivity Base Class</span></span>
<span data-ttu-id="0aeba-103"><xref:System.Activities.NativeActivity>jest klasą abstrakcyjną, przy użyciu konstruktora chronionych.</span><span class="sxs-lookup"><span data-stu-id="0aeba-103"><xref:System.Activities.NativeActivity> is an abstract class with a protected constructor.</span></span> <span data-ttu-id="0aeba-104">Podobnie jak <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> służy do zapisywania konieczne zachowanie zaimplementowanie <xref:System.Activities.NativeActivity.Execute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0aeba-104">Like <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> is used for writing imperative behavior by implementing an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span> <span data-ttu-id="0aeba-105">W odróżnieniu od <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> ma dostęp do wszystkich funkcji dostępnego środowiska uruchomieniowego przepływu pracy za pośrednictwem <xref:System.Activities.NativeActivityContext> obiekt przekazywany do <xref:System.Activities.NativeActivity.Execute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0aeba-105">Unlike <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> has access to all of the exposed features of the workflow runtime through the <xref:System.Activities.NativeActivityContext> object passed to the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
## <a name="using-nativeactivitycontext"></a><span data-ttu-id="0aeba-106">Przy użyciu NativeActivityContext</span><span class="sxs-lookup"><span data-stu-id="0aeba-106">Using NativeActivityContext</span></span>  
 <span data-ttu-id="0aeba-107">Funkcje środowiska uruchomieniowego przepływu pracy są dostępne z poziomu <xref:System.Activities.NativeActivity.Execute%2A> metody przy użyciu elementów członkowskich `context` parametr typu <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="0aeba-107">Features of the workflow runtime can be accessed from within the <xref:System.Activities.NativeActivity.Execute%2A> method by using members of the `context` parameter, of type <xref:System.Activities.NativeActivityContext>.</span></span> <span data-ttu-id="0aeba-108">Funkcji dostępnych za pośrednictwem <xref:System.Activities.NativeActivityContext> są następujące:</span><span class="sxs-lookup"><span data-stu-id="0aeba-108">The features available through <xref:System.Activities.NativeActivityContext> include the following:</span></span>  
  
-   <span data-ttu-id="0aeba-109">Pobieranie i Ustawianie zmiennych i argumentów.</span><span class="sxs-lookup"><span data-stu-id="0aeba-109">Getting and setting of arguments and variables.</span></span>  
  
-   <span data-ttu-id="0aeba-110">Planowanie działań podrzędnych z<xref:System.Activities.NativeActivityContext.ScheduleActivity%2A></span><span class="sxs-lookup"><span data-stu-id="0aeba-110">Scheduling child activities with <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A></span></span>  
  
-   <span data-ttu-id="0aeba-111">Trwa przerywanie wykonywania działania przy użyciu <xref:System.Activities.NativeActivityContext.Abort%2A>.</span><span class="sxs-lookup"><span data-stu-id="0aeba-111">Aborting activity execution using <xref:System.Activities.NativeActivityContext.Abort%2A>.</span></span>  
  
-   <span data-ttu-id="0aeba-112">Anulowanie wykonywania podrzędnych za pomocą <xref:System.Activities.NativeActivityContext.CancelChild%2A> i <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.</span><span class="sxs-lookup"><span data-stu-id="0aeba-112">Canceling child execution using <xref:System.Activities.NativeActivityContext.CancelChild%2A> and <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.</span></span>  
  
-   <span data-ttu-id="0aeba-113">Dostęp do zakładki działania przy użyciu metody, takie jak <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, i <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.</span><span class="sxs-lookup"><span data-stu-id="0aeba-113">Access to activity bookmarks using such methods as <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, and <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.</span></span>  
  
-   <span data-ttu-id="0aeba-114">Funkcje niestandardowe śledzenia przy użyciu <xref:System.Activities.CodeActivityContext.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="0aeba-114">Custom tracking features using <xref:System.Activities.CodeActivityContext.Track%2A>.</span></span>  
  
-   <span data-ttu-id="0aeba-115">Dostęp do właściwości wykonania działania i wartości właściwości, za pomocą <xref:System.Activities.CodeActivityContext.GetProperty%2A> i <xref:System.Activities.NativeActivityContext.GetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="0aeba-115">Access to the activity’s execution properties and value properties using <xref:System.Activities.CodeActivityContext.GetProperty%2A> and <xref:System.Activities.NativeActivityContext.GetValue%2A>.</span></span>  
  
-   <span data-ttu-id="0aeba-116">Planowanie działań działania i funkcji przy użyciu <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> i <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.</span><span class="sxs-lookup"><span data-stu-id="0aeba-116">Scheduling activity actions and functions using <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> and <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.</span></span>  
  
#### <a name="to-create-a-custom-activity-that-inherits-from-nativeactivity"></a><span data-ttu-id="0aeba-117">Aby utworzyć niestandardowe działania, który dziedziczy z elementu NativeActivity</span><span class="sxs-lookup"><span data-stu-id="0aeba-117">To create a custom activity that inherits from NativeActivity</span></span>  
  
1.  <span data-ttu-id="0aeba-118">Otwórz[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0aeba-118">Open[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="0aeba-119">Wybierz **pliku**, **nowe**, a następnie **projektu**.</span><span class="sxs-lookup"><span data-stu-id="0aeba-119">Select **File**, **New**, and then **Project**.</span></span> <span data-ttu-id="0aeba-120">Wybierz **Workflow 4.0** w obszarze **Visual C#** w **typów projektów** okna, a następnie wybierz **v2010** węzła.</span><span class="sxs-lookup"><span data-stu-id="0aeba-120">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="0aeba-121">Wybierz **Biblioteka działań** w **szablony** okna.</span><span class="sxs-lookup"><span data-stu-id="0aeba-121">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="0aeba-122">Nazwa nowego projektu HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="0aeba-122">Name the new project HelloActivity.</span></span>  
  
3.  <span data-ttu-id="0aeba-123">Kliknij prawym przyciskiem myszy Activity1.xaml w projekcie HelloActivity i wybierz **usunąć**.</span><span class="sxs-lookup"><span data-stu-id="0aeba-123">Right-click Activity1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4.  <span data-ttu-id="0aeba-124">Kliknij prawym przyciskiem myszy projekt HelloActivity i wybierz **Dodaj**, a następnie **klasy**.</span><span class="sxs-lookup"><span data-stu-id="0aeba-124">Right-click the HelloActivity project and select **Add**, and then **Class**.</span></span> <span data-ttu-id="0aeba-125">Nazwa nowej klasy HelloActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="0aeba-125">Name the new class HelloActivity.cs.</span></span>  
  
5.  <span data-ttu-id="0aeba-126">W pliku HelloActivity.cs, Dodaj następujący `using` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="0aeba-126">In the HelloActivity.cs file, add the following `using` directives.</span></span>  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.Statements;  
    ```  
  
6.  <span data-ttu-id="0aeba-127">Upewnij się nowa klasa dziedziczy <xref:System.Activities.NativeActivity> przez dodanie klasy podstawowej deklaracji klasy.</span><span class="sxs-lookup"><span data-stu-id="0aeba-127">Make the new class inherit from <xref:System.Activities.NativeActivity> by adding a base class to the class declaration.</span></span>  
  
    ```csharp  
    class HelloActivity : NativeActivity  
    ```  
  
7.  <span data-ttu-id="0aeba-128">Dodawanie funkcji do klasy, dodając <xref:System.Activities.NativeActivity.Execute%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0aeba-128">Add functionality to the class by adding an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>  
  
    ```csharp  
    protected override void Execute(NativeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
    }  
    ```  
  
8.  <span data-ttu-id="0aeba-129">Zastąpienie <xref:System.Activities.NativeActivity.CacheMetadata%2A> — metoda i wywołanie odpowiedniej metody Add, aby umożliwić wiedzieć o działań niestandardowych zmiennych, argumenty elementów podrzędnych i delegatów środowiska uruchomieniowego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="0aeba-129">Override the <xref:System.Activities.NativeActivity.CacheMetadata%2A> method and call the appropriate Add method to let the workflow runtime know about the custom activity’s variables, arguments, children, and delegates.</span></span> <span data-ttu-id="0aeba-130">Aby uzyskać więcej informacji, zobacz <xref:System.Activities.NativeActivityMetadata> klasy.</span><span class="sxs-lookup"><span data-stu-id="0aeba-130">For more information see the <xref:System.Activities.NativeActivityMetadata> class.</span></span>  
  
9. <span data-ttu-id="0aeba-131">Użyj <xref:System.Activities.NativeActivityContext> obiektu można zaplanować zakładki.</span><span class="sxs-lookup"><span data-stu-id="0aeba-131">Use the <xref:System.Activities.NativeActivityContext> object to schedule a bookmark.</span></span> <span data-ttu-id="0aeba-132">Zobacz <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> szczegółowe informacje dotyczące sposobu tworzenia, planowanie i wznowić zakładki.</span><span class="sxs-lookup"><span data-stu-id="0aeba-132">See <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> for details on how to create, schedule, and resume a bookmark.</span></span>  
  
    ```  
    protected override void Execute(NativeActivityContext context)  
        {  
            // Create a Bookmark and wait for it to be resumed.  
            context.CreateBookmark(BookmarkName.Get(context),   
                new BookmarkCallback(OnResumeBookmark));  
        }  
    ```
