---
title: Znak odstępu przetwarzanie w XAML
ms.date: 03/30/2017
helpviewer_keywords:
- East Asian characters [XAML Services]
- XAML [XAML Services], white-space processing
- white-space processing in XAML [XAML Services]
- characters [XAML Services], East Asian
ms.assetid: cc9cc377-7544-4fd0-b65b-117b90bb0b23
ms.openlocfilehash: da559a7e009861faaba16484276eb97be537482b
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "58048036"
---
# <a name="white-space-processing-in-xaml"></a>Znak odstępu przetwarzanie w XAML
Stan reguły języka XAML, że znaczące biały znak muszą zostać przetworzone przez [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] implementacji procesora. W tym temacie opisano te reguły języka XAML. Również dokumenty obsługi dodatkowe biały znak, który jest definiowany przez [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] implementacji procesora XAML i zapisywania XAML do serializacji.  
  
<a name="whitespace_definition"></a>   
## <a name="white-space-definition"></a>Definicja odstępu  
 Zgodne z [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)], odstępu w [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] to miejsce, wysuwu wiersza i karty. Odpowiadają one [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] wartości 0020, 000A i 0009 odpowiednio.  
  
<a name="whitespace_normalization"></a>   
## <a name="white-space-normalization"></a>Normalizacji biały znak —  
 Domyślnie następujące normalizacji biały znak — występuje gdy [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] procesów procesora [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] pliku:  
  
1.  Znaki wysuwu wiersza między znaki wschodnioazjatyckie są usuwane. Zobacz sekcję "Znaki wschodnioazjatyckie" w dalszej części tego tematu dla definicji tego terminu.  
  
2.  Wszystkie znaki odstępu (spacja, wysuw wiersza, karta) są konwertowane na miejsca do magazynowania.  
  
3.  Wszystkich następujących po sobie spacji są usunięty i zastąpiony przez jedną spację.  
  
4.  Odstęp natychmiast po tagu początkowego jest usuwany.  
  
5.  Miejsce, od razu, przed usunięciem tagu końcowego.  
  
 "Domyślna" odnosi się do stanu wskazywane przez wartość domyślną [XML: Space](xml-space-handling-in-xaml.md) atrybutu.  
  
<a name="whitespace_in_inner_text_and_string_primitives"></a>   
## <a name="white-space-in-inner-text-and-string-primitives"></a>Biały znak w tekst wewnętrzny i ciągu w nim elementów podstawowych  
 Poprzednie reguły normalizacji mają zastosowanie do wewnętrznego tekst, który znajduje się w obrębie elementów XAML. Po normalizacji procesor XAML konwertuje tekst wewnętrzny na odpowiedni typ w następujący sposób:  
  
-   Jeśli typ właściwości nie jest kolekcją, ale nie jest bezpośrednio <xref:System.Object> typu procesor XAML próbuje przekonwertować danego typu przy użyciu jego konwertera typów. W tym miejscu nie powiodło się konwersja powoduje błąd kompilacji.  
  
-   Jeśli typ właściwości jest kolekcją, a tekst wewnętrzny jest ciągły (nie pośredniczące elementu tagi), tekst wewnętrzny jest analizowany jako pojedynczy <xref:System.String>. Jeśli typ kolekcji nie może akceptować <xref:System.String>, powoduje błąd kompilacji.  
  
-   Jeśli typ właściwości to <xref:System.Object>, tekst wewnętrzny jest analizowany jako pojedynczy <xref:System.String>. Jeśli są aktywne tagi elementów, powoduje to błąd w czasie kompilacji, ponieważ <xref:System.Object> typu oznacza pojedynczy obiekt (<xref:System.String> lub w inny sposób).  
  
-   Jeśli typ właściwości jest kolekcją, a tekst wewnętrzny nie jest ciągły, pierwszego podciągu jest konwertowana na <xref:System.String> dodany jako element kolekcji, pośredniczące element zostanie dodany jako element kolekcji, a na koniec jest końcowe substring (jeśli istnieje) dodawane do kolekcji jako trzeci <xref:System.String> elementu.  
  
<a name="preserving_whitespace"></a>   
## <a name="preserving-white-space"></a>Zachowywanie białych  
 Istnieje kilka technik w celu zachowania biały znak w źródle [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dla ostatecznej prezentacji, która nie ma wpływu [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] normalizacji biały znak — procesor.  
  
 **xml:space="preserve"**: Określ ten atrybut na poziomie elementu, gdzie jest pożądane zachowania miejsca biały. Ta zachowuje wszystkie białe miejsca, która zawiera spacje, które mogłyby zostać dodane przez edytowanie kodu aplikacji "pretty print" wyrównywania elementów jako wizualnie intuicyjne zagnieżdżania. Jednak tego, czy renderowanie te miejsca do magazynowania jest określany przez model zawartości elementu zawierającego. Unikaj określania `xml:space="preserve"` na poziomie głównym ponieważ większość obiektów modeli nie bierze pod uwagę białe miejsca tak duże, niezależnie od tego, jak ustawić atrybutu. Ustawienie `xml:space` globalnie może mieć konsekwencje wydajności na XAML w niektórych implementacjach na przetworzenie (zwłaszcza serializacji). Lepiej jest tylko ustawić atrybutu specjalnie na poziomie elementów, które renderowania biały znak wewnątrz ciągów lub są kolekcjami znaczące odstępu.  
  
 **Jednostki i miejsca do magazynowania bez podziału**: [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] obsługuje umieszczanie dowolne [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] jednostki w modelu obiektu tekstu. Można użyć dedykowanej jednostki, takie jak spacja nierozdzielająca (&\#160; przy użyciu kodowania UTF-8). Można również użyć formantów tekstu sformatowanego, które obsługują znaki spacji nierozdzielających. Należy zachować ostrożność, jeśli używasz jednostek do symulacji layout charakterystyki, takie jak wcięcia, ponieważ dane wyjściowe w czasie wykonywania, które jednostek będzie zależeć od większa liczba czynników nie będzie możliwości przedstawiania wyników wcięcia w typowej system układu, takich jak polecenia paneli i marginesów. Na przykład, jednostki są mapowane na czcionek i rozmiar w odpowiedzi na wybór czcionki użytkownika można zmienić.  
  
<a name="east_asian_characters"></a>   
## <a name="east-asian-characters"></a>Znaki wschodnioazjatyckie  
 "Znaki wschodnioazjatyckie" jest zdefiniowany jako zestaw [!INCLUDE[TLA2#tla_unicode](../../../includes/tla2sharptla-unicode-md.md)] znak zakresów 20000 U + do U + 2FFFD i U + 30000 do U + 3FFFD. Podzbiór ten jest również czasami określane jako "Ideogramy CJK". Aby uzyskać więcej informacji, zobacz <https://www.unicode.org>.  
  
<a name="whitespace_and_text_content_models"></a>   
## <a name="white-space-and-text-content-models"></a>Modele zawartości biały znak i tekstu  
 W praktyce zachowywanie białych znaków jest tylko problemem w przypadku podzbiór wszystkich możliwych modele zawartości. Podzbiór ten składa się z modeli zawartości, które mogą podejmować pojedynczego <xref:System.String> typu w pewnej postaci dedykowany <xref:System.String> kolekcji lub kombinację <xref:System.String> a innymi typami danych w <xref:System.Collections.IList> lub <xref:System.Collections.Generic.ICollection%601> kolekcji.  
  
### <a name="white-space-and-text-content-models-in-wpf"></a>Modele zawartości biały znak i tekst w WPF  
 W celach ilustracyjnych w dalszej części tej sekcji odwołuje się określone typy, które są definiowane przez WPF. Funkcje obsługi odstępu, które są opisane w tym temacie są zazwyczaj przydatne do usług programu .NET Framework XAML i WPF. Aby wyświetlić to zachowanie w akcji, mogą eksperymentować z niektórych znaczników WPF XAML, wyświetlić wyniki w wykresu obiektu i następnie ponownie serializacji do znaczników.  
  
 Nawet w przypadku modeli zawartość, która może potrwać ciągami, zachowanie domyślne w ramach tych modeli zawartości jest, że dowolny biały obszar, który pozostaje nie jest traktowana jako istotny. Na przykład <xref:System.Windows.Controls.ListBox> przyjmuje <xref:System.Collections.IList>, ale biały (takie jak znaki wysuwu wiersza między poszczególnymi <xref:System.Windows.Controls.ListBoxItem>) jest nie są zachowywane i nie są renderowane. Jeśli spróbujesz użyć znaki wysuwu wiersza jako separatory między ciągi dla <xref:System.Windows.Controls.ListBoxItem> elementów, nie działa w ogóle; ciągów, które są oddzielone znaki wysuwu wiersza są traktowane jako jeden ciąg i jeden element.  
  
 Te kolekcje, które są traktowane biały znaczenia zwykle są częścią modelu dokument przepływu. Jest podstawowym kolekcji, która obsługuje zachowanie zachowania biały <xref:System.Windows.Documents.InlineCollection>. Ta klasa kolekcji jest zadeklarowana za pomocą <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>; w przypadku odnalezienia tego atrybutu [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] procesora traktują biały znak w kolekcji znaczenia. Kombinacja `xml:space="preserve"` i biały znak w <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> wskazywane Kolekcja to, czy wszystkie biały znak jest zachowywana i renderowania. Kombinacja `xml:space="default"` i biały znak w <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> powoduje, że początkowe normalizacji biały znak — opisanego wcześniej, co pozostawia jedno miejsce, w niektórych miejscach i te spacje są zachowywane i renderowania. Pożądane jest zachowanie zależy od użytkownika i należy używać `xml:space` selektywnie, aby umożliwić zachowanie, które chcesz.  
  
 Ponadto niektóre elementy wbudowane, które oznacza rzeczywistej linebreak w modelu dokument przepływu celowo nie powinna wprowadzać dodatkowe miejsce, nawet w przypadku kolekcji znaczące odstępu. Na przykład <xref:System.Windows.Documents.LineBreak> element ma tę samą funkcję co \<BR / > tag w [!INCLUDE[TLA2#tla_html](../../../includes/tla2sharptla-html-md.md)]i aby zwiększyć czytelność w znaczniku, zwykle <xref:System.Windows.Documents.LineBreak> jest oddzielona od tekstu kolejnych utworzone wysuwu wiersza. Tego wysuwu wiersza nie powinny być znormalizowane do stają się spację, kolejny wiersz. Aby włączyć to zachowanie w definicji klasy dla <xref:System.Windows.Documents.LineBreak> dotyczy elementu <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>, który następnie jest interpretowany przez [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] procesora oznacza ten biały znak otaczającego <xref:System.Windows.Documents.LineBreak> zawsze są spacje.  
  
## <a name="see-also"></a>Zobacz także
- [Przegląd XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
- [Jednostki znaków XML i XAML](xml-character-entities-and-xaml.md)
- [XML: Space — Obsługa w XAML](xml-space-handling-in-xaml.md)
