---
title: Zakładki — WF
ms.date: 03/30/2017
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
ms.openlocfilehash: a15a28cc39a4227765c238a6f2b86c72197f1a39
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868920"
---
# <a name="bookmarks"></a><span data-ttu-id="f2fbd-102">Zakładki</span><span class="sxs-lookup"><span data-stu-id="f2fbd-102">Bookmarks</span></span>
<span data-ttu-id="f2fbd-103">Zakładki to mechanizm, który umożliwia działanie pasywnego oczekiwania na dane wejściowe bez udziału w wątku przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="f2fbd-103">Bookmarks are the mechanism that enables an activity to passively wait for input without holding onto a workflow thread.</span></span> <span data-ttu-id="f2fbd-104">Gdy działanie sygnalizuje, że oczekuje na bodźce, może utworzyć zakładkę.</span><span class="sxs-lookup"><span data-stu-id="f2fbd-104">When an activity signals that it is waiting for stimulus, it can create a bookmark.</span></span> <span data-ttu-id="f2fbd-105">Wskazuje to, że środowisko uruchomieniowe nie powinno być uznawane za wykonane, nawet gdy aktualnie wykonywana Metoda (która została utworzona <xref:System.Activities.Bookmark>) zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="f2fbd-105">This indicates to the runtime that the activity’s execution should not be considered complete even when the currently executing method (which created the <xref:System.Activities.Bookmark>) returns.</span></span>  
  
## <a name="bookmark-basics"></a><span data-ttu-id="f2fbd-106">Podstawowe informacje o zakładkach</span><span class="sxs-lookup"><span data-stu-id="f2fbd-106">Bookmark Basics</span></span>  
 <span data-ttu-id="f2fbd-107"><xref:System.Activities.Bookmark> Reprezentuje punkt, w którym można wznowić wykonywanie (i za pomocą którego dane wejściowe można dostarczyć) w ramach wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="f2fbd-107">A <xref:System.Activities.Bookmark> represents a point at which execution can be resumed (and through which input can be delivered) within a workflow instance.</span></span> <span data-ttu-id="f2fbd-108"><xref:System.Activities.Bookmark> Zazwyczaj otrzymujesz nazwę i zewnętrzny kod (hosta lub rozszerzenia) jest odpowiedzialny za wznawianie zakładki z odpowiednimi danymi.</span><span class="sxs-lookup"><span data-stu-id="f2fbd-108">Typically, a <xref:System.Activities.Bookmark> is given a name and external (host or extension) code is responsible for resuming the bookmark with relevant data.</span></span> <span data-ttu-id="f2fbd-109">Gdy zostanie wznowiony, środowisko uruchomieniowe przepływu pracy <xref:System.Activities.BookmarkCallback> planuje delegata, który został <xref:System.Activities.Bookmark> skojarzony z tym w momencie jego tworzenia. <xref:System.Activities.Bookmark></span><span class="sxs-lookup"><span data-stu-id="f2fbd-109">When a <xref:System.Activities.Bookmark> is resumed, the workflow runtime schedules the <xref:System.Activities.BookmarkCallback> delegate that was associated with that <xref:System.Activities.Bookmark> at the time of its creation.</span></span>  
  
## <a name="bookmark-options"></a><span data-ttu-id="f2fbd-110">Opcje zakładki</span><span class="sxs-lookup"><span data-stu-id="f2fbd-110">Bookmark Options</span></span>  
 <span data-ttu-id="f2fbd-111">Klasa określa typ tworzonego elementu <xref:System.Activities.Bookmark>. <xref:System.Activities.BookmarkOptions></span><span class="sxs-lookup"><span data-stu-id="f2fbd-111">The <xref:System.Activities.BookmarkOptions> class specifies the type of <xref:System.Activities.Bookmark> being created.</span></span> <span data-ttu-id="f2fbd-112">Możliwe niewzajemnie wykluczające się wartości <xref:System.Activities.BookmarkOptions.None>to <xref:System.Activities.BookmarkOptions.MultipleResume>,, <xref:System.Activities.BookmarkOptions.NonBlocking>i.</span><span class="sxs-lookup"><span data-stu-id="f2fbd-112">The possible non mutually-exclusive values are <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, and <xref:System.Activities.BookmarkOptions.NonBlocking>.</span></span> <span data-ttu-id="f2fbd-113">Użyj <xref:System.Activities.BookmarkOptions.None>, domyślnie, podczas <xref:System.Activities.Bookmark> tworzenia, który jest oczekiwany do wznowienia dokładnie jeden raz.</span><span class="sxs-lookup"><span data-stu-id="f2fbd-113">Use <xref:System.Activities.BookmarkOptions.None>, the default, when creating a <xref:System.Activities.Bookmark> that is expected to be resumed exactly once.</span></span> <span data-ttu-id="f2fbd-114">Używany <xref:System.Activities.BookmarkOptions.MultipleResume> podczas<xref:System.Activities.Bookmark> tworzenia, który może być wznowiony wiele razy.</span><span class="sxs-lookup"><span data-stu-id="f2fbd-114">Use <xref:System.Activities.BookmarkOptions.MultipleResume> when creating a <xref:System.Activities.Bookmark> that can be resumed multiple times.</span></span> <span data-ttu-id="f2fbd-115">Używany <xref:System.Activities.BookmarkOptions.NonBlocking> podczas<xref:System.Activities.Bookmark> tworzenia, który może nigdy nie zostać wznowiony.</span><span class="sxs-lookup"><span data-stu-id="f2fbd-115">Use <xref:System.Activities.BookmarkOptions.NonBlocking> when creating a <xref:System.Activities.Bookmark> that might never be resumed.</span></span> <span data-ttu-id="f2fbd-116">W przeciwieństwie do zakładek utworzonych <xref:System.Activities.BookmarkOptions>przy <xref:System.Activities.BookmarkOptions.NonBlocking> użyciu domyślnego, zakładki nie uniemożliwiają ukończenia działania.</span><span class="sxs-lookup"><span data-stu-id="f2fbd-116">Unlike bookmarks created using the default <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> bookmarks do not prevent an activity from completing.</span></span>  
  
## <a name="bookmark-resumption"></a><span data-ttu-id="f2fbd-117">Wznowienie zakładki</span><span class="sxs-lookup"><span data-stu-id="f2fbd-117">Bookmark Resumption</span></span>  
 <span data-ttu-id="f2fbd-118">Zakładki można wznawiać przez kod poza przepływem pracy przy użyciu jednego z <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> przeciążeń.</span><span class="sxs-lookup"><span data-stu-id="f2fbd-118">Bookmarks can be resumed by code outside of a workflow using one of the <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> overloads.</span></span> <span data-ttu-id="f2fbd-119">W tym przykładzie `ReadLine` tworzone jest działanie.</span><span class="sxs-lookup"><span data-stu-id="f2fbd-119">In this example, a `ReadLine` activity is created.</span></span> <span data-ttu-id="f2fbd-120">Po wykonaniu `ReadLine` działanie <xref:System.Activities.Bookmark>tworzy, rejestruje wywołanie zwrotne, <xref:System.Activities.Bookmark> a następnie czeka na wznowienie.</span><span class="sxs-lookup"><span data-stu-id="f2fbd-120">When executed, the `ReadLine` activity creates a <xref:System.Activities.Bookmark>, registers a callback, and then waits for the <xref:System.Activities.Bookmark> to be resumed.</span></span> <span data-ttu-id="f2fbd-121">Gdy zostanie ono wznowione, `ReadLine` działanie przypisze dane, które zostały przesłane z do <xref:System.Activities.Bookmark> <xref:System.Activities.Activity%601.Result%2A> tego argumentu.</span><span class="sxs-lookup"><span data-stu-id="f2fbd-121">When it is resumed, the `ReadLine` activity assigns the data that was passed with the <xref:System.Activities.Bookmark> to its <xref:System.Activities.Activity%601.Result%2A> argument.</span></span>  
  
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
  
 <span data-ttu-id="f2fbd-122">W tym przykładzie zostanie utworzony przepływ pracy, który używa `ReadLine` działania do zbierania nazwy użytkownika i wyświetlania go w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="f2fbd-122">In this example, a workflow is created that uses the `ReadLine` activity to gather the user’s name and display it to the console window.</span></span> <span data-ttu-id="f2fbd-123">Aplikacja hosta wykonuje rzeczywistą ilość pracy zbierającej dane wejściowe i przekazuje ją do przepływu pracy przez wznowienie <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="f2fbd-123">The host application performs the actual work of gathering the input and passes it to the workflow by resuming the <xref:System.Activities.Bookmark>.</span></span>  
  
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
  
 <span data-ttu-id="f2fbd-124">Gdy działanie jest wykonywane, <xref:System.Activities.Bookmark> tworzy nazwę `UserName` , a następnie czeka na wznowienie zakładki. `ReadLine`</span><span class="sxs-lookup"><span data-stu-id="f2fbd-124">When the `ReadLine` activity is executed, it creates a <xref:System.Activities.Bookmark> named `UserName` and then waits for the bookmark to be resumed.</span></span> <span data-ttu-id="f2fbd-125">Host zbiera wymagane dane, a następnie wznawia działanie <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="f2fbd-125">The host collects the desired data and then resumes the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="f2fbd-126">Przepływ pracy zostanie wznowiony, zostanie wyświetlona nazwa, a następnie zostanie zakończona.</span><span class="sxs-lookup"><span data-stu-id="f2fbd-126">The workflow resumes, displays the name, and then completes.</span></span> <span data-ttu-id="f2fbd-127">Należy pamiętać, że żaden kod synchronizacji nie jest wymagany w odniesieniu do wznowienia zakładki.</span><span class="sxs-lookup"><span data-stu-id="f2fbd-127">Note that no synchronization code is required with regard to resuming the bookmark.</span></span> <span data-ttu-id="f2fbd-128">Można wznowić tylko wtedy, gdy przepływ pracy jest bezczynny, a jeśli przepływ pracy nie jest bezczynny <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> , wywołanie bloków do momentu, gdy przepływ pracy przestanie być bezczynny. <xref:System.Activities.Bookmark></span><span class="sxs-lookup"><span data-stu-id="f2fbd-128">A <xref:System.Activities.Bookmark> can only be resumed when the workflow is idle, and if the workflow is not idle, the call to <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> blocks until the workflow becomes idle.</span></span>  
  
## <a name="bookmark-resumption-result"></a><span data-ttu-id="f2fbd-129">Wynik wznowienia zakładki</span><span class="sxs-lookup"><span data-stu-id="f2fbd-129">Bookmark Resumption Result</span></span>  
 <span data-ttu-id="f2fbd-130"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A>Zwraca wartość <xref:System.Activities.BookmarkResumptionResult> wyliczenia wskazującą wyniki żądania wznowienia zakładki.</span><span class="sxs-lookup"><span data-stu-id="f2fbd-130"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> returns a <xref:System.Activities.BookmarkResumptionResult> enumeration value to indicate the results of the bookmark resumption request.</span></span> <span data-ttu-id="f2fbd-131">Możliwe wartości zwracane to <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, i <xref:System.Activities.BookmarkResumptionResult.NotFound>.</span><span class="sxs-lookup"><span data-stu-id="f2fbd-131">The possible return values are <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, and <xref:System.Activities.BookmarkResumptionResult.NotFound>.</span></span> <span data-ttu-id="f2fbd-132">Hosty i rozszerzenia mogą używać tej wartości, aby określić sposób dalszego działania.</span><span class="sxs-lookup"><span data-stu-id="f2fbd-132">Hosts and extensions can use this value to determine how to proceed.</span></span>
