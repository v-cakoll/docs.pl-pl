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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73122223"
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a>Porady: Określanie harmonogramu zadań w bloku przepływu danych
W tym dokumencie pokazano, jak skojarzyć określonego harmonogramu zadań podczas korzystania z przepływu danych w aplikacji. W przykładzie <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> użyto klasy w aplikacji Formularze systemu Windows, aby pokazać, kiedy zadania czytnika są aktywne i gdy zadanie modułu zapisującego jest aktywny. Używa również <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> metody, aby włączyć blok przepływu danych do uruchomienia w wątku interfejsu użytkownika.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a>Aby utworzyć aplikację formularzy systemu Windows  
  
1. Utwórz projekt visual C# lub Visual Basic **Windows Forms Application.** W poniższych krokach projekt `WriterReadersWinForms`nosi nazwę .  
  
2. W projektancie formularza głównego Form1.cs (Form1.vb dla języka <xref:System.Windows.Forms.CheckBox> Visual Basic) dodaj cztery formanty. Ustaw <xref:System.Windows.Forms.Control.Text%2A> właściwość na Czytnik `checkBox1` **1** dla `checkBox2`, Czytnik **2** dla `checkBox4`, Czytelnik **3** dla `checkBox3`i Moduł **zapisujący** dla . Ustaw <xref:System.Windows.Forms.Control.Enabled%2A> właściwość dla każdego `False`formantu na .  
  
3. Dodaj <xref:System.Windows.Forms.Timer> formant do formularza. Ustaw <xref:System.Windows.Forms.Timer.Interval%2A> właściwość `2500`na .  
  
## <a name="adding-dataflow-functionality"></a>Dodawanie funkcji przepływu danych  
 W tej sekcji opisano sposób tworzenia bloków przepływu danych, które uczestniczą w aplikacji i jak skojarzyć każdy z nich z harmonogramem zadań.  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a>Aby dodać funkcje przepływu danych do aplikacji  
  
1. W projekcie dodaj odwołanie do pliku System.Threading.Tasks.Dataflow.dll.  
  
2. Upewnij się, że Form1.cs (Form1.vb `using` dla`Imports` języka Visual Basic) zawiera następujące instrukcje (w języku Visual Basic).  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3. Dodaj <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> element członkowski danych do `Form1` klasy.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4. W `Form1` konstruktorze po `InitializeComponent`wywołaniu <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> , utwórz obiekt, <xref:System.Windows.Forms.CheckBox> który przełącza stan obiektów.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5. W `Form1` konstruktorze <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> utwórz <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiekt i <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> cztery <xref:System.Windows.Forms.CheckBox> obiekty, po jednym obiekcie dla każdego obiektu. Dla <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> każdego obiektu <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> należy określić <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> obiekt, który <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> ma właściwość ustawioną na właściwość dla czytników i <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> właściwość dla modułu zapisującego.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6. W `Form1` konstruktorze <xref:System.Windows.Forms.Timer> uruchom obiekt.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7. W projektancie formularza dla formularza głównego utwórz program obsługi zdarzeń dla <xref:System.Windows.Forms.Timer.Tick> czasoatora.  
  
8. Zaimplementuj <xref:System.Windows.Forms.Timer.Tick> zdarzenie dla czasowcy.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 Ponieważ `toggleCheckBox` blok przepływu danych działa na interfejs ie użytkownika, ważne jest, aby ta akcja wystąpiła w wątku interfejsu użytkownika. Aby to osiągnąć, podczas budowy <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> ten obiekt <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> zawiera <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>obiekt, który ma właściwość ustawioną na . Metoda <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> tworzy <xref:System.Threading.Tasks.TaskScheduler> obiekt, który wykonuje pracę na bieżącym kontekście synchronizacji. Ponieważ `Form1` konstruktor jest wywoływana z wątku `toggleCheckBox` interfejsu użytkownika, akcja dla bloku przepływu danych jest również uruchamiana w wątku interfejsu użytkownika.  
  
 W tym przykładzie <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> użyto również klasy, aby włączyć niektóre bloki przepływu danych do działania jednocześnie i innego bloku <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> przepływu danych do działania na wyłączność w odniesieniu do wszystkich innych bloków przepływu danych, które działają na tym samym obiekcie. Ta technika jest przydatna, gdy wiele bloków przepływu danych współużytkuje zasób, a niektóre wymagają wyłącznego dostępu do tego zasobu, ponieważ eliminuje wymóg ręcznej synchronizacji dostępu do tego zasobu. Eliminacja synchronizacji ręcznej może sprawić, że kod będzie bardziej wydajny.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono kompletny kod Form1.cs (Form1.vb dla języka Visual Basic).  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a>Zobacz też

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
