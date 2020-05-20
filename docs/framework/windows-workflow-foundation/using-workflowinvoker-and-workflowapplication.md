---
title: Używanie obiektu WorkflowInvoker i WorkflowApplication
description: W tym artykule opisano hosting przepływu pracy przy użyciu WorkflowInvoker i obiektu WorkflowApplication w Windows Workflow Foundation.
ms.date: 03/30/2017
ms.assetid: cd0e583c-a3f9-4fa2-b247-c7b3368c48a7
ms.openlocfilehash: 50ad291bc73818092e7a08d489d6860636f9c379
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421322"
---
# <a name="using-workflowinvoker-and-workflowapplication"></a>Używanie obiektu WorkflowInvoker i WorkflowApplication
Windows Workflow Foundation (WF) oferuje kilka metod hostingu przepływów pracy. <xref:System.Activities.WorkflowInvoker>zapewnia prostą metodę wywoływania przepływu pracy tak, jakby była wywołaniem metody i może być używana tylko dla przepływów pracy, które nie używają trwałości. <xref:System.Activities.WorkflowApplication>zapewnia bogatszy model służący do wykonywania przepływów pracy, które obejmują powiadomienia o zdarzeniach cyklu życia, kontroli wykonywania, wznawianiu zakładek i trwałości. <xref:System.ServiceModel.Activities.WorkflowServiceHost>zapewnia obsługę działań związanych z obsługą komunikatów i jest używany głównie z usługami Workflow Services. Ten temat zawiera wprowadzenie do obsługi przepływu pracy w programie <xref:System.Activities.WorkflowInvoker> i <xref:System.Activities.WorkflowApplication> . Aby uzyskać więcej informacji na temat hostingu przepływów pracy za pomocą programu <xref:System.ServiceModel.Activities.WorkflowServiceHost> , zobacz temat [usługi przepływu pracy](../wcf/feature-details/workflow-services.md) i [hostowanie usług przepływu pracy](../wcf/feature-details/hosting-workflow-services-overview.md).  
  
## <a name="using-workflowinvoker"></a>Korzystanie z WorkflowInvoker  
 <xref:System.Activities.WorkflowInvoker>udostępnia model do wykonywania przepływu pracy tak, jakby był wywołaniem metody. Aby wywołać przepływ pracy za pomocą polecenia <xref:System.Activities.WorkflowInvoker> , wywołaj <xref:System.Activities.WorkflowInvoker.Invoke%2A> metodę i przekaż definicję przepływu pracy do wywołania. W tym przykładzie <xref:System.Activities.Statements.WriteLine> działanie jest wywoływane przy użyciu <xref:System.Activities.WorkflowInvoker> .  
  
 [!code-csharp[CFX_WorkflowInvokerExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#1)]  
  
 Gdy przepływ pracy jest wywoływany przy użyciu <xref:System.Activities.WorkflowInvoker> , przepływ pracy jest wykonywany w wątku wywołującym i <xref:System.Activities.WorkflowInvoker.Invoke%2A> bloków metody do momentu zakończenia przepływu pracy, w tym dowolnego czasu bezczynności. Aby skonfigurować interwał przekroczenia limitu czasu, w którym przepływ pracy musi być zakończony, użyj jednego z <xref:System.Activities.WorkflowInvoker.Invoke%2A> przeciążeń, które pobiera <xref:System.TimeSpan> parametr. W tym przykładzie przepływ pracy jest wywoływany dwa razy z dwoma różnymi interwałami limitu czasu. Pierwszy przepływ pracy zakończeniu, ale drugi nie.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#50](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#50)]  
  
> [!NOTE]
> <xref:System.TimeoutException>Jest generowany tylko wtedy, gdy upłynie limit czasu, a przepływ pracy stanie się nieczynny podczas wykonywania. Przepływ pracy, który trwa dłużej niż określony limit czasu, zostanie zakończony pomyślnie, jeśli przepływ pracy nie stanie się bezczynny.  
  
 <xref:System.Activities.WorkflowInvoker>zapewnia także asynchroniczne wersje metody Invoke. Aby uzyskać więcej informacji, zobacz <xref:System.Activities.WorkflowInvoker.InvokeAsync%2A> i <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A>.  
  
### <a name="setting-input-arguments-of-a-workflow"></a>Ustawianie argumentów wejściowych przepływu pracy  
 Dane można przekazywać do przepływu pracy przy użyciu słownika parametrów wejściowych, który jest określany przez nazwę argumentu, który jest mapowany do argumentów wejściowych przepływu pracy. W tym przykładzie <xref:System.Activities.Statements.WriteLine> jest wywoływana i wartość <xref:System.Activities.Statements.WriteLine.Text%2A> argumentu jest określona przy użyciu słownika parametrów wejściowych.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#3)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>Pobieranie argumentów wyjściowych przepływu pracy  
 Parametry wyjściowe przepływu pracy można uzyskać przy użyciu słownika danych wyjściowych zwracanego z wywołania metody <xref:System.Activities.WorkflowInvoker.Invoke%2A> . Poniższy przykład wywołuje przepływ pracy składający się z pojedynczego `Divide` działania, które ma dwa argumenty wejściowe i dwa argumenty wyjściowe. Gdy przepływ pracy jest wywoływany, `arguments` jest przesyłany słownik zawierający wartości dla każdego argumentu wejściowego, który jest określany przez nazwę argumentu. Gdy wywołanie `Invoke` zwrotne zwraca, każdy argument wyjściowy jest zwracany w `outputs` słowniku, również przy użyciu nazwy argumentu.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#120](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#120)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#20](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#20)]  
  
 Jeśli przepływ pracy pochodzi z <xref:System.Activities.ActivityWithResult> , takich jak `CodeActivity<TResult>` lub `Activity<TResult>` , i istnieją argumenty wyjściowe oprócz dobrze zdefiniowanego <xref:System.Activities.Activity%601.Result%2A> argumentu wyjściowego, `Invoke` do pobrania dodatkowych argumentów musi być używany nieogólne Przeciążenie elementu. W tym celu przekazana definicja przepływu pracy `Invoke` musi być typu <xref:System.Activities.Activity> . W tym przykładzie `Divide` działanie pochodzi z `CodeActivity<int>` , ale jest zadeklarowane jako <xref:System.Activities.Activity> tak, że używane jest nieogólne Przeciążenie elementu, `Invoke` które zwraca słownik argumentów zamiast pojedynczej wartości zwracanej.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#121](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#121)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#21](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#21)]  
  
## <a name="using-workflowapplication"></a>Używanie obiektu WorkflowApplication  
 <xref:System.Activities.WorkflowApplication>oferuje bogaty zestaw funkcji zarządzania wystąpieniami przepływu pracy. <xref:System.Activities.WorkflowApplication>działa jako bezpieczny dla wątku serwer proxy do rzeczywistego <xref:System.Activities.Hosting.WorkflowInstance> , który hermetyzuje środowisko uruchomieniowe i zapewnia metody tworzenia i ładowania wystąpień przepływu pracy, wstrzymywanie i wznawianie, kończenie i powiadamianie o zdarzeniach cyklu życia. Aby uruchomić przepływ pracy za pomocą <xref:System.Activities.WorkflowApplication> tworzenia <xref:System.Activities.WorkflowApplication> , zasubskrybować wszystkie zdarzenia cyklu życia, uruchomić przepływ pracy, a następnie zaczekaj na jego zakończenie. W tym przykładzie zostanie utworzona definicja przepływu pracy, która składa się z <xref:System.Activities.Statements.WriteLine> działania i <xref:System.Activities.WorkflowApplication> jest tworzona przy użyciu określonej definicji przepływu pracy. <xref:System.Activities.WorkflowApplication.Completed%2A>jest obsługiwane, aby Host był powiadamiany po zakończeniu przepływu pracy, przepływ pracy jest uruchamiany z wywołaniem <xref:System.Activities.WorkflowApplication.Run%2A> , a następnie Host czeka na zakończenie przepływu pracy. Po zakończeniu przepływu pracy <xref:System.Threading.AutoResetEvent> jest ustawiony i aplikacja hosta może wznowić wykonywanie, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#31](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#31)]  
  
### <a name="workflowapplication-lifecycle-events"></a>Zdarzenia cyklu życia obiektu WorkflowApplication  
 Oprócz <xref:System.Activities.WorkflowApplication.Completed%2A> tego można powiadamiać autorów, gdy przepływ pracy zostanie zwolniony ( <xref:System.Activities.WorkflowApplication.Unloaded%2A> ), przerwany ( <xref:System.Activities.WorkflowApplication.Aborted%2A> ), stanie się bezczynny ( <xref:System.Activities.WorkflowApplication.Idle%2A> i <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> ) lub wystąpił nieobsługiwany wyjątek ( <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> ). Deweloperzy aplikacji przepływu pracy mogą obsługiwać te powiadomienia i podejmować odpowiednie działania, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#32](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#32)]  
  
### <a name="setting-input-arguments-of-a-workflow"></a>Ustawianie argumentów wejściowych przepływu pracy  
 Dane można przekazywać do przepływu pracy, ponieważ jest on uruchamiany przy użyciu słownika parametrów, podobnie jak dane są przesyłane podczas korzystania z programu <xref:System.Activities.WorkflowInvoker> . Każdy element w słowniku jest mapowany na argument wejściowy określonego przepływu pracy. W tym przykładzie jest wywoływany przepływ pracy, który składa się z <xref:System.Activities.Statements.WriteLine> działania, a jego <xref:System.Activities.Statements.WriteLine.Text%2A> argument jest określony przy użyciu słownika parametrów wejściowych.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#30](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#30)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>Pobieranie argumentów wyjściowych przepływu pracy  
 Po zakończeniu przepływu pracy wszystkie argumenty wyjściowe można pobrać w programie obsługi, <xref:System.Activities.WorkflowApplication.Completed%2A> uzyskując dostęp do <xref:System.Activities.WorkflowApplicationCompletedEventArgs.Outputs%2A?displayProperty=nameWithType> słownika. Poniższy przykład umożliwia hostowanie przepływu pracy przy użyciu polecenia <xref:System.Activities.WorkflowApplication> . <xref:System.Activities.WorkflowApplication>Wystąpienie jest zbudowane przy użyciu definicji przepływu pracy składającej się z pojedynczego `DiceRoll` działania. `DiceRoll`Działanie ma dwa argumenty wyjściowe, które reprezentują wyniki operacji rzutowania indeksu. Po zakończeniu przepływu pracy dane wyjściowe są pobierane w programie <xref:System.Activities.WorkflowApplication.Completed%2A> obsługi.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#130](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#130)]  
  
 [!code-csharp[CFX_WorkflowApplicationExample#21](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#21)]  
  
> [!NOTE]
> <xref:System.Activities.WorkflowApplication>i <xref:System.Activities.WorkflowInvoker> Wypełnij słownik argumentów wejściowych i zwracają słownik `out` argumentów. Te parametry słownika, właściwości i wartości zwracane są typu `IDictionary<string, object>` . Rzeczywiste wystąpienie klasy słownika, która jest przenoszona, może być dowolną klasą implementującą `IDictionary<string, object>` . W tych przykładach `Dictionary<string, object>` jest używana. Aby uzyskać więcej informacji na temat słowników, zobacz <xref:System.Collections.Generic.IDictionary%602> i <xref:System.Collections.Generic.Dictionary%602> .  
  
### <a name="passing-data-into-a-running-workflow-using-bookmarks"></a>Przekazywanie danych do działającego przepływu pracy przy użyciu zakładek  
 Zakładki to mechanizm, za pomocą którego działanie może pasywnie oczekiwać na wznowienie i jest mechanizmem przekazywania danych do uruchomionego wystąpienia przepływu pracy. Jeśli działanie oczekuje na dane, może utworzyć <xref:System.Activities.Bookmark> i zarejestrować metodę wywołania zwrotnego, która ma być wywoływana po <xref:System.Activities.Bookmark> wznowieniu, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
 Po wykonaniu `ReadLine` działanie tworzy <xref:System.Activities.Bookmark> , rejestruje wywołanie zwrotne, a następnie czeka na <xref:System.Activities.Bookmark> wznowienie. Gdy zostanie ono wznowione, `ReadLine` działanie przypisze dane, które zostały przesłane z <xref:System.Activities.Bookmark> do tego <xref:System.Activities.Activity%601.Result%2A> argumentu. W tym przykładzie zostanie utworzony przepływ pracy, który używa `ReadLine` działania do zbierania nazwy użytkownika i wyświetlania go w oknie konsoli.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#22](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#22)]  
  
 Gdy `ReadLine` działanie jest wykonywane, tworzy <xref:System.Activities.Bookmark> nazwę, `UserName` a następnie czeka na wznowienie zakładki. Host zbiera wymagane dane, a następnie wznawia działanie <xref:System.Activities.Bookmark> . Przepływ pracy zostanie wznowiony, zostanie wyświetlona nazwa, a następnie zostanie zakończona.  
  
 Aplikacja hosta może przeprowadzić inspekcję przepływu pracy w celu ustalenia, czy istnieją aktywne zakładki. Można to zrobić <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> , wywołując metodę <xref:System.Activities.WorkflowApplication> wystąpienia lub sprawdzając je <xref:System.Activities.WorkflowApplicationIdleEventArgs> w programie <xref:System.Activities.WorkflowApplication.Idle%2A> obsługi.  
  
 Poniższy przykład kodu jest podobny do poprzedniego, z tą różnicą, że zakładki aktywne są wyliczane przed wznowieniem zakładki. Przepływ pracy jest uruchamiany, a gdy <xref:System.Activities.Bookmark> zostanie utworzony, a przepływ pracy jest bezczynny, <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> jest wywoływany. Po zakończeniu przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli programu.  
  
 **Jak się nazywasz?**  
**Zakładkaname: username-OwnerDisplayName: ReadLine** 
 **Steve** 
 **Witaj, Steve**

[!code-csharp[CFX_WorkflowApplicationExample#14](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#14)]  
  
 Poniższy przykład kodu sprawdza, czy <xref:System.Activities.WorkflowApplicationIdleEventArgs> przeszedł do <xref:System.Activities.WorkflowApplication.Idle%2A> procedury obsługi <xref:System.Activities.WorkflowApplication> wystąpienia. W tym przykładzie przepływ pracy, który przejdzie do bezczynności, ma jedną <xref:System.Activities.Bookmark> z nazwami `EnterGuess` , należącymi do działania o nazwie `ReadInt` . Ten przykład kodu jest oparty na [sposobie: uruchamianie przepływu pracy](how-to-run-a-workflow.md), który jest częścią [samouczka Wprowadzenie](getting-started-tutorial.md). Jeśli <xref:System.Activities.WorkflowApplication.Idle%2A> program obsługi w tym kroku jest modyfikowany tak, aby zawierał kod z tego przykładu, wyświetlane są następujące dane wyjściowe.  
  
 **Zakładkaname: EnterGuess-OwnerDisplayName: ReadInt**

 [!code-csharp[CFX_WorkflowApplicationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#2)]  
  
## <a name="summary"></a>Podsumowanie  
 <xref:System.Activities.WorkflowInvoker>zapewnia lekki sposób wywoływania przepływów pracy, a chociaż udostępnia metody przekazywania danych na początku przepływu pracy i wyodrębniania danych z ukończonego przepływu pracy, nie zapewnia bardziej złożonych scenariuszy, których <xref:System.Activities.WorkflowApplication> można użyć.
