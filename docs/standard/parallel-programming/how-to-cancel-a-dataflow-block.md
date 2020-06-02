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
ms.openlocfilehash: 530c231deeaba007975849ab6dc41f4da6a859ea
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285550"
---
# <a name="how-to-cancel-a-dataflow-block"></a>Instrukcje: Anulowanie bloku przepływu danych
W tym dokumencie przedstawiono sposób włączania anulowania w aplikacji. Ten przykład używa Windows Forms, aby pokazać, gdzie elementy robocze są aktywne w potoku przepływu danych, a także wpływ anulowania.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a>Aby utworzyć aplikację Windows Forms  
  
1. Utwórz projekt **aplikacji Windows Forms** C# lub Visual Basic. W poniższych krokach projekt ma nazwę `CancellationWinForms` .  
  
2. W projektancie formularzy dla formularza głównego Form1.cs (Form1. vb dla Visual Basic) Dodaj <xref:System.Windows.Forms.ToolStrip> kontrolkę.  
  
3. Dodaj <xref:System.Windows.Forms.ToolStripButton> kontrolkę do <xref:System.Windows.Forms.ToolStrip> kontrolki. Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> Właściwość na <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> i właściwość, <xref:System.Windows.Forms.ToolStripItem.Text%2A> Aby **dodać elementy robocze**.  
  
4. Dodaj drugą <xref:System.Windows.Forms.ToolStripButton> kontrolkę do <xref:System.Windows.Forms.ToolStrip> kontrolki. Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> na <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> , <xref:System.Windows.Forms.ToolStripItem.Text%2A> Właściwość do **anulowania**i <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> Właściwość na `False` .  
  
5. Dodaj cztery <xref:System.Windows.Forms.ToolStripProgressBar> obiekty do <xref:System.Windows.Forms.ToolStrip> kontrolki.  
  
## <a name="creating-the-dataflow-pipeline"></a>Tworzenie potoku przepływu danych  
 W tej sekcji opisano sposób tworzenia potoku przepływu danych, który przetwarza elementy robocze i aktualizuje paski postępu.  
  
### <a name="to-create-the-dataflow-pipeline"></a>Aby utworzyć potok przepływu danych  
  
1. W projekcie Dodaj odwołanie do elementu System. Threading. Tasks. przepływu danych. dll.  
  
2. Upewnij się, że Form1.cs (Form1. vb dla Visual Basic) zawiera następujące `using` instrukcje ( `Imports` w Visual Basic).  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3. Dodaj `WorkItem` klasę jako typ wewnętrzny `Form1` klasy.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4. Dodaj następujące składowe danych do `Form1` klasy.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5. Dodaj następującą metodę `CreatePipeline` do `Form1` klasy.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 Ponieważ `incrementProgress` bloki i `decrementProgress` przepływu danych działają na interfejsie użytkownika, należy pamiętać, że te akcje są wykonywane w wątku interfejsu użytkownika. Aby to osiągnąć, podczas konstruowania obiekty każdy udostępnia <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> obiekt, który ma <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> Właściwość ustawioną na <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> . <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>Metoda tworzy <xref:System.Threading.Tasks.TaskScheduler> obiekt, który wykonuje prace w bieżącym kontekście synchronizacji. Ponieważ `Form1` Konstruktor jest wywoływany z wątku interfejsu użytkownika, akcje dla `incrementProgress` `decrementProgress` bloków i przepływu danych są również uruchamiane w wątku interfejsu użytkownika.  
  
 Ten przykład ustawia <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> Właściwość podczas konstrukcji elementów członkowskich potoku. Ponieważ <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> Właściwość trwale anuluje wykonywanie bloku przepływu danych, cały potok musi zostać utworzony ponownie, gdy użytkownik anuluje operację, a następnie chce dodać więcej elementów roboczych do potoku. Przykład demonstrujący alternatywny sposób anulowania bloku przepływu danych, dzięki czemu można wykonać inną pracę po anulowaniu operacji, zobacz [Przewodnik: używanie przepływu danych w aplikacji Windows Forms](walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a>Łączenie potoku przepływu danych z interfejsem użytkownika  
 W tej sekcji opisano sposób łączenia potoku przepływu danych z interfejsem użytkownika. Tworzenie potoku i Dodawanie elementów roboczych do potoku jest kontrolowane przez program obsługi zdarzeń dla przycisku **Dodaj elementy robocze** . Anulowanie jest inicjowane przez przycisk **Anuluj** . Gdy użytkownik kliknie jeden z tych przycisków, odpowiednia akcja zostanie zainicjowana w sposób asynchroniczny.  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a>Aby połączyć potok przepływu danych z interfejsem użytkownika  
  
1. W projektancie formularzy dla formularza głównego Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia dla przycisku **Dodaj elementy robocze** .  
  
2. Zaimplementuj <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenie dla przycisku **Dodaj elementy robocze** .  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3. W projektancie formularzy dla formularza głównego Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> programu obsługi zdarzeń dla przycisku **Anuluj** .  
  
4. Zaimplementuj <xref:System.Windows.Forms.ToolStripItem.Click> procedurę obsługi zdarzeń dla przycisku **Anuluj** .  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje kompletny kod dla Form1.cs (Form1. vb dla Visual Basic).  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 Na poniższej ilustracji przedstawiono działającą aplikację.  
  
 ![Aplikacja Windows Forms](media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")  

## <a name="see-also"></a>Zobacz także

- [Przepływ danych](dataflow-task-parallel-library.md)
