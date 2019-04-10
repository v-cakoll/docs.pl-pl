---
title: Przegląd Multimedia
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
ms.openlocfilehash: ffdcb58cdd332f9c730e7ed367e0f8bcc56da459
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222097"
---
# <a name="multimedia-overview"></a>Przegląd Multimedia
Multimediów funkcje w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] umożliwiają integrowanie audio i wideo w aplikacje w celu poprawienia środowiska użytkownika. W tym temacie przedstawiono funkcje multimedialne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="mediaapi"></a>   
## <a name="media-api"></a>Interfejs API multimediów  
 <xref:System.Windows.Controls.MediaElement> i <xref:System.Windows.Media.MediaPlayer> klasy są używane do przedstawienia zawartości audio i wideo. Te klasy można sterować interaktywnie lub za pomocą zegara. Te klasy można użyć na [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 kontrolka odtwarzania multimediów. Klasy, których używasz, zależy od scenariusza.  
  
 <xref:System.Windows.Controls.MediaElement> jest <xref:System.Windows.UIElement> który jest obsługiwany przez [układ](../advanced/layout.md) i mogą być używane jako zawartość wiele kontrolek. Jest również mogą być stosowane w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] oraz kod. <xref:System.Windows.Media.MediaPlayer>, z drugiej strony, zaprojektowano pod kątem <xref:System.Windows.Media.Drawing> obiektów i nie ma obsługi układu. Nośnik załadowany przy użyciu <xref:System.Windows.Media.MediaPlayer> mogą być podane tylko przy użyciu <xref:System.Windows.Media.VideoDrawing> lub poprzez bezpośrednie interakcje <xref:System.Windows.Media.DrawingContext>. <xref:System.Windows.Media.MediaPlayer> Nie można używać w XAML.  
  
 Aby uzyskać więcej informacji na temat Rysowanie obiektów i rysowanie w kontekście zobacz [Przegląd Rysowanie obiektów](drawing-objects-overview.md).  
  
> [!NOTE]
>  Podczas dystrybucji multimediów za pomocą aplikacji, nie można użyć pliku multimedialnego jako zasób projektu. W pliku projektu, należy zamiast tego ustawić typ nośnika na `Content` i ustaw `CopyToOutputDirectory` do `PreserveNewest` lub `Always`.  
  
<a name="mediaplaybackmodes"></a>   
## <a name="media-playback-modes"></a>Tryby odtwarzanie nośnika  
  
> [!NOTE]
>  Zarówno <xref:System.Windows.Controls.MediaElement> i <xref:System.Windows.Media.MediaPlayer> mają podobnych elementów członkowskich. Łącza w tej sekcji dotyczą <xref:System.Windows.Controls.MediaElement> składowych klasy. O ile nie zaznaczono inaczej, połączyć elementy członkowskie w <xref:System.Windows.Controls.MediaElement> klasy można również znaleźć w <xref:System.Windows.Media.MediaPlayer> klasy.  
  
 Aby zrozumieć odtwarzania multimediów w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], zrozumienie różnych trybach, w których mogą być odtwarzane nośnika jest wymagana. Zarówno <xref:System.Windows.Controls.MediaElement> i <xref:System.Windows.Media.MediaPlayer> mogą być używane w dwóch trybów innych nośników, niezależnie od trybu ani zegara. Tryb nośnika jest określana przez <xref:System.Windows.Controls.MediaElement.Clock%2A> właściwości. Gdy <xref:System.Windows.Controls.MediaElement.Clock%2A> jest `null`, obiekt multimediów jest w trybie niezależne. Gdy <xref:System.Windows.Controls.MediaElement.Clock%2A> jest różna od null, obiekt multimedialny jest w trybie zegara. Domyślnie obiektów multimedialnych są w trybie niezależne.  
  
### <a name="independent-mode"></a>Niezależnie od trybu  
 W trybie niezależne zawartości multimedialnej dysków odtwarzania multimediów. Niezależnie od trybu umożliwia następujące opcje:  
  
-   Nośnika <xref:System.Uri> można określić bezpośrednio.  
  
-   Odtwarzanie multimediów, mogą być kontrolowane bezpośrednio.  
  
-   Nośnika <xref:System.Windows.Controls.MediaElement.Position%2A> i <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> można zmodyfikować właściwości.  
  
 Nośnik jest ładowany przez dowolnego z tych ustawień <xref:System.Windows.Controls.MediaElement> obiektu <xref:System.Windows.Controls.MediaElement.Source%2A> właściwości lub przez wywołanie <xref:System.Windows.Media.MediaPlayer> obiektu <xref:System.Windows.Media.MediaPlayer.Open%2A> metody.  
  
 Aby kontrolować odtwarzanie multimediów w trybie niezależne, może służyć do obiektu multimedialnego metod kontroli. Dostępne metody kontroli <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>, i <xref:System.Windows.Controls.MediaElement.Stop%2A>. Aby uzyskać <xref:System.Windows.Controls.MediaElement>, interaktywne formant przy użyciu tych metod jest dostępna tylko podczas <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> jest ustawiona na <xref:System.Windows.Controls.MediaState.Manual>. Te metody są niedostępne, gdy obiekt multimedialny jest w trybie zegara.  
  
 Zobacz [sterowanie elementem MediaElement (Odtwórz, Wstrzymaj, Stop, woluminów i szybkość)](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md) przykład niezależnie od trybu.  
  
### <a name="clock-mode"></a>Tryb zegara  
 W trybie zegara <xref:System.Windows.Media.MediaTimeline> odtwarzania multimediów dysków. Tryb zegara ma następującą charakterystykę:  
  
-   Nośnika <xref:System.Uri> jest pośrednio ustawiona za pomocą <xref:System.Windows.Media.MediaTimeline>.  
  
-   Odtwarzanie multimediów mogą być kontrolowane przez zegara. Nie można używać metod kontroli do obiektu multimedialnego.  
  
-   Nośnik jest ładowany przez ustawienie <xref:System.Windows.Media.MediaTimeline> obiektu <xref:System.Windows.Media.MediaTimeline.Source%2A> właściwość, tworzenie zegar z osi czasu i przypisywanie zegara do obiektu multimedialnego. Nośnik jest również ładowana w ten sposób podczas <xref:System.Windows.Media.MediaTimeline> wewnątrz <xref:System.Windows.Media.Animation.Storyboard> cele <xref:System.Windows.Controls.MediaElement>.  
  
 Aby kontrolować odtwarzanie multimediów w trybie zegara <xref:System.Windows.Media.Animation.ClockController> należy używać metod kontroli. A <xref:System.Windows.Media.Animation.ClockController> są uzyskiwane z <xref:System.Windows.Media.Animation.ClockController> właściwość <xref:System.Windows.Media.MediaClock>. Jeśli spróbujesz użyć metody kontroli albo <xref:System.Windows.Controls.MediaElement> lub <xref:System.Windows.Media.MediaPlayer> obiektu w trybie zegara <xref:System.InvalidOperationException> zostanie zgłoszony.  
  
 Zobacz [Przegląd animacja](animation-overview.md) Aby uzyskać więcej informacji na temat zegary i osie czasu.  
  
 Zobacz [sterowanie elementem MediaElement z użyciem scenorysu](how-to-control-a-mediaelement-by-using-a-storyboard.md) przykład trybu zegara.  
  
<a name="mediaelement"></a>   
## <a name="mediaelement-class"></a>Klasa MediaElement  
 Dodawanie multimediów do aplikacji jest równie proste, jak dodawanie <xref:System.Windows.Controls.MediaElement> kontrolę [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] aplikacji i zapewnianie <xref:System.Uri> na nośniku, które mają zostać uwzględnione. Wszystkich typów nośników obsługiwanych przez [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 są obsługiwane w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Poniższy przykład pokazuje prosty sposób użycia klasy <xref:System.Windows.Controls.MediaElement> w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 W tym przykładzie odtwarzania multimediów automatycznie zaraz po jego załadowaniu. Po zakończeniu nośnika podczas odtwarzania, nośnika jest zamknięty, a wszystkie zasoby multimediów są wydania (w tym wideo pamięci). Jest to domyślne zachowanie <xref:System.Windows.Controls.MediaElement> obiektu i jest kontrolowana przez <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> i <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> właściwości.  
  
### <a name="controlling-a-mediaelement"></a>Kontrolowanie MediaElement  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> i <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> właściwości kontrolują zachowanie <xref:System.Windows.Controls.MediaElement> podczas <xref:System.Windows.FrameworkElement.IsLoaded%2A> jest `true` lub `false`, odpowiednio. <xref:System.Windows.Controls.MediaState> Właściwości są ustawione na mają wpływ na zachowanie odtwarzania multimediów. Na przykład, wartość domyślna <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> jest <xref:System.Windows.Controls.MediaState.Play> i domyślnego <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> jest <xref:System.Windows.Controls.MediaState.Close>. Oznacza to, że jak tylko <xref:System.Windows.Controls.MediaElement> jest ładowany i preroll zakończeniu nośnika rozpocznie się odtworzyć. Po zakończeniu odtwarzania multimediów jest zamknięty, a wszystkie zasoby multimediów są zwalniane.  
  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> i <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> właściwości nie są jedynym sposobem, aby kontrolować odtwarzanie multimediów. W trybie zegara, zegara można kontrolować <xref:System.Windows.Controls.MediaElement> i mają decyduje o metod kontroli interaktywne <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> jest <xref:System.Windows.Controls.MediaState.Manual>. <xref:System.Windows.Controls.MediaElement> obsługuje to konkurowanie o kontroli poprzez ocenę następujące priorytety.  
  
1.  <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>. W miejscu, jeśli nośnik jest zwalniana. Daje to gwarancję, że wszystkie zasoby multimediów są wydawane domyślnie nawet wtedy, gdy <xref:System.Windows.Media.MediaClock> jest skojarzony z <xref:System.Windows.Controls.MediaElement>.  
  
2.  <xref:System.Windows.Media.MediaClock>. W miejscu, w przypadku nośnika <xref:System.Windows.Controls.MediaElement.Clock%2A>. Jeśli nośnik jest zwolniony, <xref:System.Windows.Media.MediaClock> zaczną obowiązywać tak długo, jak <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> jest <xref:System.Windows.Controls.MediaState.Manual>. Tryb zegara zawsze zastępuje załadować zachowanie <xref:System.Windows.Controls.MediaElement>.  
  
3.  <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>. W miejsce po załadowaniu nośnika.  
  
4.  Metody kontroli interaktywne. W miejscu, gdy <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> jest <xref:System.Windows.Controls.MediaState.Manual>. Dostępne metody kontroli <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>, i <xref:System.Windows.Controls.MediaElement.Stop%2A>.  
  
### <a name="displaying-a-mediaelement"></a>Wyświetlanie MediaElement  
 Aby wyświetlić <xref:System.Windows.Controls.MediaElement> musi mieć zawartość do renderowania i będzie mieć jej <xref:System.Windows.FrameworkElement.ActualWidth%2A> i <xref:System.Windows.FrameworkElement.ActualHeight%2A> właściwości ustawione na wartość zero do momentu załadowania zawartości. Tylko zawartość audio te właściwości są zawsze zero. W przypadku zawartości wideo po <xref:System.Windows.Controls.MediaElement.MediaOpened> zdarzenia <xref:System.Windows.FrameworkElement.ActualWidth%2A> i <xref:System.Windows.FrameworkElement.ActualHeight%2A> będzie raportu rozmiar załadowane nośniki. Oznacza to, że do momentu załadowania nośnika, <xref:System.Windows.Controls.MediaElement> nie podejmie żadnych fizycznego miejsca w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] chyba że <xref:System.Windows.FrameworkElement.Width%2A> lub <xref:System.Windows.FrameworkElement.Height%2A> właściwości są ustawione.  
  
 Ustawienie oba <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości spowoduje, że nośnik Stretch Database, aby wypełnił obszar przewidziane <xref:System.Windows.Controls.MediaElement>. Aby zachować multimediów oryginalnego współczynnika proporcji, albo <xref:System.Windows.FrameworkElement.Width%2A> lub <xref:System.Windows.FrameworkElement.Height%2A> właściwość powinna być w zestawie, ale nie oba jednocześnie. Ustawienie oba <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> spowoduje, że właściwości nośnika, aby przedstawić w rozmiarze elementem o stałej nie może być pożądane.  
  
 Aby uniknąć elementu o stałym rozmiarze, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] można buforowania multimediów. Jest to realizowane przez ustawienie <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> do jednej <xref:System.Windows.Controls.MediaState.Play> lub <xref:System.Windows.Controls.MediaState.Pause>. W <xref:System.Windows.Controls.MediaState.Pause> stanu nośnik zostanie buforowania i będzie przedstawiać pierwszej ramki. W <xref:System.Windows.Controls.MediaState.Play> stanu nośnik buforowania i odtworzony.  
  
<a name="mediaplayer"></a>   
## <a name="mediaplayer-class"></a>MediaPlayer — klasa  
 W przypadku gdy <xref:System.Windows.Controls.MediaElement> klasa jest elementem framework <xref:System.Windows.Media.MediaPlayer> klasa jest przeznaczona do użycia w <xref:System.Windows.Media.Drawing> obiektów. Rysowanie obiektów są używane, gdy pochodzących z poziomu funkcji framework korzyści w wydajności lub gdy potrzebujesz <xref:System.Windows.Freezable> funkcji. <xref:System.Windows.Media.MediaPlayer> umożliwia dostarczanie zawartości multimedialnej w swoich aplikacjach zacząć czerpać korzyści z tych funkcji. Podobnie jak <xref:System.Windows.Controls.MediaElement>, <xref:System.Windows.Media.MediaPlayer> mogą być używane w niezależne lub nie zegara trybu, ale nie mają <xref:System.Windows.Controls.MediaElement> zwolnione i załadować stanów obiektów. Pozwala to ograniczyć złożoność kontrolki odtwarzania <xref:System.Windows.Media.MediaPlayer>.  
  
### <a name="controlling-mediaplayer"></a>Kontrolowanie MediaPlayer  
 Ponieważ <xref:System.Windows.Media.MediaPlayer> jest bezstanowych, istnieją tylko dwa sposoby, aby kontrolować odtwarzanie multimediów.  
  
1.  Metody kontroli interaktywne. W miejscu, w trybie niezależne (`null`<xref:System.Windows.Media.MediaPlayer.Clock%2A> właściwości).  
  
2.  <xref:System.Windows.Media.MediaClock>. W miejscu, w przypadku nośnika <xref:System.Windows.Media.MediaPlayer.Clock%2A>.  
  
### <a name="displaying-a-mediaplayer"></a>Wyświetlanie MediaPlayer  
 Z technicznego punktu widzenia <xref:System.Windows.Media.MediaPlayer> nie można wyświetlić, ponieważ ma ona nie fizyczna reprezentacja. Jednak może służyć do prezentowania multimediów w <xref:System.Windows.Media.Drawing> przy użyciu <xref:System.Windows.Media.VideoDrawing> klasy. W poniższym przykładzie pokazano użycie <xref:System.Windows.Media.VideoDrawing> do wyświetlenia nośnika.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Zobacz [Przegląd obiektów rysowania](drawing-objects-overview.md) Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.Drawing> obiektów.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.DrawingGroup>
- [Układ](../advanced/layout.md)
- [— Tematy porad](audio-and-video-how-to-topics.md)
