---
title: 'Wskazówki: Korzystanie z przepływu danych w aplikacji Windows Forms'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- TPL dataflow library, in Windows Forms
- Task Parallel Library, dataflows
- Windows Forms, and TPL
ms.assetid: 9c65cdf7-660c-409f-89ea-59d7ec8e127c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49935c471d10e438763e41b07944047b0924af09
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864673"
---
# <a name="walkthrough-using-dataflow-in-a-windows-forms-application"></a>Wskazówki: Korzystanie z przepływu danych w aplikacji Windows Forms
W tym dokumencie pokazano, jak utworzyć sieć bloków przepływu danych, które wykonują przetwarzania obrazów w aplikacji Windows Forms.  
  
 W tym przykładzie ładuje pliki obrazów z określonego folderu, do tworzenia obrazu złożonego i wyświetla wynik. W przykładzie użyto modelu przepływu danych do trasy obrazów za pośrednictwem sieci. W modelu przepływu danych niezależnie od składników programu komunikować się ze sobą, wysyłając komunikaty. Gdy składnik otrzymuje komunikat, wykonuje niektóre akcje, a następnie przekazuje jego wynik do innego składnika. Porównać ją z modelu przepływu sterowania, w której aplikacja używa struktury sterujące, na przykład, instrukcje warunkowe, pętli i tak dalej, aby kontrolować kolejność operacji w programie.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Odczyt [przepływu danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) przed rozpoczęciem tego instruktażu.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="sections"></a>Sekcje  
 Ten przewodnik zawiera następujące sekcje:  
  
-   [Tworzenie aplikacji Windows Forms](#winforms)  
  
-   [Tworzenie sieci przepływu danych](#network)  
  
-   [Proces łączenia dwóch sieci przepływu danych interfejsu użytkownika](#ui)  
  
-   [Kompletny przykład](#complete)  
  
<a name="winforms"></a>   
## <a name="creating-the-windows-forms-application"></a>Tworzenie aplikacji Windows Forms  
 W tej sekcji opisano sposób tworzenia podstawowych aplikacji Windows Forms i dodawanie formantów do formularza głównego.  
  
#### <a name="to-create-the-windows-forms-application"></a>Aby utworzyć Windows Forms aplikacji  
  
1.  W programie Visual Studio Utwórz Visual C# lub Visual Basic **aplikacja interfejsu Windows Forms** projektu. W tym dokumencie projekt nazwano `CompositeImages`.  
  
2.  Projektant formularzy dla tego formularza Form1.cs (Form1.vb dla języka Visual Basic), Dodaj <xref:System.Windows.Forms.ToolStrip> kontroli.  
  
3.  Dodaj <xref:System.Windows.Forms.ToolStripButton> kontrolę <xref:System.Windows.Forms.ToolStrip> kontroli. Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> właściwości <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> i <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości **wybierz Folder**.  
  
4.  Dodaj drugą <xref:System.Windows.Forms.ToolStripButton> kontrolę <xref:System.Windows.Forms.ToolStrip> kontroli. Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> właściwości <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości **anulować**i <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> właściwość `False`.  
  
5.  Dodaj <xref:System.Windows.Forms.PictureBox> obiektu do formularza głównego. Ustaw <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>.  
  
<a name="network"></a>   
## <a name="creating-the-dataflow-network"></a>Tworzenie sieci przepływu danych  
 W tej sekcji opisano, jak utworzyć sieć przepływu danych, który wykonuje przetwarzanie obrazów.  
  
#### <a name="to-create-the-dataflow-network"></a>Aby utworzyć sieć przepływu danych  
  
1.  Dodaj odwołanie do System.Threading.Tasks.Dataflow.dll do projektu.  
  
2.  Upewnij się, że Form1.cs (Form1.vb dla języka Visual Basic) zawiera następujące `using` (`Using` w języku Visual Basic) instrukcji:  
  
     [!code-csharp[TPLDataflow_CompositeImages#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#1)]  
  
3.  Dodaj następujące elementy członkowskie danych do `Form1` klasy:  
  
     [!code-csharp[TPLDataflow_CompositeImages#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#2)]  
  
4.  Dodaj następującą metodę `CreateImageProcessingNetwork`, `Form1` klasy. Ta metoda tworzy sieci przetwarzania obrazów.  
  
     [!code-csharp[TPLDataflow_CompositeImages#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#3)]  
  
5.  Implementowanie `LoadBitmaps` metody.  
  
     [!code-csharp[TPLDataflow_CompositeImages#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#4)]  
  
6.  Implementowanie `CreateCompositeBitmap` metody.  
  
     [!code-csharp[TPLDataflow_CompositeImages#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#5)]  
  
    > [!NOTE]
    >  C# wersję `CreateCompositeBitmap` metoda używa wskaźników umożliwiające wydajne przetwarzanie <xref:System.Drawing.Bitmap?displayProperty=nameWithType> obiektów. W związku z tym, należy włączyć **Zezwalaj na niebezpieczny kod** opcji w projekcie, aby można było używać [niebezpieczne](~/docs/csharp/language-reference/keywords/unsafe.md) — słowo kluczowe. Aby uzyskać więcej informacji o sposobie włączania niebezpieczny kod w projektach Visual C#, zobacz [Stroka kompilacji, Projektant projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
 W poniższej tabeli opisano elementy członkowskie w sieci.  
  
|Element członkowski|Typ|Opis|  
|------------|----------|-----------------|  
|`loadBitmaps`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Pobiera ścieżkę folderu jako dane wejściowe i tworzy zbiór <xref:System.Drawing.Bitmap> obiektów jako dane wyjściowe.|  
|`createCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Pobiera kolekcję <xref:System.Drawing.Bitmap> obiektów jako dane wejściowe i generuje złożone mapy bitowej jako dane wyjściowe.|  
|`displayCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Wyświetla złożone mapy bitowej w formularzu.|  
|`operationCancelled`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Wyświetla obraz, aby wskazać, że operacja została anulowana i umożliwia użytkownikowi wybranie innego folderu.|  
  
 Aby połączyć z bloków przepływu danych w celu utworzenia sieci, w tym przykładzie użyto <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> metody. <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> Metoda zawiera przeciążona wersja, która przyjmuje <xref:System.Predicate%601> obiekt, który określa, czy blok docelowy akceptuje lub odrzuca komunikat. Ten mechanizm filtrowania umożliwiają blokadom odbierać tylko niektóre wartości. W tym przykładzie sieci można rozgałęziać w jeden z dwóch sposobów. Główna gałąź ładuje obrazy z dysku, do tworzenia obrazu złożonego i wyświetla tego obrazu w formularzu. Alternatywne gałęzi anuluje bieżącą operację. <xref:System.Predicate%601> Obiektów umożliwiają blokom przepływu danych, wraz z głównej gałęzi, aby przełączyć się do alternatywnego gałęzi przez odrzucenie niektórych komunikatów. Na przykład, jeśli użytkownik anuluje operację, bloku przepływu danych `createCompositeBitmap` tworzy `null` (`Nothing` w języku Visual Basic) jako dane wyjściowe. W bloku przepływu danych `displayCompositeBitmap` odrzuca `null` wartości wejściowych, a w związku z tym, komunikat jest oferowany `operationCancelled`. W bloku przepływu danych `operationCancelled` akceptuje wszystkie komunikaty i dlatego wyświetla obraz, aby wskazać, że operacja została anulowana.  
  
 Poniższa ilustracja przedstawia sieci przetwarzania obrazów.  
  
 ![Sieci przetwarzania obrazów](../../../docs/standard/parallel-programming/media/dataflowwinforms.png "DataflowWinForms")  
  
 Ponieważ `displayCompositeBitmap` i `operationCancelled` przepływu danych blokuje działanie w interfejsie użytkownika, ważne jest, czy w wątku interfejsu użytkownika są wykonywane następujące akcje. Aby to osiągnąć, podczas konstruowania, należy podać tych obiektów, każdy <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> obiekt, który ma <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> właściwością <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> Metoda tworzy <xref:System.Threading.Tasks.TaskScheduler> obiektu, który wykonuje pracę w bieżącym kontekście synchronizacji. Ponieważ `CreateImageProcessingNetwork` metoda jest wywoływana w procedurze obsługi **wybierz Folder** przycisku, w którym działa w interfejsie użytkownika wątku akcje w przypadku `displayCompositeBitmap` i `operationCancelled` bloków przepływu danych również uruchomić na wątek interfejsu użytkownika.  
  
 W tym przykładzie użyto token anulowania udostępnionego zamiast ustawiać <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> właściwość ponieważ <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> właściwość trwale anuluje wykonanie bloku przepływu danych. Token anulowania umożliwia w tym przykładzie ponownie użyć tej samej sieci przepływu danych wielokrotnie, nawet wtedy, gdy użytkownik anuluje co najmniej jednej operacji. Aby uzyskać przykład, który używa <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> trwale anulować wykonanie bloku przepływu danych, zobacz [porady: anulowanie bloku przepływu danych](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md).  
  
<a name="ui"></a>   
## <a name="connecting-the-dataflow-network-to-the-user-interface"></a>Proces łączenia dwóch sieci przepływu danych interfejsu użytkownika  
 W tej sekcji opisano, jak połączyć sieć przepływu danych z interfejsu użytkownika. Tworzenie obrazu złożonego i anulowanie operacji są inicjowane z **wybierz Folder** i **anulować** przycisków. Gdy użytkownik wybierze jeden z tych przycisków, odpowiednie działanie jest inicjowane w sposób asynchroniczny.  
  
#### <a name="to-connect-the-dataflow-network-to-the-user-interface"></a>Aby połączyć sieć przepływu danych z interfejsu użytkownika  
  
1.  W Projektancie formularza dla tego formularza, należy utworzyć program obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenie **wybierz Folder** przycisku.  
  
2.  Implementowanie <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenie **wybierz Folder** przycisku.  
  
     [!code-csharp[TPLDataflow_CompositeImages#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#6)]  
  
3.  W Projektancie formularza dla tego formularza, należy utworzyć program obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenie **anulować** przycisku.  
  
4.  Implementowanie <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenie **anulować** przycisku.  
  
     [!code-csharp[TPLDataflow_CompositeImages#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#7)]  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a>Kompletny przykład  
 Poniższy przykład pokazuje kompletny kod dla tego przewodnika.  
  
 [!code-csharp[TPLDataflow_CompositeImages#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#100)]  
  
 Na poniższej ilustracji przedstawiono typowe dane wyjściowe do wspólnego folderu \Sample Pictures\.  
  
 ![Windows Forms aplikacji](../../../docs/standard/parallel-programming/media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")  

## <a name="see-also"></a>Zobacz także

- [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
