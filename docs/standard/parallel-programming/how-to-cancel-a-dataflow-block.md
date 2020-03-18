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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140094"
---
# <a name="how-to-cancel-a-dataflow-block"></a>Porady: Anulowanie bloku przepływu danych
W tym dokumencie pokazano, jak włączyć anulowanie w aplikacji. W tym przykładzie użyto formularzy systemu Windows, aby pokazać, gdzie elementy robocze są aktywne w potoku przepływu danych, a także skutki anulowania.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a>Aby utworzyć aplikację formularzy systemu Windows  
  
1. Utwórz projekt aplikacji **formularzy systemu** Windows w języku C# lub Visual Basic. W poniższych krokach projekt `CancellationWinForms`nosi nazwę .  
  
2. W projektancie formularza dla formularza głównego Form1.cs (Form1.vb <xref:System.Windows.Forms.ToolStrip> dla języka Visual Basic) dodaj formant.  
  
3. Dodaj <xref:System.Windows.Forms.ToolStripButton> formant do <xref:System.Windows.Forms.ToolStrip> formantu. Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> właściwość <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> i <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwość, aby **dodać elementy robocze**.  
  
4. Dodaj drugi <xref:System.Windows.Forms.ToolStripButton> formant <xref:System.Windows.Forms.ToolStrip> do formantu. Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> właściwość <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>na <xref:System.Windows.Forms.ToolStripItem.Text%2A> , właściwość **Anuluj**, a <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> właściwość na `False`.  
  
5. Dodaj <xref:System.Windows.Forms.ToolStripProgressBar> cztery obiekty <xref:System.Windows.Forms.ToolStrip> do formantu.  
  
## <a name="creating-the-dataflow-pipeline"></a>Tworzenie potoku przepływu danych  
 W tej sekcji opisano sposób tworzenia potoku przepływu danych, który przetwarza elementy robocze i aktualizuje paski postępu.  
  
### <a name="to-create-the-dataflow-pipeline"></a>Aby utworzyć potok przepływu danych  
  
1. W projekcie dodaj odwołanie do pliku System.Threading.Tasks.Dataflow.dll.  
  
2. Upewnij się, że Form1.cs (Form1.vb `using` dla`Imports` języka Visual Basic) zawiera następujące instrukcje (w języku Visual Basic).  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3. Dodaj `WorkItem` klasę jako wewnętrzny typ `Form1` klasy.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4. Dodaj następujące elementy członkowskie `Form1` danych do klasy.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5. Dodaj następującą `CreatePipeline`metodę, `Form1` , do klasy.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 Ponieważ `incrementProgress` bloki przepływu `decrementProgress` danych działają na interfejsie użytkownika, ważne jest, aby te akcje wystąpiły w wątku interfejsu użytkownika. Aby to osiągnąć, podczas budowy <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> te obiekty <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> każdy podać <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>obiekt, który ma właściwość ustawioną na . Metoda <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> tworzy <xref:System.Threading.Tasks.TaskScheduler> obiekt, który wykonuje pracę na bieżącym kontekście synchronizacji. Ponieważ `Form1` konstruktor jest wywoływana z wątku `incrementProgress` interfejsu `decrementProgress` użytkownika, akcje dla bloków i przepływu danych również uruchomić w wątku interfejsu użytkownika.  
  
 W tym <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> przykładzie ustawia właściwość, gdy konstruuje elementy członkowskie potoku. Ponieważ <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> właściwość trwale anuluje wykonanie bloku przepływu danych, cały potok musi zostać utworzony ponownie po użytkownik anuluje operację, a następnie chce dodać więcej elementów roboczych do potoku. Na przykład, który pokazuje alternatywny sposób anulowania bloku przepływu danych, dzięki czemu można wykonać inną pracę po anulowaniu operacji, zobacz [Instruktaż: Korzystanie z przepływu danych w aplikacji formularzy systemu Windows](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a>Podłączanie potoku przepływu danych do interfejsu użytkownika  
 W tej sekcji opisano sposób łączenia potoku przepływu danych z interfejsem użytkownika. Zarówno tworzenie potoku, jak i dodawanie elementów roboczych do potoku są kontrolowane przez program obsługi zdarzeń dla przycisku **Dodaj elementy robocze.** Anulowanie jest inicjowane przez przycisk **Anuluj.** Gdy użytkownik kliknie jeden z tych przycisków, odpowiednia akcja jest inicjowana w sposób asynchroniczny.  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a>Aby połączyć potok przepływu danych z interfejsem użytkownika  
  
1. W projektancie formularza dla formularza głównego utwórz program obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia dla przycisku Dodaj elementy **robocze.**  
  
2. Zaimplementuj <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenie dla przycisku **Dodaj elementy robocze.**  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3. W projektancie formularza dla formularza głównego utwórz program obsługi zdarzeń dla programu obsługi <xref:System.Windows.Forms.ToolStripItem.Click> zdarzeń dla przycisku **Anuluj.**  
  
4. Zaimplementuj program <xref:System.Windows.Forms.ToolStripItem.Click> obsługi zdarzeń dla przycisku **Anuluj.**  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono kompletny kod Form1.cs (Form1.vb dla języka Visual Basic).  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 Na poniższej ilustracji przedstawiono uruchomioną aplikację.  
  
 ![Aplikacja formularzy systemu Windows](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")  

## <a name="see-also"></a>Zobacz też

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
