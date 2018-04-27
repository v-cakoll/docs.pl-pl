---
title: 'Porady: Określanie harmonogramu zadań w bloku przepływu danych'
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
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
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 15b1168c34a22394424f250e8ab1887ec8ee1a5e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a>Porady: Określanie harmonogramu zadań w bloku przepływu danych
Ten dokument przedstawia sposób skojarzenia harmonogramu zadań określone przy użyciu przepływu danych w aplikacji. W przykładzie użyto <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> klasy w aplikacji formularzy systemu Windows, gdy czytnik zadania są aktywne i podczas zadania zapisywania jest aktywny. Ponadto użyto <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> metodę umożliwiającą włączenie bloku przepływu danych do uruchamiania w wątku interfejsu użytkownika.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a>Aby utworzyć systemu Windows w aplikacjach formularzy  
  
1.  Tworzenie Visual C# lub Visual Basic **aplikacji Windows Forms** projektu. W poniższych krokach projektu o nazwie `WriterReadersWinForms`.  
  
2.  Projektant formularzy dla tego formularza, pliku Form1.cs (Form1.vb w języku Visual Basic), dodaj cztery <xref:System.Windows.Forms.CheckBox> kontrolki. Ustaw <xref:System.Windows.Forms.Control.Text%2A> właściwości **1 czytnika** dla `checkBox1`, **2 czytnika** dla `checkBox2`, **3 czytnika** dla `checkBox3`, i  **Moduł zapisujący** dla `checkBox4`. Ustaw <xref:System.Windows.Forms.Control.Enabled%2A> właściwości dla każdego formantu do `False`.  
  
3.  Dodaj <xref:System.Windows.Forms.Timer> sterowania do formularza. Ustaw <xref:System.Windows.Forms.Timer.Interval%2A> właściwości `2500`.  
  
## <a name="adding-dataflow-functionality"></a>Dodawanie funkcjonalności przepływu danych  
 W tej sekcji opisano sposób tworzenia bloków przepływu danych, które uczestniczą w aplikacji oraz sposobu kojarzenia każdej z nich z harmonogramu zadań.  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a>Aby dodać funkcję przepływu danych do aplikacji  
  
1.  W projekcie Dodaj odwołanie do System.Threading.Tasks.Dataflow.dll.  
  
2.  Upewnij się, że pliku Form1.cs (Form1.vb w języku Visual Basic) zawiera następujące `using` instrukcje (`Imports` w języku Visual Basic).  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3.  Dodaj <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> element członkowski danych do `Form1` klasy.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4.  W `Form1` konstruktora, po wywołaniu `InitializeComponent`, Utwórz <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiekt, który włącza stan <xref:System.Windows.Forms.CheckBox> obiektów.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5.  W `Form1` konstruktora, Utwórz <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> obiekt i czterema <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektów, z których jeden <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiekt dla każdego <xref:System.Windows.Forms.CheckBox> obiektu. Dla każdego <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektów, określ <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> obiektu, który ma <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> ustawioną właściwość <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> właściwości czytniki i <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> właściwości dla edytora.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6.  W `Form1` konstruktora, start <xref:System.Windows.Forms.Timer> obiektu.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7.  W projektancie formularzy dla tego formularza należy utworzyć programu obsługi zdarzeń dla <xref:System.Windows.Forms.Timer.Tick> zdarzenie czasomierza.  
  
8.  Implementowanie <xref:System.Windows.Forms.Timer.Tick> zdarzenie czasomierza.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 Ponieważ `toggleCheckBox` działania bloku przepływu danych w interfejsie użytkownika, ważne jest, że ta akcja wystąpić w wątku interfejsu użytkownika. Aby to osiągnąć, podczas konstruowania ten obiekt zawiera <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> obiektu, który ma <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> ustawioną właściwość <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> Metoda tworzy <xref:System.Threading.Tasks.TaskScheduler> obiekt, który przeprowadza pracę na bieżący kontekst synchronizacji. Ponieważ `Form1` Konstruktor jest wywoływana z wątku interfejsu użytkownika, Akcja dla `toggleCheckBox` bloku przepływu danych jest również uruchamiane w wątku interfejsu użytkownika.  
  
 W tym przykładzie również używane <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> klasę, aby włączyć niektóre bloki przepływu danych, które będą działać jednocześnie, a inny blok przepływu danych do działania wyłącznego względem wszystkich innych bloków przepływu danych, które są uruchamiane na tym samym <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> obiektu. Ta technika jest przydatna w przypadku wiele bloków przepływu danych udostępniania zasobu i niektóre wymaga wyłącznego dostępu do tego zasobu, ponieważ eliminuje konieczność ręcznego synchronizowania dostęp do tego zasobu. Eliminacja ręczną synchronizację wprowadzić kod większą wydajność.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia kompletny kod dla pliku Form1.cs (Form1.vb w języku Visual Basic).  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
