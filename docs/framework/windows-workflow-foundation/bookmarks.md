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
# <a name="bookmarks"></a>Zakładki
Zakładki są mechanizm, który umożliwia działanie pasywnie czeka na dane wejściowe bez przytrzymywania na wątku przepływu pracy. Gdy działanie sygnalizuje, że trwa oczekiwanie bodziec, może utworzyć zakładki. Oznacza to, aby środowisko uruchomieniowe, wykonanie tego działania nie powinny być uwzględniane pełną nawet wtedy, gdy aktualnie wykonywanej metody (którym utworzono <xref:System.Activities.Bookmark>) zwraca.  
  
## <a name="bookmark-basics"></a>Podstawowe informacje dotyczące zakładki  
 A <xref:System.Activities.Bookmark> reprezentuje punkt, w których wykonanie można wznowić (za pośrednictwem których dane wejściowe mogą być dostarczane) w ramach wystąpienie przepływu pracy. Zazwyczaj <xref:System.Activities.Bookmark> jest nadawana nazwa i kod zewnętrzny (hosta lub rozszerzeniu) jest odpowiedzialny za wznowienie zakładki z odpowiednimi danymi. Gdy <xref:System.Activities.Bookmark> zostanie wznowione, harmonogramy środowiska uruchomieniowego przepływu pracy <xref:System.Activities.BookmarkCallback> delegat, który został skojarzony z tym <xref:System.Activities.Bookmark> w czasie jego tworzenia.  
  
## <a name="bookmark-options"></a>Opcje zakładek  
 <xref:System.Activities.BookmarkOptions> Klasy określa typ <xref:System.Activities.Bookmark> tworzona. Możliwe wartości inne niż wzajemnie wykluczającymi się <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, i <xref:System.Activities.BookmarkOptions.NonBlocking>. Użyj <xref:System.Activities.BookmarkOptions.None>, domyślnie, podczas tworzenia <xref:System.Activities.Bookmark> zgodnie z oczekiwaniami można wznowić dokładnie jeden raz. Użyj <xref:System.Activities.BookmarkOptions.MultipleResume> podczas tworzenia <xref:System.Activities.Bookmark> , może być wznowione wiele razy. Użyj <xref:System.Activities.BookmarkOptions.NonBlocking> podczas tworzenia <xref:System.Activities.Bookmark> , nigdy nie może być wznowione. W przeciwieństwie do zakładki utworzone przy użyciu domyślnego <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> zakładki uniemożliwia ukończenie działania.  
  
## <a name="bookmark-resumption"></a>Wznowienie zakładki  
 Zakładki, może być wznowione przez kod poza przepływu pracy przy użyciu jednej z <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> przeciążenia. W tym przykładzie `ReadLine` utworzeniu działania. Po wykonaniu `ReadLine` tworzy działanie <xref:System.Activities.Bookmark>, rejestruje wywołanie zwrotne, a następnie czeka na <xref:System.Activities.Bookmark> wznowienie. Gdy zostanie wznowione, `ReadLine` działania przypisuje danych, który został przekazany z <xref:System.Activities.Bookmark> do jego <xref:System.Activities.Activity%601.Result%2A> argumentu.  
  
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
  
 W tym przykładzie przepływ pracy jest tworzony, który używa `ReadLine` działanie, aby zbierać nazwy użytkownika i wyświetl ją w oknie konsoli. Aplikacja hosta wykonuje rzeczywistą pracę zbierania danych wejściowych i przekazuje je do przepływu pracy przez wznawianie <xref:System.Activities.Bookmark>.  
  
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
  
 Gdy `ReadLine` jest wykonywane działanie, tworzy on <xref:System.Activities.Bookmark> o nazwie `UserName` , a następnie czeka zakładki wznowienie. Zbiera dane żądanego hosta, a następnie kontynuowanie <xref:System.Activities.Bookmark>. Przepływ pracy zostanie wznowione, wyświetla nazwę, a następnie kończy. Zwróć uwagę, że żaden kod synchronizacji wymagane w odniesieniu do wznowienie zakładki. A <xref:System.Activities.Bookmark> można wznowić tylko wtedy, gdy przepływ pracy jest bezczynny, i jeśli przepływ pracy nie jest bezczynny, wywołanie <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> blokuje, aż przepływu pracy staje się nieaktywna.  
  
## <a name="bookmark-resumption-result"></a>Wynik wznowienie zakładki  
 <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> Zwraca <xref:System.Activities.BookmarkResumptionResult> wartości wyliczenia, aby wskazać wyniki żądania wznowienie zakładki. Możliwe wartości zwracane są <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, i <xref:System.Activities.BookmarkResumptionResult.NotFound>. Tej wartości można użyć hostów i rozszerzenia do określenia, jak można kontynuować.
