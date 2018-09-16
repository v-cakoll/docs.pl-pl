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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83451af25006e9da396a3e6618cbecee036e9fe2
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45687676"
---
# <a name="attached-and-detached-child-tasks"></a>Dołączone i odłączone zadania podrzędne
A *zadanie podrzędne* (lub *zadanie zagnieżdżone*) jest <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> wystąpienia, który jest tworzony w delegowanym użytkowniku innego zadania, który jest znany jako *zadanie nadrzędne*. Zadanie podrzędne może odłączone lub dołączone. A *odłączone zadanie podrzędne* jest zadaniem wykonywanym niezależnie od jego obiektu nadrzędnego. *Dołączone zadanie podrzędne* to zagnieżdżone zadanie, które są tworzone za pomocą <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> opcji, których elementem nadrzędnym nie jawnie lub domyślnie zabronić jako załączniki. Zadanie może utworzyć dowolną liczbę podrzędnych dołączonych i odłączonych zadań podrzędnych, ograniczony tylko ilością zasobów systemowych.  
  
 Poniższa tabela zawiera listę podstawowych różnic między dwoma rodzajami zadań podrzędnych.  
  
|Kategoria|Odłączonych zadań podrzędnych|Dołączonych zadań podrzędnych|  
|--------------|--------------------------|--------------------------|  
|Zadanie nadrzędne czeka na zakończenie zadań podrzędnych.|Nie|Tak|  
|Zadanie nadrzędne propaguje wyjątki generowane przez zadania podrzędne.|Nie|Tak|  
|Stan obiektu nadrzędnego zależy od stanu elementu podrzędnego.|Nie|Tak|  
  
 W większości scenariuszy firma Microsoft zaleca używanie odłączonych zadań podrzędnych, ponieważ ich relacje z innymi zadaniami są mniej skomplikowane. Oznacza to dlaczego zadania utworzone wewnątrz zadania nadrzędnego są odłączone domyślnie, i należy jawnie określić <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> opcję, aby utworzyć dołączone zadanie podrzędne.  
  
## <a name="detached-child-tasks"></a>Odłączonych zadań podrzędnych  
 Mimo że zadanie podrzędne jest tworzone przez zadanie nadrzędne, domyślnie jest niezależne od zadania nadrzędnego. W poniższym przykładzie zadanie nadrzędne tworzy jedno proste zadanie podrzędne. Jeśli przykładowy kod jest wykonywany wielokrotnie, można zauważyć, że dane wyjściowe z przykładu różnią się od wyświetlanych, a również że dane wyjściowe mogą ulec zmianie każdym uruchomieniu kodu. Dzieje się tak, ponieważ zadanie nadrzędne i podrzędne działają niezależnie od siebie; podrzędne jest zadaniem odłączonym. Przykład czeka tylko dla zadania nadrzędnego ukończyć i nie może być wykonywane zadanie podrzędne lub kończy się zakończona, zanim aplikacja konsoli.  
  
 [!code-csharp[TPL_ChildTasks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/nested1.cs#1)]
 [!code-vb[TPL_ChildTasks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/nested1.vb#1)]  
  
 Jeśli zadanie podrzędne jest reprezentowane przez <xref:System.Threading.Tasks.Task%601> obiektu zamiast <xref:System.Threading.Tasks.Task> obiektu, należy zapewnić, że zadanie nadrzędne będzie czekać podrzędnych zakończyć, uzyskując dostęp do <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> właściwości zadania podrzędnego, nawet jeśli odłączone zadanie podrzędne. <xref:System.Threading.Tasks.Task%601.Result%2A> Właściwość blokuje zakończenia jej zadania, co ilustruje poniższy przykład.  
  
 [!code-csharp[TPL_ChildTasks#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/childtasks.cs#4)]
 [!code-vb[TPL_ChildTasks#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/tpl_childtasks.vb#4)]  
  
## <a name="attached-child-tasks"></a>Dołączonych zadań podrzędnych  
 W przeciwieństwie do odłączonych zadań podrzędnych dołączone zadania podrzędne są ściśle zsynchronizowane z obiektem nadrzędnym. Odłączone zadanie podrzędne w poprzednim przykładzie się dołączonym zadaniem podrzędnym można zmienić za pomocą <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> opcji instrukcji tworzenia zadania, jak pokazano w poniższym przykładzie. W tym kodzie dołączone zadanie podrzędne zakończy się przed swoim obiektem nadrzędnym. Co w efekcie wynika z przykładu jest taka sama każdego wykonywania kodu.  
  
 [!code-csharp[TPL_ChildTasks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1.cs#2)]
 [!code-vb[TPL_ChildTasks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1.vb#2)]  
  
 Można użyć dołączonych zadań podrzędnych, aby utworzyć ściśle zsynchronizowane wykresy operacji asynchronicznych.  
  
 Jednak zadanie podrzędne można dołączyć do elementu nadrzędnego, tylko wtedy, gdy jego element nadrzędny nie zabraniają dołączonych zadań podrzędnych. Zadaniom nadrzędnym można jawnie zapobiec zadań podrzędnych z zadaniem, określając <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opcji w konstruktorze klasy zadania nadrzędnego lub <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metody. Zadaniom nadrzędnym niejawnie uniemożliwić zadań podrzędnych dołączanie do nich, jeśli są one tworzone przez wywołanie metody <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metody. Ilustruje to poniższy przykład. Jest identyczny z poprzednim, z tą różnicą, że zadanie nadrzędne jest tworzony przez wywołanie <xref:System.Threading.Tasks.Task.Run%28System.Action%29?displayProperty=nameWithType> metody zamiast <xref:System.Threading.Tasks.TaskFactory.StartNew%28System.Action%29?displayProperty=nameWithType> metody. Zadanie podrzędne nie jest możliwe dołączanie do elementu nadrzędnego, wynika z przykładu jest nieprzewidywalne. Ponieważ opcje tworzenia zadań domyślne <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> przeciążenia zawierają <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>, ten przykład jest funkcjonalnie równoważny programowi pierwszy przykład w sekcji "Odłączone zadania podrzędne".  
  
 [!code-csharp[TPL_ChildTasks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1a.cs#3)]
 [!code-vb[TPL_ChildTasks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1a.vb#3)]  
  
## <a name="exceptions-in-child-tasks"></a>Wyjątki w zadaniach podrzędnych  
 Jeśli odłączone zadanie podrzędne zgłasza wyjątek, ten wyjątek musi przestrzegać lub obsługiwany bezpośrednio w zadania nadrzędnym, podobnie jak w przypadku dowolnego zadania niezagnieżdżonego. Jeśli dołączone zadanie podrzędne zgłasza wyjątek, wyjątek jest automatycznie propagowany do zadania nadrzędnego i z powrotem do wątku, który czeka lub próbuje uzyskać dostęp zadania podrzędnego <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> właściwości. W związku z tym, za pomocą dołączonych zadań podrzędnych, może obsługiwać wszystkie wyjątki w tylko jednym punkcie w wywołaniu <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> na wątku wywołującym. Aby uzyskać więcej informacji, zobacz [wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
## <a name="cancellation-and-child-tasks"></a>Anulowanie i zadania podrzędne  
 Anulowanie zadania jest wspólne. Oznacza to aby móc być anulowanym, co dołączone lub odłączone zadanie podrzędne musi monitorować stan tokenu odwołania. Jeśli chcesz anulować nadrzędne i wszystkie jego elementy podrzędne, stosując jedno żądanie anulowania, przekaż ten sam token jako argument do wszystkich zadań i dostarczyć w każdym zadaniu logikę odpowiadania na żądanie w każdym zadaniu. Aby uzyskać więcej informacji, zobacz [anulowanie zadania](../../../docs/standard/parallel-programming/task-cancellation.md) i [porady: anulowanie zadania i jego elementy podrzędne](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
### <a name="when-the-parent-cancels"></a>Kiedy anulowany jest element nadrzędny  
 Jeśli zadanie nadrzędne anuluje się przed rozpoczęciem jego zadania podrzędne, nigdy nie rozpoczyna się elementem podrzędnym. Jeśli zadanie nadrzędne anuluje się po jego zadanie podrzędne już się rozpoczęła, element podrzędny wykonywanie aż do zakończenia, chyba że ma własną logikę anulowania. Aby uzyskać więcej informacji, zobacz [anulowanie zadania](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="when-a-detached-child-task-cancels"></a>Kiedy odłączone zadanie podrzędne zostaje anulowane  
 Jeśli odłączone zadanie podrzędne anuluje się za pomocą tego samego tokenu, który został przekazany do elementu nadrzędnego, a zadanie nadrzędne nie oczekuje na zadanie podrzędne, jest propagowany żaden wyjątek, ponieważ wyjątek jest traktowany jako łagodne anulowanie. To zachowanie jest takie same jak w przypadku dowolnego zadania najwyższego poziomu.  
  
### <a name="when-an-attached-child-task-cancels"></a>Kiedy dołączone zadanie podrzędne zostaje anulowane  
 Gdy dołączone zadanie podrzędne anuluje się za pomocą tego samego tokenu, który został przekazany do jego zadania nadrzędnego <xref:System.Threading.Tasks.TaskCanceledException> jest propagowana do sąsiadującego wątku wewnątrz <xref:System.AggregateException>. Należy poczekać dla zadania nadrzędnego, dzięki czemu może obsługiwać wszystkie wyjątki niegroźne, oprócz wszystkie łagodne wyjątki, które są propagowane w górę poprzez wykres dołączonych zadań podrzędnych.  
  
 Aby uzyskać więcej informacji, zobacz [wyjątków](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
## <a name="preventing-a-child-task-from-attaching-to-its-parent"></a>Zapobieganie zadania podrzędnego z odpowiadającym mu zadaniem nadrzędnym  
 Nieobsłużony wyjątek, który jest generowany przez zadanie podrzędne jest propagowany do zadania nadrzędnego. To zachowanie służy do obserwowania wszystkich wyjątków zadań podrzędnych z jednego zadania głównego zamiast przechodzić przez drzewo zadań. Jednak Propagacja wyjątków może być problematyczne, gdy zadanie nadrzędne nie spodziewa się załącznika z innego kodu. Rozważmy na przykład aplikację, która wywołuje składnik innej biblioteki z <xref:System.Threading.Tasks.Task> obiektu. Jeśli składnik innej biblioteki również tworzy <xref:System.Threading.Tasks.Task> obiektu i określa <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> ma on być dołączony zadania nadrzędnego, nieobsłużone wyjątki, które występują w zadanie podrzędne propagowane do obiektu nadrzędnego. Może to prowadzić do nieoczekiwanego zachowania w głównej aplikacji.  
  
 Aby zapobiec łączeniu zadania podrzędnego z zadaniem do jego zadania nadrzędnego, należy określić <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opcji podczas tworzenia obiektu nadrzędnego <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> obiektu. Kiedy zadanie próbuje dołączyć do elementu nadrzędnego i nadrzędne Określa <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> , zadanie podrzędne nie będzie mógł dołączyć do elementu nadrzędnego i będą wykonywane tylko tak, jakby <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> nie określono opcję.  
  
 Można również zapobiec łączeniu zadania podrzędnego z odpowiadającym mu zadaniem nadrzędnym, gdy zadanie podrzędne nie zakończy się w odpowiednim czasie. Ponieważ zadanie nadrzędne nie zakończy się aż do zakończenia wszystkich zadań podrzędnych, długo uruchamiające się zadanie podrzędne może spowodować jej ogólną niską. Na przykład, który pokazuje, jak zwiększyć wydajność aplikacji, uniemożliwiając zadaniu dołączenie do jego zadania nadrzędnego, zobacz [jak: uniemożliwić dołączanie zadania podrzędnego do elementu nadrzędnego](../../../docs/standard/parallel-programming/how-to-prevent-a-child-task-from-attaching-to-its-parent.md).  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)  
- [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
