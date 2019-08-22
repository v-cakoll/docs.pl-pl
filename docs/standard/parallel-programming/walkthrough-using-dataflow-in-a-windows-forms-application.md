---
title: 'Przewodnik: Korzystanie z przepływu danych w aplikacji Windows Forms'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- TPL dataflow library, in Windows Forms
- Task Parallel Library, dataflows
- Windows Forms, and TPL
ms.assetid: 9c65cdf7-660c-409f-89ea-59d7ec8e127c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4dc433b83fd086a1e3e165a85b6bfe64b781f45b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666339"
---
# <a name="walkthrough-using-dataflow-in-a-windows-forms-application"></a>Przewodnik: Korzystanie z przepływu danych w aplikacji Windows Forms
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
  
2. W projektancie formularzy dla formularza głównego Form1.cs (Form1. vb dla Visual Basic) Dodaj <xref:System.Windows.Forms.ToolStrip> kontrolkę.  
  
3. Dodaj kontrolkę do <xref:System.Windows.Forms.ToolStrip>kontrolki. <xref:System.Windows.Forms.ToolStripButton> Ustaw właściwość na <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> i<xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwość, aby **wybrać folder.** <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>  
  
4. Dodaj drugą <xref:System.Windows.Forms.ToolStripButton> kontrolkę <xref:System.Windows.Forms.ToolStrip> do kontrolki. <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> Ustaw właściwość na `False`, Właściwośćdoanulowaniaiwłaściwośćna<xref:System.Windows.Forms.ToolStripItem.Text%2A>. <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>  
  
5. <xref:System.Windows.Forms.PictureBox> Dodaj obiekt do formularza głównego. Ustaw <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>.  
  
<a name="network"></a>   
## <a name="creating-the-dataflow-network"></a>Tworzenie sieci przepływu danych  
 W tej sekcji opisano sposób tworzenia sieci przepływu danych, która wykonuje przetwarzanie obrazu.  
  
### <a name="to-create-the-dataflow-network"></a>Aby utworzyć sieć przepływu danych  
  
1. Dodaj odwołanie do elementu System. Threading. Tasks. przepływu danych. dll do projektu.  
  
2. Upewnij się, że Form1.cs (Form1. vb dla Visual Basic) zawiera `using` następujące`Using` instrukcje (w Visual Basic):  
  
     [!code-csharp[TPLDataflow_CompositeImages#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#1)]  
  
3. Dodaj następujące składowe danych do `Form1` klasy:  
  
     [!code-csharp[TPLDataflow_CompositeImages#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#2)]  
  
4. Dodaj następującą metodę `CreateImageProcessingNetwork` `Form1` do klasy. Ta metoda służy do tworzenia sieci przetwarzania obrazów.  
  
     [!code-csharp[TPLDataflow_CompositeImages#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#3)]  
  
5. Zaimplementuj `LoadBitmaps` metodę.  
  
     [!code-csharp[TPLDataflow_CompositeImages#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#4)]  
  
6. Zaimplementuj `CreateCompositeBitmap` metodę.  
  
     [!code-csharp[TPLDataflow_CompositeImages#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#5)]  
  
    > [!NOTE]
    >  C# Wersja`CreateCompositeBitmap` metody używa wskaźników w celu zapewnienia <xref:System.Drawing.Bitmap?displayProperty=nameWithType> wydajnego przetwarzania obiektów. W związku z tym należy włączyć opcję Zezwalaj na niebezpieczny **kod** w projekcie, aby można było [](../../csharp/language-reference/keywords/unsafe.md) użyć słowa kluczowego unsafe. Aby uzyskać więcej informacji na temat włączania niebezpiecznego kodu C# w projekcie wizualizacji, zobacz [stronę Kompilacja,C#Projektant projektu ()](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
 W poniższej tabeli opisano elementy członkowskie sieci.  
  
|Element członkowski|Typ|Opis|  
|------------|----------|-----------------|  
|`loadBitmaps`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Pobiera ścieżkę folderu jako dane wejściowe i tworzy kolekcję <xref:System.Drawing.Bitmap> obiektów jako dane wyjściowe.|  
|`createCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Pobiera kolekcję <xref:System.Drawing.Bitmap> obiektów jako dane wejściowe i tworzy kompozytową mapę bitową jako dane wyjściowe.|  
|`displayCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Wyświetla kompozytową mapę bitową w formularzu.|  
|`operationCancelled`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Wyświetla obraz wskazujący, że operacja została anulowana, i umożliwia użytkownikowi wybranie innego folderu.|  
  
 Aby połączyć bloki przepływu danych w celu utworzenia sieci, w tym przykładzie zostanie <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> użyta metoda. Metoda zawiera przeciążoną wersję, która <xref:System.Predicate%601> pobiera obiekt, który określa, czy blok docelowy akceptuje lub odrzuca komunikat. <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> Ten mechanizm filtrowania umożliwia blokom komunikatów odbieranie tylko określonych wartości. W tym przykładzie sieć może rozgałęziać się na jeden z dwóch sposobów. Gałąź główna ładuje obrazy z dysku, tworzy obraz złożony i wyświetla ten obraz w formularzu. Gałąź alternatywna anuluje bieżącą operację. <xref:System.Predicate%601> Obiekty umożliwiają blokom przepływu danych wzdłuż gałęzi głównej, aby przełączyć się na gałąź alternatywną poprzez odrzucenie niektórych komunikatów. Na przykład, jeśli użytkownik anuluje operację, blok `createCompositeBitmap` przepływu danych tworzy `null` (`Nothing` w Visual Basic) jako dane wyjściowe. Blok `displayCompositeBitmap` przepływu danych `operationCancelled`odrzuca wartości wejściowe i w związku z tym komunikat jest oferowany dla. `null` Blok `operationCancelled` przepływu danych akceptuje wszystkie komunikaty i w związku z tym wyświetla obraz, aby wskazać, że operacja została anulowana.  
  
 Na poniższej ilustracji przedstawiono sieć przetwarzania obrazów:  
  
 ![Ilustracja przedstawiająca sieć przetwarzania obrazów.](./media/walkthrough-using-dataflow-in-a-windows-forms-application/dataflow-winforms-image-processing.png)  
  
 Ponieważ bloki `operationCancelled` i przepływu danych działają na interfejsie użytkownika, należy pamiętać, że te akcje są wykonywane w wątku interfejsu użytkownika. `displayCompositeBitmap` W tym celu w czasie konstruowania obiekty te udostępniają <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> obiekt, który <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> ma właściwość ustawioną na <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> Metoda<xref:System.Threading.Tasks.TaskScheduler> tworzy obiekt, który wykonuje prace w bieżącym kontekście synchronizacji. Ponieważ metoda jest wywoływana z procedury obsługi przycisku **Wybierz folder** , który działa w wątku interfejsu użytkownika, akcje dla `displayCompositeBitmap` bloków i `operationCancelled` przepływu danych również są uruchamiane w wątku interfejsu użytkownika. `CreateImageProcessingNetwork`  
  
 W tym przykładzie używa udostępnionego tokenu anulowania zamiast ustawiania właściwości, <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> ponieważ właściwość trwale anuluje wykonywanie bloku przepływu danych. Token anulowania umożliwia korzystanie z tej samej sieci przepływu danych wiele razy, nawet jeśli użytkownik anuluje jedną lub więcej operacji. Przykład, który używa <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> do trwałego anulowania wykonywania bloku przepływu danych, znajduje się w temacie [How to: Anuluj blok](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md)przepływu danych.  
  
<a name="ui"></a>   
## <a name="connecting-the-dataflow-network-to-the-user-interface"></a>Łączenie sieci przepływu danych z interfejsem użytkownika  
 W tej sekcji opisano sposób łączenia sieci przepływu danych z interfejsem użytkownika. Tworzenie obrazu złożonego i anulowanie operacji są inicjowane z przycisków **Wybierz folder** i **Anuluj** . Gdy użytkownik wybierze jeden z tych przycisków, odpowiednia akcja zostanie zainicjowana w sposób asynchroniczny.  
  
### <a name="to-connect-the-dataflow-network-to-the-user-interface"></a>Aby połączyć sieć przepływu danych z interfejsem użytkownika  
  
1. W projektancie formularzy dla formularza głównego Utwórz procedurę obsługi <xref:System.Windows.Forms.ToolStripItem.Click> zdarzeń dla zdarzenia dla przycisku **Wybierz folder** .  
  
2. Zaimplementuj zdarzenie dla przycisku **Wybierz folder.** <xref:System.Windows.Forms.ToolStripItem.Click>  
  
     [!code-csharp[TPLDataflow_CompositeImages#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#6)]  
  
3. W projektancie formularzy dla formularza głównego Utwórz procedurę obsługi <xref:System.Windows.Forms.ToolStripItem.Click> zdarzeń dla zdarzenia dla przycisku **Anuluj** .  
  
4. Zaimplementuj zdarzenie dla przycisku **Anuluj.** <xref:System.Windows.Forms.ToolStripItem.Click>  
  
     [!code-csharp[TPLDataflow_CompositeImages#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#7)]  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a>Kompletny przykład  
 Poniższy przykład pokazuje kompletny kod dla tego przewodnika.  
  
 [!code-csharp[TPLDataflow_CompositeImages#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#100)]  
  
 Na poniższej ilustracji przedstawiono typowe dane wyjściowe folderu Common \Sample obrazy \ folder.  
  
 ![Aplikacja Windows Forms](../../../docs/standard/parallel-programming/media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")  

## <a name="see-also"></a>Zobacz także

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
