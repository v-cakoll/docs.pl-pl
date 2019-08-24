---
title: Typografia w WPF
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
ms.openlocfilehash: b4ae0d03c0207413d826e62de1d157f938b4d775
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016131"
---
# <a name="typography-in-wpf"></a>Typografia w WPF
W tym temacie przedstawiono główne funkcje typograficzne programu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Te funkcje obejmują ulepszoną jakość i wydajność renderowania tekstu, obsługę typografii OpenType, ulepszony międzynarodowy tekst, rozszerzoną obsługę czcionek oraz nowe interfejsy programowania aplikacji tekstowych (API).  
  
<a name="Improved_Quality_and_Performance_of_Text"></a>   
## <a name="improved-quality-and-performance-of-text"></a>Ulepszona jakość i wydajność tekstu  
 Tekst w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programie jest renderowany przy użyciu technologii Microsoft ClearType, która zwiększa czytelność i czytelność tekstu. Technologia ClearType jest technologią oprogramowania opracowaną przez firmę Microsoft, która zwiększa czytelność tekstu w istniejących LCDs (w przypadku wyświetlaczy Liquid Crystal), takich jak ekrany laptopów, urządzenia Pocket PC i monitory płaskoekranowe. Technologia ClearType używa renderowania w pikselach, co pozwala na wyświetlanie tekstu z większą dokładnością do jego prawdziwego kształtu przez wyrównanie znaków w ułamkowej części piksela. Dodatkowe rozwiązanie zwiększa ostrość niewielkich szczegółów w wyświetlaniu tekstu, ułatwiając odczytywanie ich w dłuższym czasie. Innym ulepszeniem technologii ClearType [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w programie jest wygładzanie kierunku y, co umożliwia wygładzanie wierzchołków i dolnych krzywych w znakach tekstowych. Aby uzyskać więcej informacji na temat funkcji ClearType, zobacz [Omówienie technologii ClearType](cleartype-overview.md).  
  
 ![Tekst z wygładzaniem kierunku x w technologii ClearType](./media/typography-in-wpf/text-y-direction-antialiasing.gif)  
Tekst z wygładzaniem kierunku y w technologii ClearType  
  
 Cały potok renderowania tekstu może być przyspieszeniem sprzętowym w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przypadku, gdy maszyna spełnia minimalny wymagany poziom sprzętu. Renderowanie, które nie może zostać wykonane przy użyciu sprzętu, powraca do renderowania oprogramowania. Przyspieszenie sprzętowe wpływa na wszystkie fazy potoku renderowania tekstu — od przechowywania pojedynczych glifów, złożenia glifów do uruchomienia glifów, stosowania efektów, do zastosowania algorytmu mieszania ClearType do końcowych wyświetlanych danych wyjściowych. Aby uzyskać więcej informacji na temat przyspieszania sprzętowego, zobacz [warstwy renderowania grafiki](graphics-rendering-tiers.md).  
  
 ![Diagram potoku renderowania tekstu](./media/typography-in-wpf/text-rendering-pipeline.png)  
  
 Dodatkowo animowany tekst, niezależnie od tego, czy jest to znak czy glif, w pełni wykorzystują możliwości sprzętowe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]grafiki włączone przez program. Powoduje to wygładzanie animacji tekstu.  
  
<a name="Rich_Typography"></a>   
## <a name="rich-typography"></a>Bogaty Typografia  
 Format czcionki OpenType jest rozszerzeniem [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] formatu czcionki. Format czcionki OpenType został opracowany wspólnie przez firmę Microsoft i firmę Adobe oraz oferuje bogaty asortyment zaawansowanych funkcji typograficznych. <xref:System.Windows.Documents.Typography> Obiekt ujawnia wiele zaawansowanych funkcji czcionek OpenType, takich jak alternatywy stylistyczne i znaki kaligraficzne. Windows SDK zawiera zestaw przykładowych czcionek OpenType, które są zaprojektowane z rozbudowanymi funkcjami, takimi jak czcionki Pericles i Pescadero. Aby uzyskać więcej informacji, zobacz [przykładowy pakiet czcionek OpenType](sample-opentype-font-pack.md).  
  
 Czcionka Pericles OpenType zawiera dodatkowe glify, które udostępniają alternatywy stylistyczne dla standardowego zestawu symboli. Następujący tekst zawiera stylistyczne glify alternatywne.  
  
 ![Tekst przy użyciu alternatywnych symboli OpenType](./media/typography-in-wpf/opentype-stylistic-alternate-glyphs.gif "Tekst przy użyciu alternatywnych symboli OpenType")  
  
 Znaki kaligraficzne to dekoracyjne glify, które używają wyrafinowanych elementów ozdobnych często skojarzonych z Calligraphy. Poniższy tekst zawiera standardowe i kaligraficzne glify dla czcionki Pescadero.  
  
 ![Tekst korzystający z symboli standardowych i kaligraficzne OpenType](./media/typography-in-wpf/opentype-standard-swash-glyphs.gif "Tekst korzystający z symboli standardowych i kaligraficzne OpenType")  
  
 Aby uzyskać więcej informacji na temat funkcji OpenType, zobacz [funkcje czcionek OpenType](opentype-font-features.md).  
  
<a name="Enhanced_International_Text_Support"></a>   
## <a name="enhanced-international-text-support"></a>Rozszerzona obsługa tekstu międzynarodowego  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zapewnia rozszerzoną obsługę tekstu międzynarodowego, udostępniając następujące funkcje:  
  
- Automatyczne odstępy między liniami we wszystkich systemach pisania, przy użyciu funkcji adaptacyjnego pomiaru.  
  
- Szeroka pomoc techniczna dla tekstu międzynarodowego. Aby uzyskać więcej informacji, zobacz [globalizacja dla WPF](globalization-for-wpf.md).  
  
- Podział wierszy z przewodnikiem, dzielenie wyrazów i uzasadnienie.  
  
<a name="Enhanced_Font_Support"></a>   
## <a name="enhanced-font-support"></a>Ulepszona obsługa czcionek  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zapewnia rozszerzoną obsługę czcionek, udostępniając następujące funkcje:  
  
- Unicode dla całego tekstu. Zachowanie czcionki i wybór nie wymagają już zestawu znaków lub strony kodowej.  
  
- Zachowanie czcionki niezależnie od ustawień globalnych, takich jak ustawienia regionalne systemu.  
  
- <xref:System.Windows.FontWeight>Oddziel <xref:System.Windows.FontStretch>, i <xref:System.Windows.FontStyle> typy do definiowania a <xref:System.Windows.Media.FontFamily>. Zapewnia to większą elastyczność niż w [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] programowaniu, w którym logiczne kombinacje kursywy i pogrubienie są używane do definiowania rodziny czcionek.  
  
- Kierunek pisania (w poziomie i w pionie) obsługiwany niezależnie od nazwy czcionki.  
  
- Łączenie czcionek i powrót do czcionki w przenośnym [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] pliku przy użyciu technologii czcionek złożonych. Czcionki złożone umożliwiają tworzenie pełnych czcionek wielojęzycznych. Czcionki złożone zapewniają również mechanizm, który pozwala uniknąć wyświetlania brakujących symboli. Aby uzyskać więcej informacji, zobacz uwagi w <xref:System.Windows.Media.FontFamily> klasie.  
  
- Czcionki międzynarodowe zbudowane z czcionek kompozytowych przy użyciu grupy czcionek jednojęzykowych. Powoduje to zapisanie kosztów zasobów podczas tworzenia czcionek dla wielu języków.  
  
- Czcionki złożone osadzone w dokumencie, co zapewnia przenośność dokumentów. Aby uzyskać więcej informacji, zobacz uwagi w <xref:System.Windows.Media.FontFamily> klasie.  
  
<a name="New_Text_APIs"></a>   
## <a name="new-text-application-programming-interfaces-apis"></a>Nowe interfejsy programowania aplikacji tekstowych (API)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Program udostępnia kilka tekstowych interfejsów API, których deweloperzy mogą używać podczas dołączania tekstu do aplikacji. Te interfejsy API są pogrupowane w trzy kategorie:  
  
- **Układ i interfejs użytkownika**. Typowe kontrolki tekstu dla graficznego interfejsu użytkownika (GUI).  
  
- **Lekkie rysowanie tekstu**. Umożliwia narysowanie tekstu bezpośrednio do obiektów.  
  
- **Zaawansowane formatowanie tekstu**. Umożliwia zaimplementowanie niestandardowego aparatu tekstu.  
  
### <a name="layout-and-user-interface"></a>Układ i interfejs użytkownika  
 Na najwyższym poziomie funkcjonalności interfejsy API tekstu zapewniają [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] typowe kontrolki, takie jak <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBlock>i <xref:System.Windows.Controls.TextBox>. Te kontrolki zapewniają podstawowe [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy w aplikacji i oferują łatwy sposób prezentowania i współpracy z tekstem. Kontrolki takie <xref:System.Windows.Controls.RichTextBox> jak <xref:System.Windows.Controls.PasswordBox> i zapewniają bardziej zaawansowaną lub wyspecjalizowaną obsługę tekstu. I klasy, takie <xref:System.Windows.Documents.TextRange>jak <xref:System.Windows.Documents.TextSelection>, i <xref:System.Windows.Documents.TextPointer> umożliwiają użyteczne manipulowanie tekstem. Te [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kontrolki zapewniają właściwości, <xref:System.Windows.Controls.Control.FontFamily%2A>takie <xref:System.Windows.Controls.Control.FontSize%2A>jak, <xref:System.Windows.Controls.Control.FontStyle%2A>, i, które umożliwiają kontrolowanie czcionki używanej do renderowania tekstu.  
  
#### <a name="using-bitmap-effects-transforms-and-text-effects"></a>Używanie efektów mapy bitowej, transformacji i efektów tekstowych  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]umożliwia tworzenie wizualnie interesujących sposobów użycia tekstu przy użyciu funkcji, takich jak efekty bitmapowe, przekształcenia i efekty tekstowe. W poniższym przykładzie przedstawiono typowy efekt cienia, który został zastosowany do tekstu.  
  
 ![Cień tekstu z miękką &#61; 0,25](./media/typography-in-wpf/drop-shadow-text-effect.jpg) 
  
 Poniższy przykład pokazuje efekt cienia i szum zastosowany do tekstu.  
  
 ![Cień tekstu z hałasem](./media/typography-in-wpf/drop-shadow-noise-text.jpg) 
  
 Poniższy przykład pokazuje efekt zewnętrznego blasku zastosowany do tekstu.  
  
 ![Cień tekstu przy użyciu elementu OuterGlowBitmapEffect](./media/typography-in-wpf/text-shadow-glow-effect.jpg)
  
 W poniższym przykładzie pokazano efekt rozmycia stosowany do tekstu.  
  
 ![Cień tekstu przy użyciu BlurBitmapEffect](./media/typography-in-wpf/text-shadow-blur-effect.jpg)  

 Poniższy przykład pokazuje drugi wiersz tekstu skalowanego przez 150% wzdłuż osi x, a trzeci wiersz tekstu skalowany przez 150% wzdłuż osi y.  
  
 ![Tekst skalowany przy użyciu ScaleTransform](./media/typography-in-wpf/scaled-text-scaletransform.jpg) 
  
 Poniższy przykład przedstawia tekst pochylony wzdłuż osi x.  
  
 ![Tekst skośny przy użyciu SkewTransform](./media/typography-in-wpf/skewed-transformed-text.jpg)
  
 <xref:System.Windows.Media.TextEffect> Obiekt jest obiektem pomocnika, który umożliwia traktowanie tekstu jako co najmniej jednej grupy znaków w ciągu tekstowym. Poniższy przykład pokazuje, że pojedynczy znak jest obracany. Każdy znak jest obracany niezależnie w odstępach 1-sekundowych.  
  
 ![Zrzut ekranu przedstawiający tekst obracania efektu tekstu](./media/typography-in-wpf/rotating-text-effect.jpg) 
  
#### <a name="using-flow-documents"></a>Używanie dokumentów przepływu  
 Oprócz formantów wspólnych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferuje kontrolkę układu <xref:System.Windows.Documents.FlowDocument> do prezentacji tekstowej — element. Element, w połączeniu <xref:System.Windows.Controls.DocumentViewer> z elementem, zapewnia formant dla dużych ilości tekstu, które mają różne wymagania dotyczące układu. <xref:System.Windows.Documents.FlowDocument> Kontrolki układu zapewniają dostęp do zaawansowanych typografii <xref:System.Windows.Documents.Typography> przy użyciu obiektów i właściwości związanych z czcionkami innych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kontrolek.  
  
 Poniższy przykład przedstawia zawartość tekstową hostowaną w <xref:System.Windows.Controls.FlowDocumentReader>, która zapewnia obsługę wyszukiwania, nawigacji, stronicowania i skalowania zawartości.  
  
 ![Zrzut ekranu pokazujący czcionki OpenType.](./media/typography-in-wpf/typography-text-flowdocumentreader.png)
  
 Aby uzyskać więcej informacji, zobacz [dokumenty w WPF](documents-in-wpf.md).  
  
### <a name="lightweight-text-drawing"></a>Lekkie rysowanie tekstu  
 Możesz narysować tekst bezpośrednio do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektów przy <xref:System.Windows.Media.DrawingContext.DrawText%2A> użyciu metody <xref:System.Windows.Media.DrawingContext> obiektu. Aby użyć tej metody, należy utworzyć <xref:System.Windows.Media.FormattedText> obiekt. Ten obiekt umożliwia narysowanie tekstu wielowierszowego, w którym każdy znak w tekście może być sformatowany osobno. Funkcja <xref:System.Windows.Media.FormattedText> obiektu zawiera wiele funkcji flag DrawText w interfejsie API systemu Windows. Ponadto <xref:System.Windows.Media.FormattedText> obiekt zawiera funkcje, takie jak obsługa wielokropka, w którym jest wyświetlany wielokropek, gdy tekst przekracza jego granice. Poniższy przykład przedstawia tekst, do którego zastosowano kilka formatów, w tym gradient liniowy na drugim i trzecim wyrazie.  
  
 ![Tekst wyświetlany przy użyciu obiektu FormattedText](./media/typography-in-wpf/text-formatted-linear-gradient.jpg) 
  
 Możesz skonwertować sformatowany tekst na <xref:System.Windows.Media.Geometry> obiekty, co pozwala na tworzenie innych typów wizualnie interesujących. Na przykład można utworzyć <xref:System.Windows.Media.Geometry> obiekt na podstawie konturu ciągu tekstowego.  
  
 ![Kontur tekstu przy użyciu gradientu liniowego](./media/typography-in-wpf/text-outline-linear-gradient.jpg)  
  
 Poniższe przykłady ilustrują kilka sposobów tworzenia interesujących efektów wizualnych przez modyfikację obrysu, wypełnienia i wyróżnienia konwertowanego tekstu.  
  
 ![Tekst z różnymi kolorami dla wypełnienia i pociągnięcia](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Tekst z pędzlem obrazu zastosowany do pociągnięcia](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Tekst z pędzlem obrazu zastosowany do obrysu i wyróżnienia](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Aby uzyskać więcej informacji na <xref:System.Windows.Media.FormattedText> temat obiektu, zobacz [rysowanie sformatowanego tekstu](drawing-formatted-text.md).  
  
### <a name="advanced-text-formatting"></a>Zaawansowane formatowanie tekstu  
 Najbardziej zaawansowany interfejs API [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umożliwia tworzenie niestandardowych układów tekstu przy <xref:System.Windows.Media.TextFormatting.TextFormatter> użyciu obiektu <xref:System.Windows.Media.TextFormatting> i innych typów w przestrzeni nazw. Skojarzone <xref:System.Windows.Media.TextFormatting.TextFormatter> klasy i umożliwiają implementowanie niestandardowego układu tekstu, który obsługuje własną definicję formatów znaków, stylów akapitu, reguł dzielenia wierszy i innych funkcji układu dla tekstu międzynarodowego. Istnieje bardzo kilka przypadków, w których chcesz zastąpić domyślną implementację [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługi układu tekstu. Jeśli jednak tworzysz kontrolkę edycji tekstu lub aplikację, może być wymagana inna implementacja niż domyślna [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .  
  
 W <xref:System.Windows.Media.TextFormatting.TextFormatter> przeciwieństwie do tradycyjnego interfejsu API tekstu, współdziała z klientem układu tekstu za pomocą zestawu metod wywołania zwrotnego. Wymaga, aby klient dostarczał te metody w implementacji <xref:System.Windows.Media.TextFormatting.TextSource> klasy. Na poniższym diagramie przedstawiono interakcje układu tekstu między aplikacją kliencką i <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Diagram klienta układu tekstu i elementu textformatującego](./media/typography-in-wpf/text-layout-text-formatter-interaction.png)  
  
 Aby uzyskać więcej informacji na temat tworzenia niestandardowego układu tekstu, zobacz [Zaawansowane formatowanie tekstu](advanced-text-formatting.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.FormattedText>
- <xref:System.Windows.Media.TextFormatting.TextFormatter>
- [ClearType — przegląd](cleartype-overview.md)
- [Funkcje czcionki OpenType](opentype-font-features.md)
- [Rysowanie formatowanego tekstu](drawing-formatted-text.md)
- [Zaawansowane formatowanie tekstu](advanced-text-formatting.md)
- [Text](optimizing-performance-text.md)
- [Typografia firmy Microsoft](https://docs.microsoft.com/typography/)
