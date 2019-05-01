---
title: 'Instrukcje: Anulowanie bloku przepływu danych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: b95f0a3535716c4a01dae52abe38eb850f080cf0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018951"
---
# <a name="how-to-cancel-a-dataflow-block"></a>Instrukcje: Anulowanie bloku przepływu danych
W tym dokumencie pokazano, jak włączyć anulowania w aplikacji. W tym przykładzie użyto Windows Forms, aby pokazać, gdzie elementy robocze są aktywne w potoku przepływu danych, a także skutki anulowania.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a>Aby utworzyć Windows Forms aplikacji  
  
1. Tworzenie języka C# lub Visual Basic **aplikacja interfejsu Windows Forms** projektu. W poniższych krokach projekt nazwano `CancellationWinForms`.  
  
2. Projektant formularzy dla tego formularza Form1.cs (Form1.vb dla języka Visual Basic), Dodaj <xref:System.Windows.Forms.ToolStrip> kontroli.  
  
3. Dodaj <xref:System.Windows.Forms.ToolStripButton> kontrolę <xref:System.Windows.Forms.ToolStrip> kontroli. Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> właściwości <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> i <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości **dodać elementy robocze**.  
  
4. Dodaj drugą <xref:System.Windows.Forms.ToolStripButton> kontrolę <xref:System.Windows.Forms.ToolStrip> kontroli. Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> właściwości <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości **anulować**i <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> właściwość `False`.  
  
5. Dodaj cztery <xref:System.Windows.Forms.ToolStripProgressBar> obiekty do <xref:System.Windows.Forms.ToolStrip> kontroli.  
  
## <a name="creating-the-dataflow-pipeline"></a>Tworzenie potoku przepływu danych  
 W tej sekcji opisano tworzenie potoku przepływu danych, która przetwarza elementy robocze i aktualizuje paski postępu.  
  
### <a name="to-create-the-dataflow-pipeline"></a>Tworzenie potoku przepływu danych  
  
1. W projekcie należy dodać odwołanie do System.Threading.Tasks.Dataflow.dll.  
  
2. Upewnij się, że Form1.cs (Form1.vb dla języka Visual Basic) zawiera następujące `using` instrukcji (`Imports` w języku Visual Basic).  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3. Dodaj `WorkItem` klasy jako wewnętrzny typ `Form1` klasy.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4. Dodaj następujące elementy członkowskie danych do `Form1` klasy.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5. Dodaj następującą metodę `CreatePipeline`, `Form1` klasy.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 Ponieważ `incrementProgress` i `decrementProgress` przepływu danych blokuje działanie w interfejsie użytkownika, ważne jest, czy w wątku interfejsu użytkownika są wykonywane następujące akcje. Aby to osiągnąć, podczas konstruowania tych obiektów, każda oferuje <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> obiekt, który ma <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> właściwością <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> Metoda tworzy <xref:System.Threading.Tasks.TaskScheduler> obiektu, który wykonuje pracę w bieżącym kontekście synchronizacji. Ponieważ `Form1` Konstruktor jest wywoływana z wątku interfejsu użytkownika, akcje w przypadku `incrementProgress` i `decrementProgress` bloków przepływu danych również działać w wątku interfejsu użytkownika.  
  
 W tym przykładzie <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> właściwość podczas jego tworzy elementy członkowskie w potoku. Ponieważ <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> właściwość trwale anuluje wykonanie bloku przepływu danych, cały potok musi zostać ponownie utworzona po użytkownik anuluje operację i chce dodać więcej elementów roboczych do potoku. Aby uzyskać przykład demonstrujący alternatywny sposób anulowanie bloku przepływu danych, dzięki czemu mogą być wykonywane inne prace, po operacji zostało anulowane, zobacz [instruktażu: Korzystanie z przepływu danych w Windows Forms aplikacji](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a>Łączenie potoku przepływu danych z interfejsu użytkownika  
 W tej sekcji opisano sposób podłączania potoku przepływu danych do interfejsu użytkownika. Tworzenie potoku i dodawanie elementów roboczych do potoku, które są kontrolowane przez program obsługi zdarzeń dla **dodać elementy robocze** przycisku. Anulowanie jest inicjowane przez **anulować** przycisku. Gdy użytkownik kliknie jeden z tych przycisków, odpowiednie działanie jest inicjowane w sposób asynchroniczny.  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a>Aby połączyć potoku przepływu danych do interfejsu użytkownika  
  
1. W Projektancie formularza dla tego formularza, należy utworzyć program obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenie **dodać elementy robocze** przycisku.  
  
2. Implementowanie <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenie **dodać elementy robocze** przycisku.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3. W Projektancie formularza dla tego formularza, należy utworzyć program obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> program obsługi zdarzeń dla **anulować** przycisku.  
  
4. Implementowanie <xref:System.Windows.Forms.ToolStripItem.Click> program obsługi zdarzeń dla **anulować** przycisku.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje kompletny kod dla Form1.cs (Form1.vb dla języka Visual Basic).  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 Na poniższej ilustracji przedstawiono uruchomionej aplikacji.  
  
 ![Windows Forms aplikacji](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")  

## <a name="see-also"></a>Zobacz także

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
