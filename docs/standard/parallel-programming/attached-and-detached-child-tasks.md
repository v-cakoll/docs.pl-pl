---
title: Dołączone i odłączone zadania podrzędne
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, child tasks
ms.assetid: c95788bf-90a6-4e96-b7bc-58e36a228cc5
ms.openlocfilehash: 8f15ee4f136e3e2df1a4e1c7683467f2a4bc9bc0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123188"
---
# <a name="attached-and-detached-child-tasks"></a>Dołączone i odłączone zadania podrzędne
*Zadanie podrzędne* (lub *zagnieżdżone zadanie)* to <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> wystąpienie utworzone w pełnomocniku użytkownika innego zadania, które jest znane jako zadanie *nadrzędne*. Zadanie podrzędne można odłączyć lub dołączyć. *Odłączone zadanie podrzędne* jest zadaniem, które jest wykonywane niezależnie od jego nadrzędnego. *Dołączone zadanie podrzędne* jest zagnieżdżonym zadaniem utworzonym z opcją, <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> której element nadrzędny nie jawnie lub domyślnie zabrania doniego dojazdu. Zadanie może utworzyć dowolną liczbę dołączonych i odłączonych zadań podrzędnych, ograniczonych tylko zasobami systemowymi.  
  
 W poniższej tabeli wymieniono podstawowe różnice między dwoma rodzajami zadań podrzędnych.  
  
|Kategoria|Odłączone zadania podrzędne|Dołączone zadania podrzędne|  
|--------------|--------------------------|--------------------------|  
|Rodzic czeka na wykonanie zadań podrzędnych.|Nie|Tak|  
|Nadrzędny propaguje wyjątki generowane przez zadania podrzędne.|Nie|Tak|  
|Status rodzica zależy od stanu dziecka.|Nie|Tak|  
  
 W większości scenariuszy zaleca się użycie odłączonych zadań podrzędnych, ponieważ ich relacje z innymi zadaniami są mniej złożone. Dlatego zadania utworzone wewnątrz zadań nadrzędnych są domyślnie odłączane <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> i należy jawnie określić opcję utworzenia dołączonego zadania podrzędnego.  
  
## <a name="detached-child-tasks"></a>Odłączone zadania podrzędne  
 Mimo że zadanie podrzędne jest tworzone przez zadanie nadrzędne, domyślnie jest niezależne od zadania nadrzędnego. W poniższym przykładzie zadanie nadrzędne tworzy jedno proste zadanie podrzędne. Jeśli zostanie uruchomiony przykładowy kod wiele razy, można zauważyć, że dane wyjściowe z przykładu różni się od pokazanego, a także, że dane wyjściowe mogą ulec zmianie przy każdym uruchomieniu kodu. Dzieje się tak, ponieważ zadania nadrzędne i zadania podrzędne są wykonywane niezależnie od siebie; dziecko jest zadaniem odłączonym. Przykład czeka tylko na wykonanie zadania nadrzędnego, a zadanie podrzędne może nie zostać wykonane lub wykonane przed zakończeniem aplikacji konsoli.  
  
 [!code-csharp[TPL_ChildTasks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/nested1.cs#1)]
 [!code-vb[TPL_ChildTasks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/nested1.vb#1)]  
  
 Jeśli zadanie podrzędne jest <xref:System.Threading.Tasks.Task%601> reprezentowane przez <xref:System.Threading.Tasks.Task> obiekt, a nie obiekt, można zapewnić, że zadanie <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> nadrzędne będzie czekać na zakończenie podrzędne, uzyskując dostęp do właściwości dziecka, nawet jeśli jest to odłączone zadanie podrzędne. Właściwość <xref:System.Threading.Tasks.Task%601.Result%2A> blokuje, aż jego zadanie zakończy się, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[TPL_ChildTasks#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/childtasks.cs#4)]
 [!code-vb[TPL_ChildTasks#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/tpl_childtasks.vb#4)]  
  
## <a name="attached-child-tasks"></a>Dołączone zadania podrzędne  
 W przeciwieństwie do zadań podrzędnych odłączonych dołączone zadania podrzędne są ściśle synchronizowane z elementem nadrzędnym. Zadanie podrzędne odłączonym w poprzednim przykładzie można zmienić <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> na dołączone zadanie podrzędne, korzystając z opcji w instrukcji tworzenia zadania, jak pokazano w poniższym przykładzie. W tym kodzie dołączone zadanie podrzędne kończy się przed jego nadrzędnego. W rezultacie dane wyjściowe z przykładu jest taka sama za każdym razem, gdy uruchomisz kod.  
  
 [!code-csharp[TPL_ChildTasks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1.cs#2)]
 [!code-vb[TPL_ChildTasks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1.vb#2)]  
  
 Za pomocą dołączonych zadań podrzędnych można tworzyć ściśle zsynchronizowane wykresy operacji asynchronicznych.  
  
 Jednak zadanie podrzędne można dołączyć do jego nadrzędnego tylko wtedy, gdy jego element nadrzędny nie zabrania dołączonych zadań podrzędne. Zadania nadrzędne mogą jawnie uniemożliwiać dołączanie do <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> nich zadań podrzędnych, określając <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> opcję w konstruktorze klasy zadania nadrzędnego lub w metodzie. Zadania nadrzędne niejawnie uniemożliwiają dołączanie do nich zadań <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> podrzędnych, jeśli są tworzone przez wywołanie metody. Ilustruje to poniższy przykład. Jest identyczny z poprzednim przykładem, z tą różnicą, <xref:System.Threading.Tasks.Task.Run%28System.Action%29?displayProperty=nameWithType> że zadanie <xref:System.Threading.Tasks.TaskFactory.StartNew%28System.Action%29?displayProperty=nameWithType> nadrzędne jest tworzone przez wywołanie metody, a nie metody. Ponieważ zadanie podrzędne nie jest w stanie dołączyć do jego nadrzędnego, dane wyjściowe z przykładu jest nieprzewidywalne. Ponieważ dostępne są domyślne <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> opcje tworzenia <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>zadań dla przeciążeń, w tym przykładzie jest funkcjonalnie odpowiednik pierwszego przykładu w sekcji "Odłączone zadania podrzędne".  
  
 [!code-csharp[TPL_ChildTasks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1a.cs#3)]
 [!code-vb[TPL_ChildTasks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1a.vb#3)]  
  
## <a name="exceptions-in-child-tasks"></a>Wyjątki w zadaniach podrzędnych  
 Jeśli odłączone zadanie podrzędne zgłasza wyjątek, ten wyjątek musi być przestrzegane lub obsługiwane bezpośrednio w zadaniu nadrzędnym, podobnie jak w przypadku każdego zadania niezagnieżdżonego. Jeśli dołączone zadanie podrzędne zgłasza wyjątek, wyjątek jest automatycznie propagowane do zadania nadrzędnego i z powrotem <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> do wątku, który czeka lub próbuje uzyskać dostęp do właściwości zadania. W związku z tym przy użyciu dołączonych zadań podrzędnych, <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> można obsługiwać wszystkie wyjątki tylko w jednym punkcie w wywołaniu wątku wywołującego. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
## <a name="cancellation-and-child-tasks"></a>Zadania związane z anulowaniem i podrzędne  
 Anulowanie zadania jest oparte na współpracy. Oznacza to, że aby można było anulować, każde dołączone lub odłączone zadanie podrzędne musi monitorować stan tokenu anulowania. Jeśli chcesz anulować element nadrzędny i wszystkie jego podrzędne przy użyciu jednego żądania anulowania, można przekazać ten sam token jako argument do wszystkich zadań i zapewnić w każdym zadaniu logikę, aby odpowiedzieć na żądanie w każdym zadaniu. Aby uzyskać więcej informacji, zobacz [Anulowanie zadań](../../../docs/standard/parallel-programming/task-cancellation.md) i [jak: Anulowanie zadania i jego dzieci](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
### <a name="when-the-parent-cancels"></a>Gdy rodzic anuluje  
 Jeśli element nadrzędny anuluje się przed uruchomieniem zadania podrzędnego, dziecko nigdy się nie rozpocznie. Jeśli element nadrzędny anuluje się po jego zadanie podrzędne zostało już uruchomione, podrzędne uruchamia do zakończenia, chyba że ma własną logikę anulowania. Aby uzyskać więcej informacji, zobacz [Anulowanie zadań](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="when-a-detached-child-task-cancels"></a>Gdy odłączone zadanie podrzędne anuluje  
 Jeśli odłączone zadanie podrzędne anuluje się przy użyciu tego samego tokenu, który został przekazany do elementu nadrzędnego, a element nadrzędny nie czeka na zadanie podrzędne, nie jest propagowany wyjątek, ponieważ wyjątek jest traktowany jako niegroźne anulowanie współpracy. To zachowanie jest takie samo jak w przypadku każdego zadania najwyższego poziomu.  
  
### <a name="when-an-attached-child-task-cancels"></a>Gdy dołączone zadanie podrzędne anuluje  
 Gdy dołączone zadanie podrzędne anuluje się przy użyciu tego <xref:System.Threading.Tasks.TaskCanceledException> samego tokenu, który został <xref:System.AggregateException>przekazany do jego zadania nadrzędnego, a jest propagowany do wątku łączącego wewnątrz . Należy poczekać na zadanie nadrzędne, dzięki czemu można obsługiwać wszystkie niegroźne wyjątki oprócz wszystkich wyjątków błędów, które są propagowane przez wykres dołączonych zadań podrzędnych.  
  
 Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
## <a name="preventing-a-child-task-from-attaching-to-its-parent"></a>Uniemożliwianie dołączania zadania podrzędnego do jego rodzica  
 Nieobsługiwany wyjątek, który jest zgłaszany przez zadanie podrzędne jest propagowane do zadania nadrzędnego. Za pomocą tego zachowania można obserwować wszystkie wyjątki zadań podrzędnych z jednego zadania głównego zamiast przechodzenia przez drzewo zadań. Jednak propagacja wyjątków może być problematyczne, gdy zadanie nadrzędne nie oczekuje załącznika z innego kodu. Rozważmy na przykład aplikację, która wywołuje składnik <xref:System.Threading.Tasks.Task> biblioteki innej firmy z obiektu. Jeśli składnik biblioteki innej firmy <xref:System.Threading.Tasks.Task> również tworzy <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> obiekt i określa, aby dołączyć go do zadania nadrzędnego, wszelkie nieobsługiwane wyjątki, które występują w zadaniu podrzędnym propagowane do obiektu nadrzędnego. Może to prowadzić do nieoczekiwanego zachowania w aplikacji głównej.  
  
 Aby zapobiec dołączaniu zadania podrzędnego do <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> zadania nadrzędnego, <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> określ tę opcję podczas tworzenia obiektu nadrzędnego lub obiektu. Gdy zadanie próbuje dołączyć do jego nadrzędnego <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> i element nadrzędny określa opcję, zadanie podrzędne nie będzie <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> mógł dołączyć do nadrzędnego i będzie wykonywać tak, jakby opcja nie została określona.  
  
 Można również zapobiec dołączania zadania podrzędnego do jego nadrzędnego, gdy zadanie podrzędne nie zakończy się w odpowiednim czasie. Ponieważ zadanie nadrzędne nie kończy się, dopóki wszystkie zadania podrzędne nie zakończą się, długotrwałe zadanie podrzędne może spowodować, że ogólna aplikacja będzie działać słabo. Na przykład, który pokazuje, jak zwiększyć wydajność aplikacji, uniemożliwiając zadanie dołączania do zadania nadrzędnego, zobacz [Jak: Zapobieganie dołączaniu zadania podrzędnego do jego nadrzędnego](../../../docs/standard/parallel-programming/how-to-prevent-a-child-task-from-attaching-to-its-parent.md).  
  
## <a name="see-also"></a>Zobacz też

- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
- [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
