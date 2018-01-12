---
title: "Wskazówki: Korzystanie z przepływu danych w aplikacji Windows Forms"
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
helpviewer_keywords:
- TPL dataflow library, in Windows Forms
- Task Parallel Library, dataflows
- Windows Forms, and TPL
ms.assetid: 9c65cdf7-660c-409f-89ea-59d7ec8e127c
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e5389b1a9d608ad8aae002f3ef9b00420f998b76
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-using-dataflow-in-a-windows-forms-application"></a>Wskazówki: Korzystanie z przepływu danych w aplikacji Windows Forms
Ten dokument przedstawia sposób tworzenia sieci bloków przepływu danych, które wykonują przetwarzania obrazu w aplikacji formularzy systemu Windows.  
  
 W tym przykładzie ładuje pliki obrazów z określonego folderu, tworzy obraz złożone i wyświetla wyniki. W przykładzie użyto model przepływu danych trasy obrazów za pośrednictwem sieci. W modelu przepływu danych niezależnie od składników programu komunikować się ze sobą przy wysyłaniu wiadomości. Składnik odebrania wiadomości wykonuje akcję, a następnie przekazuje jego wynik do innego składnika. Porównać ją z modelu przepływu sterowania, w którym aplikacja używa struktury sterujące, na przykład, warunkowe instrukcje pętli i tak dalej, aby określić kolejność operacji w programie.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Odczyt [przepływu danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) przed skorzystaniem z tego przewodnika.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="sections"></a>Sekcje  
 Ten przewodnik zawiera następujące sekcje:  
  
-   [Tworzenie aplikacji formularzy systemu Windows](#winforms)  
  
-   [Tworzenie sieci przepływu danych](#network)  
  
-   [Połączenie z siecią przepływu danych interfejsu użytkownika](#ui)  
  
-   [Pełny przykład](#complete)  
  
<a name="winforms"></a>   
## <a name="creating-the-windows-forms-application"></a>Tworzenie aplikacji formularzy systemu Windows  
 W tej sekcji opisano sposób tworzenia podstawowej aplikacji formularzy systemu Windows i dodawanie formantów do formularza głównego.  
  
#### <a name="to-create-the-windows-forms-application"></a>Aby utworzyć systemu Windows w aplikacjach formularzy  
  
1.  W [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], Utwórz [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] lub Visual Basic **aplikacji Windows Forms** projektu. W tym dokumencie projektu o nazwie `CompositeImages`.  
  
2.  W formularzu projektanta dla tego formularza, pliku Form1.cs (Form1.vb dla [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), Dodaj <xref:System.Windows.Forms.ToolStrip> formantu.  
  
3.  Dodaj <xref:System.Windows.Forms.ToolStripButton> formant <xref:System.Windows.Forms.ToolStrip> formantu. Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> właściwości <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> i <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości **wybierz Folder**.  
  
4.  Dodaj drugi <xref:System.Windows.Forms.ToolStripButton> formant <xref:System.Windows.Forms.ToolStrip> formantu. Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> właściwości <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, <xref:System.Windows.Forms.ToolStripItem.Text%2A> właściwości **anulować**i <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> właściwości `False`.  
  
5.  Dodaj <xref:System.Windows.Forms.PictureBox> obiektu do formularza głównego. Ustaw <xref:System.Windows.Forms.Control.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Fill>.  
  
<a name="network"></a>   
## <a name="creating-the-dataflow-network"></a>Tworzenie sieci przepływu danych  
 Ta sekcja zawiera opis sposobu tworzenia sieci przepływu danych, która przetwarza obrazu.  
  
#### <a name="to-create-the-dataflow-network"></a>Aby utworzyć sieć przepływu danych  
  
1.  Dodaj odwołanie do System.Threading.Tasks.Dataflow.dll do projektu.  
  
2.  Upewnij się, że pliku Form1.cs (Form1.vb dla [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) zawiera następujące `using` (`Using` w [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) instrukcji:  
  
     [!code-csharp[TPLDataflow_CompositeImages#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#1)]  
  
3.  Dodaj następujące elementy członkowskie danych, aby `Form1` klasy:  
  
     [!code-csharp[TPLDataflow_CompositeImages#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#2)]  
  
4.  Dodaj następującą metodę `CreateImageProcessingNetwork`, do `Form1` klasy. Ta metoda tworzy sieci przetwarzania obrazów.  
  
     [!code-csharp[TPLDataflow_CompositeImages#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#3)]  
  
5.  Implementowanie `LoadBitmaps` metody.  
  
     [!code-csharp[TPLDataflow_CompositeImages#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#4)]  
  
6.  Implementowanie `CreateCompositeBitmap` metody.  
  
     [!code-csharp[TPLDataflow_CompositeImages#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#5)]  
  
    > [!NOTE]
    >  C# wersja `CreateCompositeBitmap` — metoda używa wskaźników, aby umożliwić przetwarzanie wydajne <xref:System.Drawing.Bitmap?displayProperty=nameWithType> obiektów. W związku z tym należy włączyć **niebezpiecznego kodu** opcji w projekcie, aby można było używać [niebezpieczne](~/docs/csharp/language-reference/keywords/unsafe.md) — słowo kluczowe. Aby uzyskać więcej informacji o sposobie włączania niebezpieczny kod w [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] projektu, zobacz [kompilacji strony projektanta projektu (C#)] https://msdn.microsoft.com/library/kb4wyys2).  
  
 W poniższej tabeli opisano elementy członkowskie w sieci.  
  
|Element członkowski|Typ|Opis|  
|------------|----------|-----------------|  
|`loadBitmaps`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Ścieżka folderu, jako dane wejściowe i tworzy kolekcję <xref:System.Drawing.Bitmap> obiektów jako dane wyjściowe.|  
|`createCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Pobiera kolekcję <xref:System.Drawing.Bitmap> obiekty jako dane wejściowe i tworzy mapę bitową złożonego jako dane wyjściowe.|  
|`displayCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Wyświetla złożonego mapy bitowej w formularzu.|  
|`operationCancelled`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Wyświetla obraz, który będzie wskazywać, że operacja została anulowana i umożliwia użytkownikowi wybranie innego folderu.|  
  
 Aby połączyć bloków przepływu danych w celu utworzenia sieci, w tym przykładzie użyto <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> metody. <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> Metoda zawiera zastąpionej wersji, która przyjmuje <xref:System.Predicate%601> obiekt, który określa, czy blok docelowy akceptuje lub odrzuca komunikat. Ten mechanizm filtrowania umożliwia bloki komunikatów do odbierania tylko niektóre wartości. W tym przykładzie sieci można gałęzi w jeden z dwóch sposobów. Gałęzi głównej ładuje obrazów z dysku, tworzy obraz złożone i wyświetla ten obraz w formularzu. Alternatywne gałęzi anuluje bieżącą operację. <xref:System.Predicate%601> Obiektów Włącz bloków przepływu danych wzdłuż gałęzi głównej, aby przełączyć się do gałęzi alternatywnych odrzucając komunikatów. Na przykład, jeśli użytkownik anuluje operację bloku przepływu danych `createCompositeBitmap` tworzy `null` (`Nothing` w [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) jako dane wyjściowe. W bloku przepływu danych `displayCompositeBitmap` odrzuca `null` wartości wejściowe i w związku z tym komunikacie jest oferowana `operationCancelled`. W bloku przepływu danych `operationCancelled` akceptuje wszystkie komunikaty i w związku z tym Wyświetla obraz, aby wskazać, że operacja została anulowana.  
  
 Na poniższej ilustracji przedstawiono sieci przetwarzania obrazów.  
  
 ![Sieci przetwarzania obrazów](../../../docs/standard/parallel-programming/media/dataflowwinforms.png "DataflowWinForms")  
  
 Ponieważ `displayCompositeBitmap` i `operationCancelled` przepływu danych bloki działania w interfejsie użytkownika, ważne jest, że te zdarzenia w wątku interfejsu użytkownika. Aby to osiągnąć, podczas konstruowania, należy podać te obiekty każdego <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> obiektu, który ma <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> ustawioną właściwość <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> Metoda tworzy <xref:System.Threading.Tasks.TaskScheduler> obiekt, który przeprowadza pracę na bieżący kontekst synchronizacji. Ponieważ `CreateImageProcessingNetwork` metoda jest wywoływana w procedurze obsługi **wybierz Folder** przycisk, w której działa w interfejsie użytkownika wątku akcje `displayCompositeBitmap` i `operationCancelled` bloków przepływu danych również uruchomić na wątek interfejsu użytkownika.  
  
 W tym przykładzie użyto token anulowania udostępnionego zamiast ustawienie <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> właściwości ponieważ <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> właściwości trwale anuluje wykonywania bloku przepływu danych. Token anulowania umożliwia ponowne użycie tej samej sieci przepływu danych wielokrotnie, nawet wtedy, gdy użytkownik anuluje jeden lub więcej operacji w tym przykładzie. Na przykład, który używa <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> trwale anulować wykonywanie bloku przepływu danych, zobacz [porady: anulowanie bloku przepływu danych](../../../docs/standard/parallel-programming/how-to-cancel-a-dataflow-block.md).  
  
<a name="ui"></a>   
## <a name="connecting-the-dataflow-network-to-the-user-interface"></a>Połączenie z siecią przepływu danych interfejsu użytkownika  
 W tej sekcji opisano sposób nawiązywania połączenia z siecią przepływu danych interfejsu użytkownika. Tworzenie obrazu złożone i anulowanie operacji są inicjowane z **wybierz Folder** i **anulować** przycisków. Gdy użytkownik wybierze jeden z tych przycisków, odpowiednie działanie jest inicjowane w sposób asynchroniczny.  
  
#### <a name="to-connect-the-dataflow-network-to-the-user-interface"></a>Aby połączyć sieć przepływu danych interfejsu użytkownika  
  
1.  W projektancie formularzy dla tego formularza należy utworzyć programu obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia dla **wybierz Folder** przycisku.  
  
2.  Implementowanie <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia dla **wybierz Folder** przycisku.  
  
     [!code-csharp[TPLDataflow_CompositeImages#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#6)]  
  
3.  W projektancie formularzy dla tego formularza należy utworzyć programu obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia dla **anulować** przycisku.  
  
4.  Implementowanie <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia dla **anulować** przycisku.  
  
     [!code-csharp[TPLDataflow_CompositeImages#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#7)]  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a>Kompletny przykład  
 Poniższy przykład przedstawia kompletny kod dla tego przewodnika.  
  
 [!code-csharp[TPLDataflow_CompositeImages#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#100)]  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe zazwyczaj wspólnym folderze \Sample Pictures\.  
  
 ![Aplikacji formularzy systemu Windows](../../../docs/standard/parallel-programming/media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")  

## <a name="see-also"></a>Zobacz też  
 [Przepływ danych](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
