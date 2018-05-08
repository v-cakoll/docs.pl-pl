---
title: Przegląd Dokument przepływu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'documents [WPF], flow documents [WPF], , '
- ', '
- flow documents [WPF]
ms.assetid: ef236a50-d44f-43c8-ba7c-82b0c733c0b7
ms.openlocfilehash: 0cf8944298af62a512599fc52998a046c66fed9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="flow-document-overview"></a>Przegląd Dokument przepływu
Przepływ dokumenty są przeznaczone do optymalizacji wyświetlania i czytelności. Zamiast ustawiany jeden układ wstępnie zdefiniowane, dokumenty przepływu dynamicznie dostosować i ułożenia ich zawartość na podstawie czasu wykonywania zmiennych, takich jak rozmiar okna, rozdzielczość urządzenia i preferencje użytkownika opcjonalne. Ponadto przepływ dokumentów oferuje dokumentu zaawansowane funkcje, takie jak podział na strony i kolumn. Ten temat zawiera omówienie przepływu dokumentów i sposób ich tworzenia.  
  

  
<a name="what_is_a_flow_document"></a>   
## <a name="what-is-a-flow-document"></a>Co to jest dokument przepływu  
 Przepływ dokument jest przeznaczony do "ze zmianą ułożenia zawartości" w zależności od rozmiaru okna, rozdzielczość urządzenia i inne zmienne środowiskowe. Ponadto przepływ dokumenty mają wiele wbudowane funkcje takie jak wyszukiwanie, przeglądanie tryby optymalizacji czytelności i możliwość zmiany rozmiaru i wyglądu czcionek. Dokumenty przepływu najlepiej są wykorzystywane podczas czytelnej jest scenariusz użycia głównej dokumentu. Z kolei stałym dokumenty są przeznaczone do statycznego prezentację. Stały dokumenty są przydatne, gdy niezbędne jest wierności źródła zawartości. Zobacz [dokumentów na platformie WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md) Aby uzyskać więcej informacji na temat różnych typów dokumentów.  
  
 Na poniższej ilustracji przedstawiono przykładowy dokument przepływu wyświetlanych w kilka okien o różnych rozmiarach. Obszar wyświetlania zmian zawartości przepłynie najlepsze wykorzystanie dostępnego miejsca.  
  
 ![Przepływ ułożenia zawartości dokumentu](../../../../docs/framework/wpf/advanced/media/edocs-flowdocument.png "eDocs_FlowDocument")  
  
 Jak pokazano na ilustracji powyżej, zawartość śródwierszowa może zawierać wiele składników, w tym akapitów, list, obrazy i. Te składniki odpowiadają obiekty kod procedury i elementów w znaczniku. Firma Microsoft będą przekazywane tych klas szczegółowo później w [przepływ powiązanymi klasami](#flow_related_classes) sekcji z omówieniem tego zagadnienia. Teraz Oto prosty przykład kodu tworzącą dokumentu przepływu składające się z akapitu z tekstem bold i listy.
  
 [!code-xaml[FlowOvwSnippets_snip#SimpleFlowExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SimpleFlowExample.xaml#simpleflowexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SimpleFlowExample.cs#simpleflowcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SimpleFlowExample.vb#simpleflowcodeonlyexamplewholepage)]  
  
 Na poniższej ilustracji przedstawiono, jak wygląda ten fragment kodu.  
  
 ![Zrzut ekranu: Przykład renderowanego obiektu FlowDocument](../../../../docs/framework/wpf/advanced/media/flow-ovw-first-example.png "Flow_Ovw_First_Example")  
  
 W tym przykładzie <xref:System.Windows.Controls.FlowDocumentReader> kontroli jest używana do hostowania zawartości przepływu. Zobacz [typów dokumentów przepływu](#flow_document_types) uzyskać więcej informacji o dowolnej zawartości kontrolki hostingu. <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, i <xref:System.Windows.Documents.Bold> elementy są używane do kontrolowania formatowanie zawartości na podstawie ich kolejności w znaczniku. Na przykład <xref:System.Windows.Documents.Bold> element obejmuje równomiernie tylko część tekstu akapitu; w związku z tym bold jest tylko część tekstu. Użycie HTML będzie znane.  
  
 Jak wyróżniono na ilustracji powyżej istnieje kilka funkcji wbudowanych w dokumentach przepływu:
  
-   Wyszukiwania: Umożliwia użytkownikowi wyszukiwanie pełnotekstowe całego dokumentu.  
  
-   Tryb przeglądania: Użytkownik może wybrać tryb wyświetlanego w tym tryb wyświetlania (strony na a-time) jednej strony, dwa strony na pojedynczych (format księgi odczytu) wyświetlanie trybu i trybie przewijania ciągłego wyświetlania (nieograniczone od dołu).  Aby uzyskać więcej informacji na temat trybów wyświetlania, zobacz <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>.  
  
-   Formanty nawigacji strony: Tryb wyświetlania dokumentu używa stron, formantów nawigacji dołączyć przycisk, aby przejść do następnej strony (strzałkę w dół) lub poprzedniej strony (strzałkę w górę), jak również wskaźniki numer bieżącej strony i łączną liczbę stron. Przerzucanie strony można również wykonywać za pomocą klawiszy strzałek.  
  
-   Powiększenie: Kontrolki powiększania umożliwiają użytkownikowi zwiększyć lub zmniejszyć poziom powiększenia, kliknij przycisk plus lub minus przycisków, odpowiednio. Kontrolki powiększania także suwaka dostosowania poziomu powiększenia. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Controls.FlowDocumentReader.Zoom%2A>.  
  
 Te funkcje mogą być modyfikowane ustalane na podstawie formantu używany do obsługi dowolnej zawartości. W następnej sekcji opisano inne formanty.  
  
<a name="flow_document_types"></a>   
## <a name="flow-document-types"></a>Przepływ typów dokumentów  
 Wyświetlanie zawartości dokumentu przepływu i sposób wyświetlania jest zależne od tego, jak obiekt jest używana do hostowania zawartości przepływu. Istnieją cztery kontrolki, które obsługują wyświetlanie zawartości przepływu: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.RichTextBox>, i <xref:System.Windows.Controls.FlowDocumentScrollViewer>. Formanty krótko opisano poniżej.  
  
 **Uwaga:** <xref:System.Windows.Documents.FlowDocument> jest wymagany do bezpośrednio zawartość śródwierszowa hosta, aby korzystać z wszystkich tych wyświetlania formantów <xref:System.Windows.Documents.FlowDocument> umożliwiające hosting zawartości przepływu.  
  
### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader> zawiera funkcje, które umożliwiają użytkownikowi dynamicznie wybrać różne tryby wyświetlania, w tym tryb wyświetlania (strony na a-time) jednej strony, dwa strony na pojedynczych (format księgi odczytu) wyświetlanie trybu i trybie przewijania ciągłego wyświetlania (nieograniczone od dołu). Aby uzyskać więcej informacji na temat trybów wyświetlania, zobacz <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>. Jeśli nie potrzebujesz możliwości dynamicznie przełączać tryby wyświetlania różnych <xref:System.Windows.Controls.FlowDocumentPageViewer> i <xref:System.Windows.Controls.FlowDocumentScrollViewer> Podaj zawartości przeglądarek, które zostały usunięte w trybie przeglądania określonego jaśniejszego wagi przepływu.  
  
### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer i FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer> Pokazuje zawartość strony w czasie trybu wyświetlania, podczas gdy <xref:System.Windows.Controls.FlowDocumentScrollViewer> pokazuje zawartości w trybie przewijania ciągłego. Zarówno <xref:System.Windows.Controls.FlowDocumentPageViewer> i <xref:System.Windows.Controls.FlowDocumentScrollViewer> zostały usunięte w trybie przeglądania określonego. Porównaj z <xref:System.Windows.Controls.FlowDocumentReader>, która obejmuje funkcje, które umożliwiają użytkownikowi dynamicznie wybrać różne tryby wyświetlania (zgodnie z <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> wyliczenie), kosztem jest więcej zasobów niż <xref:System.Windows.Controls.FlowDocumentPageViewer> lub <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 Domyślnie pionowy pasek przewijania jest zawsze widoczne, a poziomy pasek przewijania jest widoczna, jeśli to konieczne. Domyślnie interfejs użytkownika dla <xref:System.Windows.Controls.FlowDocumentScrollViewer> nie obejmuje paska narzędzi, ale <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> właściwości może służyć do włączenia wbudowanego paska narzędzi.  
  
### <a name="richtextbox"></a>RichTextBox  
 Możesz użyć <xref:System.Windows.Controls.RichTextBox> Jeśli chcesz zezwolić użytkownikowi edytowanie zawartości przepływu. Na przykład, jeśli chcesz utworzyć edytora dozwolone użytkownika do manipulowania rzeczy, takich jak tabele, kursywa i bold formatowanie, itp., należy użyć <xref:System.Windows.Controls.RichTextBox>. Zobacz [omówienie RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md) Aby uzyskać więcej informacji.  
  
 **Uwaga:** przepływ zawartości wewnątrz <xref:System.Windows.Controls.RichTextBox> zachowuje się tak samo jak zawartość śródwierszowa zawarte w innych kontrolek. Na przykład Brak kolumn w <xref:System.Windows.Controls.RichTextBox> i dlatego nie automatyczna zmiana rozmiaru zachowanie. Ponadto zazwyczaj wbudowane funkcje przepływ zawartości jak wyszukiwanie, przeglądanie tryb, Nawigacja strony i powiększenia nie są dostępne w ramach <xref:System.Windows.Controls.RichTextBox>.  
  
<a name="creating_flow_content"></a>   
## <a name="creating-flow-content"></a>Tworzenie przepływu zawartości  
 Zawartość śródwierszowa może być skomplikowane, składające się z różnych elementów, w tym tekst, obrazy, tabel, a nawet <xref:System.Windows.UIElement> pochodnych klas takich jak kontrolki. Zrozumienie sposobu tworzenia złożonych przepływ zawartości, krytyczne są następujące kwestie:  
  
-   **Klasy związane z przepływem**: każdej klasy używane w dowolnej zawartości ma określone przeznaczenie. Ponadto Hierarchiczna relacja między klasami przepływu pomaga w zrozumieniu sposobu ich używania. Na przykład klasy wyprowadzone z <xref:System.Windows.Documents.Block> klasy służą do zawierają inne obiekty, podczas gdy pochodną klasy <xref:System.Windows.Documents.Inline> zawiera obiekty, które są wyświetlane.  
  
-   **Zawartość schematu**: dokument przepływu może wymagać dużej liczby elementów zagnieżdżonych. Schemat zawartości określa możliwe nadrzędny/podrzędny relacji między elementami.  
  
 Poniższe sekcje będą przekazywane każdego z tych obszarów bardziej szczegółowo.  
  
<a name="flow_related_classes"></a>   
## <a name="flow-related-classes"></a>Przepływ klasy pokrewne  
 Na poniższym diagramie przedstawiono obiekty najczęściej używane z dowolnej zawartości:  
  
 ![Diagram: Hierarchia klas elementu zawartości Flow](../../../../docs/framework/wpf/advanced/media/flow-class-hierarchy.png "Flow_Class_Hierarchy")  
  
 Do celów zawartość śródwierszowa istnieją dwie kategorie ważne:  
  
1.  **Klas pochodnych bloku**: nazywane również właśnie bloku elementów"" lub "Elementów zawartości bloku". Elementy, które dziedziczą z <xref:System.Windows.Documents.Block> może służyć do grupowania elementy podlegające Wspólnemu elementowi nadrzędnemu lub aby zastosować takie same atrybuty wspólne do grupy.  
  
2.  **Klas pochodnych wbudowanego**: nazywane również "Elementów zawartości śródwierszowych" lub po prostu "elementów śródwierszowych". Elementy, które dziedziczą z <xref:System.Windows.Documents.Inline> są albo zawarty w elemencie bloku lub innego elementu. Elementów śródwierszowych są często używane jako bezpośrednie kontener zawartości, który jest renderowany na ekranie. Na przykład <xref:System.Windows.Documents.Paragraph> (Element bloku) może zawierać <xref:System.Windows.Documents.Run> (elementu), ale <xref:System.Windows.Documents.Run> faktycznie zawiera tekst, który jest renderowany na ekranie.  
  
 Każda klasa w tych dwóch kategorii krótko opisano poniżej.  
  
### <a name="block-derived-classes"></a>Klas pochodnych bloku  
 **Akapitu**  
  
 <xref:System.Windows.Documents.Paragraph> jest zazwyczaj używany do zawartości grupy do akapitu. Najprostszym i najbardziej typowych akapitu polega na utworzeniu akapit tekstu.  
  
 [!code-xaml[FlowOvwSnippets_snip#ParagraphExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ParagraphExample.xaml#paragraphexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ParagraphExample.cs#paragraphcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ParagraphExample.vb#paragraphcodeonlyexamplewholepage)]  
  
 Również może jednak zawierać innych elementów pochodnych wbudowane, jak widać poniżej. 
  
 **Sekcja**  
  
 <xref:System.Windows.Documents.Section> Służy tylko do zawierać inne <xref:System.Windows.Documents.Block>-elementów pochodnych. Formatowanie elementy, które zawiera wszystkie domyślne nie ma zastosowania. Jednak żadnej właściwości wartości zestawu na <xref:System.Windows.Documents.Section> ma zastosowanie do jego elementów podrzędnych. Sekcja umożliwia także programowo iterację jego podrzędnej kolekcji. <xref:System.Windows.Documents.Section> jest używany w sposób podobny do \<DIV > znacznika w kodzie HTML.  
  
 W poniższym przykładzie trzy akapitów są zdefiniowane zgodnie z jednym <xref:System.Windows.Documents.Section>. Sekcja zawiera <xref:System.Windows.Documents.TextElement.Background%2A> wartość właściwości czerwony, w związku z tym kolor tła akapitów jest również czerwony.  
  
 [!code-xaml[FlowOvwSnippets_snip#SectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SectionExample.xaml#sectionexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SectionExample.cs#sectioncodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SectionExample.vb#sectioncodeonlyexamplewholepage)]  
  
 **BlockUIContainer**  
  
 <xref:System.Windows.Documents.BlockUIContainer> Umożliwia <xref:System.Windows.UIElement> elementy (tj. <xref:System.Windows.Controls.Button>) osadzone w zawartości przepływu pochodnych bloku. <xref:System.Windows.Documents.InlineUIContainer> (patrz poniżej) jest używany do osadzania <xref:System.Windows.UIElement> elementów pochodzących z wbudowanym przepływ zawartości. <xref:System.Windows.Documents.BlockUIContainer> i <xref:System.Windows.Documents.InlineUIContainer> są ważne, ponieważ nie istnieje inny sposób użycia <xref:System.Windows.UIElement> w dowolnej zawartości, chyba że jest on zawarty w jeden z tych dwóch elementów.  
  
 Poniższy przykład przedstawia użycie <xref:System.Windows.Documents.BlockUIContainer> element do hosta <xref:System.Windows.UIElement> obiektów w dowolnej zawartości.  
  
 [!code-xaml[SpanSnippets#_BlockUIXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml#_blockuixaml)]  
  
 Na poniższej ilustracji przedstawiono sposób renderowania w tym przykładzie.  
  
 ![Zrzut ekranu: UIElement osadzony w zawartości przepływu](../../../../docs/framework/wpf/advanced/media/blockuicontainer.png "BlockUIContainer")  
  
 **Lista**  
  
 <xref:System.Windows.Documents.List> Służy do tworzenia listy punktowanej lub liczbowe. Ustaw <xref:System.Windows.Documents.List.MarkerStyle%2A> właściwości <xref:System.Windows.TextMarkerStyle> wartość wyliczenia, aby określić styl listy. W poniższym przykładzie pokazano, jak utworzyć prostą listę.  
  
 [!code-xaml[FlowOvwSnippets_snip#ListExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ListExample.xaml#listexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ListExample.cs#listcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ListExample.vb#listcodeonlyexamplewholepage)]  
  
 **Uwaga:** <xref:System.Windows.Documents.List> jest jedynym elementem przepływu, który używa <xref:System.Windows.Documents.ListItemCollection> do zarządzania elementami podrzędnymi.  
  
 **Tabela**  
  
 <xref:System.Windows.Documents.Table> Służy do tworzenia tabeli. <xref:System.Windows.Documents.Table> przypomina <xref:System.Windows.Controls.Grid> elementu, ale ma więcej możliwości i dlatego wymaga większe obciążenie zasobów. Ponieważ <xref:System.Windows.Controls.Grid> jest <xref:System.Windows.UIElement>, nie można w dowolnej zawartości, chyba że znajduje się w <xref:System.Windows.Documents.BlockUIContainer> lub <xref:System.Windows.Documents.InlineUIContainer>. Aby uzyskać więcej informacji na temat <xref:System.Windows.Documents.Table>, zobacz [omówienie tabeli](../../../../docs/framework/wpf/advanced/table-overview.md).  
  
### <a name="inline-derived-classes"></a>Klas pochodnych wbudowany  
 **Uruchom**  
  
 <xref:System.Windows.Documents.Run> Służy do zawierają niesformatowanego tekstu. Mogą wymagać <xref:System.Windows.Documents.Run> obiektów, które ma być używany często w przepływ zawartości. Jednak w znaczniku <xref:System.Windows.Documents.Run> elementy nie są wymagane do użycia w sposób jawny. <xref:System.Windows.Documents.Run> jest wymagany do użycia podczas tworzenia lub manipulowanie przepływu dokumentów za pomocą kodu. Na przykład w przypadku znaczników poniżej pierwszy <xref:System.Windows.Documents.Paragraph> Określa <xref:System.Windows.Documents.Run> element jawnie, a druga nie. Oba punkty Generowanie identyczne dane wyjściowe.  
  
 [!code-xaml[FlowOvwSnippets_snip#RunExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/RunSnippetsExample.xaml#runexample1)]  
  
 **Uwaga:** począwszy [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], <xref:System.Windows.Documents.Run.Text%2A> właściwość <xref:System.Windows.Documents.Run> obiekt jest właściwości zależności. Możesz powiązać <xref:System.Windows.Documents.Run.Text%2A> właściwości do danych źródłowych, takich jak <xref:System.Windows.Controls.TextBlock>. <xref:System.Windows.Documents.Run.Text%2A> Właściwości w pełni obsługuje powiązania jednokierunkowe. <xref:System.Windows.Documents.Run.Text%2A> Właściwość obsługuje również Wiązanie dwukierunkowe, z wyjątkiem <xref:System.Windows.Controls.RichTextBox>. Na przykład zobacz <xref:System.Windows.Documents.Run.Text%2A?displayProperty=nameWithType>.  
  
 **Zakres**  
  
 <xref:System.Windows.Documents.Span> Grupowanie elementów zawartości innych śródwierszowych. Nie dostępu do właściwych renderowania jest stosowane do zawartości w <xref:System.Windows.Documents.Span> elementu. Jednak elementy który dziedziczyć <xref:System.Windows.Documents.Span> tym <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Italic> i <xref:System.Windows.Documents.Underline> formatowania tekstu.  
  
 Poniżej przedstawiono przykładowy <xref:System.Windows.Documents.Span> są używane do przechowywania zawartości śródwierszowej, łącznie z tekstem, <xref:System.Windows.Documents.Bold> elementu, a <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[FlowOvwSnippets_snip#SpanExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SpanExample.xaml#spanexamplewholepage)]  
  
 Poniższy zrzut ekranu pokazuje, jak renderuje w tym przykładzie.  
  
 ![Zrzut ekranu: Renderowany przykład zakresu](../../../../docs/framework/wpf/advanced/media/flow-spanexample.gif "Flow_SpanExample")  
  
 **InlineUIContainer**  
  
 <xref:System.Windows.Documents.InlineUIContainer> Umożliwia <xref:System.Windows.UIElement> elementy (tj., takich jak formantu <xref:System.Windows.Controls.Button>) do osadzenia w <xref:System.Windows.Documents.Inline> elementu zawartości. Ten element jest wbudowany odpowiednikiem <xref:System.Windows.Documents.BlockUIContainer> opisane powyżej. Poniżej znajduje się przykład używającej <xref:System.Windows.Documents.InlineUIContainer> do wstawienia <xref:System.Windows.Controls.Button> tekście <xref:System.Windows.Documents.Paragraph>.  
  
 [!code-xaml[FlowOvwSnippets_snip#InlineUIContainerExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/InlineUIContainerExample.xaml#inlineuicontainerexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/InlineUIContainerExample.cs#inlineuicontainercodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/InlineUIContainerExample.vb#inlineuicontainercodeonlyexamplewholepage)]  
  
 **Uwaga:** <xref:System.Windows.Documents.InlineUIContainer> nie trzeba używać jawnie w znaczniku. W przypadku jego pominięcia <xref:System.Windows.Documents.InlineUIContainer> zostanie utworzona mimo to podczas kompilowania kodu.  
  
 **Rysunek i Floater**  
  
 <xref:System.Windows.Documents.Figure> i <xref:System.Windows.Documents.Floater> służą do osadzania zawartości w dokumentach przepływ z właściwości umieszczania, które można dostosowywać niezależne od podstawowej przepływ zawartości. <xref:System.Windows.Documents.Figure> lub <xref:System.Windows.Documents.Floater> elementy są często używane wyróżniania lub akcentowania części zawartości do obsługi obrazów i innej zawartości w głównej przepływ zawartości, hosta lub iniekcję luźno powiązane zawartości, takie jak anonse.  
  
 Poniższy przykład przedstawia sposób osadzenia <xref:System.Windows.Documents.Figure> do tekstu akapitu.  
  
 [!code-xaml[FlowOvwSnippets_snip#FigureExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/FigureExample.xaml#figureexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/FigureExample.cs#figurecodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/FigureExample.vb#figurecodeonlyexamplewholepage)]  
  
 Na poniższej ilustracji przedstawiono sposób renderowania w tym przykładzie.  
  
 ![Zrzut ekranu: Przykład rysunek](../../../../docs/framework/wpf/advanced/media/flow-ovw-figure-example.png "Flow_Ovw_Figure_Example")  
  
 <xref:System.Windows.Documents.Figure> i <xref:System.Windows.Documents.Floater> różnią się na kilka sposobów i są używane w różnych scenariuszach.  
  
 **Rysunek:**  
  
-   Może być umieszczony: możesz ustawić jego poziome i pionowe kotwice celu względem strony, zawartość, kolumny lub akapitu. Można również użyć jego <xref:System.Windows.Documents.Figure.HorizontalOffset%2A> i <xref:System.Windows.Documents.Figure.VerticalOffset%2A> właściwości, aby określić dowolne przesunięcia.  
  
-   Może być zmieniany na więcej niż jedną kolumnę: możesz ustawić <xref:System.Windows.Documents.Figure> wysokości i szerokości wielokrotności strony, zawartości lub kolumny wysokość lub szerokość. Należy pamiętać, że w przypadku strony i zawartości wielokrotności większą niż 1 są niedozwolone. Na przykład można ustawić szerokość <xref:System.Windows.Documents.Figure> "0,5 page" lub "0,25 zawartość" lub "kolumna 2". Można również ustawić wysokość i szerokość wartości podane w pikselach.  
  
-   Nie z podziałem na strony: Jeśli zawartości wewnątrz <xref:System.Windows.Documents.Figure> nie mieści się w <xref:System.Windows.Documents.Figure>, będą zawierały, niezależnie od zawartość mieści się i pozostałej zawartości zostaną utracone  
  
 **Floater:**  
  
-   Nie może znajdować się i będzie renderować wszędzie tam, gdzie przestrzeni mogą być dostępne dla niego. Nie można ustawić przesunięcie lub zakotwiczenia <xref:System.Windows.Documents.Floater>.  
  
-   Nie może być ustalone na więcej niż jedną kolumnę: Domyślnie <xref:System.Windows.Documents.Floater> rozmiary w jednej kolumnie. Ma ona <xref:System.Windows.Documents.Floater.Width%2A> właściwość, którą można ustawić wartości podane w pikselach, ale jeśli ta wartość jest większa niż szerokość jednej kolumny jest ignorowany i floater jest o rozmiarze w jednej kolumnie. Rozmiar do mniej niż jednej kolumny ustawienie szerokości poprawne pikseli, ale zmiany rozmiaru nie jest względnego kolumny, więc "0.5Column" nie jest prawidłowym wyrażeniem dla <xref:System.Windows.Documents.Floater> szerokości. <xref:System.Windows.Documents.Floater> nie ma wysokość właściwości i jest wysokość nie może być ustawiona, jej wysokość zależy od zawartości  
  
-   <xref:System.Windows.Documents.Floater> identyczny: jeśli jego zawartość w określonej szerokości do wysokości kolumny więcej niż 1, floater przerywa i identyczny do następnej kolumnie następnej strony, itp.  
  
 <xref:System.Windows.Documents.Figure> jest dobrym miejscem do umieszczenia autonomiczny zawartości, której chcesz kontrolować rozmiar i położenie i pewność, że zawartość będzie mieści się w określonym rozmiarze. <xref:System.Windows.Documents.Floater> jest dobrym miejscem do umieszczenia więcej zawartości swobodnego przepływu podobne do zawartości strony głównej, ale jest oddzielony od niego.  
  
 **LineBreak**  
  
 <xref:System.Windows.Documents.LineBreak> powoduje, że podział wiersza w zawartości przepływu. W poniższym przykładzie pokazano użycie <xref:System.Windows.Documents.LineBreak>.  
  
 [!code-xaml[FlowOvwSnippets_snip#LineBreakExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/LineBreakExample.xaml#linebreakexamplewholepage)]  
  
 Poniższy zrzut ekranu pokazuje, jak renderuje w tym przykładzie.  
  
 ![Zrzut ekranu: Przykład LineBreak](../../../../docs/framework/wpf/advanced/media/flow-ovw-linebreakexample.png "Flow_Ovw_LineBreakExample")  
  
### <a name="flow-collection-elements"></a>Elementy kolekcji przepływu  
 W tych przykładach <xref:System.Windows.Documents.BlockCollection> i <xref:System.Windows.Documents.InlineCollection> są używane do skonstruowania zawartość śródwierszowa programowo. Na przykład, aby dodać elementy do <xref:System.Windows.Documents.Paragraph>, można użyć składni:  
  
 `…`  
  
 `myParagraph.Inlines.Add(new Run("Some text"));`  
  
 `…`  
  
 Spowoduje to dodanie <xref:System.Windows.Documents.Run> do <xref:System.Windows.Documents.InlineCollection> z <xref:System.Windows.Documents.Paragraph>.  Jest to taka sama jak niejawne <xref:System.Windows.Documents.Run> odnaleziono wewnątrz <xref:System.Windows.Documents.Paragraph> w znaczniku:  
  
 `…`  
  
 `<Paragraph>`  
  
 `Some Text`  
  
 `</Paragraph>`  
  
 `…`  
  
 Na przykład za pomocą <xref:System.Windows.Documents.BlockCollection>, poniższy przykład tworzy nowy <xref:System.Windows.Documents.Section> , a następnie używa **Dodaj** metodę, aby dodać nowy <xref:System.Windows.Documents.Paragraph> do <xref:System.Windows.Documents.Section> zawartość.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]  
  
 Oprócz Dodawanie elementów do kolekcji przepływu, należy usunąć również elementów.  Poniższy przykład powoduje usunięcie ostatniego <xref:System.Windows.Documents.Inline> element <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 Poniższy przykład Czyści całą zawartość (<xref:System.Windows.Documents.Inline> elementy) z <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
 Podczas pracy z dowolnej zawartości programowo, prawdopodobnie będzie zwiększone użycie tych kolekcji.  
  
 Określa, czy używa elementu przepływu <xref:System.Windows.Documents.InlineCollection> (Inlines) lub <xref:System.Windows.Documents.BlockCollection> (bloki), jego podrzędny zawiera elementy zależy od rodzaju elementy podrzędne (<xref:System.Windows.Documents.Block> lub <xref:System.Windows.Documents.Inline>) może być używany przez element nadrzędny. Zasady zawierania przepływać w schemacie zawartości w następnej sekcji przedstawiono podsumowanie elementów zawartości.  
  
 **Uwaga:** trzeci typ kolekcji używane z zawartością przepływu <xref:System.Windows.Documents.ListItemCollection>, ale ta kolekcja jest używana tylko z <xref:System.Windows.Documents.List>. Ponadto istnieje kilka kolekcje używane z <xref:System.Windows.Documents.Table>. Zobacz [omówienie tabeli](../../../../docs/framework/wpf/advanced/table-overview.md) Aby uzyskać więcej informacji.  
  
<a name="content_schema"></a>   
## <a name="content-schema"></a>Schemat zawartości  
 Podana liczba elementów zawartości innego przepływu, może być utrudnione do śledzenia jakiego typu element może zawierać elementy podrzędne. Na poniższym diagramie przedstawiono zasady zawierania elementy przepływu. Strzałki oznaczają relacji nadrzędny/podrzędny możliwe.  
  
 ![Diagram: Schemat zawartości zawierania przepływu](../../../../docs/framework/wpf/advanced/media/flow-content-schema.png "Flow_Content_Schema")  
  
 Jak wynika z powyższym diagramie, elementy podrzędne dozwolone dla elementu nie są zawsze określane przez czy jest <xref:System.Windows.Documents.Block> element lub <xref:System.Windows.Documents.Inline> elementu. Na przykład <xref:System.Windows.Documents.Span> ( <xref:System.Windows.Documents.Inline> element) może mieć tylko <xref:System.Windows.Documents.Inline> elementów podrzędnych podczas <xref:System.Windows.Documents.Figure> (również <xref:System.Windows.Documents.Inline> element) może mieć tylko <xref:System.Windows.Documents.Block> elementy podrzędne. W związku z tym diagramie przydaje się szybko określania, jakie elementu mogą być zawarte w innym. Na przykład użyjmy diagramu do określenia sposobu konstruowania zawartości przepływ <xref:System.Windows.Controls.RichTextBox>.  
  
 **1.** A <xref:System.Windows.Controls.RichTextBox> musi zawierać <xref:System.Windows.Documents.FlowDocument> który z kolei musi zawierać <xref:System.Windows.Documents.Block>-pochodzi z obiektu. Poniżej znajdują się odpowiednie segmentu z powyższym diagramie.  
  
 ![Diagram: Obiektu RichTextBox](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
 To jest dotychczasowych, jak może wyglądać znaczników.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
 **2.** Zgodnie z diagramu, dostępnych jest kilka <xref:System.Windows.Documents.Block> elementów do wyboru w tym <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.List>, i <xref:System.Windows.Documents.BlockUIContainer> (zobacz powyżej klas pochodnych bloku). Załóżmy, że chcemy <xref:System.Windows.Documents.Table>. Zgodnie z powyższym diagramie <xref:System.Windows.Documents.Table> zawiera <xref:System.Windows.Documents.TableRowGroup> zawierający <xref:System.Windows.Documents.TableRow> elementów, które zawierają <xref:System.Windows.Documents.TableCell> elementy, które zawierają <xref:System.Windows.Documents.Block>-pochodzi z obiektu. Poniżej znajduje się o odpowiadającym segmencie dla <xref:System.Windows.Documents.Table> pobranych z powyższym diagramie.  
  
 ![Diagram: Nadrzędnego&#47;schemat tabeli podrzędnej](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
 Poniżej znajduje się odpowiedni kod znaczników.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
 **3.** Ponownie co najmniej jeden <xref:System.Windows.Documents.Block> elementy są wymagane poniżej <xref:System.Windows.Documents.TableCell>. Aby był prosty, możemy umieścić tekst wewnątrz komórki. Firma Microsoft może to zrobić za pomocą <xref:System.Windows.Documents.Paragraph> z <xref:System.Windows.Documents.Run> elementu. Poniżej znajdują się odpowiednie segmentów z diagram przedstawiający <xref:System.Windows.Documents.Paragraph> może zająć <xref:System.Windows.Documents.Inline> elementu oraz że <xref:System.Windows.Documents.Run> ( <xref:System.Windows.Documents.Inline> element) przyjmuje tylko zwykły tekst.  
  
 ![Diagram: Nadrzędnego&#47;schematu podrzędnych akapitu](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
 ![Diagram: Nadrzędnego&#47;podrzędnych schematu dla przebiegu](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 Poniżej znajduje się cały przykładowy w znaczniku.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="customizing_text"></a>   
## <a name="customizing-text"></a>Dostosowywanie tekstu  
 Tekst jest zwykle najbardziej rozpowszechnionych typu zawartości w dokumencie przepływu. Mimo że obiekty wprowadzonych powyżej może służyć do kontrolowania większością aspektów sposób renderowania tekstu, istnieją inne metody dostosowywania tekst, który został omówiony w tej sekcji.  
  
### <a name="text-decorations"></a>Dekoracji tekstu  
 Dekoracji tekstu pozwalają na stosowanie efektów podkreślenia, nadkreślenia linii bazowej i przekreślenia do tekstu (zobacz poniżej obrazy). Dekoracje te są dodawane przy użyciu <xref:System.Windows.Documents.Inline.TextDecorations%2A> właściwość, która jest udostępniana przez liczbę obiektów w tym <xref:System.Windows.Documents.Inline>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Controls.TextBlock>, i <xref:System.Windows.Controls.TextBox>.  
  
 Poniższy przykład przedstawia sposób ustawiania <xref:System.Windows.Documents.Paragraph.TextDecorations%2A> właściwość <xref:System.Windows.Documents.Paragraph>.  
  
 [!code-xaml[InlineSnippets#_Paragraph_TextDecXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml#_paragraph_textdecxaml)]  
  
 [!code-csharp[InlineSnippets#_Paragraph_TextDec](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml.cs#_paragraph_textdec)]
 [!code-vb[InlineSnippets#_Paragraph_TextDec](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InlineSnippets/visualbasic/window1.xaml.vb#_paragraph_textdec)]  
  
 Na poniższej ilustracji przedstawiono sposób renderowania w tym przykładzie.  
  
 ![Zrzut ekranu: Tekst z efektem przekreślenia domyślne](../../../../docs/framework/wpf/advanced/media/inline-textdec-strike.png "Inline_TextDec_Strike")  
  
 Pokaż danych liczbowych następujące jak **Nadkreślenia**, **linii bazowej**, i **Underline** odpowiednio dekoracje renderowania.  
  
 ![Zrzut ekranu: Nadkreślenie TextDecorator](../../../../docs/framework/wpf/advanced/media/inline-textdec-over.png "Inline_TextDec_Over")  
  
 ![Zrzut ekranu: Domyślna efekt linii bazowej w tekście](../../../../docs/framework/wpf/advanced/media/inline-textdec-base.png "Inline_TextDec_Base")  
  
 ![Zrzut ekranu: Tekst z domyślnym efektem podkreślenia](../../../../docs/framework/wpf/advanced/media/inline-textdec-under.png "Inline_TextDec_Under")  
  
### <a name="typography"></a>Typografia  
 <xref:System.Windows.Documents.TextElement.Typography%2A> Właściwość jest udostępniana przez większość związane z przepływem zawartości w tym <xref:System.Windows.Documents.TextElement>, <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Controls.TextBlock>, i <xref:System.Windows.Controls.TextBox>. Ta właściwość jest używana do sterowania typograficzne wahania cechy tekstu (tj. minimalny i maksymalny CAP, tworzenie indeksu górnego i dolnego itp).  
  
 Poniższy przykład przedstawia sposób ustawiania <xref:System.Windows.Documents.TextElement.Typography%2A> atrybutu przy użyciu <xref:System.Windows.Documents.Paragraph> jako element przykład.  
  
 [!code-xaml[TextElementSnippets#_TextElement_TypogXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 Na poniższej ilustracji przedstawiono sposób renderowania w tym przykładzie.  
  
 ![Zrzut ekranu: Tekst z zmieniony typografii](../../../../docs/framework/wpf/advanced/media/textelement-typog.png "TextElement_Typog")  
  
 Z kolei na poniższej ilustracji przedstawiono, jak renderuje podobny przykład związane z typografią właściwości domyślnej.  
  
 ![Zrzut ekranu: Tekst z zmieniony typografii](../../../../docs/framework/wpf/advanced/media/textelement-typog-default.png "TextElement_Typog_Default")  
  
 Poniższy przykład przedstawia sposób ustawiania <xref:System.Windows.Controls.TextBox.Typography%2A> właściwości programowo.  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
 Zobacz [typografii na platformie WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md) Aby uzyskać więcej informacji na temat typografii.  
  
## <a name="see-also"></a>Zobacz też  
 [Tekst](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Typografia w WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/advanced/flow-content-elements-how-to-topics.md)  
 [Przegląd modelu zawartości TextElement](../../../../docs/framework/wpf/advanced/textelement-content-model-overview.md)  
 [RichTextBox — omówienie](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [Dokumenty w WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Przegląd tabeli](../../../../docs/framework/wpf/advanced/table-overview.md)  
 [Przegląd adnotacji](../../../../docs/framework/wpf/advanced/annotations-overview.md)
