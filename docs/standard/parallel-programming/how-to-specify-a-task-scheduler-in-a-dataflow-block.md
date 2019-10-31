---
title: 'Porady: Określanie harmonogramu zadań w bloku przepływu danych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TPL dataflow library, linking to task scheduler in TPL
- Task Parallel Library, dataflows
- task scheduler, linking from TPL
ms.assetid: 27ece374-ed5b-49ef-9cec-b20db34a65e8
ms.openlocfilehash: 2abac1ccf45fc9c9c28e27c132e72fe483a24d75
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122223"
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a>Porady: Określanie harmonogramu zadań w bloku przepływu danych
W tym dokumencie przedstawiono sposób kojarzenia określonego harmonogramu zadań w przypadku korzystania z przepływu danych w aplikacji. W przykładzie używamy klasy <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> w aplikacji Windows Forms do wyświetlania, gdy zadania czytnika są aktywne, a zadanie składnika zapisywania jest aktywne. Używa ona również metody <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>, aby umożliwić uruchamianie bloku przepływu danych w wątku interfejsu użytkownika.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a>Aby utworzyć aplikację Windows Forms  
  
1. Utwórz projekt C# **aplikacji Windows Forms** wizualizacji lub Visual Basic. W poniższych krokach projekt ma nazwę `WriterReadersWinForms`.  
  
2. W projektancie formularzy dla formularza głównego Form1.cs (Form1. vb dla Visual Basic) Dodaj cztery <xref:System.Windows.Forms.CheckBox> kontrolek. Ustaw właściwość <xref:System.Windows.Forms.Control.Text%2A> na **Reader 1** dla `checkBox1`, **czytnika 2** dla `checkBox2`, **czytnika 3** dla `checkBox3`i **składnika zapisywania** dla `checkBox4`. Ustaw właściwość <xref:System.Windows.Forms.Control.Enabled%2A> dla każdej kontrolki, aby `False`.  
  
3. Dodaj kontrolkę <xref:System.Windows.Forms.Timer> do formularza. Ustaw właściwość <xref:System.Windows.Forms.Timer.Interval%2A> na `2500`.  
  
## <a name="adding-dataflow-functionality"></a>Dodawanie funkcji przepływu danych  
 W tej sekcji opisano sposób tworzenia bloków przepływu danych, które uczestniczą w aplikacji oraz jak skojarzyć każdą z nich z harmonogramem zadań.  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a>Aby dodać funkcję przepływu danych do aplikacji  
  
1. W projekcie Dodaj odwołanie do elementu System. Threading. Tasks. przepływu danych. dll.  
  
2. Upewnij się, że Form1.cs (Form1. vb dla Visual Basic) zawiera następujące instrukcje `using` (`Imports` w Visual Basic).  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3. Dodaj element członkowski danych <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> do klasy `Form1`.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4. W konstruktorze `Form1` po wywołaniu `InitializeComponent`, Utwórz obiekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, który przełącza stan obiektów <xref:System.Windows.Forms.CheckBox>.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5. W konstruktorze `Form1` Utwórz obiekt <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> i cztery <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiekty, jeden obiekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> dla każdego obiektu <xref:System.Windows.Forms.CheckBox>. Dla każdego obiektu <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Określ obiekt <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>, który ma właściwość <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> ustawioną na Właściwość <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> dla czytelników, i Właściwość <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> dla składnika zapisywania.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6. W konstruktorze `Form1` Uruchom obiekt <xref:System.Windows.Forms.Timer>.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7. W projektancie formularzy dla formularza głównego Utwórz procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.Timer.Tick> dla czasomierza.  
  
8. Zaimplementuj zdarzenie <xref:System.Windows.Forms.Timer.Tick> dla czasomierza.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 Ponieważ blok `toggleCheckBox` przepływu danych działa w interfejsie użytkownika, należy pamiętać, że ta akcja jest wykonywana w wątku interfejsu użytkownika. Aby to osiągnąć, podczas konstruowania ten obiekt udostępnia obiekt <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>, który ma właściwość <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> ustawioną na <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. Metoda <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> tworzy obiekt <xref:System.Threading.Tasks.TaskScheduler>, który wykonuje prace w bieżącym kontekście synchronizacji. Ponieważ Konstruktor `Form1` jest wywoływany z wątku interfejsu użytkownika, akcja dla bloku `toggleCheckBox` przepływu danych jest również uruchamiana w wątku interfejsu użytkownika.  
  
 Ten przykład używa również klasy <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair>, aby umożliwić działanie niektórych bloków przepływu danych, a inny blok przepływu danych do działania wyłącznie w odniesieniu do wszystkich innych bloków przepływu danych, które działają w tym samym obiekcie <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair>. Ta technika jest przydatna, gdy wiele bloków przepływu danych współużytkuje zasób, a niektóre wymagają wyłącznego dostępu do tego zasobu, ponieważ eliminuje konieczność ręcznej synchronizacji dostępu do tego zasobu. Eliminacja synchronizacji ręcznej może zwiększyć wydajność kodu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje kompletny kod dla Form1.cs (Form1. vb dla Visual Basic).  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
