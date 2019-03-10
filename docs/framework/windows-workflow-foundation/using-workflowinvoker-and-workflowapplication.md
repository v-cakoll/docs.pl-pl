---
title: Używanie obiektu WorkflowInvoker i WorkflowApplication
ms.date: 03/30/2017
ms.assetid: cd0e583c-a3f9-4fa2-b247-c7b3368c48a7
ms.openlocfilehash: 29d152cd6011fb3b55aae60726d095dc44dd23a5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707693"
---
# <a name="using-workflowinvoker-and-workflowapplication"></a>Używanie obiektu WorkflowInvoker i WorkflowApplication
Windows Workflow Foundation (WF) udostępnia kilka metod obsługi przepływów pracy. <xref:System.Activities.WorkflowInvoker> zapewnia prostą metodę do wywołania przepływu pracy tak, jakby były wywołania metody i mogą służyć tylko w przypadku przepływów pracy, które nie korzystają z trwałości. <xref:System.Activities.WorkflowApplication> udostępnia bogatszy model do wykonywania przepływów pracy, które zawierają powiadomienie o zdarzenia cyklu życia, kontrola wykonywania, wznowienie zakładki i trwałości. <xref:System.ServiceModel.Activities.WorkflowServiceHost> zapewnia obsługę działań dotyczących komunikatów i jest używany głównie z usług przepływu pracy. Ten temat stanowi wprowadzenie do przepływu pracy obsługującego z <xref:System.Activities.WorkflowInvoker> i <xref:System.Activities.WorkflowApplication>. Aby uzyskać więcej informacji o hostingu przepływy pracy za pomocą <xref:System.ServiceModel.Activities.WorkflowServiceHost>, zobacz [usług przepływu pracy](../wcf/feature-details/workflow-services.md) i [przegląd usług przepływu pracy obsługującego](../wcf/feature-details/hosting-workflow-services-overview.md).  
  
## <a name="using-workflowinvoker"></a>Za pomocą obiektu WorkflowInvoker  
 <xref:System.Activities.WorkflowInvoker> udostępnia model do wykonywania przepływu pracy, jak w przypadku wywołania metody. Do wywołania w przepływie pracy używającym <xref:System.Activities.WorkflowInvoker>, wywołaj <xref:System.Activities.WorkflowInvoker.Invoke%2A> metody i przekazać w definicji przepływu pracy, przepływu pracy do wywołania. W tym przykładzie <xref:System.Activities.Statements.WriteLine> działania jest wywoływany przy użyciu <xref:System.Activities.WorkflowInvoker>.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#1)]  
  
 Gdy przepływ pracy jest wywoływany przy użyciu <xref:System.Activities.WorkflowInvoker>, przepływ pracy jest wykonywana na wątku wywołującym i <xref:System.Activities.WorkflowInvoker.Invoke%2A> metoda blokuje do czasu ukończenia, łącznie z każdym bezczynności przepływu pracy. Aby skonfigurować interwał limitu czasu, w którym należy wykonać przepływu pracy, użyj jednej z <xref:System.Activities.WorkflowInvoker.Invoke%2A> przeciążenia, które przyjmuje <xref:System.TimeSpan> parametru. W tym przykładzie przepływ pracy jest wywoływana dwa razy z dwóch interwałów innego limitu czasu. Pierwszy progresywne przepływu pracy, ale druga nie.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#50](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#50)]  
  
> [!NOTE]
>  <xref:System.TimeoutException> Tylko jest generowany, jeśli upłynie limit czasu i przepływ pracy staje się nieaktywna podczas wykonywania. Przepływ pracy, który trwa dłużej niż interwał określony limit czasu, aby ukończyć zakończy się pomyślnie, jeśli przepływ pracy nie przejdzie w stan bezczynności.  
  
 <xref:System.Activities.WorkflowInvoker> Ponadto zawiera asynchroniczne wersje metody invoke. Aby uzyskać więcej informacji, zobacz <xref:System.Activities.WorkflowInvoker.InvokeAsync%2A> i <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A>.  
  
### <a name="setting-input-arguments-of-a-workflow"></a>Argumenty wejściowe ustawienia przepływu pracy  
 Dane mogą być przekazywane do przepływu pracy przy użyciu słownika parametrów wejściowych, kluczach nazwę argumentu mapowane na podstawie argumentów wejściowych przepływu pracy. W tym przykładzie <xref:System.Activities.Statements.WriteLine> jest wywoływany i wartości dla swojej <xref:System.Activities.Statements.WriteLine.Text%2A> argument jest określony za pomocą słownika parametrów wejściowych.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#3)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>Trwa pobieranie danych wyjściowych argumenty przepływu pracy  
 Parametry wyjściowe przepływu pracy można uzyskać za pomocą słownika danych wyjściowych, który jest zwracany z wywołania <xref:System.Activities.WorkflowInvoker.Invoke%2A>. Poniższy przykład przedstawia wywoływanie przepływu pracy składającą się z pojedynczej `Divide` działania, ma dwa argumenty i dwa wyjściowych argumentów. Jeśli przepływ pracy zostanie wywołane, `arguments` słownika jest przekazywana, który zawiera wartości dla każdego argumentu, kluczach nazwę argumentu w danych wejściowych. Po wywołaniu `Invoke` zwraca, każdy argument dane wyjściowe są zwracane w `outputs` słownika, również kluczach nazwę argumentu.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#120](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#120)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#20](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#20)]  
  
 Jeśli przepływ pracy jest pochodną <xref:System.Activities.ActivityWithResult>, takich jak `CodeActivity<TResult>` lub `Activity<TResult>`, i argumenty wyjściowe oprócz dobrze zdefiniowanych <xref:System.Activities.Activity%601.Result%2A> danych wyjściowych argumentu, przeciążenie nieogólnego `Invoke` należy użyć w celu pobrania dodatkowe argumenty. Aby to zrobić, definicja przepływu pracy są przekazywane do `Invoke` musi być typu <xref:System.Activities.Activity>. W tym przykładzie `Divide` pochodzi od klasy działania `CodeActivity<int>`, ale jest zadeklarowany jako <xref:System.Activities.Activity> tak, aby nieogólnego przeciążenia `Invoke` jest używany, która zwraca słownika argumentów, zamiast pojedynczej wartości zwracanej.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#121](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#121)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#21](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#21)]  
  
## <a name="using-workflowapplication"></a>Za pomocą WorkflowApplication  
 <xref:System.Activities.WorkflowApplication> udostępnia bogaty zestaw funkcji zarządzania wystąpienia przepływu pracy. <xref:System.Activities.WorkflowApplication> działa jako serwer proxy awaryjny wątku do rzeczywistej <xref:System.Activities.Hosting.WorkflowInstance>, która hermetyzuje środowiska uruchomieniowego i zawiera metody służące do tworzenia i ładowanie wystąpienia przepływu pracy, wstrzymywanie i wznawianie, przerywanie i powiadomień o zdarzeniach cyklu życia. Do uruchamiania przepływu pracy przy użyciu <xref:System.Activities.WorkflowApplication> tworzenia <xref:System.Activities.WorkflowApplication>subskrybowanie dowolnego zdarzenia cyklu życia żądaną, uruchomić przepływ pracy, a następnie poczekaj na zakończenie jego działania. W tym przykładzie definicji przepływu pracy składający się z <xref:System.Activities.Statements.WriteLine> utworzeniu działania i <xref:System.Activities.WorkflowApplication> jest tworzony przy użyciu definicji określonego przepływu pracy. <xref:System.Activities.WorkflowApplication.Completed%2A> jest obsługiwane, więc hosta, zostanie powiadomiona po ukończeniu przepływu pracy, przepływ pracy zostanie uruchomiony przy użyciu wywołania <xref:System.Activities.WorkflowApplication.Run%2A>, a następnie czeka hosta przepływu pracy do wykonania. Po ukończeniu przepływu pracy <xref:System.Threading.AutoResetEvent> jest ustawiony, host aplikacji można wznowić wykonywania, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#31](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#31)]  
  
### <a name="workflowapplication-lifecycle-events"></a>Zdarzenia cyklu życia WorkflowApplication  
 Oprócz <xref:System.Activities.WorkflowApplication.Completed%2A>, może zostać poinformowany autorzy hosta, gdy przepływ pracy jest zwalniana (<xref:System.Activities.WorkflowApplication.Unloaded%2A>), przerwane (<xref:System.Activities.WorkflowApplication.Aborted%2A>), staje się bezczynności (<xref:System.Activities.WorkflowApplication.Idle%2A> i <xref:System.Activities.WorkflowApplication.PersistableIdle%2A>), lub wystąpieniu nieobsługiwanego wyjątku (<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>). Deweloperzy aplikacji przepływu pracy można obsługiwać te powiadomienia i podjąć odpowiednie działania, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#32](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#32)]  
  
### <a name="setting-input-arguments-of-a-workflow"></a>Argumenty wejściowe ustawienia przepływu pracy  
 Dane mogą być przekazywane do przepływu pracy, jak została uruchomiona przy użyciu słownik parametrów, podobne do danych w sposób jest przekazywany w przypadku korzystania z <xref:System.Activities.WorkflowInvoker>. Każdy element w słowniku mapuje argument wejściowy określonego przepływu pracy. W tym przykładzie przepływ pracy składający się z <xref:System.Activities.Statements.WriteLine> wywoływaną działanie i jego <xref:System.Activities.Statements.WriteLine.Text%2A> argument jest określony za pomocą słownika parametrów wejściowych.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#30](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#30)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>Trwa pobieranie danych wyjściowych argumenty przepływu pracy  
 Po zakończeniu przepływu pracy, argumenty dane wyjściowe mogą być pobierane w <xref:System.Activities.WorkflowApplication.Completed%2A> program obsługi, uzyskując dostęp do <xref:System.Activities.WorkflowApplicationCompletedEventArgs.Outputs%2A?displayProperty=nameWithType> słownika. Poniższy przykład hostuje przepływu pracy przy użyciu <xref:System.Activities.WorkflowApplication>. A <xref:System.Activities.WorkflowApplication> wystąpienia jest tworzony przy użyciu definicji przepływu pracy, składającą się z pojedynczej `DiceRoll` działania. `DiceRoll` Działanie ma dwa argumenty danych wyjściowych, które reprezentują wyniki operacji rzutowania dice. Po zakończeniu przepływu pracy, dane wyjściowe są pobierane w <xref:System.Activities.WorkflowApplication.Completed%2A> programu obsługi.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#130](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#130)]  
  
 [!code-csharp[CFX_WorkflowApplicationExample#21](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#21)]  
  
> [!NOTE]
>  <xref:System.Activities.WorkflowApplication> i <xref:System.Activities.WorkflowInvoker> przyjmują słownika argumentów wejściowych i zwracają słownik `out` argumentów. Te parametry słownika, właściwości i wartości zwracane są typu `IDictionary<string, object>`. Rzeczywistego wystąpienia klasy słownik, który jest przekazywany może być każda klasa implementująca `IDictionary<string, object>`. W tych przykładach `Dictionary<string, object>` jest używany. Aby uzyskać więcej informacji na temat słowników, zobacz <xref:System.Collections.Generic.IDictionary%602> i <xref:System.Collections.Generic.Dictionary%602>.  
  
### <a name="passing-data-into-a-running-workflow-using-bookmarks"></a>Przekazywanie danych do uruchamiania przepływu pracy, korzystanie z zakładek  
 Zakładki są mechanizm, za pomocą którego pasywnie poczekać na wznowienie działania, a to mechanizm przekazywania danych do uruchomionego wystąpienia przepływu pracy. Jeśli działanie czeka na dane, można utworzyć <xref:System.Activities.Bookmark> i zarejestruj metodę wywołania zwrotnego wywoływana, gdy <xref:System.Activities.Bookmark> zostanie wznowione, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
 Po wykonaniu `ReadLine` tworzy działanie <xref:System.Activities.Bookmark>, rejestruje wywołanie zwrotne, a następnie czeka na <xref:System.Activities.Bookmark> wznowienie. Gdy zostanie wznowione, `ReadLine` działania przypisuje danych, który został przekazany z <xref:System.Activities.Bookmark> do jego <xref:System.Activities.Activity%601.Result%2A> argumentu. W tym przykładzie przepływ pracy jest tworzony, który używa `ReadLine` działanie, aby zbierać nazwy użytkownika i wyświetl ją w oknie konsoli.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#22](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#22)]  
  
 Gdy `ReadLine` jest wykonywane działanie, tworzy on <xref:System.Activities.Bookmark> o nazwie `UserName` , a następnie czeka zakładki wznowienie. Zbiera dane żądanego hosta, a następnie kontynuowanie <xref:System.Activities.Bookmark>. Przepływ pracy zostanie wznowione, wyświetla nazwę, a następnie kończy.  
  
 Aplikacja hosta można sprawdzić przepływu pracy, aby ustalić, czy istnieją aktywne zakładek. Go to zrobić, wywołując <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> metody <xref:System.Activities.WorkflowApplication> wystąpienia oraz przez sprawdzanie <xref:System.Activities.WorkflowApplicationIdleEventArgs> w <xref:System.Activities.WorkflowApplication.Idle%2A> programu obsługi.  
  
 Poniższy przykład kodu jest podobnie jak w poprzednim przykładzie, chyba że wyliczane są aktywne zakładek, przed wznowieniem zakładki. Przepływ pracy jest uruchomiony, a drugi raz <xref:System.Activities.Bookmark> jest tworzony i przepływ pracy przechodzi w stan bezczynności, <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> jest wywoływana. Po ukończeniu przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli.  
  
 **Jak się nazywasz?**  
**Nazwa_zakładki: Nazwa użytkownika — OwnerDisplayName: ReadLine**   
**Steve**   
**Hello, Steve**

[!code-csharp[CFX_WorkflowApplicationExample#14](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#14)]  
  
 Poniższy przykład kodu sprawdza <xref:System.Activities.WorkflowApplicationIdleEventArgs> przekazany do <xref:System.Activities.WorkflowApplication.Idle%2A> program obsługi <xref:System.Activities.WorkflowApplication> wystąpienia. W tym przykładzie przepływu pracy, przechodząc bezczynności ma jeden <xref:System.Activities.Bookmark> o nazwie `EnterGuess`, posiadane przez działania o nazwie `ReadInt`. Ten przykładowy kod opiera się wylogować się z [jak: Uruchamianie przepływu pracy](how-to-run-a-workflow.md), który jest częścią [Samouczek wprowadzający](getting-started-tutorial.md). Jeśli <xref:System.Activities.WorkflowApplication.Idle%2A> program obsługi, w tym kroku zostanie zmodyfikowany na potrzeby zawierają kod z tego przykładu, zostaną wyświetlone następujące dane wyjściowe.  
  
 **Nazwa_zakładki: EnterGuess - OwnerDisplayName: Readint —**
 
 [!code-csharp[CFX_WorkflowApplicationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#2)]  
  
## <a name="summary"></a>Podsumowanie  
 <xref:System.Activities.WorkflowInvoker> oferuje uproszczone sposób wywołania przepływów pracy, i chociaż zapewnia metody do przekazywania danych na początku przepływu pracy i wyodrębnianie danych z ukończony przepływ pracy, a nie zapewnia ona w przypadku bardziej złożonych scenariuszy czyli, gdzie <xref:System.Activities.WorkflowApplication> mogą być używane.
