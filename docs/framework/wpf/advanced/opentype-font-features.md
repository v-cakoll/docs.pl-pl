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
ms.openlocfilehash: b96ad3266ce32a26af573a3a35392518055df37f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376952"
---
# <a name="opentype-font-features"></a>OpenType funkcje czcionki
W tym temacie omówiono niektóre kluczowe funkcje [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] technologia czcionek w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  

  
<a name="overview"></a>   
## <a name="opentype-font-format"></a>Format czcionek OpenType  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Format czcionki jest rozszerzeniem [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] format czcionek, dodanie obsługi danych czcionki PostScript. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Format czcionek została opracowana wspólnie przez [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] i Adobe Corporation. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki i systemu operacyjnego usług, które obsługują [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki udostępniają użytkownikom prostą metodę do zainstalowania i używania czcionki, czy zawierają czcionek [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] konturów lub opisanych CFF (PostScript).  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Format czcionek dotyczy następujących problemów dla deweloperów:  
  
-   Szerszy Obsługa wielu platform.  
  
-   Lepsza obsługa zestawów znaków międzynarodowych.  
  
-   Lepsza ochrona danych czcionki.  
  
-   Mniejsze pliki dokonanie dystrybucji czcionki bardziej wydajne.  
  
-   Szerszy Obsługa formantu związane z typografią zaawansowanego.  
  
> [!NOTE]
>  Zestaw Windows SDK zawiera zestaw przykładowych [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionek, które można używać z [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji. Czcionki te zapewniają większość funkcji przedstawionych w dalszej części tego tematu. Aby uzyskać więcej informacji, zobacz [przykład pakietu czcionek OpenType](sample-opentype-font-pack.md).  
  
 Zobacz [specyfikacji OpenType](https://go.microsoft.com/fwlink/?LinkId=96731) szczegóły dotyczące [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] format czcionek.  
  
### <a name="advanced-typographic-extensions"></a>Zaawansowane rozszerzenia związane z typografią  
 Zaawansowane związane z typografią tabel ([!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] tabele układu) rozszerzają funkcjonalność czcionek z oboma [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] lub CFF konturów. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Układ czcionki zawierają dodatkowe informacje, które rozszerza możliwości czcionek w celu obsługi międzynarodowej typografii wysokiej jakości. Większość [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki uwidaczniać tylko podzbiór całkowitej [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] dostępne funkcje. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki zapewniają następujące funkcje.  
  
-   Zaawansowane mapowanie między znaki i symbole, które obsługują ligatur, pozycyjne, zastępcy i innych podstawienia czcionki.  
  
-   Obsługa dwuwymiarową załącznika pozycjonowanie i symboli.  
  
-   Jawne skryptu i język informacje w czcionki, więc aplikacja przetwarzanie tekstu można odpowiednio dostosować jego zachowanie.  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Tabele są opisane bardziej szczegółowo w ["Czcionki pliku tabele"](https://www.microsoft.com/typography/otspec/otff.htm) części [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] specyfikacji.  
  
 W pozostałej części tego omówienia wprowadza szerokością i elastyczności niektórych — wizualnie [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] funkcje, które są udostępniane przez właściwości <xref:System.Windows.Documents.Typography> obiektu. Aby uzyskać więcej informacji na temat tego obiektu, zobacz [klasy typografii](#typography_class).  
  
<a name="variants"></a>   
## <a name="variants"></a>elementy Variant  
 Warianty są używane do renderowania różnych stylów związane z typografią, takie jak indeks górny i dolny.  
  
### <a name="superscripts-and-subscripts"></a>Indeksy górne i dolne  
 <xref:System.Windows.Documents.Typography.Variants%2A> Właściwość można ustawić wartości indeksach górnym i dolnym [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki.  
  
 Następujący tekst Wyświetla indeksów górnych Book Antiqua czcionki.  
  
 ![Tekst przy użyciu indeksów górnych OpenType](./media/opentypefont14.gif "opentypefont14")  
Tekst przy użyciu indeksów górnych OpenType  
  
 W poniższym przykładzie znaczników pokazuje jak zdefiniować indeks górny czcionki Book Antiqua, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 Następujący tekst Wyświetla indeksy dolne Book Antiqua czcionki.  
  
 ![Tekst indeksy dolne OpenType](./media/opentypefont15.gif "opentypefont15")  
Tekst indeksy dolne OpenType  
  
 W poniższym przykładzie znaczników pokazuje jak zdefiniować indeksy dolne czcionki Book Antiqua, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a>Zastosowań dekoracyjne indeksy górne i dolne  
 Indeks górny i dolny można również użyć do tworzenia efektów ozdobnych mieszanej wielkości liter tekstu. Następujący tekst Wyświetla czcionki Book Antiqua indeksach górnym i tekst. Należy pamiętać, zasady nie wpływają literami.  
  
 ![Tekst przy użyciu indeksy OpenType górne i dolne](./media/opentypefont16.gif "opentypefont16")  
Tekst przy użyciu indeksy OpenType górne i dolne  
  
 W poniższym przykładzie znaczników pokazuje jak zdefiniować indeks górny i dolny czcionek, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>   
## <a name="capitals"></a>W przypadku  
 W przypadku to zbiór typograficzne formularzy, które renderowanie tekstu w symbole różne wielkiej litery. Zazwyczaj, gdy tekst jest renderowane jako wielkimi literami, odstępów między literami może znajdować się zbyt ściśle i wagi, jak i część zbyt duże litery. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] obsługuje wiele formatów stylów dla wielkich liter, w tym kapitalików, wersalików, warianty kapitałowych odstępy i. Te formaty stylów umożliwiają kontrolowanie wyglądu literami.  
  
 Następujący tekst, wyświetla standardowe wielkimi literami czcionki Pescadero, a następnie liter jako "SmallCaps" i "AllSmallCaps". W takich przypadkach taki sam rozmiar czcionki jest używany dla wszystkich trzech słów.  
  
 ![Tekst, wielkie litery OpenType](./media/opentypefont11.gif "opentypefont11")  
Tekst, wielkie litery OpenType  
  
 W poniższym przykładzie znaczników pokazuje jak zdefiniować w przypadku czcionek Pescadero, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu. Gdy używany jest format "SmallCaps", jest ignorowany wiodących wielkiej litery.  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a>Wersalików  
 Stolice tytułowe są jaśniejsze udział i wagi i jest przeznaczona do bardziej elegancki wygląd niż w przypadku normalnych. Stolice tytułowe są zazwyczaj używane w większego rozmiaru czcionki w nagłówkach. Następujący tekst wyświetlany w przypadku normalnych i tytułowe czcionki Pescadero. Zwróć uwagę, mniejszą niż szerokość stem, tekst w drugim wierszu.  
  
 ![Tekst przy użyciu OpenType wersalików](./media/opentypefont20.gif "OpenTypeFont20")  
Tekst przy użyciu wersalików OpenType  
  
 W poniższym przykładzie znaczników pokazuje jak zdefiniować tytułowe w przypadku czcionek Pescadero, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet17](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a>Odstępy kapitałowych  
 Odstępy kapitałowych to funkcja, która pozwala na dostarczenie więcej odstępów, korzystając z wielkimi literami w tekście. Wielkie litery zwykle są przeznaczone do programu blend z małych liter. Odstępy, który pojawia się atrakcyjny między i Wielkiej litery i małe litery, może być zbyt ściśle stosowania wpisany tylko wielkimi literami. Następujący tekst Wyświetla odstępy w normalnym i kapitałowych czcionki Pescadero.  
  
 ![Tekst przy użyciu odstępy kapitałowych OpenType](./media/opentypefont21.gif "OpenTypeFont21")  
Tekst przy użyciu odstępy kapitałowych OpenType  
  
 W poniższym przykładzie znaczników pokazuje jak zdefiniować kapitałowych odstępy czcionki Pescadero, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet18](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>   
## <a name="ligatures"></a>Ligatur  
 Ligatury są co najmniej dwóch symbole, utworzonych w jednym symbol, aby można było utworzyć bardziej czytelne i atrakcyjność tekstu. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki obsługuje cztery rodzaje ligatur:  
  
-   **Ligatury**. Zaprojektowana w celu zwiększenia czytelności. Ligatury obejmują "fi", "mazowieckie" i "ff".  
  
-   **Kontekstowe ligatur**. Zaprojektowana, aby zwiększyć czytelność, zapewniając lepszy zachowanie między znakami, które tworzą ligatury.  
  
-   **Ligatury**. Przeznaczony do ozdobnych i nie są specjalnie zaprojektowane dla czytelności.  
  
-   **Ligatur historycznych**. Zaprojektowana jako historycznych i nie są specjalnie zaprojektowane dla czytelności.  
  
 Następujący tekst Wyświetla standardowe ligatury symbole dla czcionki Perykles.  
  
 ![Tekst przy użyciu ligatury OpenType](./media/opentypefont04.gif "opentypefont04")  
Tekst standardowe ligatury OpenType  
  
 W poniższym przykładzie znaczników pokazuje jak zdefiniować symbole standardowe ligatury czcionki Perykles, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 Następujący tekst Wyświetla symbole poufnej ligatury Perykles czcionki.  
  
 ![Tekst przy użyciu ligatury OpenType](./media/opentypefont05.gif "opentypefont05")  
Tekst przy użyciu ligatury OpenType  
  
 W poniższym przykładzie znaczników pokazuje jak zdefiniować symbole poufnej ligatury czcionki Perykles, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 Domyślnie [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionek w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Włącz ligatury. Na przykład jeśli używasz czcionki Book Antiqua, ligatury "fi", "ff" i "mazowieckie" są wyświetlane jako symbol znaku połączone. Należy zauważyć, że pary znaków dla każdego standardowe ligatury stykają.  
  
 ![Tekst przy użyciu ligatury OpenType](./media/opentypefont06.gif "opentypefont06")  
Tekst standardowe ligatury OpenType  
  
 Jednak można wyłączyć ligatury standardowe funkcje, dzięki czemu standardowe ligatury, takie jak "ff" przedstawia jako dwa osobne symbole, a nie jako symbol znaku połączone.  
  
 ![Przy użyciu tekstu wyłączone ligatury OpenType](./media/opentypefont07.gif "opentypefont07")  
Tekst przy użyciu wyłączonych ligatury OpenType  
  
 W poniższym przykładzie znaczników pokazuje, jak wyłączyć ligatury standardowe symbole dla czcionki Book Antiqua, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>   
## <a name="swashes"></a>Kaligraficzne  
 Kaligraficzne są symbole dekoracyjnych, korzystających z rozbudowanych ornamentacji często skojarzony kaligrafia. Następujący tekst, wyświetla standardowe i kaligraficzne symbole Pescadero czcionki.  
  
 ![Tekst z użyciem glifów standardowe i kaligraficzne OpenType](./media/opentypefont08.gif "opentypefont08")  
Tekst z użyciem glifów standardowe i kaligraficzne OpenType  
  
 Kaligraficzne są często używane jako to elementy dekoracyjne w krótkich fraz, takie jak Anonse zdarzeń. Następujący tekst używa kaligraficzne, aby podkreślić wielkie litery nazwy zdarzenia.  
  
 ![Tekst przy użyciu kaligraficzne OpenType](./media/opentypefont09.gif "opentypefont09")  
Tekst przy użyciu kaligraficzne OpenType  
  
 W poniższym przykładzie znaczników pokazuje jak zdefiniować kaligraficzne czcionek, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a>Kontekstowe kaligraficzne  
 Niektóre kombinacje symboli kaligrafii może spowodować nieatrakcyjnych wygląd, takich jak wydłużeń nakładających się od liter sąsiadująco. Za pomocą kontekstowego firmy swash umożliwia glif swash zastępczych, który daje lepsze wygląd. Następujący tekst zawiera samego wyrazu, przed i po zastosowaniu swash kontekstowych.  
  
 ![Tekst kontekstowe symbole kaligraficzne OpenType](./media/opentypefont19.gif "OpenTypeFont19")  
Tekst kontekstowe symbole kaligraficzne OpenType  
  
 W poniższym przykładzie znaczników pokazuje jak zdefiniować kontekstowych swash czcionki Pescadero, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet16](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>   
## <a name="alternates"></a>Wersje alternatywne  
 Wersje alternatywne są symbole, które mogą zastąpić standardowa symbol. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki, takie jak Perykles czcionkę w poniższych przykładach, mogą zawierać alternatywne symbole, używających inny wygląd tekstu. Następujący tekst Wyświetla standardowe symbole Perykles czcionki.  
  
 ![Tekst standardowe symbole OpenType](./media/opentypefont01.gif "opentypefont01")  
Tekst standardowe symbole OpenType  
  
 Perykles [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki zawiera dodatkowe symbole, zapewniających stylistyczne do standardowego zestawu symbole. Następujący tekst Wyświetla stylistyczne alternatywne symbole.  
  
 ![Tekst stylistyczne alternatywne symbole OpenType](./media/opentypefont02.gif "opentypefont02")  
Tekst stylistyczne alternatywne symbole OpenType  
  
 W poniższym przykładzie znaczników pokazuje jak zdefiniować stylistyczne alternatywnych symboli czcionki Perykles, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 Następujący tekst zawiera kilka innych stylistyczne alternatywnych symboli czcionki Perykles.  
  
 ![Tekst stylistyczne alternatywne symbole OpenType](./media/opentypefont03.gif "opentypefont03")  
Tekst stylistyczne alternatywne symbole OpenType  
  
 W poniższym przykładzie znaczników pokazuje jak zdefiniować tych innego stylistyczne alternatywnych symboli.  
  
 [!code-xaml[OpenTypeFontSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a>Losowe kontekstowe  
 Losowe kontekstowe zapewniają wiele symboli zastępczych dla pojedynczego znaku. Po wdrożeniu przy użyciu skryptu czcionki, tę funkcję można symulować pisma odręcznego za pomocą zestawu losowo wybranych symboli z niewielkimi różnicami w wyglądzie. Następujący tekst używa czcionki Lindsey losowe kontekstowe. Należy zauważyć, że literę "" różni się nieco w wyglądzie  
  
 ![Tekst przy użyciu losowego kontekstowe OpenType](./media/opentypefont23.gif "OpenTypeFont23")  
Tekst przy użyciu losowego kontekstowe OpenType  
  
 W poniższym przykładzie znaczników pokazuje jak zdefiniować losowe kontekstowe czcionki Lindsey, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet20](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a>Historyczne formularzy  
 Formularze historyczne są konwencje związane z typografią wspólnych w przeszłości. Następujący tekst Wyświetla frazy "Boston, Massachusetts", za pomocą historycznych formularza symbole Book Antiqua czcionki.  
  
 ![Tekst historyczne formy OpenType](./media/opentypefont10.gif "opentypefont10")  
Tekst historyczne formy OpenType  
  
 W poniższym przykładzie znaczników pokazuje jak zdefiniować historycznych formularzy dla czcionki Book Antiqua, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>   
## <a name="numerical-styles"></a>Style liczb  
 Czcionek OpenType obsługiwać dużą liczbę funkcji, które mogą być używane z wartości liczbowe w tekście.  
  
### <a name="fractions"></a>Użycie ułamkowych  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki obsługę ułamki, w tym przekreślonych i skumulowany style.  
  
 Następujący tekst Wyświetla ułamek style czcionki Book Antiqua.  
  
 ![Tekst przy użyciu OpenType ukośną i ułamki](./media/opentypefont12.gif "opentypefont12")  
Tekst przy użyciu OpenType ukośną i ułamki  
  
 W poniższym przykładzie znaczników pokazuje jak zdefiniować ułamek style czcionki Book Antiqua, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a>Stary rzymskie  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki pomocy technicznej ze starego Styl formatu liczb. Ten format jest użyteczny do wyświetlania liczb w style, które nie są już standardowych. Następujący tekst Wyświetla datę 18 wieku formaty liczb standardowe i stary styl czcionki Book Antiqua.  
  
 ![Tekst, w starym stylu antykwy OpenType](./media/opentypefont24.gif "OpenTypeFont24")  
Tekst, w starym stylu antykwy OpenType  
  
 Następujący tekst zawiera standardowe cyfry Book Antiqua czcionki, następuje w starym stylu antykwy.  
  
 ![Tekst przy użyciu OpenType stary styl zestawy liczb](./media/opentypefont13.gif "opentypefont13")  
Tekst przy użyciu OpenType stary styl zestawy liczb  
  
 W poniższym przykładzie znaczników pokazuje jak zdefiniować starym stylu antykwy czcionki Book Antiqua, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a>Proporcjonalne i tabelaryczne dane  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki obsługują funkcję rysunek proporcjonalne i tabelarycznym kontrolować wyrównanie szerokości, korzystając z cyfr. Rysunki proporcjonalna traktować poszczególnych liczb jako posiadające różne szerokość — "1" jest mniejsza niż "5". Dane tabelaryczne są traktowane jako równe szerokość cyfr, tak, aby były wyrównane w pionie, co zwiększa czytelność informacji o typie finansowych.  
  
 Następujący tekst Wyświetla dwóch liczb proporcjonalnych w pierwszej kolumnie przy użyciu czcionki Miramonte. Należy zanotować różnicę szerokość między cyfry "5" i "1". Druga kolumna zawiera ten sam dwóch wartości liczbowych przy użyciu szerokości dostosowane przy użyciu funkcji tabelarycznej rysunku.  
  
 ![Tekst przy użyciu OpenType proporcjonalne i tabelaryczne liczby](./media/opentypefont22.gif "OpenTypeFont22")  
Tekst, rysunki proporcjonalne i tabelarycznym OpenType  
  
 W poniższym przykładzie znaczników pokazuje jak zdefiniować proporcjonalne i tabelaryczne dane czcionki Miramonte, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet19](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a>Przekreślone Zero  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki obsługuje przekreślonych zero formatu liczb do wyróżnienia różnią się literą "O" i cyfry, "0". Przekreślonych zero liczb jest często używana dla identyfikatorów informacje finansowe i biznesowe.  
  
 Następujący tekst przedstawia przykładowy identyfikator zamówienia, przy użyciu czcionki Miramonte. Pierwszy wiersz używa standardowych cyfr. Drugi wiersz używane ukośną zero cyfr, aby zapewnić lepsze kontrast wielkiej litery "O".  
  
 ![Tekst przy użyciu OpenType ukośną zero cyfry](./media/opentypefont17.gif "OpenTypeFont17")  
Tekst przy użyciu OpenType ukośną zero cyfry  
  
 W poniższym przykładzie znaczników pokazuje jak zdefiniować ukośną zero cyfry czcionki Miramonte, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>   
## <a name="typography-class"></a>Klasa typografii  
 <xref:System.Windows.Documents.Typography> Obiekt udostępnia zestaw funkcji, [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] obsługuje czcionki. Przez ustawienie właściwości <xref:System.Windows.Documents.Typography> w znaczniku, można z łatwością twórz dokumentów, które wykorzystują [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] funkcji.  
  
 Następujący tekst, wyświetla standardowe wielkimi literami czcionki Pescadero, a następnie liter jako "SmallCaps" i "AllSmallCaps". W takich przypadkach taki sam rozmiar czcionki jest używany dla wszystkich trzech słów.  
  
 ![Tekst, wielkie litery OpenType](./media/opentypefont11.gif "opentypefont11")  
Tekst, wielkie litery OpenType  
  
 W poniższym przykładzie znaczników pokazuje jak zdefiniować w przypadku czcionek Pescadero, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu. Gdy używany jest format "SmallCaps", jest ignorowany wiodących wielkiej litery.  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 Poniższy przykład kodu w ramach tego samego zadania, jak w poprzednim przykładzie znaczników.  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a>Właściwości klasy typografii  
 W poniższej tabeli wymieniono właściwości, wartości i domyślne ustawienie opcji <xref:System.Windows.Documents.Typography> obiektu.  
  
|Właściwość|Wartości|Wartość domyślna|  
|--------------|----------------|-------------------|  
|<xref:System.Windows.Documents.Typography.AnnotationAlternates%2A>|Wartość liczbowa - bajtowych|0|  
|<xref:System.Windows.Documents.Typography.Capitals%2A>|<xref:System.Windows.FontCapitals.AllPetiteCaps> &#124; <xref:System.Windows.FontCapitals.AllSmallCaps> &#124; <xref:System.Windows.FontCapitals.Normal> &#124; <xref:System.Windows.FontCapitals.PetiteCaps> &#124; <xref:System.Windows.FontCapitals.SmallCaps> &#124; <xref:System.Windows.FontCapitals.Titling> &#124; <xref:System.Windows.FontCapitals.Unicase>|<xref:System.Windows.FontCapitals.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.CapitalSpacing%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.CaseSensitiveForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.ContextualAlternates%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualSwashes%2A>|Wartość liczbowa - bajtowych|0|  
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
|<xref:System.Windows.Documents.Typography.StandardSwashes%2A>|Wartość liczbowa — bajtów|0|  
|<xref:System.Windows.Documents.Typography.StylisticAlternates%2A>|Wartość liczbowa — bajtów|0|  
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
