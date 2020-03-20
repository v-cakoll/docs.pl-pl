---
title: Typografia
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
ms.openlocfilehash: 501a4221c99d405484a2fb908641d27d1f38f266
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187347"
---
# <a name="typography-in-wpf"></a>Typografia w WPF
W tym temacie przedstawiono główne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]cechy typograficzne programu . Funkcje te obejmują lepszą jakość i wydajność renderowania tekstu, obsługę typografii OpenType, ulepszony tekst międzynarodowy, ulepszoną obsługę czcionek i nowe interfejsy programowania aplikacji tekstowych (API).  
  
<a name="Improved_Quality_and_Performance_of_Text"></a>
## <a name="improved-quality-and-performance-of-text"></a>Lepsza jakość i wydajność tekstu  
 Tekst [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w jest renderowany przy użyciu programu Microsoft ClearType, co zwiększa przejrzystość i czytelność tekstu. ClearType to technologia oprogramowania opracowana przez firmę Microsoft, która poprawia czytelność tekstu na istniejących monitorach LCD (Wyświetlacze Ciekłokrystaliczne), takich jak ekrany laptopów, ekrany Pocket PC i monitory płaskoekranowe. ClearType używa renderowania subpikseli, które umożliwia wyświetlanie tekstu z większą wiernością jego prawdziwego kształtu przez wyrównanie znaków na ułamkowej części piksela. Dodatkowa rozdzielczość zwiększa ostrość drobnych szczegółów na ekranie tekstu, dzięki czemu znacznie łatwiej jest czytać przez długi czas. Inną ulepszeniem ClearType w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest y-kierunek wygładzanie, który wygładza szczyty i dna płytkich krzywych w znakach tekstowych. Aby uzyskać więcej informacji na temat funkcji ClearType, zobacz [ClearType Overview](cleartype-overview.md).  
  
 ![Tekst z wygładą wygładzania ClearType y-kierunek](./media/typography-in-wpf/text-y-direction-antialiasing.gif)  
Tekst z antialiasing cleartype y-kierunek  
  
 Cały potok renderowania tekstu może być [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przyspieszany sprzętowo, pod warunkiem, że komputer spełnia minimalny wymagany poziom sprzętu. Renderowanie, które nie może być wykonywane przy użyciu sprzętu, powraca do renderowania programowego. Przyspieszenie sprzętowe wpływa na wszystkie fazy potoku renderowania tekstu — od przechowywania pojedynczych glifów, komponowania glifów w przebiegi glifów, stosowania efektów, do stosowania algorytmu mieszania ClearType do ostatecznego wyświetlanego wyjścia. Aby uzyskać więcej informacji na temat przyspieszania sprzętowego, zobacz [Warstwy renderowania grafiki](graphics-rendering-tiers.md).  
  
 ![Diagram potoku renderowania tekstu](./media/typography-in-wpf/text-rendering-pipeline.png)  
  
 Ponadto animowany tekst, czy to znakiem, czy glifem, w pełni [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]wykorzystuje możliwości sprzętu graficznego włączone przez program . Powoduje to płynną animację tekstu.  
  
<a name="Rich_Typography"></a>
## <a name="rich-typography"></a>Typografia bogata  
 Format czcionki OpenType jest rozszerzeniem formatu czcionki TrueType®. Format czcionki OpenType został opracowany wspólnie przez microsoft i adobe i zapewnia bogaty asortyment zaawansowanych funkcji typograficznych. Obiekt <xref:System.Windows.Documents.Typography> udostępnia wiele zaawansowanych funkcji czcionek OpenType, takich jak alternatywy stylistyczne i swashes. Zestaw Windows SDK zawiera zestaw przykładowych czcionek OpenType zaprojektowanych z bogatymi funkcjami, takimi jak czcionki Perykles i Pescadero. Aby uzyskać więcej informacji, zobacz [Przykładowy pakiet czcionek OpenType](sample-opentype-font-pack.md).  
  
 Czcionka Perykles OpenType zawiera dodatkowe glify, które zapewniają stylistyczne alternatywy dla standardowego zestawu glifów. W poniższym tekście są wyświetlane glify alternatywne stylistyczne.  
  
 ![Tekst przy użyciu alternatywnych glifów stylistycznych OpenType](./media/typography-in-wpf/opentype-stylistic-alternate-glyphs.gif "Tekst przy użyciu alternatywnych glifów stylistycznych OpenType")  
  
 Swashes są dekoracyjne glify, które używają opracowania ornamentacji często związane z kaligrafii. W poniższym tekście są wyświetlane standardowe i swash glify dla czcionki Pescadero.  
  
 ![Tekst przy użyciu standardu OpenType i glifów](./media/typography-in-wpf/opentype-standard-swash-glyphs.gif "Tekst przy użyciu standardu OpenType i glifów")  
  
 Aby uzyskać więcej informacji na temat funkcji OpenType, zobacz [Funkcje czcionek OpenType](opentype-font-features.md).  
  
<a name="Enhanced_International_Text_Support"></a>
## <a name="enhanced-international-text-support"></a>Ulepszona międzynarodowa obsługa tekstu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zapewnia ulepszoną obsługę tekstu międzynarodowego, zapewniając następujące funkcje:  
  
- Automatyczne odstępy między wierszami we wszystkich systemach pisania, przy użyciu pomiarów adaptacyjnych.  
  
- Szerokie poparcie dla tekstu międzynarodowego. Aby uzyskać więcej informacji, zobacz [Globalizacja dla WPF](globalization-for-wpf.md).  
  
- Podział wiersza z przewodnikiem w języku, dzielenie wyrazów i justowanie.  
  
<a name="Enhanced_Font_Support"></a>
## <a name="enhanced-font-support"></a>Ulepszona obsługa czcionek  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zapewnia ulepszoną obsługę czcionek, udostępniając następujące funkcje:  
  
- Unicode dla całego tekstu. Zachowanie i zaznaczenie czcionki nie wymagają już zestawu znaków ani strony kodowej.  
  
- Zachowanie czcionki niezależne od ustawień globalnych, takich jak ustawienia regionalne systemu.  
  
- <xref:System.Windows.FontWeight>Oddziel <xref:System.Windows.FontStretch>i <xref:System.Windows.FontStyle> typy do <xref:System.Windows.Media.FontFamily>definiowania pliku . Zapewnia to większą elastyczność niż w programowaniu Win32, w którym kombinacje logiczne kursywy i pogrubienia są używane do definiowania rodziny czcionek.  
  
- Kierunek pisania (poziomy a pionowy) obsługiwany niezależnie od nazwy czcionki.  
  
- Łączenie czcionek i rezerwowanie czcionek w przenośnym pliku XML przy użyciu technologii czcionek kompozytowych. Czcionki kompozytowe umożliwiają budowę pełnego zakresu czcionek wielojęzycznych. Czcionki kompozytowe zapewniają również mechanizm, który pozwala uniknąć wyświetlania brakujących glifów. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.FontFamily> uwagi w klasie.  
  
- Czcionki międzynarodowe zbudowane z czcionek kompozytowych, przy użyciu grupy czcionek jednojęzykowych. Pozwala to zaoszczędzić na kosztach zasobów podczas tworzenia czcionek dla wielu języków.  
  
- Czcionki kompozytowe osadzone w dokumencie, zapewniając w ten sposób możliwość przenoszenia dokumentów. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Media.FontFamily> uwagi w klasie.  
  
<a name="New_Text_APIs"></a>
## <a name="new-text-application-programming-interfaces-apis"></a>Nowe interfejsy programowania aplikacji tekstowych (API)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]udostępnia kilka interfejsów API tekstu dla deweloperów do użycia podczas dołączania tekstu w swoich aplikacjach. Te interfejsy API są pogrupowane w trzy kategorie:  
  
- **Układ i interfejs użytkownika**. Typowy tekst steruje graficznym interfejsem użytkownika (GUI).  
  
- **Lekki rysunek tekstowy**. Umożliwia rysowanie tekstu bezpośrednio do obiektów.  
  
- **Zaawansowane formatowanie tekstu**. Umożliwia zaimplementowanie niestandardowego aparatu tekstu.  
  
### <a name="layout-and-user-interface"></a>Układ i interfejs użytkownika  
 Na najwyższym poziomie funkcjonalności tekstowe interfejsy API [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] zapewniają <xref:System.Windows.Controls.Label>typowe <xref:System.Windows.Controls.TextBlock>formanty, takie jak , i <xref:System.Windows.Controls.TextBox>. Te formanty [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zapewniają podstawowe elementy w aplikacji i oferują łatwy sposób prezentacji i interakcji z tekstem. Formanty, takie jak <xref:System.Windows.Controls.RichTextBox> i <xref:System.Windows.Controls.PasswordBox> włączyć bardziej zaawansowane lub specjalistyczne obsługi tekstu. I klasy <xref:System.Windows.Documents.TextRange>takie <xref:System.Windows.Documents.TextSelection>jak <xref:System.Windows.Documents.TextPointer> , i umożliwiają przydatne manipulacji tekstem. Te [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] formanty zapewniają <xref:System.Windows.Controls.Control.FontFamily%2A> <xref:System.Windows.Controls.Control.FontSize%2A>właściwości, <xref:System.Windows.Controls.Control.FontStyle%2A>takie jak , i , które umożliwiają sterowanie czcionką używaną do renderowania tekstu.  
  
#### <a name="using-bitmap-effects-transforms-and-text-effects"></a>Korzystanie z efektów bitmapowych, przekształceń i efektów tekstowych  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]umożliwia tworzenie interesujących wizualnie zastosowań tekstu przez użycie funkcji, takich jak efekty bitmapowe, przekształcenia i efekty tekstowe. W poniższym przykładzie przedstawiono typowy typ efektu cienia zastosowanego do tekstu.  
  
 ![Cień tekstu z miękkością &#61; 0,25](./media/typography-in-wpf/drop-shadow-text-effect.jpg)
  
 W poniższym przykładzie pokazano efekt cienia i szumy zastosowane do tekstu.  
  
 ![Cień tekstu z szumem](./media/typography-in-wpf/drop-shadow-noise-text.jpg)
  
 W poniższym przykładzie przedstawiono efekt blasku zewnętrznego zastosowany do tekstu.  
  
 ![Cień tekstu przy użyciu efektu OuterGlowBitmapEffect](./media/typography-in-wpf/text-shadow-glow-effect.jpg)
  
 W poniższym przykładzie przedstawiono efekt rozmycia zastosowany do tekstu.  
  
 ![Cień tekstu przy użyciu efektu BlurBitmapEffect](./media/typography-in-wpf/text-shadow-blur-effect.jpg)  

 W poniższym przykładzie pokazano drugi wiersz tekstu przeskalowany o 150% wzdłuż osi x, a trzeci wiersz tekstu przeskalowany o 150% wzdłuż osi y.  
  
 ![Tekst skalowany przy użyciu scaletransform](./media/typography-in-wpf/scaled-text-scaletransform.jpg)
  
 W poniższym przykładzie pokazano tekst pochylony wzdłuż osi x.  
  
 ![Tekst pochylony za pomocą skewTransform](./media/typography-in-wpf/skewed-transformed-text.jpg)
  
 Obiekt <xref:System.Windows.Media.TextEffect> jest obiektem pomocniczym, który umożliwia traktowanie tekstu jako jednej lub więcej grup znaków w ciągu tekstowym. W poniższym przykładzie przedstawiono obracany pojedynczy znak. Każdy znak jest obracany niezależnie w odstępach 1-sekundowych.  
  
 ![Zrzut ekranu przedstawiający efekt tekstowy obracający tekst](./media/typography-in-wpf/rotating-text-effect.jpg)
  
#### <a name="using-flow-documents"></a>Korzystanie z dokumentów przepływu  
 Oprócz typowych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] formantów, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferuje formant układu <xref:System.Windows.Documents.FlowDocument> dla prezentacji tekstu — element. Element, <xref:System.Windows.Documents.FlowDocument> w połączeniu <xref:System.Windows.Controls.DocumentViewer> z elementem, zapewnia kontrolę dla dużych ilości tekstu o różnych wymagań układu. Formanty układu zapewniają dostęp <xref:System.Windows.Documents.Typography> do zaawansowanej typografii za [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pośrednictwem obiektu i właściwości związanych z czcionkami innych formantów.  
  
 W poniższym przykładzie przedstawiono <xref:System.Windows.Controls.FlowDocumentReader>zawartość tekstową hostowaną w trybie , który zapewnia obsługę wyszukiwania, nawigacji, podziałów na strony i skalowanie zawartości.  
  
 ![Zrzut ekranu przedstawiający czcionki OpenType.](./media/typography-in-wpf/typography-text-flowdocumentreader.png)
  
 Aby uzyskać więcej informacji, zobacz [Dokumenty w WPF](documents-in-wpf.md).  
  
### <a name="lightweight-text-drawing"></a>Odciążony rysunek tekstu  
 Tekst można rysować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bezpośrednio do <xref:System.Windows.Media.DrawingContext.DrawText%2A> obiektów przy <xref:System.Windows.Media.DrawingContext> użyciu metody obiektu. Aby użyć tej metody, <xref:System.Windows.Media.FormattedText> należy utworzyć obiekt. Ten obiekt umożliwia rysowanie tekstu wielowierszowego, w którym każdy znak w tekście może być indywidualnie sformatowany. Funkcjonalność <xref:System.Windows.Media.FormattedText> obiektu zawiera wiele funkcji drawtext flagi w interfejsie API systemu Windows. Ponadto <xref:System.Windows.Media.FormattedText> obiekt zawiera funkcje, takie jak obsługa wielokropka, w którym wielokropek jest wyświetlany, gdy tekst przekracza swoje granice. W poniższym przykładzie przedstawiono tekst, który ma kilka formatów stosowanych do niego, w tym gradient liniowy na drugim i trzecim wyrazu.  
  
 ![Tekst wyświetlany przy użyciu obiektu FormattedText](./media/typography-in-wpf/text-formatted-linear-gradient.jpg)
  
 Sformatowany tekst <xref:System.Windows.Media.Geometry> można konwertować na obiekty, co pozwala na tworzenie innych typów tekstu interesującego wizualnie. Na przykład można utworzyć <xref:System.Windows.Media.Geometry> obiekt na podstawie konturu ciągu tekstowego.  
  
 ![Kontur tekstu przy użyciu pędzla gradientu liniowego](./media/typography-in-wpf/text-outline-linear-gradient.jpg)  
  
 Poniższe przykłady ilustrują kilka sposobów tworzenia interesujących efektów wizualnych przez modyfikowanie obrysu, wypełnienia i wyróżnienia przekonwertowanego tekstu.  
  
 ![Tekst o różnych kolorach wypełnienia i obrysu](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Tekst z pędzlem obrazu zastosowanym do obrysu](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Tekst z pędzlem obrazu zastosowanym do obrysu i podświetlenia](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Aby uzyskać więcej <xref:System.Windows.Media.FormattedText> informacji na temat obiektu, zobacz [Rysowanie tekstu sformatowanego](drawing-formatted-text.md).  
  
### <a name="advanced-text-formatting"></a>Zaawansowane formatowanie tekstu  
 Na najbardziej zaawansowanym poziomie interfejsów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API tekstu oferuje możliwość tworzenia niestandardowego <xref:System.Windows.Media.TextFormatting.TextFormatter> układu tekstu przy <xref:System.Windows.Media.TextFormatting> użyciu obiektu i innych typów w obszarze nazw. Klasy <xref:System.Windows.Media.TextFormatting.TextFormatter> i skojarzone z nimi umożliwiają implementowanie niestandardowego układu tekstu, który obsługuje własną definicję formatów znaków, stylów akapitów, reguł łamania wierszy i innych funkcji układu dla tekstu międzynarodowego. Istnieje bardzo niewiele przypadków, w których chcesz zastąpić domyślną [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementację obsługi układu tekstu. Jednak jeśli tworzysz formant edycji tekstu lub aplikacji, może wymagać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] innej implementacji niż domyślna implementacja.  
  
 W przeciwieństwie do tradycyjnego interfejsu API tekstu <xref:System.Windows.Media.TextFormatting.TextFormatter> współdziała z klientem układu tekstu za pomocą zestawu metod wywołania zwrotnego. Wymaga klienta, aby zapewnić te metody <xref:System.Windows.Media.TextFormatting.TextSource> w implementacji klasy. Na poniższym diagramie przedstawiono interakcję układu <xref:System.Windows.Media.TextFormatting.TextFormatter>tekstu między aplikacją kliencką i .  
  
 ![Diagram klienta układu tekstu i textformatter](./media/typography-in-wpf/text-layout-text-formatter-interaction.png)  
  
 Aby uzyskać więcej informacji na temat tworzenia niestandardowego układu tekstu, zobacz [Zaawansowane formatowanie tekstu](advanced-text-formatting.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.FormattedText>
- <xref:System.Windows.Media.TextFormatting.TextFormatter>
- [ClearType — przegląd](cleartype-overview.md)
- [Funkcje czcionki OpenType](opentype-font-features.md)
- [Rysowanie formatowanego tekstu](drawing-formatted-text.md)
- [Zaawansowane formatowanie tekstu](advanced-text-formatting.md)
- [Tekst](optimizing-performance-text.md)
- [Typografia firmy Microsoft](https://docs.microsoft.com/typography/)
