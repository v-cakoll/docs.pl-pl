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
ms.openlocfilehash: c8a5d2c1ccb8bb2d272c2582cd416cdfd75506d8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285693"
---
# <a name="attached-and-detached-child-tasks"></a>Dołączone i odłączone zadania podrzędne
*Zadanie podrzędne* (lub *zadanie zagnieżdżone*) jest <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> wystąpieniem, które jest tworzone w delegatze użytkownika innego zadania, który jest znany jako *zadanie nadrzędne*. Zadanie podrzędne może być odłączone lub dołączone. *Odłączone zadanie podrzędne* to zadanie, które jest wykonywane niezależnie od jego elementu nadrzędnego. *Dołączone zadanie podrzędne* to zadanie zagnieżdżone, które jest tworzone z opcją, <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> której element nadrzędny nie jest jawnie lub domyślnie uniemożliwia dołączenie. Zadanie może utworzyć dowolną liczbę dołączonych i odłączonych zadań podrzędnych, ograniczoną tylko przez zasoby systemowe.  
  
 W poniższej tabeli wymieniono podstawowe różnice między dwoma rodzajami zadań podrzędnych.  
  
|Kategoria|Odłączone zadania podrzędne|Dołączone zadania podrzędne|  
|--------------|--------------------------|--------------------------|  
|Element nadrzędny czeka na zakończenie zadań podrzędnych.|Nie|Tak|  
|Element nadrzędny propaguje wyjątki zgłoszone przez zadania podrzędne.|Nie|Tak|  
|Stan elementu nadrzędnego zależy od stanu elementu podrzędnego.|Nie|Tak|  
  
 W większości scenariuszy zalecamy korzystanie z odłączonych zadań podrzędnych, ponieważ ich relacje z innymi zadaniami są mniej skomplikowane. Dlatego zadania utworzone wewnątrz zadań nadrzędnych są odłączone domyślnie i należy jawnie określić <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> opcję tworzenia dołączonego zadania podrzędnego.  
  
## <a name="detached-child-tasks"></a>Odłączone zadania podrzędne  
 Chociaż zadanie podrzędne jest tworzone przez zadanie nadrzędne, domyślnie jest ono niezależne od zadania nadrzędnego. W poniższym przykładzie zadanie nadrzędne tworzy jedno proste zadanie podrzędne. Jeśli przykładowy kod zostanie uruchomiony wielokrotnie, można zauważyć, że dane wyjściowe z przykładu różnią się od tego, a także że dane wyjściowe mogą ulec zmianie za każdym razem, gdy uruchamiasz kod. Dzieje się tak, ponieważ zadanie nadrzędne i podrzędne zadania są wykonywane niezależnie od siebie. obiekt podrzędny jest odłączonym zadaniem. Przykład czeka tylko na ukończenie zadania nadrzędnego, a zadanie podrzędne może nie zostać wykonane lub ukończone przed zakończeniem działania aplikacji konsolowej.  
  
 [!code-csharp[TPL_ChildTasks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/nested1.cs#1)]
 [!code-vb[TPL_ChildTasks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/nested1.vb#1)]  
  
 Jeśli zadanie podrzędne jest reprezentowane przez <xref:System.Threading.Tasks.Task%601> obiekt, a nie <xref:System.Threading.Tasks.Task> obiekt, można upewnić się, że zadanie nadrzędne będzie oczekiwać na ukończenie działania podrzędnego przez uzyskanie dostępu do <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> właściwości elementu podrzędnego, nawet jeśli jest to odłączonego zadanie podrzędne. <xref:System.Threading.Tasks.Task%601.Result%2A>Właściwość jest blokowana do momentu zakończenia jego zadania, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[TPL_ChildTasks#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/childtasks.cs#4)]
 [!code-vb[TPL_ChildTasks#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/tpl_childtasks.vb#4)]  
  
## <a name="attached-child-tasks"></a>Dołączone zadania podrzędne  
 W przeciwieństwie do odłączonych zadań podrzędnych, dołączone zadania podrzędne są ściśle zsynchronizowane z elementem nadrzędnym. Można zmienić odłączone zadanie podrzędne w poprzednim przykładzie do dołączonego zadania podrzędnego przy użyciu <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> opcji w instrukcji tworzenia zadania, jak pokazano w poniższym przykładzie. W tym kodzie, dołączone zadanie podrzędne zostanie zakończone przed jego elementem nadrzędnym. W związku z tym dane wyjściowe z przykładu są takie same przy każdym uruchomieniu kodu.  
  
 [!code-csharp[TPL_ChildTasks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1.cs#2)]
 [!code-vb[TPL_ChildTasks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1.vb#2)]  
  
 Do tworzenia ściśle zsynchronizowanych wykresów operacji asynchronicznych można użyć dołączonych zadań podrzędnych.  
  
 Jednak zadanie podrzędne może dołączyć do jego elementu nadrzędnego tylko wtedy, gdy jego element nadrzędny nie zabrania załączonych zadań podrzędnych. Zadania nadrzędne mogą jawnie uniemożliwić dołączanie do nich zadań podrzędnych przez określenie <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opcji w konstruktorze klas zadania nadrzędnego lub <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> metodzie. Zadania nadrzędne niejawnie uniemożliwiają dołączenie do nich zadań podrzędnych, jeśli są tworzone przez wywołanie <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metody. Ilustruje to poniższy przykład. Jest identyczny z poprzednim przykładem, z tą różnicą, że zadanie nadrzędne jest tworzone przez wywołanie <xref:System.Threading.Tasks.Task.Run%28System.Action%29?displayProperty=nameWithType> metody zamiast <xref:System.Threading.Tasks.TaskFactory.StartNew%28System.Action%29?displayProperty=nameWithType> metody. Ponieważ zadanie podrzędne nie jest w stanie dołączyć do jego elementu nadrzędnego, dane wyjściowe z przykładu są nieprzewidywalne. Ponieważ domyślne opcje tworzenia zadań dla <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> przeciążenia obejmują <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> , ten przykład jest funkcjonalnie odpowiednikiem pierwszego przykładu w sekcji "odłączone zadania podrzędne".  
  
 [!code-csharp[TPL_ChildTasks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1a.cs#3)]
 [!code-vb[TPL_ChildTasks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1a.vb#3)]  
  
## <a name="exceptions-in-child-tasks"></a>Wyjątki w zadaniach podrzędnych  
 Jeśli odłączone zadanie podrzędne zgłasza wyjątek, ten wyjątek musi zostać zaobserwowany lub obsłużony bezpośrednio w zadaniu nadrzędnym, podobnie jak w przypadku dowolnego zadania niezagnieżdżonego. Jeśli dołączone zadanie podrzędne zgłasza wyjątek, wyjątek jest automatycznie propagowany do zadania nadrzędnego i z powrotem do wątku, który czeka lub próbuje uzyskać dostęp do <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> właściwości zadania. W związku z tym przy użyciu dołączonych zadań podrzędnych można obsługiwać wszystkie wyjątki w tylko jednym punkcie w wywołaniu <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> w wątku wywołującym. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków](exception-handling-task-parallel-library.md).  
  
## <a name="cancellation-and-child-tasks"></a>Anulowanie i zadania podrzędne  
 Anulowanie zadania jest spółdzielnią. Oznacza to, że jako możliwe do anulowania każde dołączone lub odłączone zadanie podrzędne musi monitorować stan tokenu anulowania. Aby anulować nadrzędne i wszystkie jego elementy podrzędne przy użyciu jednego żądania anulowania, należy przekazać ten sam token jako argument do wszystkich zadań i udostępnić każdemu zadaniu logikę odpowiedzi na żądanie w każdym zadaniu. Aby uzyskać więcej informacji, zobacz [Anulowanie zadania](task-cancellation.md) i [instrukcje: Anulowanie zadania i jego elementów podrzędnych](how-to-cancel-a-task-and-its-children.md).  
  
### <a name="when-the-parent-cancels"></a>Gdy element nadrzędny zostanie anulowany  
 Jeśli element nadrzędny zostanie anulowany przed rozpoczęciem jego zadania podrzędnego, element podrzędny nigdy nie zostanie uruchomiony. Jeśli element nadrzędny zostanie anulowany po uruchomieniu zadania podrzędnego, element podrzędny zostanie uruchomiony do ukończenia, chyba że ma własną logikę anulowania. Aby uzyskać więcej informacji, zobacz [Anulowanie zadania](task-cancellation.md).  
  
### <a name="when-a-detached-child-task-cancels"></a>Po anulowaniu odłączonego zadania podrzędnego  
 Jeśli odłączone zadanie podrzędne anuluje się za pomocą tego samego tokenu, który został przekazano do elementu nadrzędnego, a element nadrzędny nie czeka na zadanie podrzędne, żaden wyjątek nie jest propagowany, ponieważ wyjątek jest traktowany jako niegroźne anulowanie współpracy. Takie zachowanie jest takie samo jak w przypadku każdego zadania najwyższego poziomu.  
  
### <a name="when-an-attached-child-task-cancels"></a>Gdy dołączone zadanie podrzędne zostanie anulowane  
 Gdy dołączone zadanie podrzędne anuluje się za pomocą tego samego tokenu, który został przekazano do jego zadania nadrzędnego, <xref:System.Threading.Tasks.TaskCanceledException> jest propagowany do wątku przyłączania wewnątrz <xref:System.AggregateException> . Należy poczekać na zadanie nadrzędne, aby można było obsługiwać wszystkie niegroźne wyjątki oprócz wszystkich wyjątków powodujących błędy, które są propagowane za pomocą grafu dołączonych zadań podrzędnych.  
  
 Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków](exception-handling-task-parallel-library.md).  
  
## <a name="preventing-a-child-task-from-attaching-to-its-parent"></a>Uniemożliwianie podłączania zadania podrzędnego do jego elementu nadrzędnego  
 Nieobsłużony wyjątek, który jest generowany przez zadanie podrzędne jest propagowany do zadania nadrzędnego. To zachowanie służy do przestrzegania wszystkich wyjątków zadań podrzędnych z jednego zadania głównego zamiast przechodzenia drzewa zadań. Jednakże Propagacja wyjątku może być problematyczna, gdy zadanie nadrzędne nie oczekuje załącznika od innego kodu. Rozważmy na przykład aplikację, która wywołuje składnik biblioteki innej firmy z <xref:System.Threading.Tasks.Task> obiektu. Jeśli składnik biblioteki innej firmy tworzy również <xref:System.Threading.Tasks.Task> obiekt i określa <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> , że ma zostać dołączony do zadania nadrzędnego, wszelkie Nieobsłużone wyjątki występujące w zadaniu podrzędnym propagują do obiektu nadrzędnego. Może to prowadzić do nieoczekiwanego zachowania w aplikacji głównej.  
  
 Aby zapobiec dołączeniu zadania podrzędnego do jego zadania nadrzędnego, należy określić <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opcję podczas tworzenia elementu nadrzędnego <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> obiektu. Gdy zadanie próbuje dołączyć do jego elementu nadrzędnego, a element nadrzędny określa <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opcję, zadanie podrzędne nie będzie mogło dołączyć do elementu nadrzędnego i zostanie wykonane tak, jakby <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> nie określono opcji.  
  
 Możesz również zapobiec dołączeniu zadania podrzędnego do jego elementu nadrzędnego, gdy zadanie podrzędne nie zakończy się w odpowiednim czasie. Ponieważ zadanie nadrzędne nie kończy się do momentu zakończenia wszystkich zadań podrzędnych, długotrwałe zadanie podrzędne może spowodować słabą pracę aplikacji. Aby zapoznać się z przykładem, który pokazuje, jak zwiększyć wydajność aplikacji, zapobiegając dołączeniu zadania do jego zadania nadrzędnego, zobacz [How to: zapobiegaj dołączeniu zadania podrzędnego do jego elementu nadrzędnego](how-to-prevent-a-child-task-from-attaching-to-its-parent.md).  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie równoległe](index.md)
- [Równoległość danych](data-parallelism-task-parallel-library.md)
