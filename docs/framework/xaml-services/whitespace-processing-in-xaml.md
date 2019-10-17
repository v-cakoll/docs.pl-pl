---
title: Przetwarzanie spacji w XAML
ms.date: 03/30/2017
helpviewer_keywords:
- East Asian characters [XAML Services]
- XAML [XAML Services], white-space processing
- white-space processing in XAML [XAML Services]
- characters [XAML Services], East Asian
ms.assetid: cc9cc377-7544-4fd0-b65b-117b90bb0b23
ms.openlocfilehash: bf5c13f59b9e9c4774fde952a52289abb2815b65
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395980"
---
# <a name="white-space-processing-in-xaml"></a>Przetwarzanie spacji w XAML
Reguły języka języka XAML, które mają znaczący biały znak, muszą być przetwarzane przez implementację procesora [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]. Ten temat dokumentuje te reguły języka XAML. Zawiera również dodatkową obsługę odstępów, która jest definiowana przez implementację [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] procesora XAML i składnika zapisywania XAML do serializacji.  
  
<a name="whitespace_definition"></a>   
## <a name="white-space-definition"></a>Definicja odstępu  
 Spójne z [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)], białych znaków w [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] to Space, wysuw wiersza i tabulator. Odpowiadają odpowiednio wartościom Unicode 0020, 000A i 0009.  
  
<a name="whitespace_normalization"></a>   
## <a name="white-space-normalization"></a>Normalizacja białych miejsc  
 Domyślnie następująca nieodstępowa normalizacja występuje, gdy procesor [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] przetwarza plik [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]:  
  
1. Znaki wysuwu wiersza między wschodnioazjatyckimi znakami są usuwane. Zobacz sekcję "znaki wschodnioazjatyckie" w dalszej części tego tematu, aby zapoznać się z definicją tego terminu.  
  
2. Wszystkie znaki odstępu (spacja, znak wysuwu wiersza) są konwertowane na spacje.  
  
3. Wszystkie kolejne spacje są usuwane i zastępowane jedną spacją.  
  
4. Spacja bezpośrednio po tagu początkowym zostanie usunięta.  
  
5. Spacja bezpośrednio przed tagiem końcowym zostanie usunięta.  
  
 "Domyślnie" odpowiada stanowi wskazywanym przez wartość domyślną atrybutu [XML: Space](xml-space-handling-in-xaml.md) .  
  
<a name="whitespace_in_inner_text_and_string_primitives"></a>   
## <a name="white-space-in-inner-text-and-string-primitives"></a>Biały znak w tekście wewnętrznym i parametry pierwotne ciągu  
 Poprzednie reguły normalizacji mają zastosowanie do tekstu wewnętrznego, który znajduje się w elementach XAML. Po normalizacji procesor XAML konwertuje tekst wewnętrzny na odpowiedni typ w następujący sposób:  
  
- Jeśli typ właściwości nie jest kolekcją, ale nie jest bezpośrednio typu <xref:System.Object>, procesor XAML próbuje skonwertować do tego typu przy użyciu konwertera typów. Konwersja nie powiodła się w tym miejscu powoduje błąd czasu kompilacji.  
  
- Jeśli typ właściwości jest kolekcją, a tekst wewnętrzny jest ciągły (bez tagów elementów będących częścią), tekst wewnętrzny jest analizowany jako pojedynczy <xref:System.String>. Jeśli typ kolekcji nie może akceptować <xref:System.String>, spowoduje to również błąd czasu kompilacji.  
  
- Jeśli typ właściwości jest <xref:System.Object>, tekst wewnętrzny jest analizowany jako pojedynczy <xref:System.String>. Jeśli istnieją elementy, które powodują interwencję, powoduje to błąd czasu kompilacji, ponieważ typ <xref:System.Object> oznacza pojedynczy obiekt (<xref:System.String> lub inny).  
  
- Jeśli typ właściwości jest kolekcją, a tekst wewnętrzny nie jest ciągły, pierwszy podciąg jest konwertowany na <xref:System.String> i dodany jako element kolekcji, element, który zostanie dodany jako element kolekcji, a wreszcie zostanie dodany końcowy podciąg (jeśli istnieje) do kolekcji jako trzeci element <xref:System.String>.  
  
<a name="preserving_whitespace"></a>   
## <a name="preserving-white-space"></a>Zachowywanie białych znaków  
 Istnieje kilka technik zachowywania białych znaków w źródle [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dla prezentacji ostatecznej, w przypadku których nie ma to żadnego wpływ na normalizację [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)].  
  
 **XML: Space = "preserve"**: Określ ten atrybut na poziomie elementu, w którym jest zachowywane białe miejsce. Powoduje to zachowanie wszystkich białych znaków, które obejmują spacje, które mogą być dodawane przez aplikacje edytujące kod do "wyglądu" "widocznego" w postaci wizualnie intuicyjnego zagnieżdżenia. Jednak niezależnie od tego, czy te miejsca renderowania są określane przez model zawartości dla elementu zawierającego. Należy unikać określania `xml:space="preserve"` na poziomie głównym, ponieważ większość modeli obiektów nie traktuje odstępu jako znaczącego, niezależnie od sposobu ustawienia atrybutu. Ustawienie `xml:space` globalnie może mieć wpływ na wydajność przetwarzania XAML (szczególnie serializacji) w niektórych implementacjach. Lepszym rozwiązaniem jest ustawienie atrybutu tylko w odróżnieniu od elementów, które renderują białe znaki w ciągu, lub są znacznymi znaczącymi kolekcjami.  
  
 **Jednostki i spacje nierozdzielające**: [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] obsługuje umieszczanie dowolnej jednostki Unicode w obrębie modelu obiektów tekstowych. Można użyć dedykowanych jednostek, takich jak spacja nierozdzielająca (& \#160; w kodowaniu UTF-8). Można również użyć formantów tekstu sformatowanego, które obsługują znaki nierozdzielające. Należy zachować ostrożność, jeśli używasz jednostek do symulowania cech układu, takich jak wcięcia, ponieważ dane wyjściowe w czasie wykonywania jednostek będą się różnić w zależności od większej liczby czynników niż w przypadku, gdy możliwości tworzenia wcięć mają wynik w typowym Układ układu, taki jak poprawne użycie paneli i marginesów. Na przykład jednostki są mapowane na czcionki i mogą zmieniać rozmiar w odpowiedzi na wybór czcionki użytkownika.  
  
<a name="east_asian_characters"></a>   
## <a name="east-asian-characters"></a>Znaki wschodnioazjatyckie  
 "Znaki wschodnioazjatyckie" są zdefiniowane jako zestaw zakresów znaków Unicode U + 20000 do U + 2FFFD i U + 30000 do U + 3FFFD. Ten podzestaw jest również czasami określany jako "ideogramy CJK". Aby uzyskać więcej informacji, zobacz <https://www.unicode.org>.  
  
<a name="whitespace_and_text_content_models"></a>   
## <a name="white-space-and-text-content-models"></a>Biały znak i modele zawartości tekstu  
 W tym celu zachowywanie białego miejsca jest tylko problemem tylko dla podzbioru wszystkich możliwych modeli zawartości. Ten podzbiór składa się z modeli zawartości, które mogą przyjmować pojedyncze <xref:System.String> w niektórych formularzach, dedykowane kolekcje <xref:System.String> lub kombinację <xref:System.String> i innych typów w kolekcji <xref:System.Collections.IList> lub <xref:System.Collections.Generic.ICollection%601>.  
  
### <a name="white-space-and-text-content-models-in-wpf"></a>Biały znak i modele zawartości tekstu w WPF  
 W celach ilustracyjnych pozostała część tej sekcji odwołuje się do określonych typów, które są zdefiniowane przez WPF. Funkcje obsługi białych znaków, które są opisane w tym temacie, mają zwykle miejsce w przypadku usług XAML .NET Framework i WPF. Aby zobaczyć to zachowanie w działaniu, można eksperymentować z niektórymi znacznikami XAML WPF, przeglądać wyniki na grafie obiektów, a następnie ponownie serializować do znaczników.  
  
 Nawet w przypadku modeli zawartości, które mogą przyjmować ciągi, domyślne zachowanie w ramach tych modeli zawartości polega na tym, że wszystkie białe miejsca, które pozostało nie są traktowane jako znaczące. Na przykład <xref:System.Windows.Controls.ListBox> przyjmuje <xref:System.Collections.IList>, ale odstępy (takie jak wysuwu wiersza między poszczególnymi <xref:System.Windows.Controls.ListBoxItem>) nie są zachowywane i nierenderowane. Próba użycia wysuwu wiersza jako separatorów między ciągami dla elementów <xref:System.Windows.Controls.ListBoxItem> nie działa wcale; ciągi, które są rozdzielone znakami wysuwu wiersza, są traktowane jako jeden ciąg i jeden element.  
  
 Kolekcje te, które traktują biały znak jako znaczące są zwykle częścią modelu dokumentu przepływu. Główna kolekcja, która obsługuje zachowanie zachowywania białych miejsc, to <xref:System.Windows.Documents.InlineCollection>. Ta klasa kolekcji jest zadeklarowana z <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>; Po znalezieniu tego atrybutu procesor [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] będzie traktować biały znak w kolekcji jako znaczący. Kombinacja `xml:space="preserve"` i odstępu w kolekcji z <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> oznacza, że wszystkie białe miejsca są zachowywane i renderowane. Kombinacja `xml:space="default"` i białych znaków w <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> powoduje, że początkowa normalizacja białych miejsc opisana wcześniej, która pozostawia pojedyncze miejsce w niektórych położeniach, a te miejsca są zachowywane i renderowane. Takie zachowanie jest pożądane i należy używać `xml:space` selektywnie, aby włączyć odpowiednie zachowanie.  
  
 Ponadto niektóre elementy wbudowane, które zanotują LineBreak w modelu dokumentu przepływu, powinny celowo nie wprowadzać dodatkowego miejsca nawet w znaczącej kolekcji o białej przestrzeni. Na przykład element <xref:System.Windows.Documents.LineBreak> ma takie samo znaczenie jak tag \<BR/> w kodzie HTML i czytelność w znaczniku, zazwyczaj <xref:System.Windows.Documents.LineBreak> jest oddzielona od dowolnego kolejnego tekstu przez utworzony znak wysuwu wiersza. Ten znak wysuwu wiersza nie powinien być znormalizowany, aby stał się początkowym miejscem w następnym wierszu. Aby włączyć to zachowanie, definicja klasy dla elementu <xref:System.Windows.Documents.LineBreak> stosuje <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>, który jest następnie interpretowany przez procesor [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)], aby oznaczało, że białe miejsce otaczające <xref:System.Windows.Documents.LineBreak> jest zawsze przycinane.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
- [Jednostki znaków XML i XAML](xml-character-entities-and-xaml.md)
- [XML: obsługa miejsca w języku XAML](xml-space-handling-in-xaml.md)
