---
title: OpenType funkcje czcionki
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [WPF], OpenType
- typography [WPF], OpenType font technology
- OpenType font technology [WPF]
ms.assetid: 4061a9d1-fe8b-4921-9e17-18ec7d2e3ea2
ms.openlocfilehash: 52fe73bccd625c9508b398874fd6b075af2445e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186808"
---
# <a name="opentype-font-features"></a>OpenType funkcje czcionki

Ten temat zawiera omówienie niektórych kluczowych funkcji technologii [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]czcionek OpenType w pliku .  
  
<a name="overview"></a>
## <a name="opentype-font-format"></a>Format czcionki OpenType  
 Format czcionki OpenType jest rozszerzeniem formatu czcionki TrueType®, dodając obsługę danych czcionek PostScript. Format czcionki OpenType został opracowany wspólnie przez microsoft i Adobe Corporation. Czcionki OpenType i usługi systemu operacyjnego obsługujące czcionki OpenType zapewniają użytkownikom prosty sposób instalowania i używania czcionek, niezależnie od tego, czy czcionki zawierają kontury TrueType, czy kontury CFF (PostScript).  
  
 Format czcionki OpenType rozwiązuje następujące wyzwania dla deweloperów:  
  
- Szersza obsługa wielu platform.  
  
- Lepsze wsparcie dla międzynarodowych zestawów postaci.  
  
- Lepsza ochrona danych czcionek.  
  
- Mniejsze rozmiary plików, aby bardziej efektywna dystrybucja czcionek.  
  
- Szersze wsparcie dla zaawansowanej kontroli typograficznej.  
  
> [!NOTE]
> Zestaw Windows SDK zawiera zestaw przykładowych czcionek [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] OpenType, których można używać z aplikacjami. Czcionki te zapewniają większość funkcji zilustrowanych w pozostałej części tego tematu. Aby uzyskać więcej informacji, zobacz [Przykładowy pakiet czcionek OpenType](sample-opentype-font-pack.md).  
  
Aby uzyskać szczegółowe informacje o formacie czcionki OpenType, zobacz [specyfikację OpenType](https://docs.microsoft.com/typography/opentype/spec/).  
  
### <a name="advanced-typographic-extensions"></a>Zaawansowane rozszerzenia typograficzne  
 Zaawansowane tabele typograficzne (tabele układu OpenType) rozszerzają funkcjonalność czcionek za pomocą konturów TrueType lub CFF. Czcionki Układu OpenType zawierają dodatkowe informacje, które rozszerzają możliwości czcionek do obsługi wysokiej jakości typografii międzynarodowej. Większość czcionek OpenType udostępnia tylko podzbiór całkowitych dostępnych funkcji OpenType. Czcionki OpenType zapewniają następujące funkcje.  
  
- Bogate mapowanie między znakami i glifami obsługującymi ligatury, formularze pozycyjne, alternatywy i inne podstawienia czcionek.  
  
- Obsługa dwuwymiarowego pozycjonowania i mocowania glifów.  
  
- Jawne informacje o skrypcie i języku zawarte w czcionce, dzięki czemu aplikacja do przetwarzania tekstu może odpowiednio dostosować swoje zachowanie.  
  
 Tabele układu OpenType są opisane bardziej szczegółowo w sekcji ["Tabele plików czcionek"](https://www.microsoft.com/typography/otspec/otff.htm) w specyfikacji OpenType.  
  
 W pozostałej części tego przeglądu wprowadza szerokość i elastyczność niektórych wizualnie ciekawe funkcje OpenType, które są udostępniane przez właściwości <xref:System.Windows.Documents.Typography> obiektu. Aby uzyskać więcej informacji na temat tego obiektu, zobacz [Typografia Klasy](#typography_class).  
  
<a name="variants"></a>
## <a name="variants"></a>elementy Variant  
 Warianty są używane do renderowania różnych stylów typograficznych, takich jak indeksy górne i indeksy dolnego.  
  
### <a name="superscripts-and-subscripts"></a>Indeksy górne i dolny  
 Właściwość <xref:System.Windows.Documents.Typography.Variants%2A> umożliwia ustawienie wartości indeksu górnego i dolnego dla czcionki OpenType.  
  
 W poniższym tekście są wyświetlane indeksy górne czcionki Palatino Linotype.  
  
 ![Tekst przy użyciu indeksów górnych OpenType](./media/opentype-font-features/opentype-superscripts.gif "Tekst przy użyciu indeksów górnych OpenType")  
  
 Poniższy przykład znaczników pokazuje, jak zdefiniować indeksy górne dla czcionki <xref:System.Windows.Documents.Typography> Palatino Linotype, używając właściwości obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 W poniższym tekście są wyświetlane indeksy dolny dla czcionki Palatino Linotype.  
  
 ![Tekst przy użyciu skryptów dolnego Typu OpenType](./media/opentype-font-features/opentype-subscripts.gif "Tekst przy użyciu skryptów dolnego Typu OpenType")  
  
 Poniższy przykład znaczników pokazuje, jak zdefiniować indeksy dolny dla czcionki <xref:System.Windows.Documents.Typography> Palatino Linotype, przy użyciu właściwości obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a>Dekoracyjne zastosowania indeksów górnych i dolnego  
 Można również użyć indeksów górnych i dolnego do tworzenia efektów dekoracyjnych mieszanego tekstu sprawy. W poniższym tekście jest wyświetlany tekst indeksu górnego i dolnego czcionki Palatino Linotype. Należy pamiętać, że nie ma to wpływu na stolice.  
  
 ![Tekst przy użyciu indeksów górnych i dolnego OpenType](./media/opentype-font-features/opentype-superscripts-subscripts.gif "Tekst przy użyciu indeksów górnych i dolnego OpenType")  

 Poniższy przykład znaczników pokazuje, jak zdefiniować indeksy górne i dolny dla czcionki przy użyciu właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>
## <a name="capitals"></a>Stolice  
 Wielkie litery to zestaw form typograficznych, które renderują tekst w glifach w stylu wielkim. Zazwyczaj, gdy tekst jest renderowany jako wszystkie wielkie litery, odstępy między literami mogą wydawać się zbyt ciasne, a waga i proporcja liter są zbyt ciężkie. OpenType obsługuje szereg formatów stylów dla wielkich liter, w tym małe wielkie litery, drobne litery, napisy i odstępy między wielkimi literami. Te formaty stylów pozwalają kontrolować wygląd wielkich liter.  
  
 W poniższym tekście są wyświetlane standardowe wielkie litery czcionki Pescadero, a następnie litery stylizowane na "SmallCaps" i "AllSmallCaps". W takim przypadku ten sam rozmiar czcionki jest używany dla wszystkich trzech słów.  
  
 ![Tekst przy użyciu wielkich liter OpenType](./media/opentype-font-features/opentype-capitals.gif "Tekst przy użyciu wielkich liter OpenType")  
  
 Poniższy przykład znaczników pokazuje, jak zdefiniować wielkie litery czcionki <xref:System.Windows.Documents.Typography> Pescadero przy użyciu właściwości obiektu. Gdy używany jest format "SmallCaps", każda wiodąca wielka litera jest ignorowana.  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a>Tytułowe stolice  
 Tytułowe stolice są lżejsze pod względem wagi i proporcji i mają na celu nadanie bardziej eleganckiego wyglądu niż zwykłe stolice. Tytuły wielkich liter są zwykle używane w większych rozmiarach czcionek jako nagłówki. W poniższym tekście są wyświetlane zwykłe i tytułowe litery czcionki Pescadero. Zwróć uwagę na węższe szerokości trzpienia tekstu w drugim wierszu.  
  
 ![Tekst przy użyciu wielkich liter napisów OpenType](./media/opentype-font-features/opentype-titling-capitals.gif "Tekst przy użyciu wielkich liter napisów OpenType")  
  
 Poniższy przykład znaczników pokazuje, jak zdefiniować tytułowe litery dla czcionki <xref:System.Windows.Documents.Typography> Pescadero przy użyciu właściwości obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet17](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a>Odstępy między literami  
 Odstępy między literami to funkcja, która umożliwia zapewnienie większej liczby odstępów podczas używania wszystkich wielkich liter w tekście. Wielkie litery są zazwyczaj przeznaczone do mieszania z małych liter. Odstępy, które wydają się atrakcyjne między i wielkimi literami i małe litery mogą wyglądać zbyt mocno, gdy wszystkie wielkie litery są używane. W poniższym tekście są wyświetlane odstępy między normalnymi i kapitaliami dla czcionki Pescadero.  
  
 ![Tekst przy użyciu odstępów między literami OpenType](./media/opentype-font-features/opentype-capital-spacing.gif "Tekst przy użyciu odstępów między literami OpenType")  

 W poniższym przykładzie znaczników pokazano, jak zdefiniować odstępy między literami dla czcionki Pescadero przy użyciu właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet18](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>
## <a name="ligatures"></a>Ligatury  
 Ligatury to dwa lub więcej glifów, które są formowane w pojedynczy glif w celu utworzenia bardziej czytelnego lub atrakcyjnego tekstu. Czcionki OpenType obsługują cztery typy ligatur:  
  
- **Standardowe ligatury**. Zaprojektowany, aby zwiększyć czytelność. Standardowe ligatury to "fi", "fl" i "ff".  
  
- **Ligatury kontekstowe**. Zaprojektowany w celu zwiększenia czytelności, zapewniając lepsze zachowanie łączenia między znakami, które tworzą ligaturę.  
  
- **Ligatury uznaniowe**. Zaprojektowany, aby być ozdobne, a nie specjalnie zaprojektowane dla czytelności.  
  
- **Historyczne ligatury**. Zaprojektowany, aby być historycznym, a nie specjalnie zaprojektowany dla czytelności.  
  
 W poniższym tekście są wyświetlane standardowe glify ligatury dla czcionki Perykles.  
  
 ![Tekst przy użyciu ligatur standardowych OpenType](./media/opentype-font-features/opentype-standard-ligatures.gif "Tekst przy użyciu ligatur standardowych OpenType")  
  
 Poniższy przykład znaczników pokazuje, jak zdefiniować standardowe glify ligatury dla <xref:System.Windows.Documents.Typography> czcionki Perykles, używając właściwości obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 W poniższym tekście są wyświetlane glify ligatury uznaniowej dla czcionki Perykles.  
  
 ![Tekst przy użyciu ligatur uznaniowych OpenType](./media/opentype-font-features/opentype-discretionary-ligatures.gif "Tekst przy użyciu ligatur uznaniowych OpenType")  
  
 Poniższy przykład znaczników pokazuje, jak zdefiniować dyskrecjonalne ligatury glifów <xref:System.Windows.Documents.Typography> dla czcionki Perykles, przy użyciu właściwości obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 Domyślnie czcionki OpenType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] w włączaniu ligatur standardowych. Na przykład, jeśli używasz czcionki Palatino Linotype, standardowe ligatury "fi", "ff" i "fl" są wyświetlane jako połączony glif znaków. Należy zauważyć, że para znaków dla każdej ligatury standardowej dotykać siebie.  
  
 ![Tekst przy użyciu ligatur standardowych OpenType z Palatino Linotype](./media/opentype-font-features/opentype-standard-ligatures-palatino.gif "Tekst przy użyciu ligatur standardowych OpenType z Palatino Linotype")

 Można jednak wyłączyć standardowe operacje ligatury, tak aby standardowa ligatura, taka jak "ff", była wyświetlana jako dwa oddzielne glify, a nie jako połączony glif znaków.  
  
 ![Tekst przy użyciu wyłączonych ligatur standardowych OpenType](./media/opentype-font-features/disabled-opentype-standard-ligatures.gif "Tekst przy użyciu wyłączonych ligatur standardowych OpenType")  

 Poniższy przykład znaczników pokazuje, jak wyłączyć standardowe glify ligatury dla czcionki <xref:System.Windows.Documents.Typography> Palatino Linotype, używając właściwości obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>
## <a name="swashes"></a>Swashes (swashes)  
 Swashes są dekoracyjne glify, które używają opracowania ornamentacji często związane z kaligrafii. W poniższym tekście są wyświetlane standardowe i swash glify dla czcionki Pescadero.  
  
 ![Tekst przy użyciu standardu OpenType i glifów](./media/opentype-font-features/opentype-standard-swash-glyphs.gif "Tekst przy użyciu standardu OpenType i glifów")  

 Swashes są często używane jako elementy dekoracyjne w krótkich zwrotów, takich jak ogłoszenia zdarzeń. Poniższy tekst używa swashes do podkreślenia wielkich liter nazwy zdarzenia.  
  
 ![Tekst przy użyciu swashes OpenType](./media/opentype-font-features/opentype-swashes.gif "Tekst przy użyciu swashes OpenType")  
  
 W poniższym przykładzie znaczników pokazano, jak zdefiniować swashes dla czcionki, przy użyciu właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a>Swashes kontekstowe  
 Niektóre kombinacje glifów swash mogą powodować nieatrakcyjny wygląd, na przykład nakładające się maleństwa na sąsiednich literach. Za pomocą kontekstowego swash pozwala na użycie zastępczego swash glif, który daje lepszy wygląd. Poniższy tekst przedstawia ten sam wyraz przed i po zastosowaniu kontekstowego swash.  
  
 ![Tekst przy użyciu plików kontekstowych OpenType](./media/opentype-font-features/opentype-contextual-swashes.gif "Tekst przy użyciu plików kontekstowych OpenType")  
  
 Poniższy przykład znaczników pokazuje, jak zdefiniować kontekstowe swash dla czcionki Pescadero, przy użyciu właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet16](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>
## <a name="alternates"></a>Zastępców  
 Alternatywami są glify, które można zastąpić standardowym glifem. Czcionki OpenType, takie jak czcionka Peryklesa używana w poniższych przykładach, mogą zawierać alternatywne glify, których można użyć do tworzenia różnych wyglądów tekstu. W poniższym tekście są wyświetlane standardowe glify dla czcionki Perykles.  
  
 ![Tekst przy użyciu standardowych glifów OpenType](./media/opentype-font-features/opentype-standard-glyphs.gif "Tekst przy użyciu standardowych glifów OpenType")  

 Czcionka Perykles OpenType zawiera dodatkowe glify, które zapewniają stylistyczne alternatywy dla standardowego zestawu glifów. W poniższym tekście są wyświetlane glify alternatywne stylistyczne.  
  
 ![Tekst przy użyciu alternatywnych glifów stylistycznych OpenType](./media/opentype-font-features/opentype-stylistic-alternate-glyphs.gif "Tekst przy użyciu alternatywnych glifów stylistycznych OpenType")  
  
 Poniższy przykład znaczników pokazuje, jak zdefiniować stylistyczne glify alternatywne dla <xref:System.Windows.Documents.Typography> czcionki Perykles, przy użyciu właściwości obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 W poniższym tekście jest wyświetlanych kilka innych alternatywnych glifów stylistycznych dla czcionki Perykles.  
  
 ![Tekst przy użyciu alternatywnych glifów stylistycznych OpenType dla czcionki Perykles](./media/opentype-font-features/opentype-stylistic-alternate-glyphs-pericles.gif "Tekst przy użyciu alternatywnych glifów stylistycznych OpenType dla czcionki Perykles")

 Poniższy przykład znaczników pokazuje, jak zdefiniować te inne glify alternatywne stylistyczne.  
  
 [!code-xaml[OpenTypeFontSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a>Losowi kontekstowi zastępcy  
 Losowe kontekstowe alternatywy zapewniają wiele glifów zastępczych dla pojedynczego znaku. Po zaimplementowaniu za pomocą czcionek typu skrypt, ta funkcja może symulować pismo ręczne przy użyciu zestawu losowo wybranych glifów o niewielkich różnicach w wyglądzie. Poniższy tekst używa losowych kontekstowych alternatyw dla czcionki Lindsey. Należy zauważyć, że litera "a" różni się nieznacznie wyglądem  
  
 ![Tekst przy użyciu losowych kontekstowych zastępców OpenType](./media/opentype-font-features/opentype-random-contextual-alternates.gif "Tekst przy użyciu losowych kontekstowych zastępców OpenType")  
  
 Poniższy przykład znaczników pokazuje, jak zdefiniować losowe kontekstowe alternatywy <xref:System.Windows.Documents.Typography> dla czcionki Lindsey, przy użyciu właściwości obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet20](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a>Formy historyczne  
 Formy historyczne są konwencjami typograficznymi, które były powszechne w przeszłości. W poniższym tekście jest wyświetlana fraza "Boston, Massachusetts", używająca historycznej formy glifów dla czcionki Palatino Linotype.  
  
 ![Tekst przy użyciu formularzy historycznych OpenType](./media/opentype-font-features/opentype-historical-forms.gif "Tekst przy użyciu formularzy historycznych OpenType")  

 Poniższy przykład znaczników pokazuje, jak zdefiniować formularze historyczne dla czcionki <xref:System.Windows.Documents.Typography> Palatino Linotype, przy użyciu właściwości obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>
## <a name="numerical-styles"></a>Style numeryczne  
 Czcionki OpenType obsługują dużą liczbę funkcji, których można używać z wartościami liczbowymi w tekście.  
  
### <a name="fractions"></a>Frakcji  
 Czcionki OpenType obsługują style ułamków, w tym ukośne i skumulowane.  
  
 W poniższym tekście są wyświetlane style ułamków czcionki Palatino Linotype.  
  
 ![Tekst przy użyciu ułamków ukośnych i skumulowanych OpenType](./media/opentype-font-features/opentype-slashed-stacked-fractions.gif "Tekst przy użyciu ułamków ukośnych i skumulowanych OpenType")  

 Poniższy przykład znaczników pokazuje, jak zdefiniować style ułamków czcionki Palatino Linotype przy użyciu właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a>Cyfry starego stylu  
 Czcionki OpenType obsługują format liczbowy starego stylu. Ten format jest przydatny do wyświetlania cyfr w stylach, które nie są już standardowe. W poniższym tekście jest wyświetlana data XVIII wieku w standardowych i starych formatach liczbowych dla czcionki Palatino Linotype.  
  
 ![Tekst przy użyciu liczb starego stylu OpenType](./media/opentype-font-features/opentype-old-style-numerals.gif "Tekst przy użyciu liczb starego stylu OpenType")  

 W poniższym tekście są wyświetlane standardowe cyfry czcionki Palatino Linotype, po których następowały cyfry starego stylu.  
  
 ![Tekst przy użyciu starych zestawów liczbowych OpenType](./media/opentype-font-features/opentype-old-style-numeral-sets.gif "Tekst przy użyciu starych zestawów liczbowych OpenType")  
  
 Poniższy przykład znaczników pokazuje, jak zdefiniować stare numery stylu czcionki Palatino <xref:System.Windows.Documents.Typography> Linotype, przy użyciu właściwości obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a>Liczby proporcjonalne i tabelaryczne  
 Czcionki OpenType obsługują funkcję proporcjonalnego i tabelarycznego rysunku, aby kontrolować wyrównanie szerokości podczas korzystania z cyfr. Liczby proporcjonalne traktują każdą cyfrę jako mającą inną szerokość — "1" jest węższa niż "5". Liczby tabelaryczne są traktowane jako cyfry o równej szerokości, tak aby były wyrównane pionowo, co zwiększa czytelność informacji o typie finansowym.  
  
 W poniższym tekście są wyświetlane dwie wartości proporcjonalne w pierwszej kolumnie przy użyciu czcionki Miramonte. Zwróć uwagę na różnicę w szerokości między cyframi "5" i "1". Druga kolumna pokazuje te same dwie wartości liczbowe z szerokościami dostosowanymi za pomocą operacji figury tabelarycznej.  
  
 ![Tekst przy użyciu proporcjonalnych & opentype](./media/opentype-font-features/opentype-proportional-tabular-figures.gif "Tekst przy użyciu liczb proporcjonalnych i tabelaryjskich OpenType")  

 Poniższy przykład znaczników pokazuje, jak zdefiniować proporcjonalne i tabelaryczne liczby <xref:System.Windows.Documents.Typography> dla czcionki Miramonte, przy użyciu właściwości obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet19](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a>Zdysknięty zerem  
 Czcionki OpenType obsługują ukośnikowany format liczbowy zerowy, aby podkreślić różnicę między literą "O" a cyfrą "0". Liczba zerowa z cięciami jest często używana dla identyfikatorów w informacjach finansowych i biznesowych.  
  
 W poniższym tekście jest wyświetlany przykładowy identyfikator zamówienia przy użyciu czcionki Miramonte. Pierwszy wiersz używa standardowych cyfr. W drugim wierszu użyto cyfr zerowych, aby zapewnić lepszy kontrast z wielką literą "O".  
  
 ![Tekst przy użyciu liczb zerowych ukształtowanych typu OpenType](./media/opentype-font-features/opentype-slashed-zero-numerals.gif "Tekst przy użyciu liczb zerowych ukształtowanych typu OpenType")  

 Poniższy przykład znaczników pokazuje, jak zdefiniować ukośne cyfry zerowe <xref:System.Windows.Documents.Typography> dla czcionki Miramonte przy użyciu właściwości obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>
## <a name="typography-class"></a>Klasa typografii  
 Obiekt <xref:System.Windows.Documents.Typography> udostępnia zestaw funkcji, które obsługuje czcionka OpenType. Ustawiając właściwości w <xref:System.Windows.Documents.Typography> znacznikach, można łatwo tworzyć dokumenty korzystające z funkcji OpenType.  
  
 W poniższym tekście są wyświetlane standardowe wielkie litery czcionki Pescadero, a następnie litery stylizowane na "SmallCaps" i "AllSmallCaps". W takim przypadku ten sam rozmiar czcionki jest używany dla wszystkich trzech słów.  
  
 ![Tekst przy użyciu wielkich liter OpenType](./media/opentype-font-features/opentype-capitals.gif "Tekst przy użyciu wielkich liter OpenType")  

 Poniższy przykład znaczników pokazuje, jak zdefiniować wielkie litery czcionki <xref:System.Windows.Documents.Typography> Pescadero przy użyciu właściwości obiektu. Gdy używany jest format "SmallCaps", każda wiodąca wielka litera jest ignorowana.  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 Poniższy przykład kodu wykonuje to samo zadanie, co w poprzednim przykładzie znaczników.  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a>Właściwości klasy typografii  
 W poniższej tabeli wymieniono właściwości, wartości <xref:System.Windows.Documents.Typography> i ustawienia domyślne obiektu.  
  
|Właściwość|Wartości|Wartość domyślna|  
|--------------|----------------|-------------------|  
|<xref:System.Windows.Documents.Typography.AnnotationAlternates%2A>|Wartość liczbowa - bajt|0|  
|<xref:System.Windows.Documents.Typography.Capitals%2A>|<xref:System.Windows.FontCapitals.AllPetiteCaps>&#124; &#124; <xref:System.Windows.FontCapitals.AllSmallCaps> <xref:System.Windows.FontCapitals.Normal> &#124; <xref:System.Windows.FontCapitals.PetiteCaps> &#124; &#124; <xref:System.Windows.FontCapitals.SmallCaps> &#124; &#124; <xref:System.Windows.FontCapitals.Titling><xref:System.Windows.FontCapitals.Unicase>|<xref:System.Windows.FontCapitals.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.CapitalSpacing%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.CaseSensitiveForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.ContextualAlternates%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualSwashes%2A>|Wartość liczbowa - bajt|0|  
|<xref:System.Windows.Documents.Typography.DiscretionaryLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianExpertForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianLanguage%2A>|<xref:System.Windows.FontEastAsianLanguage.HojoKanji>&#124; <xref:System.Windows.FontEastAsianLanguage.Jis04> <xref:System.Windows.FontEastAsianLanguage.Jis78> &#124; &#124; <xref:System.Windows.FontEastAsianLanguage.Jis83> &#124; &#124; <xref:System.Windows.FontEastAsianLanguage.Jis90> <xref:System.Windows.FontEastAsianLanguage.NlcKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Normal> &#124; &#124; <xref:System.Windows.FontEastAsianLanguage.Simplified> <xref:System.Windows.FontEastAsianLanguage.Traditional> &#124; &#124;<xref:System.Windows.FontEastAsianLanguage.TraditionalNames>|<xref:System.Windows.FontEastAsianLanguage.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.EastAsianWidths%2A>|<xref:System.Windows.FontEastAsianWidths.Full>&#124; <xref:System.Windows.FontEastAsianWidths.Half> &#124; <xref:System.Windows.FontEastAsianWidths.Normal> &#124; <xref:System.Windows.FontEastAsianWidths.Proportional> &#124; <xref:System.Windows.FontEastAsianWidths.Quarter> &#124; &#124;<xref:System.Windows.FontEastAsianWidths.Third>|<xref:System.Windows.FontEastAsianWidths.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.Fraction%2A>|<xref:System.Windows.FontFraction.Normal>&#124; <xref:System.Windows.FontFraction.Slashed> &#124;<xref:System.Windows.FontFraction.Stacked>|<xref:System.Windows.FontFraction.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.HistoricalForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.HistoricalLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Kerning%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.MathematicalGreek%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.NumeralAlignment%2A>|<xref:System.Windows.FontNumeralAlignment.Normal>&#124; <xref:System.Windows.FontNumeralAlignment.Proportional> &#124;<xref:System.Windows.FontNumeralAlignment.Tabular>|<xref:System.Windows.FontNumeralAlignment.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.NumeralStyle%2A>|<xref:System.Boolean>|<xref:System.Windows.FontNumeralStyle.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.SlashedZero%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StandardLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.StandardSwashes%2A>|wartość liczbowa – bajt|0|  
|<xref:System.Windows.Documents.Typography.StylisticAlternates%2A>|wartość liczbowa – bajt|0|  
|<xref:System.Windows.Documents.Typography.StylisticSet1%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet2%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet3%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet4%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet5%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet6%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet7%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet8%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet9%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet10%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet11%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet12%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet13%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet14%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet15%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet16%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet17%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet18%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet19%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet20%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Variants%2A>|<xref:System.Windows.FontVariants.Inferior>&#124; <xref:System.Windows.FontVariants.Normal> &#124; <xref:System.Windows.FontVariants.Ordinal> &#124; <xref:System.Windows.FontVariants.Ruby> &#124; <xref:System.Windows.FontVariants.Subscript> &#124; &#124;<xref:System.Windows.FontVariants.Superscript>|<xref:System.Windows.FontVariants.Normal?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Documents.Typography>
- [Specyfikacja OpenType](https://docs.microsoft.com/typography/opentype/spec/)
- [Typografia w WPF](typography-in-wpf.md)
- [Przykład pakietu czcionek OpenType](sample-opentype-font-pack.md)
- [Pakowanie czcionek z aplikacjami](packaging-fonts-with-applications.md)
