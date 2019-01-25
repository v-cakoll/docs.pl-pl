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
ms.openlocfilehash: 34bab81f10b52829558e9a44c6bd4e1ed6c0fdbe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648511"
---
# <a name="flow-document-overview"></a>Przegląd Dokument przepływu
Dokumenty przepływu są przeznaczone do optymalizacji wyświetlania i czytelności. Zamiast jest ustawiona na jeden układ wstępnie zdefiniowanych, dokumenty przepływu dynamicznie Dostosuj i przepełnieniem ich zawartości na podstawie zmiennych czasu wykonywania, takich jak rozmiar okna, rozdzielczość urządzenia i preferencje użytkownika opcjonalne. Ponadto dokumenty przepływu oferują funkcje zaawansowane dokumentu, takie jak podział na strony i kolumn. Ten temat zawiera omówienie dokumenty przepływu i jak je utworzyć.  
  

  
<a name="what_is_a_flow_document"></a>   
## <a name="what-is-a-flow-document"></a>Co to jest dokument usługi Flow  
 Dokument przepływu jest przeznaczony do "ze zmianą ułożenia zawartości" w zależności od rozmiaru okna, rozdzielczość urządzenia i inne zmienne środowiskowe. Ponadto dokumenty przepływu ma szereg wbudowanych funkcji, w tym wyszukiwanie, wyświetlanie trybów, które optymalizują czytelności i możliwości zmiany rozmiaru i wygląd czcionek. Dokumenty przepływu są wykorzystywane najlepiej, gdy czytelnej jest scenariusz użycia dokumentu głównego. Z kolei Naprawiono dokumenty mają mieć statyczne prezentacji. Naprawiono dokumenty są przydatne, gdy wierności zawartość źródłowa jest niezbędne. Zobacz [dokumenty w WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md) Aby uzyskać więcej informacji na temat różnych typów dokumentów.  
  
 Poniższa ilustracja przedstawia przykładowy dokument przepływu wyświetlany w kilka okien o różnych rozmiarach. Zmian obszaru wyświetlania zawartości przepłynie najlepszego wykorzystania dostępnego miejsca.  
  
 ![Przepływ zawartości przepełnieniem dokumentu](../../../../docs/framework/wpf/advanced/media/edocs-flowdocument.png "eDocs_FlowDocument")  
  
 Jak widać na ilustracji powyżej, zawartość może zawierać wiele składników, w tym akapitów, list, obrazów i innych. Te składniki odnoszą się do elementów w znacznikach i obiektów w kodzie proceduralnym. Firma Microsoft będzie przechodzi przez te klasy szczegółowo później w [przepływu powiązanymi klasami](#flow_related_classes) części w tym omówieniu. Teraz poniżej przedstawiono prosty przykład kodu, który tworzy dokument przepływu składający się z akapit jakiś tekst pogrubiony i listy.
  
 [!code-xaml[FlowOvwSnippets_snip#SimpleFlowExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SimpleFlowExample.xaml#simpleflowexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SimpleFlowExample.cs#simpleflowcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SimpleFlowExample.vb#simpleflowcodeonlyexamplewholepage)]  
  
 Na poniższej ilustracji przedstawiono, jak wygląda ten fragment kodu.  
  
 ![Zrzut ekranu: Renderowany przykład FlowDocument](../../../../docs/framework/wpf/advanced/media/flow-ovw-first-example.png "Flow_Ovw_First_Example")  
  
 W tym przykładzie <xref:System.Windows.Controls.FlowDocumentReader> formant jest używany do hostowania zawartości przepływu. Zobacz [typów dokumentów przepływ](#flow_document_types) więcej informacji na temat zawartości przepływu hosting kontrolek. <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, i <xref:System.Windows.Documents.Bold> elementy są używane do kontrolowania, formatowanie zawartości na podstawie ich kolejności, w znacznikach. Na przykład <xref:System.Windows.Documents.Bold> element obejmuje WE tylko część tekstu w akapicie; w wyniku tego część tekstu jest pogrubiony. Jeśli używano HTML są to znane.  
  
 Jak podkreślono na ilustracji powyżej istnieje kilka funkcji wbudowanych w dokumentach przepływu:
  
-   Wyszukiwanie: Zezwala użytkownikowi na wyszukiwanie pełnotekstowe całego dokumentu.  
  
-   Tryb wyświetlania: Użytkownik może wybrać tryb wyświetlanego w tym trybie jednej strony, przeglądania (strona na a-time), dwie strony na pojedynczych (w formacie czytania książki) wyświetlanie trybu i trybie przewijania ciągłego wyświetlania (nieograniczony).  Aby uzyskać więcej informacji dotyczących tych trybów wyświetlania, zobacz <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>.  
  
-   Formanty nawigacji na stronie: Jeśli tryb wyświetlania dokumentu używa stron, formanty nawigacji na stronie obejmują przycisk, aby przejść do następnej strony (strzałkę w dół) lub poprzedniej strony (strzałkę w górę), a także wskaźniki numer bieżącej strony i łączna liczba stron. Przerzucanie kolejnych stron może być również wykonywane za pomocą klawiszy strzałek.  
  
-   Powiększenie: Kontrolki powiększenia Włącz użytkownika zwiększyć lub zmniejszyć poziom powiększenia, klikając znak plus lub minus przyciski, odpowiednio. Kontrolki powiększenia także suwaka dostosowania poziomu powiększenia. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Controls.FlowDocumentReader.Zoom%2A>.  
  
 Te funkcje mogą być modyfikowane na podstawie kontroli używane do hostowania zawartości przepływu. W następnej sekcji opisano różne formanty.  
  
<a name="flow_document_types"></a>   
## <a name="flow-document-types"></a>Typy dokumentów przepływu  
 Wyświetlanie zawartości dokumentu przepływu i sposób ich wyświetlania jest zależne od tego, jak obiekt jest używany do hostowania zawartości przepływu. Istnieją cztery formanty, które obsługują wyświetlanie zawartości przepływu: <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.RichTextBox>, i <xref:System.Windows.Controls.FlowDocumentScrollViewer>. Te kontrolki krótko opisano poniżej.  
  
 **Uwaga:** <xref:System.Windows.Documents.FlowDocument> jest wymagany do bezpośrednio zawartości przepływu hosta, więc wszystkie te formanty wyświetlania używanie <xref:System.Windows.Documents.FlowDocument> umożliwiające hosting zawartości przepływu.  
  
### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader> zawiera funkcje, które umożliwiają użytkownikowi dynamicznie do wyboru różnych trybów wyświetlania, w tym trybie jednej strony, przeglądania (strona na a-time), dwie strony na pojedynczych (w formacie czytania książki) wyświetlanie trybu i trybie przewijania ciągłego wyświetlania (nieograniczony). Aby uzyskać więcej informacji dotyczących tych trybów wyświetlania, zobacz <xref:System.Windows.Controls.FlowDocumentReaderViewingMode>. Jeśli nie potrzebujesz możliwości dynamicznie przełączać się między trybami wyświetlania różnych <xref:System.Windows.Controls.FlowDocumentPageViewer> i <xref:System.Windows.Controls.FlowDocumentScrollViewer> zapewniają podglądy zawartości, które zostały usunięte w trybie przeglądania określonego przepływu lekki.  
  
### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer and FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer> przedstawia zawartość strony w czasie trybu wyświetlania, podczas gdy <xref:System.Windows.Controls.FlowDocumentScrollViewer> pokazuje zawartości w trybie przewijania ciągłego. Zarówno <xref:System.Windows.Controls.FlowDocumentPageViewer> i <xref:System.Windows.Controls.FlowDocumentScrollViewer> są rozwiązywane do trybu wyświetlania określonego. Porównaj <xref:System.Windows.Controls.FlowDocumentReader>, która obejmuje funkcje, które umożliwiają użytkownikowi dynamicznie do wyboru różnych trybów wyświetlania (zgodnie z informacjami od <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> wyliczenie), kosztem trwa więcej zasobów niż <xref:System.Windows.Controls.FlowDocumentPageViewer> lub <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 Domyślnie pionowy pasek przewijania jest zawsze wyświetlany, i poziomy pasek przewijania staje się widoczny, jeśli to konieczne. Wartość domyślna dla interfejsu użytkownika <xref:System.Windows.Controls.FlowDocumentScrollViewer> nie obejmuje paska narzędzi & lt; jednak <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> właściwość może służyć do włączyć pasek narzędzi.  
  
### <a name="richtextbox"></a>RichTextBox  
 Możesz użyć <xref:System.Windows.Controls.RichTextBox> kiedy chcesz umożliwić użytkownikowi edytować zawartość usługi flow. Na przykład, jeśli chcesz utworzyć Edytor który może użytkownika do manipulowania rzeczy, takich jak tabele, kursywa i bold formatowanie itp, należy użyć <xref:System.Windows.Controls.RichTextBox>. Zobacz [RichTextBox — Przegląd](../../../../docs/framework/wpf/controls/richtextbox-overview.md) Aby uzyskać więcej informacji.  
  
 **Uwaga:** Przepływ zawartości wewnątrz <xref:System.Windows.Controls.RichTextBox> nie zachowuje się tak samo jak dowolnej zawartości znajdujących się w innych kontrolek. Na przykład istnieją Brak kolumn w <xref:System.Windows.Controls.RichTextBox> i dlatego nie automatyczne zmienianie rozmiaru zachowanie. Ponadto, zazwyczaj wbudowane funkcje zawartość przepływu, taką jak wyszukiwanie, wyświetlanie trybu, nawigowania po stronach i powiększenia nie są dostępne w ramach <xref:System.Windows.Controls.RichTextBox>.  
  
<a name="creating_flow_content"></a>   
## <a name="creating-flow-content"></a>Tworzenie zawartości przepływu  
 Zawartość przepływu, może być skomplikowane, składający się z różnych elementów, w tym tekst, obrazy, tabele, a nawet <xref:System.Windows.UIElement> klasy, takie jak formanty pochodne. Aby zrozumieć sposób tworzenia złożonych dowolnej zawartości, krytyczne są następujące kwestie:  
  
-   **Klasy związane z przepływem**: Każda klasa używana w dowolnej zawartości ma określonego celu. Ponadto hierarchicznych relacji między klasami przepływ pomaga zrozumieć, jak są one używane. Na przykład klasy pochodne <xref:System.Windows.Documents.Block> klasy są używane do zawierać inne obiekty, gdy klasy pochodne <xref:System.Windows.Documents.Inline> zawierają obiekty, które są wyświetlane.  
  
-   **Zawartość schematu**: Dokument przepływu może wymagać dużej liczby elementów zagnieżdżonych. Schemat zawartości określa relacje nadrzędne/podrzędne możliwe między elementami.  
  
 Poniższe sekcje zaczną się nad każdym z tych obszarów, które bardziej szczegółowo.  
  
<a name="flow_related_classes"></a>   
## <a name="flow-related-classes"></a>Przepływ powiązanymi klasami  
 Na poniższym diagramie przedstawiono obiekty najczęściej używane z zawartości przepływu:  
  
 ![Diagram: Hierarchia klas elementów zawartości przepływu](../../../../docs/framework/wpf/advanced/media/flow-class-hierarchy.png "Flow_Class_Hierarchy")  
  
 Do celów zawartość przepływu istnieją dwie ważne kategorie:  
  
1.  **Klasy pochodne bloku**: Skrót "Elementów zawartości bloku" lub po prostu bloku elementów"". Elementy, które dziedziczą z <xref:System.Windows.Documents.Block> może służyć do grupowania elementów do wspólnego elementu nadrzędnego lub można zastosować atrybuty wspólne do grupy.  
  
2.  **Klasy pochodne wbudowane**: Skrót "Zawartości elementów śródwierszowych" lub po prostu "elementów śródwierszowych". Elementy, które dziedziczą z <xref:System.Windows.Documents.Inline> są albo zawarte w elemencie bloku lub innego wbudowanego elementu. Elementy wbudowane są często używane jako bezpośrednie kontener zawartości, który jest renderowany na ekranie. Na przykład <xref:System.Windows.Documents.Paragraph> (Blokuj) może zawierać <xref:System.Windows.Documents.Run> (wbudowanego elementu), ale <xref:System.Windows.Documents.Run> faktycznie zawiera tekst, który jest renderowany na ekranie.  
  
 Każda klasa w tych dwóch kategorii krótko opisano poniżej.  
  
### <a name="block-derived-classes"></a>Klasy pochodne bloku  
 **Akapitu**  
  
 <xref:System.Windows.Documents.Paragraph> Zazwyczaj służy do zawartości grupy do akapitu. Najprostszy i najbardziej powszechnym akapitu polega na utworzeniu akapit tekstu.  
  
 [!code-xaml[FlowOvwSnippets_snip#ParagraphExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ParagraphExample.xaml#paragraphexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ParagraphExample.cs#paragraphcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ParagraphExample.vb#paragraphcodeonlyexamplewholepage)]  
  
 Również może jednak zawierać innych elementów pochodnych wbudowane, jak widać poniżej. 
  
 **Sekcja**  
  
 <xref:System.Windows.Documents.Section> Umożliwia tylko zawierać inne <xref:System.Windows.Documents.Block>-elementów pochodnych. Formatowanie elementów, które zawiera wszystkie domyślne nie ma zastosowania. Jednak wartości wszystkich właściwości zestawu na <xref:System.Windows.Documents.Section> ma zastosowanie do jego elementów podrzędnych. Sekcja umożliwia także programowo wykonać iterację jego kolekcja potomna. <xref:System.Windows.Documents.Section> jest używana w sposób podobny do \<DIV > tag HTML.  
  
 W poniższym przykładzie zdefiniowano następujących trzech akapitach znajdujące się pod jednym <xref:System.Windows.Documents.Section>. Sekcja zawiera <xref:System.Windows.Documents.TextElement.Background%2A> czerwony, w związku z tym kolor tła akapitów wartość właściwości jest również czerwony.  
  
 [!code-xaml[FlowOvwSnippets_snip#SectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SectionExample.xaml#sectionexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SectionExample.cs#sectioncodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SectionExample.vb#sectioncodeonlyexamplewholepage)]  
  
 **BlockUIContainer**  
  
 <xref:System.Windows.Documents.BlockUIContainer> Włącza <xref:System.Windows.UIElement> elementów (czyli <xref:System.Windows.Controls.Button>) można osadzać w dowolnej klasy pochodnej bloku zawartości. <xref:System.Windows.Documents.InlineUIContainer> (patrz poniżej) służy do osadzania <xref:System.Windows.UIElement> elementów zawartości przepływu pochodzące z wbudowanego. <xref:System.Windows.Documents.BlockUIContainer> i <xref:System.Windows.Documents.InlineUIContainer> są ważne, ponieważ nie ma innego sposobu używania <xref:System.Windows.UIElement> w dowolnej zawartości, chyba że znajduje się w jednej z tych dwóch elementach.  
  
 Poniższy przykład pokazuje, jak używać <xref:System.Windows.Documents.BlockUIContainer> elementu hosta <xref:System.Windows.UIElement> obiektów w ramach dowolnej zawartości.  
  
 [!code-xaml[SpanSnippets#_BlockUIXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml#_blockuixaml)]  
  
 Na poniższej ilustracji przedstawiono, jak powoduje wyświetlenie w tym przykładzie.  
  
 ![Zrzut ekranu: UIElement osadzony w zawartości przepływu](../../../../docs/framework/wpf/advanced/media/blockuicontainer.png "BlockUIContainer")  
  
 **Lista**  
  
 <xref:System.Windows.Documents.List> Służy do tworzenia listy punktowanej lub liczbowe. Ustaw <xref:System.Windows.Documents.List.MarkerStyle%2A> właściwości <xref:System.Windows.TextMarkerStyle> wartości wyliczenia, aby określić styl listy. W poniższym przykładzie pokazano sposób tworzenia prostej listy.  
  
 [!code-xaml[FlowOvwSnippets_snip#ListExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ListExample.xaml#listexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ListExample.cs#listcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ListExample.vb#listcodeonlyexamplewholepage)]  
  
 **Uwaga:** <xref:System.Windows.Documents.List> jest jedynym elementem przepływ, który używa <xref:System.Windows.Documents.ListItemCollection> do zarządzania elementami podrzędnymi.  
  
 **Tabela**  
  
 <xref:System.Windows.Documents.Table> Służy do tworzenia tabeli. <xref:System.Windows.Documents.Table> jest podobny do <xref:System.Windows.Controls.Grid> elementu, ale ma więcej możliwości i dlatego wymagają większe obciążenie zasobów. Ponieważ <xref:System.Windows.Controls.Grid> jest <xref:System.Windows.UIElement>, chyba że znajduje się w nie można używać w dowolnej zawartości <xref:System.Windows.Documents.BlockUIContainer> lub <xref:System.Windows.Documents.InlineUIContainer>. Aby uzyskać więcej informacji na temat <xref:System.Windows.Documents.Table>, zobacz [Omówienie tabel](../../../../docs/framework/wpf/advanced/table-overview.md).  
  
### <a name="inline-derived-classes"></a>Klasy pochodne w tekście  
 **Uruchom**  
  
 <xref:System.Windows.Documents.Run> Służy do zawierają niesformatowanego tekstu. Można by oczekiwać <xref:System.Windows.Documents.Run> obiektów, które ma być używany często w przepływu zawartości. Jednak w znaczniku <xref:System.Windows.Documents.Run> elementy nie są wymagane do użycia w sposób jawny. <xref:System.Windows.Documents.Run> jest wymagany do użycia podczas tworzenia i manipulowania dokumenty przepływu przy użyciu kodu. Na przykład w znaczniku poniżej pierwszej <xref:System.Windows.Documents.Paragraph> Określa <xref:System.Windows.Documents.Run> nie zawiera elementu jawnie, podczas gdy drugi. Oba punkty generują identyczne dane wyjściowe.  
  
 [!code-xaml[FlowOvwSnippets_snip#RunExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/RunSnippetsExample.xaml#runexample1)]  
  
 **Uwaga:**  Począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], <xref:System.Windows.Documents.Run.Text%2A> właściwość <xref:System.Windows.Documents.Run> obiekt jest właściwość zależności. Możesz powiązać <xref:System.Windows.Documents.Run.Text%2A> właściwości do danych źródłowych, takich jak <xref:System.Windows.Controls.TextBlock>. <xref:System.Windows.Documents.Run.Text%2A> Właściwość w pełni obsługuje powiązania jednokierunkowe. <xref:System.Windows.Documents.Run.Text%2A> Właściwość obsługuje także określają powiązanie dwukierunkowe, z wyjątkiem <xref:System.Windows.Controls.RichTextBox>. Aby uzyskać przykład, zobacz <xref:System.Windows.Documents.Run.Text%2A?displayProperty=nameWithType>.  
  
 **zakres**  
  
 <xref:System.Windows.Documents.Span> Grupuje elementy zawartości innych wbudowanych. Nie nieprzerwaną pracę renderowania są stosowane do zawartości w ramach <xref:System.Windows.Documents.Span> elementu. Jednak elementy, dziedziczyć <xref:System.Windows.Documents.Span> tym <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Italic> i <xref:System.Windows.Documents.Underline> formatowania tekstu.  
  
 Poniżej znajduje się przykład <xref:System.Windows.Documents.Span> używanej do mają wbudowane zawartość, łącznie z tekstem, <xref:System.Windows.Documents.Bold> elementu, a <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[FlowOvwSnippets_snip#SpanExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SpanExample.xaml#spanexamplewholepage)]  
  
 Poniższy zrzut ekranu pokazuje, jak powoduje wyświetlenie w tym przykładzie.  
  
 ![Zrzut ekranu: Renderowany przykład zakresu](../../../../docs/framework/wpf/advanced/media/flow-spanexample.gif "Flow_SpanExample")  
  
 **InlineUIContainer**  
  
 <xref:System.Windows.Documents.InlineUIContainer> Włącza <xref:System.Windows.UIElement> elementów (czyli kontrolki, takie jak <xref:System.Windows.Controls.Button>) do osadzenia w <xref:System.Windows.Documents.Inline> elementu zawartości. Ten element jest odpowiednikiem wbudowane <xref:System.Windows.Documents.BlockUIContainer> opisanych powyżej. Poniżej znajduje się przykład, który używa <xref:System.Windows.Documents.InlineUIContainer> do wstawienia <xref:System.Windows.Controls.Button> bezpośrednio w <xref:System.Windows.Documents.Paragraph>.  
  
 [!code-xaml[FlowOvwSnippets_snip#InlineUIContainerExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/InlineUIContainerExample.xaml#inlineuicontainerexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/InlineUIContainerExample.cs#inlineuicontainercodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/InlineUIContainerExample.vb#inlineuicontainercodeonlyexamplewholepage)]  
  
 **Uwaga:** <xref:System.Windows.Documents.InlineUIContainer> nie trzeba jawnie służyć w znacznikach. Jeśli parametr zostanie pominięty, <xref:System.Windows.Documents.InlineUIContainer> zostaną utworzone, mimo to gdy kod jest kompilowany.  
  
 **Ilustracja i Floater**  
  
 <xref:System.Windows.Documents.Figure> i <xref:System.Windows.Documents.Floater> są używane do osadzania zawartości w dokumentach przepływu za pomocą właściwości umieszczania, które można dostosować niezależnie od głównej przepływ zawartości. <xref:System.Windows.Documents.Figure> lub <xref:System.Windows.Documents.Floater> elementy są często używane do wyróżniania lub akcentowania części zawartości do obsługi obrazów i innej zawartości w obrębie głównego przepływu zawartości, hosta lub iniekcję luźno powiązanych zawartości, takie jak anonse.  
  
 Poniższy przykład pokazuje sposób osadzenia <xref:System.Windows.Documents.Figure> do tekstu akapitu.  
  
 [!code-xaml[FlowOvwSnippets_snip#FigureExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/FigureExample.xaml#figureexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/FigureExample.cs#figurecodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/FigureExample.vb#figurecodeonlyexamplewholepage)]  
  
 Poniższa ilustracja przedstawia, jak powoduje wyświetlenie w tym przykładzie.  
  
 ![Zrzut ekranu: Przykład rysunek](../../../../docs/framework/wpf/advanced/media/flow-ovw-figure-example.png "Flow_Ovw_Figure_Example")  
  
 <xref:System.Windows.Documents.Figure> i <xref:System.Windows.Documents.Floater> różnią się na kilka sposobów i są używane w różnych scenariuszach.  
  
 **Rysunek:**  
  
-   Może zostać umieszczony: Można ustawić jego poziome i pionowe kotwic go zadokować względem strony, zawartość, kolumny lub akapitu. Można również użyć jego <xref:System.Windows.Documents.Figure.HorizontalOffset%2A> i <xref:System.Windows.Documents.Figure.VerticalOffset%2A> właściwości, aby określić dowolne przesunięcia.  
  
-   To może być zmieniany do więcej niż jednej kolumny: Możesz ustawić <xref:System.Windows.Documents.Figure> wysokością i szerokością wielokrotności strony, szerokość lub wysokość zawartości lub kolumny. Należy pamiętać, że w przypadku strony i zawartości wielokrotności większą niż 1 nie są dozwolone. Na przykład można ustawić szerokość <xref:System.Windows.Documents.Figure> "0,5 page" lub "0,25 treści" lub "2 kolumnę". Można również ustawić szerokość i wysokość, do wartości podane w pikselach.  
  
-   Nie podzielony na strony: Jeśli zawartość wewnątrz <xref:System.Windows.Documents.Figure> nie mieści się wewnątrz <xref:System.Windows.Documents.Figure>, renderowanie zostanie przeprowadzone dowolną zawartość mieści się, jak i pozostałej zawartości zostaną utracone  
  
 **Floater:**  
  
-   Nie może znajdować się i będzie renderowany wszędzie tam, gdzie miejsca mogą być dostępne dla niego. Nie można ustawić przesunięcie lub kotwicy <xref:System.Windows.Documents.Floater>.  
  
-   Nie może zostać zwiększony do więcej niż jednej kolumny: Domyślnie <xref:System.Windows.Documents.Floater> rozmiary w jedną kolumnę. Ma ona <xref:System.Windows.Documents.Floater.Width%2A> właściwość, która może być ustawiona na wartość bezwzględna pikseli, ale jeśli ta wartość jest większa niż szerokość jedną kolumnę, jest ignorowany i floater ma rozmiar w jedną kolumnę. Rozmiarze mniejszym niż jedna kolumnę, ustawiając szerokość piksela poprawne, ale zmiany rozmiaru nie jest kolumny powiązane z wątkiem, dlatego "0.5Column" nie jest prawidłowym wyrażeniem dla <xref:System.Windows.Documents.Floater> szerokości. <xref:System.Windows.Documents.Floater> nie ma wysokość właściwości i jest wysokość nie może być ustawiona, jego wysokość jest zależna od zawartości  
  
-   <xref:System.Windows.Documents.Floater> identyczny: Jeśli jej zawartość w jego określona szerokość rozciąga się do więcej niż 1 wysokości kolumny, floater przerywa i identyczny z następnej kolumnie, Następna strona itp.  
  
 <xref:System.Windows.Documents.Figure> jest dobrym miejscem do umieszczenia zawartości autonomiczny potrzebne do kontrolowania rozmiaru i pozycjonowania i pewność, że zawartość zmieści się w określonym rozmiarem. <xref:System.Windows.Documents.Floater> jest dobrym miejscem, aby umieścić więcej zawartości wolny przepływający przepływy podobne do zawartości strony głównej, ale jest oddzielony od niego.  
  
 **LineBreak**  
  
 <xref:System.Windows.Documents.LineBreak> powoduje, że podział wiersza w zawartości przepływu. W poniższym przykładzie pokazano użycie <xref:System.Windows.Documents.LineBreak>.  
  
 [!code-xaml[FlowOvwSnippets_snip#LineBreakExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/LineBreakExample.xaml#linebreakexamplewholepage)]  
  
 Poniższy zrzut ekranu pokazuje, jak powoduje wyświetlenie w tym przykładzie.  
  
 ![Zrzut ekranu: Przykład LineBreak](../../../../docs/framework/wpf/advanced/media/flow-ovw-linebreakexample.png "Flow_Ovw_LineBreakExample")  
  
### <a name="flow-collection-elements"></a>Elementy kolekcji przepływu  
 W wielu przykładach <xref:System.Windows.Documents.BlockCollection> i <xref:System.Windows.Documents.InlineCollection> są używane do konstruowania zawartości przepływu programowo. Na przykład, aby dodać elementy do <xref:System.Windows.Documents.Paragraph>, można użyć składni:  
  
 `…`  
  
 `myParagraph.Inlines.Add(new Run("Some text"));`  
  
 `…`  
  
 Spowoduje to dodanie <xref:System.Windows.Documents.Run> do <xref:System.Windows.Documents.InlineCollection> z <xref:System.Windows.Documents.Paragraph>.  Jest to taka sama jak niejawny <xref:System.Windows.Documents.Run> odnaleziono <xref:System.Windows.Documents.Paragraph> w znacznikach:  
  
 `…`  
  
 `<Paragraph>`  
  
 `Some Text`  
  
 `</Paragraph>`  
  
 `…`  
  
 Na przykład za pomocą <xref:System.Windows.Documents.BlockCollection>, poniższy przykład tworzy nowy <xref:System.Windows.Documents.Section> , a następnie używa **Dodaj** metodę, aby dodać nowy <xref:System.Windows.Documents.Paragraph> do <xref:System.Windows.Documents.Section> zawartość.  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]  
  
 Oprócz dodawania elementów do kolekcji przepływu, możesz usunąć elementy, jak również.  Poniższy przykład usuwa ostatni <xref:System.Windows.Documents.Inline> element <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 Poniższy przykład Czyści całą zawartość (<xref:System.Windows.Documents.Inline> elementy) z <xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
 Podczas pracy z zawartości przepływu programowo, prawdopodobnie spowoduje zwiększone użycie tych kolekcji.  
  
 Czy używa elementu przepływu <xref:System.Windows.Documents.InlineCollection> (Inlines) lub <xref:System.Windows.Documents.BlockCollection> (bloki), jego podrzędny zawiera elementy zależy od rodzaju elementy podrzędne (<xref:System.Windows.Documents.Block> lub <xref:System.Windows.Documents.Inline>) mogą być zawarte przez nadrzędne. Zasady zawierania przepływu zawartości, że elementy są podsumowywane w schemacie zawartości w następnej sekcji.  
  
 **Uwaga:** Trzeci typ kolekcji używane z zawartości przepływu <xref:System.Windows.Documents.ListItemCollection>, ale ta kolekcja jest używana tylko z <xref:System.Windows.Documents.List>. Ponadto, istnieje kilka kolekcje używane z <xref:System.Windows.Documents.Table>. Zobacz [Omówienie tabel](../../../../docs/framework/wpf/advanced/table-overview.md) Aby uzyskać więcej informacji.  
  
<a name="content_schema"></a>   
## <a name="content-schema"></a>Schemat zawartości  
 Biorąc pod uwagę liczbę różnych przepływem elementów zawartości, może być trudne do śledzenia jakiego rodzaju elementy podrzędne mogą zawierać elementu. Na poniższym diagramie przedstawiono podsumowanie zasad zawierania przepływem elementów. Strzałki reprezentuje relacje nadrzędne/podrzędne możliwe.  
  
 ![Diagram: Przepływ zawartości zawierania schematu](../../../../docs/framework/wpf/advanced/media/flow-content-schema.png "Flow_Content_Schema")  
  
 Jak widać w powyższym diagramie, elementy podrzędne dozwolone dla elementu nie zawsze zależą od tego, czy jest <xref:System.Windows.Documents.Block> element lub <xref:System.Windows.Documents.Inline> elementu. Na przykład <xref:System.Windows.Documents.Span> ( <xref:System.Windows.Documents.Inline> elementu) może mieć tylko <xref:System.Windows.Documents.Inline> elementów podrzędnych podczas <xref:System.Windows.Documents.Figure> (również <xref:System.Windows.Documents.Inline> elementu) może mieć tylko <xref:System.Windows.Documents.Block> elementów podrzędnych. W związku z tym diagram jest przydatne w przypadku szybkie ustalenie zgodności tego, jaki element mogą być zawarte w innym. Na przykład użyjmy diagramu do określenia sposobu konstruowania zawartości przepływu <xref:System.Windows.Controls.RichTextBox>.  
  
 **1.** A <xref:System.Windows.Controls.RichTextBox> musi zawierać <xref:System.Windows.Documents.FlowDocument> który z kolei musi zawierać <xref:System.Windows.Documents.Block>-pochodnych obiektu. Poniżej przedstawiono odpowiadającym segmencie: w powyższym diagramie.  
  
 ![Diagram: RichTextBox containment rules](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
 Tej pory jest to, jak może wyglądać znaczników.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
 **2.** Zgodnie z diagramem, istnieje kilka <xref:System.Windows.Documents.Block> elementów z tym <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.List>, i <xref:System.Windows.Documents.BlockUIContainer> (zobacz powyżej klas pochodnych bloku). Załóżmy, że chcemy <xref:System.Windows.Documents.Table>. Zgodnie z powyższym diagramie <xref:System.Windows.Documents.Table> zawiera <xref:System.Windows.Documents.TableRowGroup> zawierający <xref:System.Windows.Documents.TableRow> elementów, które zawierają <xref:System.Windows.Documents.TableCell> elementy, które zawierają <xref:System.Windows.Documents.Block>-pochodnych obiektu. Poniżej znajduje się odpowiedni segment dla <xref:System.Windows.Documents.Table> pobranych z powyższym diagramie.  
  
 ![Diagram: Parent&#47;child schema for Table](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
 Poniżej znajduje się odpowiedni kod znaczników.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
 **3.** Ponownie co najmniej jeden <xref:System.Windows.Documents.Block> elementy są wymagane, poniżej <xref:System.Windows.Documents.TableCell>. Się to uprościć, możemy umieścić tekst w komórce. Możemy to zrobić za pomocą <xref:System.Windows.Documents.Paragraph> z <xref:System.Windows.Documents.Run> elementu. Poniżej znajduje się odpowiedni segmentów z diagramu, na którym widać, że <xref:System.Windows.Documents.Paragraph> może potrwać <xref:System.Windows.Documents.Inline> elementu i że <xref:System.Windows.Documents.Run> ( <xref:System.Windows.Documents.Inline> elementu) przyjmuje tylko zwykły tekst.  
  
 ![Diagram: Nadrzędny&#47;schemat element podrzędny dla akapitu](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
 ![Diagram: Parent&#47;Child schema for Run](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 Poniżej znajduje się cały przykład w znacznikach.  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="customizing_text"></a>   
## <a name="customizing-text"></a>Dostosowywanie tekstu  
 Zazwyczaj tekst jest najbardziej rozpowszechnionych typu zawartości w dokumencie usługi flow. Mimo że obiekty wprowadzonych powyżej może służyć do kontrolowania większością aspektów sposób renderowania tekstu, istnieje kilka innych metod dostosowywania tekst, który został omówiony w tej sekcji.  
  
### <a name="text-decorations"></a>Dekoracje tekstu  
 Dekoracje tekstu pozwala na stosowanie efektów podkreślenia, nadkreślenia, punkt odniesienia i przekreślony tekst (zobacz poniżej obrazów). Dekoracje te są dodawane przy użyciu <xref:System.Windows.Documents.Inline.TextDecorations%2A> właściwość, która jest uwidaczniany przez liczbę obiektów w tym <xref:System.Windows.Documents.Inline>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Controls.TextBlock>, i <xref:System.Windows.Controls.TextBox>.  
  
 Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.Documents.Paragraph.TextDecorations%2A> właściwość <xref:System.Windows.Documents.Paragraph>.  
  
 [!code-xaml[InlineSnippets#_Paragraph_TextDecXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml#_paragraph_textdecxaml)]  
  
 [!code-csharp[InlineSnippets#_Paragraph_TextDec](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml.cs#_paragraph_textdec)]
 [!code-vb[InlineSnippets#_Paragraph_TextDec](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InlineSnippets/visualbasic/window1.xaml.vb#_paragraph_textdec)]  
  
 Na poniższej ilustracji przedstawiono, jak powoduje wyświetlenie w tym przykładzie.  
  
 ![Zrzut ekranu: Tekst domyślny przekreślenia efekt](../../../../docs/framework/wpf/advanced/media/inline-textdec-strike.png "Inline_TextDec_Strike")  
  
 Następujące wartości Pokaż sposób, w jaki **Nadkreślenia**, **linii bazowej**, i **Underline** dekoracje renderowania, odpowiednio.  
  
 ![Zrzut ekranu: Overline TextDecorator](../../../../docs/framework/wpf/advanced/media/inline-textdec-over.png "Inline_TextDec_Over")  
  
 ![Zrzut ekranu: Domyślny punkt odniesienia wpływu na tekst](../../../../docs/framework/wpf/advanced/media/inline-textdec-base.png "Inline_TextDec_Base")  
  
 ![Zrzut ekranu: Tekst z domyślnym efektem podkreślenia](../../../../docs/framework/wpf/advanced/media/inline-textdec-under.png "Inline_TextDec_Under")  
  
### <a name="typography"></a>Typografia  
 <xref:System.Windows.Documents.TextElement.Typography%2A> Właściwość jest uwidaczniana, umieszczając większość związane z przepływem zawartości <xref:System.Windows.Documents.TextElement>, <xref:System.Windows.Documents.FlowDocument>, <xref:System.Windows.Controls.TextBlock>, i <xref:System.Windows.Controls.TextBox>. Ta właściwość jest używana do sterowania typograficzne cech/zmiany tekstu (czyli małych lub dużych CAP, dzięki czemu indeks górny i dolny, itp.).  
  
 Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.Documents.TextElement.Typography%2A> atrybutu, za pomocą <xref:System.Windows.Documents.Paragraph> jako element przykładu.  
  
 [!code-xaml[TextElementSnippets#_TextElement_TypogXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 Na poniższej ilustracji przedstawiono, jak powoduje wyświetlenie w tym przykładzie.  
  
 ![Zrzut ekranu: Tekst przy użyciu zmienionego typografii](../../../../docs/framework/wpf/advanced/media/textelement-typog.png "TextElement_Typog")  
  
 Z kolei na poniższej ilustracji pokazano, jak uzyskać podobny przykład przy użyciu domyślnych właściwości związane z typografią renderuje.  
  
 ![Zrzut ekranu: Tekst przy użyciu zmienionego typografii](../../../../docs/framework/wpf/advanced/media/textelement-typog-default.png "TextElement_Typog_Default")  
  
 Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.Controls.TextBox.Typography%2A> właściwość programowo.  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
 Zobacz [Typografia w WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md) więcej informacji na temat typografii.  
  
## <a name="see-also"></a>Zobacz także
- [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)
- [Typografia w WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)
- [Tematy z instrukcjami](../../../../docs/framework/wpf/advanced/flow-content-elements-how-to-topics.md)
- [Przegląd modelu zawartości TextElement](../../../../docs/framework/wpf/advanced/textelement-content-model-overview.md)
- [RichTextBox — omówienie](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
- [Dokumenty w WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
- [Przegląd tabeli](../../../../docs/framework/wpf/advanced/table-overview.md)
- [Przegląd adnotacji](../../../../docs/framework/wpf/advanced/annotations-overview.md)
