---
title: "Przegląd Multimedia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multimedia [WPF]
- media [WPF]
ms.assetid: feb25b15-d741-4ac3-818f-1b19f63a3562
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 65553e18fc66825c9c0a991aba600b4b90d0d4c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="multimedia-overview"></a>Przegląd Multimedia
Funkcje multimediów w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] umożliwiają integrowanie aplikacji ulepszanie środowiska użytkownika audio i wideo. W tym temacie przedstawiono funkcje multimediów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 
  
<a name="mediaapi"></a>   
## <a name="media-api"></a>Interfejs API nośnika  
 <xref:System.Windows.Controls.MediaElement> i <xref:System.Windows.Media.MediaPlayer> klasy służą do prezentowania zawartości audio i wideo. Te klasy można kontrolować, interakcyjnego lub przez zegar. Te klasy można używać na [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 kontroli dla odtwarzania multimediów. Klasy, których używasz, zależy od scenariusza.  
  
 <xref:System.Windows.Controls.MediaElement>jest <xref:System.Windows.UIElement> który jest obsługiwany przez [układu](../../../../docs/framework/wpf/advanced/layout.md) i mogą być używane jako zawartość wielu formantów. Jest również w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a także kod. <xref:System.Windows.Media.MediaPlayer>, z drugiej strony, jest przeznaczona dla <xref:System.Windows.Media.Drawing> obiektów i nie ma układ pomocy technicznej. Nośnik załadowany przy użyciu <xref:System.Windows.Media.MediaPlayer> mogą być podane tylko przy użyciu <xref:System.Windows.Media.VideoDrawing> lub bezpośrednio interakcji z <xref:System.Windows.Media.DrawingContext>. <xref:System.Windows.Media.MediaPlayer>Nie można używać w języku XAML.  
  
 Aby uzyskać więcej informacji na temat rysowania obiektów i rysowanie kontekstu, zobacz [rysowania Przegląd obiektów](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).  
  
> [!NOTE]
>  Podczas dystrybucji nośnika z aplikacji, nie można użyć pliku multimedialnego jako zasób projektu. W pliku projektu, należy zamiast tego ustawić typ nośnika `Content` i ustaw `CopyToOutputDirectory` do `PreserveNewest` lub `Always`.  
  
<a name="mediaplaybackmodes"></a>   
## <a name="media-playback-modes"></a>Tryby odtwarzania multimediów  
  
> [!NOTE]
>  Zarówno <xref:System.Windows.Controls.MediaElement> i <xref:System.Windows.Media.MediaPlayer> ma podobnych elementów członkowskich. Łącza w tej sekcji dotyczą <xref:System.Windows.Controls.MediaElement> klasy elementów członkowskich. O ile nie zaznaczono inaczej, powiązany elementów członkowskich w <xref:System.Windows.Controls.MediaElement> klasy można znaleźć w <xref:System.Windows.Media.MediaPlayer> klasy.  
  
 Aby zrozumieć odtwarzanie multimediów w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], wymagana jest zrozumienie różnych trybach, w których można odtwarzać nośnika. Zarówno <xref:System.Windows.Controls.MediaElement> i <xref:System.Windows.Media.MediaPlayer> mogą być używane w dwóch trybach innego nośnika, niezależnie od trybu ani zegara. Tryb nośnika jest określany przez <xref:System.Windows.Controls.MediaElement.Clock%2A> właściwości. Gdy <xref:System.Windows.Controls.MediaElement.Clock%2A> jest `null`, obiekt nośnika jest w trybie niezależne. Gdy <xref:System.Windows.Controls.MediaElement.Clock%2A> jest różna od null, obiekt nośnika jest w trybie zegara. Domyślnie obiekty nośnika znajdują się w trybie niezależne.  
  
### <a name="independent-mode"></a>Niezależnie od trybu  
 W trybie niezależne dla zawartości multimedialnej dysków odtwarzania multimediów. Niezależnie od trybu umożliwia następujące opcje:  
  
-   Nośnika <xref:System.Uri> można określić bezpośrednio.  
  
-   Odtwarzanie multimediów można sterować bezpośrednio.  
  
-   Nośnika <xref:System.Windows.Controls.MediaElement.Position%2A> i <xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> można zmodyfikować właściwości.  
  
 Nośnik jest ładowany przez dowolnego z tych ustawień <xref:System.Windows.Controls.MediaElement> obiektu <xref:System.Windows.Controls.MediaElement.Source%2A> właściwości lub poprzez wywołanie <xref:System.Windows.Media.MediaPlayer> obiektu <xref:System.Windows.Media.MediaPlayer.Open%2A> metody.  
  
 Aby kontrolować odtwarzanie multimediów w trybie niezależne, obiekt nośnika kontroli metody mogą być używane. Dostępne metody kontroli <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>, i <xref:System.Windows.Controls.MediaElement.Stop%2A>. Aby uzyskać <xref:System.Windows.Controls.MediaElement>, sterowania interaktywnego przy użyciu tych metod jest dostępna tylko podczas <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> ma ustawioną wartość <xref:System.Windows.Controls.MediaState.Manual>. Te metody są niedostępne, gdy obiekt nośnika jest w trybie zegara.  
  
 Zobacz [kontroli MediaElement (Play, Wstrzymaj Stop, woluminów i szybkość)](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md) przykład niezależnie od trybu.  
  
### <a name="clock-mode"></a>Tryb zegara  
 W trybie zegara <xref:System.Windows.Media.MediaTimeline> odtwarzanie multimediów dysków. Tryb zegara ma następującą charakterystykę:  
  
-   Nośnika <xref:System.Uri> jest pośrednio ustawione za pośrednictwem <xref:System.Windows.Media.MediaTimeline>.  
  
-   Odtwarzanie multimediów mogą być kontrolowane przez zegar. Nie można użyć metody kontroli obiektu nośnika.  
  
-   Nośnik jest ładowany przez ustawienie <xref:System.Windows.Media.MediaTimeline> obiektu <xref:System.Windows.Media.MediaTimeline.Source%2A> właściwości, tworzenie zegara z osi czasu i przypisywanie zegar do obiektu nośnika. Nośnik jest również załadowany w ten sposób podczas <xref:System.Windows.Media.MediaTimeline> wewnątrz <xref:System.Windows.Media.Animation.Storyboard> cele <xref:System.Windows.Controls.MediaElement>.  
  
 Odtwarzanie multimediów formant w trybie zegara <xref:System.Windows.Media.Animation.ClockController> należy użyć metody kontroli. A <xref:System.Windows.Media.Animation.ClockController> są uzyskiwane z <xref:System.Windows.Media.Animation.ClockController> właściwość <xref:System.Windows.Media.MediaClock>. Jeśli spróbujesz użyć metod kontroli albo <xref:System.Windows.Controls.MediaElement> lub <xref:System.Windows.Media.MediaPlayer> obiektów w trybie zegara <xref:System.InvalidOperationException> zostanie wygenerowany.  
  
 Zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) uzyskać więcej informacji o zegary i osi czasu.  
  
 Zobacz [kontrolować MediaElement za pomocą scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-by-using-a-storyboard.md) przykład trybu zegara.  
  
<a name="mediaelement"></a>   
## <a name="mediaelement-class"></a>Element MediaElement — klasa  
 Dodawanie nośnika do aplikacji jest tak proste, jak dodawanie <xref:System.Windows.Controls.MediaElement> formant [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] aplikacji i zapewnianie <xref:System.Uri> na nośniku, które mają zostać uwzględnione. Obsługiwane przez wszystkie typy nośników [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] 10 są obsługiwane w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. W poniższym przykładzie przedstawiono użycie prostego <xref:System.Windows.Controls.MediaElement> w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[MediaElement_snip#SimpleMediaElementUsageWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaElement_snip/CSharp/SimpleUsage.xaml#simplemediaelementusagewholepage)]  
  
 W tym przykładzie odtwarzania multimediów automatycznie natychmiast po załadowaniu go. Po zakończeniu nośnika odtwarzanie nośnika zostanie zamknięte, a wszystkie zasoby nośnika są w wersji (włącznie z pamięci wideo). Jest to domyślne zachowanie <xref:System.Windows.Controls.MediaElement> obiektów i kontrolowane przez <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> i <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> właściwości.  
  
### <a name="controlling-a-mediaelement"></a>Kontrolowanie MediaElement  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> i <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> właściwości kontrolują zachowanie <xref:System.Windows.Controls.MediaElement> podczas <xref:System.Windows.FrameworkElement.IsLoaded%2A> jest `true` lub `false`odpowiednio. <xref:System.Windows.Controls.MediaState> Właściwości są ustawione na wpływają na zachowanie odtwarzania multimediów. Na przykład, wartość domyślna <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> jest <xref:System.Windows.Controls.MediaState.Play> i domyślnie <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> jest <xref:System.Windows.Controls.MediaState.Close>. Oznacza to, że natychmiast <xref:System.Windows.Controls.MediaElement> jest załadowany i zakończeniu preroll, nośnika rozpocznie się do odtwarzania. Po zakończeniu odtwarzania multimediów zostanie zamknięte, a wszystkie zasoby nośnika są wydawane.  
  
 <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> i <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> właściwości nie są jedynym sposobem na odtwarzanie multimediów formantu. W trybie zegara, można kontrolować zegar <xref:System.Windows.Controls.MediaElement> i metody sterowania interaktywnego ma decyduje o <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> jest <xref:System.Windows.Controls.MediaState.Manual>. <xref:System.Windows.Controls.MediaElement>obsługuje to konkurowanie o kontroli przez oceny następujący priorytetów.  
  
1.  <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A>., W miejscu, gdy nośnik zostanie zwolniona. Dzięki temu, czy wszystkie zasoby nośnika są wydawane domyślnie nawet wtedy, gdy <xref:System.Windows.Media.MediaClock> jest skojarzony z <xref:System.Windows.Controls.MediaElement>.  
  
2.  <xref:System.Windows.Media.MediaClock>., W miejscu po nośnika <xref:System.Windows.Controls.MediaElement.Clock%2A>. Jeśli nośnik jest zwolniony, <xref:System.Windows.Media.MediaClock> zacznie obowiązywać tak długo, jak <xref:System.Windows.Controls.MediaElement.UnloadedBehavior%2A> jest <xref:System.Windows.Controls.MediaState.Manual>. Tryb zegara zawsze zastępuje załadować zachowanie <xref:System.Windows.Controls.MediaElement>.  
  
3.  <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>., W miejscu po załadowaniu nośnika.  
  
4.  Metody sterowania interaktywnego. Umieść w przypadku <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> jest <xref:System.Windows.Controls.MediaState.Manual>. Dostępne metody kontroli <xref:System.Windows.Controls.MediaElement.Play%2A>, <xref:System.Windows.Controls.MediaElement.Pause%2A>, <xref:System.Windows.Controls.MediaElement.Close%2A>, i <xref:System.Windows.Controls.MediaElement.Stop%2A>.  
  
### <a name="displaying-a-mediaelement"></a>Wyświetlanie MediaElement  
 Aby wyświetlić <xref:System.Windows.Controls.MediaElement> musi mieć zawartość do renderowania i będzie mieć jego <xref:System.Windows.FrameworkElement.ActualWidth%2A> i <xref:System.Windows.FrameworkElement.ActualHeight%2A> właściwości ustawiono wartość zero do momentu załadowania zawartości. Tylko zawartość audio te właściwości są zawsze zero. Dla zawartości wideo, raz <xref:System.Windows.Controls.MediaElement.MediaOpened> zdarzenia <xref:System.Windows.FrameworkElement.ActualWidth%2A> i <xref:System.Windows.FrameworkElement.ActualHeight%2A> będzie raportu rozmiar załadowanego nośnika. Oznacza to, że do momentu załadowania nośnika, <xref:System.Windows.Controls.MediaElement> nie będzie zajmuje fizycznego miejsca w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] chyba że <xref:System.Windows.FrameworkElement.Width%2A> lub <xref:System.Windows.FrameworkElement.Height%2A> właściwości są ustawione.  
  
 Ustawienie obu <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> spowoduje, że nośnik rozciągają się, aby wypełnił obszar podany dla właściwości <xref:System.Windows.Controls.MediaElement>. Aby zachować oryginalny współczynnik proporcji nośnika albo <xref:System.Windows.FrameworkElement.Width%2A> lub <xref:System.Windows.FrameworkElement.Height%2A> właściwość powinna mieć zestawu, ale nie oba. Ustawienie obu <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości spowoduje, że nośnik do prezentowania rozmiar stały element, który nie może być pożądane.  
  
 Aby uniknąć element o stałym rozmiarze, który [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] można buforowania multimediów. Odbywa się przez ustawienie <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A> albo <xref:System.Windows.Controls.MediaState.Play> lub <xref:System.Windows.Controls.MediaState.Pause>. W <xref:System.Windows.Controls.MediaState.Pause> stan nośnika zostanie buforowania i wyświetli pierwszej ramki. W <xref:System.Windows.Controls.MediaState.Play> stanu nośnik buforowania i odtworzony.  
  
<a name="mediaplayer"></a>   
## <a name="mediaplayer-class"></a>Klasa MediaPlayer  
 W przypadku gdy <xref:System.Windows.Controls.MediaElement> klasa jest elementem framework <xref:System.Windows.Media.MediaPlayer> klasy jest przeznaczona do użycia w <xref:System.Windows.Media.Drawing> obiektów. Rysowanie obiekty są używane podczas pochodzących z poziomu funkcji framework do korzyści wydajności lub należy <xref:System.Windows.Freezable> funkcji. <xref:System.Windows.Media.MediaPlayer>Umożliwia korzystanie z tych funkcji zapewniają zawartości multimedialnej w aplikacji. Podobnie jak <xref:System.Windows.Controls.MediaElement>, <xref:System.Windows.Media.MediaPlayer> mogą być używane w niezależnych lub nie zegara tryb, ale nie ma <xref:System.Windows.Controls.MediaElement> zwalnianie i załadować stanów obiektów. Pozwala to zmniejszyć złożoność kontroli odtwarzania <xref:System.Windows.Media.MediaPlayer>.  
  
### <a name="controlling-mediaplayer"></a>Kontrolowanie MediaPlayer  
 Ponieważ <xref:System.Windows.Media.MediaPlayer> jest bezstanowych, istnieją tylko dwa sposoby sterowania odtwarzania multimediów.  
  
1.  Metody sterowania interaktywnego. W miejscu w trybie niezależne (`null` <xref:System.Windows.Media.MediaPlayer.Clock%2A> właściwości).  
  
2.  <xref:System.Windows.Media.MediaClock>., W miejscu po nośnika <xref:System.Windows.Media.MediaPlayer.Clock%2A>.  
  
### <a name="displaying-a-mediaplayer"></a>Wyświetlanie MediaPlayer  
 Z technicznego punktu widzenia <xref:System.Windows.Media.MediaPlayer> nie można wyświetlić, ponieważ go nie posiada fizycznych. Jednak może służyć do prezentowania nośnika w <xref:System.Windows.Media.Drawing> przy użyciu <xref:System.Windows.Media.VideoDrawing> klasy. W poniższym przykładzie pokazano użycie <xref:System.Windows.Media.VideoDrawing> do wyświetlenia nośnika.  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 Zobacz [Przegląd obiektów rysunku](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md) uzyskać więcej informacji o <xref:System.Windows.Media.Drawing> obiektów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.DrawingGroup>  
 [Układ](../../../../docs/framework/wpf/advanced/layout.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)
