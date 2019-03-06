---
title: Przegląd Dwukierunkowe funkcje WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Span elements [WPF]
- bidirectional features [WPF]
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
ms.openlocfilehash: fbbd400ae842ae24bae0307c362642d8fe1d5bea
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364063"
---
# <a name="bidirectional-features-in-wpf-overview"></a>Przegląd Dwukierunkowe funkcje WPF
W przeciwieństwie do innych platform tworzenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ma wiele funkcji, które obsługują szybkiego opracowywania zawartości dwukierunkowy, na przykład mieszanej po lewej stronie kliknij prawym przyciskiem myszy i kliknij prawym przyciskiem myszy, aby left danych w tym samym dokumencie. W tym samym czasie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tworzy doskonałe środowisko dla użytkowników, którzy potrzebują dwukierunkowe funkcje, takie jak arabski i hebrajski wypowiedzi użytkowników.  
  
 W poniższych sekcjach opisano wiele dwukierunkowe funkcje oraz przykłady ilustrujące sposób osiągnięcia najlepszych wyświetlanie zawartości dwukierunkowy. Większość przykładów użycia [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], ale koncepcji, które można z łatwością zastosować C# lub kodu języka Visual Basic.  
  

  
<a name="FlowDirection"></a>   
## <a name="flowdirection"></a>FlowDirection  
 Podstawowa właściwość, która definiuje kierunek przepływu zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacja jest <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Tę właściwość można ustawić na jeden z dwóch wartości wyliczenia, <xref:System.Windows.FlowDirection.LeftToRight> lub <xref:System.Windows.FlowDirection.RightToLeft>. Właściwość jest dostępny dla wszystkich [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy, które dziedziczą z <xref:System.Windows.FrameworkElement>.  
  
 W następujących przykładach ustawiona kierunek przepływu <xref:System.Windows.Controls.TextBox> elementu.  
  
 **Kierunek przepływu od lewej do prawej**  
  
 [!code-xaml[LTRRTL#LTR](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]  
  
 **Kierunek przepływu od prawej do lewej**  
  
 [!code-xaml[LTRRTL#RTL](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]  
  
 Na poniższym rysunku przedstawiono, jak poprzedni kod renderuje.  
  
 **Grafika, który ilustruje FlowDirection**  
  
 ![Wyrównanie TextBlock](./media/lefttorightrighttoleft.PNG "LefttoRightRighttoLeft")  
  
 Element w obrębie [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] drzewa będzie dziedziczyć <xref:System.Windows.FrameworkElement.FlowDirection%2A> z jego kontenerem. W poniższym przykładzie <xref:System.Windows.Controls.TextBlock> znajduje się wewnątrz <xref:System.Windows.Controls.Grid>, który znajduje się w <xref:System.Windows.Window>. Ustawienie <xref:System.Windows.FrameworkElement.FlowDirection%2A> dla <xref:System.Windows.Window> oznacza ustawienie dla <xref:System.Windows.Controls.Grid> i <xref:System.Windows.Controls.TextBlock> również.  
  
 W poniższym przykładzie pokazano ustawienie <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 [!code-xaml[FlowDirection#FlowDirection](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]  
  
 Najwyższego poziomu <xref:System.Windows.Window> ma <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection>, więc wszystkie elementy zawarte w nim również dziedziczyć takie same <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Element do zastąpienia określonej <xref:System.Windows.FrameworkElement.FlowDirection%2A> należy dodać, zmiany kierunku jawne, takich jak drugi <xref:System.Windows.Controls.TextBlock> w poprzednim przykładzie, który zmienia się na <xref:System.Windows.FlowDirection.LeftToRight>. Gdy nie <xref:System.Windows.FrameworkElement.FlowDirection%2A> jest zdefiniowana wartość domyślna <xref:System.Windows.FlowDirection.LeftToRight> ma zastosowanie.  
  
 Na poniższym rysunku przedstawiono dane wyjściowe poprzedniego przykładu.  
  
 **Grafika, który ilustruje jawnie przypisane FlowDirection**  
  
 ![Ilustracja kierunek przepływu](./media/flowdir.PNG "FlowDir")  
  
<a name="FlowDocument"></a>   
## <a name="flowdocument"></a>FlowDocument  
 Wiele platform programowania, takich jak [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)], [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] i Java umożliwiają specjalne dwukierunkowe tworzenia zawartości. Języków znaczników, takich jak [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] zapewniają autorzy zawartości kodu znaczników niezbędne do wyświetlania tekstu w dowolnym kierunku wymagane, na przykład [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] 4.0 tag, "dir" ValidateEndElement "od prawej do lewej" lub "od lewej do prawej" jako wartości. Ten tag jest podobny do <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwości, ale <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwości działa w sposób bardziej zaawansowane do zawartości tekstowej układ i mogą być używane dla zawartości innych niż tekst.  
  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.Documents.FlowDocument> jest uniwersalny [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] element, który może obsługiwać kombinację tekstu, tabele, obrazy i inne elementy. Przykłady w poniższych sekcjach, użyj tego elementu.  
  
 Dodawanie tekstu do <xref:System.Windows.Documents.FlowDocument> może odbywać się w bardziej tego jednym ze sposobów. Najprościej można to zrobić to za pośrednictwem <xref:System.Windows.Documents.Paragraph> który jest używany do zawartości grupy, takie jak tekst elementu na poziomie bloku. Aby dodać tekst do elementów śródwierszowy przykłady użycia <xref:System.Windows.Documents.Span> i <xref:System.Windows.Documents.Run>. <xref:System.Windows.Documents.Span> jest elementem zawartości przepływu śródwierszowy używane do grupowania innych elementów śródwierszowych podczas <xref:System.Windows.Documents.Run> jest przepływ śródwierszowy zawartości elementu przeznaczona do przechowywania przebiegu niesformatowanego tekstu. A <xref:System.Windows.Documents.Span> może zawierać więcej niż jednego <xref:System.Windows.Documents.Run> elementów.  
  
 Pierwszy przykład dokument zawiera dokument, który ma wiele sieci udostępniać nazwy. na przykład `\\server1\folder\file.ext`. Czy masz to łącze sieci w dokumencie arabski lub angielski, należy zawsze ma się pojawić w taki sam sposób. Na poniższym rysunku przedstawiono łącze w języku arabskim <xref:System.Windows.FlowDirection.RightToLeft> dokumentu.  
  
 **Grafika, który ilustruje użycie Span Element**  
  
 ![Dokument, który przepływa od prawej do lewej](./media/flowdocument.PNG "FlowDocument")  
  
 Ponieważ tekst jest <xref:System.Windows.FlowDirection.RightToLeft>, wszystkie specjalne znaki, takie jak "\\", tekstu w prawo do kolejności po lewej stronie. Który skutkuje łącza nie są wyświetlane w odpowiedniej kolejności, dlatego aby rozwiązać ten problem, tekst muszą być osadzone zachowanie oddzielnej <xref:System.Windows.Documents.Run> przepływających <xref:System.Windows.FlowDirection.LeftToRight>. Zamiast oddzielnego <xref:System.Windows.Documents.Run> dla każdego z języków lepszy sposób rozwiązania tego problemu jest osadzanie rzadziej używane tekstu w języku angielskim w większych arabski <xref:System.Windows.Documents.Span>.  
  
 Poniższa ilustracja przedstawia to.  
  
 **Grafika, który ilustruje użycie wykonywania elementu osadzonego w elemencie zakresu**  
  
 ![Zrzut ekranu przedstawiający edytor XamlPad](./media/runspan.PNG "RunSpan")  
  
 Poniższy przykład demonstruje użycie <xref:System.Windows.Documents.Run> i <xref:System.Windows.Documents.Span> elementy w dokumentach.  
  
 [!code-xaml[RunSpan#RunSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]  
  
<a name="SpanElements"></a>   
## <a name="span-elements"></a>Elementy obszaru  
 <xref:System.Windows.Documents.Span> Elementu działa jako separator granic między teksty z różnymi kierunkami przepływu.  Nawet <xref:System.Windows.Documents.Span> elementów z tym samym kierunku przepływu jest uznawany za zakresy różnych dwukierunkową, co oznacza, które <xref:System.Windows.Documents.Span> elementy są uporządkowane w kontenerze <xref:System.Windows.FlowDirection>, tylko zawartość w ramach <xref:System.Windows.Documents.Span> — element następuje <xref:System.Windows.FlowDirection> z <xref:System.Windows.Documents.Span>.  
  
 Na poniższym rysunku przedstawiono kierunek przepływu kilka <xref:System.Windows.Controls.TextBlock> elementów.  
  
 **Grafika, który ilustruje FlowDirection w kilku elementach TextBlock**  
  
 ![Bloki tekstu z różnymi kierunkami przepływu](./media/span.PNG "zakresu")  
  
 Poniższy przykład pokazuje, jak używać <xref:System.Windows.Documents.Span> i <xref:System.Windows.Documents.Run> elementy w celu uzyskania wyników pokazano na poprzednim rysunku.  
  
 [!code-xaml[Span#Span](~/samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]  
  
 W <xref:System.Windows.Controls.TextBlock> elementów w tym przykładzie <xref:System.Windows.Documents.Span> elementy są ułożone zgodnie z opisem w <xref:System.Windows.FlowDirection> nadrzędnych, ale tekst w ramach każdej <xref:System.Windows.Documents.Span> element przepływy zgodnie z jego własnej <xref:System.Windows.FlowDirection>. Dotyczy to urządzeń z Łacińskiej i arabski lub dowolnym innym języku.  
  
### <a name="adding-xmllang"></a>Dodawanie XML: lang.  
 Na poniższym rysunku przedstawiono inny przykład, korzystającą z liczb i wyrażenia arytmetyczne, takie jak `"200.0+21.4=221.4"`. Zwróć uwagę że tylko <xref:System.Windows.FlowDirection> jest ustawiona.  
  
 **Grafiki, która wyświetla liczby przy użyciu tylko FlowDirection**  
  
 ![Liczby przepływające od prawej do lewej](./media/langattribute.PNG "LangAttribute")  
  
 Użytkownicy w tej aplikacji będzie można ubolewa nad faktem dane wyjściowe, nawet jeśli <xref:System.Windows.FlowDirection> jest poprawna, liczby nie są kształt, jak arabski numery powinny kształcie.  
  
 Może zawierać elementów XAML [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] atrybutu (`xml:lang`) definiujący język każdego elementu. Obsługuje również XAML [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] zasady języka zgodnie z którą `xml:lang` wartości stosowane do elementami nadrzędnymi w drzewie są używane przez elementy podrzędne. W poprzednim przykładzie ponieważ nie zdefiniowano języka dla <xref:System.Windows.Documents.Run> element lub dowolny z najwyższego poziomu elementów, wartość domyślna `xml:lang` było używane, czyli `en-US` dla XAML. Wewnętrzny numer kształtowania algorytm [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] wybiera liczb w odpowiednim języku — w tym przypadku angielski. Zapewnienie arabski liczby renderowania poprawnie `xml:lang` musi być ustawiona.  
  
 Na poniższym rysunku przedstawiono przykład z `xml:lang` dodane.  
  
 **Ilustracja czy ilustruje używanie XML: lang — atrybut**  
  
 ![Liczby arabskie przepływające od prawej do lewej](./media/langattribute2.PNG "LangAttribute2")  
  
 W poniższym przykładzie dodano `xml:lang` do aplikacji.  
  
 [!code-xaml[LangAttribute#LangAttribute](~/samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]  
  
 Należy pamiętać, że wiele języków mają różne `xml:lang` wartości w zależności od regionu docelowego, na przykład `"ar-SA"` i `"ar-EG"` reprezentują dwie odmiany arabski. W poprzednich przykładach pokazano, trzeba zdefiniować zarówno `xml:lang` i <xref:System.Windows.FlowDirection> wartości.  
  
<a name="FlowDirectionNontext"></a>   
## <a name="flowdirection-with-non-text-elements"></a>FlowDirection z elementami nietekstowymi  
 <xref:System.Windows.FlowDirection> Określa nie tylko sposób przepływu tekstu w element tekstowy, ale również kierunek przepływu w prawie każdym innych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementu. Pokazano grafiki <xref:System.Windows.Controls.ToolBar> poziomej, który używa <xref:System.Windows.Media.LinearGradientBrush> do rysowania tła.  
  
 **Grafika przedstawiająca pasek narzędzi o od lewej do prawej gradientu**  
  
 ![Zrzut ekranu przedstawiający gradient](./media/gradient.PNG "gradientu")  
  
 Po ustawieniu <xref:System.Windows.FlowDirection> do <xref:System.Windows.FlowDirection.RightToLeft>, nie tylko <xref:System.Windows.Controls.ToolBar> przyciski są rozmieszczane od prawej do lewej, ale nawet <xref:System.Windows.Media.LinearGradientBrush> ponowne wyrównywanie jego przesunięcia, które będą przepływać od prawej do lewej.  
  
 Na poniższym rysunku przedstawiono Wyrównaj ponownie z <xref:System.Windows.Media.LinearGradientBrush>.  
  
 **Grafika przedstawiająca narzędzi z prawej strony do lewej gradientu**  
  
 ![Gradientu, który przepływa od prawej do lewej](./media/gradient2-wpf.PNG "Gradient2_WPF")  
  
 Poniższy przykład pobiera <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.Controls.ToolBar>. (Można ją rysować od lewej do prawej, Usuń <xref:System.Windows.FlowDirection> atrybutu na <xref:System.Windows.Controls.ToolBar>.  
  
 [!code-xaml[Gradient#Gradient](~/samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]  
  
<a name="FlowDirectionExceptions"></a>   
### <a name="flowdirection-exceptions"></a>Wyjątki FlowDirection  
 Istnieje kilka przypadków których <xref:System.Windows.FlowDirection> nie zachowywać się zgodnie z oczekiwaniami. W tej sekcji omówiono dwa z tych wyjątków.  
  
 **Obraz**  
  
 <xref:System.Windows.Controls.Image> Reprezentuje kontrolkę wyświetlającą obraz. W [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] mogą być używane z <xref:System.Windows.Controls.Image.Source%2A> właściwość, która definiuje [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] z <xref:System.Windows.Controls.Image> do wyświetlenia.  
  
 W odróżnieniu od innych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementów <xref:System.Windows.Controls.Image> nie dziedziczy <xref:System.Windows.FlowDirection> z kontenera. Jednak jeśli <xref:System.Windows.FlowDirection> ustawiono jawnie na <xref:System.Windows.FlowDirection.RightToLeft>, <xref:System.Windows.Controls.Image> jest wyświetlany poziomo odwrócony. Ten sposób jest implementowany jako wygodny funkcji dla deweloperów dwukierunkowe zawartości; ponieważ w niektórych przypadkach poziomo Przerzucanie obrazu daje pożądanych efektów.  
  
 Na poniższym rysunku przedstawiono odwrócony <xref:System.Windows.Controls.Image>.  
  
 **Grafika, który ilustruje odwrócony obraz**  
  
 ![Zrzut ekranu przedstawiający edytor XamlPad](./media/image.PNG "obrazu")  
  
 Poniższy przykład pokazuje, że <xref:System.Windows.Controls.Image> nie może dziedziczyć <xref:System.Windows.FlowDirection> z <xref:System.Windows.Controls.StackPanel> zawierający go. **Uwaga** musi mieć w pliku o nazwie **ms_logo.jpg** na Twoje C:\ dysk, aby uruchomić ten przykład.  
  
 [!code-xaml[Image#Image](~/samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]  
  
 **Uwaga** jest dołączone do plików do pobrania **ms_logo.jpg** pliku. W kodzie założono, że plik jpg znajduje się poza projektu, ale miejsce na dysku C:\. Należy skopiować .jpg z plików projektu na dysku C:\, lub zmień kod, aby wyszukać plik w projekcie. Aby wykonać tę zmianę `Source="file://c:/ms_logo.jpg"` do `Source="ms_logo.jpg"`.  
  
 **Ścieżki**  
  
 Oprócz <xref:System.Windows.Controls.Image>, jest inny interesujący element <xref:System.Windows.Shapes.Path>. Ścieżka jest obiektem, który można narysować szereg podłączonych linii i krzywych. Działa w sposób podobny do <xref:System.Windows.Controls.Image> dotyczące jego <xref:System.Windows.FlowDirection>; na przykład jego <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> jest poziomy odzwierciedleniem jej <xref:System.Windows.FlowDirection.LeftToRight> jeden. Jednak w przeciwieństwie do <xref:System.Windows.Controls.Image>, <xref:System.Windows.Shapes.Path> dziedziczy jej <xref:System.Windows.FlowDirection> z kontenera i jeden trzeba określić ręcznie.  
  
 Poniższy przykład pobiera Prosta strzałka przy użyciu 3 wiersze. Pierwsza Strzałka dziedziczy <xref:System.Windows.FlowDirection.RightToLeft> kierunek z przepływu <xref:System.Windows.Controls.StackPanel> tak, aby jego początkowego i punktu końcowego są mierzone w katalogu głównym, po prawej stronie. Druga strzałka, mającej jawny <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> również rozpoczyna się po prawej stronie. Jednak począwszy od główny trzeci strzałkę jest się po lewej stronie. Aby uzyskać więcej informacji na rysunku zobacz <xref:System.Windows.Media.LineGeometry> i <xref:System.Windows.Media.GeometryGroup>.  
  
 [!code-xaml[Paths#Paths](~/samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]  
  
 Na poniższym rysunku przedstawiono dane wyjściowe poprzedniego przykładu.  
  
 **Grafika, który ilustruje strzałki przy użyciu elementu Path**  
  
 ![Ścieżki](./media/paths.PNG "ścieżki")  
  
 <xref:System.Windows.Controls.Image> i <xref:System.Windows.Shapes.Path> przedstawiono dwa przykłady sposób [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] używa <xref:System.Windows.FlowDirection>. Obok pozycji układania [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy w określonym kierunku w kontenerze, <xref:System.Windows.FlowDirection> mogą być używane z elementami takich jak <xref:System.Windows.Controls.InkPresenter> która renderuje pismo odręczne na powierzchni, <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>. Zawsze, gdy potrzebujesz prawo do lewej zachowanie dotyczące Twojej zawartości, który naśladuje zleva nagradza prawidłowe zachowanie, lub na odwrót [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapewnia taką możliwość.  
  
<a name="NumberSubstitution"></a>   
## <a name="number-substitution"></a>Liczba podstawienia  
 W przeszłości [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] ma obsługiwane podstawienia liczb, umożliwiając reprezentacją przy jednoczesnym zachowaniu pamięci wewnętrznej te cyfry unified wśród różnych ustawień regionalnych, na przykład liczby są przechowywane w różnych kształtów kultury dla tych samych cyfr ich dobrze znane wartości szesnastkowych, 0x40, 0x41, ale wyświetlane zgodnie z wybranym języku.  
  
 To jest dozwolone aplikacje do przetworzenia wartości liczbowe, bez konieczności ich konwersja z jednego języka do innego, na przykład użytkownik może otworzyć [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)] arkusza kalkulacyjnego w zlokalizowanych arabski [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] i wyświetlić numery ukształtowane w języku arabskim, ale go otworzyć w Środkowoeuropejski wersję [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] zobaczyć Europejskiego reprezentacja takie same numery. To jest również dla innych symboli, takie jak przecinki jako separatory i procent symboli, ponieważ są zazwyczaj dołączone liczb w tym samym dokumencie.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kontynuuje tradycję zapewniania tego samego i alokowanej dalsze to funkcja, która umożliwia większa kontrola użytkownika nad kiedy i w jaki sposób podstawienie jest używany. Gdy ta funkcja została zaprojektowana dla dowolnego języka, jego jest szczególnie przydatne w dwukierunkowe zawartości w przypadku, gdy kształtowania cyfr dla określonego języka jest zazwyczaj wyzwanie dla deweloperów aplikacji z powodu różnych kultur, w których aplikacja może działać w.  
  
 Właściwości podstawowe kontrolowanie jak numer podstawienia działa w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jest <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> właściwość zależności. <xref:System.Windows.Media.NumberSubstitution> Klasa określa, jak mają być wyświetlane numery w tekście. Posiada trzy właściwości publicznej, które definiują jego zachowanie. Poniżej znajduje się podsumowanie wszystkich właściwości.  
  
 **CultureSource:**  
  
 Ta właściwość określa sposób ustalania kultury dla liczb. Przyjmuje on jedną z trzech <xref:System.Windows.Media.NumberCultureSource> wartości wyliczenia.  
  
-   Zastąpienie: Liczba kultury jest <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> właściwości.  
  
-   Tekst: Liczba kulturą jest kultura tekstu, uruchom. W znaczniku, będzie to `xml:lang`, lub jego alias `Language` właściwości (<xref:System.Windows.FrameworkElement.Language%2A> lub <xref:System.Windows.FrameworkContentElement.Language%2A>). Ponadto jest ustawieniem domyślnym dla klasy wywodzące się z <xref:System.Windows.FrameworkContentElement>. Takich klas obejmują <xref:System.Windows.Documents.Paragraph?displayProperty=nameWithType>, <xref:System.Windows.Documents.Table?displayProperty=nameWithType>, <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType> itd.  
  
-   Użytkownik: Liczba kulturą jest kultura bieżącego wątku. Ta właściwość jest ustawieniem domyślnym dla wszystkich podklasy <xref:System.Windows.FrameworkElement> takich jak <xref:System.Windows.Controls.Page>, <xref:System.Windows.Window> i <xref:System.Windows.Controls.TextBlock>.  
  
 **CultureOverride**:  
  
 <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> Właściwość jest używana tylko wtedy, gdy <xref:System.Windows.Media.NumberSubstitution.CultureSource%2A> właściwość jest ustawiona na <xref:System.Windows.Media.NumberCultureSource.Override> i jest ignorowany w innych przypadkach. Określa numer kultury. Wartość `null`, wartością domyślną jest interpretowany jako en US.  
  
 **Podstawianie**:  
  
 Ta właściwość określa typ numeru podstawienia do wykonania. Przyjmuje on jedną z następujących <xref:System.Windows.Media.NumberSubstitutionMethod> wartości wyliczenia.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.AsCulture>: Metoda podstawienia jest określana na podstawie kultury numer <xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=nameWithType> właściwości. Domyślnie włączone.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.Context>: Liczba kulturą jest arabski lub Farsi kultury, określa, że cyfry są zależne od kontekstu.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.European>: Numery zawsze są renderowane jako cyfry Europejskich.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>: Cyfry są renderowane przy użyciu national cyfr numeru kultury, określony przez kultury <xref:System.Globalization.CultureInfo.NumberFormat%2A>.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.Traditional>: Cyfry są renderowane przy użyciu tradycyjnych cyfr numeru kultury. Dla większości kultur jest to taka sama jak <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>. Jednak <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational> skutkuje alfabetu łacińskiego cyfr dla niektórych kultur arabski, natomiast wartość ta powoduje arabski cyfr dla wszystkich języków arabski.  
  
 Co oznaczają te wartości dwukierunkowe deweloperowi zawartości? W większości przypadków, deweloper może być konieczne tylko w celu zdefiniowania <xref:System.Windows.FlowDirection> i język każdy tekstową [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementu, na przykład `Language="ar-SA"` i <xref:System.Windows.Media.NumberSubstitution> logiki dba o wyświetlaniu liczb zgodnie z prawidłowych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Poniższy przykład demonstruje użycie arabski i angielskim numerów [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji uruchomionej w języku arabskim wersję [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  
  
 [!code-xaml[Numbers#Numbers](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]  
  
 Na poniższym rysunku przedstawiono dane wyjściowe w poprzednim przykładzie, jeśli są uruchomione w języku arabskim wersji [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  
  
 **Grafika przedstawiająca arabski i angielskim liczby wyświetlane**  
  
 ![Edytor XamlPad odpowiednio zmienić zrzut ekranu z międzynarodowymi numerami identyfikującymi](./media/numbers.PNG "liczb")  
  
 <xref:System.Windows.FlowDirection> Była ważna w tym przypadku, ponieważ ustawienie <xref:System.Windows.FlowDirection> do <xref:System.Windows.FlowDirection.LeftToRight> zamiast tego będzie mieć zwróciło Europejskiego cyfr. W poniższych sekcjach omówiono sposób zostały ujednolicony wyświetlanie cyfr w całym dokumencie. Jeśli w tym przykładzie nie jest uruchomiona na arabski Windows, wszystkie cyfry są wyświetlane jako Europejskiego cyfr.  
  
 **Definiowanie reguł podstawienia**  
  
 W rzeczywistej aplikacji może wymagać programowo ustawić język. Na przykład chcesz ustawić `xml:lang` atrybutu, aby być taka sama, jak konto używane przez system [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], lub może zmienić język, w zależności od stanu aplikacji.  
  
 Jeśli chcesz, aby zmiany oparciu o stan aplikacji, należy korzystać z innych funkcji, dostarczonych przez [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 Najpierw ustaw składnik aplikacji `NumberSubstitution.CultureSource="Text"`. Przy użyciu tego ustawienia upewnia się, że ustawienia nie są udzielane przez firmę [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dla elementów tekstowych, które mają "User" jako domyślne, takie jak <xref:System.Windows.Controls.TextBlock>.  
  
Na przykład:  

```xaml  
<TextBlock
   Name="text1" NumberSubstitution.CultureSource="Text">
   1234+5679=6913
</TextBlock>
```

W odpowiednich C# kodu, ustaw `Language` właściwości, na przykład, aby `"ar-SA"`.  
  
```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");
```

Jeśli musisz ustawić `Language` właściwości język interfejsu użytkownika bieżącego użytkownika, użyj następującego kodu.  
  
```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage(System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);
```

 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> reprezentuje bieżącą kulturę używaną przez bieżący wątek w czasie wykonywania.  
  
 Ostateczna [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] przykład powinien być podobny do poniższego przykładu.  
  
 [!code-xaml[Numbers2#Numbers2](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]  
  
 Ostateczna C# przykład powinien być podobny do następującego.  
  
 [!code-csharp[NumbersCSharp#NumbersCSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]  
  
 Na poniższym rysunku przedstawiono, jak wygląda okna dla dowolnego języka programowania.  
  
 **Grafiki, która wyświetla numery arabski**  
  
 ![Arabski numery](./media/numbers2.PNG "Numbers2")  
  
 **Przy użyciu właściwości podstawienia**  
  
 Sposób numer podstawienia działa w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zależy od języka elementu tekstu i jego <xref:System.Windows.FlowDirection>. Jeśli <xref:System.Windows.FlowDirection> jest od lewej do prawej, a następnie cyfry europejskie są renderowane. Jednak jeśli jest poprzedzona tekst arabski lub ma język jest ustawiony na "ar" i <xref:System.Windows.FlowDirection> jest <xref:System.Windows.FlowDirection.RightToLeft>, arabski cyfr są renderowane w zamian.  
  
 W niektórych przypadkach jednak warto utworzyć ujednoliconego aplikację, na przykład Europejskiego cyfr dla wszystkich użytkowników. Lub arabski cyfr w <xref:System.Windows.Documents.Table> komórki z określonym <xref:System.Windows.Style>. Jeden łatwy sposób przeprowadzenia używanej <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> właściwości.  
  
 W poniższym przykładzie pierwszy <xref:System.Windows.Controls.TextBlock> nie ma <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> właściwością, więc algorytm wyświetla cyfry arabski, zgodnie z oczekiwaniami. Jednak w drugim <xref:System.Windows.Controls.TextBlock>podstawienia jest równa Europejskiej zastępowanie podstawienia domyślny dla języka arabskiego liczb oraz Europejskiego cyfry są wyświetlane.  
  
 [!code-xaml[Numbers3#Numbers3](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]
