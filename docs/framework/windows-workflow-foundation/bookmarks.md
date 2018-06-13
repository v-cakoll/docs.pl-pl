---
title: Bookmarks1
ms.date: 03/30/2017
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
ms.openlocfilehash: 8b7ca9549327087e30d6c72a8b784aa37ad09f3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515571"
---
# <a name="bookmarks"></a>Zakładki
Zakładki są mechanizm, który umożliwia działanie pasywnie oczekiwania na dane wejściowe nieposiadających na wątku przepływu pracy. Gdy działanie sygnalizuje, że oczekuje bodźca, może utworzyć zakładki. Oznacza to środowisko uruchomieniowe czy wykonanie działania nie należy traktować jako pełną nawet wtedy, gdy aktualnie wykonywane — metoda (który utworzony <xref:System.Activities.Bookmark>) zwraca.  
  
## <a name="bookmark-basics"></a>Podstawy zakładki  
 A <xref:System.Activities.Bookmark> reprezentuje punkt, w których wykonanie może wznowić (oraz za pośrednictwem których dane wejściowe mogą być dostarczane) w ramach wystąpienia przepływu pracy. Zazwyczaj <xref:System.Activities.Bookmark> podano nazwę i kod zewnętrzny (host lub rozszerzenia) jest odpowiedzialny za wznawianie zakładki z właściwymi danymi. Gdy <xref:System.Activities.Bookmark> zostanie wznowione, harmonogramy środowiska uruchomieniowego przepływu pracy <xref:System.Activities.BookmarkCallback> delegata, który został skojarzony z tym <xref:System.Activities.Bookmark> w momencie jego tworzenia.  
  
## <a name="bookmark-options"></a>Opcje zakładki  
 <xref:System.Activities.BookmarkOptions> Klasy określa typ <xref:System.Activities.Bookmark> tworzona. Możliwe wartości innych niż wzajemnie wykluczającymi się <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, i <xref:System.Activities.BookmarkOptions.NonBlocking>. Użyj <xref:System.Activities.BookmarkOptions.None>, wartość domyślna, tworząc <xref:System.Activities.Bookmark> zgodnie z oczekiwaniami można wznowić tylko raz. Użyj <xref:System.Activities.BookmarkOptions.MultipleResume> podczas tworzenia <xref:System.Activities.Bookmark> który może zostać wznowiony wiele razy. Użyj <xref:System.Activities.BookmarkOptions.NonBlocking> podczas tworzenia <xref:System.Activities.Bookmark> który nigdy nie może zostać wznowiony. W przeciwieństwie do zakładki utworzone przy użyciu domyślnego <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> zakładek nie uniemożliwiają ukończenie działania.  
  
## <a name="bookmark-resumption"></a>Wznowienie zakładki  
 Zakładki może wznowić przez kod poza przepływu pracy przy użyciu jednej z <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> przeciążenia. W tym przykładzie `ReadLine` utworzeniu działania. Po wykonaniu `ReadLine` działanie tworzy <xref:System.Activities.Bookmark>, rejestruje wywołanie zwrotne, a następnie oczekiwanie <xref:System.Activities.Bookmark> wznowienie zadania było. Gdy zostanie wznowione, `ReadLine` działania przypisuje danych, który został przekazany z <xref:System.Activities.Bookmark> do jego <xref:System.Activities.Activity%601.Result%2A> argumentu.  
  
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
  
 W tym przykładzie przepływ pracy jest tworzony, który używa `ReadLine` działania zebranie nazwy użytkownika i wyświetlić je w oknie konsoli. Aplikacja hosta wykonuje faktyczną pracę zbierania danych wejściowych i przekazuje je do przepływu pracy przez wznawianie <xref:System.Activities.Bookmark>.  
  
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
  
 Gdy `ReadLine` działania jest wykonywana, tworzy <xref:System.Activities.Bookmark> o nazwie `UserName` , a następnie oczekiwanie zakładki wznowienie zadania było. Zbiera dane żądanego hosta, a następnie kontynuowanie <xref:System.Activities.Bookmark>. Przepływ pracy wznawia, wyświetla nazwę, a następnie kończy. Należy pamiętać, że żaden kod synchronizacji jest wymagana w odniesieniu do wznawiania działania zakładki. A <xref:System.Activities.Bookmark> można wznowić tylko wtedy, gdy przepływ pracy jest bezczynny, a jeśli przepływ pracy nie jest w stanie bezczynności, wywołanie <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> blokuje aż przepływ pracy stanie bezczynności.  
  
## <a name="bookmark-resumption-result"></a>Wynik wznowienie zakładki  
 <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> Zwraca <xref:System.Activities.BookmarkResumptionResult> wartość wyliczenia wskazująca wyniki żądania wznowienia zakładki. Możliwe wartości zwracane są <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, i <xref:System.Activities.BookmarkResumptionResult.NotFound>. Tej wartości można użyć hostów i rozszerzenia do określania, jak kontynuować.
