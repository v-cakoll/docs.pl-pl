---
title: "Porady: Anulowanie bloku przepływu danych"
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- dataflow blocks, canceling in TPL
- TPL dataflow library,canceling dataflow blocks
ms.assetid: fbddda0d-da3b-4ec8-a1d6-67ab8573fcd7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3ef7fa62513072e1ee0dc7a8fecf3e600f9c26f2
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-cancel-a-dataflow-block"></a>Porady: Anulowanie bloku przepływu danych
Ten dokument pokazano, jak włączyć anulowania w aplikacji. W tym przykładzie użyto formularzy systemu Windows do wyświetlenia, gdy elementy robocze są aktywne w potoku przepływu danych, a także skutków anulowania.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a>Aby utworzyć systemu Windows w aplikacjach formularzy  
  
1.  Tworzenie C# lub Visual Basic **aplikacji Windows Forms** projektu. W poniższych krokach projektu o nazwie `CancellationWinForms`.  
  
2.  W formularzu projektanta dla tego formularza, pliku Form1.cs (Form1.vb dla [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), Dodaj <xref:System.Windows.Forms.ToolStrip> formantu.  
  
3.  Dodaj <xref:System.Windows.Forms.ToolStripButton> formant <xref:System.Windows.Forms.ToolStrip> formantu. Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> właściwości <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> i <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości **dodać elementy robocze**.  
  
4.  Dodaj drugi <xref:System.Windows.Forms.ToolStripButton> formant <xref:System.Windows.Forms.ToolStrip> formantu. Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> właściwości <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości **anulować**i <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> właściwości `False`.  
  
5.  Dodaj cztery <xref:System.Windows.Forms.ToolStripProgressBar> obiekty do <xref:System.Windows.Forms.ToolStrip> formantu.  
  
## <a name="creating-the-dataflow-pipeline"></a>Tworzenie potoku przepływu danych  
 Ta sekcja zawiera opis sposobu tworzenia potoku przepływu danych, która przetwarza elementy robocze i aktualizuje paski postępu.  
  
### <a name="to-create-the-dataflow-pipeline"></a>Do utworzenia potoku przepływu danych  
  
1.  W projekcie Dodaj odwołanie do System.Threading.Tasks.Dataflow.dll.  
  
2.  Upewnij się, że pliku Form1.cs (Form1.vb dla [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) zawiera następujące `using` instrukcje (`Imports` w [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3.  Dodaj `WorkItem` klasy jako wewnętrzny typ `Form1` klasy.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4.  Dodaj następujące elementy członkowskie danych, aby `Form1` klasy.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5.  Dodaj następującą metodę `CreatePipeline`, do `Form1` klasy.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 Ponieważ `incrementProgress` i `decrementProgress` przepływu danych bloki działania w interfejsie użytkownika, ważne jest, że te zdarzenia w wątku interfejsu użytkownika. Aby to zrobić, podczas konstruowania te obiekty każdego podaj <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> obiektu, który ma <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> ustawioną właściwość <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> Metoda tworzy <xref:System.Threading.Tasks.TaskScheduler> obiekt, który przeprowadza pracę na bieżący kontekst synchronizacji. Ponieważ `Form1` Konstruktor jest wywoływana z wątku interfejsu użytkownika, akcje `incrementProgress` i `decrementProgress` bloków przepływu danych również uruchomić w wątku interfejsu użytkownika.  
  
 W tym przykładzie <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> właściwości, gdy tworzy on elementy członkowskie potoku. Ponieważ <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> właściwości trwale anuluje wykonywania bloku przepływu danych, całe potoku muszą zostać ponownie utworzone po użytkownik anulował operację i chce dodać więcej elementów roboczych do potoku. Na przykład, który pokazuje alternatywny sposób anulowanie bloku przepływu danych, dzięki czemu inne zadania mogą być wykonywane po operacja została anulowana, zobacz [wskazówki: Korzystanie z przepływu danych w aplikacji formularzy systemu Windows](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a>Połączenie potoku przepływu danych interfejsu użytkownika  
 W tej sekcji opisano sposób podłączania potoku przepływu danych interfejsu użytkownika. Tworzenie potoku, a także dodawanie elementów roboczych do potoku są kontrolowane przez program obsługi zdarzeń dla **dodać elementy robocze** przycisku. Anulowanie jest inicjowane przez **anulować** przycisku. Gdy użytkownik kliknie jeden z tych przycisków, odpowiednie działanie jest inicjowane w sposób asynchroniczny.  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a>Aby połączyć potoku przepływu danych interfejsu użytkownika  
  
1.  W projektancie formularzy dla tego formularza należy utworzyć programu obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia dla **dodać elementy robocze** przycisku.  
  
2.  Implementowanie <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia dla **dodać elementy robocze** przycisku.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3.  W projektancie formularzy dla tego formularza należy utworzyć programu obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> programu obsługi zdarzeń dla **anulować** przycisku.  
  
4.  Implementowanie <xref:System.Windows.Forms.ToolStripItem.Click> programu obsługi zdarzeń dla **anulować** przycisku.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia kompletny kod dla pliku Form1.cs (Form1.vb dla [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 Na poniższej ilustracji przedstawiono działającej aplikacji.  
  
 ![Aplikacji formularzy systemu Windows](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")  

## <a name="see-also"></a>Zobacz też  
 [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
