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
ms.openlocfilehash: a8ee4107ee7db20f2948ea9a33ef853815a22665
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549607"
---
# <a name="opentype-font-features"></a>OpenType funkcje czcionki
W tym temacie omówiono niektóre z kluczowych funkcji usługi [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] technologii czcionek w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  

  
<a name="overview"></a>   
## <a name="opentype-font-format"></a>Format czcionek OpenType  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Format czcionki jest rozszerzeniem [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] format czcionki, dodawanie obsługi PostScript dane czcionek. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Format czcionki został opracowany przez wspólnie [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] i Adobe Corporation. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki i system operacyjny usług których [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki udostępniać użytkownikom prosty sposób instalacji i używania czcionki, czy czcionki zawierać [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] zawiera lub zawiera CFF (PostScript).  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Format czcionki uwzględniają następujące problemy developer:  
  
-   Szersze możliwości obsługi wielu platform.  
  
-   Lepszą obsługę międzynarodowego zestawu znaków.  
  
-   Lepszą ochronę danych czcionki.  
  
-   Mniejsze pliki dokonanie dystrybucji czcionki większą wydajność.  
  
-   Szerszych obsługę zaawansowanych związane z typografią formant.  
  
> [!NOTE]
>  Zestaw Windows SDK zawiera zestaw próbki [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionek, które można używać z [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji. Te czcionki zawierają większość funkcji zilustrowane w pozostałej części tego tematu. Aby uzyskać więcej informacji, zobacz [przykładowym pakiecie czcionek OpenType](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md).  
  
 Zobacz [specyfikacji OpenType](http://go.microsoft.com/fwlink/?LinkId=96731) informacji o [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] format czcionki.  
  
### <a name="advanced-typographic-extensions"></a>Zaawansowane rozszerzeń związane z typografią  
 Zaawansowane typograficznych tabele ([!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] tabele) rozszerzyć funkcjonalność czcionek przy użyciu jednej [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] lub CFF konturów. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Układ czcionki zawierają dodatkowe informacje, które rozszerza możliwości czcionki do obsługi międzynarodowej typografii wysokiej jakości. Większość [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionek narazić tylko podzbiór całkowitej [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] funkcje dostępne. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki zawierają następujące funkcje.  
  
-   Rozbudowane mapowanie między znaki oraz symbole, obsługujących ligatur, tj zastępców i innych podstawianie czcionek.  
  
-   Obsługa dwuwymiarowa załącznika pozycjonowanie i symboli.  
  
-   Jawne informacje skryptu i język zawarte w czcionki, dzięki aplikacji przetwarzanie tekstu odpowiednio zmienić jego zachowania.  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Tabele są opisane bardziej szczegółowo w ["Tabel plików czcionki"](http://www.microsoft.com/typography/otspec/otff.htm) sekcji [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] specyfikacji.  
  
 W pozostałej części w tym omówieniu przedstawiono szerokości i elastyczności niektórych-wizualnie [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] funkcje, które są dostępne w właściwości <xref:System.Windows.Documents.Typography> obiektu. Aby uzyskać więcej informacji dotyczących tego obiektu, zobacz [klasy typografii](#typography_class).  
  
<a name="variants"></a>   
## <a name="variants"></a>elementy Variant  
 Warianty są używane do renderowania różnych stylach typograficznych, takich jak indeksy górne i dolne.  
  
### <a name="superscripts-and-subscripts"></a>Indeksy górne i dolne  
 <xref:System.Windows.Documents.Typography.Variants%2A> Właściwości można ustawić wartości indeksu górnego i dolnego [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki.  
  
 Następujący tekst Wyświetla indeksów górnych Book Antiqua czcionki.  
  
 ![Tekst przy użyciu indeksów górnych OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont14.gif "opentypefont14")  
Tekst przy użyciu indeksów górnych OpenType  
  
 W poniższym przykładzie znaczników pokazano, jak zdefiniować indeksów górnych czcionki Book Antiqua, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 Następujący tekst Wyświetla indeksy dolne Book Antiqua czcionki.  
  
 ![Tekst przy użyciu dolnego OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont15.gif "opentypefont15")  
Indeksy dolne OpenType tekstu  
  
 W poniższym przykładzie znaczników pokazano, jak zdefiniować indeksy dolne czcionki Book Antiqua, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a>Ozdobne używa indeksu górnego i dolnego  
 Umożliwia także indeksy górne i dolne utworzyć ozdobne skutków wielkość tekstu mieszanego. Następujący tekst Wyświetla tekst indeksu górnego i dolnego Book Antiqua czcionki. Należy pamiętać, nie dotyczy wersalików.  
  
 ![Tekst przy użyciu OpenType indeksy górne i dolne](../../../../docs/framework/wpf/advanced/media/opentypefont16.gif "opentypefont16")  
Tekst przy użyciu OpenType indeksy górne i dolne  
  
 W poniższym przykładzie znaczników pokazano, jak zdefiniować indeksy górne i dolne czcionki, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>   
## <a name="capitals"></a>Literami  
 Wersalików to zbiór typograficzne formularze, które renderowania tekstu w wyglądzie kapitału symboli. Zwykle Po wyrenderowaniu tekstu jako wersaliki odstępów między literami może występować zbyt ścisłej i wagi, jak i część zbyt duże litery. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] obsługuje wiele formatów stylów literami, w tym kapitalików, małych wersalików, tytułowych i inwestycyjne odstępów. Formaty te style pozwala na kontrolowanie wyglądu wersalików.  
  
 Następujący tekst zawiera standardowe wielkimi literami czcionki Pescadero, a następnie liter jako "SmallCaps" i "AllSmallCaps". W takim przypadku ten sam rozmiar czcionki jest używany dla wszystkich trzech słów.  
  
 ![Tekst wielkie litery OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont11.gif "opentypefont11")  
Wielkie litery OpenType tekstu  
  
 W poniższym przykładzie znaczników pokazano, jak zdefiniować wersalików w przypadku czcionki Pescadero, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu. Gdy używany jest format "SmallCaps", wszystkie wiodące litera jest ignorowana.  
  
 [!code-xaml[OpenTypeFontSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a>Tytułowych wersalików  
 Wersalików tytułowe są jaśniejsze udział i wagi i zaprojektowane, aby nadać bardziej elegancki wygląd niż normalne wersalików. Wersalików tytułowe są zazwyczaj używane w większym rozmiarze czcionki w nagłówkach. Następujący tekst Wyświetla normalne i tytułowe wersalików w przypadku czcionki Pescadero. Zwróć uwagę, mniejszą niż szerokość stem tekst w drugim wierszu.  
  
 ![Tekst przy użyciu OpenType tytułowych wersalików](../../../../docs/framework/wpf/advanced/media/opentypefont20.gif "OpenTypeFont20")  
Tekst przy użyciu OpenType tytułowych wersalików  
  
 W poniższym przykładzie znaczników pokazano, jak zdefiniować tytułowe wersalików w przypadku czcionki Pescadero, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a>Odstępy kapitału  
 Odstępy kapitału jest funkcją, która umożliwia podanie więcej odstępów, korzystając z wielkimi literami w tekście. Wielkie litery mają zwykle blend z małych liter. Między wierszami, który pojawi się atrakcyjne między i się wielką literą i zawierać małą literę może wyglądać zbyt ścisłej stosowania wielkimi literami. Następujący tekst Wyświetla normalne i inwestycyjne odstępy Pescadero czcionki.  
  
 ![Tekst przy użyciu odstępy kapitału OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont21.gif "OpenTypeFont21")  
Tekst przy użyciu odstępy kapitału OpenType  
  
 W poniższym przykładzie znaczników pokazano, jak zdefiniować odstępy kapitału dla czcionki Pescadero, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>   
## <a name="ligatures"></a>Ligatur  
 Ligatury są dwa lub więcej symboli utworzonych w jednym symbolu, aby można było utworzyć bardziej czytelny i atrakcyjność tekstu. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki są obsługiwane cztery typy ligatur:  
  
-   **Ligatury**. Zaprojektowany w celu zwiększenia czytelności. Ligatury obejmują "fi", "fl" i "one".  
  
-   **Ligatury kontekstowe**. Zaprojektowana, aby zwiększyć czytelność, zapewniając lepszy zachowanie między znakami, które tworzą ligatury.  
  
-   **Ligatury**. Bardzo ozdobne, a nie są specjalnie zaprojektowane dla czytelności.  
  
-   **Ligatur historycznych**. Zaprojektowaną do historycznych i nie są specjalnie zaprojektowane dla czytelności.  
  
 Następujący tekst zawiera standardowe ligatury symboli czcionki Perykles.  
  
 ![Tekst przy użyciu ligatury OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont04.gif "opentypefont04")  
Tekst przy użyciu ligatury OpenType  
  
 W poniższym przykładzie znaczników pokazano, jak zdefiniować standardowe ligatury symboli czcionki Perykles, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 Następujący tekst Wyświetla DACL ligatury symboli czcionki Perykles.  
  
 ![Tekst przy użyciu ligatury OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont05.gif "opentypefont05")  
Tekst przy użyciu ligatury OpenType  
  
 W poniższym przykładzie znaczników pokazano, jak zdefiniować DACL ligatury symboli czcionki Perykles, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 Domyślnie [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionek w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] włączyć ligatury. Na przykład jeśli używasz czcionki Book Antiqua ligatury "fi", "one" i "fl" są wyświetlane jako symbolu Scalonej znak. Zwróć uwagę, że pary znaków dla każdego standardowe ligatury stykają.  
  
 ![Tekst przy użyciu ligatury OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont06.gif "opentypefont06")  
Tekst przy użyciu ligatury OpenType  
  
 Jednak można wyłączyć ligatury standardowe funkcje, aby standardowe ligatury, takie jak "ff" wyświetlany jako dwa osobne symboli, a nie jako symbolu Scalonej znaków.  
  
 ![Przy użyciu tekstu wyłączone ligatury OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont07.gif "opentypefont07")  
Tekst przy użyciu wyłączonych ligatury OpenType  
  
 W poniższym przykładzie znaczników pokazano, jak wyłączyć ligatury standardowe symboli czcionki Book Antiqua, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>   
## <a name="swashes"></a>Kaligraficzne  
 Kaligraficzne są ozdobne symbole, używające rozbudowane ornamentacji często skojarzone z kaligrafia. Następujący tekst, wyświetla standardowe i kaligraficzne symbole czcionki Pescadero.  
  
 ![Tekst standardowe i kaligraficzne symbole OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont08.gif "opentypefont08")  
Tekst standardowe i kaligraficzne symbole OpenType  
  
 Kaligraficzne są często używane jako elementy ozdobne zwroty, takie jak Anonse zdarzeń. Następujący tekst używa kaligraficzne, aby podkreślić wielkich liter nazwy zdarzenia.  
  
 ![Tekst przy użyciu kaligraficzne OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont09.gif "opentypefont09")  
Tekst przy użyciu kaligraficzne OpenType  
  
 W poniższym przykładzie znaczników pokazano, jak zdefiniować kaligraficzne czcionki, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a>Kontekstowe kaligraficzne  
 Niektóre połączenia symboli kaligrafii może spowodować nieatrakcyjnych wygląd, np. nakładające się wydłużeń dolnych z liter sąsiadujących ze sobą. Przy użyciu kontekstowe kaligrafii umożliwia przy użyciu symbolu kaligrafii substitute tworzącego lepsze wyglądu. Następujący tekst zawiera ten sam wyraz przed i po zastosowaniu kontekstowe kaligrafii.  
  
 ![Tekst kontekstowe symbole kaligraficzne OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont19.gif "OpenTypeFont19")  
Tekst kontekstowe symbole kaligraficzne OpenType  
  
 W poniższym przykładzie znaczników pokazano, jak zdefiniować kontekstowe kaligrafii czcionki Pescadero, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>   
## <a name="alternates"></a>Przełącza  
 Zastępcy są symbole, które mogą zastąpić standardowe symbolu. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki, takie jak Perykles czcionkę w poniższych przykładach, mogą zawierać alternatywne symbole, których można utworzyć różne typy wyglądu tekstu. Następujący tekst zawiera standardowe symboli czcionki Perykles.  
  
 ![Tekst standardowy symbole OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont01.gif "opentypefont01")  
Tekst standardowy symbole OpenType  
  
 Perykles [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionka zawiera symbole dodatkowe, które zapewniają alternatyw stylistycznych do standardowego zestawu symboli. Następujący tekst Wyświetla stylistycznych alternatywnych symboli.  
  
 ![Tekst stylistycznych alternatywne symbole OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont02.gif "opentypefont02")  
Tekst stylistycznych alternatywne symbole OpenType  
  
 W poniższym przykładzie znaczników pokazano, jak zdefiniować stylistycznych alternatywnych symboli czcionki Perykles, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 Następujący tekst zawiera kilka innych stylistycznych alternatywnych symboli czcionki Perykles.  
  
 ![Tekst stylistycznych alternatywne symbole OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont03.gif "opentypefont03")  
Tekst stylistycznych alternatywne symbole OpenType  
  
 W poniższym przykładzie znaczników przedstawia sposób definiowania tych innych stylistycznych alternatywnych symboli.  
  
 [!code-xaml[OpenTypeFontSamples#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a>Losowe kontekstowe  
 Losowe kontekstowe Podaj wiele symboli zastępczych dla jednego znaku. W przypadku wdrożenia z czcionkami typ skryptu tej funkcji można symulować pisma ręcznego przy użyciu zestawu losowo wybranych symboli z niewielkie różnice w wyglądzie. Następujący tekst używa losowe kontekstowe Lindsey czcionki. Zwróć uwagę, że litery "" różni się nieco w wyglądu  
  
 ![Tekst przy użyciu losowego kontekstowe OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont23.gif "OpenTypeFont23")  
Tekst przy użyciu losowego kontekstowe OpenType  
  
 W poniższym przykładzie znaczników pokazano, jak zdefiniować losowe kontekstowe czcionki Lindsey, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a>Formularze historycznych  
 Formularze historyczne są Konwencji typograficznych, które były często używane w przeszłości. Następujący tekst wyświetla słowo "Boston, Massachusetts", za pomocą formularza historycznych symboli czcionki Book Antiqua.  
  
 ![Tekst historyczne formy OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont10.gif "opentypefont10")  
Tekst historyczne formy OpenType  
  
 W poniższym przykładzie znaczników pokazano, jak zdefiniować historycznych formularze czcionki Book Antiqua, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>   
## <a name="numerical-styles"></a>Style liczb  
 Czcionek OpenType obsługuje wiele funkcji, które mogą być używane z wartości liczbowe w tekście.  
  
### <a name="fractions"></a>Ułamków  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki obsługę ułamków, w tym przekreślonych i skumulowany style.  
  
 Następujący tekst Wyświetla ułamek style czcionki Book Antiqua.  
  
 ![Tekst przy użyciu OpenType ukośną i ułamków piętrowych](../../../../docs/framework/wpf/advanced/media/opentypefont12.gif "opentypefont12")  
Tekst przy użyciu OpenType ukośną i ułamków piętrowych  
  
 W poniższym przykładzie znaczników pokazuje, jak określenie ułamku style czcionki Book Antiqua, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a>Stary styl cyfr  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki obsługuje stary styl format liczb. Ten format jest przydatne w przypadku wyświetlanie liczb w style, które nie są już standardowa. Następujący tekst Wyświetla datę 18 wieku formatów liczb standardowe i stary styl czcionki Book Antiqua.  
  
 ![Tekst przy użyciu OpenType starego stylu antykwy](../../../../docs/framework/wpf/advanced/media/opentypefont24.gif "OpenTypeFont24")  
Tekst przy użyciu OpenType stary styl cyfr  
  
 Następujący tekst zawiera standardowe liczb czcionki Book Antiqua, następuje stary styl cyfr.  
  
 ![Tekst przy użyciu starego zestawy liczb OpenType styl](../../../../docs/framework/wpf/advanced/media/opentypefont13.gif "opentypefont13")  
Tekst przy użyciu starego zestawy liczb OpenType stylu  
  
 W poniższym przykładzie znaczników pokazano, jak zdefiniować starego cyfry styl czcionki Book Antiqua, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a>Rysunki proporcjonalne i tabelaryczne  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki obsługuje funkcji rysunek proporcjonalne i tabelaryczne celu sterowania wyrównaniem szerokości, korzystając z cyfr. Rysunki proporcjonalne zaliczenie o różnych szerokości każdego liczb, "1" jest mniejsza niż "5". Dane tabelaryczne są traktowane jako szerokość równości cyfry tak, aby ich wyrównane w pionie, co zwiększa czytelność informacji o typie finansowych.  
  
 Następujący tekst Wyświetla dwóch liczb proporcjonalnych w pierwszej kolumnie przy użyciu czcionki Miramonte. Należy zwrócić uwagę różnicy w szerokość cyfry "5" i "1". Druga kolumna przedstawia tego samego dwóch wartości liczbowych z szerokości dostosowane przy użyciu funkcji rysunek tabelarycznych.  
  
 ![Tekst przy użyciu proporcjonalne i tabelaryczne liczby OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont22.gif "OpenTypeFont22")  
Tekst przy użyciu OpenType proporcjonalne i tabelaryczne dane  
  
 W poniższym przykładzie znaczników pokazano, jak zdefiniować proporcjonalne i tabelaryczne dane czcionki Miramonte, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a>Przekreślone Zero  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionki obsługuje przekreślonych zero format liczb do wyróżnienia różnica między litera "O" i liczb, "0". Przekreślonych zero liczb jest często używana dla identyfikatorów informacje finansowe i biznesowe.  
  
 Następujący tekst zawiera identyfikator zamówienia próbki, przy użyciu czcionki Miramonte. Pierwszy wiersz używa standardowych cyfr. Drugi wiersz używane ukośną zero cyfr, aby zapewnić lepsze kontrastu wielkiej litery "E".  
  
 ![Tekst przy użyciu OpenType ukośną zerowej liczby](../../../../docs/framework/wpf/advanced/media/opentypefont17.gif "OpenTypeFont17")  
Tekst przy użyciu OpenType ukośną zerowej liczby  
  
 W poniższym przykładzie znaczników pokazano, jak zdefiniować ukośną zerowej liczby czcionki Miramonte, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>   
## <a name="typography-class"></a>Klasa typografii  
 <xref:System.Windows.Documents.Typography> Obiekt udostępnia zestaw funkcji, które [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] obsługuje czcionki. Przez ustawienie właściwości <xref:System.Windows.Documents.Typography> w znaczniku, można łatwo tworzyć dokumenty, które korzystają z [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] funkcji.  
  
 Następujący tekst zawiera standardowe wielkimi literami czcionki Pescadero, a następnie liter jako "SmallCaps" i "AllSmallCaps". W takim przypadku ten sam rozmiar czcionki jest używany dla wszystkich trzech słów.  
  
 ![Tekst wielkie litery OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont11.gif "opentypefont11")  
Wielkie litery OpenType tekstu  
  
 W poniższym przykładzie znaczników pokazano, jak zdefiniować wersalików w przypadku czcionki Pescadero, za pomocą właściwości <xref:System.Windows.Documents.Typography> obiektu. Gdy używany jest format "SmallCaps", wszystkie wiodące litera jest ignorowana.  
  
 [!code-xaml[OpenTypeFontSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 Poniższy przykład kodu następuje to w ramach tego samego zadania, co w poprzednim przykładzie kodu znaczników.  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a>Właściwości typografii — klasa  
 W poniższej tabeli wymieniono właściwości, wartości i ustawienia domyślne <xref:System.Windows.Documents.Typography> obiektu.  
  
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
|<xref:System.Windows.Documents.Typography.StandardSwashes%2A>|wartość liczbowa — bajtów|0|  
|<xref:System.Windows.Documents.Typography.StylisticAlternates%2A>|wartość liczbowa — bajtów|0|  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Documents.Typography>  
 [Specyfikacja OpenType](http://go.microsoft.com/fwlink/?LinkId=96731)  
 [Typografia w WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [Przykład pakietu czcionek OpenType](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)  
 [Pakowanie czcionek z aplikacjami](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md)
