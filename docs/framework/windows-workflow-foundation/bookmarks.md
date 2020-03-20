---
title: Zakładki - WF
ms.date: 03/30/2017
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
ms.openlocfilehash: c5bd8130ee623599e80014777baf92986c3b6969
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183009"
---
# <a name="bookmarks"></a><span data-ttu-id="11ea3-102">Zakładki</span><span class="sxs-lookup"><span data-stu-id="11ea3-102">Bookmarks</span></span>
<span data-ttu-id="11ea3-103">Zakładki są mechanizmem, który umożliwia działanie pasywnie czekać na dane wejściowe bez przytrzymywać na wątku przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="11ea3-103">Bookmarks are the mechanism that enables an activity to passively wait for input without holding onto a workflow thread.</span></span> <span data-ttu-id="11ea3-104">Gdy działanie sygnalizuje, że czeka na bodziec, może utworzyć zakładkę.</span><span class="sxs-lookup"><span data-stu-id="11ea3-104">When an activity signals that it is waiting for stimulus, it can create a bookmark.</span></span> <span data-ttu-id="11ea3-105">Wskazuje to do środowiska wykonawczego, że wykonanie działania nie powinny być uważane za kompletne, <xref:System.Activities.Bookmark>nawet wtedy, gdy aktualnie wykonywana metoda (która utworzyła ) zwraca.</span><span class="sxs-lookup"><span data-stu-id="11ea3-105">This indicates to the runtime that the activity’s execution should not be considered complete even when the currently executing method (which created the <xref:System.Activities.Bookmark>) returns.</span></span>  
  
## <a name="bookmark-basics"></a><span data-ttu-id="11ea3-106">Podstawy do zakładek</span><span class="sxs-lookup"><span data-stu-id="11ea3-106">Bookmark Basics</span></span>  
 <span data-ttu-id="11ea3-107">A <xref:System.Activities.Bookmark> reprezentuje punkt, w którym można wznowić wykonywanie (i za pośrednictwem którego dane wejściowe mogą być dostarczane) w wystąpieniu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="11ea3-107">A <xref:System.Activities.Bookmark> represents a point at which execution can be resumed (and through which input can be delivered) within a workflow instance.</span></span> <span data-ttu-id="11ea3-108">Zazwyczaj <xref:System.Activities.Bookmark> a otrzymuje nazwę i kod zewnętrzny (host lub rozszerzenie) jest odpowiedzialny za wznowienie zakładki z odpowiednimi danymi.</span><span class="sxs-lookup"><span data-stu-id="11ea3-108">Typically, a <xref:System.Activities.Bookmark> is given a name and external (host or extension) code is responsible for resuming the bookmark with relevant data.</span></span> <span data-ttu-id="11ea3-109">Po <xref:System.Activities.Bookmark> wznowieniu środowiska wykonawczego przepływu pracy planuje <xref:System.Activities.BookmarkCallback> delegata, który <xref:System.Activities.Bookmark> był skojarzony z tym w momencie jego tworzenia.</span><span class="sxs-lookup"><span data-stu-id="11ea3-109">When a <xref:System.Activities.Bookmark> is resumed, the workflow runtime schedules the <xref:System.Activities.BookmarkCallback> delegate that was associated with that <xref:System.Activities.Bookmark> at the time of its creation.</span></span>  
  
## <a name="bookmark-options"></a><span data-ttu-id="11ea3-110">Opcje zakładek</span><span class="sxs-lookup"><span data-stu-id="11ea3-110">Bookmark Options</span></span>  
 <span data-ttu-id="11ea3-111">Klasa <xref:System.Activities.BookmarkOptions> określa typ tworzonego. <xref:System.Activities.Bookmark></span><span class="sxs-lookup"><span data-stu-id="11ea3-111">The <xref:System.Activities.BookmarkOptions> class specifies the type of <xref:System.Activities.Bookmark> being created.</span></span> <span data-ttu-id="11ea3-112">Możliwe wartości niewyłączone wzajemnie <xref:System.Activities.BookmarkOptions.MultipleResume>są <xref:System.Activities.BookmarkOptions.NonBlocking> <xref:System.Activities.BookmarkOptions.None>, i .</span><span class="sxs-lookup"><span data-stu-id="11ea3-112">The possible non mutually-exclusive values are <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, and <xref:System.Activities.BookmarkOptions.NonBlocking>.</span></span> <span data-ttu-id="11ea3-113">Użyj <xref:System.Activities.BookmarkOptions.None>, domyślnie, podczas <xref:System.Activities.Bookmark> tworzenia, który ma zostać wznowiony dokładnie raz.</span><span class="sxs-lookup"><span data-stu-id="11ea3-113">Use <xref:System.Activities.BookmarkOptions.None>, the default, when creating a <xref:System.Activities.Bookmark> that is expected to be resumed exactly once.</span></span> <span data-ttu-id="11ea3-114">Użyj <xref:System.Activities.BookmarkOptions.MultipleResume> podczas tworzenia, <xref:System.Activities.Bookmark> które mogą być wznawiane wiele razy.</span><span class="sxs-lookup"><span data-stu-id="11ea3-114">Use <xref:System.Activities.BookmarkOptions.MultipleResume> when creating a <xref:System.Activities.Bookmark> that can be resumed multiple times.</span></span> <span data-ttu-id="11ea3-115">Użyj <xref:System.Activities.BookmarkOptions.NonBlocking> podczas <xref:System.Activities.Bookmark> tworzenia, które nigdy nie mogą być wznowione.</span><span class="sxs-lookup"><span data-stu-id="11ea3-115">Use <xref:System.Activities.BookmarkOptions.NonBlocking> when creating a <xref:System.Activities.Bookmark> that might never be resumed.</span></span> <span data-ttu-id="11ea3-116">W przeciwieństwie do zakładek <xref:System.Activities.BookmarkOptions> <xref:System.Activities.BookmarkOptions.NonBlocking> utworzonych przy użyciu domyślnych zakładek zakładki nie uniemożliwiają ukończenia działania.</span><span class="sxs-lookup"><span data-stu-id="11ea3-116">Unlike bookmarks created using the default <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> bookmarks do not prevent an activity from completing.</span></span>  
  
## <a name="bookmark-resumption"></a><span data-ttu-id="11ea3-117">Wznowienie zakładek</span><span class="sxs-lookup"><span data-stu-id="11ea3-117">Bookmark Resumption</span></span>  
 <span data-ttu-id="11ea3-118">Zakładki mogą być wznawiane przez kod poza <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> przepływem pracy przy użyciu jednego z przeciążeń.</span><span class="sxs-lookup"><span data-stu-id="11ea3-118">Bookmarks can be resumed by code outside of a workflow using one of the <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> overloads.</span></span> <span data-ttu-id="11ea3-119">W tym przykładzie `ReadLine` tworzone jest działanie.</span><span class="sxs-lookup"><span data-stu-id="11ea3-119">In this example, a `ReadLine` activity is created.</span></span> <span data-ttu-id="11ea3-120">Po wykonaniu `ReadLine` działanie tworzy <xref:System.Activities.Bookmark>, rejestruje wywołanie zwrotne, a <xref:System.Activities.Bookmark> następnie czeka na wznowienie.</span><span class="sxs-lookup"><span data-stu-id="11ea3-120">When executed, the `ReadLine` activity creates a <xref:System.Activities.Bookmark>, registers a callback, and then waits for the <xref:System.Activities.Bookmark> to be resumed.</span></span> <span data-ttu-id="11ea3-121">Po wznowieniu `ReadLine` działanie przypisuje dane, które zostały przekazane <xref:System.Activities.Bookmark> z <xref:System.Activities.Activity%601.Result%2A> argumentem.</span><span class="sxs-lookup"><span data-stu-id="11ea3-121">When it is resumed, the `ReadLine` activity assigns the data that was passed with the <xref:System.Activities.Bookmark> to its <xref:System.Activities.Activity%601.Result%2A> argument.</span></span>  
  
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
  
 <span data-ttu-id="11ea3-122">W tym przykładzie tworzony jest przepływ `ReadLine` pracy, który używa działania do zbierania nazwy użytkownika i wyświetlania go w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="11ea3-122">In this example, a workflow is created that uses the `ReadLine` activity to gather the user’s name and display it to the console window.</span></span> <span data-ttu-id="11ea3-123">Aplikacja hosta wykonuje rzeczywistą pracę zbierania danych wejściowych i przekazuje go <xref:System.Activities.Bookmark>do przepływu pracy, wznawiając program .</span><span class="sxs-lookup"><span data-stu-id="11ea3-123">The host application performs the actual work of gathering the input and passes it to the workflow by resuming the <xref:System.Activities.Bookmark>.</span></span>  
  
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
  
 <span data-ttu-id="11ea3-124">Po `ReadLine` wykonaniu działania tworzy <xref:System.Activities.Bookmark> nazwę `UserName` o nazwie, a następnie czeka na zakładkę do wznowienia.</span><span class="sxs-lookup"><span data-stu-id="11ea3-124">When the `ReadLine` activity is executed, it creates a <xref:System.Activities.Bookmark> named `UserName` and then waits for the bookmark to be resumed.</span></span> <span data-ttu-id="11ea3-125">Host zbiera żądane dane, a <xref:System.Activities.Bookmark>następnie wznawia program .</span><span class="sxs-lookup"><span data-stu-id="11ea3-125">The host collects the desired data and then resumes the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="11ea3-126">Przepływ pracy zostanie wznowiony, wyświetli nazwę, a następnie zakończy pracę.</span><span class="sxs-lookup"><span data-stu-id="11ea3-126">The workflow resumes, displays the name, and then completes.</span></span> <span data-ttu-id="11ea3-127">Należy zauważyć, że nie jest wymagany kod synchronizacji w odniesieniu do wznowienia zakładki.</span><span class="sxs-lookup"><span data-stu-id="11ea3-127">Note that no synchronization code is required with regard to resuming the bookmark.</span></span> <span data-ttu-id="11ea3-128">A <xref:System.Activities.Bookmark> można wznowić tylko wtedy, gdy przepływ pracy jest bezczynny, a jeśli przepływ <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> pracy nie jest bezczynny, wywołanie blokuje, dopóki przepływ pracy nie stanie się bezczynny.</span><span class="sxs-lookup"><span data-stu-id="11ea3-128">A <xref:System.Activities.Bookmark> can only be resumed when the workflow is idle, and if the workflow is not idle, the call to <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> blocks until the workflow becomes idle.</span></span>  
  
## <a name="bookmark-resumption-result"></a><span data-ttu-id="11ea3-129">Wynik wznowienia zakładki</span><span class="sxs-lookup"><span data-stu-id="11ea3-129">Bookmark Resumption Result</span></span>  
 <span data-ttu-id="11ea3-130"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A>zwraca <xref:System.Activities.BookmarkResumptionResult> wartość wyliczenia, aby wskazać wyniki żądania wznowienia zakładki.</span><span class="sxs-lookup"><span data-stu-id="11ea3-130"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> returns a <xref:System.Activities.BookmarkResumptionResult> enumeration value to indicate the results of the bookmark resumption request.</span></span> <span data-ttu-id="11ea3-131">Możliwe wartości zwracane <xref:System.Activities.BookmarkResumptionResult.NotReady>to <xref:System.Activities.BookmarkResumptionResult.NotFound> <xref:System.Activities.BookmarkResumptionResult.Success>, i .</span><span class="sxs-lookup"><span data-stu-id="11ea3-131">The possible return values are <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, and <xref:System.Activities.BookmarkResumptionResult.NotFound>.</span></span> <span data-ttu-id="11ea3-132">Hosty i rozszerzenia można użyć tej wartości, aby określić, jak postępować.</span><span class="sxs-lookup"><span data-stu-id="11ea3-132">Hosts and extensions can use this value to determine how to proceed.</span></span>
