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
ms.openlocfilehash: 3f1f0698afce6e64711e37ac60d0662d65bbee6b
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016139"
---
# <a name="opentype-font-features"></a>OpenType funkcje czcionki

Ten temat zawiera omówienie niektórych kluczowych funkcji technologii czcionek OpenType w programie [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
<a name="overview"></a>   
## <a name="opentype-font-format"></a>Format czcionki OpenType  
 Format czcionki OpenType to rozszerzenie [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] formatu czcionki, umożliwiające dodanie obsługi danych czcionki PostScript. Format czcionki OpenType został opracowany wspólnie przez firmę Microsoft i firmę Adobe Corporation. Czcionki OpenType i usługi systemu operacyjnego, które obsługują czcionki OpenType, umożliwiają użytkownikom prostą metodę instalowania i używania czcionek, niezależnie od tego, czy [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] czcionki zawierają kontury czy CFF (PostScript).  
  
 Format czcionki OpenType rozwiązuje następujące wyzwania dla deweloperów:  
  
- Szersze wsparcie dla wielu platform.  
  
- Lepsza obsługa międzynarodowych zestawów znaków.  
  
- Lepsza ochrona danych czcionki.  
  
- Mniejsze rozmiary plików, aby zwiększyć efektywność rozkładu czcionek.  
  
- Szersze wsparcie dla zaawansowanej kontrolki typograficznej.  
  
> [!NOTE]
> Windows SDK zawiera zestaw przykładowych czcionek OpenType, których można używać z [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacjami. Czcionki te zawierają większość funkcji przedstawionych w pozostałej części tego tematu. Aby uzyskać więcej informacji, zobacz [przykładowy pakiet czcionek OpenType](sample-opentype-font-pack.md).  
  
 Zobacz [specyfikację OpenType](https://go.microsoft.com/fwlink/?LinkId=96731) , aby uzyskać szczegółowe informacje o formacie czcionki OpenType.  
  
### <a name="advanced-typographic-extensions"></a>Zaawansowane rozszerzenia typograficzne  
 Zaawansowane tabele typograficzne (tabele układu OpenType) zwiększają funkcjonalność czcionek z [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] lub CFF konspektów. Czcionki układu OpenType zawierają dodatkowe informacje, które rozszerzają możliwości czcionek w celu zapewnienia obsługi wysokiej jakości międzynarodowej typografii. Większość czcionek OpenType uwidacznia tylko podzestaw łącznej liczby dostępnych funkcji OpenType. Czcionki OpenType zapewniają następujące funkcje.  
  
- Rozbudowane mapowanie między znakami i symbolami, które obsługują ligatury, formularze pozycyjne, alternatywy i inne podstawianie czcionek.  
  
- Obsługa dwuwymiarowego pozycjonowania i załącznika symboli.  
  
- Jawne informacje o skrypcie i języku zawarte w czcionce, dzięki czemu aplikacja do przetwarzania tekstu może odpowiednio dostosować swoje zachowanie.  
  
 Tabele układu OpenType są opisane bardziej szczegółowo w sekcji ["tabele plików czcionek"](https://www.microsoft.com/typography/otspec/otff.htm) specyfikacji OpenType.  
  
 W pozostałej części tego omówienia przedstawiono zakres i elastyczność niektórych wizualnie atrakcyjnych funkcji OpenType, które są udostępniane przez właściwości <xref:System.Windows.Documents.Typography> obiektu. Aby uzyskać więcej informacji na temat tego obiektu, zobacz [Typografia klasy](#typography_class).  
  
<a name="variants"></a>   
## <a name="variants"></a>elementy Variant  
 Warianty są używane do renderowania różnych stylów typograficznych, takich jak indeks górny i dolny.  
  
### <a name="superscripts-and-subscripts"></a>Indeksy górne i dolne  
 <xref:System.Windows.Documents.Typography.Variants%2A> Właściwość umożliwia ustawianie wartości indeksu górnego i dolnego dla czcionki OpenType.  
  
 Poniższy tekst wyświetla górne indeksy dla czcionki Palatino Linotype.  
  
 ![Tekst przy użyciu górnych skryptów OpenType](./media/opentype-font-features/opentype-superscripts.gif "Tekst przy użyciu górnych skryptów OpenType")  
  
 Poniższy przykład znacznika pokazuje, jak definiować indeks górny dla czcionki Palatino Linotype przy użyciu właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 Poniższy tekst przedstawia indeksy dla czcionki Palatino Linotype.  
  
 ![Tekst używający indeksów OpenType](./media/opentype-font-features/opentype-subscripts.gif "Tekst używający indeksów OpenType")  
  
 Poniższy przykład znacznika ilustruje sposób definiowania indeksów dolnych dla czcionki Palatino Linotype, przy użyciu właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a>Dekoracyjne zastosowania górnych skryptów i indeksów dolnych  
 Można również użyć górnych skryptów i indeksów dolnych, aby utworzyć ozdobne efekty mieszanego przypadku tekstu. Poniższy tekst wyświetla indeks górny i dolny dla czcionki Palatino Linotype. Należy pamiętać, że nie ma to żadnego na wielkie litery.  
  
 ![Tekst przy użyciu górnych skryptów OpenType i indeksów dolnych](./media/opentype-font-features/opentype-superscripts-subscripts.gif "Tekst przy użyciu górnych skryptów OpenType i indeksów dolnych")  

 Poniższy przykład znacznika pokazuje, jak definiować indeksy górne i dolne dla czcionki przy użyciu właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>   
## <a name="capitals"></a>Wersalików  
 Wielkie litery są zestawem form typograficznych, które renderują tekst w symbolach z stylem wielkiej litery. Zwykle, gdy tekst jest renderowany jako wersaliki, odstępy między literami mogą pojawić się zbyt przylegle, a waga i proporcja liter są zbyt duże. OpenType obsługuje wiele formatów stylów dla wielkich liter, w tym małych wersalików, wyświetlanie małychów, tytułów i wielkich liter. Te formaty stylów umożliwiają kontrolowanie wyglądu wielkich liter.  
  
 Następujący tekst zawiera standardowe litery dla czcionki Pescadero, a następnie litery, które są pisane jako "SmallCaps" i "AllSmallCaps". W takim przypadku ten sam rozmiar czcionki jest używany dla wszystkich trzech wyrazów.  
  
 ![Tekst używający wersalików OpenType](./media/opentype-font-features/opentype-capitals.gif "Tekst używający wersalików OpenType")  
  
 Poniższy przykład znacznika pokazuje, jak definiować wielkie litery dla czcionki Pescadero przy użyciu właściwości <xref:System.Windows.Documents.Typography> obiektu. Gdy używany jest format "SmallCaps", każda wiodąca litera jest ignorowana.  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a>Wielkie litery  
 Wielkie litery są lżejsze i proporcjonalne i zaprojektowane w celu uzyskania bardziej eleganckiego wyglądu niż zwykłych wersalików. Litery nagłówkowe są zwykle używane w większych rozmiarach czcionki jako nagłówki. Poniższy tekst przedstawia zwykłe i tytułowe wersaliki dla czcionki Pescadero. Zauważ, że węższe szerokości łodyg tekstu w drugim wierszu.  
  
 ![Tekst przy użyciu inicjałów z tytułami OpenType](./media/opentype-font-features/opentype-titling-capitals.gif "Tekst przy użyciu inicjałów z tytułami OpenType")  
  
 Poniższy przykład znacznika ilustruje sposób definiowania tytułów wersalików dla czcionki Pescadero przy użyciu właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet17](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a>Odstępy w Wielkiej litery  
 Interlinia to funkcja, która pozwala na zapewnienie większej ilości interlinii w przypadku używania wersalików w tekście. Wielkie litery są zwykle przeznaczone do mieszania z małymi literami. Odstępy, które pojawiają się w sposób atrakcyjny od litery i małe litery, mogą wyglądać zbyt mocno, gdy są używane wszystkie wielkie litery. Poniższy tekst przedstawia normalne i wielkie litery dla czcionki Pescadero.  
  
 ![Tekst używający odstępów w postaci OpenType](./media/opentype-font-features/opentype-capital-spacing.gif "Tekst używający odstępów w postaci OpenType")  
 
 Poniższy przykład znacznika pokazuje, jak zdefiniować odstępy dla czcionki Pescadero przy użyciu właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet18](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>   
## <a name="ligatures"></a>Ligatur  
 Ligatury to dwa lub więcej symboli, które są tworzone w pojedynczym symbolu, aby można było utworzyć bardziej czytelny lub atrakcyjny tekst. Czcionki OpenType obsługują cztery typy ligatur:  
  
- **Ligatury standardowe**. Zaprojektowano w celu zwiększenia czytelności. Ligatury standardowe obejmują "Fi", "FL" i "FF".  
  
- **Ligatury kontekstowe**. Zaprojektowana w celu zwiększenia czytelności przez zapewnienie lepszego łączenia między znakami, które składają się na ligatury.  
  
- **Ligatury ozdobne**. Zaprojektowana jako ozdobna i nie została zaprojektowana z myślą o czytelności.  
  
- **Ligatury historyczne**. Zaprojektowana tak, aby była historyczna i nie została zaprojektowana z myślą o czytelności.  
  
 Poniższy tekst przedstawia standardowe symbole ligatur dla czcionki Pericles.  
  
 ![Tekst korzystający z ligatur standardowych OpenType](./media/opentype-font-features/opentype-standard-ligatures.gif "Tekst korzystający z ligatur standardowych OpenType")  
  
 Poniższy przykład znacznika pokazuje, jak definiować standardowe symbole ligatur dla czcionki Pericles przy użyciu właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 Poniższy tekst przedstawia własne symbole ligatury dla czcionki Pericles.  
  
 ![Tekst wykorzystujący Ligatury ozdobne OpenType](./media/opentype-font-features/opentype-discretionary-ligatures.gif "Tekst wykorzystujący Ligatury ozdobne OpenType")  
  
 Poniższy przykład znacznika pokazuje, jak definiować glify ligatury dla czcionki Pericles przy użyciu właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 Domyślnie czcionki OpenType w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] włączają Ligatury standardowe. Na przykład jeśli używasz czcionki Palatino Linotype, standardowe ligatury "Fi", "FF" i "FL" są wyświetlane jako symbol połączonego znaku. Należy zauważyć, że para znaków dla każdej standardowej ligatury dotyka siebie nawzajem.  
  
 ![Tekst korzystający z ligatur standardowych OpenType z Palatino Linotype](./media/opentype-font-features/opentype-standard-ligatures-palatino.gif "Tekst korzystający z ligatur standardowych OpenType z Palatino Linotype")    
   
 Można jednak wyłączyć standardowe ligatury, aby standardowe ligatury, takie jak "FF", były wyświetlane jako dwa oddzielne glify, a nie jako symbol symbolu połączonego.  
  
 ![Tekst używający wyłączonych ligatur standardowych OpenType](./media/opentype-font-features/disabled-opentype-standard-ligatures.gif "Tekst używający wyłączonych ligatur standardowych OpenType")  
    
 Poniższy przykład znacznika pokazuje, jak wyłączyć standardowe symbole ligatur dla czcionki Linotype Palatino, używając właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>   
## <a name="swashes"></a>Znaki kaligraficzne  
 Znaki kaligraficzne to dekoracyjne glify, które używają wyrafinowanych elementów ozdobnych często skojarzonych z Calligraphy. Poniższy tekst zawiera standardowe i kaligraficzne glify dla czcionki Pescadero.  
  
 ![Tekst korzystający z symboli standardowych i kaligraficzne OpenType](./media/opentype-font-features/opentype-standard-swash-glyphs.gif "Tekst korzystający z symboli standardowych i kaligraficzne OpenType")  

 Znaki kaligraficzne są często używane jako elementy dekoracyjne w krótkich frazach, takich jak anonse zdarzeń. Poniższy tekst używa znaków kaligraficzne, aby wyróżnić wielkie litery nazwy zdarzenia.  
  
 ![Tekst z użyciem kaligraficzne OpenType](./media/opentype-font-features/opentype-swashes.gif "Tekst z użyciem kaligraficzne OpenType")  
  
 Poniższy przykład znacznika pokazuje, jak definiować znaki kaligraficzne dla czcionki przy użyciu właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a>Kontekstowe znaki kaligraficzne  
 Niektóre kombinacje symboli kaligraficzne mogą spowodować nieatrakcyjny wygląd, na przykład nakładające się dolne na sąsiednie litery. Użycie kontekstowego elementu kaligraficzne pozwala na użycie zastępczego glifu kaligraficzne, który zapewnia lepszy wygląd. Poniższy tekst zawiera ten sam wyraz przed i po zastosowaniu kontekstowego elementu kaligraficzne.  
  
 ![Tekst wykorzystujący znaki kaligraficzne kontekstowe OpenType](./media/opentype-font-features/opentype-contextual-swashes.gif "Tekst wykorzystujący znaki kaligraficzne kontekstowe OpenType")  
  
 Poniższy przykład znacznika pokazuje, jak zdefiniować kontekstowe znaki kaligraficzne dla czcionki Pescadero przy użyciu właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet16](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>   
## <a name="alternates"></a>Wersje alternatywne  
 Alternatywy są glifami, które można zastąpić symbolem standardowym. Czcionki OpenType, takie jak czcionka Pericles używana w poniższych przykładach, mogą zawierać alternatywne glify, których można użyć do tworzenia różnych wyglądów tekstu. Poniższy tekst wyświetla standardowe glify dla czcionki Pericles.  
  
 ![Tekst przy użyciu standardowych symboli OpenType](./media/opentype-font-features/opentype-standard-glyphs.gif "Tekst przy użyciu standardowych symboli OpenType")  

 Czcionka Pericles OpenType zawiera dodatkowe glify, które udostępniają alternatywy stylistyczne dla standardowego zestawu symboli. Następujący tekst zawiera stylistyczne glify alternatywne.  
  
 ![Tekst przy użyciu alternatywnych symboli OpenType](./media/opentype-font-features/opentype-stylistic-alternate-glyphs.gif "Tekst przy użyciu alternatywnych symboli OpenType")  
  
 Poniższy przykład znacznika pokazuje, jak definiować alternatywne glify dla czcionki Pericles przy użyciu właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 Poniższy tekst zawiera kilka innych glifów alternatywnych dla czcionki Pericles.  
  
 ![Tekst korzystający z stylistycznych alternatywnych symboli OpenType dla czcionki Pericles](./media/opentype-font-features/opentype-stylistic-alternate-glyphs-pericles.gif "Tekst korzystający z stylistycznych alternatywnych symboli OpenType dla czcionki Pericles")

 Poniższy przykład znacznika pokazuje, jak zdefiniować te inne glify alternatywne.  
  
 [!code-xaml[OpenTypeFontSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a>Losowe alternatywy kontekstowe  
 Losowe alternatywy kontekstowe zapewniają wiele zastępczych glifów dla pojedynczego znaku. W przypadku zaimplementowania za pomocą czcionek typu Script funkcja ta umożliwia symulowanie pisma ręcznego przy użyciu zestawu losowo wybranych glifów z niewielkimi różnicami w wyglądzie. Następujący tekst używa losowych kontekstowych alternatyw dla czcionki Lindsey. Zauważ, że litera "a" różni się nieco w wyglądzie  
  
 ![Tekst używający losowych alternatyw kontekstowych OpenType](./media/opentype-font-features/opentype-random-contextual-alternates.gif "Tekst używający losowych alternatyw kontekstowych OpenType")  
  
 Poniższy przykład znacznika pokazuje, jak zdefiniować losowe alternatywy kontekstowe dla czcionki Lindsey przy użyciu właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet20](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a>Formularze historyczne  
 Formularze historyczne to konwencje typograficzne, które były wspólne w przeszłości. Poniższy tekst przedstawia frazę "Boston, Massachusetts", używając historycznej formy symboli dla czcionki Palatino Linotype.  
  
 ![Tekst korzystający z formularzy historycznych OpenType](./media/opentype-font-features/opentype-historical-forms.gif "Tekst korzystający z formularzy historycznych OpenType")  
   
 Poniższy przykład znacznika pokazuje, jak definiować formularze historyczne dla czcionki Palatino Linotype przy użyciu właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>   
## <a name="numerical-styles"></a>Style liczbowe  
 Czcionki OpenType obsługują dużą liczbę funkcji, które mogą być używane z wartościami liczbowymi w tekście.  
  
### <a name="fractions"></a>Ułamki  
 Czcionki OpenType obsługują style dla ułamków, w tym kreski ukośne i ułożone na stosie.  
  
 Poniższy tekst wyświetla style ułamków dla czcionki Linotype Palatino.  
  
 ![Tekst przy użyciu ukośników OpenType i skumulowanych ułamkowych](./media/opentype-font-features/opentype-slashed-stacked-fractions.gif "Tekst przy użyciu ukośników OpenType i skumulowanych ułamkowych")  
   
 Poniższy przykład znacznika ilustruje sposób definiowania stylów ułamków dla czcionki Palatino Linotype, przy użyciu właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a>Stare cyfry stylów  
 Czcionki OpenType obsługują stary format liczbowy stylu. Ten format jest przydatny do wyświetlania liczb w stylach, które nie są już standardowe. Następujący tekst przedstawia 18-dniową datę w formatach liczbowych w stylu Standard i Old dla czcionki Palatino Linotype.  
  
 ![Tekst używający cyfr w starym stylu OpenType](./media/opentype-font-features/opentype-old-style-numerals.gif "Tekst używający cyfr w starym stylu OpenType")  
    
 Poniższy tekst wyświetla standardowe cyfry dla czcionki Linotype Palatino, a następnie stare cyfry stylów.  
  
 ![Tekst korzystający ze starych zestawów liczbowych stylów OpenType](./media/opentype-font-features/opentype-old-style-numeral-sets.gif "Tekst korzystający ze starych zestawów liczbowych stylów OpenType")  
  
 Poniższy przykład znacznika pokazuje, jak zdefiniować stare cyfry stylów dla czcionki Linotype Palatino, używając właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a>Wartości proporcjonalne i tabelaryczne  
 Czcionki OpenType obsługują funkcję proporcjonalnej i tabelaryczną, która kontroluje wyrównanie szerokości przy użyciu cyfr. Proporcjonalne liczby traktują każdą cyfrę jako mającą inną szerokość — "1" jest węższe niż "5". Liczby tabelaryczne są traktowane jako cyfry o równej szerokości, aby były wyrównane pionowo, co zwiększa czytelność informacji o typie finansowym.  
  
 Poniższy tekst przedstawia dwie proporcjonalne cyfry w pierwszej kolumnie przy użyciu czcionki Miramonte. Zwróć uwagę na różnicę między cyframi "5" i "1". W drugiej kolumnie są wyświetlane te same wartości liczbowe o szerokościach skorygowanych przy użyciu funkcji tabelarycznej.  
  
 ![Tekst przy użyciu proporcji OpenType & tabelarycznych](./media/opentype-font-features/opentype-proportional-tabular-figures.gif "Tekst przy użyciu proporcji OpenType i tabelarycznych")  
    
 Poniższy przykład znacznika ilustruje sposób definiowania proporcjonalnych i tabelarycznych liczb dla czcionki Miramonte przy użyciu właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet19](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a>Zero ukośnikiem  
 Czcionki OpenType obsługują ukośnik o zerowej liczbie znaków, aby wyróżnić różnicę między literą "O" i cyfrą "0". Liczbowa wartość zerowa jest często używana w przypadku identyfikatorów w danych finansowych i firmowych.  
  
 Poniższy tekst przedstawia przykładowy identyfikator kolejności przy użyciu czcionki Miramonte. Pierwszy wiersz używa standardowych liczb. Drugi wiersz używa ukośników o wartości zero, aby zapewnić lepszy kontrast z wielką literą "O".  
  
 ![Tekst korzystający z zer z ukośnikiem OpenType](./media/opentype-font-features/opentype-slashed-zero-numerals.gif "Tekst korzystający z zer z ukośnikiem OpenType")  
    
 Poniższy przykład znacznika pokazuje, jak zdefiniować ukośniki zerowe dla czcionki Miramonte przy użyciu właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>   
## <a name="typography-class"></a>Klasa typografii  
 <xref:System.Windows.Documents.Typography> Obiekt uwidacznia zestaw funkcji, które obsługuje czcionka OpenType. Ustawiając właściwości <xref:System.Windows.Documents.Typography> w znacznikach, można łatwo tworzyć dokumenty, które korzystają z funkcji OpenType.  
  
 Następujący tekst zawiera standardowe litery dla czcionki Pescadero, a następnie litery, które są pisane jako "SmallCaps" i "AllSmallCaps". W takim przypadku ten sam rozmiar czcionki jest używany dla wszystkich trzech wyrazów.  
  
 ![Tekst używający wersalików OpenType](./media/opentype-font-features/opentype-capitals.gif "Tekst używający wersalików OpenType")  
    
 Poniższy przykład znacznika pokazuje, jak definiować wielkie litery dla czcionki Pescadero przy użyciu właściwości <xref:System.Windows.Documents.Typography> obiektu. Gdy używany jest format "SmallCaps", każda wiodąca litera jest ignorowana.  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 Poniższy przykład kodu wykonuje to samo zadanie jak w poprzednim przykładzie znaczników.  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a>Właściwości klasy typografii  
 W poniższej tabeli wymieniono właściwości, wartości i ustawienia <xref:System.Windows.Documents.Typography> domyślne obiektu.  
  
|Właściwość|Wartość (s)|Wartość domyślna|  
|--------------|----------------|-------------------|  
|<xref:System.Windows.Documents.Typography.AnnotationAlternates%2A>|Wartość liczbowa-bajt|0|  
|<xref:System.Windows.Documents.Typography.Capitals%2A>|<xref:System.Windows.FontCapitals.AllPetiteCaps> &#124; <xref:System.Windows.FontCapitals.AllSmallCaps> &#124; <xref:System.Windows.FontCapitals.Normal> &#124; <xref:System.Windows.FontCapitals.PetiteCaps> &#124; <xref:System.Windows.FontCapitals.SmallCaps> &#124; <xref:System.Windows.FontCapitals.Titling> &#124; <xref:System.Windows.FontCapitals.Unicase>|<xref:System.Windows.FontCapitals.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.CapitalSpacing%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.CaseSensitiveForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.ContextualAlternates%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualSwashes%2A>|Wartość liczbowa-bajt|0|  
|<xref:System.Windows.Documents.Typography.DiscretionaryLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianExpertForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianLanguage%2A>|<xref:System.Windows.FontEastAsianLanguage.HojoKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis04> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis78> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis83> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis90> &#124; <xref:System.Windows.FontEastAsianLanguage.NlcKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Normal> &#124; <xref:System.Windows.FontEastAsianLanguage.Simplified> &#124; <xref:System.Windows.FontEastAsianLanguage.Traditional> &#124; <xref:System.Windows.FontEastAsianLanguage.TraditionalNames>|<xref:System.Windows.FontEastAsianLanguage.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.EastAsianWidths%2A>|<xref:System.Windows.FontEastAsianWidths.Full> &#124; <xref:System.Windows.FontEastAsianWidths.Half> &#124; <xref:System.Windows.FontEastAsianWidths.Normal> &#124; <xref:System.Windows.FontEastAsianWidths.Proportional> &#124; <xref:System.Windows.FontEastAsianWidths.Quarter> &#124; <xref:System.Windows.FontEastAsianWidths.Third>|<xref:System.Windows.FontEastAsianWidths.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.Fraction%2A>|<xref:System.Windows.FontFraction.Normal> &#124; <xref:System.Windows.FontFraction.Slashed> &#124; <xref:System.Windows.FontFraction.Stacked>|<xref:System.Windows.FontFraction.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.HistoricalForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.HistoricalLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Kerning%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.MathematicalGreek%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.NumeralAlignment%2A>|<xref:System.Windows.FontNumeralAlignment.Normal> &#124; <xref:System.Windows.FontNumeralAlignment.Proportional> &#124; <xref:System.Windows.FontNumeralAlignment.Tabular>|<xref:System.Windows.FontNumeralAlignment.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.NumeralStyle%2A>|<xref:System.Boolean>|<xref:System.Windows.FontNumeralStyle.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.SlashedZero%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StandardLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.StandardSwashes%2A>|wartość liczbowa — bajt|0|  
|<xref:System.Windows.Documents.Typography.StylisticAlternates%2A>|wartość liczbowa — bajt|0|  
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
|<xref:System.Windows.Documents.Typography.Variants%2A>|<xref:System.Windows.FontVariants.Inferior> &#124; <xref:System.Windows.FontVariants.Normal> &#124; <xref:System.Windows.FontVariants.Ordinal> &#124; <xref:System.Windows.FontVariants.Ruby> &#124; <xref:System.Windows.FontVariants.Subscript> &#124; <xref:System.Windows.FontVariants.Superscript>|<xref:System.Windows.FontVariants.Normal?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Documents.Typography>
- [Specyfikacja OpenType](https://go.microsoft.com/fwlink/?LinkId=96731)
- [Typografia w WPF](typography-in-wpf.md)
- [Przykład pakietu czcionek OpenType](sample-opentype-font-pack.md)
- [Pakowanie czcionek z aplikacjami](packaging-fonts-with-applications.md)
