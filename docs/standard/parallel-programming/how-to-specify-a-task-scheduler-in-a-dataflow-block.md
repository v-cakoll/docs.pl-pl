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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9338d06cf7774e1451a0c470c7e078cdb17510ae
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43879080"
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a>Porady: Określanie harmonogramu zadań w bloku przepływu danych
W tym dokumencie pokazano, jak skojarzyć harmonogram zadań szczególnych, korzystając z przepływu danych w aplikacji. W przykładzie użyto <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> klasy w aplikacji Windows Forms do wyświetlenia, gdy czytnik zadania są aktywne i podczas zadania zapisywania jest aktywny. Korzysta również <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> metodę umożliwiającą włączenie bloku przepływu danych do uruchamiania w wątku interfejsu użytkownika.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a>Aby utworzyć Windows Forms aplikacji  
  
1.  Tworzenie języka Visual C# lub Visual Basic **aplikacja interfejsu Windows Forms** projektu. W poniższych krokach projekt nazwano `WriterReadersWinForms`.  
  
2.  W Projektancie formularza dla tego formularza Form1.cs (Form1.vb dla języka Visual Basic), dodaj cztery <xref:System.Windows.Forms.CheckBox> kontrolki. Ustaw <xref:System.Windows.Forms.Control.Text%2A> właściwości **1 czytnika** dla `checkBox1`, **Reader 2** dla `checkBox2`, **3 czytnika** dla `checkBox3`, i  **Moduł zapisujący** dla `checkBox4`. Ustaw <xref:System.Windows.Forms.Control.Enabled%2A> właściwości dla każdego formantu do `False`.  
  
3.  Dodaj <xref:System.Windows.Forms.Timer> formantu do formularza. Ustaw <xref:System.Windows.Forms.Timer.Interval%2A> właściwość `2500`.  
  
## <a name="adding-dataflow-functionality"></a>Dodawanie funkcjonalności przepływu danych  
 W tej sekcji opisano sposób tworzenia bloków przepływu danych, które uczestniczą w aplikacji oraz jak skojarzyć każdy z nich za pomocą harmonogramu zadań.  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a>Aby dodać funkcje przepływu danych do aplikacji  
  
1.  W projekcie należy dodać odwołanie do System.Threading.Tasks.Dataflow.dll.  
  
2.  Upewnij się, że Form1.cs (Form1.vb dla języka Visual Basic) zawiera następujące `using` instrukcji (`Imports` w języku Visual Basic).  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3.  Dodaj <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> element członkowski danych do `Form1` klasy.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4.  W `Form1` konstruktora, po wywołaniu `InitializeComponent`, Utwórz <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiekt, który włącza/wyłącza stan <xref:System.Windows.Forms.CheckBox> obiektów.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5.  W `Form1` konstruktora, Utwórz <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> obiektu i cztery <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektów, po jednym <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiekt dla każdego <xref:System.Windows.Forms.CheckBox> obiektu. Dla każdego <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektów, określ <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> obiekt, który ma <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> właściwością <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> właściwości dla czytników zawartości i <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> właściwości dla edytora.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6.  W `Form1` konstruktora, start <xref:System.Windows.Forms.Timer> obiektu.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7.  W Projektancie formularza dla tego formularza, należy utworzyć program obsługi zdarzeń dla <xref:System.Windows.Forms.Timer.Tick> zdarzenie czasomierza.  
  
8.  Implementowanie <xref:System.Windows.Forms.Timer.Tick> zdarzenie czasomierza.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 Ponieważ `toggleCheckBox` działa bloku przepływu danych w interfejsie użytkownika, ważne jest, że ta akcja wystąpić w wątku interfejsu użytkownika. Aby to osiągnąć, podczas konstruowania ten obiekt zawiera <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> obiekt, który ma <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> właściwością <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> Metoda tworzy <xref:System.Threading.Tasks.TaskScheduler> obiektu, który wykonuje pracę w bieżącym kontekście synchronizacji. Ponieważ `Form1` Konstruktor jest wywoływana z wątku interfejsu użytkownika w akcji dla `toggleCheckBox` bloku przepływu danych jest również uruchamiane w wątku interfejsu użytkownika.  
  
 W tym przykładzie również użyto <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> klasy w celu włączenia pewnych bloków przepływu danych, która będzie działać jednocześnie, a inny blok przepływu danych do działania na wyłączność w odniesieniu do wszystkich innych bloków przepływu danych, które są uruchamiane na tym samym <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> obiektu. Ta technika jest przydatna, gdy wiele bloków przepływu danych dzielą jakiś zasób, a niektóre wymagają wyłącznego dostępu do tego zasobu, ponieważ eliminuje wymóg, aby ręcznie zsynchronizować dostęp do tego zasobu. Eliminacja ręcznej synchronizacji może uczynić kod bardziej wydajne.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje kompletny kod dla Form1.cs (Form1.vb dla języka Visual Basic).  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
