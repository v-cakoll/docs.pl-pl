---
title: Przegląd Model zawartości TextElement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], flow documents
- TextElement content model [WPF]
- flow content elements [WPF], TextElement content model
ms.assetid: d0a7791c-b090-438c-812f-b9d009d83ee9
ms.openlocfilehash: ecb9441bc63eae41cfbbadf3bf81b0e5392bd0cb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125123"
---
# <a name="textelement-content-model-overview"></a>Przegląd Model zawartości TextElement
Ten przegląd model zawartości w tym artykule opisano obsługiwane zawartość <xref:System.Windows.Documents.TextElement>. <xref:System.Windows.Documents.Paragraph> Klasa jest typem <xref:System.Windows.Documents.TextElement>. Model zawartości w tym artykule opisano obiekty/elementy mogą być zawarte w innym. W tym omówieniu przedstawiono podsumowanie model zawartości używane dla obiektów pochodzących od <xref:System.Windows.Documents.TextElement>. Aby uzyskać więcej informacji, zobacz [Przegląd dokumentu przepływu](flow-document-overview.md).  

<a name="text_element_classes"></a>   
## <a name="content-model-diagram"></a>Diagram modelu zawartości  
 Poniższy diagram przedstawia model zawartości dla klasy pochodne <xref:System.Windows.Documents.TextElement> oraz jak inne non - `TextElement` klasy do takiego modelu pasuje.  
  
 ![Diagram: Przepływ zawartości zawierania schematu](./media/flow-content-schema.png "Flow_Content_Schema")  
  
 Jak widać w powyższym diagramie, elementy podrzędne dozwolone dla elementu nie zawsze zależą od tego, czy klasa jest pochodną <xref:System.Windows.Documents.Block> klasy lub <xref:System.Windows.Documents.Inline> klasy. Na przykład <xref:System.Windows.Documents.Span> ( <xref:System.Windows.Documents.Inline>-klasy pochodnej) może mieć tylko <xref:System.Windows.Documents.Inline> elementy podrzędne, ale <xref:System.Windows.Documents.Figure> (również <xref:System.Windows.Documents.Inline>-klasy pochodnej) może mieć tylko <xref:System.Windows.Documents.Block> elementów podrzędnych. W związku z tym diagram jest przydatne w przypadku szybkie ustalenie zgodności tego, jaki element mogą być zawarte w innym. Na przykład użyjmy diagramu do określenia sposobu konstruowania zawartości przepływu <xref:System.Windows.Controls.RichTextBox>.  
  
1.  A <xref:System.Windows.Controls.RichTextBox> musi zawierać <xref:System.Windows.Documents.FlowDocument> który z kolei musi zawierać <xref:System.Windows.Documents.Block>-pochodnych obiektu. Poniżej przedstawiono odpowiadającym segmencie z poprzedniego diagramu.  
  
     ![Diagram: RichTextBox containment rules](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     Tej pory jest to, jak może wyglądać znaczników.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2.  Zgodnie z diagramem, istnieje kilka <xref:System.Windows.Documents.Block> elementów z tym <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.List>, i <xref:System.Windows.Documents.BlockUIContainer> (Zobacz klasy pochodnej bloku na powyższym diagramie). Załóżmy, że chcemy <xref:System.Windows.Documents.Table>. Zgodnie z powyższym diagramie <xref:System.Windows.Documents.Table> zawiera <xref:System.Windows.Documents.TableRowGroup> zawierający <xref:System.Windows.Documents.TableRow> elementów, które zawierają <xref:System.Windows.Documents.TableCell> elementy, które zawierają <xref:System.Windows.Documents.Block>-pochodnych obiektu. Poniżej przedstawiono odpowiadającym segmencie: dla <xref:System.Windows.Documents.Table> pobranych z na powyższym diagramie.  
  
     ![Diagram: Parent&#47;child schema for Table](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
     Poniżej znajduje się odpowiedni kod znaczników.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3.  Ponownie co najmniej jeden <xref:System.Windows.Documents.Block> elementy są wymagane, poniżej <xref:System.Windows.Documents.TableCell>. Się to uprościć, możemy umieścić tekst w komórce. Możemy to zrobić za pomocą <xref:System.Windows.Documents.Paragraph> z <xref:System.Windows.Documents.Run> elementu. Oto odpowiednie segmentów z diagramu, na którym widać, że <xref:System.Windows.Documents.Paragraph> może potrwać <xref:System.Windows.Documents.Inline> elementu i że <xref:System.Windows.Documents.Run> ( <xref:System.Windows.Documents.Inline> elementu) przyjmuje tylko zwykły tekst.  
  
     ![Diagram: Nadrzędny&#47;schemat element podrzędny dla akapitu](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
     ![Diagram: Parent&#47;Child schema for Run](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 Poniżej znajduje się cały przykład w znacznikach.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## <a name="working-with-textelement-content-programmatically"></a>Praca z zawartości TextElement programowe  
 Zawartość <xref:System.Windows.Documents.TextElement> jest tworzone przez kolekcje, a tym samym programowo manipulowanie zawartością <xref:System.Windows.Documents.TextElement> obiektów odbywa się dzięki współpracy z tymi kolekcjami. Istnieją trzy różne kolekcje posługują się <xref:System.Windows.Documents.TextElement> -klas pochodnych:  
  
-   <xref:System.Windows.Documents.InlineCollection>: Reprezentuje kolekcję <xref:System.Windows.Documents.Inline> elementów. <xref:System.Windows.Documents.InlineCollection> definiuje zawartość elementu podrzędnego dopuszczalny rozmiar <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Span>, i <xref:System.Windows.Controls.TextBlock> elementów.  
  
-   <xref:System.Windows.Documents.BlockCollection>: Reprezentuje kolekcję <xref:System.Windows.Documents.Block> elementów. <xref:System.Windows.Documents.BlockCollection> definiuje zawartość elementu podrzędnego dopuszczalny rozmiar <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.TableCell>, <xref:System.Windows.Documents.Floater>, i <xref:System.Windows.Documents.Figure> elementów.  
  
-   <xref:System.Windows.Documents.ListItemCollection>: Elementu zawartości przepływu, który reprezentuje określonego elementu zawartości uporządkowane i nieuporządkowane <xref:System.Windows.Documents.List>.  
  
 Możesz manipulować (Dodawanie lub usuwanie elementów) w tych kolekcjach, za pomocą odpowiednich właściwości **Inlines**, **bloki**, i **ListItems**. W poniższych przykładach pokazano, jak i manipulować zawartością zakresu przy użyciu **Inlines** właściwości.  
  
> [!NOTE]
>  Tabela używa kilku kolekcji do manipulowania jego zawartość, ale one nie zostały omówione w tym miejscu. Aby uzyskać więcej informacji, zobacz [Omówienie tabel](table-overview.md).  
  
 Poniższy przykład tworzy nowy <xref:System.Windows.Documents.Span> obiektu, a następnie używa `Add` metody w celu dodania dwóch tekstu działa jako zawartości elementy podrzędne <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 Poniższy przykład tworzy nowy <xref:System.Windows.Documents.Run> elementów i wstawia go na początku <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 Poniższy przykład usuwa ostatni <xref:System.Windows.Documents.Inline> element <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 Poniższy przykład Czyści całą zawartość (<xref:System.Windows.Documents.Inline> elementy) z <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## <a name="types-that-share-this-content-model"></a>Typy, które współużytkują ten Model zawartości  
 Następujące typy dziedziczyć <xref:System.Windows.Documents.TextElement> klasy i mogą być używane do wyświetlania zawartości, opisane w tym omówieniu.  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 Należy pamiętać, że ta lista zawiera tylko typy nieabstrakcyjnej rozpowszechniać za pomocą [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]. Możesz użyć innych typów, które dziedziczą z <xref:System.Windows.Documents.TextElement>.  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## <a name="types-that-can-contain-textelement-objects"></a>Typy, które mogą zawierać obiekty TextElement  
 Zobacz [Model zawartości WPF](../controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzanie parametrem FlowDocument przez właściwość Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Zarządzanie przepływem elementów zawartości za pomocą właściwości Blocks](how-to-manipulate-flow-content-elements-through-the-blocks-property.md)
- [Zarządzanie parametrem FlowDocument przez właściwość Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Zarządzanie kolumnami tabeli za pomocą właściwości Columns](how-to-manipulate-table-columns-through-the-columns-property.md)
- [Zarządzanie grupami wierszy tabeli za pomocą właściwości RowGroups](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
