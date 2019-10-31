---
title: 'Wskazówki: Korzystanie z przepływu danych w Aplikacji formularzy systemu Windows'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- TPL dataflow library, in Windows Forms
- Task Parallel Library, dataflows
- Windows Forms, and TPL
ms.assetid: 9c65cdf7-660c-409f-89ea-59d7ec8e127c
ms.openlocfilehash: b6f4b933f76834f48d522d9c97fb0c9b5c24e13d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139918"
---
# <a name="walkthrough-using-dataflow-in-a-windows-forms-application"></a>Wskazówki: Korzystanie z przepływu danych w Aplikacji formularzy systemu Windows
W tym dokumencie przedstawiono sposób tworzenia sieci bloków przepływu danych, które wykonują przetwarzanie obrazów w aplikacji Windows Forms.  
  
 Ten przykład służy do ładowania plików obrazów z określonego folderu, tworzenia obrazu złożonego i wyświetlania wyniku. W przykładzie zastosowano model przepływu danych do rozsyłania obrazów za pośrednictwem sieci. W modelu przepływu danych niezależne składniki programu komunikują się ze sobą przez wysyłanie komunikatów. Gdy składnik odbiera komunikat, wykonuje pewne działania, a następnie przekazuje wynik do innego składnika. Porównaj ten element z modelem przepływu sterowania, w którym aplikacja używa struktur kontroli, na przykład instrukcji warunkowych, pętli i tak dalej, aby kontrolować kolejność operacji w programie.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Przeczytaj [przepływu danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) przed rozpoczęciem tego instruktażu.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="sections"></a>Sekcje  
 Ten Instruktaż zawiera następujące sekcje:  
  
- [Tworzenie aplikacji Windows Forms](#winforms)  
  
- [Tworzenie sieci przepływu danych](#network)  
  
- [Łączenie sieci przepływu danych z interfejsem użytkownika](#ui)  
  
- [Kompletny przykład](#complete)  
  
<a name="winforms"></a>   
## <a name="creating-the-windows-forms-application"></a>Tworzenie aplikacji Windows Forms  
 W tej sekcji opisano, jak utworzyć podstawową aplikację Windows Forms i dodać kontrolki do formularza głównego.  
  
### <a name="to-create-the-windows-forms-application"></a>Aby utworzyć aplikację Windows Forms  
  
1. W programie Visual Studio Utwórz projekt C# **aplikacji Windows Forms** wizualizacji lub Visual Basic. W tym dokumencie projekt ma nazwę `CompositeImages`.  
  
2. W projektancie formularzy dla formularza głównego Form1.cs (Form1. vb dla Visual Basic) Dodaj kontrolkę <xref:System.Windows.Forms.ToolStrip>.  
  
3. Dodaj kontrolkę <xref:System.Windows.Forms.ToolStripButton> do kontrolki <xref:System.Windows.Forms.ToolStrip>. Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> na <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> i Właściwość <xref:System.Windows.Forms.ToolStripItem.Text%2A>, aby **wybrać folder**.  
  
4. Dodaj drugą kontrolkę <xref:System.Windows.Forms.ToolStripButton> do kontrolki <xref:System.Windows.Forms.ToolStrip>. Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> na <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, właściwość <xref:System.Windows.Forms.ToolStripItem.Text%2A> na wartość **Cancel**i Właściwość <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> na `False`.  
  
5. Dodaj obiekt <xref:System.Windows.Forms.PictureBox> do formularza głównego. Ustaw właściwość <xref:System.Windows.Forms.Control.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Fill>.  
  
<a name="network"></a>   
## <a name="creating-the-dataflow-network"></a>Tworzenie sieci przepływu danych  
 W tej sekcji opisano sposób tworzenia sieci przepływu danych, która wykonuje przetwarzanie obrazu.  
  
### <a name="to-create-the-dataflow-network"></a>Aby utworzyć sieć przepływu danych  
  
1. Dodaj odwołanie do elementu System. Threading. Tasks. przepływu danych. dll do projektu.  
  
2. Upewnij się, że Form1.cs (Form1. vb dla Visual Basic) zawiera następujące instrukcje `using` (`Using` w Visual Basic):  
  
     [!code-csharp[TPLDataflow_CompositeImages#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#1)]  
  
3. Dodaj następujące składowe danych do klasy `Form1`:  
  
     [!code-csharp[TPLDataflow_CompositeImages#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#2)]  
  
4. Dodaj następującą metodę, `CreateImageProcessingNetwork`, do klasy `Form1`. Ta metoda służy do tworzenia sieci przetwarzania obrazów.  
  
     [!code-csharp[TPLDataflow_CompositeImages#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#3)]  
  
5. Zaimplementuj metodę `LoadBitmaps`.  
  
     [!code-csharp[TPLDataflow_CompositeImages#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#4)]  
  
6. Zaimplementuj metodę `CreateCompositeBitmap`.  
  
     [!code-csharp[TPLDataflow_CompositeImages#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#5)]  
  
    > [!NOTE]
    > C# Wersja metody `CreateCompositeBitmap` używa wskaźników w celu zapewnienia wydajnego przetwarzania obiektów <xref:System.Drawing.Bitmap?displayProperty=nameWithType>. W związku z tym należy włączyć opcję **Zezwalaj na niebezpieczny kod** w projekcie, aby można było [użyć słowa kluczowego unsafe.](../../csharp/language-reference/keywords/unsafe.md) Aby uzyskać więcej informacji na temat włączania niebezpiecznego kodu C# w projekcie wizualizacji, zobacz [stronę Kompilacja,C#Projektant projektu ()](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
 W poniższej tabeli opisano elementy członkowskie sieci.  
  
|Element członkowski|Typ|Opis|  
|------------|----------|-----------------|  
|`loadBitmaps`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Pobiera ścieżkę folderu jako dane wejściowe i tworzy kolekcję <xref:System.Drawing.Bitmap> obiektów jako dane wyjściowe.|  
|`createCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Pobiera kolekcję obiektów <xref:System.Drawing.Bitmap> jako dane wejściowe i tworzy kompozytową mapę bitową jako dane wyjściowe.|  
|`displayCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Wyświetla kompozytową mapę bitową w formularzu.|  
|`operationCancelled`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Wyświetla obraz wskazujący, że operacja została anulowana, i umożliwia użytkownikowi wybranie innego folderu.|  
  
 Aby połączyć bloki przepływu danych w celu utworzenia sieci, w tym przykładzie zostanie użyta metoda <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A>. Metoda <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> zawiera przeciążoną wersję, która przyjmuje obiekt <xref:System.Predicate%601>, który określa, czy blok docelowy akceptuje lub odrzuca komunikat. Ten mechanizm filtrowania umożliwia blokom komunikatów odbieranie tylko określonych wartości. W tym przykładzie sieć może rozgałęziać się na jeden z dwóch sposobów. Gałąź główna ładuje obrazy z dysku, tworzy obraz złożony i wyświetla ten obraz w formularzu. Gałąź alternatywna anuluje bieżącą operację. Obiekty <xref:System.Predicate%601> umożliwiają blokom przepływu danych wzdłuż gałęzi głównej, aby przełączyć się na gałąź alternatywną poprzez odrzucenie niektórych komunikatów. Na przykład, jeśli użytkownik anuluje operację, blok przepływu danych `createCompositeBitmap` produkuje `null` (`Nothing` w Visual Basic) jako dane wyjściowe. Blok przepływu danych `displayCompositeBitmap` odrzuca wartości wejściowe `null` i w związku z tym komunikat jest oferowany do `operationCancelled`. Blok przepływu danych `operationCancelled` akceptuje wszystkie komunikaty i w związku z tym wyświetla obraz, aby wskazać, że operacja została anulowana.  
  
 Na poniższej ilustracji przedstawiono sieć przetwarzania obrazów:  
  
 ![Ilustracja przedstawiająca sieć przetwarzania obrazów.](./media/walkthrough-using-dataflow-in-a-windows-forms-application/dataflow-winforms-image-processing.png)  
  
 Ponieważ `displayCompositeBitmap` i `operationCancelled` bloków przepływu danych działają w interfejsie użytkownika, ważne jest, aby te akcje miały miejsce w wątku interfejsu użytkownika. W tym celu w czasie konstruowania obiekty te udostępniają <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> obiekt, który ma właściwość <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> ustawioną na <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. Metoda <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> tworzy obiekt <xref:System.Threading.Tasks.TaskScheduler>, który wykonuje prace w bieżącym kontekście synchronizacji. Ponieważ metoda `CreateImageProcessingNetwork` jest wywoływana z procedury obsługi przycisku **Wybierz folder** , który działa w wątku interfejsu użytkownika, akcje dla bloków `displayCompositeBitmap` i `operationCancelled` przepływu danych również są uruchamiane w wątku interfejsu użytkownika.  
  
 W tym przykładzie używa udostępnionego tokenu anulowania zamiast ustawiania właściwości <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A>, ponieważ właściwość <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> trwale anuluje wykonywanie bloku przepływu danych. Token anulowania umożliwia korzystanie z tej samej sieci przepływu danych wiele razy, nawet jeśli użytkownik anuluje jedną lub więcej operacji. Przykład, który używa <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> do trwałego anulowania wykonywania bloku przepływu danych, można znaleźć w temacie [How to: Cancel a przepływu danych Block](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md).  
  
<a name="ui"></a>   
## <a name="connecting-the-dataflow-network-to-the-user-interface"></a>Łączenie sieci przepływu danych z interfejsem użytkownika  
 W tej sekcji opisano sposób łączenia sieci przepływu danych z interfejsem użytkownika. Tworzenie obrazu złożonego i anulowanie operacji są inicjowane z przycisków **Wybierz folder** i **Anuluj** . Gdy użytkownik wybierze jeden z tych przycisków, odpowiednia akcja zostanie zainicjowana w sposób asynchroniczny.  
  
### <a name="to-connect-the-dataflow-network-to-the-user-interface"></a>Aby połączyć sieć przepływu danych z interfejsem użytkownika  
  
1. W projektancie formularzy dla formularza głównego Utwórz procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.ToolStripItem.Click> dla przycisku **Wybierz folder** .  
  
2. Zaimplementuj zdarzenie <xref:System.Windows.Forms.ToolStripItem.Click> dla przycisku **Wybierz folder** .  
  
     [!code-csharp[TPLDataflow_CompositeImages#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#6)]  
  
3. W projektancie formularzy dla formularza głównego Utwórz procedurę obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.ToolStripItem.Click> dla przycisku **Anuluj** .  
  
4. Zaimplementuj zdarzenie <xref:System.Windows.Forms.ToolStripItem.Click> dla przycisku **Anuluj** .  
  
     [!code-csharp[TPLDataflow_CompositeImages#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#7)]  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a>Kompletny przykład  
 Poniższy przykład pokazuje kompletny kod dla tego przewodnika.  
  
 [!code-csharp[TPLDataflow_CompositeImages#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#100)]  
  
 Na poniższej ilustracji przedstawiono typowe dane wyjściowe folderu Common \Sample obrazy \ folder.  
  
 ![Aplikacja Windows Forms](../../../docs/standard/parallel-programming/media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")  

## <a name="see-also"></a>Zobacz także

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
