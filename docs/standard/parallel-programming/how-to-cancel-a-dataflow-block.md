---
title: 'Porady: Anulowanie bloku przepływu danych'
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
ms.openlocfilehash: aa175d95f27fcbf28c3f3da3eaa7b8f7988681e1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140094"
---
# <a name="how-to-cancel-a-dataflow-block"></a>Porady: Anulowanie bloku przepływu danych
W tym dokumencie przedstawiono sposób włączania anulowania w aplikacji. Ten przykład używa Windows Forms, aby pokazać, gdzie elementy robocze są aktywne w potoku przepływu danych, a także wpływ anulowania.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a>Aby utworzyć aplikację Windows Forms  
  
1. Utwórz projekt C# **aplikacji Windows Forms** lub Visual Basic. W poniższych krokach projekt ma nazwę `CancellationWinForms`.  
  
2. W projektancie formularzy dla formularza głównego Form1.cs (Form1. vb dla Visual Basic) Dodaj kontrolkę <xref:System.Windows.Forms.ToolStrip>.  
  
3. Dodaj kontrolkę <xref:System.Windows.Forms.ToolStripButton> do kontrolki <xref:System.Windows.Forms.ToolStrip>. Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> na <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> i Właściwość <xref:System.Windows.Forms.ToolStripItem.Text%2A>, aby **dodać elementy robocze**.  
  
4. Dodaj drugą kontrolkę <xref:System.Windows.Forms.ToolStripButton> do kontrolki <xref:System.Windows.Forms.ToolStrip>. Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> na <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, właściwość <xref:System.Windows.Forms.ToolStripItem.Text%2A> na wartość **Cancel**i Właściwość <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> na `False`.  
  
5. Dodaj cztery <xref:System.Windows.Forms.ToolStripProgressBar> obiektów do kontrolki <xref:System.Windows.Forms.ToolStrip>.  
  
## <a name="creating-the-dataflow-pipeline"></a>Tworzenie potoku przepływu danych  
 W tej sekcji opisano sposób tworzenia potoku przepływu danych, który przetwarza elementy robocze i aktualizuje paski postępu.  
  
### <a name="to-create-the-dataflow-pipeline"></a>Aby utworzyć potok przepływu danych  
  
1. W projekcie Dodaj odwołanie do elementu System. Threading. Tasks. przepływu danych. dll.  
  
2. Upewnij się, że Form1.cs (Form1. vb dla Visual Basic) zawiera następujące instrukcje `using` (`Imports` w Visual Basic).  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3. Dodaj klasę `WorkItem` jako typ wewnętrzny klasy `Form1`.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4. Dodaj następujące elementy członkowskie danych do klasy `Form1`.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5. Dodaj następującą metodę, `CreatePipeline`, do klasy `Form1`.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 Ponieważ `incrementProgress` i `decrementProgress` bloków przepływu danych działają w interfejsie użytkownika, ważne jest, aby te akcje miały miejsce w wątku interfejsu użytkownika. Aby to osiągnąć, podczas konstruowania obiekty każdy udostępnia obiekt <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>, który ma właściwość <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> ustawioną na <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. Metoda <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> tworzy obiekt <xref:System.Threading.Tasks.TaskScheduler>, który wykonuje prace w bieżącym kontekście synchronizacji. Ponieważ Konstruktor `Form1` jest wywoływany z wątku interfejsu użytkownika, akcje dla bloków `incrementProgress` i `decrementProgress` przepływu danych również są uruchamiane w wątku interfejsu użytkownika.  
  
 Ten przykład ustawia właściwość <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> podczas konstrukcji elementów członkowskich potoku. Ponieważ właściwość <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> trwale anuluje wykonywanie bloku przepływu danych, cały potok musi zostać utworzony ponownie, gdy użytkownik anuluje operację, a następnie chce dodać więcej elementów roboczych do potoku. Przykład demonstrujący alternatywny sposób anulowania bloku przepływu danych, dzięki czemu można wykonać inną pracę po anulowaniu operacji, zobacz [Przewodnik: używanie przepływu danych w aplikacji Windows Forms](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a>Łączenie potoku przepływu danych z interfejsem użytkownika  
 W tej sekcji opisano sposób łączenia potoku przepływu danych z interfejsem użytkownika. Tworzenie potoku i Dodawanie elementów roboczych do potoku jest kontrolowane przez program obsługi zdarzeń dla przycisku **Dodaj elementy robocze** . Anulowanie jest inicjowane przez przycisk **Anuluj** . Gdy użytkownik kliknie jeden z tych przycisków, odpowiednia akcja zostanie zainicjowana w sposób asynchroniczny.  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a>Aby połączyć potok przepływu danych z interfejsem użytkownika  
  
1. W projektancie formularzy dla formularza głównego Utwórz procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.ToolStripItem.Click> dla przycisku **Dodaj elementy robocze** .  
  
2. Zaimplementuj zdarzenie <xref:System.Windows.Forms.ToolStripItem.Click> dla przycisku **Dodaj elementy robocze** .  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3. W projektancie formularzy dla formularza głównego Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> obsługi zdarzeń dla przycisku **Anuluj** .  
  
4. Zaimplementuj procedurę obsługi zdarzeń <xref:System.Windows.Forms.ToolStripItem.Click> dla przycisku **Anuluj** .  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje kompletny kod dla Form1.cs (Form1. vb dla Visual Basic).  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 Na poniższej ilustracji przedstawiono działającą aplikację.  
  
 ![Aplikacja Windows Forms](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")  

## <a name="see-also"></a>Zobacz także

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
