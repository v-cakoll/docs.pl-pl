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
ms.openlocfilehash: 21df7228f8dca884c5f36be23ae1aced7b31cc9a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942216"
---
# <a name="textelement-content-model-overview"></a>Przegląd Model zawartości TextElement
Ten model zawartości zawiera opis obsługiwanej zawartości dla programu <xref:System.Windows.Documents.TextElement>. <xref:System.Windows.Documents.Paragraph> Klasa jest <xref:System.Windows.Documents.TextElement>typem. Model zawartości opisuje, jakie obiekty/elementy mogą być zawarte w innych. Ten przegląd podsumowuje model zawartości używany dla obiektów pochodnych od <xref:System.Windows.Documents.TextElement>. Aby uzyskać więcej informacji, zobacz [Omówienie dokumentu przepływu](flow-document-overview.md).  

<a name="text_element_classes"></a>   
## <a name="content-model-diagram"></a>Diagram modelu zawartości  
 Poniższy diagram podsumowuje model zawartości dla klas pochodnych <xref:System.Windows.Documents.TextElement> , a także sposobu dopasowania innych `TextElement` klas do tego modelu.  
  
 ![4b ](./media/flow-content-schema.png "Flow_Content_Schema") schematu zawierania zawartości przepływu  
  
 Jak widać na powyższym diagramie, elementy podrzędne dozwolone dla elementu nie muszą być ustalane w zależności od tego <xref:System.Windows.Documents.Block> , czy Klasa pochodzi od klasy <xref:System.Windows.Documents.Inline> lub klasy. Na <xref:System.Windows.Documents.Span> przykład <xref:System.Windows.Documents.Inline> <xref:System.Windows.Documents.Figure> <xref:System.Windows.Documents.Inline>Klasa pochodna może mieć tylko elementy podrzędne, ale (również Klasa pochodna) może mieć <xref:System.Windows.Documents.Block> tylko elementy podrzędne. <xref:System.Windows.Documents.Inline> W związku z tym diagram jest przydatny do szybkiego określania, który element może być zawarty w innym. Na przykład użyjemy diagramu, aby określić sposób konstruowania zawartości <xref:System.Windows.Controls.RichTextBox>przepływu.  
  
1. A <xref:System.Windows.Controls.RichTextBox> musi <xref:System.Windows.Documents.Block>zawierać, który z kolei musi zawierać obiekt pochodny. <xref:System.Windows.Documents.FlowDocument> Poniżej znajduje się odpowiedni segment z poprzedniego diagramu.  
  
     ![4b Reguły]zawierania RichTextBox(./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     Do tej pory może wyglądać znacznik.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2. Zgodnie <xref:System.Windows.Documents.Block> z diagramem istnieje kilka elementów do wyboru, <xref:System.Windows.Documents.Section> <xref:System.Windows.Documents.Table> <xref:System.Windows.Documents.List>takich jak <xref:System.Windows.Documents.Paragraph>,,, i <xref:System.Windows.Documents.BlockUIContainer> (zobacz klasy pochodne bloków na powyższym diagramie). Załóżmy, że <xref:System.Windows.Documents.Table>chcemy. Zgodnie <xref:System.Windows.Documents.Table> z powyższym diagramem <xref:System.Windows.Documents.TableRowGroup> zawiera <xref:System.Windows.Documents.TableRow> <xref:System.Windows.Documents.TableCell> elementy zawierające elementy, którezawierająobiektypochodne.<xref:System.Windows.Documents.Block> Poniżej znajduje się odpowiedni segment do <xref:System.Windows.Documents.Table> wykonania z poprzedniego diagramu.  
  
     ![4b Nadrzędny&#47;schemat podrzędny dla tabeli](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
     Poniżej znajduje się odpowiednie oznaczenie.  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3. Ponownie co najmniej jeden <xref:System.Windows.Documents.Block> element jest wymagany <xref:System.Windows.Documents.TableCell>poniżej. Aby to ułatwić, umieść trochę tekstu wewnątrz komórki. Możemy to zrobić przy użyciu <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.Run> elementu z. Poniżej przedstawiono odpowiednie segmenty z diagramu, które pokazują, że <xref:System.Windows.Documents.Paragraph> może <xref:System.Windows.Documents.Inline> przyjmować element <xref:System.Windows.Documents.Inline> i czy <xref:System.Windows.Documents.Run> (element) może przyjmować tylko zwykły tekst.  
  
     ![4b Nadrzędny&#47;schemat podrzędny dla akapitu](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
     ![4b Nadrzędny&#47;schemat podrzędny dla uruchomienia](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 Poniżej znajduje się cały przykład w znacznikach.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## <a name="working-with-textelement-content-programmatically"></a>Programistyczne praca z zawartością Tekstuelement  
 Zawartość a <xref:System.Windows.Documents.TextElement> jest tworzony przez kolekcje i programistycznie manipuluje <xref:System.Windows.Documents.TextElement> zawartością obiektów jest wykonywana przez pracę z tymi kolekcjami. Istnieją trzy różne kolekcje używane przez <xref:System.Windows.Documents.TextElement> klasy pochodne:  
  
- <xref:System.Windows.Documents.InlineCollection>: Reprezentuje kolekcję <xref:System.Windows.Documents.Inline> elementów. <xref:System.Windows.Documents.InlineCollection>definiuje dozwoloną zawartość <xref:System.Windows.Documents.Paragraph>podrzędną elementów, <xref:System.Windows.Documents.Span>, i <xref:System.Windows.Controls.TextBlock> .  
  
- <xref:System.Windows.Documents.BlockCollection>: Reprezentuje kolekcję <xref:System.Windows.Documents.Block> elementów. <xref:System.Windows.Documents.BlockCollection>definiuje dozwoloną <xref:System.Windows.Documents.FlowDocument>zawartość podrzędną elementów, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.TableCell> <xref:System.Windows.Documents.Floater>, i <xref:System.Windows.Documents.Figure> .  
  
- <xref:System.Windows.Documents.ListItemCollection>: Element zawartości przepływu reprezentujący określony element zawartości w uporządkowanej lub nieuporządkowanej kolejności <xref:System.Windows.Documents.List>.  
  
 Można manipulować (dodawać lub usuwać elementy) z tych kolekcji przy użyciu odpowiednich właściwości elementów, **bloków**i elementów listy. W poniższych przykładach pokazano, jak manipulować zawartością zakresu przy użyciu właściwości Inlines.  
  
> [!NOTE]
> W tabeli są wykorzystywane kilka kolekcji do manipulowania zawartością, ale nie są tu omówione. Aby uzyskać więcej informacji, zobacz temat [Omówienie tabeli](table-overview.md).  
  
 Poniższy przykład tworzy nowy <xref:System.Windows.Documents.Span> obiekt, a następnie `Add` używa metody, aby dodać dwa teksty <xref:System.Windows.Documents.Span>jako elementy podrzędne elementu.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 Poniższy przykład tworzy nowy <xref:System.Windows.Documents.Run> element i wstawia go na początku. <xref:System.Windows.Documents.Span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 Poniższy przykład usuwa ostatni <xref:System.Windows.Documents.Inline> element <xref:System.Windows.Documents.Span>z.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 Poniższy przykład czyści całą zawartość (<xref:System.Windows.Documents.Inline> elementy) <xref:System.Windows.Documents.Span>z.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## <a name="types-that-share-this-content-model"></a>Typy, które współużytkują ten model zawartości  
 Następujące typy dziedziczą z <xref:System.Windows.Documents.TextElement> klasy i mogą być używane do wyświetlania zawartości opisanej w tym przeglądzie.  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 Należy pamiętać, że ta lista zawiera tylko typy nieabstrakcyjne [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]dystrybuowane z. Można użyć innych typów, które dziedziczą <xref:System.Windows.Documents.TextElement>z.  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## <a name="types-that-can-contain-textelement-objects"></a>Typy, które mogą zawierać obiekty TextElement  
 Zobacz artykuł [model zawartości WPF](../controls/wpf-content-model.md).  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzanie parametrem FlowDocument przez właściwość Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Zarządzanie przepływem elementów zawartości za pomocą właściwości Blocks](how-to-manipulate-flow-content-elements-through-the-blocks-property.md)
- [Zarządzanie parametrem FlowDocument przez właściwość Blocks](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Zarządzanie kolumnami tabeli za pomocą właściwości Columns](how-to-manipulate-table-columns-through-the-columns-property.md)
- [Zarządzanie grupami wierszy tabeli za pomocą właściwości RowGroups](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
