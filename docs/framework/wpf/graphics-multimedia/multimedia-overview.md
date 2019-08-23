---
title: Przegląd Multimedia
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
ms.openlocfilehash: 44059fe96a0deeda18f0abd9079100b55be98e77
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929620"
---
# <a name="multimedia-overview"></a>Przegląd Multimedia
Funkcje multimedialne w programie [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] umożliwiają integrację audio i wideo z aplikacjami w celu udoskonalenia środowiska użytkownika. W tym temacie przedstawiono funkcje multimedialne programu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="mediaapi"></a>   
## <a name="media-api"></a>Interfejs API multimediów  
 Klasy <xref:System.Windows.Controls.MediaElement> i<xref:System.Windows.Media.MediaPlayer> służą do prezentowania zawartości audio lub wideo. Te klasy mogą być sterowane interaktywnie lub przez zegar. Te klasy mogą być używane na [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] potrzeby odtwarzania multimediów w 10 kontrolkach. Której klasy używasz, zależy od scenariusza.  
  
 <xref:System.Windows.Controls.MediaElement>jest obsługiwana przez układ i może być używana jako zawartość wielu kontrolek. [](../advanced/layout.md) <xref:System.Windows.UIElement> Jest również użyteczny zarówno [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] w jak i w kodzie. <xref:System.Windows.Media.MediaPlayer>z drugiej strony program jest przeznaczony dla <xref:System.Windows.Media.Drawing> obiektów i nie obsługuje układu. Nośnik załadowany przy użyciu <xref:System.Windows.Media.MediaPlayer> elementu może być prezentowany tylko <xref:System.Windows.Media.VideoDrawing> przy użyciu elementu lub przez <xref:System.Windows.Media.DrawingContext>bezpośrednie współpracującie z. <xref:System.Windows.Media.MediaPlayer>nie można używać w języku XAML.  
  
 Aby uzyskać więcej informacji na temat rysowania obiektów i kontekstu rysowania, zobacz [Omówienie obiektów rysowania](drawing-objects-overview.md).  
  
> [!NOTE]
> Podczas dystrybucji multimediów za pomocą aplikacji nie można używać pliku multimedialnego jako zasobu projektu. W pliku projektu należy zamiast tego ustawić `Content` typ nośnika na i ustawić `CopyToOutputDirectory` na `PreserveNewest` lub `Always`.  
  
<a name="mediaplaybackmodes"></a>   
## <a name="media-playback-modes"></a>Tryby odtwarzania multimediów  
  
> [!NOTE]
> Obie <xref:System.Windows.Controls.MediaElement> i<xref:System.Windows.Media.MediaPlayer> mają podobne elementy członkowskie. Linki w tej sekcji odnoszą się do <xref:System.Windows.Controls.MediaElement> elementów członkowskich klasy. O ile nie zaznaczono inaczej, elementy członkowskie <xref:System.Windows.Controls.MediaElement> połączone z w klasie można również znaleźć <xref:System.Windows.Media.MediaPlayer> w klasie.  
  
 Aby zrozumieć odtwarzanie multimediów w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]programie, należy zapoznać się z różnymi trybami, w których można odtwarzać multimedia. Oba <xref:System.Windows.Controls.MediaElement> i<xref:System.Windows.Media.MediaPlayer> mogą być używane w dwóch różnych trybach nośnika, Tryb niezależny i tryb zegara. Tryb multimedialny jest określany przez <xref:System.Windows.Controls.MediaElement.Clock%2A> właściwość. Gdy <xref:System.Windows.Controls.MediaElement.Clock%2A> jest`null`, obiekt multimedialny jest w trybie niezależnym. Gdy wartość <xref:System.Windows.Controls.MediaElement.Clock%2A> jest inna niż null, obiekt multimedialny jest w trybie zegara. Domyślnie obiekty multimedialne są w trybie niezależnym.  
  
### <a name="independent-mode"></a>Tryb niezależny  
 W trybie niezależnym zawartość multimedialna jest odtwarzana na nośnikach. Tryb niezależny zapewnia następujące opcje:  
  
- <xref:System.Uri> Można określić bezpośrednio multimedia.  
  
- Odtwarzanie multimediów można kontrolować bezpośrednio.  
  
- <xref:System.Windows.Controls.MediaElement.Position%2A> Multimedia i <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> właściwości można modyfikować.  
  
 Nośnik <xref:System.Windows.Controls.MediaElement> jest ładowany przez ustawienie <xref:System.Windows.Controls.MediaElement.Source%2A> <xref:System.Windows.Media.MediaPlayer> właściwości obiektu lub wywołanie <xref:System.Windows.Media.MediaPlayer.Open%2A> metody obiektu.  
  
 Aby sterować odtwarzaniem multimediów w trybie niezależnym, można użyć metod kontroli obiektu multimedialnego. <xref:System.Windows.Controls.MediaElement.Play%2A>Dostępne metody kontroli to <xref:System.Windows.Controls.MediaElement.Pause%2A> <xref:System.Windows.Controls.MediaElement.Close%2A>,,, i. <xref:System.Windows.Controls.MediaElement.Stop%2A> W <xref:System.Windows.Controls.MediaElement>przypadku programu interaktywna kontrola przy użyciu tych metod jest dostępna <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> tylko wtedy, <xref:System.Windows.Controls.MediaState.Manual>gdy jest ustawiona na. Te metody są niedostępne, gdy obiekt multimedialny jest w trybie zegara.  
  
 Zobacz [Control MediaElement (Play, Pause, stop, Volume i Speed)](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md) , aby zapoznać się z przykładowym trybem niezależnym.  
  
### <a name="clock-mode"></a>Tryb zegara  
 W trybie zegara dysk jest <xref:System.Windows.Media.MediaTimeline> odtwarzany. Tryb zegara ma następujące cechy:  
  
- Nośnik jest pośrednio ustawiony za pomocą <xref:System.Windows.Media.MediaTimeline>. <xref:System.Uri>  
  
- Odtwarzanie multimediów może być kontrolowane przez zegar. Nie można używać metod sterowania obiektu multimedialnego.  
  
- Nośnik jest ładowany przez ustawienie <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaTimeline.Source%2A> właściwości obiektu, utworzenie zegara z osi czasu i przypisanie zegara do obiektu nośnika. Nośnik jest również ładowany w ten sposób, <xref:System.Windows.Media.MediaTimeline> gdy element <xref:System.Windows.Media.Animation.Storyboard> docelowy a <xref:System.Windows.Controls.MediaElement>.  
  
 Aby można było sterować odtwarzaniem multimediów w trybie <xref:System.Windows.Media.Animation.ClockController> zegara, należy użyć metod kontroli. A <xref:System.Windows.Media.Animation.ClockController> jest uzyskiwany <xref:System.Windows.Media.Animation.ClockController> z właściwości <xref:System.Windows.Media.MediaClock>. Jeśli spróbujesz użyć metod <xref:System.Windows.Controls.MediaElement> kontrolnych obiektu lub <xref:System.Windows.Media.MediaPlayer> <xref:System.InvalidOperationException> w trybie zegara, zostanie zgłoszony.  
  
 Zobacz [Omówienie animacji](animation-overview.md) , aby uzyskać więcej informacji na temat zegarów i osi czasu.  
  
 Zobacz [kontrolowanie elementu MediaElement przy użyciu scenorysu](how-to-control-a-mediaelement-by-using-a-storyboard.md) na przykład trybu zegara.  
  
<a name="mediaelement"></a>   
## <a name="mediaelement-class"></a>MediaElement — Klasa  
 Dodawanie multimediów do aplikacji jest tak proste jak dodanie <xref:System.Windows.Controls.MediaElement> kontrolki [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] do aplikacji i udostępnienie <xref:System.Uri> nośnika, który ma zostać uwzględniony. Wszystkie typy nośników obsługiwane przez [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] program 10 są obsługiwane [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]w programie. Poniższy przykład pokazuje proste użycie <xref:System.Windows.Controls.MediaElement> w. [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 W tym przykładzie nośnik jest odtwarzany automatycznie zaraz po jego załadowaniu. Po zakończeniu odtwarzania nośnika nośnik zostanie zamknięty i wszystkie zasoby multimedialne są zwalniane (w tym pamięci wideo). Jest to domyślne zachowanie <xref:System.Windows.Controls.MediaElement> obiektu i jest kontrolowane <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> przez właściwości i <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> .  
  
### <a name="controlling-a-mediaelement"></a>Kontrolowanie elementu MediaElement  
 <xref:System.Windows.FrameworkElement.IsLoaded%2A> `true` `false`Właściwości <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> i <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> kontrolujązachowaniew<xref:System.Windows.Controls.MediaElement> przypadku, gdy jest lub, odpowiednio. <xref:System.Windows.Controls.MediaState> Właściwości są ustawione na wpływ na zachowanie odtwarzania multimediów. Na przykład wartość <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> domyślna to <xref:System.Windows.Controls.MediaState.Play> i wartość domyślna <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Close>to. Oznacza to, że zaraz <xref:System.Windows.Controls.MediaElement> po załadowaniu i przewróceniu, nośnik zacznie być odtwarzany. Po zakończeniu odtwarzania nośnik zostanie zamknięty i zostaną wydane wszystkie zasoby multimedialne.  
  
 Właściwości <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> i<xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> nie są jedynym sposobem sterowania odtwarzaniem multimediów. W trybie zegara zegar może kontrolować <xref:System.Windows.Controls.MediaElement> , a interaktywne metody sterowania mają kontrolę, <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> gdy wartość jest <xref:System.Windows.Controls.MediaState.Manual>. <xref:System.Windows.Controls.MediaElement>obsługuje takie konkursy na potrzeby kontroli, oceniając poniższe priorytety.  
  
1. <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>. W miejscu, gdy nośnik zostanie zwolniony. Gwarantuje to, że wszystkie zasoby multimedialne są domyślnie udostępniane, nawet jeśli <xref:System.Windows.Media.MediaClock> jest skojarzony <xref:System.Windows.Controls.MediaElement>z.  
  
2. <xref:System.Windows.Media.MediaClock>. W miejscu, <xref:System.Windows.Controls.MediaElement.Clock%2A>gdy nośnik ma. Jeśli nośnik zostanie zwolniony, zacznie obowiązywać tak <xref:System.Windows.Media.MediaClock> długo, <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> jak to jest <xref:System.Windows.Controls.MediaState.Manual>. Tryb zegara zawsze zastępuje załadowane zachowanie <xref:System.Windows.Controls.MediaElement>.  
  
3. <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>. W miejscu podczas ładowania nośnika.  
  
4. Metody interaktywnej kontroli. W miejscu <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>. <xref:System.Windows.Controls.MediaState.Manual> <xref:System.Windows.Controls.MediaElement.Play%2A>Dostępne metody kontroli to <xref:System.Windows.Controls.MediaElement.Pause%2A> <xref:System.Windows.Controls.MediaElement.Close%2A>,,, i. <xref:System.Windows.Controls.MediaElement.Stop%2A>  
  
### <a name="displaying-a-mediaelement"></a>Wyświetlanie elementu MediaElement  
 Aby wyświetlić element <xref:System.Windows.Controls.MediaElement> , musi on mieć zawartość do renderowania i będzie <xref:System.Windows.FrameworkElement.ActualWidth%2A> miał właściwość i <xref:System.Windows.FrameworkElement.ActualHeight%2A> właściwości ustawione na zero do momentu załadowania zawartości. W przypadku zawartości tylko audio, te właściwości są zawsze zerowe. Dla zawartości wideo, gdy <xref:System.Windows.Controls.MediaElement.MediaOpened> zdarzenie zostało <xref:System.Windows.FrameworkElement.ActualWidth%2A> wywołane i <xref:System.Windows.FrameworkElement.ActualHeight%2A> zgłosi rozmiar załadowanego nośnika. Oznacza to, że do momentu załadowania <xref:System.Windows.Controls.MediaElement> nośnika nie zajmie żadnych fizycznych miejsc w, [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] chyba że <xref:System.Windows.FrameworkElement.Width%2A> właściwości lub <xref:System.Windows.FrameworkElement.Height%2A> są ustawione.  
  
 Ustawienie właściwości <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Controls.MediaElement>i spowoduje rozciągnięcie nośnika w celu wypełnienia obszaru podanego dla. <xref:System.Windows.FrameworkElement.Width%2A> Aby zachować pierwotny współczynnik proporcji nośnika, <xref:System.Windows.FrameworkElement.Width%2A> należy ustawić właściwość lub <xref:System.Windows.FrameworkElement.Height%2A> , ale nie oba. Ustawienie właściwości <xref:System.Windows.FrameworkElement.Height%2A> i spowoduje, że nośnik będzie obecny w stałym rozmiarze elementu, który może nie być pożądany. <xref:System.Windows.FrameworkElement.Width%2A>  
  
 Aby uniknąć posiadania elementu o stałym rozmiarze, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] który może wycofać nośnik. Można to zrobić, ustawiając <xref:System.Windows.Controls.MediaState.Pause> wartośćnalub.<xref:System.Windows.Controls.MediaState.Play> <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> <xref:System.Windows.Controls.MediaState.Pause> W stanie nośnik zostanie przeddany i zaprezentuje pierwszą klatkę. <xref:System.Windows.Controls.MediaState.Play> W stanie nośnik zostanie przeddany i rozpocznie się odtwarzanie.  
  
<a name="mediaplayer"></a>   
## <a name="mediaplayer-class"></a>Klasa MediaPlayer  
 Gdzie Klasa jest elementem Framework <xref:System.Windows.Media.MediaPlayer> , Klasa jest przeznaczona do użycia w <xref:System.Windows.Media.Drawing> obiektach. <xref:System.Windows.Controls.MediaElement> Obiekty rysunkowe są używane w przypadku, gdy można wymusić funkcje poziomu platformy w celu uzyskania korzyści <xref:System.Windows.Freezable> z wydajności lub korzystania z funkcji. <xref:System.Windows.Media.MediaPlayer>umożliwia korzystanie z tych funkcji podczas udostępniania zawartości multimedialnej w aplikacjach. Na przykład, może być używany w trybie niezależnym lub zegarowym, <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaPlayer> ale nie ma Stanów zwolnionych i załadowanych obiektu. <xref:System.Windows.Controls.MediaElement> Zmniejsza to złożoność <xref:System.Windows.Media.MediaPlayer>formantu odtwarzania.  
  
### <a name="controlling-mediaplayer"></a>Kontrolowanie MediaPlayer  
 Ponieważ <xref:System.Windows.Media.MediaPlayer> jest bezstanowa, istnieją tylko dwa sposoby sterowania odtwarzaniem multimediów.  
  
1. Metody interaktywnej kontroli. W miejscu w trybie niezależnym`null` (<xref:System.Windows.Media.MediaPlayer.Clock%2A> Właściwość).  
  
2. <xref:System.Windows.Media.MediaClock>. W miejscu, <xref:System.Windows.Media.MediaPlayer.Clock%2A>gdy nośnik ma.  
  
### <a name="displaying-a-mediaplayer"></a>Wyświetlanie MediaPlayer  
 Technicznie <xref:System.Windows.Media.MediaPlayer> nie można wyświetlić, ponieważ nie ma fizycznej reprezentacji. Można go jednak użyć do prezentowania nośnika <xref:System.Windows.Media.Drawing> <xref:System.Windows.Media.VideoDrawing> przy użyciu klasy. Poniższy przykład ilustruje użycie elementu <xref:System.Windows.Media.VideoDrawing> do wyświetlania nośnika.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Zobacz [Omówienie obiektów rysowania](drawing-objects-overview.md) , aby uzyskać więcej informacji <xref:System.Windows.Media.Drawing> o obiektach.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.DrawingGroup>
- [Układ](../advanced/layout.md)
- [Tematy z instrukcjami](audio-and-video-how-to-topics.md)
