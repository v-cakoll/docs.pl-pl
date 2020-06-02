---
title: 'Instrukcje: Określanie harmonogramu zadań w bloku przepływu danych'
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
ms.openlocfilehash: 76c9e75f787c28657af143b46bb22d08039e2dc4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288137"
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a>Instrukcje: Określanie harmonogramu zadań w bloku przepływu danych
W tym dokumencie przedstawiono sposób kojarzenia określonego harmonogramu zadań w przypadku korzystania z przepływu danych w aplikacji. W przykładzie używa <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> klasy w aplikacji Windows Forms, aby pokazać, kiedy zadania czytnika są aktywne, a zadanie składnika zapisywania jest aktywne. Używa również metody, <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> Aby umożliwić uruchamianie bloku przepływu danych w wątku interfejsu użytkownika.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a>Aby utworzyć aplikację Windows Forms  
  
1. Utwórz projekt aplikacji Visual C# lub Visual Basic **Windows Forms** . W poniższych krokach projekt ma nazwę `WriterReadersWinForms` .  
  
2. W projektancie formularzy dla formularza głównego Form1.cs (Form1. vb dla Visual Basic) Dodaj cztery <xref:System.Windows.Forms.CheckBox> kontrolki. Ustaw <xref:System.Windows.Forms.Control.Text%2A> Właściwość na **Reader 1** dla `checkBox1` , **Reader 2** dla `checkBox2` , **Reader 3** dla `checkBox3` i **składnika zapisywania** dla `checkBox4` . Ustaw <xref:System.Windows.Forms.Control.Enabled%2A> Właściwość dla każdej kontrolki na `False` .  
  
3. Dodaj <xref:System.Windows.Forms.Timer> kontrolkę do formularza. Ustaw <xref:System.Windows.Forms.Timer.Interval%2A> Właściwość na wartość `2500` .  
  
## <a name="adding-dataflow-functionality"></a>Dodawanie funkcji przepływu danych  
 W tej sekcji opisano sposób tworzenia bloków przepływu danych, które uczestniczą w aplikacji oraz jak skojarzyć każdą z nich z harmonogramem zadań.  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a>Aby dodać funkcję przepływu danych do aplikacji  
  
1. W projekcie Dodaj odwołanie do elementu System. Threading. Tasks. przepływu danych. dll.  
  
2. Upewnij się, że Form1.cs (Form1. vb dla Visual Basic) zawiera następujące `using` instrukcje ( `Imports` w Visual Basic).  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3. Dodaj <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> element członkowski danych do `Form1` klasy.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4. W `Form1` konstruktorze po wywołaniu do `InitializeComponent` , Utwórz <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiekt, który przełącza stan <xref:System.Windows.Forms.CheckBox> obiektów.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5. W `Form1` konstruktorze Utwórz <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> obiekt i cztery <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiekty, jeden <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiekt dla każdego <xref:System.Windows.Forms.CheckBox> obiektu. Dla każdego <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> obiektu należy określić <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> obiekt, który ma <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> Właściwość ustawioną na <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> Właściwość dla czytelników, i <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> Właściwość dla składnika zapisywania.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6. W `Form1` konstruktorze Uruchom <xref:System.Windows.Forms.Timer> obiekt.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7. W projektancie formularzy dla formularza głównego Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.Timer.Tick> zdarzenia czasomierza.  
  
8. Zaimplementuj <xref:System.Windows.Forms.Timer.Tick> zdarzenie dla czasomierza.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 Ponieważ `toggleCheckBox` blok przepływu danych działa w interfejsie użytkownika, należy pamiętać, że ta akcja jest wykonywana w wątku interfejsu użytkownika. Aby to osiągnąć, podczas konstruowania ten obiekt udostępnia <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> obiekt, który ma <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> Właściwość ustawioną na <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> . <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A>Metoda tworzy <xref:System.Threading.Tasks.TaskScheduler> obiekt, który wykonuje prace w bieżącym kontekście synchronizacji. Ponieważ `Form1` Konstruktor jest wywoływany z wątku interfejsu użytkownika, akcja dla `toggleCheckBox` bloku przepływu danych jest również uruchamiana w wątku interfejsu użytkownika.  
  
 Ten przykład używa również <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> klasy do włączania pewnych bloków przepływu danych do działania współbieżnie i innego bloku przepływu danych do działania wyłącznie w odniesieniu do wszystkich innych bloków przepływu danych, które działają w tym samym <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> obiekcie. Ta technika jest przydatna, gdy wiele bloków przepływu danych współużytkuje zasób, a niektóre wymagają wyłącznego dostępu do tego zasobu, ponieważ eliminuje konieczność ręcznej synchronizacji dostępu do tego zasobu. Eliminacja synchronizacji ręcznej może zwiększyć wydajność kodu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje kompletny kod dla Form1.cs (Form1. vb dla Visual Basic).  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ danych](dataflow-task-parallel-library.md)
