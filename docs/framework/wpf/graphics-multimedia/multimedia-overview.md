---
title: Przegląd Multimedia
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
ms.openlocfilehash: d4abf4d9fd324ffbf2737dc686c02e50ca1a8a5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181886"
---
# <a name="multimedia-overview"></a>Przegląd Multimedia
Funkcje multimedialne umożliwiają integrację dźwięku i wideo z aplikacjami w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] celu zwiększenia komfortu użytkowania. W tym temacie przedstawiono [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]funkcje multimedialne programu .  

<a name="mediaapi"></a>
## <a name="media-api"></a>Interfejs API multimediów  
 Klasy <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaPlayer> i są używane do prezentowania zawartości audio lub wideo. Klasy te mogą być kontrolowane interaktywnie lub przez zegar. Te klasy mogą być używane w formancie Microsoft Windows Media Player 10 do odtwarzania multimediów. Klasa, której używasz, zależy od scenariusza.  
  
 <xref:System.Windows.Controls.MediaElement><xref:System.Windows.UIElement> jest, który jest obsługiwany przez [układ](../advanced/layout.md) i mogą być używane jako zawartość wielu formantów. Jest również użyteczny [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] w, jak również kod. <xref:System.Windows.Media.MediaPlayer>, z drugiej strony, <xref:System.Windows.Media.Drawing> jest przeznaczony dla obiektów i brakuje obsługi układu. Nośniki ładowane za <xref:System.Windows.Media.MediaPlayer> pomocą <xref:System.Windows.Media.VideoDrawing> a mogą być prezentowane tylko za pomocą lub poprzez bezpośrednią interakcję z . <xref:System.Windows.Media.DrawingContext> <xref:System.Windows.Media.MediaPlayer>nie można używać w języku XAML.  
  
 Aby uzyskać więcej informacji na temat obiektów rysunkowych i kontekstu rysunku, zobacz [Omówienie obiektów rysunkowych](drawing-objects-overview.md).  
  
> [!NOTE]
> Podczas dystrybucji multimediów z aplikacją nie można używać pliku multimedialnego jako zasobu projektu. W pliku projektu należy zamiast tego ustawić `Content` typ `CopyToOutputDirectory` nośnika i ustawić na `PreserveNewest` lub . `Always`  
  
<a name="mediaplaybackmodes"></a>
## <a name="media-playback-modes"></a>Tryby odtwarzania multimediów  
  
> [!NOTE]
> Zarówno <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaPlayer> i mają podobnych członków. Łącza w tej sekcji <xref:System.Windows.Controls.MediaElement> odnoszą się do członków klasy. O ile nie zaznaczono inaczej, elementy członkowskie połączone w <xref:System.Windows.Controls.MediaElement> klasie można również znaleźć w <xref:System.Windows.Media.MediaPlayer> klasie.  
  
 Aby zrozumieć odtwarzanie [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]multimediów w , wymagane jest zrozumienie różnych trybów, w których można odtwarzać multimedia. Oba <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaPlayer> i mogą być używane w dwóch różnych trybach multimedialnych, trybie niezależnym i trybie zegara. Tryb nośnika jest <xref:System.Windows.Controls.MediaElement.Clock%2A> określany przez właściwość. Gdy <xref:System.Windows.Controls.MediaElement.Clock%2A> `null`jest , obiekt multimedialny jest w trybie niezależnym. Gdy <xref:System.Windows.Controls.MediaElement.Clock%2A> jest null, obiekt multimedialny jest w trybie zegara. Domyślnie obiekty multimedialne są w trybie niezależnym.  
  
### <a name="independent-mode"></a>Tryb niezależny  
 W trybie niezależnym zawartość multimedialna napędza odtwarzanie multimediów. Tryb niezależny umożliwia następujące opcje:  
  
- <xref:System.Uri> Media mogą być bezpośrednio określone.  
  
- Odtwarzanie multimediów może być sterowane bezpośrednio.  
  
- Nośniki <xref:System.Windows.Controls.MediaElement.Position%2A> i <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> właściwości mogą być modyfikowane.  
  
 Nośnik jest ładowany <xref:System.Windows.Controls.MediaElement> przez ustawienie <xref:System.Windows.Controls.MediaElement.Source%2A> właściwości obiektu <xref:System.Windows.Media.MediaPlayer> lub wywołanie <xref:System.Windows.Media.MediaPlayer.Open%2A> metody obiektu.  
  
 Do sterowania odtwarzaniem multimediów w trybie niezależnym można użyć metod sterowania obiektu multimedialnego. Dostępne metody sterowania <xref:System.Windows.Controls.MediaElement.Play%2A> <xref:System.Windows.Controls.MediaElement.Pause%2A>to <xref:System.Windows.Controls.MediaElement.Close%2A>, <xref:System.Windows.Controls.MediaElement.Stop%2A>, i . Dla <xref:System.Windows.Controls.MediaElement>, interaktywna kontrola przy użyciu <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> tych <xref:System.Windows.Controls.MediaState.Manual>metod jest dostępna tylko wtedy, gdy jest ustawiona na . Metody te są niedostępne, gdy obiekt multimedialny jest w trybie zegara.  
  
 Zobacz [Sterowanie MediaElement (Odtwarzanie, Pauza, Zatrzymaj, Głośność i Szybkość)](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md) na przykład trybu niezależnego.  
  
### <a name="clock-mode"></a>Tryb zegara  
 W trybie <xref:System.Windows.Media.MediaTimeline> zegara odtwarzanie multimediów dysków. Tryb zegara ma następujące cechy:  
  
- Media <xref:System.Uri> są pośrednio ustawiane <xref:System.Windows.Media.MediaTimeline>przez .  
  
- Odtwarzanie multimediów może być kontrolowane przez zegar. Nie można użyć metod sterowania obiektu multimedialnego.  
  
- Nośnik jest ładowany przez ustawienie właściwości <xref:System.Windows.Media.MediaTimeline> obiektu, utworzenie zegara <xref:System.Windows.Media.MediaTimeline.Source%2A> z osi czasu i przypisanie zegara do obiektu multimedialnego. Nośnik jest również ładowany w ten sposób, <xref:System.Windows.Media.MediaTimeline> gdy wewnątrz <xref:System.Windows.Media.Animation.Storyboard> obiektu docelowego <xref:System.Windows.Controls.MediaElement>.  
  
 Aby sterować odtwarzaniem multimediów w trybie zegara, <xref:System.Windows.Media.Animation.ClockController> należy użyć metod sterowania. A <xref:System.Windows.Media.Animation.ClockController> uzyskuje się <xref:System.Windows.Media.Animation.ClockController> z <xref:System.Windows.Media.MediaClock>właściwości . Jeśli spróbujesz użyć metod kontroli <xref:System.Windows.Controls.MediaElement> albo <xref:System.Windows.Media.MediaPlayer> obiektu w trybie <xref:System.InvalidOperationException> zegara, zostanie rzucony.  
  
 Zobacz [Omówienie animacji, aby](animation-overview.md) uzyskać więcej informacji na temat zegarów i osi czasu.  
  
 Zobacz [Sterowanie MediaElement przy użyciu scenorysu](how-to-control-a-mediaelement-by-using-a-storyboard.md) na przykład trybu zegara.  
  
<a name="mediaelement"></a>
## <a name="mediaelement-class"></a>Klasa MediaElement  
 Dodawanie nośnika do aplikacji jest <xref:System.Windows.Controls.MediaElement> tak proste, jak dodanie formantu do [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] aplikacji i zapewnienie do <xref:System.Uri> nośnika, który chcesz dołączyć. Wszystkie typy nośników obsługiwane przez program Microsoft Windows [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Media Player 10 są obsługiwane w programie . W poniższym przykładzie przedstawiono proste użycie <xref:System.Windows.Controls.MediaElement> w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 W tym przykładzie nośnik jest odtwarzany automatycznie po załadowaniu. Po zakończeniu odtwarzania nośnika nośnik zostanie zamknięty, a wszystkie zasoby multimedialne zostaną uwolnione (w tym pamięć wideo). Jest to domyślne <xref:System.Windows.Controls.MediaElement> zachowanie obiektu i <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> jest <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> kontrolowane przez i właściwości.  
  
### <a name="controlling-a-mediaelement"></a>Kontrolowanie mediaelement  
 Właściwości <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> i <xref:System.Windows.Controls.MediaElement> kontrolować zachowanie, kiedy <xref:System.Windows.FrameworkElement.IsLoaded%2A> `true` jest `false`lub , odpowiednio. Właściwości <xref:System.Windows.Controls.MediaState> są ustawione tak, aby wpłynąć na zachowanie odtwarzania multimediów. Na przykład wartość <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Play> domyślna <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> to <xref:System.Windows.Controls.MediaState.Close>. Oznacza to, że <xref:System.Windows.Controls.MediaElement> po załadowaniu i zakończeniu prerolla, media zaczynają grać. Po zakończeniu odtwarzania nośnik zostanie zamknięty i wszystkie zasoby multimedialne są zwalniane.  
  
 Właściwości <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> i właściwości nie są jedynym sposobem kontrolowania odtwarzania multimediów. W trybie zegara zegar <xref:System.Windows.Controls.MediaElement> może kontrolować i interaktywne <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Manual>metody sterowania mają kontrolę, gdy jest . <xref:System.Windows.Controls.MediaElement>konkurencji poprzez ocenę następujących priorytetów.  
  
1. <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>. W miejscu, gdy nośnik jest rozładowywany. Gwarantuje to, że wszystkie zasoby multimedialne są <xref:System.Windows.Media.MediaClock> zwalniane domyślnie, nawet jeśli jest skojarzony z programem <xref:System.Windows.Controls.MediaElement>.  
  
2. <xref:System.Windows.Media.MediaClock>. W miejscu, gdy <xref:System.Windows.Controls.MediaElement.Clock%2A>nośnik ma . Jeśli nośnik zostanie rozładowany, <xref:System.Windows.Media.MediaClock> będzie obowiązywać <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Manual>tak długo, jak jest . Tryb zegara zawsze zastępuje załadowane <xref:System.Windows.Controls.MediaElement>zachowanie .  
  
3. <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>. W miejscu podczas ładowania nośnika.  
  
4. Interaktywne metody sterowania. W miejscu, gdy <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> jest <xref:System.Windows.Controls.MediaState.Manual>. Dostępne metody sterowania <xref:System.Windows.Controls.MediaElement.Play%2A> <xref:System.Windows.Controls.MediaElement.Pause%2A>to <xref:System.Windows.Controls.MediaElement.Close%2A>, <xref:System.Windows.Controls.MediaElement.Stop%2A>, i .  
  
### <a name="displaying-a-mediaelement"></a>Wyświetlanie mediaelement  
 Aby wyświetlić <xref:System.Windows.Controls.MediaElement> musi mieć zawartość do renderowania i będzie miał jego <xref:System.Windows.FrameworkElement.ActualWidth%2A> i <xref:System.Windows.FrameworkElement.ActualHeight%2A> właściwości ustawione na zero, dopóki zawartość jest ładowany. W przypadku zawartości tylko audio te właściwości są zawsze zerowe. W przypadku zawartości <xref:System.Windows.Controls.MediaElement.MediaOpened> wideo po podniesieniu zdarzenia <xref:System.Windows.FrameworkElement.ActualWidth%2A> i <xref:System.Windows.FrameworkElement.ActualHeight%2A> zgłosić rozmiar załadowanego nośnika. Oznacza to, że dopóki <xref:System.Windows.Controls.MediaElement> nośnik nie zostanie załadowany, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] nie <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> zajmie żadnego miejsca fizycznego w, chyba że lub właściwości są ustawione.  
  
 Ustawienie zarówno <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> właściwości, jak i właściwości spowoduje, że nośnik <xref:System.Windows.Controls.MediaElement>zostanie rozciągnięty, aby wypełnić obszar przewidziany dla pliku . Aby zachować oryginalny współczynnik proporcji nośnika, należy ustawić <xref:System.Windows.FrameworkElement.Width%2A> właściwość lub właściwość, <xref:System.Windows.FrameworkElement.Height%2A> ale nie obie. Ustawienie zarówno <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> właściwości, jak i właściwości spowoduje, że nośnik będzie obecny w rozmiarze elementu stałego, który może nie być pożądany.  
  
 Aby uniknąć posiadania elementu o [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] stałym rozmiarze, który może wstępnie roll nośnika. Odbywa się to <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> poprzez ustawienie <xref:System.Windows.Controls.MediaState.Play> <xref:System.Windows.Controls.MediaState.Pause>na jedną lub . W <xref:System.Windows.Controls.MediaState.Pause> stanie, media będą wstępnie i przedstawi pierwszą klatkę. W <xref:System.Windows.Controls.MediaState.Play> stanie, media będą preroll i rozpocząć grę.  
  
<a name="mediaplayer"></a>
## <a name="mediaplayer-class"></a>Klasa MediaPlayer  
 Podczas gdy <xref:System.Windows.Controls.MediaElement> klasa jest elementem <xref:System.Windows.Media.MediaPlayer> framework, klasa jest <xref:System.Windows.Media.Drawing> przeznaczona do użycia w obiektach. Obiekty rysunkowe są używane, gdy można poświęcić funkcje <xref:System.Windows.Freezable> na poziomie struktury, aby uzyskać korzyści wydajności lub gdy potrzebujesz funkcji. <xref:System.Windows.Media.MediaPlayer>umożliwia korzystanie z tych funkcji przy jednoczesnym dostarczaniu zawartości multimedialnej w aplikacjach. Like <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaPlayer> , może być używany w trybie <xref:System.Windows.Controls.MediaElement> niezależnym lub zegara, ale nie ma nieuciążonych i załadowanych stanów obiektu. Zmniejsza to złożoność sterowania odtwarzaniem pliku <xref:System.Windows.Media.MediaPlayer>.  
  
### <a name="controlling-mediaplayer"></a>Sterowanie MediaPlayerem  
 Ponieważ <xref:System.Windows.Media.MediaPlayer> jest bezstanowy, istnieją tylko dwa sposoby kontrolowania odtwarzania multimediów.  
  
1. Interaktywne metody sterowania. W miejscu, gdy`null` <xref:System.Windows.Media.MediaPlayer.Clock%2A> w trybie niezależnym (właściwość).  
  
2. <xref:System.Windows.Media.MediaClock>. W miejscu, gdy <xref:System.Windows.Media.MediaPlayer.Clock%2A>nośnik ma .  
  
### <a name="displaying-a-mediaplayer"></a>Wyświetlanie odtwarzacza MediaPlayer  
 Technicznie nie <xref:System.Windows.Media.MediaPlayer> można wyświetlić, ponieważ nie ma fizycznej reprezentacji. Jednak może służyć do prezentowania <xref:System.Windows.Media.Drawing> multimediów w klasie przy użyciu. <xref:System.Windows.Media.VideoDrawing> W poniższym przykładzie pokazano <xref:System.Windows.Media.VideoDrawing> użycie nośnika do wyświetlania.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Aby uzyskać więcej informacji na <xref:System.Windows.Media.Drawing> temat obiektów, [zobacz Omówienie obiektów rysunkowych.](drawing-objects-overview.md)  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.DrawingGroup>
- [Układ](../advanced/layout.md)
- [Tematy in jakże](audio-and-video-how-to-topics.md)
