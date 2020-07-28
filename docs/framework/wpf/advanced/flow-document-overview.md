---
title: Przegląd Dokument przepływu
description: Dowiedz się więcej o dokumentach przepływu w Windows Presentation Foundation, które dynamicznie dostosowują zawartość na podstawie rozmiaru okna, rozdzielczości urządzenia i preferencji użytkownika.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'documents [WPF], flow documents [WPF], , '
- ', '
- flow documents [WPF]
ms.assetid: ef236a50-d44f-43c8-ba7c-82b0c733c0b7
ms.openlocfilehash: dac0cb91175a1398a0124020c048e14d7bcd1f76
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165243"
---
# <a name="flow-document-overview"></a>Przegląd Dokument przepływu

Dokumenty przepływu zaprojektowano w celu zoptymalizowania wyświetlania i czytelności. Zamiast ustawić na jeden wstępnie zdefiniowany układ, dokumenty przepływu dynamicznie dostosowują i przepływają zawartość na podstawie zmiennych czasu wykonywania, takich jak rozmiar okna, rozdzielczość urządzenia i opcjonalne preferencje użytkownika. Ponadto dokumenty przepływu oferują zaawansowane funkcje dokumentu, takie jak podział na strony i kolumny. Ten temat zawiera omówienie dokumentów przepływu i sposobu ich tworzenia.

<a name="what_is_a_flow_document"></a>

## <a name="what-is-a-flow-document"></a>Co to jest dokument przepływu

Dokument przepływu jest przeznaczony do "przepływania zawartości" w zależności od rozmiaru okna, rozdzielczości urządzenia i innych zmiennych środowiskowych. Ponadto dokumenty przepływu mają wiele wbudowanych funkcji, takich jak wyszukiwanie, wyświetlanie trybów, które optymalizują czytelność i możliwość zmiany rozmiaru i wyglądu czcionek. Dokumenty przepływu są najlepiej wykorzystywane, gdy Łatwość czytania jest scenariuszem zużycia dokumentu podstawowego. Z kolei stałe dokumenty są przeznaczone do posiadania statycznej prezentacji. Stałe dokumenty są przydatne, gdy wierność zawartości źródłowej są istotne. Zobacz [dokumenty w WPF](documents-in-wpf.md) , aby uzyskać więcej informacji na temat różnych typów dokumentów.

Na poniższej ilustracji przedstawiono przykładowy dokument przepływu wyświetlany w kilku oknach o różnych rozmiarach. W miarę zmiany obszaru wyświetlania zawartość jest przepływa, aby najlepiej wykorzystać dostępne miejsce.

![Ponowne przepływ zawartości dokumentu przepływu](./media/edocs-flowdocument.png "eDocs_FlowDocument")

Jak widać na powyższym obrazie, zawartość przepływu może obejmować wiele składników, w tym akapity, listy, obrazy i wiele innych. Te składniki odpowiadają elementom w znacznikach i obiektach w kodzie proceduralnym. Te klasy szczegółowo opisano w sekcji [dotyczącej klas związanych z przepływem](#flow_related_classes) tego omówienia. Oto prosty przykład kodu, który tworzy dokument przepływu składający się z akapitu zawierającego tekst pogrubiony i listę.

[!code-xaml[FlowOvwSnippets_snip#SimpleFlowExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SimpleFlowExample.xaml#simpleflowexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SimpleFlowExample.cs#simpleflowcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SimpleFlowExample.vb#simpleflowcodeonlyexamplewholepage)]

Na poniższej ilustracji przedstawiono wygląd fragmentu kodu.

![Zrzut ekranu: renderowany przykład FlowDocument](./media/flow-ovw-first-example.png "Flow_Ovw_First_Example")

W tym przykładzie <xref:System.Windows.Controls.FlowDocumentReader> formant jest używany do hostowania zawartości przepływu. Zobacz [typy dokumentów przepływu](#flow_document_types) , aby uzyskać więcej informacji o kontrolkach hostingu zawartości przepływu. <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.List> , <xref:System.Windows.Documents.ListItem> , i <xref:System.Windows.Documents.Bold> elementy są używane do sterowania formatowaniem zawartości, na podstawie ich kolejności w znacznikach. Na przykład <xref:System.Windows.Documents.Bold> element rozciąga się tylko na część tekstu w akapicie; w efekcie tylko ta część tekstu jest pogrubienie. Jeśli używasz języka HTML, zobaczysz go.

Jak pokazano na powyższej ilustracji, istnieje kilka funkcji wbudowanych w dokumenty przepływu:

- Wyszukaj: umożliwia użytkownikowi przeszukiwanie pełnego tekstu całego dokumentu.

- Tryb wyświetlania: użytkownik może wybrać preferowany tryb wyświetlania, w tym tryb wyświetlania pojedynczej strony (strona w czasie), tryb wyświetlania dwustronicowego (w formacie książki) i przewijanie ciągłego (w dół).  Aby uzyskać więcej informacji na temat tych trybów wyświetlania, zobacz <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> .

- Kontrolki nawigacji stron: Jeśli tryb wyświetlania dokumentu używa stron, formanty nawigacji stron obejmują przycisk Przejdź do następnej strony (Strzałka w dół) lub poprzedniej strony (Strzałka w górę), a także wskaźniki dla bieżącego numeru strony i całkowitej liczby stron. Przechodzenie między stronami można także wykonać przy użyciu klawiszy strzałek na klawiaturze.

- Powiększenie: kontrolki powiększenia umożliwiają użytkownikowi zwiększenie lub zmniejszenie poziomu powiększenia, klikając odpowiednio przycisk Plus lub minus. Kontrolki powiększenia zawierają także suwak służący do dostosowywania poziomu powiększenia. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Controls.FlowDocumentReader.Zoom%2A>.

Te funkcje można modyfikować w zależności od kontrolki używanej do hostowania zawartości przepływu. W następnej sekcji opisano różne kontrolki.

<a name="flow_document_types"></a>

## <a name="flow-document-types"></a>Typy dokumentów przepływu

Wyświetlanie zawartości dokumentu przepływu i jej wygląd jest zależne od tego, który obiekt jest używany do hostowania zawartości przepływu. Istnieją cztery kontrolki obsługujące wyświetlanie zawartości przepływu: <xref:System.Windows.Controls.FlowDocumentReader> , <xref:System.Windows.Controls.FlowDocumentPageViewer> , <xref:System.Windows.Controls.RichTextBox> , i <xref:System.Windows.Controls.FlowDocumentScrollViewer> . Te kontrolki zostały krótko opisane poniżej.

> [!NOTE]
> <xref:System.Windows.Documents.FlowDocument>jest wymagany do bezpośredniego hostowania zawartości przepływu, dlatego wszystkie te kontrolki wyświetlania wykorzystują <xref:System.Windows.Documents.FlowDocument> funkcję, aby umożliwić hosting zawartości przepływu.

### <a name="flowdocumentreader"></a>FlowDocumentReader

<xref:System.Windows.Controls.FlowDocumentReader>obejmuje funkcje, które umożliwiają użytkownikowi dynamiczne wybieranie różnych trybów wyświetlania, w tym tryb wyświetlania pojedynczej strony (strona w czasie), tryb wyświetlania dwustronicowego (do odczytu książki) i przewijanie ciągłego (w dół). Aby uzyskać więcej informacji na temat tych trybów wyświetlania, zobacz <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> . Jeśli nie potrzebujesz możliwości dynamicznego przełączania między różnymi trybami wyświetlania, <xref:System.Windows.Controls.FlowDocumentPageViewer> a następnie <xref:System.Windows.Controls.FlowDocumentScrollViewer> udostępniaj jaśniejsze osoby przeglądające zawartość przepływu, które są rozwiązane w określonym trybie wyświetlania.

### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer i FlowDocumentScrollViewer

<xref:System.Windows.Controls.FlowDocumentPageViewer>Wyświetla zawartość w trybie wyświetlania strony w czasie, podczas gdy <xref:System.Windows.Controls.FlowDocumentScrollViewer> pokazuje zawartość w trybie przewijania ciągłego. Oba <xref:System.Windows.Controls.FlowDocumentPageViewer> i <xref:System.Windows.Controls.FlowDocumentScrollViewer> są stałe do określonego trybu wyświetlania. Porównaj z <xref:System.Windows.Controls.FlowDocumentReader> , która obejmuje funkcje, które umożliwiają użytkownikowi dynamiczne wybieranie różnych trybów wyświetlania (zgodnie z <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> wyliczeniem), przy kosztach większej ilości zasobów niż <xref:System.Windows.Controls.FlowDocumentPageViewer> lub <xref:System.Windows.Controls.FlowDocumentScrollViewer> .

Domyślnie pionowy pasek przewijania jest zawsze pokazywany, a poziomy pasek przewijania jest widoczny w razie konieczności. Domyślny interfejs użytkownika dla programu nie <xref:System.Windows.Controls.FlowDocumentScrollViewer> zawiera paska narzędzi; jednak <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> Właściwość może być używana do włączania wbudowanego paska narzędzi.

### <a name="richtextbox"></a>RichTextBox

Używasz, <xref:System.Windows.Controls.RichTextBox> gdy chcesz zezwolić użytkownikowi na edytowanie zawartości przepływu. Jeśli na przykład chcesz utworzyć Edytor, który zezwoli użytkownikowi na manipulowanie takimi jak tabele, kursywę i formatowanie pogrubione, należy użyć <xref:System.Windows.Controls.RichTextBox> . Aby uzyskać więcej informacji, zobacz [Omówienie RichTextBox](../controls/richtextbox-overview.md) .

> [!NOTE]
> Zawartość przepływu wewnątrz elementu <xref:System.Windows.Controls.RichTextBox> nie zachowuje się dokładnie tak, jak zawartość przepływu zawarta w innych kontrolkach. Na przykład nie ma żadnych kolumn w <xref:System.Windows.Controls.RichTextBox> i nie ma żadnego automatycznego zmieniania rozmiarów. Ponadto zazwyczaj wbudowane funkcje przepływu zawartości, takie jak wyszukiwanie, tryb wyświetlania, Nawigacja po stronie i powiększenie, nie są dostępne w obrębie <xref:System.Windows.Controls.RichTextBox> .

<a name="creating_flow_content"></a>

## <a name="creating-flow-content"></a>Tworzenie zawartości przepływu

Zawartość przepływu może być złożona, składa się z różnych elementów, takich jak tekst, obrazy, tabele, a nawet <xref:System.Windows.UIElement> klasy pochodne, takie jak formanty. Aby zrozumieć, jak utworzyć złożoną zawartość przepływu, następujące punkty są krytyczne:

- **Klasy związane z przepływem**: Każda Klasa używana w treści przepływu ma określony cel. Ponadto relacja hierarchiczna między klasami Flow ułatwia zrozumienie sposobu ich używania. Na przykład klasy pochodne <xref:System.Windows.Documents.Block> klasy są używane do przechowywania innych obiektów, gdy klasy pochodne od <xref:System.Windows.Documents.Inline> zawierają obiekty, które są wyświetlane.

- **Schemat zawartości**: dokument przepływu może wymagać znacznej liczby zagnieżdżonych elementów. Schemat zawartości określa możliwe relacje nadrzędny/podrzędny między elementami.

Poniższe sekcje zawierają szczegółowe informacje o każdym z tych obszarów.

<a name="flow_related_classes"></a>

## <a name="flow-related-classes"></a>Klasy pokrewne przepływu

Na poniższym diagramie przedstawiono obiekty najczęściej używane z zawartością przepływu:

![Diagram: Hierarchia klas elementów zawartości przepływu](./media/flow-class-hierarchy.png "Flow_Class_Hierarchy")

Na potrzeby zawartości usługi Flow istnieją dwie ważne Kategorie:

1. **Klasy pochodne bloków**: nazywane również "blokami elementów zawartości" lub "tylko elementy bloku". Elementy dziedziczące po <xref:System.Windows.Documents.Block> mogą służyć do grupowania elementów w ramach wspólnego elementu nadrzędnego lub do zastosowania wspólnych atrybutów do grupy.

2. **Klasy pochodne wbudowane**: nazywane również "elementami zawartości wbudowanej" lub po prostu "elementami wbudowanymi". Elementy dziedziczące po <xref:System.Windows.Documents.Inline> są zawarte w obrębie elementu bloku lub innego elementu wbudowanego. Elementy śródwierszowe są często używane jako bezpośrednie kontenery zawartości, która jest renderowana na ekranie. Na przykład <xref:System.Windows.Documents.Paragraph> (element bloku) może zawierać <xref:System.Windows.Documents.Run> (element wbudowany), ale <xref:System.Windows.Documents.Run> faktycznie zawiera tekst, który jest renderowany na ekranie.

Każda Klasa w tych dwóch kategoriach została krótko opisana poniżej.

### <a name="block-derived-classes"></a>Klasy pochodne bloków

**Akapitu**

<xref:System.Windows.Documents.Paragraph>jest zazwyczaj używany do grupowania zawartości w akapicie. Najprostszym i najbardziej typowym zastosowaniem akapitu jest utworzenie akapitu tekstu.

[!code-xaml[FlowOvwSnippets_snip#ParagraphExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ParagraphExample.xaml#paragraphexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ParagraphExample.cs#paragraphcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ParagraphExample.vb#paragraphcodeonlyexamplewholepage)]

Można jednak również zawierać inne elementy pochodne wbudowane, jak pokazano poniżej.

**Sekcja**

<xref:System.Windows.Documents.Section>służy tylko do przechowywania elementów innych niż <xref:System.Windows.Documents.Block> pochodne. Nie stosuje żadnego domyślnego formatowania do elementów, które zawiera. Jednak wszystkie wartości właściwości ustawione w odniesieniu <xref:System.Windows.Documents.Section> do jego elementów podrzędnych. Sekcja umożliwia również programistyczne wykonywanie iteracji za pomocą swojej kolekcji podrzędnej. <xref:System.Windows.Documents.Section>jest używany w podobny sposób do \<DIV> znacznika w kodzie HTML.

W poniższym przykładzie trzy akapity są zdefiniowane w jednej z nich <xref:System.Windows.Documents.Section> . Sekcja ma <xref:System.Windows.Documents.TextElement.Background%2A> wartość właściwości Red, w związku z czym kolor tła akapitów jest również czerwony.

[!code-xaml[FlowOvwSnippets_snip#SectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SectionExample.xaml#sectionexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SectionExample.cs#sectioncodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SectionExample.vb#sectioncodeonlyexamplewholepage)]

**BlockUIContainer**

<xref:System.Windows.Documents.BlockUIContainer>umożliwia <xref:System.Windows.UIElement> Osadzanie elementów (tj. <xref:System.Windows.Controls.Button> ) w zawartości przepływu pochodzącego od bloku. <xref:System.Windows.Documents.InlineUIContainer>(patrz poniżej) służy do osadzania <xref:System.Windows.UIElement> elementów w wewnętrznej zawartości przepływu. <xref:System.Windows.Documents.BlockUIContainer>i <xref:System.Windows.Documents.InlineUIContainer> są ważne, ponieważ nie istnieje żaden inny sposób użycia <xref:System.Windows.UIElement> zawartości w przepływie, chyba że jest ona zawarta w jednym z tych dwóch elementów.

Poniższy przykład pokazuje, jak używać <xref:System.Windows.Documents.BlockUIContainer> elementu do hostowania <xref:System.Windows.UIElement> obiektów w zawartości przepływu.

[!code-xaml[SpanSnippets#_BlockUIXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml#_blockuixaml)]

Na poniższej ilustracji przedstawiono sposób renderowania tego przykładu:

![Zrzut ekranu pokazujący obiekt UIElement osadzony w zawartości przepływu.](./media/flow-document-overview/embedded-blockuicontainer.png)

**Lista**

<xref:System.Windows.Documents.List>służy do tworzenia listy punktowanej lub liczbowej. Ustaw <xref:System.Windows.Documents.List.MarkerStyle%2A> Właściwość na <xref:System.Windows.TextMarkerStyle> wartość wyliczenia, aby określić styl listy. W poniższym przykładzie pokazano, jak utworzyć prostą listę.

[!code-xaml[FlowOvwSnippets_snip#ListExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ListExample.xaml#listexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ListExample.cs#listcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ListExample.vb#listcodeonlyexamplewholepage)]

> [!NOTE]
> <xref:System.Windows.Documents.List>jest jedynym elementem przepływu, który używa <xref:System.Windows.Documents.ListItemCollection> do zarządzania elementami podrzędnymi.

**Tabela**

<xref:System.Windows.Documents.Table>służy do tworzenia tabeli. <xref:System.Windows.Documents.Table>jest podobny do <xref:System.Windows.Controls.Grid> elementu, ale ma więcej możliwości i w związku z tym wymaga większego obciążenia zasobów. Ponieważ <xref:System.Windows.Controls.Grid> ma wartość <xref:System.Windows.UIElement> , nie można jej używać w przepływie zawartości, chyba że znajduje się w <xref:System.Windows.Documents.BlockUIContainer> lub <xref:System.Windows.Documents.InlineUIContainer> . Aby uzyskać więcej informacji na temat <xref:System.Windows.Documents.Table> , zobacz temat [Omówienie tabeli](table-overview.md).

### <a name="inline-derived-classes"></a>Klasy pochodne wbudowane

**Wykonane**

<xref:System.Windows.Documents.Run>służy do przechowywania niesformatowanego tekstu. Mogą oczekiwać, że <xref:System.Windows.Documents.Run> obiekty mają być szeroko używane w zawartości przepływu. Jednak w znaczniku <xref:System.Windows.Documents.Run> elementy nie są wymagane do użycia jawnie. <xref:System.Windows.Documents.Run>jest wymagany do użycia podczas tworzenia lub manipulowania dokumentami przepływu za pomocą kodu. Na przykład, w poniższym znaczniku, pierwszy <xref:System.Windows.Documents.Paragraph> określa <xref:System.Windows.Documents.Run> element jawnie, podczas gdy drugi nie. Oba akapity generują identyczne dane wyjściowe.

[!code-xaml[FlowOvwSnippets_snip#RunExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/RunSnippetsExample.xaml#runexample1)]

> [!NOTE]
> Począwszy od .NET Framework 4, <xref:System.Windows.Documents.Run.Text%2A> Właściwość <xref:System.Windows.Documents.Run> obiektu jest właściwością zależności. Właściwość można powiązać <xref:System.Windows.Documents.Run.Text%2A> ze źródłem danych, takim jak <xref:System.Windows.Controls.TextBlock> . <xref:System.Windows.Documents.Run.Text%2A>Właściwość w pełni obsługuje powiązanie jednokierunkowe. <xref:System.Windows.Documents.Run.Text%2A>Właściwość obsługuje również powiązanie dwukierunkowe, z wyjątkiem <xref:System.Windows.Controls.RichTextBox> . Aby zapoznać się z przykładem, zobacz <xref:System.Windows.Documents.Run.Text%2A?displayProperty=nameWithType> .

**Span**

<xref:System.Windows.Documents.Span>grupuje jednocześnie inne elementy zawartości wbudowanej. Do zawartości w obrębie elementu nie są stosowane żadne wbudowane renderowanie <xref:System.Windows.Documents.Span> . Jednak elementy dziedziczące po <xref:System.Windows.Documents.Span> dołączeniu <xref:System.Windows.Documents.Hyperlink> , <xref:System.Windows.Documents.Bold> <xref:System.Windows.Documents.Italic> i do <xref:System.Windows.Documents.Underline> formatowania tekstu.

Poniżej znajduje się przykład <xref:System.Windows.Documents.Span> służący do przechowywania zawartości wbudowanej, w tym tekstu, <xref:System.Windows.Documents.Bold> elementu i <xref:System.Windows.Controls.Button> .

[!code-xaml[FlowOvwSnippets_snip#SpanExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SpanExample.xaml#spanexamplewholepage)]

Poniższy zrzut ekranu przedstawia sposób renderowania tego przykładu.

![Zrzut ekranu: przykład renderowanego zakresu](./media/flow-spanexample.gif "Flow_SpanExample")

**InlineUIContainer**

<xref:System.Windows.Documents.InlineUIContainer>umożliwia <xref:System.Windows.UIElement> osadzenie elementów (tj. kontrolki <xref:System.Windows.Controls.Button> ) w <xref:System.Windows.Documents.Inline> elemencie zawartości. Ten element jest wbudowanym odpowiednikiem <xref:System.Windows.Documents.BlockUIContainer> opisanym powyżej. Poniżej znajduje się przykład, który używa <xref:System.Windows.Documents.InlineUIContainer> do wstawiania <xref:System.Windows.Controls.Button> wbudowanego elementu <xref:System.Windows.Documents.Paragraph> .

[!code-xaml[FlowOvwSnippets_snip#InlineUIContainerExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/InlineUIContainerExample.xaml#inlineuicontainerexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/InlineUIContainerExample.cs#inlineuicontainercodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/InlineUIContainerExample.vb#inlineuicontainercodeonlyexamplewholepage)]

> [!NOTE]
> <xref:System.Windows.Documents.InlineUIContainer>nie musi być używany jawnie w znaczniku. Jeśli zostanie pominięty, <xref:System.Windows.Documents.InlineUIContainer> zostanie on utworzony podczas kompilowania kodu.

**Rysunek i Floater**

<xref:System.Windows.Documents.Figure>i <xref:System.Windows.Documents.Floater> są używane do osadzania zawartości w dokumentach przepływu z właściwościami umieszczania, które mogą być dostosowane niezależnie od podstawowego przepływu zawartości. <xref:System.Windows.Documents.Figure>lub <xref:System.Windows.Documents.Floater> elementy są często używane do wyróżniania lub Accentuate części zawartości, do hostowania obrazów pomocniczych lub innej zawartości w ramach głównego przepływu zawartości lub do dodawania luźno powiązanej zawartości, takiej jak anonse.

Poniższy przykład pokazuje, jak osadzić a <xref:System.Windows.Documents.Figure> w akapit tekstu.

[!code-xaml[FlowOvwSnippets_snip#FigureExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/FigureExample.xaml#figureexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/FigureExample.cs#figurecodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/FigureExample.vb#figurecodeonlyexamplewholepage)]

Na poniższej ilustracji przedstawiono sposób renderowania tego przykładu.

![Zrzut ekranu: przykład rysunku](./media/flow-ovw-figure-example.png "Flow_Ovw_Figure_Example")

<xref:System.Windows.Documents.Figure>i <xref:System.Windows.Documents.Floater> są różne na kilka sposobów i są używane w różnych scenariuszach.

**Poznać**

- Może być umieszczony: można ustawić jego poziomy i pionową kotwicę, aby zadokować ją względem strony, zawartości, kolumny lub akapitu. Można również użyć <xref:System.Windows.Documents.Figure.HorizontalOffset%2A> właściwości i, <xref:System.Windows.Documents.Figure.VerticalOffset%2A> Aby określić dowolne przesunięcia.

- Jest zmienny na więcej niż jedną kolumnę: można ustawić <xref:System.Windows.Documents.Figure> wysokość i szerokość na wielokrotność rozmiaru strony, zawartości lub kolumny lub szerokości. Należy pamiętać, że w przypadku strony i zawartości wielokrotności większe niż 1 są niedozwolone. Na przykład można ustawić szerokość na <xref:System.Windows.Documents.Figure> "0,5 strony" lub "0,25 Content" lub "2 kolumny". Możesz również ustawić wysokość i szerokość na wartości bezwzględne pikseli.

- Nie ma stronicowania: Jeśli zawartość wewnątrz elementu nie <xref:System.Windows.Documents.Figure> mieści się w <xref:System.Windows.Documents.Figure> , będzie ona renderowana, dopóki zawartość jest dopasowana, a pozostała zawartość zostanie utracona

**Floater:**

- Nie może być pozycjonowane i będzie renderowany wszędzie tam, gdzie można dla niego udostępnić miejsce. Nie można ustawić przesunięcia ani zakotwiczenia a <xref:System.Windows.Documents.Floater> .

- Nie można mieć rozmiaru do więcej niż jednej kolumny: Domyślnie <xref:System.Windows.Documents.Floater> rozmiary w jednej kolumnie. Ma <xref:System.Windows.Documents.Floater.Width%2A> Właściwość, która może być ustawiona na wartość bezwzględną pikseli, ale jeśli ta wartość jest większa niż jedna szerokość kolumny jest ignorowana, a obiekt Floater ma rozmiar w jednej kolumnie. Można zmienić rozmiar do mniejszej niż jednej kolumny, ustawiając poprawną szerokość pikseli, ale rozmiar nie jest względny kolumną, więc "0.5 kolumna" nie jest prawidłowym wyrażeniem określającym <xref:System.Windows.Documents.Floater> Szerokość. <xref:System.Windows.Documents.Floater>nie ma właściwości Height i nie można ustawić jej wysokości, wysokość zależy od zawartości

- <xref:System.Windows.Documents.Floater>podziały stron: Jeśli jej zawartość z określoną szerokością rozciąga się na więcej niż 1 wysokość kolumny, nastąpi przerwania i dzielenia na następną kolumnę, następną stronę itd.

 <xref:System.Windows.Documents.Figure>jest dobrym miejscem do umieszczania zawartości autonomicznej w celu kontrolowania rozmiaru i pozycjonowania, a użytkownik ma pewność, że zawartość będzie mieści się w określonym rozmiarze. <xref:System.Windows.Documents.Floater>jest dobrym miejscem, aby umieścić więcej swobodnego przepływu zawartości, która jest podobna do zawartości strony głównej, ale jest oddzielona od niej.

**LineBreak**

<xref:System.Windows.Documents.LineBreak>powoduje, że w treści przepływu występuje podział wiersza. Poniższy przykład ilustruje użycie <xref:System.Windows.Documents.LineBreak> .

[!code-xaml[FlowOvwSnippets_snip#LineBreakExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/LineBreakExample.xaml#linebreakexamplewholepage)]

Poniższy zrzut ekranu przedstawia sposób renderowania tego przykładu.

![Zrzut ekranu: LineBreak przykład](./media/flow-ovw-linebreakexample.png "Flow_Ovw_LineBreakExample")

### <a name="flow-collection-elements"></a>Elementy kolekcji przepływu

W wielu powyższych przykładach <xref:System.Windows.Documents.BlockCollection> i <xref:System.Windows.Documents.InlineCollection> są używane do programistycznego konstruowania zawartości przepływu. Na przykład aby dodać elementy do, można <xref:System.Windows.Documents.Paragraph> użyć składni:

```csharp
myParagraph.Inlines.Add(new Run("Some text"));
```

Spowoduje to dodanie <xref:System.Windows.Documents.Run> do <xref:System.Windows.Documents.InlineCollection> elementu <xref:System.Windows.Documents.Paragraph> .  Jest to takie samo, jak znalezione niejawnie <xref:System.Windows.Documents.Run> wewnątrz <xref:System.Windows.Documents.Paragraph> znacznika:

```xml
<Paragraph>
Some Text
</Paragraph>
```

Przykładem użycia <xref:System.Windows.Documents.BlockCollection> , w poniższym przykładzie jest utworzenie nowej, <xref:System.Windows.Documents.Section> a następnie użycie metody **Add** w celu dodania nowej <xref:System.Windows.Documents.Paragraph> do <xref:System.Windows.Documents.Section> zawartości.

[!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
[!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]

Oprócz dodawania elementów do kolekcji przepływów można również usunąć elementy.  Poniższy przykład usuwa ostatni element z <xref:System.Windows.Documents.Inline> <xref:System.Windows.Documents.Span> .

[!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
[!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]

Poniższy przykład czyści całą zawartość ( <xref:System.Windows.Documents.Inline> elementy) z <xref:System.Windows.Documents.Span> .

[!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
[!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]

Podczas pracy z zawartością przepływu programowo, prawdopodobnie będziesz intensywnie korzystać z tych kolekcji.

Określa, czy element Flow używa <xref:System.Windows.Documents.InlineCollection> (konspektów) czy <xref:System.Windows.Documents.BlockCollection> (bloków) do przechowywania elementów podrzędnych, zależy od tego, jakiego typu elementy podrzędne ( <xref:System.Windows.Documents.Block> lub <xref:System.Windows.Documents.Inline> ) mogą być zawarte w elemencie nadrzędnym. Reguły zawierania dla elementów zawartości przepływu są podsumowywane w schemacie zawartości w następnej sekcji.

> [!NOTE]
> Istnieje trzeci typ kolekcji używany z zawartością przepływu, <xref:System.Windows.Documents.ListItemCollection> ale ta kolekcja jest używana tylko z <xref:System.Windows.Documents.List> . Ponadto istnieje kilka kolekcji używanych z programem <xref:System.Windows.Documents.Table> . Zobacz [Omówienie tabeli](table-overview.md) , aby uzyskać więcej informacji.

<a name="content_schema"></a>

## <a name="content-schema"></a>Schemat zawartości

Uwzględniając liczbę różnych elementów zawartości przepływu, można przeciążyć, aby śledzić typ elementów podrzędnych, które może zawierać element. Poniższy diagram podsumowuje reguły zawierania dla elementów przepływu. Strzałki reprezentują możliwe relacje nadrzędny/podrzędny.

![Diagram: schemat zawierania zawartości przepływu](./media/flow-content-schema.png "Flow_Content_Schema")

Jak widać na powyższym diagramie, elementy podrzędne dozwolone dla elementu nie muszą być ustalane w zależności od tego, czy jest to <xref:System.Windows.Documents.Block> element, czy <xref:System.Windows.Documents.Inline> element. Na przykład <xref:System.Windows.Documents.Span> <xref:System.Windows.Documents.Inline> element (elementu) może mieć tylko <xref:System.Windows.Documents.Inline> elementy podrzędne, chociaż <xref:System.Windows.Documents.Figure> element (również <xref:System.Windows.Documents.Inline> ) może mieć tylko <xref:System.Windows.Documents.Block> elementy podrzędne. W związku z tym diagram jest przydatny do szybkiego określania, który element może być zawarty w innym. Na przykład użyjemy diagramu, aby określić sposób konstruowania zawartości przepływu <xref:System.Windows.Controls.RichTextBox> .

**1.** A <xref:System.Windows.Controls.RichTextBox> musi zawierać, <xref:System.Windows.Documents.FlowDocument> które z kolei muszą zawierać <xref:System.Windows.Documents.Block> obiekt pochodny. Poniżej znajduje się odpowiedni segment z powyższego poziomu diagramu.

![Diagram: reguły zawierania RichTextBox](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")

Do tej pory może wyglądać znacznik.

[!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]

**2.** zgodnie z diagramem istnieją różne <xref:System.Windows.Documents.Block> elementy do wyboru, takie jak,, <xref:System.Windows.Documents.Paragraph> , <xref:System.Windows.Documents.Section> <xref:System.Windows.Documents.Table> <xref:System.Windows.Documents.List> i <xref:System.Windows.Documents.BlockUIContainer> (zobacz klasy pochodne bloków powyżej). Załóżmy, że chcemy <xref:System.Windows.Documents.Table> . Zgodnie z powyższym diagramem <xref:System.Windows.Documents.Table> zawiera <xref:System.Windows.Documents.TableRowGroup> elementy zawierające elementy, które zawierają <xref:System.Windows.Documents.TableRow> <xref:System.Windows.Documents.TableCell> <xref:System.Windows.Documents.Block> obiekty pochodne. Poniżej znajduje się odpowiedni segment na <xref:System.Windows.Documents.Table> podstawie powyższego diagramu.

![Diagram: nadrzędny schemat podrzędny&#47;tabeli](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")

Poniżej znajduje się odpowiednie oznaczenie.

[!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]

**3.** ponownie jeden lub więcej <xref:System.Windows.Documents.Block> elementów jest wymaganych poniżej <xref:System.Windows.Documents.TableCell> . Aby to ułatwić, umieść trochę tekstu wewnątrz komórki. Możemy to zrobić przy użyciu <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.Run> elementu z. Poniżej znajduje się odpowiednie segmenty z diagramu, które pokazują, że <xref:System.Windows.Documents.Paragraph> może przyjmować <xref:System.Windows.Documents.Inline> element i czy <xref:System.Windows.Documents.Run> ( <xref:System.Windows.Documents.Inline> element) może przyjmować tylko zwykły tekst.

![Diagram: nadrzędny&#47;schemat podrzędny dla akapitu](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")

![Diagram: nadrzędny&#47;schemat podrzędny dla przebiegu](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")

Poniżej znajduje się cały przykład znaczników.

[!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]

<a name="customizing_text"></a>

## <a name="customizing-text"></a>Dostosowywanie tekstu

Zazwyczaj tekst jest najbardziej rozpowszechnionym typem zawartości w dokumencie przepływu. Chociaż obiekty wprowadzone powyżej mogą służyć do kontrolowania większości aspektów renderowania tekstu, istnieją inne metody dostosowywania tekstu omówionego w tej sekcji.

### <a name="text-decorations"></a>Dekoracje tekstu

Dekoracje tekstu umożliwiają zastosowanie efektów podkreślenia, nadkreślenia, linii bazowej i przekreślenia do tekstu (Zobacz obrazy poniżej). Te dekoracje są dodawane przy użyciu <xref:System.Windows.Documents.Inline.TextDecorations%2A> właściwości, która jest udostępniana przez wiele obiektów <xref:System.Windows.Documents.Inline> , takich jak,, <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Controls.TextBox> .

Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.Documents.Paragraph.TextDecorations%2A> Właściwość <xref:System.Windows.Documents.Paragraph> .

[!code-xaml[InlineSnippets#_Paragraph_TextDecXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml#_paragraph_textdecxaml)]

[!code-csharp[InlineSnippets#_Paragraph_TextDec](~/samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml.cs#_paragraph_textdec)]
[!code-vb[InlineSnippets#_Paragraph_TextDec](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InlineSnippets/visualbasic/window1.xaml.vb#_paragraph_textdec)]

Na poniższej ilustracji przedstawiono sposób renderowania tego przykładu.

![Zrzut ekranu: tekst z domyślnym efektem przekreślenia](./media/inline-textdec-strike.png "Inline_TextDec_Strike")

Poniższe ilustracje pokazują, jak są renderowane **nadkreślenie**, **linie bazowe**i **podkreślenia** .

![Zrzut ekranu: nadkreślenie TextDecorator](./media/inline-textdec-over.png "Inline_TextDec_Over")

![Zrzut ekranu: domyślny efekt linii bazowej dla tekstu](./media/inline-textdec-base.png "Inline_TextDec_Base")

![Zrzut ekranu: tekst z domyślnym efektem podkreślenia](./media/inline-textdec-under.png "Inline_TextDec_Under")

### <a name="typography"></a>Typografia

<xref:System.Windows.Documents.TextElement.Typography%2A>Właściwość jest udostępniana przez większość treści związanych z przepływem <xref:System.Windows.Documents.TextElement> , takich jak,, <xref:System.Windows.Documents.FlowDocument> <xref:System.Windows.Controls.TextBlock> i <xref:System.Windows.Controls.TextBox> . Ta właściwość służy do kontrolowania cech charakterystycznych/odmian tekstu (tj. małych lub wielkich liter, tworzenia indeksów górnych i indeksów itp.).

Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.Documents.TextElement.Typography%2A> atrybut, używając <xref:System.Windows.Documents.Paragraph> jako przykładowego elementu.

[!code-xaml[TextElementSnippets#_TextElement_TypogXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]

Na poniższej ilustracji przedstawiono sposób renderowania tego przykładu.

![Zrzut ekranu: tekst z zmienioną typografią](./media/textelement-typog.png "TextElement_Typog")

Z drugiej strony na poniższej ilustracji pokazano, jak podobny przykład z domyślnymi właściwościami typograficznych.

![Zrzut ekranu: tekst z zmienioną typografią](./media/textelement-typog-default.png "TextElement_Typog_Default")

Poniższy przykład pokazuje, jak ustawić <xref:System.Windows.Controls.TextBox.Typography%2A> właściwości programowo.

[!code-csharp[TextElementSnippets#_TextElement_Typog](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
[!code-vb[TextElementSnippets#_TextElement_Typog](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]

Zobacz [Typografia w WPF](typography-in-wpf.md) , aby uzyskać więcej informacji na temat typografii.

## <a name="see-also"></a>Zobacz także

- [Tekst](optimizing-performance-text.md)
- [Typografia w WPF](typography-in-wpf.md)
- [— Tematy porad](flow-content-elements-how-to-topics.md)
- [Przegląd Model zawartości TextElement](textelement-content-model-overview.md)
- [RichTextBox — Przegląd](../controls/richtextbox-overview.md)
- [Dokumenty w WPF](documents-in-wpf.md)
- [Przegląd Tabela](table-overview.md)
- [Przegląd Adnotacje](annotations-overview.md)
