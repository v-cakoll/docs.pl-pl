---
title: Typografia w WPF
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
ms.openlocfilehash: 16897413c31e39be5c1d45b43d6ef816d3f80aad
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482694"
---
# <a name="typography-in-wpf"></a>Typografia w WPF
W tym temacie przedstawiono główne funkcje związane z typografią [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Te funkcje obejmują poprawy jakości i wydajności renderowania tekstu [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] typografii obsługi rozszerzonego tekstu międzynarodowe, rozszerzona obsługa czcionek i interfejsy programowania aplikacji w usłudze nowy tekst (API).  
  
<a name="Improved_Quality_and_Performance_of_Text"></a>   
## <a name="improved-quality-and-performance-of-text"></a>Poprawy jakości i wydajności tekstu  
 Tekst w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest renderowany przy użyciu [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)], która rozszerza, przejrzystości i czytelności, tekstu. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] jest to technologia oprogramowanie opracowane przez [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] który poprawia czytelność tekstu na istniejące LCD (należy zmienić.), takie jak ekranów komputerów przenośnych, ekrany Pocket PC i monitory płaskie. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] korzysta z renderowania podrzędnych pikseli, umożliwiający tekst ma być wyświetlany z większą wierność na jego true kształt znakami wyrównywanie na część ułamkową piksela. Dodatkowe rozwiązanie zwiększa ostrość niewielki Szczegóły sposobu wyświetlania tekstu, znacznie ułatwiając przeczytaniu długim czasie trwania. Ulepszanie innego [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest kierunku y wygładzanie, który wygładza stacjonarne i dołu krzywych płytka w znakach tekstu. Aby uzyskać szczegółowe informacje na temat [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] funkcje, zobacz [ClearType — Przegląd](cleartype-overview.md).  
  
 ![Tekst z ClearType y&#45;kierunek ochrony przed złośliwym&#45;aliasów](./media/typographyinwpf02.gif "TypographyInWPF02")  
Tekst z antialiasingu kierunku y ClearType  
  
 Potok renderowania całego tekstu można przyspieszanych sprzętowo w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pod warunkiem Twoja maszyna spełnia minimalnego wymagania sprzętowe. Renderowanie, nie można wykonać przy użyciu sprzętu powróci do renderowania oprogramowania. Przyspieszanie sprzętowe wpływa na wszystkich etapach potoku renderowania tekstu — przechowywanie poszczególnych symbole, symbole składania do uruchomienia symbol stosowanie efektów, zastosowanie [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] mieszania algorytm końcowych danych wyjściowych wyświetlanych. Aby uzyskać więcej informacji na temat przyspieszania sprzętowego, zobacz [poziomy renderowania grafiki](graphics-rendering-tiers.md).  
  
 ![Diagram potoku renderowania tekstu](./media/typographyinwpf01.png "TypographyInWPF01")  
Diagram potoku renderowania tekstu  
  
 Ponadto animacji tekstu przez znaku lub symbolu, w pełni korzysta grafiki możliwości sprzętu przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Skutkuje to animacji smooth tekstu.  
  
<a name="Rich_Typography"></a>   
## <a name="rich-typography"></a>Rozbudowane typografii  
 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] Format czcionki jest rozszerzeniem [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] format czcionek. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] Format czcionek została opracowana wspólnie przez [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] i Adobe i zapewnia bogate gamę zaawansowane funkcje związane z typografią. <xref:System.Windows.Documents.Typography> Obiekt udostępnia wiele zaawansowanych funkcji [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] czcionki, takie jak stylistyczne i kaligraficzne. [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)] Udostępnia zestaw przykładowych [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] czcionek, które są skonstruowane z zaawansowanych funkcji, takich jak Perykles i Pescadero czcionki. Aby uzyskać więcej informacji, zobacz [przykład pakietu czcionek OpenType](sample-opentype-font-pack.md).  
  
 Perykles [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] czcionki zawiera dodatkowe symbole, zapewniających stylistyczne do standardowego zestawu symbole. Następujący tekst Wyświetla stylistyczne alternatywne symbole.  
  
 ![Tekst stylistyczne alternatywne symbole OpenType](./media/typography-in-wpf/opentype-stylistic-alternate-glyphs.gif "tekst stylistyczne alternatywne symbole OpenType")  
  
 Kaligraficzne są symbole dekoracyjnych, korzystających z rozbudowanych ornamentacji często skojarzony kaligrafia. Następujący tekst, wyświetla standardowe i kaligraficzne symbole Pescadero czcionki.  
  
 ![Tekst z użyciem glifów standardowe i kaligraficzne OpenType](./media/typography-in-wpf/opentype-standard-swash-glyphs.gif "tekst z użyciem glifów standardowe i kaligraficzne OpenType")  
  
 Aby uzyskać szczegółowe informacje na temat [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] funkcje, zobacz [funkcje czcionki OpenType](opentype-font-features.md).  
  
<a name="Enhanced_International_Text_Support"></a>   
## <a name="enhanced-international-text-support"></a>Obsługa rozszerzonego tekstu międzynarodowych  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapewnia obsługę rozszerzonych tekst międzynarodowy, podając następujące funkcje:  
  
-   Automatyczne — interlinia we wszystkich systemach piśmie, przy użyciu adaptacyjne miary.  
  
-   Obsługi szerokiej gamy międzynarodowych tekstu. Aby uzyskać więcej informacji, zobacz [globalizacja dla WPF](globalization-for-wpf.md).  
  
-   Dzielenie wierszy z przewodnikiem języka, dzielenie wyrazów i uzasadnienie.  
  
<a name="Enhanced_Font_Support"></a>   
## <a name="enhanced-font-support"></a>Obsługa czcionek rozszerzone  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapewnia obsługę rozszerzonych czcionki, podając następujące funkcje:  
  
-   Unicode dla całego tekstu. Zachowanie czcionki i zaznaczenia nie są już wymagać charset lub stronę kodową.  
  
-   Zachowanie czcionka jest niezależne od ustawień globalnych, takich jak ustawienia regionalne systemu.  
  
-   Oddzielne <xref:System.Windows.FontWeight>, <xref:System.Windows.FontStretch>, i <xref:System.Windows.FontStyle> typów do definiowania <xref:System.Windows.Media.FontFamily>. Zapewnia to większą elastyczność niż w [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] programowania, w których atrybut typu wartość logiczna kombinacji kursywę i pogrubienie są używane do definiowania rodzinę czcionek.  
  
-   Zapisywanie kierunek (w poziomie i w pionie) obsługiwane niezależnie od nazwę czcionki.  
  
-   Łączenie czcionek i czcionka fallback na przenośnym [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] plików, przy użyciu technologii złożonego czcionki. Czcionki umożliwiają konstrukcji wielojęzyczny czcionek używanej do próby spośród całego zakresu. Czcionki udostępniają mechanizm, który pozwala uniknąć wyświetlania Brak symbole. Aby uzyskać więcej informacji, zobacz uwagi w <xref:System.Windows.Media.FontFamily> klasy.  
  
-   Międzynarodowe czcionki, utworzony na podstawie złożonego czcionek, za pomocą grupy czcionek w jednym języku. Zapisuje to koszty zasobów podczas tworzenia czcionki dla wielu języków.  
  
-   Czcionki osadzony w dokumencie, zapewniając w ten sposób przenoszenia dokumentu. Aby uzyskać więcej informacji, zobacz uwagi w <xref:System.Windows.Media.FontFamily> klasy.  
  
<a name="New_Text_APIs"></a>   
## <a name="new-text-application-programming-interfaces-apis"></a>Nowy tekst interfejsy programowania aplikacji (API)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera kilka tekst [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] dla deweloperów do użycia podczas łącznie z tekstem w swoich aplikacjach. Te [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] są podzielone na trzy kategorie:  
  
-   **Układ i interfejsu użytkownika**. Wspólny tekst kontrolki do [!INCLUDE[TLA#tla_gui](../../../../includes/tlasharptla-gui-md.md)].  
  
-   **Uproszczone rysowania tekstu**. Można rysować tekst bezpośrednio do obiektów.  
  
-   **Zaawansowane formatowanie tekstu**. Pozwala na implementowanie aparatu niestandardowego tekstu.  
  
### <a name="layout-and-user-interface"></a>Układ i interfejsu użytkownika  
 Na najwyższym poziomie funkcjonalności, tekst [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] zapewnić wspólnego [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] kontrolki, takie jak <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBlock>, i <xref:System.Windows.Controls.TextBox>. Te elementy sterujące udostępniają podstawowe [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementów w obrębie aplikacji i oferty w prosty sposób obecne i wchodzić w interakcje z tekstem. Określa, takich jak <xref:System.Windows.Controls.RichTextBox> i <xref:System.Windows.Controls.PasswordBox> Włącz bardziej zaawansowany lub wyspecjalizowane obsługi tekstu. Takie jak klasy i <xref:System.Windows.Documents.TextRange>, <xref:System.Windows.Documents.TextSelection>, i <xref:System.Windows.Documents.TextPointer> Włącz manipulacja tekstem przydatne. Te [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy sterujące udostępniają właściwości <xref:System.Windows.Controls.Control.FontFamily%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, i <xref:System.Windows.Controls.Control.FontStyle%2A>, które umożliwiają kontrolowanie czcionki, który jest używany do renderowania tekstu.  
  
#### <a name="using-bitmap-effects-transforms-and-text-effects"></a>Przy użyciu efektów mapy bitowej, transformacji i efektów tekstowych  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Umożliwia tworzenie wizualnie interesujące używa tekstu przez korzysta z funkcji takich jak efektów mapy bitowej, transformacji i efektów tekstowych. Poniższy kod przedstawia typowy typ efektem cienia tekstu.  
  
 ![Cień tekstu z miękkości &#61; 0,25](./media/shadowtext01.jpg "ShadowText01")  
Tekst z cień  
  
 Poniższy przykład pokazuje efektem cienia i szumu tekstu.  
  
 ![Cień tekstu z szumu](./media/shadowtext04.jpg "ShadowText04")  
Tekst z Cień i hałasu  
  
 Poniższy przykład przedstawia efekt zewnętrzna poświata tekstu.  
  
 ![Cień tekstu z użyciem efektu OuterGlowBitmapEffect](./media/shadowtext05.jpg "ShadowText05")  
Tekst z efektem zewnętrzna poświata  
  
 Poniższy przykład przedstawia efekt rozmycia tekstu.  
  
 ![Cień tekstu przy użyciu BlurBitmapEffect](./media/shadowtext06.jpg "ShadowText06")  
Tekst z efektem Rozmycie  
  
 Poniższy przykład pokazuje, drugi wiersz tekstu skalowania przez 150% wzdłuż osi x, a trzeci wiersz tekstu skalowania przez 150% wzdłuż osi y.  
  
 ![Tekst skalowane za pomocą ScaleTransform](./media/transformedtext02.jpg "TransformedText02")  
Tekst przy użyciu ScaleTransform  
  
 Poniższy przykład pokazuje tekst skośny wzdłuż osi x.  
  
 ![Tekst skośny przy użyciu metody SkewTransform](./media/transformedtext03.jpg "TransformedText03")  
Tekst przy użyciu SkewTransform  
  
 A <xref:System.Windows.Media.TextEffect> obiekt jest obiektem pomocnika umożliwiająca traktuje tekst jako co najmniej jedną grupę znaków w ciągu tekstowym. Poniższy przykład pokazuje za pojedynczy znak. Każdy znak jest obracana niezależnie w odstępach czasu 1 sekundę.  
  
 ![Zrzut ekranu przedstawiający efekt obrócenia tekstu](./media/texteffect01.jpg "TextEffect01")  
Przykład rotacji animacji efekt tekstu  
  
#### <a name="using-flow-documents"></a>Używanie dokumentów przepływu  
 Oprócz typowe [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kontrolek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferuje kontrolkę układu, aby obejrzeć prezentację tekstu — <xref:System.Windows.Documents.FlowDocument> elementu. <xref:System.Windows.Documents.FlowDocument> Elementu w połączeniu z <xref:System.Windows.Controls.DocumentViewer> elementu udostępnia kontrolkę do dużych ilości tekstu ze zróżnicowanymi wymagania związane z układem. Układ kontrolki zapewniają dostęp do zaawansowanych typografii za pośrednictwem <xref:System.Windows.Documents.Typography> obiektu i właściwości związane z czcionki innych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kontrolki.  
  
 W poniższym przykładzie pokazano tekstu, zawartości hostowanej w <xref:System.Windows.Controls.FlowDocumentReader>, która umożliwia wyszukiwanie, nawigacji, dzielenia na strony i zawartości skalowanie pomocy technicznej.  
  
 ![Przykład użycia czcionek OpenType zrzut ekranu przedstawiający](./media/typographyinwpf-03.png "TypographyInWPF_03")  
Tekst hostowanych w FlowDocumentReader  
  
 Aby uzyskać więcej informacji, zobacz [dokumenty w WPF](documents-in-wpf.md).  
  
### <a name="lightweight-text-drawing"></a>Rysowanie tekstu lekkie  
 Rysowanie tekstu w bezpośrednio do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektów przy użyciu <xref:System.Windows.Media.DrawingContext.DrawText%2A> metody <xref:System.Windows.Media.DrawingContext> obiektu. Aby użyć tej metody, należy utworzyć <xref:System.Windows.Media.FormattedText> obiektu. Ten obiekt umożliwia rysowanie tekstu wielowierszowego, w którym każdy znak w tekście mogą indywidualnie sformatowane. Funkcje <xref:System.Windows.Media.FormattedText> obiekt zawiera wiele funkcji flagi DrawText w interfejsie API Win32. Ponadto <xref:System.Windows.Media.FormattedText> obiekt zawiera funkcje, takie jak obsługa wielokropka, w którym wielokropka jest wyświetlane, gdy tekst przekracza jego granice. Poniższy przykład pokazuje tekst, który ma kilka formatów zastosowano, tym gradientu liniowego na drugi i trzeci słów.  
  
 ![Tekst wyświetlany za pomocą obiektu FormattedText](./media/formattedtext01.jpg "FormattedText01")  
Przy użyciu obiektu FormattedText wyświetlanego tekstu.  
  
 Możesz przekonwertować sformatowany tekst do <xref:System.Windows.Media.Geometry> obiektów, co pozwala na tworzenie innych rodzajów wizualnie tekstu. Na przykład można utworzyć <xref:System.Windows.Media.Geometry> obiektu oparte na konspekt ciąg tekstowy.  
  
 ![Kontur tekstu przy użyciu pędzel gradientów liniowych](./media/outlinedtext02.jpg "OutlinedText02")  
Kontur tekstu przy użyciu pędzel gradientów liniowych  
  
 Poniższe przykłady ilustrują kilka sposobów tworzenia efektów wizualnych interesujące, modyfikując obrysu, wypełnij i wyróżnienie tekst skonwertowany.  
  
 ![Tekst w różnych kolorach wypełnienia i pociągnięcia](./media/outlinedtext03.jpg "OutlinedText03")  
Przykład ustawień obrysu i wypełnienia na różne kolory  
  
 ![Tekst z ImageBrush zastosowany do obrysu](./media/outlinedtext04.jpg "OutlinedText04")  
Przykład ImageBrush dotyczą pociągnięcia  
  
 ![Tekst z ImageBrush zastosowany do obrysu](./media/outlinedtext05.jpg "OutlinedText05")  
Przykład ImageBrush stosowane do obrysu i wyróżnienia  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.FormattedText> obiektu, zobacz [Rysowanie tekstu w formacie](drawing-formatted-text.md).  
  
### <a name="advanced-text-formatting"></a>Zaawansowane formatowanie tekstu  
 Najbardziej zaawansowane poziom tekst [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferuje możliwość utworzenia układu niestandardowego tekstu przy użyciu <xref:System.Windows.Media.TextFormatting.TextFormatter> obiektu a innymi typami danych w <xref:System.Windows.Media.TextFormatting> przestrzeni nazw. <xref:System.Windows.Media.TextFormatting.TextFormatter> i skojarzonych klas można zaimplementować układ niestandardowy tekst, który obsługuje własnych definicji formatów znaków, style akapitu wiersz reguł podziału, a inne układ funkcji międzynarodowych tekstu. Istnieje bardzo nielicznych przypadkach, w których chcesz zastąpić domyślną implementację elementu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługi układu tekstu. Jednak jeśli podczas tworzenia edycji formantu lub aplikacji tekstu, możesz wymagać inną implementację niż domyślna [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementacji.  
  
 W przeciwieństwie do tradycyjnych tekstu [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)], <xref:System.Windows.Media.TextFormatting.TextFormatter> wchodzi w interakcję z klientem układu tekstu za pomocą zestawu metod wywołania zwrotnego. Wymaga od klienta zapewnienia tych metod w celu wykonania <xref:System.Windows.Media.TextFormatting.TextSource> klasy. Na poniższym diagramie przedstawiono interakcje układu tekstu między aplikacji klienckiej i <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Diagram klienta układu tekstu i obiekt TextFormatter](./media/textformatter01.png "TextFormatter01")  
Interakcja między aplikacją i obiekt TextFormatter  
  
 Aby uzyskać więcej informacji na temat tworzenia układu niestandardowego tekstu, zobacz [zaawansowane formatowanie tekstu](advanced-text-formatting.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.FormattedText>
- <xref:System.Windows.Media.TextFormatting.TextFormatter>
- [ClearType — przegląd](cleartype-overview.md)
- [Funkcje czcionki OpenType](opentype-font-features.md)
- [Rysowanie formatowanego tekstu](drawing-formatted-text.md)
- [Zaawansowane formatowanie tekstu](advanced-text-formatting.md)
- [Text](optimizing-performance-text.md)
- [Microsoft Typography](https://docs.microsoft.com/typography/)