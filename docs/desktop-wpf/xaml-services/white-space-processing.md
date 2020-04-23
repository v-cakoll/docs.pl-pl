---
title: Przetwarzanie spacji w XAML
ms.date: 03/30/2017
helpviewer_keywords:
- East Asian characters [XAML Services]
- XAML [XAML Services], white-space processing
- white-space processing in XAML [XAML Services]
- characters [XAML Services], East Asian
ms.assetid: cc9cc377-7544-4fd0-b65b-117b90bb0b23
ms.openlocfilehash: 05f28c9115326424164b92e1b704c52bba31cf35
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071606"
---
# <a name="white-space-processing-in-xaml"></a>Przetwarzanie spacji w XAML

Reguły języka dla XAML stan, że znaczne [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] białe miejsce musi być przetwarzane przez implementację procesora. Ten artykuł dokumentuje te reguły języka XAML. Dokumentuje również dodatkową obsługę odstępu, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] który jest zdefiniowany przez implementację procesora XAML i modułu zapisującego XAML do serializacji.

## <a name="white-space-definition"></a>Definicja odstępu

Zgodnie z kodem XML [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] znaki odstępu to spacja, posajon wiersza i karta. Odpowiadają one odpowiednio wartościom Unicode 0020, 000A i 0009.

## <a name="white-space-normalization"></a>Normalizacja odstępów

Domyślnie podczas przetwarzania pliku występuje następująca normalizacja odstępu: [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]

1. Znaki wysuwu liniowego między znakami wschodnioazjatyckimi są usuwane. Zobacz sekcję "Znaki wschodnioazjatyckie" w dalszej części tego tematu, aby uzyskać definicję tego terminu.

2. Wszystkie znaki odstępu (spacja, wysuw wiersza, karta) są konwertowane na spacje.

3. Wszystkie kolejne spacje są usuwane i zastępowane jedną spacją.

4. Spacja bezpośrednio po znaczniku startowym zostanie usunięta.

5. Spacja bezpośrednio przed usunięciem znacznika końcowego.

"Domyślny" odpowiada stanowi oznaczonemu domyślną wartością atrybutu [xml:space.](xml-space-handling.md)

## <a name="white-space-in-inner-text-and-string-primitives"></a>Biały znak w tekście wewnętrznym i prymitywów ciągów

Poprzednie reguły normalizacji mają zastosowanie do tekstu wewnętrznego, który znajduje się w elementach XAML. Po normalizacji procesor XAML konwertuje dowolny tekst wewnętrzny na odpowiedni typ w następujący sposób:

- Jeśli typ właściwości nie jest kolekcją, ale <xref:System.Object> nie jest bezpośrednio typem, procesor XAML próbuje przekonwertować na ten typ przy użyciu konwertera typu. Konwersja nie powiodła się w tym miejscu powoduje błąd w czasie kompilacji.

- Jeśli typ właściwości jest kolekcją, a tekst wewnętrzny jest ciągły (bez zainterweniujących znaczników elementów), tekst wewnętrzny jest analizowany jako pojedynczy <xref:System.String>. Jeśli typ kolekcji <xref:System.String>nie może zaakceptować, powoduje to również błąd w czasie kompilacji.

- Jeśli typem właściwości <xref:System.Object>jest , tekst wewnętrzny jest analizowany jako pojedynczy <xref:System.String>. Jeśli istnieją interweniujące znaczniki elementu, powoduje to <xref:System.Object> błąd w czasie kompilacji, ponieważ typ implikuje pojedynczy obiekt (<xref:System.String> lub w inny sposób).

- Jeśli typ właściwości jest kolekcją, a tekst wewnętrzny nie jest ciągły, pierwszy podciąg <xref:System.String> jest konwertowany na a i dodawany jako element kolekcji, interweniujący element jest dodawany jako <xref:System.String> element kolekcji, a na koniec podciąg końcowy (jeśli istnieje) jest dodawany do kolekcji jako trzeci element.

## <a name="preserving-white-space"></a>Zachowywanie odstępu

Istnieje kilka technik zachowania odstępu w [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] źródle dla ostatecznej prezentacji, które nie są dotknięte normalizacji białej przestrzeni [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] procesora.

**xml:space="preserve":** Określ ten atrybut na poziomie elementu, w którym pożądane jest zachowanie odstępu. Pozwala to zachować wszystkie białe znaki, które obejmują spacje, które mogą być dodawane przez aplikacje do edycji kodu do "pretty-print" wyrównać elementy jako wizualnie intuicyjne zagnieżdżania. Jednak czy te spacje renderowania jest określana przez model zawartości dla elementu zawierającego. Należy unikać `xml:space="preserve"` określania na poziomie głównym, ponieważ większość modeli obiektów nie uważają biały znak za istotne, niezależnie od sposobu ustawiania atrybutu. Ustawienie `xml:space` globalnie może mieć wpływ na wydajność przetwarzania XAML (szczególnie serializacji) w niektórych implementacjach. Jest to lepsza praktyka, aby tylko ustawić atrybut w szczególności na poziomie elementów, które renderowania odstępu w ciągach lub są zbiory znaczące odstępu.

**Elementy i spacje nierozładujące:** [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] obsługuje umieszczanie dowolnego elementu Unicode w modelu obiektu tekstowego. Można użyć dedykowanych jednostek, takich jak nierozdzielające miejsce (&\#160; w kodowaniu UTF-8). Można również użyć formantów tekstu sformatującego, które obsługują znaki spacji nierozdzielające. Należy zachować ostrożność, jeśli używasz jednostek do symulowania charakterystyk układu, takich jak wcięcie, ponieważ dane wyjściowe w czasie wykonywania jednostek będą się różnić w zależności od większej liczby czynników niż możliwości tworzenia wyników wcięcie w typowym systemie układu, takich jak właściwe użycie paneli i marginesów. Na przykład jednostki są mapowane na czcionki i mogą zmieniać rozmiar w odpowiedzi na wybór czcionki użytkownika.

## <a name="east-asian-characters"></a>Znaki wschodnioazjatyckie

"Znaki wschodnioazjatyckie" jest zdefiniowany jako zestaw zakresów znaków Unicode U + 20000 do U + 2FFFD i U + 30000 do U + 3FFFD. Ten podzbiór jest również czasami określane jako "ideografy CJK". Aby uzyskać więcej informacji, zobacz <https://www.unicode.org>.

## <a name="white-space-and-text-content-models"></a>Modele zawartości odstępów i tekstu

W praktyce zachowanie odstępu jest tylko problemem dla podzbioru wszystkich możliwych modeli zawartości. Ten podzbiór składa się z modeli <xref:System.String> zawartości, które mogą <xref:System.String> przyjmować typ <xref:System.String> singleton w <xref:System.Collections.IList> jakiejś formie, dedykowanej kolekcji lub mieszaniny i innych typów w lub <xref:System.Collections.Generic.ICollection%601> kolekcji.

### <a name="white-space-and-text-content-models-in-wpf"></a>Modele zawartości odstępów i tekstu w wyw.

Na potrzeby ilustracji pozostała część tej sekcji odwołuje się do określonych typów, które są zdefiniowane przez WPF. Funkcje obsługi odstępu, które są opisane w tym artykule są istotne dla usług .NET XAML i WPF. Aby zobaczyć to zachowanie w akcji, można eksperymentować z niektórych znaczników WPF XAML, wyświetlić wyniki na wykresie obiektu, a następnie serializować z powrotem do znaczników ponownie.

Nawet w przypadku modeli zawartości, które mogą przyjmować ciągi, domyślne zachowanie w tych modelach zawartości jest, że wszystkie odstępy, które pozostaje nie jest traktowany jako istotne. Na przykład <xref:System.Windows.Controls.ListBox> przyjmuje <xref:System.Collections.IList>, ale biały znak (na przykład <xref:System.Windows.Controls.ListBoxItem>wysuwy wiersza między każdym ) nie jest zachowywany i nie jest renderowany. Jeśli spróbujesz użyć posyłaczy wierszy <xref:System.Windows.Controls.ListBoxItem> jako separatorów między ciągami dla elementów, nie działa w ogóle; ciągi, które są oddzielone przez wysuwy wiersza są traktowane jako jeden ciąg i jeden element.

Te kolekcje, które traktują biały znak jako istotne są zazwyczaj częścią modelu dokumentu przepływu. Podstawowa kolekcja, która obsługuje zachowanie <xref:System.Windows.Documents.InlineCollection>zachowania zachowania zachowania odstępu jest . Ta klasa kolekcji <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>jest zadeklarowana za pomocą ; po znalezieniu tego atrybutu [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] procesor będzie traktować biały znak w kolekcji jako istotne. Kombinacja `xml:space="preserve"` i biały znak <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> w obrębie oznaczonej kolekcji jest, że wszystkie białe znak jest zachowywany i renderowane. Kombinacja `xml:space="default"` i biały znak <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> w obrębie powoduje początkową normalizację odstępu opisane wcześniej, która pozostawia jedną przestrzeń w niektórych pozycjach, a te spacje są zachowywane i renderowane. Jakie zachowanie jest pożądane jest do Ciebie `xml:space` i należy użyć selektywnie, aby włączyć zachowanie, które chcesz.

Ponadto niektóre elementy wbudowane, które oznaczają podział wiersza w modelu dokumentu przepływu, nie powinny celowo wprowadzać dodatkowego miejsca nawet w kolekcji znaczącej w białej przestrzeni. Na przykład <xref:System.Windows.Documents.LineBreak> element ma ten sam \<cel co znacznik BR/> w HTML, a dla <xref:System.Windows.Documents.LineBreak> czytelności w znacznikach zazwyczaj jest oddzielony od każdego kolejnego tekstu przez autorski posuw wiersza. Ten posuw liniowy nie powinien być znormalizowany, aby stał się wiodącą przestrzenią w kolejnej linii. Aby włączyć to zachowanie, definicja klasy <xref:System.Windows.Documents.LineBreak> <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>dla elementu stosuje , [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] który jest następnie interpretowany przez procesor, aby oznaczać, że biały znak otaczający <xref:System.Windows.Documents.LineBreak> jest zawsze przycięty.

## <a name="see-also"></a>Zobacz też

- [Omówienie XAML (WPF)](../fundamentals/xaml.md)
- [Jednostki znaków XML i XAML](xml-character-entities.md)
- [xml:obsługa spacji w języku XAML](xml-space-handling.md)
