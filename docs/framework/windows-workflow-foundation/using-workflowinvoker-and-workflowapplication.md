---
title: Przy użyciu WorkflowInvoker i działanie obiektu WorkflowApplication
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cd0e583c-a3f9-4fa2-b247-c7b3368c48a7
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 90999867ee1dd678e279832d73d7ecaaa416fe7b
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="using-workflowinvoker-and-workflowapplication"></a>Przy użyciu WorkflowInvoker i działanie obiektu WorkflowApplication
Windows Workflow Foundation (WF) zapewnia kilka metod obsługi przepływów pracy. <xref:System.Activities.WorkflowInvoker> zapewnia prostą metodę do wywoływania przepływu pracy, tak, jakby były wywołanie metody i można używać tylko w przypadku przepływów pracy, które nie korzystają z trwałości. <xref:System.Activities.WorkflowApplication> zapewnia bardziej rozbudowane model do wykonywania przepływów pracy, które zawiera powiadomienia o zdarzenia cyklu życia, kontrola wykonywania wznowienie zakładek i trwałości. <xref:System.ServiceModel.Activities.WorkflowServiceHost> zapewnia obsługę działań dotyczących komunikatów i jest używany głównie z usług przepływu pracy. Ten temat stanowi wprowadzenie do przepływu pracy obsługującego z <xref:System.Activities.WorkflowInvoker> i <xref:System.Activities.WorkflowApplication>. [!INCLUDE[crabout](../../../includes/crabout-md.md)] hosting przepływy pracy z <xref:System.ServiceModel.Activities.WorkflowServiceHost>, zobacz [usług przepływu pracy](../../../docs/framework/wcf/feature-details/workflow-services.md) i [Hosting przegląd usług przepływu pracy](../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md).  
  
## <a name="using-workflowinvoker"></a>Przy użyciu WorkflowInvoker  
 <xref:System.Activities.WorkflowInvoker> udostępnia model wykonania przepływu pracy, jak w przypadku wywołania metody. Można wywołać przepływu pracy przy użyciu <xref:System.Activities.WorkflowInvoker>, wywołaj <xref:System.Activities.WorkflowInvoker.Invoke%2A> — metoda i przekazać w definicji przepływu pracy przepływu pracy do wywołania. W tym przykładzie <xref:System.Activities.Statements.WriteLine> działania jest wywoływana przy użyciu <xref:System.Activities.WorkflowInvoker>.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#1)]  
  
 Jeśli przepływ pracy zostanie wywołane przy użyciu <xref:System.Activities.WorkflowInvoker>, przepływu pracy wykonuje w wątku wywołującym i <xref:System.Activities.WorkflowInvoker.Invoke%2A> metody blokuje aż przepływ pracy zostanie zakończone, w tym wszelkie czas bezczynności. Aby skonfigurować interwał limitu czasu, w którym należy wykonać przepływu pracy, użyj jednej z <xref:System.Activities.WorkflowInvoker.Invoke%2A> przeciążeń, które przyjmuje <xref:System.TimeSpan> parametru. W tym przykładzie przepływu pracy została wywołana dwa razy z dwóch różnych limitu czasu odstępach czasu. Pierwszy complets przepływu pracy, ale druga nie.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#50](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#50)]  
  
> [!NOTE]
>  <xref:System.TimeoutException> Jest tylko element zgłaszany, gdy upłynie limit czasu, a przepływ pracy przestanie być bezczynne podczas wykonywania. Przepływ pracy, który będzie trwało dłużej niż interwał określony limit czasu, aby ukończyć zakończy się pomyślnie, jeśli przepływ pracy przejdzie w stan bezczynności.  
  
 <xref:System.Activities.WorkflowInvoker> udostępnia asynchroniczne wersje metody invoke. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] <xref:System.Activities.WorkflowInvoker.InvokeAsync%2A> i <xref:System.Activities.WorkflowInvoker.BeginInvoke%2A>.  
  
### <a name="setting-input-arguments-of-a-workflow"></a>Ustawienia argumentów wejściowych przepływu pracy  
 Dane mogą być przekazywane do przepływu pracy za pomocą słownika parametrów wejściowych, wyznaczaną przez Nazwa argumentu mapowane na argumenty wejściowe przepływu pracy. W tym przykładzie <xref:System.Activities.Statements.WriteLine> jest wywoływany i wartości dla jego <xref:System.Activities.Statements.WriteLine.Text%2A> argument zostanie określony, używając słownika parametrów wejściowych.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#3)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>Pobieranie danych wyjściowych argumenty przepływu pracy  
 Parametry wyjściowe przepływu pracy można uzyskać za pomocą słownika danych wyjściowych, która jest zwracana z wywołania <xref:System.Activities.WorkflowInvoker.Invoke%2A>. Poniższy przykład przedstawia wywoływanie przepływu pracy składającą się z pojedynczej `Divide` działanie, czy ma dwa argumenty w danych wejściowych i wyjściowych dwóch argumentów. Jeśli przepływ pracy zostanie wywołane, `arguments` słownika jest przekazywany, która zawiera wartości dla każdego wejścia argumentu, wyznaczaną przez Nazwa argumentu. Po wywołaniu `Invoke` zwraca każdy argument wyjściowy jest zwracany w `outputs` słownika, także klucze w postaci nazwy argumentu.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#120](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#120)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#20](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#20)]  
  
 Jeśli przepływ pracy jest pochodną <xref:System.Activities.ActivityWithResult>, takich jak `CodeActivity<TResult>` lub `Activity<TResult>`, i argumenty wyjściowe oprócz dobrze zdefiniowany <xref:System.Activities.Activity%601.Result%2A> output argumentu, przeciążenia nierodzajową `Invoke` musi być używany w celu pobrania dodatkowe argumenty. Aby to zrobić, definicji przepływu pracy przekazany `Invoke` musi być typu <xref:System.Activities.Activity>. W tym przykładzie `Divide` działania pochodzi z `CodeActivity<int>`, ale jest zadeklarowany jako <xref:System.Activities.Activity> tak, aby nieogólnego przeciążenia z `Invoke` jest używany, która zwraca słownika argumentów zamiast pojedynczej wartości zwracanych.  
  
 [!code-csharp[CFX_WorkflowInvokerExample#121](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#121)]  
  
 [!code-csharp[CFX_WorkflowInvokerExample#21](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowinvokerexample/cs/program.cs#21)]  
  
## <a name="using-workflowapplication"></a>Przy użyciu obiektu WorkflowApplication  
 <xref:System.Activities.WorkflowApplication> zawiera bogaty zestaw funkcji do zarządzania wystąpienia przepływu pracy. <xref:System.Activities.WorkflowApplication> działa jako serwer proxy bezpieczne wątek, do rzeczywistych <xref:System.Activities.Hosting.WorkflowInstance>, który hermetyzuje środowiska uruchomieniowego i udostępnia metody do tworzenia i ładowanie wystąpienia przepływu pracy, wstrzymywanie i wznawianie, przerywanie i powiadomienia o zdarzeniach cyklu życia. Do uruchamiania przepływu pracy przy użyciu <xref:System.Activities.WorkflowApplication> tworzenia <xref:System.Activities.WorkflowApplication>, subskrybowanie zdarzeń cyklu życia żądaną uruchomienia przepływu pracy i poczekaj na jego zakończenie. W tym przykładzie definicji przepływu pracy składający się z <xref:System.Activities.Statements.WriteLine> utworzeniu działania i <xref:System.Activities.WorkflowApplication> jest tworzony przy użyciu definicji określonego przepływu pracy. <xref:System.Activities.WorkflowApplication.Completed%2A> jest obsługiwane, dlatego host otrzymał powiadomienie po zakończeniu przepływu pracy, przepływ pracy zostanie uruchomiony przy użyciu wywołania <xref:System.Activities.WorkflowApplication.Run%2A>, a następnie oczekiwanie hosta do ukończenia przepływu pracy. Po zakończeniu przepływu pracy, <xref:System.Threading.AutoResetEvent> jest ustawiony, a host aplikacji można wznowić wykonywania, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#31](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#31)]  
  
### <a name="workflowapplication-lifecycle-events"></a>Zdarzenia cyklu życia obiektu WorkflowApplication  
 Oprócz <xref:System.Activities.WorkflowApplication.Completed%2A>, autorzy hosta może otrzymać powiadomienie, gdy przepływ pracy zostanie zwolniony (<xref:System.Activities.WorkflowApplication.Unloaded%2A>), zostało przerwane (<xref:System.Activities.WorkflowApplication.Aborted%2A>), staje się bezczynności (<xref:System.Activities.WorkflowApplication.Idle%2A> i <xref:System.Activities.WorkflowApplication.PersistableIdle%2A>), lub wystąpi nieobsługiwany wyjątek (<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>). Deweloperzy aplikacji przepływu pracy można obsługiwać te powiadomienia i podejmij odpowiednią akcję, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#32](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#32)]  
  
### <a name="setting-input-arguments-of-a-workflow"></a>Ustawienia argumentów wejściowych przepływu pracy  
 Dane mogą być przekazywane do przepływu pracy, jak została uruchomiona przy użyciu słownik parametrów, podobne do danych sposób jest przekazywany w przypadku korzystania z <xref:System.Activities.WorkflowInvoker>. Argument wejściowy określonego przepływu pracy mapuje każdego elementu w słowniku. W tym przykładzie przepływ pracy składający się z <xref:System.Activities.Statements.WriteLine> działania jest wywoływany i jego <xref:System.Activities.Statements.WriteLine.Text%2A> argument zostanie określony, używając słownika parametrów wejściowych.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#30](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#30)]  
  
### <a name="retrieving-output-arguments-of-a-workflow"></a>Pobieranie danych wyjściowych argumenty przepływu pracy  
 Po zakończeniu przepływu pracy, można pobrać żadnych danych wyjściowych argumentów w <xref:System.Activities.WorkflowApplication.Completed%2A> obsługi uzyskując dostęp do <xref:System.Activities.WorkflowApplicationCompletedEventArgs.Outputs%2A?displayProperty=nameWithType> słownika. Poniższy przykład zawiera przepływu pracy przy użyciu <xref:System.Activities.WorkflowApplication>. A <xref:System.Activities.WorkflowApplication> wystąpienia jest tworzony przy użyciu definicji przepływu pracy, składającą się z pojedynczej `DiceRoll` działania. `DiceRoll` Działanie ma dwa argumenty danych wyjściowych reprezentujące wyniki operacji zbiorczego grupowane. Po zakończeniu przepływu pracy, dane wyjściowe są pobierane w <xref:System.Activities.WorkflowApplication.Completed%2A> programu obsługi.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#130](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#130)]  
  
 [!code-csharp[CFX_WorkflowApplicationExample#21](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#21)]  
  
> [!NOTE]
>  <xref:System.Activities.WorkflowApplication> i <xref:System.Activities.WorkflowInvoker> przyjmować ze słownika wejściowego argumenty i zwracać słownik `out` argumentów. Te parametry słownika, właściwości i wartości zwracane są typu `IDictionary<string, object>`. Rzeczywiste wystąpienie klasy słownik, który jest przekazywany w może być każda klasa implementująca `IDictionary<string, object>`. W tym przykładzie `Dictionary<string, object>` jest używany. [!INCLUDE[crabout](../../../includes/crabout-md.md)] Zobacz słowników, <xref:System.Collections.Generic.IDictionary%602> i <xref:System.Collections.Generic.Dictionary%602>.  
  
### <a name="passing-data-into-a-running-workflow-using-bookmarks"></a>Przekazywanie danych do działania przepływu pracy korzystanie z zakładek  
 Zakładki są mechanizm, za pomocą której działanie pasywnie poczekać wznowienie zadania było i jest mechanizm przekazywania danych do uruchomionego wystąpienia przepływu pracy. Jeśli działanie oczekuje na dane, można utworzyć <xref:System.Activities.Bookmark> i zarejestruj Metoda wywołania zwrotnego wywoływana, gdy <xref:System.Activities.Bookmark> zostanie wznowione, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
 Po wykonaniu `ReadLine` działanie tworzy <xref:System.Activities.Bookmark>, rejestruje wywołanie zwrotne, a następnie oczekiwanie <xref:System.Activities.Bookmark> wznowienie zadania było. Gdy zostanie wznowione, `ReadLine` działania przypisuje danych, który został przekazany z <xref:System.Activities.Bookmark> do jego <xref:System.Activities.Activity%601.Result%2A> argumentu. W tym przykładzie przepływ pracy jest tworzony, który używa `ReadLine` działania zebranie nazwy użytkownika i wyświetlić je w oknie konsoli.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#22](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#22)]  
  
 Gdy `ReadLine` działania jest wykonywana, tworzy <xref:System.Activities.Bookmark> o nazwie `UserName` , a następnie oczekiwanie zakładki wznowienie zadania było. Zbiera dane żądanego hosta, a następnie kontynuowanie <xref:System.Activities.Bookmark>. Przepływ pracy wznawia, wyświetla nazwę, a następnie kończy.  
  
 Host aplikacji może sprawdzać przepływu pracy, aby określić, czy istnieją aktywne zakładek. Go to zrobić przez wywołanie metody <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> metody <xref:System.Activities.WorkflowApplication> wystąpienia, lub przez kontrolę <xref:System.Activities.WorkflowApplicationIdleEventArgs> w <xref:System.Activities.WorkflowApplication.Idle%2A> programu obsługi.  
  
 Poniższy przykład kodu jest tak jak w poprzednim przykładzie, z tą różnicą, że wyliczane są aktywne zakładki przed wznowieniu działania zakładki. Przepływu pracy została uruchomiona, a drugi raz <xref:System.Activities.Bookmark> jest tworzony i przepływ pracy przejdzie bezczynności, <xref:System.Activities.WorkflowApplication.GetBookmarks%2A> nosi nazwę. Po zakończeniu przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli.  
  
 **Jak się nazywasz?**  
**Nazwa zakładki: Nazwa_użytkownika - OwnerDisplayName: ReadLine**   
**Steve**   
**Witaj, Steve**

[!code-csharp[CFX_WorkflowApplicationExample#14](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#14)]  
  
 Poniższy przykład kodu sprawdza <xref:System.Activities.WorkflowApplicationIdleEventArgs> przekazany <xref:System.Activities.WorkflowApplication.Idle%2A> obsługi <xref:System.Activities.WorkflowApplication> wystąpienia. W tym przykładzie przepływu pracy, przejście w stan bezczynności ma jeden <xref:System.Activities.Bookmark> o nazwie `EnterGuess`, będących własnością przez działanie o nazwie `ReadInt`. W tym przykładzie kodu opiera się z [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md), który jest częścią [Wprowadzenie — samouczek](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md). Jeśli <xref:System.Activities.WorkflowApplication.Idle%2A> program obsługi, w tym kroku są modyfikowane w celu zawiera kod z tego przykładu, wyświetlane są następujące dane wyjściowe.  
  
 **Nazwa zakładki: EnterGuess - OwnerDisplayName: ReadInt**
 
 [!code-csharp[CFX_WorkflowApplicationExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#2)]  
  
## <a name="summary"></a>Podsumowanie  
 <xref:System.Activities.WorkflowInvoker> Umożliwia uproszczonego wywoływać przepływy pracy, i chociaż zapewnia metody przekazywanie danych podczas uruchamiania przepływu pracy i wyodrębniania danych z ukończonych przepływów pracy, a nie zapewnia bardziej złożonych scenariuszach czyli gdzie <xref:System.Activities.WorkflowApplication> mogą być używane.
