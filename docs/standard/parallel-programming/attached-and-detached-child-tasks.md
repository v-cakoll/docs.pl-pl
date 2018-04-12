---
title: Dołączone i odłączone zadania podrzędne
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, child tasks
ms.assetid: c95788bf-90a6-4e96-b7bc-58e36a228cc5
caps.latest.revision: 21
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 298ccdc4628c840874d10832da29c10d6d496655
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="attached-and-detached-child-tasks"></a>Dołączone i odłączone zadania podrzędne
A *zadania podrzędnego* (lub *zadania zagnieżdżonego*) jest <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> wystąpienia utworzone w delegata użytkownika innego zadania, które jest nazywany *zadaniem nadrzędnym*. Zadania podrzędnego można odłączyć lub dołączony. A *zadania podrzędnego odłączyć* to zadanie, które wykonuje niezależnie od jego elementu nadrzędnego. *Dołączony zadania podrzędnego* jest tworzonych za pomocą zadania zagnieżdżonego <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> opcji, których elementem nadrzędnym nie jawnie lub domyślnie zabronić dołączony. Zadanie może utworzyć dowolną liczbę podrzędnych dołączone i odłączone zadania ograniczony tylko ilością zasobów systemowych.  
  
 W poniższej tabeli wymieniono podstawowe różnice między dwa rodzaje zadań podrzędnych.  
  
|Kategoria|Zadania podrzędne odłączona|Zadania podrzędne dołączone|  
|--------------|--------------------------|--------------------------|  
|Nadrzędny czeka na ukończenie zadań podrzędnych.|Nie|Tak|  
|Nadrzędny propaguje wyjątków zgłaszanych przez zadania podrzędne.|Nie|Tak|  
|Stan elementu nadrzędnego jest zależny od stanu podrzędnego.|Nie|Tak|  
  
 W większości przypadków firma Microsoft zaleca użycie zadania podrzędne odłączony, ponieważ ich relacji z innymi zadaniami są mniej złożona. Oznacza to dlaczego zadania utworzone w nadrzędnej zadania są odłączone domyślnie i należy jawnie określić <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> opcję, aby utworzyć zadanie podrzędne dołączone.  
  
## <a name="detached-child-tasks"></a>Zadania podrzędne odłączona  
 Chociaż zadania podrzędnego jest tworzony przez zadaniem nadrzędnym, domyślnie jest niezależna od zadaniem nadrzędnym. W poniższym przykładzie zadaniem nadrzędnym tworzy jedno zadanie podrzędne proste. Jeśli przykładowy kod należy uruchamiać wielokrotnie, mogą pojawić się dane wyjściowe z przykładu różni się od pokazano, czy również, że dane wyjściowe mogą ulec zmianie po każdej aktualizacji można uruchomić kod. Dzieje się tak, ponieważ niezależnie od siebie nawzajem; zadaniem nadrzędnym i zadania podrzędne obiekt podrzędny jest odłączony zadanie. Przykład oczekuje tylko dla zadania nadrzędnego zakończyć i nie może wykonać zadania podrzędnego lub kończy ukończone przed aplikacji konsoli.  
  
 [!code-csharp[TPL_ChildTasks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/nested1.cs#1)]
 [!code-vb[TPL_ChildTasks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/nested1.vb#1)]  
  
 Jeśli zadanie podrzędne jest reprezentowana przez <xref:System.Threading.Tasks.Task%601> obiektu zamiast <xref:System.Threading.Tasks.Task> obiektu, można zapewnić, że zadaniem nadrzędnym będzie czekać podrzędny wykonać uzyskując dostęp do <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> właściwości nawet wtedy, gdy jest to zadanie podrzędne odłączyć podrzędnej. <xref:System.Threading.Tasks.Task%601.Result%2A> Właściwość blokuje dopiero po zakończeniu jego zadania, jak przedstawiono na poniższym przykładzie.  
  
 [!code-csharp[TPL_ChildTasks#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/childtasks.cs#4)]
 [!code-vb[TPL_ChildTasks#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/tpl_childtasks.vb#4)]  
  
## <a name="attached-child-tasks"></a>Zadania podrzędne dołączone  
 W przeciwieństwie do zadania podrzędne odłączony zadania podrzędne dołączone ściśle są synchronizowane z obiektu nadrzędnego. Zadanie odłączyć podrzędnej w poprzednim przykładzie do zadania podrzędne dołączone można zmienić za pomocą <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> opcji w instrukcji tworzenia zadania, jak pokazano w poniższym przykładzie. W tym kodzie zadania podrzędnego dołączonego kończy się przed jego elementu nadrzędnego. W związku z tym dane wyjściowe z przykładu jest taka sama każdego wykonywania kodu.  
  
 [!code-csharp[TPL_ChildTasks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1.cs#2)]
 [!code-vb[TPL_ChildTasks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1.vb#2)]  
  
 Zadania podrzędne dołączone umożliwia tworzenie wykresów ściśle zsynchronizowanych operacji asynchronicznej.  
  
 Jednak zadanie podrzędne można dołączyć do elementu nadrzędnego tylko wtedy, gdy jego elementu nadrzędnego nie zabrania zadania podrzędne dołączone. Zadania nadrzędnego jawnie uniemożliwi zadania podrzędne dołączanie do nich, określając <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opcji w konstruktorze klasy zadania nadrzędnego lub <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metody. Zadania nadrzędnego niejawnie uniemożliwić zadania podrzędne dołączanie do nich, jeśli są one tworzone przez wywołanie metody <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metody. Ilustruje to poniższy przykład. Jest taki sam jak poprzedni przykład, z wyjątkiem tego, że zadaniem nadrzędnym jest tworzony przez wywołanie metody <xref:System.Threading.Tasks.Task.Run%28System.Action%29?displayProperty=nameWithType> metody zamiast <xref:System.Threading.Tasks.TaskFactory.StartNew%28System.Action%29?displayProperty=nameWithType> metody. Ponieważ zadania podrzędnego nie można dołączyć do elementu nadrzędnego, dane wyjściowe z przykładu będzie nieprzewidywalny. Ponieważ opcje tworzenia zadań domyślne <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> przeciążenia obejmują <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>, w tym przykładzie jest funkcjonalnym odpowiednikiem pierwszym przykładzie w sekcji "Odłączone zadania podrzędne".  
  
 [!code-csharp[TPL_ChildTasks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1a.cs#3)]
 [!code-vb[TPL_ChildTasks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1a.vb#3)]  
  
## <a name="exceptions-in-child-tasks"></a>Wyjątki w zadania podrzędne  
 Zadania podrzędnego odłączyć zgłasza wyjątek, ten wyjątek musi być obserwowane lub obsługi bezpośrednio w zadaniem nadrzędnym, tak jak w przypadku dowolnego zadania-nested. Jeśli zadanie podrzędne dołączone zgłasza wyjątek, wyjątek automatycznie propagowane do zadaniem nadrzędnym i z powrotem do wątku, który oczekuje lub próbuje uzyskać dostęp zadania <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> właściwości. W związku z tym, za pomocą zadania podrzędne dołączone, może obsługiwać wszystkie wyjątki w tylko jednym punkcie w wywołaniu <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> w wątku wywołującym. Aby uzyskać więcej informacji, zobacz [obsługi wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
## <a name="cancellation-and-child-tasks"></a>Anulowanie i podrzędne zadania  
 Anulowanie zadania jest współpracy. Oznacza to istnieć możliwość anulowania, każdego zadania podrzędnego dołączonego ani odłączonego należy monitorować stan token anulowania. Jeśli chcesz anulować nadrzędne i wszystkich jego obiektów podrzędnych za pomocą jednego żądania anulowania, przekaż ten sam token jako argument do wszystkich zadań i podać w każdym zadaniu logiki na odpowiedź na żądanie w każdym zadaniu. Aby uzyskać więcej informacji, zobacz [anulowanie zadania](../../../docs/standard/parallel-programming/task-cancellation.md) i [porady: anulowanie zadania i jego elementy podrzędne](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
### <a name="when-the-parent-cancels"></a>Gdy anuluje nadrzędnego  
 Jeśli nadrzędny anuluje się przed rozpoczęciem jego zadań podrzędnych, podrzędne nigdy nie zostanie uruchomiony. Jeśli element nadrzędny jest anulowany automatycznie po jego zadań podrzędnych została już uruchomiona, do ukończenia jest uruchamiana podrzędnych, chyba że ma ona własnej logiki anulowania. Aby uzyskać więcej informacji, zobacz [anulowanie zadania](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="when-a-detached-child-task-cancels"></a>Gdy anuluje zadania podrzędnego odłączona  
 Jeśli zadania podrzędnego odłączyć anuluje przy użyciu tego samego tokenu, który został przekazany do elementu nadrzędnego, a element nadrzędny nie oczekuje zadań podrzędnych, wyjątek nie są propagowane, ponieważ wyjątek jest traktowane jako anulowania niegroźne współpracy. To zachowanie jest takie samo jak dowolnego zadania najwyższego poziomu.  
  
### <a name="when-an-attached-child-task-cancels"></a>Gdy anuluje zadania podrzędnego dołączone  
 Gdy zadanie podrzędne dołączone anuluje przy użyciu tego samego tokenu, który został przekazany do jego zadaniem nadrzędnym <xref:System.Threading.Tasks.TaskCanceledException> jest propagowana do łącząca wątek wewnątrz <xref:System.AggregateException>. Poczekaj, aż zadaniem nadrzędnym, aby mogły obsługiwać wszystkie wyjątki niegroźne oprócz wszystkich źle działający wyjątki, które są propagowane w górę za pomocą wykresu zadania podrzędne dołączone.  
  
 Aby uzyskać więcej informacji, zobacz [obsługi wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
## <a name="preventing-a-child-task-from-attaching-to-its-parent"></a>Zapobieganie zadania podrzędnego z odpowiadającym mu zadaniem nadrzędnym  
 Nieobsługiwany wyjątek zgłaszany przez zadanie podrzędne są propagowane do zadaniem nadrzędnym. To zachowanie umożliwia obserwowanie wszystkie wyjątki zadania podrzędnego z jednego katalogu głównego zadania zamiast przechodzenie drzewa zadań. Jednak propagacji wyjątku może sprawiać problemy podczas zadaniem nadrzędnym nie oczekuje załącznika z innego kodu. Rozważmy na przykład aplikację, która wywołuje składnik biblioteki innych firm z <xref:System.Threading.Tasks.Task> obiektu. Jeśli składnik biblioteki innych firm również tworzy <xref:System.Threading.Tasks.Task> obiektu i określa <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> dołączenia do zadaniem nadrzędnym, nieobsługiwanych wyjątków, które występują w zadania podrzędnego propagowane do obiektu nadrzędnego. Może to prowadzić do nieoczekiwanego zachowania w głównym aplikacji.  
  
 Aby zapobiec łączeniu zadania podrzędnego z odpowiadającym jej zadaniem nadrzędnym, określ <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> podczas tworzenia obiektu nadrzędnego <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> obiektu. Gdy zadanie próbuje dołączyć do jego obiektu nadrzędnego i określa element nadrzędny <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opcji, nie będzie mógł dołączyć do elementu nadrzędnego zadania podrzędnego i będzie wykonywać tylko tak, jakby <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> opcja nie została określona.  
  
 Można również zapobiec łączeniu zadania podrzędnego z odpowiadającym mu zadaniem nadrzędnym, gdy zadanie podrzędne nie zakończy się w odpowiednim czasie. Ponieważ zadaniem nadrzędnym nie zakończy się do momentu zakończenia wszystkich zadań podrzędnych, długotrwałe zadania podrzędnego może spowodować ogólną niskiej wydajności aplikacji. Na przykład, który pokazuje, jak poprawić wydajność aplikacji, zapobiegając zadania związane z ich zadaniem nadrzędnym, zobacz [porady: zapobiec łączeniu zadania podrzędnego z dołączenie do elementu nadrzędnego](../../../docs/standard/parallel-programming/how-to-prevent-a-child-task-from-attaching-to-its-parent.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)  
 [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
