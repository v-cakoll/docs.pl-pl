---
title: Przegląd Multimedia
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
ms.openlocfilehash: 42d0d388e859b556d23b7fc81931cd61470ba541
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039803"
---
# <a name="multimedia-overview"></a>Przegląd Multimedia
Funkcje multimedialne w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] umożliwiają integrację audio i wideo z aplikacjami w celu ulepszenia środowiska użytkownika. W tym temacie przedstawiono funkcje multimedialne [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="mediaapi"></a>   
## <a name="media-api"></a>Interfejs API multimediów  
 Klasy <xref:System.Windows.Controls.MediaElement> i <xref:System.Windows.Media.MediaPlayer> są używane do prezentowania zawartości audio lub wideo. Te klasy mogą być sterowane interaktywnie lub przez zegar. Te klasy mogą być używane na potrzeby odtwarzania multimediów w systemie Microsoft Windows Media Player 10. Której klasy używasz, zależy od scenariusza.  
  
 <xref:System.Windows.Controls.MediaElement> jest <xref:System.Windows.UIElement> obsługiwana przez [Układ](../advanced/layout.md) i może być używana jako zawartość wielu kontrolek. Jest również użyteczny w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], jak również kod. <xref:System.Windows.Media.MediaPlayer>, z drugiej strony, jest przeznaczony dla obiektów <xref:System.Windows.Media.Drawing> i nie obsługuje układu. Nośnik załadowany przy użyciu <xref:System.Windows.Media.MediaPlayer> może być przedstawiony tylko przy użyciu <xref:System.Windows.Media.VideoDrawing> lub bezpośrednio z <xref:System.Windows.Media.DrawingContext>. nie można użyć <xref:System.Windows.Media.MediaPlayer> w języku XAML.  
  
 Aby uzyskać więcej informacji na temat rysowania obiektów i kontekstu rysowania, zobacz [Omówienie obiektów rysowania](drawing-objects-overview.md).  
  
> [!NOTE]
> Podczas dystrybucji multimediów za pomocą aplikacji nie można używać pliku multimedialnego jako zasobu projektu. W pliku projektu należy zamiast tego ustawić typ nośnika na `Content` i ustawić `CopyToOutputDirectory` na `PreserveNewest` lub `Always`.  
  
<a name="mediaplaybackmodes"></a>   
## <a name="media-playback-modes"></a>Tryby odtwarzania multimediów  
  
> [!NOTE]
> Zarówno <xref:System.Windows.Controls.MediaElement>, jak i <xref:System.Windows.Media.MediaPlayer> mają podobne elementy członkowskie. Linki w tej sekcji odnoszą się do elementów członkowskich klasy <xref:System.Windows.Controls.MediaElement>. O ile nie zaznaczono inaczej, elementy członkowskie połączone z klasą <xref:System.Windows.Controls.MediaElement> można również znaleźć w klasie <xref:System.Windows.Media.MediaPlayer>.  
  
 Aby zrozumieć odtwarzanie multimediów w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], należy zapoznać się z różnymi trybami, w których można odtwarzać multimedia. Zarówno <xref:System.Windows.Controls.MediaElement>, jak i <xref:System.Windows.Media.MediaPlayer> mogą być używane w dwóch różnych trybach nośnika, Tryb niezależny i tryb zegara. Tryb multimedialny jest określany przez właściwość <xref:System.Windows.Controls.MediaElement.Clock%2A>. Gdy <xref:System.Windows.Controls.MediaElement.Clock%2A> jest `null`, obiekt multimedialny jest w trybie niezależnym. Gdy <xref:System.Windows.Controls.MediaElement.Clock%2A> ma wartość różną od null, obiekt multimedialny jest w trybie zegara. Domyślnie obiekty multimedialne są w trybie niezależnym.  
  
### <a name="independent-mode"></a>Tryb niezależny  
 W trybie niezależnym zawartość multimedialna jest odtwarzana na nośnikach. Tryb niezależny zapewnia następujące opcje:  
  
- <xref:System.Uri> można określić bezpośrednio dla nośnika.  
  
- Odtwarzanie multimediów można kontrolować bezpośrednio.  
  
- <xref:System.Windows.Controls.MediaElement.Position%2A> i właściwości <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> multimediów można modyfikować.  
  
 Nośnik jest ładowany przez ustawienie właściwości <xref:System.Windows.Controls.MediaElement.Source%2A> obiektu <xref:System.Windows.Controls.MediaElement> lub przez wywołanie metody <xref:System.Windows.Media.MediaPlayer.Open%2A> obiektu <xref:System.Windows.Media.MediaPlayer>.  
  
 Aby sterować odtwarzaniem multimediów w trybie niezależnym, można użyć metod kontroli obiektu multimedialnego. Dostępne metody kontrolne to <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>i <xref:System.Windows.Controls.MediaElement.Stop%2A>. W przypadku <xref:System.Windows.Controls.MediaElement>interaktywna kontrola przy użyciu tych metod jest dostępna tylko wtedy, gdy <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> jest ustawiona na <xref:System.Windows.Controls.MediaState.Manual>. Te metody są niedostępne, gdy obiekt multimedialny jest w trybie zegara.  
  
 Zobacz [Control MediaElement (Play, Pause, stop, Volume i Speed)](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md) , aby zapoznać się z przykładowym trybem niezależnym.  
  
### <a name="clock-mode"></a>Tryb zegara  
 W trybie zegara <xref:System.Windows.Media.MediaTimeline> dyski odtwarzania multimediów. Tryb zegara ma następujące cechy:  
  
- <xref:System.Uri> multimediów jest pośrednio ustawiany za pomocą <xref:System.Windows.Media.MediaTimeline>.  
  
- Odtwarzanie multimediów może być kontrolowane przez zegar. Nie można używać metod sterowania obiektu multimedialnego.  
  
- Nośnik jest ładowany przez ustawienie właściwości <xref:System.Windows.Media.MediaTimeline.Source%2A> obiektu <xref:System.Windows.Media.MediaTimeline>, utworzenie zegara z osi czasu i przypisanie zegara do obiektu multimedialnego. Nośnik jest również ładowany w ten sposób, gdy <xref:System.Windows.Media.MediaTimeline> wewnątrz <xref:System.Windows.Media.Animation.Storyboard>y jako element docelowy <xref:System.Windows.Controls.MediaElement>.  
  
 Aby można było sterować odtwarzaniem multimediów w trybie zegara, należy użyć metod kontroli <xref:System.Windows.Media.Animation.ClockController>. <xref:System.Windows.Media.Animation.ClockController> jest uzyskiwany z właściwości <xref:System.Windows.Media.Animation.ClockController> <xref:System.Windows.Media.MediaClock>. Jeśli spróbujesz użyć metod kontrolnych obiektu <xref:System.Windows.Controls.MediaElement> lub <xref:System.Windows.Media.MediaPlayer> w trybie zegara, zostanie zgłoszony <xref:System.InvalidOperationException>.  
  
 Zobacz [Omówienie animacji](animation-overview.md) , aby uzyskać więcej informacji na temat zegarów i osi czasu.  
  
 Zobacz [kontrolowanie elementu MediaElement przy użyciu scenorysu](how-to-control-a-mediaelement-by-using-a-storyboard.md) na przykład trybu zegara.  
  
<a name="mediaelement"></a>   
## <a name="mediaelement-class"></a>MediaElement — Klasa  
 Dodawanie multimediów do aplikacji jest tak proste, jak dodanie formantu <xref:System.Windows.Controls.MediaElement> do [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] aplikacji i dostarczenie <xref:System.Uri> do nośnika, który ma zostać uwzględniony. W [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]obsługiwane są wszystkie typy nośników obsługiwane przez system Microsoft Windows Media Player 10. W poniższym przykładzie pokazano proste użycie <xref:System.Windows.Controls.MediaElement> w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 W tym przykładzie nośnik jest odtwarzany automatycznie zaraz po jego załadowaniu. Po zakończeniu odtwarzania nośnika nośnik zostanie zamknięty i wszystkie zasoby multimedialne są zwalniane (w tym pamięci wideo). Jest to domyślne zachowanie obiektu <xref:System.Windows.Controls.MediaElement> i jest ono kontrolowane przez właściwości <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> i <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>.  
  
### <a name="controlling-a-mediaelement"></a>Kontrolowanie elementu MediaElement  
 Właściwości <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> i <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> kontrolują zachowanie <xref:System.Windows.Controls.MediaElement>, gdy <xref:System.Windows.FrameworkElement.IsLoaded%2A> jest odpowiednio `true` lub `false`. <xref:System.Windows.Controls.MediaState> właściwości są ustawione na wpływ na zachowanie odtwarzania multimediów. Na przykład domyślną <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> jest <xref:System.Windows.Controls.MediaState.Play>, a <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> domyślne to <xref:System.Windows.Controls.MediaState.Close>. Oznacza to, że zaraz po załadowaniu <xref:System.Windows.Controls.MediaElement> i zakończeniu preroll rozpocznie się odtwarzanie nośnika. Po zakończeniu odtwarzania nośnik zostanie zamknięty i zostaną wydane wszystkie zasoby multimedialne.  
  
 Właściwości <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> i <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> nie są jedynym sposobem sterowania odtwarzaniem multimediów. W trybie zegara zegar może kontrolować <xref:System.Windows.Controls.MediaElement> i interaktywne metody sterowania kontrolują, kiedy <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> jest <xref:System.Windows.Controls.MediaState.Manual>. <xref:System.Windows.Controls.MediaElement> obsługuje tę konkurs kontroli, oceniając następujące priorytety.  
  
1. <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>., W miejscu, gdy nośnik zostanie zwolniony. Gwarantuje to, że wszystkie zasoby multimedialne są domyślnie udostępniane, nawet jeśli <xref:System.Windows.Media.MediaClock> jest skojarzona z <xref:System.Windows.Controls.MediaElement>.  
  
2. <xref:System.Windows.Media.MediaClock>., W miejscu, gdy nośnik ma <xref:System.Windows.Controls.MediaElement.Clock%2A>. Jeśli nośnik zostanie zwolniony, <xref:System.Windows.Media.MediaClock> zacznie obowiązywać, dopóki <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> zostanie <xref:System.Windows.Controls.MediaState.Manual>. Tryb zegara zawsze zastępuje załadowane zachowanie <xref:System.Windows.Controls.MediaElement>.  
  
3. <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>., W miejscu podczas ładowania nośnika.  
  
4. Metody interaktywnej kontroli. Na miejscu, gdy <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> jest <xref:System.Windows.Controls.MediaState.Manual>. Dostępne metody kontrolne to <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>i <xref:System.Windows.Controls.MediaElement.Stop%2A>.  
  
### <a name="displaying-a-mediaelement"></a>Wyświetlanie elementu MediaElement  
 Aby wyświetlić <xref:System.Windows.Controls.MediaElement> musi mieć zawartość do renderowania, a jej <xref:System.Windows.FrameworkElement.ActualWidth%2A> i właściwości <xref:System.Windows.FrameworkElement.ActualHeight%2A> ustawione na zero do momentu załadowania zawartości. W przypadku zawartości tylko audio, te właściwości są zawsze zerowe. W przypadku zawartości wideo, gdy zdarzenie <xref:System.Windows.Controls.MediaElement.MediaOpened> zostało zgłoszone <xref:System.Windows.FrameworkElement.ActualWidth%2A>, a <xref:System.Windows.FrameworkElement.ActualHeight%2A> spowoduje zgłoszenie rozmiaru załadowanego nośnika. Oznacza to, że do momentu załadowania multimediów <xref:System.Windows.Controls.MediaElement> nie zajmie żadnego miejsca fizycznego w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], chyba że zostaną ustawione właściwości <xref:System.Windows.FrameworkElement.Width%2A> lub <xref:System.Windows.FrameworkElement.Height%2A>.  
  
 Ustawienie właściwości <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> spowoduje rozciągnięcie nośnika w celu wypełnienia obszaru dostarczonego dla <xref:System.Windows.Controls.MediaElement>. Aby zachować pierwotny współczynnik proporcji nośnika, należy ustawić właściwość <xref:System.Windows.FrameworkElement.Width%2A> lub <xref:System.Windows.FrameworkElement.Height%2A>, ale nie obie. Ustawienie właściwości <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> spowoduje, że nośnik zostanie zaprezentowany w stałym rozmiarze elementu, który może nie być pożądany.  
  
 Aby uniknąć posiadania elementu o stałym rozmiarze, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] może przedrzutować nośnik. W tym celu należy ustawić <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> na <xref:System.Windows.Controls.MediaState.Play> lub <xref:System.Windows.Controls.MediaState.Pause>. W stanie <xref:System.Windows.Controls.MediaState.Pause> nośnik zostanie przeddany i zaprezentuje pierwszą ramkę. W stanie <xref:System.Windows.Controls.MediaState.Play> nośnik zostanie przedgrany i rozpocznie się odtwarzanie.  
  
<a name="mediaplayer"></a>   
## <a name="mediaplayer-class"></a>Klasa MediaPlayer  
 Gdzie Klasa <xref:System.Windows.Controls.MediaElement> jest elementem Framework, Klasa <xref:System.Windows.Media.MediaPlayer> została zaprojektowana tak, aby była używana w obiektach <xref:System.Windows.Media.Drawing>. Obiekty rysunkowe są używane, gdy można wymusić funkcje poziomu platformy w celu uzyskania korzyści z wydajności lub gdy potrzebujesz <xref:System.Windows.Freezable> funkcji. <xref:System.Windows.Media.MediaPlayer> umożliwia korzystanie z tych funkcji przy udostępnianiu zawartości multimedialnej w aplikacjach. Podobnie jak <xref:System.Windows.Controls.MediaElement>, <xref:System.Windows.Media.MediaPlayer> może być używany w trybie niezależnym lub zegarowym, ale nie ma Stanów <xref:System.Windows.Controls.MediaElement>, które są zwolnione i załadowane. Zmniejsza to złożoność formantu odtwarzania <xref:System.Windows.Media.MediaPlayer>.  
  
### <a name="controlling-mediaplayer"></a>Kontrolowanie MediaPlayer  
 Ponieważ <xref:System.Windows.Media.MediaPlayer> jest bezstanowa, istnieją tylko dwa sposoby sterowania odtwarzaniem multimediów.  
  
1. Metody interaktywnej kontroli. W miejscu w trybie niezależnym (`null`<xref:System.Windows.Media.MediaPlayer.Clock%2A> Właściwość).  
  
2. <xref:System.Windows.Media.MediaClock>., W miejscu, gdy nośnik ma <xref:System.Windows.Media.MediaPlayer.Clock%2A>.  
  
### <a name="displaying-a-mediaplayer"></a>Wyświetlanie MediaPlayer  
 Technicznie nie można wyświetlić <xref:System.Windows.Media.MediaPlayer>, ponieważ nie ma fizycznego przedstawienia. Można go jednak użyć do prezentowania nośników w <xref:System.Windows.Media.Drawing> przy użyciu klasy <xref:System.Windows.Media.VideoDrawing>. Poniższy przykład ilustruje użycie <xref:System.Windows.Media.VideoDrawing> do wyświetlania multimediów.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Zobacz [Omówienie obiektów rysowania](drawing-objects-overview.md) , aby uzyskać więcej informacji na temat <xref:System.Windows.Media.Drawing> obiektów.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.DrawingGroup>
- [Układ](../advanced/layout.md)
- [Tematy z instrukcjami](audio-and-video-how-to-topics.md)
