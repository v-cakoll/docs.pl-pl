---
title: Typografia w WPF
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
ms.openlocfilehash: 0c98d0e7363e7732f44f2edf238b9cb6d2bf11fb
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740275"
---
# <a name="typography-in-wpf"></a>Typografia w WPF
W tym temacie przedstawiono główne funkcje typograficzne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Te funkcje obejmują ulepszoną jakość i wydajność renderowania tekstu, obsługę typografii OpenType, ulepszony międzynarodowy tekst, rozszerzoną obsługę czcionek oraz nowe interfejsy programowania aplikacji tekstowych (API).  
  
<a name="Improved_Quality_and_Performance_of_Text"></a>   
## <a name="improved-quality-and-performance-of-text"></a>Ulepszona jakość i wydajność tekstu  
 Tekst w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest renderowany przy użyciu technologii Microsoft ClearType, która zwiększa czytelność i czytelność tekstu. Technologia ClearType jest technologią oprogramowania opracowaną przez firmę Microsoft, która zwiększa czytelność tekstu w istniejących LCDs (w przypadku wyświetlaczy Liquid Crystal), takich jak ekrany laptopów, urządzenia Pocket PC i monitory płaskoekranowe. Technologia ClearType używa renderowania w pikselach, co pozwala na wyświetlanie tekstu z większą dokładnością do jego prawdziwego kształtu przez wyrównanie znaków w ułamkowej części piksela. Dodatkowe rozwiązanie zwiększa ostrość niewielkich szczegółów w wyświetlaniu tekstu, ułatwiając odczytywanie ich w dłuższym czasie. Innym ulepszeniem technologii ClearType w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest wygładzanie kierunku y, które wygładza górne i dolne płytki w znakach tekstowych. Aby uzyskać więcej informacji na temat funkcji ClearType, zobacz [Omówienie technologii ClearType](cleartype-overview.md).  
  
 ![Tekst z wygładzaniem kierunku x w technologii ClearType](./media/typography-in-wpf/text-y-direction-antialiasing.gif)  
Tekst z wygładzaniem kierunku y w technologii ClearType  
  
 Cały potok renderowania tekstu może być przyspieszeniem sprzętowym w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pod warunkiem, że maszyna spełnia minimalny wymagany poziom sprzętu. Renderowanie, które nie może zostać wykonane przy użyciu sprzętu, powraca do renderowania oprogramowania. Przyspieszenie sprzętowe wpływa na wszystkie fazy potoku renderowania tekstu — od przechowywania pojedynczych glifów, złożenia glifów do uruchomienia glifów, stosowania efektów, do zastosowania algorytmu mieszania ClearType do końcowych wyświetlanych danych wyjściowych. Aby uzyskać więcej informacji na temat przyspieszania sprzętowego, zobacz [warstwy renderowania grafiki](graphics-rendering-tiers.md).  
  
 ![Diagram potoku renderowania tekstu](./media/typography-in-wpf/text-rendering-pipeline.png)  
  
 Dodatkowo animowany tekst, niezależnie od znaku lub glifu, w pełni wykorzystuje możliwości sprzętowe grafiki włączone przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Powoduje to wygładzanie animacji tekstu.  
  
<a name="Rich_Typography"></a>   
## <a name="rich-typography"></a>Bogaty Typografia  
 Format czcionki OpenType to rozszerzenie czcionki TrueType®. Format czcionki OpenType został opracowany wspólnie przez firmę Microsoft i firmę Adobe oraz oferuje bogaty asortyment zaawansowanych funkcji typograficznych. Obiekt <xref:System.Windows.Documents.Typography> uwidacznia wiele zaawansowanych funkcji czcionek OpenType, takich jak alternatywy stylistyczne i znaki kaligraficzne. Windows SDK zawiera zestaw przykładowych czcionek OpenType, które są zaprojektowane z rozbudowanymi funkcjami, takimi jak czcionki Pericles i Pescadero. Aby uzyskać więcej informacji, zobacz [przykładowy pakiet czcionek OpenType](sample-opentype-font-pack.md).  
  
 Czcionka Pericles OpenType zawiera dodatkowe glify, które udostępniają alternatywy stylistyczne dla standardowego zestawu symboli. Następujący tekst zawiera stylistyczne glify alternatywne.  
  
 ![Tekst przy użyciu alternatywnych symboli OpenType](./media/typography-in-wpf/opentype-stylistic-alternate-glyphs.gif "Tekst przy użyciu alternatywnych symboli OpenType")  
  
 Znaki kaligraficzne to dekoracyjne glify, które używają wyrafinowanych elementów ozdobnych często skojarzonych z Calligraphy. Poniższy tekst zawiera standardowe i kaligraficzne glify dla czcionki Pescadero.  
  
 ![Tekst korzystający z symboli standardowych i kaligraficzne OpenType](./media/typography-in-wpf/opentype-standard-swash-glyphs.gif "Tekst korzystający z symboli standardowych i kaligraficzne OpenType")  
  
 Aby uzyskać więcej informacji na temat funkcji OpenType, zobacz [funkcje czcionek OpenType](opentype-font-features.md).  
  
<a name="Enhanced_International_Text_Support"></a>   
## <a name="enhanced-international-text-support"></a>Rozszerzona obsługa tekstu międzynarodowego  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapewnia rozszerzoną obsługę tekstu międzynarodowego, udostępniając następujące funkcje:  
  
- Automatyczne odstępy między liniami we wszystkich systemach pisania, przy użyciu funkcji adaptacyjnego pomiaru.  
  
- Szeroka pomoc techniczna dla tekstu międzynarodowego. Aby uzyskać więcej informacji, zobacz [globalizacja dla WPF](globalization-for-wpf.md).  
  
- Podział wierszy z przewodnikiem, dzielenie wyrazów i uzasadnienie.  
  
<a name="Enhanced_Font_Support"></a>   
## <a name="enhanced-font-support"></a>Ulepszona obsługa czcionek  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapewnia rozszerzoną obsługę czcionek, udostępniając następujące funkcje:  
  
- Unicode dla całego tekstu. Zachowanie czcionki i wybór nie wymagają już zestawu znaków lub strony kodowej.  
  
- Zachowanie czcionki niezależnie od ustawień globalnych, takich jak ustawienia regionalne systemu.  
  
- Oddzielne typy <xref:System.Windows.FontWeight>, <xref:System.Windows.FontStretch>i <xref:System.Windows.FontStyle> do definiowania <xref:System.Windows.Media.FontFamily>. Zapewnia to większą elastyczność niż w programowaniu Win32, w którym logiczne kombinacje kursywy i pogrubienie są używane do definiowania rodziny czcionek.  
  
- Kierunek pisania (w poziomie i w pionie) obsługiwany niezależnie od nazwy czcionki.  
  
- Łączenie czcionek i powrót do czcionki w przenośnym pliku XML przy użyciu technologii czcionek złożonych. Czcionki złożone umożliwiają tworzenie pełnych czcionek wielojęzycznych. Czcionki złożone zapewniają również mechanizm, który pozwala uniknąć wyświetlania brakujących symboli. Aby uzyskać więcej informacji, zobacz uwagi w klasie <xref:System.Windows.Media.FontFamily>.  
  
- Czcionki międzynarodowe zbudowane z czcionek kompozytowych przy użyciu grupy czcionek jednojęzykowych. Powoduje to zapisanie kosztów zasobów podczas tworzenia czcionek dla wielu języków.  
  
- Czcionki złożone osadzone w dokumencie, co zapewnia przenośność dokumentów. Aby uzyskać więcej informacji, zobacz uwagi w klasie <xref:System.Windows.Media.FontFamily>.  
  
<a name="New_Text_APIs"></a>   
## <a name="new-text-application-programming-interfaces-apis"></a>Nowe interfejsy programowania aplikacji tekstowych (API)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia kilka tekstowych interfejsów API, których deweloperzy mogą używać podczas dołączania tekstu do aplikacji. Te interfejsy API są pogrupowane w trzy kategorie:  
  
- **Układ i interfejs użytkownika**. Typowe kontrolki tekstu dla graficznego interfejsu użytkownika (GUI).  
  
- **Lekkie rysowanie tekstu**. Umożliwia narysowanie tekstu bezpośrednio do obiektów.  
  
- **Zaawansowane formatowanie tekstu**. Umożliwia zaimplementowanie niestandardowego aparatu tekstu.  
  
### <a name="layout-and-user-interface"></a>Układ i interfejs użytkownika  
 W przypadku najwyższego poziomu funkcjonalności interfejsy API tekstu udostępniają typowe formanty [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], takie jak <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBlock>i <xref:System.Windows.Controls.TextBox>. Te kontrolki zapewniają podstawowe elementy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] w aplikacji i oferują łatwy sposób prezentowania i współpracy z tekstem. Kontrolki, takie jak <xref:System.Windows.Controls.RichTextBox> i <xref:System.Windows.Controls.PasswordBox> umożliwiają bardziej zaawansowaną lub wyspecjalizowaną obsługę tekstu. I klasy takie jak <xref:System.Windows.Documents.TextRange>, <xref:System.Windows.Documents.TextSelection>i <xref:System.Windows.Documents.TextPointer> umożliwiają użyteczne manipulowanie tekstem. Te [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] formanty zapewniają właściwości, takie jak <xref:System.Windows.Controls.Control.FontFamily%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>i <xref:System.Windows.Controls.Control.FontStyle%2A>, które umożliwiają kontrolowanie czcionki używanej do renderowania tekstu.  
  
#### <a name="using-bitmap-effects-transforms-and-text-effects"></a>Używanie efektów mapy bitowej, transformacji i efektów tekstowych  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umożliwia tworzenie wizualnie interesujących sposobów użycia tekstu przy użyciu funkcji, takich jak efekty mapy bitowej, przekształcenia i efekty tekstowe. W poniższym przykładzie przedstawiono typowy efekt cienia, który został zastosowany do tekstu.  
  
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
  
 Obiekt <xref:System.Windows.Media.TextEffect> jest obiektem pomocnika, który umożliwia traktowanie tekstu jako co najmniej jednej grupy znaków w ciągu tekstowym. Poniższy przykład pokazuje, że pojedynczy znak jest obracany. Każdy znak jest obracany niezależnie w odstępach 1-sekundowych.  
  
 ![Zrzut ekranu przedstawiający tekst obracania efektu tekstu](./media/typography-in-wpf/rotating-text-effect.jpg) 
  
#### <a name="using-flow-documents"></a>Używanie dokumentów przepływu  
 Poza typowymi kontrolkami [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferuje kontrolkę układu dla prezentacji tekstowej — element <xref:System.Windows.Documents.FlowDocument>. Element <xref:System.Windows.Documents.FlowDocument>, w połączeniu z elementem <xref:System.Windows.Controls.DocumentViewer>, zapewnia kontrolę nad dużymi ilościami tekstu, które mają różne wymagania dotyczące układu. Kontrolki układu zapewniają dostęp do zaawansowanych typografii przy użyciu obiektu <xref:System.Windows.Documents.Typography> i właściwości związanych z czcionkami innych kontrolek [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Poniższy przykład przedstawia zawartość tekstową hostowaną w <xref:System.Windows.Controls.FlowDocumentReader>, która zapewnia obsługę wyszukiwania, nawigacji, stronicowania i skalowania zawartości.  
  
 ![Zrzut ekranu pokazujący czcionki OpenType.](./media/typography-in-wpf/typography-text-flowdocumentreader.png)
  
 Aby uzyskać więcej informacji, zobacz [dokumenty w WPF](documents-in-wpf.md).  
  
### <a name="lightweight-text-drawing"></a>Lekkie rysowanie tekstu  
 Możesz narysować tekst bezpośrednio do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektów przy użyciu metody <xref:System.Windows.Media.DrawingContext.DrawText%2A> obiektu <xref:System.Windows.Media.DrawingContext>. Aby użyć tej metody, należy utworzyć obiekt <xref:System.Windows.Media.FormattedText>. Ten obiekt umożliwia narysowanie tekstu wielowierszowego, w którym każdy znak w tekście może być sformatowany osobno. Funkcja obiektu <xref:System.Windows.Media.FormattedText> zawiera wiele funkcji flag DrawText w interfejsie API systemu Windows. Ponadto obiekt <xref:System.Windows.Media.FormattedText> zawiera funkcje, takie jak obsługa wielokropka, w którym jest wyświetlany wielokropek, gdy tekst przekracza jego granice. Poniższy przykład przedstawia tekst, do którego zastosowano kilka formatów, w tym gradient liniowy na drugim i trzecim wyrazie.  
  
 ![Tekst wyświetlany przy użyciu obiektu FormattedText](./media/typography-in-wpf/text-formatted-linear-gradient.jpg) 
  
 Możesz skonwertować sformatowany tekst na obiekty <xref:System.Windows.Media.Geometry>, co pozwala na tworzenie innych typów wizualnie interesujących. Na przykład można utworzyć obiekt <xref:System.Windows.Media.Geometry> na podstawie konturu ciągu tekstowego.  
  
 ![Kontur tekstu przy użyciu gradientu liniowego](./media/typography-in-wpf/text-outline-linear-gradient.jpg)  
  
 Poniższe przykłady ilustrują kilka sposobów tworzenia interesujących efektów wizualnych przez modyfikację obrysu, wypełnienia i wyróżnienia konwertowanego tekstu.  
  
 ![Tekst z różnymi kolorami dla wypełnienia i pociągnięcia](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Tekst z pędzlem obrazu zastosowany do pociągnięcia](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Tekst z pędzlem obrazu zastosowany do obrysu i wyróżnienia](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Aby uzyskać więcej informacji na temat obiektu <xref:System.Windows.Media.FormattedText>, zobacz [rysowanie sformatowanego tekstu](drawing-formatted-text.md).  
  
### <a name="advanced-text-formatting"></a>Zaawansowane formatowanie tekstu  
 Na najbardziej zaawansowanym poziomie interfejsów API tekstu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferuje możliwość tworzenia niestandardowego układu tekstu przy użyciu obiektu <xref:System.Windows.Media.TextFormatting.TextFormatter> i innych typów w <xref:System.Windows.Media.TextFormatting> przestrzeni nazw. <xref:System.Windows.Media.TextFormatting.TextFormatter> i skojarzone klasy umożliwiają wdrożenie niestandardowego układu tekstu, który obsługuje własną definicję formatów znaków, stylów akapitu, reguł podziału wierszy i innych funkcji układu dla tekstu międzynarodowego. Istnieje bardzo kilka przypadków, w których chcesz zastąpić domyślną implementację obsługi układu tekstu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Jeśli jednak tworzysz kontrolkę edycji tekstu lub aplikację, może być wymagana inna implementacja niż domyślna implementacja [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 W przeciwieństwie do tradycyjnego interfejsu API tekstu, <xref:System.Windows.Media.TextFormatting.TextFormatter> współdziała z klientem układu tekstu za pomocą zestawu metod wywołania zwrotnego. Wymaga, aby klient dostarczał te metody w implementacji klasy <xref:System.Windows.Media.TextFormatting.TextSource>. Na poniższym diagramie przedstawiono interakcje układu tekstu między aplikacją kliencką a <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Diagram klienta układu tekstu i elementu textformatującego](./media/typography-in-wpf/text-layout-text-formatter-interaction.png)  
  
 Aby uzyskać więcej informacji na temat tworzenia niestandardowego układu tekstu, zobacz [Zaawansowane formatowanie tekstu](advanced-text-formatting.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.FormattedText>
- <xref:System.Windows.Media.TextFormatting.TextFormatter>
- [ClearType — przegląd](cleartype-overview.md)
- [Funkcje czcionki OpenType](opentype-font-features.md)
- [Rysowanie formatowanego tekstu](drawing-formatted-text.md)
- [Zaawansowane formatowanie tekstu](advanced-text-formatting.md)
- [Tekst](optimizing-performance-text.md)
- [Typografia firmy Microsoft](https://docs.microsoft.com/typography/)
