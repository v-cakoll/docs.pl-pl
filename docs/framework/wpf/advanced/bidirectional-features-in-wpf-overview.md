---
title: "Przegląd Dwukierunkowe funkcje WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Span elements [WPF]
- bidirectional features [WPF]
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b50d98d5f02a59a013d7577f0e312e6ffde35690
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="bidirectional-features-in-wpf-overview"></a>Przegląd Dwukierunkowe funkcje WPF
W przeciwieństwie do innych platformy programistycznej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ma wiele funkcji, które obsługują szybkie opracowywanie zawartości dwukierunkowego, na przykład mieszanych od lewej do prawej i kliknij prawym przyciskiem myszy, aby pozostawić danych w tym samym dokumencie. W tym samym czasie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tworzy doskonałe środowisko dla użytkowników wymagających dwukierunkowego funkcje, takie jak arabski i hebrajski mówiąc użytkownikami.  
  
 W poniższych sekcjach opisano wiele funkcji dwukierunkowego wraz z przykładami pokazujący sposób uzyskania najlepszych wyświetlanie zawartości dwukierunkowego. Większość przykładów użycia [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], ale można łatwo zastosować pojęć [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] lub [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] kodu.  
  

  
<a name="FlowDirection"></a>   
## <a name="flowdirection"></a>Wartość FlowDirection  
 Podstawowa właściwość, która definiuje kierunek przepływu zawartości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacja jest <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Ta właściwość może należeć do jednej z dwóch wartości wyliczenia, <xref:System.Windows.FlowDirection.LeftToRight> lub <xref:System.Windows.FlowDirection.RightToLeft>. Właściwość jest dostępna dla wszystkich [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy, które dziedziczą z <xref:System.Windows.FrameworkElement>.  
  
 Poniższe przykłady ustaw kierunek przepływu <xref:System.Windows.Controls.TextBox> elementu.  
  
 **Kierunek przepływu od lewej do prawej**  
  
 [!code-xaml[LTRRTL#LTR](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]  
  
 **Kierunek przepływu od prawej do lewej**  
  
 [!code-xaml[LTRRTL#RTL](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]  
  
 Na poniższym rysunku przedstawiono, jak poprzedni kod renderuje.  
  
 **Grafika, która ilustruje wartość FlowDirection**  
  
 ![Wyrównanie obiektu TextBlock](../../../../docs/framework/wpf/advanced/media/lefttorightrighttoleft.PNG "LefttoRightRighttoLeft")  
  
 W elemencie [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] drzewo będzie dziedziczyć <xref:System.Windows.FrameworkElement.FlowDirection%2A> z jego kontenera. W poniższym przykładzie <xref:System.Windows.Controls.TextBlock> znajduje się wewnątrz <xref:System.Windows.Controls.Grid>, który znajduje się w <xref:System.Windows.Window>. Ustawienie <xref:System.Windows.FrameworkElement.FlowDirection%2A> dla <xref:System.Windows.Window> oznacza ustawieniem dla niego dla <xref:System.Windows.Controls.Grid> i <xref:System.Windows.Controls.TextBlock> również.  
  
 W poniższym przykładzie pokazano ustawienie <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 [!code-xaml[FlowDirection#FlowDirection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]  
  
 Najwyższego poziomu <xref:System.Windows.Window> ma <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection>, więc wszystkie elementy zawarte w nim także takie same dziedziczą <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Dla elementu, aby zastąpić określonej <xref:System.Windows.FrameworkElement.FlowDirection%2A> należy dodać zmiany kierunku jawne, takich jak drugi <xref:System.Windows.Controls.TextBlock> w poprzednim przykładzie, który zmienia się na <xref:System.Windows.FlowDirection.LeftToRight>. Gdy nie <xref:System.Windows.FrameworkElement.FlowDirection%2A> jest zdefiniowana, wartość domyślna <xref:System.Windows.FlowDirection.LeftToRight> ma zastosowanie.  
  
 Na poniższym rysunku przedstawiono dane wyjściowe z poprzedniego przykładu.  
  
 **Grafika, która ilustruje jawnie przypisać wartość FlowDirection**  
  
 ![Ilustracja kierunek przepływu](../../../../docs/framework/wpf/advanced/media/flowdir.PNG "FlowDir")  
  
<a name="FlowDocument"></a>   
## <a name="flowdocument"></a>FlowDocument  
 Wiele platformy programistyczne, takie jak [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)], [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] i Java zapewniają obsługę specjalne programowanie zawartości dwukierunkowego. Kod znaczników języków, takich jak [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] nadaj zapisywania zawartości znaczników niezbędne do wyświetlania tekstu w dowolnym kierunku wymagane, na przykład [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] 4.0 tag, "dir", który przyjmuje "od prawej do lewej" lub "od lewej do prawej" jako wartości. Ten tag jest podobny do <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwości, ale <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwości działa w sposób bardziej zaawansowanych, aby zawartość tekstową układ i mogą być używane dla zawartości innego niż tekstu.  
  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.Documents.FlowDocument> jest uniwersalny [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] element, który może obsługiwać kombinację tekstu, tabel, obrazy i inne elementy. Ten element służy próbek w poniższych sekcjach.  
  
 Dodawanie tekstu do <xref:System.Windows.Documents.FlowDocument> może odbywać się bardziej temu jeden. To prosty sposób, aby to zrobić za pomocą <xref:System.Windows.Documents.Paragraph> czyli element na poziomie bloku, używany do zawartości grupy, taki jak tekst. Dodawanie tekstu do elementów wbudowanych przykłady użycia <xref:System.Windows.Documents.Span> i <xref:System.Windows.Documents.Run>. <xref:System.Windows.Documents.Span>jest elementem zawartości przepływ śródwierszowy używane do grupowania innych elementów śródwierszowych podczas <xref:System.Windows.Documents.Run> jest przepływ śródwierszowy zawartości elementu mają zawierać Uruchom niesformatowanego tekstu. A <xref:System.Windows.Documents.Span> może zawierać wiele <xref:System.Windows.Documents.Run> elementów.  
  
 W pierwszym przykładzie dokument zawiera dokument, który ma liczbę sieci udostępnianie nazw; na przykład `\\server1\folder\file.ext`. Określa, czy ma to łącze sieci w dokumentach arabskiego lub angielski, należy zawsze będzie wyświetlana w taki sam sposób. Na poniższym rysunku przedstawiono łącze w arabski <xref:System.Windows.FlowDirection.RightToLeft> dokumentu.  
  
 **Grafika, która ilustruje za pomocą elementu zakresu**  
  
 ![Dokument, który przepływa od prawej do lewej](../../../../docs/framework/wpf/advanced/media/flowdocument.PNG "FlowDocument")  
  
 Ponieważ tekst jest <xref:System.Windows.FlowDirection.RightToLeft>, wszystkie specjalne znaki, takie jak "\\", tekstu w prawej do lewej zamówienia. Która powoduje łącze nie jest pokazywany w odpowiedniej kolejności, dlatego aby rozwiązać ten problem, tekst musi być osadzony w celu zachowania oddzielnej <xref:System.Windows.Documents.Run> przepływu <xref:System.Windows.FlowDirection.LeftToRight>. Zamiast oddzielnego <xref:System.Windows.Documents.Run> dla każdego języka lepszy sposób rozwiązania tego problemu jest do osadzenia tekstu w języku angielskim rzadziej używanych do większych arabski <xref:System.Windows.Documents.Span>.  
  
 Poniższa ilustracja przedstawia to.  
  
 **Grafika, która ilustruje za pomocą elementu wykonywania osadzone w elemencie zakresu**  
  
 ![Zrzut ekranu przedstawiający edytor XamlPad](../../../../docs/framework/wpf/advanced/media/runspan.PNG "RunSpan")  
  
 W poniższym przykładzie pokazano, za pomocą <xref:System.Windows.Documents.Run> i <xref:System.Windows.Documents.Span> elementy w dokumentach.  
  
 [!code-xaml[RunSpan#RunSpan](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]  
  
<a name="SpanElements"></a>   
## <a name="span-elements"></a>Elementy zakresu  
 <xref:System.Windows.Documents.Span> Element działa jako separator granicę między teksty z instrukcjami innego przepływu.  Nawet <xref:System.Windows.Documents.Span> elementy o tym samym kierunku przepływu jest uznawany za dwukierunkowego różne zakresy, których <xref:System.Windows.Documents.Span> elementy są uporządkowane w kontenerze <xref:System.Windows.FlowDirection>, tylko zawartość w <xref:System.Windows.Documents.Span> — element następuje <xref:System.Windows.FlowDirection> z <xref:System.Windows.Documents.Span>.  
  
 Na poniższym rysunku przedstawiono kierunek przepływu kilka <xref:System.Windows.Controls.TextBlock> elementów.  
  
 **Grafika, która ilustruje wartość FlowDirection w kilku elementach blok tekstu**  
  
 ![Bloki tekst z instrukcjami innego przepływu](../../../../docs/framework/wpf/advanced/media/span.PNG "zakresu")  
  
 Poniższy przykład przedstawia użycie <xref:System.Windows.Documents.Span> i <xref:System.Windows.Documents.Run> elementów w celu uzyskania wyników pokazano na rysunku poprzedniej.  
  
 [!code-xaml[Span#Span](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]  
  
 W <xref:System.Windows.Controls.TextBlock> elementów w przykładzie <xref:System.Windows.Documents.Span> elementy zostały przedstawione zgodnie z <xref:System.Windows.FlowDirection> nadrzędnych, ale tekst wewnątrz każdego <xref:System.Windows.Documents.Span> przepływów elementu zgodnie z jego własnej <xref:System.Windows.FlowDirection>. Ma to zastosowanie Latin i arabski — lub dowolnego innego języka.  
  
### <a name="adding-xmllang"></a>Dodawanie XML: lang  
 Na poniższym rysunku przedstawiono inny przykład korzystającego z liczb i wyrażenia arytmetyczne, takie jak `"200.0+21.4=221.4"`. Uwaga tylko <xref:System.Windows.FlowDirection> jest ustawiona.  
  
 **Graficzne, który wyświetla liczb przy użyciu tylko wartość FlowDirection**  
  
 ![Liczby przepływające od prawej do lewej](../../../../docs/framework/wpf/advanced/media/langattribute.PNG "LangAttribute")  
  
 Użytkownicy w tej aplikacji będzie można ubolewa nad faktem przez dane wyjściowe, nawet jeśli <xref:System.Windows.FlowDirection> jest poprawna, liczby nie są kształt, jak powinna mieć kształt liczb arabskich.  
  
 Elementy języka XAML może zawierać [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] atrybutu (`xml:lang`) definiuje język każdego elementu. Obsługuje także XAML [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] języka zasady zgodnie z którymi `xml:lang` wartości stosowane do elementów nadrzędnego w drzewie są używane przez elementy podrzędne. W poprzednim przykładzie ponieważ język nie został zdefiniowany dla <xref:System.Windows.Documents.Run> element lub dowolny z jego najwyższego poziomu elementów, domyślnie `xml:lang` użyto, który jest `en-US` dla języka XAML. Wewnętrzny numer kształtowania algorytm [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] wybiera numery w odpowiednim języku — w takim przypadku język angielski. Aby wprowadzić arabski numery renderowania poprawnie `xml:lang` musi być ustawiona.  
  
 Na poniższym rysunku przedstawiono przykład `xml:lang` dodane.  
  
 **Graficzne ilustruje wykorzystanie XML: lang — atrybut**  
  
 ![Liczby arabskie przepływające od prawej do lewej](../../../../docs/framework/wpf/advanced/media/langattribute2.PNG "LangAttribute2")  
  
 W poniższym przykładzie dodano `xml:lang` do aplikacji.  
  
 [!code-xaml[LangAttribute#LangAttribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]  
  
 Należy pamiętać, że wiele języków mają różne `xml:lang` wartości w zależności od regionu docelowe, na przykład `"ar-SA"` i `"ar-EG"` reprezentować dwie odmiany arabski. Poprzednich przykładach trzeba zdefiniować zarówno `xml:lang` i <xref:System.Windows.FlowDirection> wartości.  
  
<a name="FlowDirectionNontext"></a>   
## <a name="flowdirection-with-non-text-elements"></a>Wartość FlowDirection nietekstowych elementów  
 <xref:System.Windows.FlowDirection>Definiuje, nie tylko sposób przepływu tekstu w elemencie tekstową, ale również kierunek przepływu prawie wszystkich innych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementu. Poniżej przedstawiono graficzne <xref:System.Windows.Controls.ToolBar> używającą poziomym <xref:System.Windows.Media.LinearGradientBrush> do rysowania tła.  
  
 **Graficzne, który zawiera narzędzi z lewej do prawej gradientu**  
  
 ![Zrzut ekranu przedstawiający gradient](../../../../docs/framework/wpf/advanced/media/gradient.PNG "gradientu")  
  
 Po ustawieniu <xref:System.Windows.FlowDirection> do <xref:System.Windows.FlowDirection.RightToLeft>, nie tylko <xref:System.Windows.Controls.ToolBar> ułożone przycisków od prawej do lewej, ale nawet <xref:System.Windows.Media.LinearGradientBrush> ponowne wyrównywanie jego przesunięcia, które będą przepływać od prawej do lewej.  
  
 Na poniższym rysunku przedstawiono Wyrównaj ponownie z <xref:System.Windows.Media.LinearGradientBrush>.  
  
 **Grafika przedstawiająca narzędzi z prawej strony do lewej gradientu**  
  
 ![Gradient przepływającego od prawej do lewej](../../../../docs/framework/wpf/advanced/media/gradient2-wpf.PNG "Gradient2_WPF")  
  
 Poniższy przykładowy kod rysuje <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.Controls.ToolBar>. (Aby rysowania od lewej do prawej, Usuń <xref:System.Windows.FlowDirection> atrybutu <xref:System.Windows.Controls.ToolBar>.  
  
 [!code-xaml[Gradient#Gradient](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]  
  
<a name="FlowDirectionExceptions"></a>   
### <a name="flowdirection-exceptions"></a>Wartość FlowDirection wyjątków  
 Istnieje kilka przypadków gdzie <xref:System.Windows.FlowDirection> działają zgodnie z oczekiwaniami. W tej sekcji omówiono dwa z tych wyjątków.  
  
 **Obraz**  
  
 <xref:System.Windows.Controls.Image> Reprezentuje kontrolkę wyświetlającą obraz. W [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] może być używany z <xref:System.Windows.Controls.Image.Source%2A> właściwość, która definiuje [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] z <xref:System.Windows.Controls.Image> do wyświetlenia.  
  
 W odróżnieniu od innych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementów <xref:System.Windows.Controls.Image> nie dziedziczy <xref:System.Windows.FlowDirection> z kontenera. Jednak jeśli <xref:System.Windows.FlowDirection> ustawiono jawnie na <xref:System.Windows.FlowDirection.RightToLeft>, <xref:System.Windows.Controls.Image> jest wyświetlany poziomo odwrócony. Ten sposób jest implementowany jako funkcja wygodny dla deweloperów zawartości dwukierunkowych; ponieważ w niektórych przypadkach poziomie Przerzucanie obrazu daje pożądanych efektów.  
  
 Na poniższym rysunku przedstawiono odwrócony <xref:System.Windows.Controls.Image>.  
  
 **Grafika, która ilustruje odwrócony obraz**  
  
 ![Zrzut ekranu przedstawiający edytor XamlPad](../../../../docs/framework/wpf/advanced/media/image.PNG "obrazu")  
  
 W poniższym przykładzie pokazano, że <xref:System.Windows.Controls.Image> nie dziedziczy <xref:System.Windows.FlowDirection> z <xref:System.Windows.Controls.StackPanel> go zawiera. **Uwaga** musi mieć plik o nazwie **ms_logo.jpg** na dysku C:\ do uruchomienia tego przykładu.  
  
 [!code-xaml[Image#Image](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]  
  
 **Uwaga** jest dołączone do pobierania plików **ms_logo.jpg** pliku. Kod zakłada, że plik jpg nie znajduje się w projekcie, ale miejsce na dysku C:\. Musi kopiować .jpg z plików projektu na dysku C:\, lub zmień kod, aby wyszukać plik wewnątrz projektu. Przeprowadzenie tej zmiany `Source="file://c:/ms_logo.jpg"` do `Source="ms_logo.jpg"`.  
  
 **Ścieżki**  
  
 Oprócz <xref:System.Windows.Controls.Image>, jest inny element interesujące <xref:System.Windows.Shapes.Path>. Ścieżka jest obiekt, który może pobierać serii połączonych linii i krzywych. Działa w sposób podobny do <xref:System.Windows.Controls.Image> dotyczące jego <xref:System.Windows.FlowDirection>, na przykład jego <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> stanowi poziome jego <xref:System.Windows.FlowDirection.LeftToRight> jeden. Jednak w przeciwieństwie do <xref:System.Windows.Controls.Image>, <xref:System.Windows.Shapes.Path> dziedziczy jego <xref:System.Windows.FlowDirection> z kontenera i co trzeba określić ręcznie.  
  
 Poniższy przykład rysuje Prosta strzałka przy użyciu 3 wiersze. Pierwszy strzałkę dziedziczy <xref:System.Windows.FlowDirection.RightToLeft> flow direction z <xref:System.Windows.Controls.StackPanel> tak, aby jego początkowego i końcowego są mierzone od głównego po prawej stronie. Drugi strzałkę mającej jawnego <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> również rozpoczyna się po prawej stronie. Jednak trzeci strzałkę ma początkowy głównym po lewej stronie. Aby uzyskać więcej informacji na rysunku zobacz <xref:System.Windows.Media.LineGeometry> i <xref:System.Windows.Media.GeometryGroup>.  
  
 [!code-xaml[Paths#Paths](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]  
  
 Na poniższym rysunku przedstawiono dane wyjściowe z poprzedniego przykładu.  
  
 **Grafika, która ilustruje strzałki rysowane przy użyciu elementu ścieżki**  
  
 ![Ścieżki](../../../../docs/framework/wpf/advanced/media/paths.PNG "ścieżki")  
  
 <xref:System.Windows.Controls.Image> i <xref:System.Windows.Shapes.Path> przedstawiono dwa przykłady tego, jak [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] używa <xref:System.Windows.FlowDirection>. Obok układania [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementów w określonym kierunku w kontenerze, <xref:System.Windows.FlowDirection> mogą być używane z elementów takich jak <xref:System.Windows.Controls.InkPresenter> która renderuje pismo odręczne na powierzchni, <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>. Jeśli potrzebne jest prawej do lewej zachowania zawartości, które naśladuje od lewej do prawej zachowanie, albo na odwrót [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] udostępnia taką możliwość.  
  
<a name="NumberSubstitution"></a>   
## <a name="number-substitution"></a>Liczba podstawienia  
 W przeszłości [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] obsługiwał zezwalając reprezentację różnych kształtów kultury cyfr samego przy zachowaniu pamięci wewnętrznej te cyfr unified między różnymi ustawieniami regionalnymi, na przykład numery są przechowywane w wielu podstawieniach ich dobrze znane wartości szesnastkowe, 0x40, 0x41, ale wyświetlane zgodnie z wybranym języku.  
  
 Jest to dozwolone aplikacje do przetworzenia wartości liczbowe, bez konieczności przekonwertować je z jednego języka do innego, na przykład użytkownik może otworzyć [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)] arkusza kalkulacyjnego w zlokalizowanych arabski [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] i wyświetlić numery kształt arabski, ale otworzyć go w Wersja co Europejskich [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] i zobacz Europejskiego reprezentację tej samej liczby. To jest również dla innych symboli, takie jak separatory i procent symboli, ponieważ są zwykle dołączone numery w tym samym dokumencie.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Trwa tradycji tego samego i dalsze dodaje obsługę to funkcja, która umożliwia większa kontrola użytkownika nad kiedy i jak podstawienia jest używany. Gdy ta funkcja jest przeznaczona dla dowolnego języka, jego jest szczególnie przydatna w dwukierunkowego zawartości w przypadku, gdy kształtowania cyfr dla określonego języka jest zwykle wyzwanie dla deweloperów aplikacji z powodu różnych kultur, który aplikacja może działać na.  
  
 Właściwości podstawowe kontrolowanie sposobu wielu podstawieniach działa w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jest <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> właściwości zależności. <xref:System.Windows.Media.NumberSubstitution> Klasa określa, jak mają być wyświetlane liczby w tekście. Ma trzy właściwości publiczne, które określają zachowanie. Poniżej znajduje się podsumowanie właściwości.  
  
 **CultureSource:**  
  
 Ta właściwość wskazuje sposób kultury dla liczby. Jedną z trzech zajmuje <xref:System.Windows.Media.NumberCultureSource> wartości wyliczenia.  
  
-   Przesłoń: Liczba kultury jest <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> właściwości.  
  
-   Tekst: Numer kultury jest kultura Uruchom tekstu. W znaczniku, będzie to `xml:lang`, lub jego alias `Language` właściwości (<xref:System.Windows.FrameworkElement.Language%2A> lub <xref:System.Windows.FrameworkContentElement.Language%2A>). Ponadto jest ustawieniem domyślnym dla klasy wywodzące się z <xref:System.Windows.FrameworkContentElement>. Obejmują takie klasy <xref:System.Windows.Documents.Paragraph?displayProperty=nameWithType>, <xref:System.Windows.Documents.Table?displayProperty=nameWithType>, <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType> itd.  
  
-   Użytkownik: Liczba kultury jest kultura bieżącego wątku. Ta właściwość jest ustawieniem domyślnym dla wszystkich podklasy <xref:System.Windows.FrameworkElement> takich jak <xref:System.Windows.Controls.Page>, <xref:System.Windows.Window> i <xref:System.Windows.Controls.TextBlock>.  
  
 **CultureOverride**:  
  
 <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> Właściwość jest używana tylko wtedy, gdy <xref:System.Windows.Media.NumberSubstitution.CultureSource%2A> właściwość jest ustawiona na <xref:System.Windows.Media.NumberCultureSource.Override> i jest ignorowany w innych przypadkach. Określa numer kultury. Wartość `null`, wartością domyślną jest interpretowana jako en US.  
  
 **Podstawienie**:  
  
 Ta właściwość określa typ wielu podstawieniach do wykonania. Jedną z następujących zajmuje <xref:System.Windows.Media.NumberSubstitutionMethod> wartości wyliczenia.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.AsCulture>: Metoda podstawienia jest określana według numerów kultury <xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=nameWithType> właściwości. Domyślnie włączone.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.Context>: Jeśli numer kultury jest kulturą arabskiego lub Farsi, określa, że cyfry są zależne od kontekstu.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.European>: Cyfry są renderowane co Europejskich cyfr.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>: Cyfry są renderowane przy użyciu national cyfr numeru kultury, zgodnie z kulturą <xref:System.Globalization.CultureInfo.NumberFormat%2A>.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.Traditional>: Cyfry są renderowane przy użyciu tradycyjnych cyfr numeru kultury. Dla większości kultur jest taka sama jak <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>. Jednak <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational> powoduje alfabetu łacińskiego cyfr dla niektórych Arabic kultury, natomiast wartość ta powoduje Arabic cyfr dla wszystkich języków Arabic.  
  
 Co oznaczają te wartości dwukierunkowego projektantowi zawartości? W większości przypadków deweloper może być konieczne tylko zdefiniować <xref:System.Windows.FlowDirection> i język każdy tekstową [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] element, na przykład `Language="ar-SA"` i <xref:System.Windows.Media.NumberSubstitution> logiki dba o wyświetlaniu liczb zgodnie z poprawny [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. W poniższym przykładzie pokazano, przy użyciu arabski i angielski numerów [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji uruchomionej w wersji Arabic [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  
  
 [!code-xaml[Numbers#Numbers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]  
  
 Na poniższym rysunku przedstawiono dane wyjściowe poprzedniego przykładu, jeśli używasz wersji Arabic [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  
  
 **Grafika przedstawiająca Arabic i angielskiej wersji językowej liczby wyświetlane**  
  
 ![Ekranu przedstawiający numerami edytor XamlPad](../../../../docs/framework/wpf/advanced/media/numbers.PNG "liczb")  
  
 <xref:System.Windows.FlowDirection> Jest ważna w tym przypadku, ponieważ ustawienie <xref:System.Windows.FlowDirection> do <xref:System.Windows.FlowDirection.LeftToRight> zamiast tego będzie mieć zwróciło Europejskiego cyfr. W poniższych sekcjach omówiono sposób mieć wyłącznie ujednoliconą wyświetlania cyfr w całym dokumencie. Jeśli w tym przykładzie nie jest uruchomiony w systemie Windows arabski, wszystkie cyfry wyświetlanie co Europejskich cyfr.  
  
 **Definiowanie reguł podstawienia**  
  
 W rzeczywistej aplikacji może być konieczne ustawić język programowo. Na przykład chcesz ustawić `xml:lang` atrybutu, aby była taka sama jak używany przez system [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], lub może zmienić język, w zależności od stanu aplikacji.  
  
 Jeśli chcesz zmiany oparte na stanie aplikacji, należy korzystać z innych funkcji udostępnianych przez [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 Najpierw należy ustawić składnika aplikacji `NumberSubstitution.CultureSource="Text"`. Za pomocą tego ustawienia upewnia się, że ustawienia nie pochodzą z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dla elementów tekstu, które mają "Użytkownika" jako domyślny, takich jak <xref:System.Windows.Controls.TextBlock>.  
  
 Na przykład:  
  
||  
|-|  
|`<TextBlock`<br /><br /> `Name="text1" NumberSubstitution.CultureSource="Text">`<br /><br /> `1234+5679=6913`<br /><br /> `</TextBlock>`|  
  
 W polu [!INCLUDE[TLA2#tla_lhcshrp](../../../../includes/tla2sharptla-lhcshrp-md.md)] kodu, ustaw `Language` właściwości na przykład, aby `"ar-SA"`.  
  
||  
|-|  
|`text1.Language =`<br /><br /> `System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");`|  
  
 Jeśli musisz ustawić `Language` właściwości z bieżącym użytkownikiem [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] języka użyć poniższego kodu.  
  
||  
|-|  
|`text1.Language =`<br /><br /> `System.Windows.Markup.XmlLanguage.GetLanguage(`<br /><br /> `System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);`|  
  
 <xref:System.Globalization.CultureInfo.CurrentCulture%2A>reprezentuje bieżącą kulturę używaną przez bieżący wątek w czasie wykonywania.  
  
 Twoje final [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] przykład powinien być podobny do poniższego przykładu.  
  
 [!code-xaml[Numbers2#Numbers2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]  
  
 Twoje final [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] powinien być podobny do następującego.  
  
 [!code-csharp[NumbersCSharp#NumbersCSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]  
  
 Na poniższym rysunku przedstawiono, jak wygląda okna dla albo języka programowania.  
  
 **Graficzne, który wyświetla liczb arabskich**  
  
 ![Liczb arabskich](../../../../docs/framework/wpf/advanced/media/numbers2.PNG "Numbers2")  
  
 **Za pomocą właściwości podstawienia**  
  
 Sposób wielu podstawieniach działa w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zależy od języka tekstu elementu i jego <xref:System.Windows.FlowDirection>. Jeśli <xref:System.Windows.FlowDirection> jest od lewej do prawej, następnie Europejskiego cyfr są renderowane. Jednak jeśli jest poprzedzony tekstu arabskiego lub ma ustawiony język "ar" i <xref:System.Windows.FlowDirection> jest <xref:System.Windows.FlowDirection.RightToLeft>, zamiast renderowania Arabic cyfr.  
  
 Jednak w niektórych przypadkach może chcesz utworzyć aplikację ujednoliconą, na przykład Europejskiego cyfr dla wszystkich użytkowników. Lub Arabic cyfr w <xref:System.Windows.Documents.Table> komórki z określonym <xref:System.Windows.Style>. Jeden łatwy sposób przeprowadzenia używanej <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> właściwości.  
  
 W poniższym przykładzie pierwszy <xref:System.Windows.Controls.TextBlock> nie ma <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> zbioru właściwości, dlatego algorytm Wyświetla Arabic cyfr, zgodnie z oczekiwaniami. Jednak w ciągu sekundy <xref:System.Windows.Controls.TextBlock>podstawienie ma ustawioną wartość Europejskiej zastępowanie zastąpienia domyślnej liczb arabskich i Europejskiego cyfry są wyświetlane.  
  
 [!code-xaml[Numbers3#Numbers3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]
