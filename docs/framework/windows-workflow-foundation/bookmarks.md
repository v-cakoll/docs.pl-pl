---
title: Bookmarks1
ms.date: 03/30/2017
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
ms.openlocfilehash: 8b7ca9549327087e30d6c72a8b784aa37ad09f3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774149"
---
# <a name="bookmarks"></a><span data-ttu-id="8e20f-102">Zakładki</span><span class="sxs-lookup"><span data-stu-id="8e20f-102">Bookmarks</span></span>
<span data-ttu-id="8e20f-103">Zakładki są mechanizm, który umożliwia działanie pasywnie czeka na dane wejściowe bez przytrzymywania na wątku przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8e20f-103">Bookmarks are the mechanism that enables an activity to passively wait for input without holding onto a workflow thread.</span></span> <span data-ttu-id="8e20f-104">Gdy działanie sygnalizuje, że trwa oczekiwanie bodziec, może utworzyć zakładki.</span><span class="sxs-lookup"><span data-stu-id="8e20f-104">When an activity signals that it is waiting for stimulus, it can create a bookmark.</span></span> <span data-ttu-id="8e20f-105">Oznacza to, aby środowisko uruchomieniowe, wykonanie tego działania nie powinny być uwzględniane pełną nawet wtedy, gdy aktualnie wykonywanej metody (którym utworzono <xref:System.Activities.Bookmark>) zwraca.</span><span class="sxs-lookup"><span data-stu-id="8e20f-105">This indicates to the runtime that the activity’s execution should not be considered complete even when the currently executing method (which created the <xref:System.Activities.Bookmark>) returns.</span></span>  
  
## <a name="bookmark-basics"></a><span data-ttu-id="8e20f-106">Podstawowe informacje dotyczące zakładki</span><span class="sxs-lookup"><span data-stu-id="8e20f-106">Bookmark Basics</span></span>  
 <span data-ttu-id="8e20f-107">A <xref:System.Activities.Bookmark> reprezentuje punkt, w których wykonanie można wznowić (za pośrednictwem których dane wejściowe mogą być dostarczane) w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8e20f-107">A <xref:System.Activities.Bookmark> represents a point at which execution can be resumed (and through which input can be delivered) within a workflow instance.</span></span> <span data-ttu-id="8e20f-108">Zazwyczaj <xref:System.Activities.Bookmark> jest nadawana nazwa i kod zewnętrzny (hosta lub rozszerzeniu) jest odpowiedzialny za wznowienie zakładki z odpowiednimi danymi.</span><span class="sxs-lookup"><span data-stu-id="8e20f-108">Typically, a <xref:System.Activities.Bookmark> is given a name and external (host or extension) code is responsible for resuming the bookmark with relevant data.</span></span> <span data-ttu-id="8e20f-109">Gdy <xref:System.Activities.Bookmark> zostanie wznowione, harmonogramy środowiska uruchomieniowego przepływu pracy <xref:System.Activities.BookmarkCallback> delegat, który został skojarzony z tym <xref:System.Activities.Bookmark> w czasie jego tworzenia.</span><span class="sxs-lookup"><span data-stu-id="8e20f-109">When a <xref:System.Activities.Bookmark> is resumed, the workflow runtime schedules the <xref:System.Activities.BookmarkCallback> delegate that was associated with that <xref:System.Activities.Bookmark> at the time of its creation.</span></span>  
  
## <a name="bookmark-options"></a><span data-ttu-id="8e20f-110">Opcje zakładek</span><span class="sxs-lookup"><span data-stu-id="8e20f-110">Bookmark Options</span></span>  
 <span data-ttu-id="8e20f-111"><xref:System.Activities.BookmarkOptions> Klasy określa typ <xref:System.Activities.Bookmark> tworzona.</span><span class="sxs-lookup"><span data-stu-id="8e20f-111">The <xref:System.Activities.BookmarkOptions> class specifies the type of <xref:System.Activities.Bookmark> being created.</span></span> <span data-ttu-id="8e20f-112">Możliwe wartości inne niż wzajemnie wykluczającymi się <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, i <xref:System.Activities.BookmarkOptions.NonBlocking>.</span><span class="sxs-lookup"><span data-stu-id="8e20f-112">The possible non mutually-exclusive values are <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, and <xref:System.Activities.BookmarkOptions.NonBlocking>.</span></span> <span data-ttu-id="8e20f-113">Użyj <xref:System.Activities.BookmarkOptions.None>, domyślnie, podczas tworzenia <xref:System.Activities.Bookmark> zgodnie z oczekiwaniami można wznowić dokładnie jeden raz.</span><span class="sxs-lookup"><span data-stu-id="8e20f-113">Use <xref:System.Activities.BookmarkOptions.None>, the default, when creating a <xref:System.Activities.Bookmark> that is expected to be resumed exactly once.</span></span> <span data-ttu-id="8e20f-114">Użyj <xref:System.Activities.BookmarkOptions.MultipleResume> podczas tworzenia <xref:System.Activities.Bookmark> , może być wznowione wiele razy.</span><span class="sxs-lookup"><span data-stu-id="8e20f-114">Use <xref:System.Activities.BookmarkOptions.MultipleResume> when creating a <xref:System.Activities.Bookmark> that can be resumed multiple times.</span></span> <span data-ttu-id="8e20f-115">Użyj <xref:System.Activities.BookmarkOptions.NonBlocking> podczas tworzenia <xref:System.Activities.Bookmark> , nigdy nie może być wznowione.</span><span class="sxs-lookup"><span data-stu-id="8e20f-115">Use <xref:System.Activities.BookmarkOptions.NonBlocking> when creating a <xref:System.Activities.Bookmark> that might never be resumed.</span></span> <span data-ttu-id="8e20f-116">W przeciwieństwie do zakładki utworzone przy użyciu domyślnego <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> zakładki uniemożliwia ukończenie działania.</span><span class="sxs-lookup"><span data-stu-id="8e20f-116">Unlike bookmarks created using the default <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> bookmarks do not prevent an activity from completing.</span></span>  
  
## <a name="bookmark-resumption"></a><span data-ttu-id="8e20f-117">Wznowienie zakładki</span><span class="sxs-lookup"><span data-stu-id="8e20f-117">Bookmark Resumption</span></span>  
 <span data-ttu-id="8e20f-118">Zakładki, może być wznowione przez kod poza przepływu pracy przy użyciu jednej z <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="8e20f-118">Bookmarks can be resumed by code outside of a workflow using one of the <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> overloads.</span></span> <span data-ttu-id="8e20f-119">W tym przykładzie `ReadLine` utworzeniu działania.</span><span class="sxs-lookup"><span data-stu-id="8e20f-119">In this example, a `ReadLine` activity is created.</span></span> <span data-ttu-id="8e20f-120">Po wykonaniu `ReadLine` tworzy działanie <xref:System.Activities.Bookmark>, rejestruje wywołanie zwrotne, a następnie czeka na <xref:System.Activities.Bookmark> wznowienie.</span><span class="sxs-lookup"><span data-stu-id="8e20f-120">When executed, the `ReadLine` activity creates a <xref:System.Activities.Bookmark>, registers a callback, and then waits for the <xref:System.Activities.Bookmark> to be resumed.</span></span> <span data-ttu-id="8e20f-121">Gdy zostanie wznowione, `ReadLine` działania przypisuje danych, który został przekazany z <xref:System.Activities.Bookmark> do jego <xref:System.Activities.Activity%601.Result%2A> argumentu.</span><span class="sxs-lookup"><span data-stu-id="8e20f-121">When it is resumed, the `ReadLine` activity assigns the data that was passed with the <xref:System.Activities.Bookmark> to its <xref:System.Activities.Activity%601.Result%2A> argument.</span></span>  
  
```csharp  
public sealed class ReadLine : NativeActivity<string>  
{  
    [RequiredArgument]  
    public  InArgument<string> BookmarkName { get; set; }  
  
    protected override void Execute(NativeActivityContext context)  
    {  
        // Create a Bookmark and wait for it to be resumed.  
        context.CreateBookmark(BookmarkName.Get(context),   
            new BookmarkCallback(OnResumeBookmark));  
    }  
  
    // NativeActivity derived activities that do asynchronous operations by calling   
    // one of the CreateBookmark overloads defined on System.Activities.NativeActivityContext   
    // must override the CanInduceIdle property and return true.  
    protected override bool CanInduceIdle  
    {  
        get { return true; }  
    }  
  
    public void OnResumeBookmark(NativeActivityContext context, Bookmark bookmark, object obj)  
    {  
        // When the Bookmark is resumed, assign its value to  
        // the Result argument.  
        Result.Set(context, (string)obj);  
    }  
}  
```  
  
 <span data-ttu-id="8e20f-122">W tym przykładzie przepływ pracy jest tworzony, który używa `ReadLine` działanie, aby zbierać nazwy użytkownika i wyświetl ją w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="8e20f-122">In this example, a workflow is created that uses the `ReadLine` activity to gather the user’s name and display it to the console window.</span></span> <span data-ttu-id="8e20f-123">Aplikacja hosta wykonuje rzeczywistą pracę zbierania danych wejściowych i przekazuje je do przepływu pracy przez wznawianie <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="8e20f-123">The host application performs the actual work of gathering the input and passes it to the workflow by resuming the <xref:System.Activities.Bookmark>.</span></span>  
  
```csharp  
Variable<string> name = new Variable<string>  
{  
    Name = "name"  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        name  
    },  
    Activities =  
    {  
        new WriteLine()  
        {  
            Text = "What is your name?"  
        },  
        new ReadLine()  
        {  
            BookmarkName = "UserName",  
            Result = name  
        },  
        new WriteLine()  
        {  
            Text = new InArgument<string>((env) => "Hello, " + name.Get(env))  
        }  
    }  
};  
  
AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
// Create the WorkflowApplication using the desired  
// workflow definition.  
WorkflowApplication wfApp = new WorkflowApplication(wf);  
  
// Handle the desired lifecycle events.  
wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
{  
    // Signal the host that the workflow is complete.  
    syncEvent.Set();  
};  
  
// Start the workflow.  
wfApp.Run();  
  
// Collect the user's name and resume the bookmark.  
// Bookmark resumption only occurs when the workflow  
// is idle. If a call to ResumeBookmark is made and the workflow  
// is not idle, ResumeBookmark blocks until the workflow becomes  
// idle before resuming the bookmark.  
wfApp.ResumeBookmark("UserName", Console.ReadLine());  
  
// Wait for Completed to arrive and signal that  
// the workflow is complete.  
syncEvent.WaitOne();  
```  
  
 <span data-ttu-id="8e20f-124">Gdy `ReadLine` jest wykonywane działanie, tworzy on <xref:System.Activities.Bookmark> o nazwie `UserName` , a następnie czeka zakładki wznowienie.</span><span class="sxs-lookup"><span data-stu-id="8e20f-124">When the `ReadLine` activity is executed, it creates a <xref:System.Activities.Bookmark> named `UserName` and then waits for the bookmark to be resumed.</span></span> <span data-ttu-id="8e20f-125">Zbiera dane żądanego hosta, a następnie kontynuowanie <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="8e20f-125">The host collects the desired data and then resumes the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="8e20f-126">Przepływ pracy zostanie wznowione, wyświetla nazwę, a następnie kończy.</span><span class="sxs-lookup"><span data-stu-id="8e20f-126">The workflow resumes, displays the name, and then completes.</span></span> <span data-ttu-id="8e20f-127">Zwróć uwagę, że żaden kod synchronizacji wymagane w odniesieniu do wznowienie zakładki.</span><span class="sxs-lookup"><span data-stu-id="8e20f-127">Note that no synchronization code is required with regard to resuming the bookmark.</span></span> <span data-ttu-id="8e20f-128">A <xref:System.Activities.Bookmark> można wznowić tylko wtedy, gdy przepływ pracy jest bezczynny, i jeśli przepływ pracy nie jest bezczynny, wywołanie <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> blokuje, aż przepływu pracy staje się nieaktywna.</span><span class="sxs-lookup"><span data-stu-id="8e20f-128">A <xref:System.Activities.Bookmark> can only be resumed when the workflow is idle, and if the workflow is not idle, the call to <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> blocks until the workflow becomes idle.</span></span>  
  
## <a name="bookmark-resumption-result"></a><span data-ttu-id="8e20f-129">Wynik wznowienie zakładki</span><span class="sxs-lookup"><span data-stu-id="8e20f-129">Bookmark Resumption Result</span></span>  
 <span data-ttu-id="8e20f-130"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> Zwraca <xref:System.Activities.BookmarkResumptionResult> wartości wyliczenia, aby wskazać wyniki żądania wznowienie zakładki.</span><span class="sxs-lookup"><span data-stu-id="8e20f-130"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> returns a <xref:System.Activities.BookmarkResumptionResult> enumeration value to indicate the results of the bookmark resumption request.</span></span> <span data-ttu-id="8e20f-131">Możliwe wartości zwracane są <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, i <xref:System.Activities.BookmarkResumptionResult.NotFound>.</span><span class="sxs-lookup"><span data-stu-id="8e20f-131">The possible return values are <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, and <xref:System.Activities.BookmarkResumptionResult.NotFound>.</span></span> <span data-ttu-id="8e20f-132">Tej wartości można użyć hostów i rozszerzenia do określenia, jak można kontynuować.</span><span class="sxs-lookup"><span data-stu-id="8e20f-132">Hosts and extensions can use this value to determine how to proceed.</span></span>
