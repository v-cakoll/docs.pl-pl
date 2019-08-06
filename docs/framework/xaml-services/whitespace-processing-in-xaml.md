---
title: Przetwarzanie spacji w XAML
ms.date: 03/30/2017
helpviewer_keywords:
- East Asian characters [XAML Services]
- XAML [XAML Services], white-space processing
- white-space processing in XAML [XAML Services]
- characters [XAML Services], East Asian
ms.assetid: cc9cc377-7544-4fd0-b65b-117b90bb0b23
ms.openlocfilehash: 077f19690d204d3b8f682d01c51feee9e9edbfd4
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796812"
---
# <a name="white-space-processing-in-xaml"></a>Przetwarzanie spacji w XAML
Reguły języka dla stanu XAML, które mają znaczący biały znak, muszą być [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] przetwarzane przez implementację procesora. Ten temat dokumentuje te reguły języka XAML. Zawiera również dodatkową obsługę odstępów, która jest definiowana przez [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] implementację procesora XAML i składnika zapisywania XAML do serializacji.  
  
<a name="whitespace_definition"></a>   
## <a name="white-space-definition"></a>Definicja odstępu  
 Spójne z [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)], biały znak w [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] to Space, wysuw wiersza i tabulator. Odpowiadają [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] odpowiednio wartościom 0020, 000A i 0009.  
  
<a name="whitespace_normalization"></a>   
## <a name="white-space-normalization"></a>Normalizacja białych miejsc  
 Domyślnie następujące białe normalizacji są wykonywane, gdy [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] procesor [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] przetwarza plik:  
  
1. Znaki wysuwu wiersza między wschodnioazjatyckimi znakami są usuwane. Zobacz sekcję "znaki wschodnioazjatyckie" w dalszej części tego tematu, aby zapoznać się z definicją tego terminu.  
  
2. Wszystkie znaki odstępu (spacja, znak wysuwu wiersza) są konwertowane na spacje.  
  
3. Wszystkie kolejne spacje są usuwane i zastępowane jedną spacją.  
  
4. Spacja bezpośrednio po tagu początkowym zostanie usunięta.  
  
5. Spacja bezpośrednio przed tagiem końcowym zostanie usunięta.  
  
 "Domyślnie" odpowiada stanowi wskazywanym przez wartość domyślną atrybutu [XML: Space](xml-space-handling-in-xaml.md) .  
  
<a name="whitespace_in_inner_text_and_string_primitives"></a>   
## <a name="white-space-in-inner-text-and-string-primitives"></a>Biały znak w tekście wewnętrznym i parametry pierwotne ciągu  
 Poprzednie reguły normalizacji mają zastosowanie do tekstu wewnętrznego, który znajduje się w elementach XAML. Po normalizacji procesor XAML konwertuje tekst wewnętrzny na odpowiedni typ w następujący sposób:  
  
- Jeśli typ właściwości nie jest kolekcją, ale nie jest bezpośrednio <xref:System.Object> typem, procesor XAML próbuje skonwertować do tego typu przy użyciu konwertera typów. Konwersja nie powiodła się w tym miejscu powoduje błąd czasu kompilacji.  
  
- Jeśli typ właściwości jest kolekcją, a tekst wewnętrzny jest ciągły (bez tagów elementów, które nie działa), tekst wewnętrzny jest analizowany jako pojedynczy <xref:System.String>. Jeśli typ kolekcji nie może akceptować <xref:System.String>, spowoduje to również błąd czasu kompilacji.  
  
- Jeśli typ właściwości to <xref:System.Object>, tekst wewnętrzny jest analizowany jako pojedynczy. <xref:System.String> Jeśli istnieją elementy, które powodują interwencję, powoduje to błąd czasu kompilacji, ponieważ <xref:System.Object> typ implikuje pojedynczy obiekt (<xref:System.String> lub w inny sposób).  
  
- Jeśli typ właściwości jest kolekcją, a tekst wewnętrzny nie jest ciągły, pierwszy podciąg jest konwertowany na <xref:System.String> a i dodany jako element kolekcji, element, który zostanie dodany jako element kolekcji, a wreszcie końcowy podciąg (jeśli istnieje) jest dodano do kolekcji jako trzeci <xref:System.String> element.  
  
<a name="preserving_whitespace"></a>   
## <a name="preserving-white-space"></a>Zachowywanie białych znaków  
 Istnieje kilka technik zachowywania białych znaków w źródle [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dla prezentacji ostatecznej, które nie mają [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] wpływ na normalizację odstępów między procesorami.  
  
 **xml:space="preserve"** : Określ ten atrybut na poziomie elementu, w którym jest wymagane zachowywanie odstępu. Powoduje to zachowanie wszystkich białych znaków, które obejmują spacje, które mogą być dodawane przez aplikacje edytujące kod do "wyglądu" "widocznego" w postaci wizualnie intuicyjnego zagnieżdżenia. Jednak niezależnie od tego, czy te miejsca renderowania są określane przez model zawartości dla elementu zawierającego. Należy unikać `xml:space="preserve"` określania na poziomie głównym, ponieważ większość modeli obiektów nie traktuje odstępu jako znaczącego, niezależnie od sposobu ustawiania atrybutu. Ustawienie `xml:space` globalne może mieć wpływ na wydajność przetwarzania XAML (szczególnie serializacji) w niektórych implementacjach. Lepszym rozwiązaniem jest ustawienie atrybutu tylko w odróżnieniu od elementów, które renderują białe znaki w ciągu, lub są znacznymi znaczącymi kolekcjami.  
  
 **Jednostki i spacje**nierozdzielające: [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] program [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] obsługuje umieszczanie dowolnej jednostki w obrębie modelu obiektów tekstowych. Można użyć dedykowanych jednostek, takich jak spacja nierozdzielająca\#(& 160; w kodowaniu UTF-8). Można również użyć formantów tekstu sformatowanego, które obsługują znaki nierozdzielające. Należy zachować ostrożność, jeśli używasz jednostek do symulacji layout charakterystyki, takie jak wcięcia, ponieważ dane wyjściowe w czasie wykonywania, które jednostek będzie zależeć od większa liczba czynników nie będzie możliwości przedstawiania wyników wcięcia w typowej system układu, takich jak polecenia paneli i marginesów. Na przykład jednostki są mapowane na czcionki i mogą zmieniać rozmiar w odpowiedzi na wybór czcionki użytkownika.  
  
<a name="east_asian_characters"></a>   
## <a name="east-asian-characters"></a>Znaki wschodnioazjatyckie  
 "Znaki wschodnioazjatyckie" są zdefiniowane jako zestaw [!INCLUDE[TLA2#tla_unicode](../../../includes/tla2sharptla-unicode-md.md)] zakresów znaku U + 20000 do u + 2FFFD i u + 30000 do u + 3FFFD. Ten podzestaw jest również czasami określany jako "ideogramy CJK". Aby uzyskać więcej informacji, zobacz <https://www.unicode.org>.  
  
<a name="whitespace_and_text_content_models"></a>   
## <a name="white-space-and-text-content-models"></a>Biały znak i modele zawartości tekstu  
 W tym celu zachowywanie białego miejsca jest tylko problemem tylko dla podzbioru wszystkich możliwych modeli zawartości. Ten podzbiór składa się z modeli zawartości, które mogą <xref:System.String> przyjmować pojedynczy typ w postaci <xref:System.String> pojedynczej kolekcji lub kombinacji <xref:System.String> i innych typów w <xref:System.Collections.IList> kolekcji lub <xref:System.Collections.Generic.ICollection%601> .  
  
### <a name="white-space-and-text-content-models-in-wpf"></a>Biały znak i modele zawartości tekstu w WPF  
 W celach ilustracyjnych pozostała część tej sekcji odwołuje się do określonych typów, które są zdefiniowane przez WPF. Funkcje obsługi białych znaków, które są opisane w tym temacie, mają zwykle miejsce w przypadku usług XAML .NET Framework i WPF. Aby zobaczyć to zachowanie w działaniu, można eksperymentować z niektórymi znacznikami XAML WPF, przeglądać wyniki na grafie obiektów, a następnie ponownie serializować do znaczników.  
  
 Nawet w przypadku modeli zawartości, które mogą przyjmować ciągi, domyślne zachowanie w ramach tych modeli zawartości polega na tym, że wszystkie białe miejsca, które pozostało nie są traktowane jako znaczące. Na przykład <xref:System.Windows.Controls.ListBox> <xref:System.Collections.IList>przyjmuje, że biały znak (na przykład wysuwu wiersza <xref:System.Windows.Controls.ListBoxItem>) nie jest zachowywany i nierenderowany. Jeśli próbujesz użyć znaku wysuwu wiersza jako separatorów między ciągami <xref:System.Windows.Controls.ListBoxItem> dla elementów, nie działa wcale. ciągi, które są rozdzielone znakami wysuwu wiersza, są traktowane jako jeden ciąg i jeden element.  
  
 Kolekcje te, które traktują biały znak jako znaczące są zwykle częścią modelu dokumentu przepływu. Główna kolekcja, która obsługuje zachowanie zachowywania białych miejsc, <xref:System.Windows.Documents.InlineCollection>to. Ta klasa kolekcji jest zadeklarowana z <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>; po znalezieniu [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] tego atrybutu procesor będzie traktować biały znak w kolekcji jako znaczący. Kombinacja `xml:space="preserve"` i biały znak <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> w kolekcji oznacza, że wszystkie białe miejsca są zachowywane i renderowane. Kombinacja `xml:space="default"` i biały znak <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> w programie powoduje, że poprzednia Poprzednia pozostała normalizacja białych miejsc nie pozostawia jednego miejsca w niektórych położeniach, a te spacje są zachowywane i renderowane. Takie zachowanie jest pożądane i należy używać `xml:space` selektywnie, aby włączyć żądane zachowanie.  
  
 Ponadto niektóre elementy wbudowane, które zanotują LineBreak w modelu dokumentu przepływu, powinny celowo nie wprowadzać dodatkowego miejsca nawet w znaczącej kolekcji o białej przestrzeni. Na przykład <xref:System.Windows.Documents.LineBreak> element ma takie samo przeznaczenie \<jak tag br/> w kodzie HTML i czytelność <xref:System.Windows.Documents.LineBreak> w znaczniku, zazwyczaj jest oddzielona od dowolnego kolejnego tekstu przez utworzony znak wysuwu wiersza. Ten znak wysuwu wiersza nie powinien być znormalizowany, aby stał się początkowym miejscem w następnym wierszu. Aby włączyć to zachowanie, definicja klasy <xref:System.Windows.Documents.LineBreak> dla elementu <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>stosuje, który następnie [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] jest interpretowany przez procesor, aby oznaczało, że białe miejsce otaczające <xref:System.Windows.Documents.LineBreak> jest zawsze przycinane.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
- [Jednostki znaków XML i XAML](xml-character-entities-and-xaml.md)
- [XML: obsługa miejsca w języku XAML](xml-space-handling-in-xaml.md)
