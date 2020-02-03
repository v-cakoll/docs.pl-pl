---
title: Omówienie funkcji dwukierunkowych
ms.date: 03/30/2017
helpviewer_keywords:
- Span elements [WPF]
- bidirectional features [WPF]
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
ms.openlocfilehash: 17167b1afa5037998d9ea8ed679a66c89babe242
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741632"
---
# <a name="bidirectional-features-in-wpf-overview"></a>Przegląd Dwukierunkowe funkcje WPF

W przeciwieństwie do żadnej innej platformy deweloperskiej, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ma wiele funkcji, które obsługują szybkie opracowywanie zawartości dwukierunkowej, na przykład mieszane od lewej do prawej i prawo do lewej strony w tym samym dokumencie. W tym samym czasie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tworzy doskonałe środowisko dla użytkowników, którzy wymagają funkcji dwukierunkowych, takich jak arabski i hebrajski.

W poniższych sekcjach opisano wiele funkcji dwukierunkowych wraz z Przykładami ilustrującymi sposób osiągnięcia najlepszego sposobu wyświetlania zawartości dwukierunkowej. Większość przykładów używa języka XAML, chociaż można łatwo zastosować koncepcje do C# kodu programu lub Microsoft Visual Basic Code.

<a name="FlowDirection"></a>

## <a name="flowdirection"></a>FlowDirection

Właściwość podstawowa definiująca kierunek przepływu zawartości w aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Tę właściwość można ustawić na jedną z dwóch wartości wyliczenia, <xref:System.Windows.FlowDirection.LeftToRight> lub <xref:System.Windows.FlowDirection.RightToLeft>. Właściwość jest dostępna dla wszystkich elementów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], które dziedziczą z <xref:System.Windows.FrameworkElement>.

W poniższych przykładach ustawiono kierunek przepływu elementu <xref:System.Windows.Controls.TextBox>.

**Kierunek przepływu od lewej do prawej**

[!code-xaml[LTRRTL#LTR](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]

**Kierunek przepływu od prawej do lewej**

[!code-xaml[LTRRTL#RTL](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]

Na poniższej ilustracji przedstawiono sposób renderowania poprzedniego kodu.

![Ilustracja, która ilustruje różne kierunki przepływu.](./media/bidirectional-features-in-wpf-overview/left-right-right-left.png)

Element w drzewie [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dziedziczy <xref:System.Windows.FrameworkElement.FlowDirection%2A> z jego kontenera. W poniższym przykładzie <xref:System.Windows.Controls.TextBlock> znajduje się w <xref:System.Windows.Controls.Grid>, który znajduje się w <xref:System.Windows.Window>. Ustawienie <xref:System.Windows.FrameworkElement.FlowDirection%2A> dla <xref:System.Windows.Window> oznacza również ustawienie <xref:System.Windows.Controls.Grid> i <xref:System.Windows.Controls.TextBlock>.

Poniższy przykład demonstruje ustawienie <xref:System.Windows.FrameworkElement.FlowDirection%2A>.

[!code-xaml[FlowDirection#FlowDirection](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]

<xref:System.Windows.Window> najwyższego poziomu ma <xref:System.Windows.FlowDirection><xref:System.Windows.FlowDirection.RightToLeft>, więc wszystkie zawarte w nim elementy również dziedziczą te same <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Aby element przesłaniał określoną <xref:System.Windows.FrameworkElement.FlowDirection%2A>, musi dodać jawną zmianę kierunku, taką jak druga <xref:System.Windows.Controls.TextBlock> w poprzednim przykładzie, która zmienia się w <xref:System.Windows.FlowDirection.LeftToRight>. Jeśli nie zdefiniowano <xref:System.Windows.FrameworkElement.FlowDirection%2A>, <xref:System.Windows.FlowDirection.LeftToRight> ma zastosowanie domyślny.

Na poniższej ilustracji przedstawiono dane wyjściowe poprzedniego przykładu:

![Ilustracja przedstawiająca jawną zmianę kierunku przepływu.](./media/bidirectional-features-in-wpf-overview/explicit-direction-change.png)

<a name="FlowDocument"></a>

## <a name="flowdocument"></a>FlowDocument

Wiele platform programistycznych, takich jak HTML, Win32 i Java, zapewnia specjalną obsługę tworzenia zawartości dwukierunkowej. Języki znaczników, takie jak HTML, dają autorom zawartości niezbędne znaczniki do wyświetlania tekstu w dowolnym wymaganym kierunku, na przykład tag HTML 4,0, "dir", który pobiera "RTL" lub "ltr" jako wartości. Ten tag jest podobny do właściwości <xref:System.Windows.FrameworkElement.FlowDirection%2A>, ale Właściwość <xref:System.Windows.FrameworkElement.FlowDirection%2A> działa w bardziej zaawansowany sposób do układu zawartości tekstowej i może być używana w przypadku zawartości innej niż tekst.

W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Documents.FlowDocument> jest uniwersalnym [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementu, który może obsługiwać kombinację tekstu, tabel, obrazów i innych elementów. Przykłady w poniższych sekcjach używają tego elementu.

Dodawanie tekstu do <xref:System.Windows.Documents.FlowDocument> można wykonać w większy sposób. Prostym sposobem wykonania tej czynności jest użycie <xref:System.Windows.Documents.Paragraph>, który jest elementem poziomu bloku używanym do grupowania zawartości, takiej jak tekst. Aby dodać tekst do elementów na poziomie wbudowanym, przykłady używają <xref:System.Windows.Documents.Span> i <xref:System.Windows.Documents.Run>. <xref:System.Windows.Documents.Span> jest elementem zawartości przepływu na poziomie wbudowanym używanym do grupowania innych elementów wbudowanych, podczas gdy <xref:System.Windows.Documents.Run> jest elementem zawartości przepływu na poziomie wbudowanym, który ma zawierać przebieg niesformatowanego tekstu. <xref:System.Windows.Documents.Span> może zawierać wiele elementów <xref:System.Windows.Documents.Run>.

Pierwszy przykład dokumentu zawiera dokument zawierający wiele nazw udziałów sieciowych; na przykład `\\server1\folder\file.ext`. Bez względu na to, czy masz to łącze sieciowe w dokumencie arabskim, czy w języku angielskim, zawsze ma być wyświetlana w ten sam sposób. Poniższa ilustracja ilustruje użycie elementu span i wyświetla link w dokumencie <xref:System.Windows.FlowDirection.RightToLeft> arabskiej:

![Ilustracja, która ilustruje użycie elementu span.](./media/bidirectional-features-in-wpf-overview/flow-direction-span-element.png "FlowDocument")

Ponieważ tekst jest <xref:System.Windows.FlowDirection.RightToLeft>, wszystkie znaki specjalne, takie jak "\\", oddzielają tekst w kolejności od prawej do lewej. Powoduje to, że link nie jest wyświetlany w prawidłowej kolejności, dlatego w celu rozwiązania problemu tekst musi być osadzony, aby zachować osobne <xref:System.Windows.Documents.Run> przepływające <xref:System.Windows.FlowDirection.LeftToRight>. Zamiast oddzielnego <xref:System.Windows.Documents.Run> dla każdego języka, lepszym sposobem rozwiązania problemu jest osadzenie rzadziej używanych tekstów w języku angielskim do większych <xref:System.Windows.Documents.Span>arabskich.

Poniższy rysunek ilustruje to przy użyciu elementu Run osadzonego w elemencie span:

![Ilustracja, która ilustruje element run osadzony w elemencie span.](./media/bidirectional-features-in-wpf-overview/embedded-span-element.png)

Poniższy przykład ilustruje użycie <xref:System.Windows.Documents.Run> i <xref:System.Windows.Documents.Span> elementów w dokumentach.

[!code-xaml[RunSpan#RunSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]

<a name="SpanElements"></a>

## <a name="span-elements"></a>Span elementy

Element <xref:System.Windows.Documents.Span> działa jako separator graniczny między tekstami z różnymi kierunkami przepływu.  Nawet <xref:System.Windows.Documents.Span> elementy o tym samym kierunku przepływu są uważane za mające różne zakresy dwukierunkowe, co oznacza, że elementy <xref:System.Windows.Documents.Span> są uporządkowane w <xref:System.Windows.FlowDirection>kontenera, tylko zawartość w elemencie <xref:System.Windows.Documents.Span> jest zgodna z <xref:System.Windows.FlowDirection> <xref:System.Windows.Documents.Span>.

Na poniższej ilustracji przedstawiono kierunek przepływu kilku elementów <xref:System.Windows.Controls.TextBlock>.

![Grafika, która ilustruje bloki tekstu z różnymi kierunkami przepływu.](./media/bidirectional-features-in-wpf-overview/flow-direction-text-blocks.png)

Poniższy przykład pokazuje, jak używać elementów <xref:System.Windows.Documents.Span> i <xref:System.Windows.Documents.Run> do tworzenia wyników przedstawionych na poprzedniej ilustracji.

[!code-xaml[Span#Span](~/samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]

W <xref:System.Windows.Controls.TextBlock> elementów w przykładzie elementy <xref:System.Windows.Documents.Span> są układane zgodnie z <xref:System.Windows.FlowDirection> ich obiektów nadrzędnych, ale tekst w poszczególnych elementach <xref:System.Windows.Documents.Span> przepływów zgodnie z własnym <xref:System.Windows.FlowDirection>. Ma to zastosowanie do języka łacińskiego i języka arabskiego lub innego.

### <a name="adding-xmllang"></a>Dodawanie pliku XML: lang

Poniższa ilustracja przedstawia inny przykład, który używa liczb i wyrażeń arytmetycznych, takich jak `"200.0+21.4=221.4"`. Zauważ, że ustawiono tylko <xref:System.Windows.FlowDirection>.

![Grafika, która wyświetla liczby tylko przy użyciu FlowDirection.](./media/bidirectional-features-in-wpf-overview/numbers-flow-right-left.png)

Użytkownicy tej aplikacji zostaną Wyznaczeni przez dane wyjściowe, nawet jeśli <xref:System.Windows.FlowDirection> są poprawne, a liczby nie są takie same jak cyfry arabskie.

Elementy XAML mogą zawierać atrybut XML (`xml:lang`), który definiuje język każdego elementu. XAML obsługuje również zasadę języka XML, w której `xml:lang` wartości stosowane do elementów nadrzędnych w drzewie są używane przez elementy podrzędne. W poprzednim przykładzie, ponieważ język nie został zdefiniowany dla elementu <xref:System.Windows.Documents.Run> ani żadnego z jego elementów najwyższego poziomu, użyto domyślnego `xml:lang`, który jest `en-US` dla języka XAML. Wewnętrzny algorytm kształtowania liczby [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] wybiera liczby w odpowiadającym języku — w tym przypadku w języku angielskim. Aby numery Arabskie były renderowane prawidłowo `xml:lang` należy ustawić.

Na poniższej ilustracji przedstawiono przykład, w którym dodano `xml:lang`.

![Ilustracja przedstawiająca liczby Arabskie, które są przesyłane od prawej do lewej.](./media/bidirectional-features-in-wpf-overview/arabic-numbers-flow-right-left.png)

Poniższy przykład dodaje `xml:lang` do aplikacji.

[!code-xaml[LangAttribute#LangAttribute](~/samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]

Należy pamiętać, że wiele języków ma różne wartości `xml:lang` w zależności od regionu, na przykład `"ar-SA"` i `"ar-EG"` reprezentują dwie odmiany arabskiej. Poprzednie przykłady ilustrują, że należy zdefiniować zarówno wartości `xml:lang`, jak i <xref:System.Windows.FlowDirection>.

<a name="FlowDirectionNontext"></a>

## <a name="flowdirection-with-non-text-elements"></a>FlowDirection z elementami nietekstowymi

<xref:System.Windows.FlowDirection> definiuje nie tylko sposób przepływu tekstu w elemencie tekstowym, ale również kierunek przepływu niemal każdego elementu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Na poniższej ilustracji przedstawiono <xref:System.Windows.Controls.ToolBar>, która używa <xref:System.Windows.Media.LinearGradientBrush> poziomego do rysowania tła z gradientem od lewej do prawej.

![Ilustracja pokazująca pasek narzędzi z gradientem od lewej do prawej.](./media/bidirectional-features-in-wpf-overview/toolbar-left-right-gradient.png)

Po ustawieniu <xref:System.Windows.FlowDirection> na <xref:System.Windows.FlowDirection.RightToLeft>, nie tylko przyciski <xref:System.Windows.Controls.ToolBar> są ułożone od prawej do lewej, ale nawet <xref:System.Windows.Media.LinearGradientBrush> ponownie wyrównuje przesunięcia do przepływu od prawej do lewej.

Poniższa ilustracja przedstawia zmianę wyrównania <xref:System.Windows.Media.LinearGradientBrush>.

![Grafika pokazująca pasek narzędzi z lewej strony gradientu.](./media/bidirectional-features-in-wpf-overview/toolbar-right-left-gradient.png)

Poniższy przykład rysuje <xref:System.Windows.Controls.ToolBar><xref:System.Windows.FlowDirection.RightToLeft>. (Aby narysować ją od lewej do prawej, Usuń atrybut <xref:System.Windows.FlowDirection> w <xref:System.Windows.Controls.ToolBar>.

[!code-xaml[Gradient#Gradient](~/samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]

<a name="FlowDirectionExceptions"></a>

### <a name="flowdirection-exceptions"></a>Wyjątki FlowDirection

Istnieje kilka przypadków, w których <xref:System.Windows.FlowDirection> nie zadziała zgodnie z oczekiwaniami. W tej sekcji omówiono dwa z tych wyjątków.

**Obraz**

<xref:System.Windows.Controls.Image> reprezentuje kontrolkę wyświetlającą obraz. W języku XAML można go użyć z właściwością <xref:System.Windows.Controls.Image.Source%2A>, która definiuje jednolity identyfikator zasobów (URI) <xref:System.Windows.Controls.Image> do wyświetlenia.

W przeciwieństwie do innych elementów [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], <xref:System.Windows.Controls.Image> nie dziedziczy <xref:System.Windows.FlowDirection> z kontenera. Jeśli jednak <xref:System.Windows.FlowDirection> jest jawnie ustawiona do <xref:System.Windows.FlowDirection.RightToLeft>, zostanie wyświetlony <xref:System.Windows.Controls.Image> przesunięty w poziomie. Jest to funkcja zaimplementowana jako wygodna dla deweloperów zawartości dwukierunkowej. ponieważ w niektórych przypadkach w poziomie Przerzucanie obrazu skutkuje żądanym efektem.

Na poniższej ilustracji przedstawiono <xref:System.Windows.Controls.Image>przerzucane.

![Ilustracja, która ilustruje przerzucony obraz.](./media/bidirectional-features-in-wpf-overview/flipped-image-example.png)

Poniższy przykład pokazuje, że <xref:System.Windows.Controls.Image> nie dziedziczy <xref:System.Windows.FlowDirection> z <xref:System.Windows.Controls.StackPanel>, który go zawiera.

> [!NOTE]
> W C:\ musi znajdować się plik o nazwie **ms_logo. jpg** dysk do uruchomienia tego przykładu.

[!code-xaml[Image#Image](~/samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]

> [!NOTE]
> Pliki do pobrania to plik **jpg ms_logo** . Kod założono, że plik. jpg nie znajduje się w projekcie, ale gdzieś na C:\ litera. Należy skopiować plik jpg z plików projektu do C:\ dysk lub Zmień kod w celu wyszukania pliku w projekcie. Aby wykonać tę zmianę `Source="file://c:/ms_logo.jpg"` w `Source="ms_logo.jpg"`.

**Ścieżki**

Oprócz <xref:System.Windows.Controls.Image>inny interesujący element jest <xref:System.Windows.Shapes.Path>. Ścieżka jest obiektem, który może rysować serię połączonych linii i krzywych. Działa w sposób podobny do <xref:System.Windows.Controls.Image> w odniesieniu do jego <xref:System.Windows.FlowDirection>; na przykład <xref:System.Windows.FlowDirection> <xref:System.Windows.FlowDirection.RightToLeft>to pozioma kopia <xref:System.Windows.FlowDirection.LeftToRight> jednego. Jednak, w przeciwieństwie do <xref:System.Windows.Controls.Image>, <xref:System.Windows.Shapes.Path> dziedziczy <xref:System.Windows.FlowDirection> z kontenera, a jeden nie musi jawnie określać go.

Poniższy przykład rysuje prostą strzałkę przy użyciu 3 wierszy. Pierwsza strzałka dziedziczy kierunek przepływu <xref:System.Windows.FlowDirection.RightToLeft> z <xref:System.Windows.Controls.StackPanel>, tak aby jego punkty początkowe i końcowe były mierzone z poziomu korzenia po prawej stronie. Druga strzałka, która ma jawną <xref:System.Windows.FlowDirection.RightToLeft><xref:System.Windows.FlowDirection> również zaczyna się po prawej stronie. Jednak trzecia strzałka ma swój Start główny po lewej stronie. Aby uzyskać więcej informacji na temat rysowania, zobacz <xref:System.Windows.Media.LineGeometry> i <xref:System.Windows.Media.GeometryGroup>.

[!code-xaml[Paths#Paths](~/samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]

Na poniższej ilustracji przedstawiono dane wyjściowe poprzedniego przykładu ze strzałkami rysowanymi przy użyciu elementu `Path`:

![Grafika, która ilustruje strzałki rysowane przy użyciu elementu Path.](./media/bidirectional-features-in-wpf-overview/arrows-drawn-path-element.png)

<xref:System.Windows.Controls.Image> i <xref:System.Windows.Shapes.Path> są dwoma przykładami użycia [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.FlowDirection>. Obok układu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementów w określonym kierunku w obrębie kontenera <xref:System.Windows.FlowDirection> mogą być używane z elementami takimi jak <xref:System.Windows.Controls.InkPresenter>, które renderuje pismo odręczne na powierzchni, <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>. Za każdym razem, gdy jest potrzebne prawo do lewego zachowania zawartości, która naśladuje zachowanie po lewej stronie lub na odwrót, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia tę możliwość.

<a name="NumberSubstitution"></a>

## <a name="number-substitution"></a>Podstawianie numerów

W przeszłości system Windows obsługuje podstawianie numerów, umożliwiając reprezentację różnych kształtów kulturowych dla tych samych cyfr przy jednoczesnym zachowaniu wewnętrznego magazynu tych cyfr dla różnych ustawień regionalnych, na przykład liczby są przechowywane w ich dobrze znane wartości szesnastkowe, 0x40, 0x41, ale wyświetlane zgodnie z wybranym językiem.

Dzięki temu aplikacje mogą przetwarzać wartości liczbowe bez konieczności konwertowania ich z jednego języka na inny, na przykład w przypadku, gdy użytkownik może otworzyć arkusz kalkulacyjny programu Microsoft Excel w zlokalizowanych oknach arabskich i zobaczyć cyfry w języku arabskim, ale otworzyć je w Europejska wersja systemu Windows i zobacz Europejski reprezentacja tych samych numerów. Jest to również konieczne w przypadku innych symboli, takich jak separatory przecinki i symbol procentu, ponieważ zazwyczaj towarzyszą one numerom w tym samym dokumencie.

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kontynuuje te same tradycje i dodaje dalszą obsługę tej funkcji, która umożliwia większą kontrolę nad tym, kiedy i jak są używane podstawienia. Chociaż ta funkcja jest zaprojektowana dla dowolnego języka, jest szczególnie przydatna w przypadku zawartości dwukierunkowej, gdzie kształtowanie cyfr dla określonego języka zwykle jest wyzwaniem dla deweloperów aplikacji z powodu różnych kultur, w których aplikacja może być uruchomiona.

Właściwość Core kontrolująca sposób działania podstawiania numerów w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jest właściwością zależności <xref:System.Windows.Media.NumberSubstitution.Substitution%2A>. Klasa <xref:System.Windows.Media.NumberSubstitution> określa, jak będą wyświetlane liczby w tekście. Ma trzy właściwości publiczne, które definiują jego zachowanie. Poniżej znajduje się podsumowanie poszczególnych właściwości:

**CultureSource:**

Ta właściwość określa sposób określania kultury dla liczb. Przyjmuje jedną z trzech <xref:System.Windows.Media.NumberCultureSource> wartości wyliczenia.

- Przesłonięcie: wartość kultury jest wartością właściwości <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A>.

- Tekst: kultura liczbowa jest kulturą uruchomienia tekstu. W znaczniku można `xml:lang`lub jego alias `Language` Właściwość (<xref:System.Windows.FrameworkElement.Language%2A> lub <xref:System.Windows.FrameworkContentElement.Language%2A>). Ponadto jest to wartość domyślna dla klas pochodnych z <xref:System.Windows.FrameworkContentElement>. Takie klasy obejmują <xref:System.Windows.Documents.Paragraph?displayProperty=nameWithType>, <xref:System.Windows.Documents.Table?displayProperty=nameWithType>, <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType> i tak dalej.

- Użytkownik: wartość Culture jest kulturą bieżącego wątku. Ta właściwość jest wartością domyślną dla wszystkich podklas <xref:System.Windows.FrameworkElement>, takich jak <xref:System.Windows.Controls.Page>, <xref:System.Windows.Window> i <xref:System.Windows.Controls.TextBlock>.

**CultureOverride**:

Właściwość <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> jest używana tylko wtedy, gdy właściwość <xref:System.Windows.Media.NumberSubstitution.CultureSource%2A> jest ustawiona na <xref:System.Windows.Media.NumberCultureSource.Override> i w przeciwnym razie jest ignorowana. Określa kulturę liczby. Wartość `null`wartość domyślna jest interpretowana jako en-US.

**Podstawienie**:

Ta właściwość określa typ podstawiania numerów do wykonania. Przyjmuje jedną z następujących <xref:System.Windows.Media.NumberSubstitutionMethod> wartości wyliczenia:

- <xref:System.Windows.Media.NumberSubstitutionMethod.AsCulture>: Metoda podstawienia jest określana na podstawie właściwości <xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=nameWithType> kultury liczbowej. Domyślnie włączone.

- <xref:System.Windows.Media.NumberSubstitutionMethod.Context>: Jeśli kultura liczbowa jest kulturą arabską lub perski, określa, że cyfry są zależne od kontekstu.

- <xref:System.Windows.Media.NumberSubstitutionMethod.European>: numery są zawsze renderowane jako cyfry europejskie.

- <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>: liczby są renderowane przy użyciu cyfr narodowych dla kultury liczbowej, jak określono przez <xref:System.Globalization.CultureInfo.NumberFormat%2A>kultury.

- <xref:System.Windows.Media.NumberSubstitutionMethod.Traditional>: liczby są renderowane przy użyciu tradycyjnych cyfr dla kultury liczbowej. W przypadku większości kultur jest to taka sama jak <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>. Jednak <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational> wyniki w postaci cyfr łacińskich dla niektórych kultur arabskich, podczas gdy ta wartość skutkuje cyframi arabskimi dla wszystkich kultur arabskich.

Co oznaczają te wartości dla wielokierunkowego programisty zawartości? W większości przypadków deweloper może potrzebować tylko do zdefiniowania <xref:System.Windows.FlowDirection> i języka każdego tekstu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementu, na przykład `Language="ar-SA"`, a logika <xref:System.Windows.Media.NumberSubstitution>u uwzględnia wyświetlanie liczb zgodnie z poprawną [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. W poniższym przykładzie pokazano, jak używać numerów arabskich i angielskich w aplikacji [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] działającej w arabskiej wersji systemu Windows.

[!code-xaml[Numbers#Numbers](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]

Na poniższej ilustracji przedstawiono dane wyjściowe poprzedniego przykładu, jeśli używasz wersji arabskiej systemu Windows z wyświetlonymi numerami arabskimi i angielskimi:

![Grafika pokazująca cyfry arabskie i angielskie.](./media/bidirectional-features-in-wpf-overview/arabic-english-numbers.png)

<xref:System.Windows.FlowDirection> była ważna w tym przypadku, ponieważ ustawienie <xref:System.Windows.FlowDirection> do <xref:System.Windows.FlowDirection.LeftToRight> zamiast nich spowodowałoby nakazanie cyfr europejskich. W poniższych sekcjach omówiono, jak mieć ujednolicony sposób wyświetlania cyfr w całym dokumencie. Jeśli ten przykład nie jest uruchomiony w oknach arabskich, wszystkie cyfry są wyświetlane jako cyfry europejskie.

**Definiowanie reguł podstawienia**

W prawdziwej aplikacji może być konieczne ustawienie języka programowo. Na przykład, chcesz ustawić atrybut `xml:lang` tak samo jak używany przez [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]systemu, lub może zmienić język w zależności od stanu aplikacji.

Jeśli chcesz wprowadzić zmiany na podstawie stanu aplikacji, Skorzystaj z innych funkcji udostępnianych przez [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].

Najpierw ustaw `NumberSubstitution.CultureSource="Text"`składnika aplikacji. Korzystając z tego ustawienia, należy upewnić się, że ustawienia nie pochodzą z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dla elementów tekstowych, które mają wartość domyślną, np. <xref:System.Windows.Controls.TextBlock>.

Na przykład:

```xaml
<TextBlock
   Name="text1" NumberSubstitution.CultureSource="Text">
   1234+5679=6913
</TextBlock>
```

W odpowiednim C# kodzie ustaw właściwość `Language`, na przykład, aby `"ar-SA"`.

```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");
```

Jeśli musisz ustawić właściwość `Language` na język interfejsu użytkownika bieżącego, użyj następującego kodu.

```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage(System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);
```

<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> reprezentuje bieżącą kulturę używaną przez bieżący wątek w czasie wykonywania.

Końcowy przykład XAML powinien wyglądać podobnie do poniższego przykładu.

[!code-xaml[Numbers2#Numbers2](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]

Ostatni C# przykład powinien wyglądać podobnie do poniższego.

[!code-csharp[NumbersCSharp#NumbersCSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]

Na poniższej ilustracji przedstawiono, jak wygląda okno dla każdego języka programowania, wyświetlając cyfry arabskie:

![Grafika wyświetlająca liczby Arabskie.](./media/bidirectional-features-in-wpf-overview/displays-arabic-numbers.png)

**Korzystanie z właściwości podstawienia**

Sposób, w jaki podstawianie numerów działa w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], zależy zarówno od języka elementu tekstowego, jak i jego <xref:System.Windows.FlowDirection>. Jeśli <xref:System.Windows.FlowDirection> jest od lewej do prawej, są renderowane cyfry europejskie. Jednak jeśli jest poprzedzony przez tekst arabski lub ma ustawiony język "ar", a <xref:System.Windows.FlowDirection> jest <xref:System.Windows.FlowDirection.RightToLeft>, zamiast tego są renderowane cyfry arabskie.

Jednak w niektórych przypadkach możesz chcieć utworzyć ujednoliconą aplikację, na przykład cyfry europejskie dla wszystkich użytkowników. Lub cyfry arabskie w <xref:System.Windows.Documents.Table> komórkach z określonym <xref:System.Windows.Style>. Jeden prosty sposób to użycie właściwości <xref:System.Windows.Media.NumberSubstitution.Substitution%2A>.

W poniższym przykładzie pierwszy <xref:System.Windows.Controls.TextBlock> nie ma ustawionej właściwości <xref:System.Windows.Media.NumberSubstitution.Substitution%2A>, dlatego algorytm wyświetla cyfry arabskie zgodnie z oczekiwaniami. Jednak w drugim <xref:System.Windows.Controls.TextBlock>podstawienia jest ustawiona na Europejski zastępowanie domyślnego podstawienia dla numerów arabskich i są wyświetlane cyfry europejskie.

[!code-xaml[Numbers3#Numbers3](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]
