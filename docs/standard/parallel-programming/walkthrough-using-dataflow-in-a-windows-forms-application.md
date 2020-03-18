---
title: 'Wskazówki: Korzystanie z przepływu danych w Aplikacji formularzy systemu Windows'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- TPL dataflow library, in Windows Forms
- Task Parallel Library, dataflows
- Windows Forms, and TPL
ms.assetid: 9c65cdf7-660c-409f-89ea-59d7ec8e127c
ms.openlocfilehash: 794253514edf63f02276e1ece21c60a85c534390
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159770"
---
# <a name="walkthrough-using-dataflow-in-a-windows-forms-application"></a>Wskazówki: Korzystanie z przepływu danych w Aplikacji formularzy systemu Windows
W tym dokumencie pokazano, jak utworzyć sieć bloków przepływu danych, które wykonują przetwarzanie obrazu w aplikacji Formularzy systemu Windows.  
  
 W tym przykładzie wczytuje pliki obrazów z określonego folderu, tworzy obraz złożony i wyświetla wynik. W przykładzie użyto modelu przepływu danych do kierowania obrazów przez sieć. W modelu przepływu danych niezależne składniki programu komunikują się ze sobą, wysyłając wiadomości. Gdy składnik odbiera komunikat, wykonuje niektóre działania, a następnie przekazuje wynik do innego składnika. Porównaj to z modelem przepływu sterowania, w którym aplikacja używa struktur kontroli, na przykład instrukcji warunkowych, pętli i tak dalej, aby kontrolować kolejność operacji w programie.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Przeczytaj [przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) przed rozpoczęciem tego instruktażenia.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="sections"></a>Sekcje  
 Ten instruktaż zawiera następujące sekcje:  
  
- [Tworzenie aplikacji formularzy systemu Windows](#winforms)  
  
- [Tworzenie sieci przepływu danych](#network)  
  
- [Podłączanie sieci przepływu danych do interfejsu użytkownika](#ui)  
  
- [Kompletny przykład](#complete)  
  
<a name="winforms"></a>
## <a name="creating-the-windows-forms-application"></a>Tworzenie aplikacji formularzy systemu Windows  
 W tej sekcji opisano sposób tworzenia podstawowej aplikacji formularzy systemu Windows i dodawania kontrolek do formularza głównego.  
  
### <a name="to-create-the-windows-forms-application"></a>Aby utworzyć aplikację formularzy systemu Windows  
  
1. W programie Visual Studio utwórz projekt aplikacji Visual C# lub Visual Basic **Windows Forms Application.** W tym dokumencie projekt `CompositeImages`nosi nazwę .  
  
2. W projektancie formularza dla formularza głównego Form1.cs (Form1.vb <xref:System.Windows.Forms.ToolStrip> dla języka Visual Basic) dodaj formant.  
  
3. Dodaj <xref:System.Windows.Forms.ToolStripButton> formant do <xref:System.Windows.Forms.ToolStrip> formantu. Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> właściwość <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> i <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwość wybierz **folder**.  
  
4. Dodaj drugi <xref:System.Windows.Forms.ToolStripButton> formant <xref:System.Windows.Forms.ToolStrip> do formantu. Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> właściwość <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>na <xref:System.Windows.Forms.ToolStripItem.Text%2A> , właściwość **Anuluj**, a <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> właściwość na `False`.  
  
5. Dodaj <xref:System.Windows.Forms.PictureBox> obiekt do formularza głównego. Ustaw <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>na .  
  
<a name="network"></a>
## <a name="creating-the-dataflow-network"></a>Tworzenie sieci przepływu danych  
 W tej sekcji opisano sposób tworzenia sieci przepływu danych, która wykonuje przetwarzanie obrazu.  
  
### <a name="to-create-the-dataflow-network"></a>Aby utworzyć sieć przepływu danych  
  
1. Dodaj odwołanie do pliku System.Threading.Tasks.Dataflow.dll do projektu.  
  
2. Upewnij się, że Form1.cs (Form1.vb `using` dla`Using` języka Visual Basic) zawiera następujące instrukcje (w języku Visual Basic):  
  
     [!code-csharp[TPLDataflow_CompositeImages#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#1)]  
  
3. Dodaj następujące elementy członkowskie `Form1` danych do klasy:  
  
     [!code-csharp[TPLDataflow_CompositeImages#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#2)]  
  
4. Dodaj następującą `CreateImageProcessingNetwork`metodę, `Form1` , do klasy. Ta metoda tworzy sieć przetwarzania obrazu.  
  
     [!code-csharp[TPLDataflow_CompositeImages#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#3)]  
  
5. Zaimplementuj `LoadBitmaps` metodę.  
  
     [!code-csharp[TPLDataflow_CompositeImages#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#4)]  
  
6. Zaimplementuj `CreateCompositeBitmap` metodę.  
  
     [!code-csharp[TPLDataflow_CompositeImages#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#5)]  
  
    > [!NOTE]
    > Wersja C# `CreateCompositeBitmap` metody używa wskaźników, aby umożliwić <xref:System.Drawing.Bitmap?displayProperty=nameWithType> wydajne przetwarzanie obiektów. W związku z tym należy włączyć **zezwalaj na niebezpieczny kod** opcji w projekcie, aby użyć [niebezpiecznego](../../csharp/language-reference/keywords/unsafe.md) słowa kluczowego. Aby uzyskać więcej informacji na temat włączania niebezpiecznego kodu w projekcie visual c#, zobacz [Tworzenie strony, projektanta projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
 W poniższej tabeli opisano elementy członkowskie sieci.  
  
|Członek|Typ|Opis|  
|------------|----------|-----------------|  
|`loadBitmaps`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Przyjmuje ścieżkę folderu jako dane <xref:System.Drawing.Bitmap> wejściowe i tworzy kolekcję obiektów jako dane wyjściowe.|  
|`createCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Pobiera kolekcję <xref:System.Drawing.Bitmap> obiektów jako dane wejściowe i tworzy złożoną mapę bitową jako dane wyjściowe.|  
|`displayCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Wyświetla złożoną mapę bitową w formularzu.|  
|`operationCancelled`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Wyświetla obraz wskazujący, że operacja została anulowana i umożliwia użytkownikowi wybranie innego folderu.|  
  
 Aby połączyć bloki przepływu danych w celu <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> utworzenia sieci, w tym przykładzie używa metody. Metoda <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> zawiera przeciążoną wersję, <xref:System.Predicate%601> która przyjmuje obiekt, który określa, czy blok docelowy akceptuje lub odrzuca wiadomość. Ten mechanizm filtrowania umożliwia blokom komunikatów odbieranie tylko niektórych wartości. W tym przykładzie sieć może rozgałęziać się na jeden z dwóch sposobów. Główna gałąź ładuje obrazy z dysku, tworzy obraz złożony i wyświetla ten obraz w formularzu. Alternatywna gałąź anuluje bieżącą operację. Obiekty <xref:System.Predicate%601> umożliwiają bloków przepływu danych wzdłuż gałęzi głównej, aby przełączyć się do alternatywnej gałęzi, odrzucając niektóre wiadomości. Na przykład jeśli użytkownik anuluje operację, `createCompositeBitmap` blok `null` `Nothing` przepływu danych generuje (w języku Visual Basic) jako dane wyjściowe. Blok `displayCompositeBitmap` przepływu danych `null` odrzuca wartości wejściowe i w związku `operationCancelled`z tym wiadomość jest oferowana do . Blok `operationCancelled` przepływu danych akceptuje wszystkie wiadomości i w związku z tym wyświetla obraz, aby wskazać, że operacja została anulowana.  
  
 Na poniższej ilustracji przedstawiono sieć przetwarzania obrazu:  
  
 ![Ilustracja przedstawiająca sieć przetwarzania obrazu.](./media/walkthrough-using-dataflow-in-a-windows-forms-application/dataflow-winforms-image-processing.png)  
  
 Ponieważ `displayCompositeBitmap` bloki przepływu `operationCancelled` danych działają na interfejsie użytkownika, ważne jest, aby te akcje wystąpiły w wątku interfejsu użytkownika. Aby to osiągnąć, podczas budowy, <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> te obiekty <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> każdy podać <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>obiekt, który ma właściwość ustawioną . Metoda <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> tworzy <xref:System.Threading.Tasks.TaskScheduler> obiekt, który wykonuje pracę na bieżącym kontekście synchronizacji. Ponieważ `CreateImageProcessingNetwork` metoda jest wywoływana z obsługi wybierz **folder** przycisk, który jest uruchamiany `displayCompositeBitmap` w `operationCancelled` wątku interfejsu użytkownika, akcje dla bloków i przepływu danych również uruchomić w wątku interfejsu użytkownika.  
  
 W tym przykładzie używa tokenu <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> anulowania udostępnionego zamiast ustawiania właściwości, <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> ponieważ właściwość trwale anuluje wykonanie bloku przepływu danych. Token anulowania umożliwia w tym przykładzie ponowne użycie tej samej sieci przepływu danych wiele razy, nawet wtedy, gdy użytkownik anuluje jedną lub więcej operacji. Na przykład, <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> który używa do trwałego anulowania wykonywania bloku przepływu danych, zobacz [Jak: Anulowanie bloku przepływu danych](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md).  
  
<a name="ui"></a>
## <a name="connecting-the-dataflow-network-to-the-user-interface"></a>Podłączanie sieci przepływu danych do interfejsu użytkownika  
 W tej sekcji opisano sposób łączenia sieci przepływu danych z interfejsem użytkownika. Tworzenie obrazu złożonego i anulowanie operacji są inicjowane z **wybierz folder** i **Anuluj** przyciski. Gdy użytkownik wybierze jeden z tych przycisków, odpowiednia akcja jest inicjowana w sposób asynchroniczny.  
  
### <a name="to-connect-the-dataflow-network-to-the-user-interface"></a>Aby połączyć sieć przepływu danych z interfejsem użytkownika  
  
1. W projektancie formularza dla formularza głównego utwórz program obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia dla przycisku Wybierz **folder.**  
  
2. Zaimplementuj <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenie dla przycisku **Wybierz folder.**  
  
     [!code-csharp[TPLDataflow_CompositeImages#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#6)]  
  
3. W projektancie formularza dla formularza głównego utwórz program obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia dla przycisku **Anuluj.**  
  
4. Zaimplementuj <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenie dla przycisku **Anuluj.**  
  
     [!code-csharp[TPLDataflow_CompositeImages#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#7)]  
  
<a name="complete"></a>
## <a name="the-complete-example"></a>Kompletny przykład  
 W poniższym przykładzie przedstawiono pełny kod dla tego instruktaże.  
  
 [!code-csharp[TPLDataflow_CompositeImages#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#100)]  
  
 Na poniższej ilustracji przedstawiono typowe dane wyjściowe dla wspólnego folderu \Sample Pictures\.  
  
 ![Aplikacja formularzy systemu Windows](../../../docs/standard/parallel-programming/media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")  

## <a name="see-also"></a>Zobacz też

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
