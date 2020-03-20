---
title: Używanie obiektu WorkflowInvoker i WorkflowApplication
ms.date: 03/30/2017
ms.assetid: cd0e583c-a3f9-4fa2-b247-c7b3368c48a7
ms.openlocfilehash: 5d09fc3c902b1993b32edf3e9f92393433281636
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182705"
---
# <a name="using-workflowinvoker-and-workflowapplication"></a>Używanie obiektu WorkflowInvoker i WorkflowApplication
Windows Workflow Foundation (WF) udostępnia kilka metod hostingu przepływów pracy. <xref:System.Activities.WorkflowInvoker>zapewnia prosty sposób wywoływania przepływu pracy tak, jakby był wywołaniem metody i może być używany tylko dla przepływów pracy, które nie używają trwałości. <xref:System.Activities.WorkflowApplication>zapewnia bogatszy model do wykonywania przepływów pracy, który obejmuje powiadamianie o zdarzeniach cyklu życia, kontroli wykonania, wznowienie zakładki i trwałość. <xref:System.ServiceModel.Activities.WorkflowServiceHost>zapewnia obsługę działań obsługi wiadomości i jest używany głównie z usługami przepływu pracy. W tym temacie przedstawiono hosting <xref:System.Activities.WorkflowInvoker> <xref:System.Activities.WorkflowApplication>przepływu pracy z i . Aby uzyskać więcej informacji na <xref:System.ServiceModel.Activities.WorkflowServiceHost>temat hostingu przepływów pracy za pomocą , zobacz [Omówienie usług przepływu pracy](../wcf/feature-details/workflow-services.md) i [hostingu](../wcf/feature-details/hosting-workflow-services-overview.md).  
  
## <a name="using-workflowinvoker"></a>Korzystanie z funkcji WorkflowInvoker  
 <xref:System.Activities.WorkflowInvoker>udostępnia model do wykonywania przepływu pracy, tak jakby był wywołanie metody. Aby wywołać przepływ <xref:System.Activities.WorkflowInvoker>pracy przy <xref:System.Activities.WorkflowInvoker.Invoke%2A> użyciu , wywołać metodę i przekazać w definicji przepływu pracy przepływu pracy do wywołania. W tym przykładzie <xref:System.Activities.Statements.WriteLine> działanie jest <xref:System.Activities.WorkflowInvoker>wywoływane przy użyciu .  
  
 [!code-csharp[CFX_WorkflowInvokerExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#1)]  
  
 Gdy przepływ pracy jest <xref:System.Activities.WorkflowInvoker>wywoływany przy użyciu, przepływ pracy <xref:System.Activities.WorkflowInvoker.Invoke%2A> jest wykonywany w wątku wywołującym, a metoda blokuje się do czasu zakończenia przepływu pracy, w tym czasu bezczynności. Aby skonfigurować limit czasu, w którym przepływ pracy musi <xref:System.Activities.WorkflowInvoker.Invoke%2A> zostać ukończony, <xref:System.TimeSpan> należy użyć jednego z przeciążeń, który przyjmuje parametr. W tym przykładzie przepływ pracy jest wywoływany dwa razy z dwoma różnymi interwałami przesuwu. Pierwszy przepływ pracy jest ujedkwący, ale drugi nie.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#50](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#50)]  
  
> [!NOTE]
> Jest <xref:System.TimeoutException> wyrzucany tylko wtedy, gdy upłynie interwał przekroju czasu i przepływ pracy staje się bezczynny podczas wykonywania. Przepływ pracy, który trwa dłużej niż określony przedział czasu, aby zakończyć pomyślnie, jeśli przepływ pracy nie staje się bezczynny.  
  
 <xref:System.Activities.WorkflowInvoker>zapewnia również asynchroniczne wersje metody invoke. Aby uzyskać więcej informacji, zobacz <xref:System.Activities.WorkflowInvoker.InvokeAsync%2A> i <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A>.  
  
### <a name="setting-input-arguments-of-a-workflow"></a>Ustawianie argumentów wejściowych przepływu pracy  
 Dane mogą być przekazywane do przepływu pracy przy użyciu słownika parametrów wejściowych, wpisane według nazwy argumentu, które mapują do argumentów wejściowych przepływu pracy. W tym przykładzie <xref:System.Activities.Statements.WriteLine> jest wywoływana i <xref:System.Activities.Statements.WriteLine.Text%2A> wartość jego argument jest określona przy użyciu słownika parametrów wejściowych.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#3)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>Pobieranie argumentów wyjściowych przepływu pracy  
 Parametry wyjściowe przepływu pracy można uzyskać za pomocą słownika wyjść, <xref:System.Activities.WorkflowInvoker.Invoke%2A>który jest zwracany z wywołania do . Poniższy przykład wywołuje przepływ pracy składający się z pojedynczego `Divide` działania, które ma dwa argumenty wejściowe i dwa argumenty wyjściowe. Po wywołaniu przepływu `arguments` pracy, słownik jest przekazywany, który zawiera wartości dla każdego argumentu wejściowego, wpisane według nazwy argumentu. Gdy wywołanie `Invoke` zwraca, każdy argument danych `outputs` wyjściowych jest zwracany w słowniku, również wpisane według nazwy argumentu.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#120](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#120)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#20](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#20)]  
  
 Jeśli przepływ pracy pochodzi <xref:System.Activities.ActivityWithResult>od `CodeActivity<TResult>` , `Activity<TResult>`takich jak lub , i istnieją <xref:System.Activities.Activity%601.Result%2A> argumenty wyjściowe oprócz dobrze zdefiniowanego argumentu wyjściowego, `Invoke` nieogólne przeciążenie musi być używane w celu pobrania dodatkowych argumentów. Aby to zrobić, definicja `Invoke` przepływu pracy <xref:System.Activities.Activity>przekazywana do musi być typu . W tym `Divide` przykładzie działanie `CodeActivity<int>`pochodzi od <xref:System.Activities.Activity> , ale jest zadeklarowany `Invoke` jako tak, że niegeneryczne przeciążenie jest używany, który zwraca słownik argumentów zamiast pojedynczej wartości zwracanej.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#121](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#121)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#21](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#21)]  
  
## <a name="using-workflowapplication"></a>Korzystanie z aplikacji przepływu pracy  
 <xref:System.Activities.WorkflowApplication>zapewnia bogaty zestaw funkcji do zarządzania wystąpieniami przepływu pracy. <xref:System.Activities.WorkflowApplication>działa jako serwer proxy bezpiecznego <xref:System.Activities.Hosting.WorkflowInstance>wątku do rzeczywistego , który hermetyzuje środowisko uruchomieniowe i udostępnia metody tworzenia i ładowania wystąpień przepływu pracy, wstrzymywania i wznawiania, kończenia i powiadamiania o zdarzeniach cyklu życia. Aby uruchomić przepływ <xref:System.Activities.WorkflowApplication> pracy przy <xref:System.Activities.WorkflowApplication>użyciu tworzenia , subskrybować żądane zdarzenia cyklu życia, uruchom przepływ pracy, a następnie poczekaj na jego zakończenie. W tym przykładzie tworzona jest <xref:System.Activities.Statements.WriteLine> definicja przepływu <xref:System.Activities.WorkflowApplication> pracy, która składa się z działania i jest tworzona przy użyciu określonej definicji przepływu pracy. <xref:System.Activities.WorkflowApplication.Completed%2A>jest obsługiwany, więc host jest powiadamiany po zakończeniu przepływu pracy, przepływ <xref:System.Activities.WorkflowApplication.Run%2A>pracy jest uruchamiany z wywołaniem do , a następnie host czeka na zakończenie przepływu pracy. Po zakończeniu przepływu pracy <xref:System.Threading.AutoResetEvent> jest ustawiona i aplikacja hosta można wznowić wykonywanie, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#31](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#31)]  
  
### <a name="workflowapplication-lifecycle-events"></a>Zdarzenia cyklu życia przepływu pracy  
 Oprócz <xref:System.Activities.WorkflowApplication.Completed%2A>, autorzy hosta mogą być powiadamiani,<xref:System.Activities.WorkflowApplication.Unloaded%2A>gdy przepływ pracy<xref:System.Activities.WorkflowApplication.Aborted%2A>jest rozładowywany ( ), przerywany ( ), staje się bezczynny (<xref:System.Activities.WorkflowApplication.Idle%2A> i <xref:System.Activities.WorkflowApplication.PersistableIdle%2A>), lub występuje nieobsługiwany wyjątek (<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>). Deweloperzy aplikacji przepływu pracy mogą obsługiwać te powiadomienia i podejmować odpowiednie działania, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#32](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#32)]  
  
### <a name="setting-input-arguments-of-a-workflow"></a>Ustawianie argumentów wejściowych przepływu pracy  
 Dane mogą być przekazywane do przepływu pracy, ponieważ jest uruchamiany przy użyciu słownika <xref:System.Activities.WorkflowInvoker>parametrów, podobnie jak dane są przekazywane podczas korzystania . Każdy element w słowniku jest mapowana na argument wejściowy określonego przepływu pracy. W tym przykładzie przepływ pracy, <xref:System.Activities.Statements.WriteLine> który składa się <xref:System.Activities.Statements.WriteLine.Text%2A> z działania jest wywoływany, a jego argument jest określony przy użyciu słownika parametrów wejściowych.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#30](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#30)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>Pobieranie argumentów wyjściowych przepływu pracy  
 Po zakończeniu przepływu pracy wszystkie argumenty wyjściowe można <xref:System.Activities.WorkflowApplication.Completed%2A> pobrać w <xref:System.Activities.WorkflowApplicationCompletedEventArgs.Outputs%2A?displayProperty=nameWithType> programie obsługi, uzyskując dostęp do słownika. W poniższym przykładzie <xref:System.Activities.WorkflowApplication>znajduje się przepływ pracy przy użyciu programu . Wystąpienie <xref:System.Activities.WorkflowApplication> jest konstruowane przy użyciu definicji przepływu pracy składającej się z pojedynczego `DiceRoll` działania. Działanie `DiceRoll` ma dwa argumenty wyjściowe, które reprezentują wyniki operacji rzutu kości. Po zakończeniu przepływu pracy dane wyjściowe są <xref:System.Activities.WorkflowApplication.Completed%2A> pobierane w programie obsługi.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#130](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#130)]  
  
 [!code-csharp[CFX_WorkflowApplicationExample#21](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#21)]  
  
> [!NOTE]
> <xref:System.Activities.WorkflowApplication>i <xref:System.Activities.WorkflowInvoker> weź słownik argumentów wejściowych i `out` zwróć słownik argumentów. Te parametry słownika, właściwości i zwracane `IDictionary<string, object>`wartości są typu . Rzeczywiste wystąpienie klasy słownika, która jest przekazywana `IDictionary<string, object>`w może być dowolna klasa, która implementuje . W tych przykładach `Dictionary<string, object>` jest używany. Aby uzyskać więcej informacji <xref:System.Collections.Generic.IDictionary%602> o <xref:System.Collections.Generic.Dictionary%602>słownikach, zobacz i .  
  
### <a name="passing-data-into-a-running-workflow-using-bookmarks"></a>Przekazywanie danych do uruchomionego przepływu pracy przy użyciu zakładek  
 Zakładki są mechanizm, za pomocą którego działanie można pasywnie czekać na wznowienie i są mechanizm przekazywania danych do uruchomionego wystąpienia przepływu pracy. Jeśli działanie oczekuje na dane, można <xref:System.Activities.Bookmark> utworzyć i zarejestrować metodę wywołania <xref:System.Activities.Bookmark> zwrotnego, która ma być wywoływana po wznowieniu, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
 Po wykonaniu `ReadLine` działanie tworzy <xref:System.Activities.Bookmark>, rejestruje wywołanie zwrotne, a <xref:System.Activities.Bookmark> następnie czeka na wznowienie. Po wznowieniu `ReadLine` działanie przypisuje dane, które zostały przekazane <xref:System.Activities.Bookmark> z <xref:System.Activities.Activity%601.Result%2A> argumentem. W tym przykładzie tworzony jest przepływ `ReadLine` pracy, który używa działania do zbierania nazwy użytkownika i wyświetlania go w oknie konsoli.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#22](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#22)]  
  
 Po `ReadLine` wykonaniu działania tworzy <xref:System.Activities.Bookmark> nazwę `UserName` o nazwie, a następnie czeka na zakładkę do wznowienia. Host zbiera żądane dane, a <xref:System.Activities.Bookmark>następnie wznawia program . Przepływ pracy zostanie wznowiony, wyświetli nazwę, a następnie zakończy pracę.  
  
 Aplikacja hosta można sprawdzić przepływu pracy, aby ustalić, czy istnieją aktywne zakładki. Można to zrobić, <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> wywołując metodę <xref:System.Activities.WorkflowApplication> wystąpienia lub sprawdzając <xref:System.Activities.WorkflowApplicationIdleEventArgs> w <xref:System.Activities.WorkflowApplication.Idle%2A> programie obsługi.  
  
 Poniższy przykład kodu jest podobny do poprzedniego przykładu, z tą różnicą, że aktywne zakładki są wyliczone przed wznowieniem zakładki. Przepływ pracy jest uruchamiany, <xref:System.Activities.Bookmark> a po utworzeniu i przepływ <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> pracy przechodzi bezczynności, jest wywoływana. Po zakończeniu przepływu pracy do konsoli są wyświetlane następujące dane wyjściowe.  
  
 **Jak się nazywasz?**  
**Nazwa zakładki: Nazwa użytkownika - OwnerDisplayName: ReadLine**
**Steve**
**Hello, Steve**

[!code-csharp[CFX_WorkflowApplicationExample#14](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#14)]  
  
 Poniższy przykład kodu <xref:System.Activities.WorkflowApplicationIdleEventArgs> sprawdza przekazywane <xref:System.Activities.WorkflowApplication.Idle%2A> do <xref:System.Activities.WorkflowApplication> obsługi wystąpienia. W tym przykładzie przepływ pracy będzie <xref:System.Activities.Bookmark> bezczynny `EnterGuess`ma jeden z `ReadInt`nazwą , własnością działania o nazwie . W tym przykładzie kodu jest oparty na [jak: Uruchom przepływ pracy](how-to-run-a-workflow.md), który jest częścią [samouczek Wprowadzenie](getting-started-tutorial.md). Jeśli <xref:System.Activities.WorkflowApplication.Idle%2A> program obsługi w tym kroku jest modyfikowany, aby zawierał kod z tego przykładu, wyświetlane są następujące dane wyjściowe.  
  
 **Nazwa zakładki: EnterGuess - OwnerDisplayName: ReadInt**

 [!code-csharp[CFX_WorkflowApplicationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#2)]  
  
## <a name="summary"></a>Podsumowanie  
 <xref:System.Activities.WorkflowInvoker>zapewnia lekki sposób wywoływania przepływów pracy i chociaż udostępnia metody przekazywania danych na początku przepływu pracy i wyodrębniania danych z ukończonego przepływu <xref:System.Activities.WorkflowApplication> pracy, nie zapewnia bardziej złożonych scenariuszy, które są tam, gdzie można użyć.
