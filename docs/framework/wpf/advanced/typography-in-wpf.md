---
title: Typografia w WPF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 28c51c6208bfdfe068b9fb3ed2cdc58dd0350fdb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="typography-in-wpf"></a>Typografia w WPF
W tym temacie przedstawiono główne funkcje związane z typografią [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Te funkcje obejmują lepszą jakość i wydajność renderowanie tekstu [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] typografii pomocy technicznej, rozszerzone tekstu międzynarodowe, rozszerzona obsługa czcionek i interfejsy programowania aplikacji w usłudze nowy tekst (API).  
  

  
<a name="Improved_Quality_and_Performance_of_Text"></a>   
## <a name="improved-quality-and-performance-of-text"></a>Poprawy jakości i wydajności tekstu  
 Tekst w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest renderowany przy użyciu [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)], która zwiększa jasności i czytelność tekstu. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]jest to technologia oprogramowania opracowane przez [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] która poprawia czytelność tekstu w istniejących LCDs (należy zmienić.), takie jak ekranów komputerów przenośnych, Pocket PC ekrany i prosty monitory. [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)]używa renderowania podrzędne pikseli, dzięki czemu tekst wyświetlany z większą dokładność do jego kształtu true znakami wyrównywanie ułamkową część piksel. Dodatkowe rozpoznawania zwiększa ostrość szczegóły niewielki rozmiar wyświetlania tekstu, co znacznie ułatwia odczytanie przez długi czas trwania. Poprawa innego [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest kierunku y wygładzanie, która wygładza stacjonarne i dołu skrócona krzywych w znaki tekstu. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] funkcji, zobacz [omówienie ClearType](../../../../docs/framework/wpf/advanced/cleartype-overview.md).  
  
 ![Tekst z & ClearType y 45; kierunek anty &#45; aliasów](../../../../docs/framework/wpf/advanced/media/typographyinwpf02.gif "TypographyInWPF02")  
Tekst z ClearType antialiasingu kierunku y  
  
 Potoku renderowania cały tekst może być przyspieszane w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pod warunkiem, że komputer spełnia minimalnego wymagania sprzętowe. Renderowanie, którego nie można wykonać przy użyciu sprzętu powróci do renderowania oprogramowania. Przyspieszanie sprzętowe ma wpływ na wszystkich etapach potoku renderowania tekstu — zapisywanie poszczególnych symboli, składania symboli do symbolu serii, efekty, do stosowania [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] mieszania algorytmu do końcowego wyświetlanych wyników. Aby uzyskać więcej informacji na temat sprzętowego przyspieszania, zobacz [warstw renderowania grafiki](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
 ![Diagram potoku renderowania tekstu](../../../../docs/framework/wpf/advanced/media/typographyinwpf01.png "TypographyInWPF01")  
Diagram potoku renderowania tekstu  
  
 Ponadto animacji tekstu przez znaku lub symbolu, w pełni korzysta grafiki możliwości sprzętowe włączane przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Powoduje to animacji smooth tekstu.  
  
<a name="Rich_Typography"></a>   
## <a name="rich-typography"></a>Typografia RTF  
 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] Format czcionki jest rozszerzeniem [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] format czcionki. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] Format czcionki został opracowany przez wspólnie [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] i Adobe i udostępnia bogate gamę zaawansowane funkcje związane z typografią. <xref:System.Windows.Documents.Typography> Obiekt udostępnia wiele zaawansowanych funkcji [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] czcionek, takie jak alternatyw stylistycznych i kaligraficzne. [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)] Zawiera zestaw próbki [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] czcionek z zaawansowanych funkcji, takich jak Perykles i Pescadero czcionki. Aby uzyskać więcej informacji, zobacz [przykładowym pakiecie czcionek OpenType](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md).  
  
 Perykles [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] czcionka zawiera symbole dodatkowe, które zapewniają alternatyw stylistycznych do standardowego zestawu symboli. Następujący tekst Wyświetla stylistycznych alternatywnych symboli.  
  
 ![Tekst stylistycznych alternatywne symbole OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont02.gif "opentypefont02")  
Tekst stylistycznych alternatywne symbole OpenType  
  
 Kaligraficzne są ozdobne symbole, używające rozbudowane ornamentacji często skojarzone z kaligrafia. Następujący tekst, wyświetla standardowe i kaligraficzne symbole czcionki Pescadero.  
  
 ![Tekst standardowe i kaligraficzne symbole OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont08.gif "opentypefont08")  
Tekst standardowe i kaligraficzne symbole OpenType  
  
 Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] funkcji, zobacz [funkcji czcionek OpenType](../../../../docs/framework/wpf/advanced/opentype-font-features.md).  
  
<a name="Enhanced_International_Text_Support"></a>   
## <a name="enhanced-international-text-support"></a>Obsługa rozszerzonego tekstu międzynarodowych  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zapewnia obsługę rozszerzonych tekst międzynarodowy podając następujące funkcje:  
  
-   Automatyczne wiersza odstępy we wszystkich systemach zapisu, przy użyciu adaptacyjną miary.  
  
-   Szerokie Obsługa międzynarodowych tekstu. Aby uzyskać więcej informacji, zobacz [globalizacji dla WPF](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md).  
  
-   Dzielenie wierszy z przewodnikiem języka, dzielenie wyrazów oraz uzasadnienie.  
  
<a name="Enhanced_Font_Support"></a>   
## <a name="enhanced-font-support"></a>Obsługa czcionek rozszerzone  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zapewnia obsługę rozszerzonych czcionki podając następujące funkcje:  
  
-   Unicode dla całego tekstu. Zachowanie czcionki i zaznaczenia nie wymagają charset lub stronę kodową.  
  
-   Zachowanie czcionki niezależnie od ustawień globalnych, takich jak ustawienia regionalne systemu.  
  
-   Oddzielne <xref:System.Windows.FontWeight>, <xref:System.Windows.FontStretch>, i <xref:System.Windows.FontStyle> typów określających <xref:System.Windows.Media.FontFamily>. Zapewnia to większą elastyczność niż w [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] programowania, w którym wartość logiczna kombinacje kursywą i pogrubione są używane do definiowania rodziny czcionek.  
  
-   Pisanie kierunek (poziome i pionowe) obsługiwane zależy od nazwy czcionki.  
  
-   Łączenie czcionek i czcionki na przenośnym [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] plików, przy użyciu technologii czcionek złożonych. Zezwalaj czcionki do budowy czcionki wielojęzyczny pełnego zakresu. Czcionki udostępniają mechanizm, który pozwala uniknąć wyświetlania Brak symboli. Aby uzyskać więcej informacji, zobacz uwagi w <xref:System.Windows.Media.FontFamily> klasy.  
  
-   Międzynarodowe czcionki zbudowane na podstawie czcionki, za pomocą grupy czcionek w jednym języku. To jest zapisywany kosztów zasobów podczas opracowywania czcionki dla wielu języków.  
  
-   Czcionki osadzony w dokumencie, zapewniając przenośność dokumentu. Aby uzyskać więcej informacji, zobacz uwagi w <xref:System.Windows.Media.FontFamily> klasy.  
  
<a name="New_Text_APIs"></a>   
## <a name="new-text-application-programming-interfaces-apis"></a>Nowy tekst interfejsy programowania aplikacji (API)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]udostępnia kilka tekst [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] dla deweloperów do użycia podczas łącznie z tekstem w swoich aplikacjach. Te [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] są podzielone na trzy kategorie:  
  
-   **Układ i interfejs**. Typowe tekst kontrolki do [!INCLUDE[TLA#tla_gui](../../../../includes/tlasharptla-gui-md.md)].  
  
-   **Lekkie rysowania tekstu**. Umożliwia rysowanie tekstu bezpośrednio do obiektów.  
  
-   **Zaawansowane, formatowanie tekstu**. Umożliwia Implementowanie aparatu niestandardowego tekstu.  
  
### <a name="layout-and-user-interface"></a>Układ i interfejsu użytkownika  
 Na najwyższym poziomie funkcjonalności, tekst [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] Podaj wspólnej [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] formanty, takie jak <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBlock>, i <xref:System.Windows.Controls.TextBox>. Te elementy sterujące udostępniają podstawowe [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementów wewnątrz aplikacji i oferty w prosty sposób stanowią i interakcję z tekstem. Określa, takich jak <xref:System.Windows.Controls.RichTextBox> i <xref:System.Windows.Controls.PasswordBox> Włącz bardziej zaawansowane lub specjalizowany obsługi tekstu. Takich jak klasy i <xref:System.Windows.Documents.TextRange>, <xref:System.Windows.Documents.TextSelection>, i <xref:System.Windows.Documents.TextPointer> włączyć manipulowania przydatne tekstu. Te [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy sterujące udostępniają właściwości <xref:System.Windows.Controls.Control.FontFamily%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, i <xref:System.Windows.Controls.Control.FontStyle%2A>, które umożliwiają kontrolowanie czcionki, który jest używany do renderowania tekstu.  
  
#### <a name="using-bitmap-effects-transforms-and-text-effects"></a>Przy użyciu mapy bitowej efekty, transformacji i efektów tekstowych  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Służy do tworzenia wizualnego interesujące używa tekstu przez korzysta z funkcji takich jak efekty mapy bitowej, transformacji i efektów tekstowych. Poniższy przykład przedstawia typowy typ efektem cienia tekstu.  
  
 ![Cień tekstu z miękkości &#61; 0,25](../../../../docs/framework/wpf/advanced/media/shadowtext01.jpg "ShadowText01")  
Tekst z cień  
  
 W poniższym przykładzie przedstawiono efekt cienia i szumu zastosowany do tekstu.  
  
 ![Cień tekstu z szumu](../../../../docs/framework/wpf/advanced/media/shadowtext04.jpg "ShadowText04")  
Tekst z Cień i hałasu  
  
 W poniższym przykładzie przedstawiono zastosowany do tekstu efekt zewnętrzny.  
  
 ![Cień tekstu z użyciem efektu OuterGlowBitmapEffect](../../../../docs/framework/wpf/advanced/media/shadowtext05.jpg "ShadowText05")  
Tekst z efektem zewnętrzny  
  
 W poniższym przykładzie przedstawiono efekt rozmycia zastosowany do tekstu.  
  
 ![Cień tekstu przy użyciu BlurBitmapEffect](../../../../docs/framework/wpf/advanced/media/shadowtext06.jpg "ShadowText06")  
Tekst z efektem rozmycia  
  
 W poniższym przykładzie pokazano drugi wiersz tekstu skalowania o 150% wzdłuż osi x, a trzeci wiersz tekstu skalowania o 150% wzdłuż osi y.  
  
 ![Tekst wyskalowany przy użyciu ScaleTransform](../../../../docs/framework/wpf/advanced/media/transformedtext02.jpg "TransformedText02")  
Tekst przy użyciu ScaleTransform  
  
 W poniższym przykładzie przedstawiono tekst niesymetryczna wzdłuż osi x.  
  
 ![Tekst niesymetryczna przy użyciu metody SkewTransform](../../../../docs/framework/wpf/advanced/media/transformedtext03.jpg "TransformedText03")  
Tekst przy użyciu SkewTransform  
  
 A <xref:System.Windows.Media.TextEffect> obiekt jest obiektem pomocnika, która pozwala na traktowanie tekstu jako jedną lub więcej grup znaków w ciągu tekstowym. W poniższym przykładzie przedstawiono indywidualnym za. Każdy znak jest obracana niezależnie w odstępach czasu 1 sekundę.  
  
 ![Zrzut ekranu przedstawiający efekt obrócenia tekstu](../../../../docs/framework/wpf/advanced/media/texteffect01.jpg "TextEffect01")  
Przykład obracania animacji efekt tekstu  
  
#### <a name="using-flow-documents"></a>Używanie dokumentów przepływu  
 Oprócz typowe [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] formantów, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia kontrolkę układu tekstu prezentacji — <xref:System.Windows.Documents.FlowDocument> elementu. <xref:System.Windows.Documents.FlowDocument> Elementu w połączeniu z <xref:System.Windows.Controls.DocumentViewer> elementu udostępnia kontrolkę do dużych ilości tekstu ze zróżnicowanymi wymagania układu. Formanty układu zapewniają dostęp do zaawansowanych typografii za pośrednictwem <xref:System.Windows.Documents.Typography> obiekt i właściwości związanych z czcionki innych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] kontrolki.  
  
 W poniższym przykładzie przedstawiono tekst zawartości hostowanej w <xref:System.Windows.Controls.FlowDocumentReader>, zapewniające wyszukiwania, nawigacji podział na strony i zawartości skalowanie pomocy technicznej.  
  
 ![Przykład użycia czcionek OpenType zrzut ekranu](../../../../docs/framework/wpf/advanced/media/typographyinwpf-03.png "TypographyInWPF_03")  
Tekst w FlowDocumentReader  
  
 Aby uzyskać więcej informacji, zobacz [dokumentów na platformie WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
### <a name="lightweight-text-drawing"></a>Rysowanie tekstu lekkie  
 Rysowanie tekstu w bezpośrednio do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obiektów przy użyciu <xref:System.Windows.Media.DrawingContext.DrawText%2A> metody <xref:System.Windows.Media.DrawingContext> obiektu. Aby użyć tej metody, należy utworzyć <xref:System.Windows.Media.FormattedText> obiektu. Ten obiekt umożliwia rysowanie tekstu w wielu wierszach, w którym każdy znak w tekście można osobno sformatowany. Funkcje <xref:System.Windows.Media.FormattedText> obiekt zawiera wiele funkcji flagi DrawText w interfejsie API Win32. Ponadto <xref:System.Windows.Media.FormattedText> obiektu zawiera funkcje, takie jak obsługa wielokropka, w którym wielokropek jest wyświetlane, gdy tekst przekracza jej zakresem. W poniższym przykładzie przedstawiono tekst, który ma kilka formatów zastosowane, tym gradientu liniowego, drugi i trzeci słowa.  
  
 ![Tekst wyświetlany przy użyciu obiektu FormattedText](../../../../docs/framework/wpf/advanced/media/formattedtext01.jpg "FormattedText01")  
Przy użyciu obiektu FormattedText wyświetlanego tekstu.  
  
 Możesz przekształcić tekst sformatowany do <xref:System.Windows.Media.Geometry> obiektów, pozwala na tworzenie innych typów wizualnie tekstu. Na przykład można utworzyć <xref:System.Windows.Media.Geometry> obiektu oparte na konturu ciąg tekstowy.  
  
 ![Używanie pędzla gradientu liniowego konspektu tekstu](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")  
Używanie pędzla gradientu liniowego konspektu tekstu  
  
 Poniższe przykłady przedstawiają kilka sposobów tworzenia interesujące efekty wizualne, modyfikując obrysu, wypełnij i wyróżnianie tekstu przekonwertowany.  
  
 ![Tekst z różnymi kolorami wypełnienia i pociągnięcia](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")  
Przykładowa konfiguracja obrysu i wypełnienia do różnych kolorów  
  
 ![Tekst z pędzel obrazu na obrysu](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")  
Przykład pędzel obrazu na obrysu  
  
 ![Tekst z pędzel obrazu na obrysu](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")  
Przykład pędzel obrazu na obrysu i wyróżnienia  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.FormattedText> obiektów, zobacz [Rysowanie tekstu w formacie](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md).  
  
### <a name="advanced-text-formatting"></a>Zaawansowane formatowanie tekstu  
 Najbardziej zaawansowane poziom tekst [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oferuje możliwość tworzenia układu niestandardowego tekstu przy użyciu <xref:System.Windows.Media.TextFormatting.TextFormatter> obiektu i innych typów w <xref:System.Windows.Media.TextFormatting> przestrzeni nazw. <xref:System.Windows.Media.TextFormatting.TextFormatter> i skojarzonych klas Zezwól można zapewnić układu niestandardowego tekstu, który obsługuje własnych definicji formatu znaków, style akapitu wiersz reguł podziału i innych układu funkcje międzynarodowe tekstu. Istnieje bardzo mało przypadków, w których należy zastąpić domyślną implementację elementu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Obsługa układu tekstu. Jednak jeśli zostały Tworzenie tekstu edycji formant lub aplikacji, można wymagać inną implementację niż domyślne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementacji.  
  
 W przeciwieństwie do tradycyjnych tekst [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)], <xref:System.Windows.Media.TextFormatting.TextFormatter> wchodzi w interakcję z klientem układu tekstu za pomocą zestawu metod wywołania zwrotnego. Wymaga od klienta zapewnienia tych metod w celu wykonania <xref:System.Windows.Media.TextFormatting.TextSource> klasy. Na poniższym diagramie przedstawiono układu tekstu współdziałanie aplikacji klienckiej i <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Diagram klienta układu tekstu i obiekt TextFormatter](../../../../docs/framework/wpf/advanced/media/textformatter01.png "TextFormatter01")  
Interakcja między aplikacją a obiekt TextFormatter  
  
 Aby uzyskać więcej informacji na temat tworzenia układu niestandardowego tekstu, zobacz [zaawansowane formatowania tekstu](../../../../docs/framework/wpf/advanced/advanced-text-formatting.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.FormattedText>  
 <xref:System.Windows.Media.TextFormatting.TextFormatter>  
 [Omówienie ClearType](../../../../docs/framework/wpf/advanced/cleartype-overview.md)  
 [Funkcje czcionek OpenType](../../../../docs/framework/wpf/advanced/opentype-font-features.md)  
 [Rysowanie sformatowanego tekstu](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)  
 [Zaawansowane formatowanie tekstu](../../../../docs/framework/wpf/advanced/advanced-text-formatting.md)  
 [Tekst](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Typografia firmy Microsoft](http://www.microsoft.com/typography/default.mspx)
