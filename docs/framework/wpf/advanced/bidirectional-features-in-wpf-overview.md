---
title: Przegląd Dwukierunkowe funkcje WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Span elements [WPF]
- bidirectional features [WPF]
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
ms.openlocfilehash: b009c2503c7cbf6aca847fc7318135842a060f69
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965039"
---
# <a name="bidirectional-features-in-wpf-overview"></a>Przegląd Dwukierunkowe funkcje WPF
W przeciwieństwie do żadnej innej platformy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] deweloperskiej program oferuje wiele funkcji, które obsługują szybkie opracowywanie zawartości dwukierunkowej, na przykład mieszane od lewej do prawej i od prawej do lewej w tym samym dokumencie. W tym samym czasie program [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tworzy doskonałe środowisko dla użytkowników, którzy wymagają funkcji dwukierunkowych, takich jak arabski i hebrajski.  
  
 W poniższych sekcjach opisano wiele funkcji dwukierunkowych wraz z Przykładami ilustrującymi sposób osiągnięcia najlepszego sposobu wyświetlania zawartości dwukierunkowej. Większość przykładów używa [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], chociaż można łatwo zastosować koncepcje do C# kodu programu lub Microsoft Visual Basic Code.  

<a name="FlowDirection"></a>   
## <a name="flowdirection"></a>FlowDirection  
 Właściwość podstawowa, która definiuje kierunek przepływu zawartości w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, to. <xref:System.Windows.FrameworkElement.FlowDirection%2A> Tę właściwość można ustawić na jedną z dwóch wartości <xref:System.Windows.FlowDirection.LeftToRight> wyliczenia lub. <xref:System.Windows.FlowDirection.RightToLeft> Właściwość jest dostępna dla wszystkich [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementów, które dziedziczą z. <xref:System.Windows.FrameworkElement>  
  
 W poniższych przykładach ustawiono kierunek <xref:System.Windows.Controls.TextBox> przepływu elementu.  
  
 **Kierunek przepływu od lewej do prawej**  
  
 [!code-xaml[LTRRTL#LTR](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]  
  
 **Kierunek przepływu od prawej do lewej**  
  
 [!code-xaml[LTRRTL#RTL](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]  
  
 Na poniższej ilustracji przedstawiono sposób renderowania poprzedniego kodu.  
    
 ![Ilustracja, która ilustruje różne kierunki przepływu.](./media/bidirectional-features-in-wpf-overview/left-right-right-left.png)  
  
 Element w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] drzewie <xref:System.Windows.FrameworkElement.FlowDirection%2A> dziedziczy z jego kontenera. W poniższym przykładzie <xref:System.Windows.Controls.TextBlock> znajduje się <xref:System.Windows.Controls.Grid>wewnątrz, która znajduje się w <xref:System.Windows.Window>. <xref:System.Windows.Controls.TextBlock> Ustawienie ustawienia <xref:System.Windows.FrameworkElement.FlowDirection%2A> dlaustawień<xref:System.Windows.Controls.Grid> dotyczy również dla i. <xref:System.Windows.Window>  
  
 Poniższy przykład ilustruje ustawienie <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 [!code-xaml[FlowDirection#FlowDirection](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]  
  
 <xref:System.Windows.Window> Najwyższy poziom <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FrameworkElement.FlowDirection%2A>ma, więc wszystkie zawarte w nim elementy również dziedziczą te same. <xref:System.Windows.FlowDirection> Dla elementu, który ma zostać zastąpiony, <xref:System.Windows.FrameworkElement.FlowDirection%2A> musi dodać jawną zmianę kierunku, taką jak druga <xref:System.Windows.Controls.TextBlock> w poprzednim przykładzie, która zmienia <xref:System.Windows.FlowDirection.LeftToRight>się na. Gdy nie <xref:System.Windows.FrameworkElement.FlowDirection%2A> jest zdefiniowany, stosowane jest <xref:System.Windows.FlowDirection.LeftToRight> ustawienie domyślne.  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe poprzedniego przykładu:

 ![Ilustracja przedstawiająca jawną zmianę kierunku przepływu.](./media/bidirectional-features-in-wpf-overview/explicit-direction-change.png)  

<a name="FlowDocument"></a>   
## <a name="flowdocument"></a>FlowDocument  
 Wiele platform programistycznych, takich jak [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] HTML i Java, zapewnia specjalną obsługę tworzenia zawartości dwukierunkowej. Języki znaczników, takie jak HTML, dają autorom zawartości niezbędne znaczniki do wyświetlania tekstu w dowolnym wymaganym kierunku, na przykład tag HTML 4,0, "dir", który pobiera "RTL" lub "ltr" jako wartości. Ten tag jest podobny do <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwości, <xref:System.Windows.FrameworkElement.FlowDirection%2A> ale Właściwość działa w bardziej zaawansowany sposób do układu zawartości tekstowej i może być używana w przypadku zawartości innej niż tekst.  
  
 W programie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jest to uniwersalny element, który może obsługiwać kombinację tekstu, tabel, obrazów i innych elementów. <xref:System.Windows.Documents.FlowDocument> Przykłady w poniższych sekcjach używają tego elementu.  
  
 Dodawanie tekstu do programu <xref:System.Windows.Documents.FlowDocument> może odbywać się w większy sposób. Prostym sposobem tego jest to, że <xref:System.Windows.Documents.Paragraph> jest to element poziomu bloku służący do grupowania zawartości, takiej jak tekst. Aby dodać tekst do elementów na poziomie wbudowanym, używane <xref:System.Windows.Documents.Span> są <xref:System.Windows.Documents.Run>próbki i. <xref:System.Windows.Documents.Span>jest elementem zawartości przepływu na poziomie wbudowanym używanym do grupowania innych elementów wbudowanych, podczas <xref:System.Windows.Documents.Run> gdy jest element zawartości przepływu na poziomie wbudowanym, który ma zawierać przebieg niesformatowanego tekstu. Może zawierać wiele <xref:System.Windows.Documents.Run>elementów. <xref:System.Windows.Documents.Span>  
  
 Pierwszy przykład dokumentu zawiera dokument zawierający wiele nazw udziałów sieciowych; na przykład `\\server1\folder\file.ext`. Bez względu na to, czy masz to łącze sieciowe w dokumencie arabskim, czy w języku angielskim, zawsze ma być wyświetlana w ten sam sposób. Poniższa ilustracja ilustruje użycie elementu span i pokazuje link w dokumencie arabskim <xref:System.Windows.FlowDirection.RightToLeft> :

 ![Ilustracja, która ilustruje użycie elementu span.](./media/bidirectional-features-in-wpf-overview/flow-direction-span-element.png "FlowDocument")  
  
 Ponieważ tekst to <xref:System.Windows.FlowDirection.RightToLeft>, wszystkie znaki specjalne, takie jak "\\", oddzielaj tekst w kolejności od prawej do lewej. Powoduje to, że link nie jest wyświetlany w prawidłowej kolejności, dlatego w celu rozwiązania problemu tekst musi być osadzony, aby zachować oddzielne <xref:System.Windows.Documents.Run> <xref:System.Windows.FlowDirection.LeftToRight>przepływy. Zamiast oddzielnego <xref:System.Windows.Documents.Run> dla każdego języka lepszym sposobem rozwiązania problemu jest osadzenie rzadziej używanych tekstów w języku angielskim w większej liczbie arabskiej <xref:System.Windows.Documents.Span>.  
  
 Poniższy rysunek ilustruje to przy użyciu elementu Run osadzonego w elemencie span:

 ![Ilustracja, która ilustruje element run osadzony w elemencie span.](./media/bidirectional-features-in-wpf-overview/embedded-span-element.png)  
  
 Poniższy przykład ilustruje użycie <xref:System.Windows.Documents.Run> elementów i <xref:System.Windows.Documents.Span> w dokumentach.  
  
 [!code-xaml[RunSpan#RunSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]  
  
<a name="SpanElements"></a>   
## <a name="span-elements"></a>Span elementy  
 <xref:System.Windows.Documents.Span> Element działa jako separator graniczny między tekstami z różnymi kierunkami przepływu.  Nawet <xref:System.Windows.Documents.Span> elementy o tym samym kierunku przepływu są uważane za posiadające różne zakresy dwukierunkowe <xref:System.Windows.FlowDirection>, co <xref:System.Windows.Documents.Span> oznacza, że elementy są uporządkowane w kontenerze, tylko zawartość <xref:System.Windows.Documents.Span> w obrębie elementu. <xref:System.Windows.FlowDirection> poniżej .<xref:System.Windows.Documents.Span>  
  
 Na poniższej ilustracji przedstawiono kierunek przepływu kilku <xref:System.Windows.Controls.TextBlock> elementów.  
    
 ![Grafika, która ilustruje bloki tekstu z różnymi kierunkami przepływu.](./media/bidirectional-features-in-wpf-overview/flow-direction-text-blocks.png)  
  
 Poniższy przykład pokazuje, jak używać <xref:System.Windows.Documents.Span> elementów i <xref:System.Windows.Documents.Run> , aby wygenerować wyniki widoczne w poprzedniej grafice.  
  
 [!code-xaml[Span#Span](~/samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]  
  
 <xref:System.Windows.FlowDirection> <xref:System.Windows.FlowDirection> <xref:System.Windows.Documents.Span> W elementach w przykładzie <xref:System.Windows.Documents.Span> elementy są układane zgodnie z ich elementami nadrzędnymi, ale tekst w poszczególnych elementach przepływów zgodnie ze swoimi elementami. <xref:System.Windows.Controls.TextBlock> Ma to zastosowanie do języka łacińskiego i języka arabskiego lub innego.  
  
### <a name="adding-xmllang"></a>Dodawanie pliku XML: lang  
 Poniższa ilustracja przedstawia inny przykład, który używa liczb i wyrażeń arytmetycznych, `"200.0+21.4=221.4"`takich jak. Zauważ, że tylko <xref:System.Windows.FlowDirection> jest ustawiony.  
    
 ![Grafika, która wyświetla liczby tylko przy użyciu FlowDirection.](./media/bidirectional-features-in-wpf-overview/numbers-flow-right-left.png)  
  
 Użytkownicy tej aplikacji zostaną Wyznaczeni przez dane wyjściowe, nawet <xref:System.Windows.FlowDirection> jeśli są poprawne, a liczby nie są w formie liczb arabskich.  
  
 Elementy XAML mogą zawierać [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] atrybut (`xml:lang`), który definiuje język każdego elementu. Kod XAML obsługuje [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] również zasadę języka, `xml:lang` w której wartości stosowane do elementów nadrzędnych w drzewie są używane przez elementy podrzędne. W poprzednim przykładzie, ponieważ język nie został zdefiniowany dla <xref:System.Windows.Documents.Run> elementu lub żadnego z jego elementów najwyższego poziomu, użyto wartości domyślnej `xml:lang` , która jest `en-US` dla języka XAML. Wewnętrzny algorytm [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kształtowania liczby wybiera liczby w odpowiadającym języku — w tym przypadku w języku angielskim. Aby ustawienia Arabskie były renderowane prawidłowo `xml:lang` , muszą być ustawione.  
  
 Na poniższej ilustracji przedstawiono przykład z `xml:lang` dodaniem.  
    
 ![Ilustracja przedstawiająca liczby Arabskie, które są przesyłane od prawej do lewej.](./media/bidirectional-features-in-wpf-overview/arabic-numbers-flow-right-left.png)  
  
 Poniższy przykład dodaje `xml:lang` do aplikacji.  
  
 [!code-xaml[LangAttribute#LangAttribute](~/samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]  
  
 Należy pamiętać, że wiele języków ma `xml:lang` różne wartości, w zależności od regionu, na przykład, `"ar-SA"` i `"ar-EG"` reprezentuje dwie Wariacje języka arabskiego. Poprzednie przykłady ilustrują, że należy zdefiniować zarówno `xml:lang` wartości, jak i. <xref:System.Windows.FlowDirection>  
  
<a name="FlowDirectionNontext"></a>   
## <a name="flowdirection-with-non-text-elements"></a>FlowDirection z elementami nietekstowymi  
 <xref:System.Windows.FlowDirection>definiuje nie tylko sposób przepływu tekstu w elemencie tekstowym, ale również kierunek przepływu niemal każdego innego [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementu. Poniższa ilustracja przedstawia <xref:System.Windows.Controls.ToolBar> , który używa <xref:System.Windows.Media.LinearGradientBrush> stopniowego do rysowania tła z gradientem od lewej do prawej.  

 ![Ilustracja pokazująca pasek narzędzi z gradientem od lewej do prawej.](./media/bidirectional-features-in-wpf-overview/toolbar-left-right-gradient.png)  
  
 Po ustawieniu <xref:System.Windows.FlowDirection> do <xref:System.Windows.FlowDirection.RightToLeft>, nie tylko <xref:System.Windows.Controls.ToolBar> przyciski są układane <xref:System.Windows.Media.LinearGradientBrush> od prawej do lewej, ale nawet przerównuje przesunięcia do przepływu od prawej do lewej.  
  
 Na poniższej ilustracji przedstawiono ponownie wyrównanie <xref:System.Windows.Media.LinearGradientBrush>.  
    
 ![Grafika pokazująca pasek narzędzi z lewej strony gradientu.](./media/bidirectional-features-in-wpf-overview/toolbar-right-left-gradient.png)  
  
 Poniższy przykład rysuje <xref:System.Windows.FlowDirection.RightToLeft>. <xref:System.Windows.Controls.ToolBar> (Aby narysować ją od lewej do prawej, <xref:System.Windows.FlowDirection> Usuń atrybut <xref:System.Windows.Controls.ToolBar>na.  
  
 [!code-xaml[Gradient#Gradient](~/samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]  
  
<a name="FlowDirectionExceptions"></a>   
### <a name="flowdirection-exceptions"></a>Wyjątki FlowDirection  
 Istnieje kilka przypadków, w których <xref:System.Windows.FlowDirection> nie zachowuje się zgodnie z oczekiwaniami. W tej sekcji omówiono dwa z tych wyjątków.  
  
 **Obraz**  
  
 <xref:System.Windows.Controls.Image> Reprezentuje kontrolkę wyświetlającą obraz. W [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] tym <xref:System.Windows.Controls.Image> celu można go użyć z <xref:System.Windows.Controls.Image.Source%2A> właściwością, która [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] definiuje element do wyświetlenia.  
  
 W przeciwieństwie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do innych elementów <xref:System.Windows.Controls.Image> , obiekt nie dziedziczy <xref:System.Windows.FlowDirection> z kontenera. Jeśli <xref:System.Windows.FlowDirection> jednak ustawienie jest <xref:System.Windows.FlowDirection.RightToLeft>jawnie ustawione, <xref:System.Windows.Controls.Image> jest wyświetlane w poziomie. Jest to funkcja zaimplementowana jako wygodna dla deweloperów zawartości dwukierunkowej. ponieważ w niektórych przypadkach w poziomie Przerzucanie obrazu skutkuje żądanym efektem.  
  
 Na poniższej ilustracji przedstawiono Przerzucanie <xref:System.Windows.Controls.Image>.  
    
 ![Ilustracja, która ilustruje przerzucony obraz.](./media/bidirectional-features-in-wpf-overview/flipped-image-example.png)  
  
 Poniższy przykład pokazuje, że <xref:System.Windows.Controls.Image> nie powiodło się <xref:System.Windows.FlowDirection> dziedziczenie z <xref:System.Windows.Controls.StackPanel> , który zawiera. **Uwaga** W C:\ musi znajdować się plik o nazwie **ms_logo. jpg.** dysk do uruchomienia tego przykładu.  
  
 [!code-xaml[Image#Image](~/samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]  
  
 **Uwaga** Pliki do pobrania to plik **ms_logo. jpg** . Kod założono, że plik. jpg nie znajduje się w projekcie, ale gdzieś na C:\ litera. Należy skopiować plik jpg z plików projektu do C:\ dysk lub Zmień kod w celu wyszukania pliku w projekcie. Aby to zrobić, `Source="file://c:/ms_logo.jpg"` przejdź `Source="ms_logo.jpg"`do.  
  
 **Ścieżki**  
  
 Oprócz <xref:System.Windows.Controls.Image>, inny interesujący element to <xref:System.Windows.Shapes.Path>. Ścieżka jest obiektem, który może rysować serię połączonych linii i krzywych. Zachowuje się to w sposób podobny <xref:System.Windows.Controls.Image> do elementu <xref:System.Windows.FlowDirection>, na przykład, jest jego <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> poziomą <xref:System.Windows.FlowDirection.LeftToRight> kopią. Jednak, w przeciwieństwie <xref:System.Windows.Controls.Image>do <xref:System.Windows.Shapes.Path> , dziedziczy <xref:System.Windows.FlowDirection> od kontenera, a jeden nie musi jawnie określać go.  
  
 Poniższy przykład rysuje prostą strzałkę przy użyciu 3 wierszy. Pierwsza strzałka dziedziczy <xref:System.Windows.FlowDirection.RightToLeft> kierunek przepływu <xref:System.Windows.Controls.StackPanel> od, tak aby jego punkty początkowe i końcowe były mierzone z poziomu korzenia po prawej stronie. Druga strzałka z jawnym <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> również zaczyna się po prawej stronie. Jednak trzecia strzałka ma swój Start główny po lewej stronie. Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.LineGeometry> rysowania <xref:System.Windows.Media.GeometryGroup>, zobacz i.  
  
 [!code-xaml[Paths#Paths](~/samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe poprzedniego przykładu ze strzałkami rysowanymi przy `Path` użyciu elementu:

 ![Grafika, która ilustruje strzałki rysowane przy użyciu elementu Path.](./media/bidirectional-features-in-wpf-overview/arrows-drawn-path-element.png)  
  
 I są dwa przykłady użycia .<xref:System.Windows.FlowDirection> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.Image> <xref:System.Windows.Shapes.Path> Obok [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] układu elementów w określonym kierunku w kontenerze, <xref:System.Windows.FlowDirection> można używać z elementami takimi jak <xref:System.Windows.Controls.InkPresenter> , które renderuje atrament na powierzchni, <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>. Za każdym razem, gdy potrzebne jest zachowanie praw do lewej zawartości, która naśladuje zachowanie po lewej stronie lub odwrotnie, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia tę możliwość.  
  
<a name="NumberSubstitution"></a>   
## <a name="number-substitution"></a>Podstawianie numerów  
 W przeszłości system Windows obsługuje podstawianie numerów, umożliwiając reprezentację różnych kształtów kulturowych dla tych samych cyfr przy jednoczesnym zachowaniu wewnętrznego magazynu tych cyfr dla różnych ustawień regionalnych, na przykład liczby są przechowywane w ich dobrze znane wartości szesnastkowe, 0x40, 0x41, ale wyświetlane zgodnie z wybranym językiem.  
  
 Dzięki temu aplikacje mogą przetwarzać wartości liczbowe bez konieczności konwertowania ich z jednego języka na inny, na przykład użytkownik może otworzyć [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)] arkusz kalkulacyjny w zlokalizowanych oknach arabskich i zobaczyć liczby w kształcie arabskim, ale otworzyć go w Europejska wersja systemu Windows i zobacz Europejski reprezentacja tych samych numerów. Jest to również konieczne w przypadku innych symboli, takich jak separatory przecinki i symbol procentu, ponieważ zazwyczaj towarzyszą one numerom w tym samym dokumencie.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]kontynuuje te same tradycje i dodaje do niej dalszą pomoc techniczną, która umożliwia większą kontrolę nad tym, kiedy i jak są używane podstawienia. Chociaż ta funkcja jest zaprojektowana dla dowolnego języka, jest szczególnie przydatna w przypadku zawartości dwukierunkowej, gdzie kształtowanie cyfr dla określonego języka zwykle jest wyzwaniem dla deweloperów aplikacji z powodu różnych kultur, w których aplikacja może być uruchomiona.  
  
 Właściwość Core kontrolująca sposób działania podstawiania [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] numerów w <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> programie jest właściwością zależności. <xref:System.Windows.Media.NumberSubstitution> Klasa określa sposób wyświetlania liczb w tekście. Ma trzy właściwości publiczne, które definiują jego zachowanie. Poniżej znajduje się podsumowanie poszczególnych właściwości.  
  
 **CultureSource:**  
  
 Ta właściwość określa sposób określania kultury dla liczb. Przyjmuje jedną z trzech <xref:System.Windows.Media.NumberCultureSource> wartości wyliczenia.  
  
- Mapowań Kulturą liczbową jest <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> właściwość.  
  
- Opis Kultura liczbowa jest kulturą uruchomienia tekstu. W znaczniku może to być `xml:lang`lub jego właściwość aliasu `Language` (<xref:System.Windows.FrameworkElement.Language%2A> lub <xref:System.Windows.FrameworkContentElement.Language%2A>). Ponadto jest to wartość domyślna dla klas pochodnych z <xref:System.Windows.FrameworkContentElement>. Takie klasy obejmują <xref:System.Windows.Documents.Paragraph?displayProperty=nameWithType> <xref:System.Windows.Documents.Table?displayProperty=nameWithType>, itakdalej.<xref:System.Windows.Documents.TableCell?displayProperty=nameWithType>  
  
- Użytkownicy Kultura liczbowa jest kulturą bieżącego wątku. Ta właściwość jest wartością <xref:System.Windows.FrameworkElement> domyślną dla wszystkich podklas takich jak <xref:System.Windows.Controls.Page>, <xref:System.Windows.Window> i <xref:System.Windows.Controls.TextBlock>.  
  
 **CultureOverride**:  
  
 Właściwość jest używana tylko wtedy, <xref:System.Windows.Media.NumberSubstitution.CultureSource%2A> gdy właściwość jest ustawiona na <xref:System.Windows.Media.NumberCultureSource.Override> i jest ignorowana w przeciwnym razie. <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> Określa kulturę liczby. Wartość `null`domyślna jest interpretowana jako en-us.  
  
 **Podstawienie**:  
  
 Ta właściwość określa typ podstawiania numerów do wykonania. Przyjmuje jedną z następujących <xref:System.Windows.Media.NumberSubstitutionMethod> wartości wyliczenia:  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.AsCulture>: Metoda podstawienia jest określana na podstawie <xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=nameWithType> właściwości kultury wartości. Domyślnie włączone.  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.Context>: Jeśli kultura liczbowa jest kulturą arabską lub perski, określa, że cyfry są zależne od kontekstu.  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.European>: Liczby są zawsze renderowane jako cyfry europejskie.  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>: Liczby są renderowane przy użyciu cyfr narodowych dla kultury liczbowej, jak określono przez kulturę <xref:System.Globalization.CultureInfo.NumberFormat%2A>.  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.Traditional>: Liczby są renderowane przy użyciu tradycyjnych cyfr dla kultury liczbowej. W przypadku większości kultur jest to taka sama jak <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>. <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational> Jednak wyniki w postaci cyfr łacińskich niektórych kultur arabskich, podczas gdy ta wartość powoduje cyfry arabskie dla wszystkich kultur arabskich.  
  
 Co oznaczają te wartości dla wielokierunkowego programisty zawartości? W większości przypadków deweloper może potrzebować tylko do <xref:System.Windows.FlowDirection> definiowania i języka każdego elementu tekstowego <xref:System.Windows.Media.NumberSubstitution> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , na przykład `Language="ar-SA"` , a logika wymaga wyświetlania liczb zgodnie z poprawnymi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. W poniższym przykładzie pokazano, jak używać numerów arabskich i angielskich [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] w aplikacji uruchomionej w arabskiej wersji systemu Windows.  
  
 [!code-xaml[Numbers#Numbers](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe poprzedniego przykładu, jeśli używasz wersji arabskiej systemu Windows z wyświetlonymi numerami arabskimi i angielskimi:

 ![Grafika pokazująca cyfry arabskie i angielskie.](./media/bidirectional-features-in-wpf-overview/arabic-english-numbers.png)  
  
 Jest <xref:System.Windows.FlowDirection> to ważne w tym przypadku, ponieważ ustawienie <xref:System.Windows.FlowDirection> <xref:System.Windows.FlowDirection.LeftToRight> w zamian spowodowałoby nakazanie cyfr europejskich. W poniższych sekcjach omówiono, jak mieć ujednolicony sposób wyświetlania cyfr w całym dokumencie. Jeśli ten przykład nie jest uruchomiony w oknach arabskich, wszystkie cyfry są wyświetlane jako cyfry europejskie.  
  
 **Definiowanie reguł podstawienia**  
  
 W prawdziwej aplikacji może być konieczne ustawienie języka programowo. Na przykład, chcesz ustawić `xml:lang` atrybut tak samo jak używany przez [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]system lub może zmienić język w zależności od stanu aplikacji.  
  
 Jeśli chcesz wprowadzić zmiany na podstawie stanu aplikacji, Skorzystaj z innych funkcji udostępnianych przez [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]program.  
  
 Najpierw ustaw składnik `NumberSubstitution.CultureSource="Text"`aplikacji. Korzystając z tego ustawienia, upewnij się, że ustawienia nie pochodzą z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementów tekstowych, które mają wartość "User", <xref:System.Windows.Controls.TextBlock>na przykład.  
  
Na przykład:  

```xaml  
<TextBlock
   Name="text1" NumberSubstitution.CultureSource="Text">
   1234+5679=6913
</TextBlock>
```

W odpowiednim C# kodzie Ustaw `Language` właściwość, na przykład na `"ar-SA"`.  
  
```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");
```

Jeśli musisz ustawić `Language` właściwość na język interfejsu użytkownika bieżącego użytkownika, użyj poniższego kodu.  
  
```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage(System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);
```

 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>reprezentuje bieżącą kulturę używaną przez bieżący wątek w czasie wykonywania.  
  
 Ostatni [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] przykład powinien wyglądać podobnie do poniższego przykładu.  
  
 [!code-xaml[Numbers2#Numbers2](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]  
  
 Ostatni C# przykład powinien wyglądać podobnie do poniższego.  
  
 [!code-csharp[NumbersCSharp#NumbersCSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]  
  
 Na poniższej ilustracji przedstawiono, jak wygląda okno dla każdego języka programowania, wyświetlając cyfry arabskie:
     
 ![Grafika wyświetlająca liczby Arabskie.](./media/bidirectional-features-in-wpf-overview/displays-arabic-numbers.png)  
  
 **Korzystanie z właściwości podstawienia**  
  
 Sposób, w jaki podstawianie numerów działa w programie [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] , zależy od zarówno języka elementu tekstowego, jak i jego. <xref:System.Windows.FlowDirection> Jeśli pozycja <xref:System.Windows.FlowDirection> jest od lewej do prawej, są renderowane cyfry europejskie. Jednak jeśli jest poprzedzony przez tekst arabski lub język ma ustawioną wartość "ar" i <xref:System.Windows.FlowDirection> parametrem is <xref:System.Windows.FlowDirection.RightToLeft>, zamiast tego są renderowane cyfry arabskie.  
  
 Jednak w niektórych przypadkach możesz chcieć utworzyć ujednoliconą aplikację, na przykład cyfry europejskie dla wszystkich użytkowników. Lub cyfry arabskie w <xref:System.Windows.Documents.Table> komórkach z określonym <xref:System.Windows.Style>. Jednym z łatwych metod jest użycie <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> właściwości.  
  
 W poniższym przykładzie pierwszy <xref:System.Windows.Controls.TextBlock> nie <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> ma ustawionej właściwości, więc algorytm wyświetla cyfry arabskie zgodnie z oczekiwaniami. Jednak w drugim <xref:System.Windows.Controls.TextBlock>podstawianie jest ustawione na Europejski zastępowanie domyślnego podstawienia dla numerów arabskich, a cyfry europejskie są wyświetlane.  
  
 [!code-xaml[Numbers3#Numbers3](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]
