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
# <a name="bookmarks"></a>Zakładki
Zakładki są mechanizmem, który umożliwia działanie pasywnie czekać na dane wejściowe bez przytrzymywać na wątku przepływu pracy. Gdy działanie sygnalizuje, że czeka na bodziec, może utworzyć zakładkę. Wskazuje to do środowiska wykonawczego, że wykonanie działania nie powinny być uważane za kompletne, <xref:System.Activities.Bookmark>nawet wtedy, gdy aktualnie wykonywana metoda (która utworzyła ) zwraca.  
  
## <a name="bookmark-basics"></a>Podstawy do zakładek  
 A <xref:System.Activities.Bookmark> reprezentuje punkt, w którym można wznowić wykonywanie (i za pośrednictwem którego dane wejściowe mogą być dostarczane) w wystąpieniu przepływu pracy. Zazwyczaj <xref:System.Activities.Bookmark> a otrzymuje nazwę i kod zewnętrzny (host lub rozszerzenie) jest odpowiedzialny za wznowienie zakładki z odpowiednimi danymi. Po <xref:System.Activities.Bookmark> wznowieniu środowiska wykonawczego przepływu pracy planuje <xref:System.Activities.BookmarkCallback> delegata, który <xref:System.Activities.Bookmark> był skojarzony z tym w momencie jego tworzenia.  
  
## <a name="bookmark-options"></a>Opcje zakładek  
 Klasa <xref:System.Activities.BookmarkOptions> określa typ tworzonego. <xref:System.Activities.Bookmark> Możliwe wartości niewyłączone wzajemnie <xref:System.Activities.BookmarkOptions.MultipleResume>są <xref:System.Activities.BookmarkOptions.NonBlocking> <xref:System.Activities.BookmarkOptions.None>, i . Użyj <xref:System.Activities.BookmarkOptions.None>, domyślnie, podczas <xref:System.Activities.Bookmark> tworzenia, który ma zostać wznowiony dokładnie raz. Użyj <xref:System.Activities.BookmarkOptions.MultipleResume> podczas tworzenia, <xref:System.Activities.Bookmark> które mogą być wznawiane wiele razy. Użyj <xref:System.Activities.BookmarkOptions.NonBlocking> podczas <xref:System.Activities.Bookmark> tworzenia, które nigdy nie mogą być wznowione. W przeciwieństwie do zakładek <xref:System.Activities.BookmarkOptions> <xref:System.Activities.BookmarkOptions.NonBlocking> utworzonych przy użyciu domyślnych zakładek zakładki nie uniemożliwiają ukończenia działania.  
  
## <a name="bookmark-resumption"></a>Wznowienie zakładek  
 Zakładki mogą być wznawiane przez kod poza <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> przepływem pracy przy użyciu jednego z przeciążeń. W tym przykładzie `ReadLine` tworzone jest działanie. Po wykonaniu `ReadLine` działanie tworzy <xref:System.Activities.Bookmark>, rejestruje wywołanie zwrotne, a <xref:System.Activities.Bookmark> następnie czeka na wznowienie. Po wznowieniu `ReadLine` działanie przypisuje dane, które zostały przekazane <xref:System.Activities.Bookmark> z <xref:System.Activities.Activity%601.Result%2A> argumentem.  
  
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
  
 W tym przykładzie tworzony jest przepływ `ReadLine` pracy, który używa działania do zbierania nazwy użytkownika i wyświetlania go w oknie konsoli. Aplikacja hosta wykonuje rzeczywistą pracę zbierania danych wejściowych i przekazuje go <xref:System.Activities.Bookmark>do przepływu pracy, wznawiając program .  
  
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
  
 Po `ReadLine` wykonaniu działania tworzy <xref:System.Activities.Bookmark> nazwę `UserName` o nazwie, a następnie czeka na zakładkę do wznowienia. Host zbiera żądane dane, a <xref:System.Activities.Bookmark>następnie wznawia program . Przepływ pracy zostanie wznowiony, wyświetli nazwę, a następnie zakończy pracę. Należy zauważyć, że nie jest wymagany kod synchronizacji w odniesieniu do wznowienia zakładki. A <xref:System.Activities.Bookmark> można wznowić tylko wtedy, gdy przepływ pracy jest bezczynny, a jeśli przepływ <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> pracy nie jest bezczynny, wywołanie blokuje, dopóki przepływ pracy nie stanie się bezczynny.  
  
## <a name="bookmark-resumption-result"></a>Wynik wznowienia zakładki  
 <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A>zwraca <xref:System.Activities.BookmarkResumptionResult> wartość wyliczenia, aby wskazać wyniki żądania wznowienia zakładki. Możliwe wartości zwracane <xref:System.Activities.BookmarkResumptionResult.NotReady>to <xref:System.Activities.BookmarkResumptionResult.NotFound> <xref:System.Activities.BookmarkResumptionResult.Success>, i . Hosty i rozszerzenia można użyć tej wartości, aby określić, jak postępować.
