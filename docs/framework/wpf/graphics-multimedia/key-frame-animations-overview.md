---
title: "Przegląd Animacja kluczowych klatek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], key-frame
- key frames [WPF], about key-frame animations
- multiple animation target values [WPF]
ms.assetid: 10028f97-bb63-41fc-b8ad-663dac7ea203
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8c4f4179087679ff891c705cf16693fc69c808d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="key-frame-animations-overview"></a>Przegląd Animacja kluczowych klatek
W tym temacie przedstawiono klucza ramki animacji. Klucz poklatkowych umożliwiają animować przy użyciu więcej niż dwóch wartości docelowych i kontrolować metodę interpolacji animacji.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć, w tym omówieniu, należy się zapoznać z [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] animacji i osi czasu. Wprowadzenie do animacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Pomaga również należy zapoznać się z lub do/przez animacji. Aby uzyskać więcej informacji zobacz Omówienie animacje From/To/By.  
  
<a name="whatisakeyframeanimation"></a>   
## <a name="what-is-a-key-frame-animation"></a>Co to jest animacji klucza ramki?  
 From lub do/przez, takich jak wartość właściwości target animuje animacji, animacji ramki klucza. Tworzy ona przejścia między jego wartości docelowej w jego <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Jednakże podczas From lub do/przez animację tworzy przejścia między dwiema wartościami, pojedynczy animacji ramki klucza można utworzyć przejścia między dowolną liczbę wartości docelowych. W odróżnieniu od From lub do/przez animacji, klatek kluczowych animacji nie ma żadnych From, aby lub za pomocą właściwości, z którego mają zostać ustawione wartości docelowej. Opisano wartości docelowych animację ramki klucza przy użyciu obiektów klatek kluczowych (dlatego termin, "klucz ramki animacji"). Aby określić wartości docelowe animacji, tworzenia obiektów klatki i dodaj je do animacji <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> kolekcji. Po uruchomieniu animacji go przechodzi między ramek, które można określić.  
  
 Oprócz obsługi wielu wartości docelowych, niektóre metody ramki klucza nawet obsługują wiele metod interpolacji. Metoda interpolacji animacji Określa, jak jego przejścia z jedną wartość do następnego. Istnieją trzy typy potrzeby interpolacji: odrębny liniowej i splined.  
  
 Aby animować z animacją klucza ramki, zakończeniu następujące kroki.  
  
-   Deklarowanie animacji i określ jej <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, tak jak z lub do/przez animacji.  
  
-   Dla każdej wartości docelowej, należy utworzyć klatki odpowiedniego typu, ustaw jej wartość i <xref:System.Windows.Media.Animation.KeyTime>i dodaj go do animacji <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> kolekcji.  
  
-   Kojarzenie animacji z właściwością, tak jak z From lub do/przez animacji. Aby uzyskać więcej informacji dotyczących stosowania animacji do właściwości przy użyciu scenorysu, zobacz [omówienie Scenorys](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> do animowania <xref:System.Windows.Shapes.Rectangle> element do czterech różnych lokalizacji.  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
 From lub do/przez, takich jak animacji, animacji ramki klucz może odnosić się do właściwości, za pomocą <xref:System.Windows.Media.Animation.Storyboard> znaczników i kodu lub za pomocą <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> w kodzie. Można także użyć animacji ramki klucza do utworzenia <xref:System.Windows.Media.Animation.AnimationClock> i zastosować je do co najmniej jednej właściwości. Aby uzyskać więcej informacji na temat różnych metod do zastosowania animacji, zobacz [— Przegląd właściwości animacji techniki](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
<a name="animation_types"></a>   
## <a name="key-frame-animation-types"></a>Typy klucza ramki animacji  
 Ponieważ animacje Generowanie wartości właściwości, istnieją typy innej animacji dla różnych typach właściwości. Do animowania właściwości, która przyjmuje <xref:System.Double> (takie jak element <xref:System.Windows.FrameworkElement.Width%2A> właściwości), użyj animacji tworzącego <xref:System.Double> wartości. Aby animować właściwości, która przyjmuje <xref:System.Windows.Point>, użyj animacji tworzącego <xref:System.Windows.Point> wartości i tak dalej.  
  
 Klasy klucza ramki animacji należą do <xref:System.Windows.Media.Animation> przestrzeni nazw i być zgodne z następującą konwencją nazewnictwa:  
  
 *\<Typ >*`AnimationUsingKeyFrames`  
  
 Gdzie  *\<typu >* jest typ wartości, które animuje klasy.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]udostępnia następujące klasy klucza ramki animacji.  
  
|Typ właściwości|Odpowiadającą klasę z lub do/przez animacji|Obsługiwane metody interpolacji|  
|-------------------|------------------------------------------------|-------------------------------------|  
|<xref:System.Boolean>|<xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>|Dyskretne|  
|<xref:System.Byte>|<xref:System.Windows.Media.Animation.ByteAnimationUsingKeyFrames>|Odrębny, liniowego, Splined|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|Odrębny, liniowego, Splined|  
|<xref:System.Decimal>|<xref:System.Windows.Media.Animation.DecimalAnimationUsingKeyFrames>|Odrębny, liniowego, Splined|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|Odrębny, liniowego, Splined|  
|<xref:System.Int16>|<xref:System.Windows.Media.Animation.Int16AnimationUsingKeyFrames>|Odrębny, liniowego, Splined|  
|<xref:System.Int32>|<xref:System.Windows.Media.Animation.Int32AnimationUsingKeyFrames>|Odrębny, liniowego, Splined|  
|<xref:System.Int64>|<xref:System.Windows.Media.Animation.Int64AnimationUsingKeyFrames>|Odrębny, liniowego, Splined|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames>|Dyskretne|  
|<xref:System.Object>|<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>|Dyskretne|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|Odrębny, liniowego, Splined|  
|<xref:System.Windows.Media.Media3D.Quaternion>|<xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames>|Odrębny, liniowego, Splined|  
|<xref:System.Windows.Rect>|<xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>|Odrębny, liniowego, Splined|  
|<xref:System.Windows.Media.Media3D.Rotation3D>|<xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames>|Odrębny, liniowego, Splined|  
|<xref:System.Single>|<xref:System.Windows.Media.Animation.SingleAnimationUsingKeyFrames>|Odrębny, liniowego, Splined|  
|<xref:System.String>|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|Dyskretne|  
|<xref:System.Windows.Size>|<xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>|Odrębny, liniowego, Splined|  
|<xref:System.Windows.Thickness>|<xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames>|Odrębny, liniowego, Splined|  
|<xref:System.Windows.Media.Media3D.Vector3D>|<xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames>|Odrębny, liniowego, Splined|  
|<xref:System.Windows.Vector>|<xref:System.Windows.Media.Animation.VectorAnimationUsingKeyFrames>|Odrębny, liniowego, Splined|  
  
<a name="animation_target_values"></a>   
## <a name="target-values-key-frames-and-key-times"></a>Wartości (klatek kluczowych) docelowych i czasy klucza  
 Tak samo, jak są różnego rodzaju klucza poklatkowych dla różnych typach właściwości animacji, są także różne typy obiektów klatki: jeden dla każdego typu wartości animowany i metodę interpolacji obsługiwane. Typy klatki być zgodne z następującą konwencją nazewnictwa:  
  
 *\<InterpolationMethod >\<typu >*`KeyFrame`  
  
 Gdzie  *\<InterpolationMethod >* jest metodę interpolacji używa klatek kluczowych i  *\<typu >* jest typ wartości, które animuje klasy. Animację klucza ramki, która obsługuje wszystkie trzy interpolacji metody ma trzy typy klatki, które są dostępne. Na przykład można użyć trzech typów klatki z <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>: <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>, <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>, i <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>. (Metody interpolacji opisano szczegółowo w dalszej części artykułu.)  
  
 Głównym celem klatek kluczowych jest określenie <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> i <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>. Każdy typ klatki udostępnia te dwie właściwości.  
  
-   <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> Właściwość określa wartości docelowej dla tej ramki klucza.  
  
-   <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> Właściwość określa, kiedy (w animacji <xref:System.Windows.Media.Animation.Timeline.Duration%2A>) klatek kluczowych <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> zostanie osiągnięty.  
  
 Po rozpoczęciu klatek kluczowych animacji iteruje po jego klatek kluczowych w kolejności zdefiniowanej przez ich <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> właściwości.  
  
-   Jeśli w czasie 0 jest bez klucza ramki, animacji tworzy przejście między bieżącą wartość właściwości target i <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> pierwszej ramki klucza; w przeciwnym razie animacji wyjściowy wartość staje się wartością pierwszej ramki klucza.  
  
-   Animacja tworzy przejście między <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> klatek kluczowych pierwszego i drugiego przy użyciu metody interpolacji określony przez drugi klatki. Przejście rozpoczyna się od pierwszej ramki klucza <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> i kończy się po drugim klatek kluczowych <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> zostanie osiągnięty.  
  
-   Animacja będzie się powtarzać, tworzenie przejścia między każdym klatek kluczowych kolejnych i jego poprzedniej ramki klucza.  
  
-   Na koniec przejścia animacji na wartość klucza ramki z największą czas klucza jest równa lub mniejsza niż animacji <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.  
  
 Jeśli animacji <xref:System.Windows.Media.Animation.Timeline.Duration%2A> jest <xref:System.Windows.Duration.Automatic%2A> lub jego <xref:System.Windows.Media.Animation.Timeline.Duration%2A> jest taki sam, jak czas ostatniego klatek kluczowych animacji zakończenia. W przeciwnym razie, jeśli animacji <xref:System.Windows.Duration> jest większa niż wartość klucza czasu ostatniego klatek kluczowych blokad animacji wartość klatki, dopóki osiągnie koniec jego <xref:System.Windows.Duration>. Podobnie jak wszystkie animacje używa animacji ramki klucza jego <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> właściwości w celu określenia, czy przechowuje go końcowej po dotarciu serwerów do zakończenia okresu aktywacji. Aby uzyskać więcej informacji, zobacz [omówienie zachowania chronometrażu](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md).  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> obiekt zdefiniowany w poprzednim przykładzie, aby zademonstrować sposób <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> i <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> pracy właściwości.  
  
-   Pierwszy klatki natychmiast ustawia wartość wyjściowa animacji na 0.  
  
-   Drugi klatki animuje z zakresu od 0 do 350. Rozpoczyna się po zakończeniu pierwszego klatki (czas = 0 sekund) i odtworzenie przez 2 sekundy, koniec czas = 0:0:2.  
  
-   Trzeci klatki animuje od 350 do 50. Rozpoczyna się po zakończeniu drugiego klatki (w czasie = 2 sekundy) i odtworzenie 5 sekund, koniec czas = 0:0:7.  
  
-   Czwarty klatki animuje od 50 do 200. Rozpoczyna się po zakończeniu trzeci klatki (w czasie = 7 sekund) i odtworzenie 1 sekundy, koniec czas = 0:0:8.  
  
-   Ponieważ <xref:System.Windows.Media.Animation.Timeline.Duration%2A> właściwości animacji został ustawiony na 10 sekund, animacji zawiera jego końcowej dla dwóch sekund przed zakończeniem w czasie = 0:0:10.  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
<a name="interpolationmethods"></a>   
## <a name="interpolation-methods"></a>Metody interpolacji  
 Poprzednich sekcjach wspomniano, że niektóre klucza poklatkowych obsługują wiele metod interpolacji. Animacja interpolacji opisano, jak animacji przejścia między wartościami w czasie jego trwania. Po wybraniu typu klatki używających animacji, można zdefiniować metodę interpolacji dla tego segmentu klatki. Istnieją trzy różne typy metody interpolacji: liniowego, odrębny i splined.  
  
### <a name="linear-interpolation"></a>Interpolacji liniowej  
 Z interpolacji liniowej realizowany animacji przy stałym trwania segmentu. Na przykład, jeśli segment klatki przejścia z zakresu od 0 do 10 przez dany okres 5 sekund, animacji dane wyjściowe obejmują następujące wartości w określonym razy:  
  
|Godzina|Wartość wyjściowa|  
|----------|------------------|  
|0|0|  
|1|2|  
|2|4|  
|3|6|  
|4|8|  
|4.25|8.5|  
|4.5|9|  
|5|10|  
  
### <a name="discrete-interpolation"></a>Odrębny interpolacji  
 Z interpolacji odrębny funkcja animacji przechodzi z jedną wartość do następnego bez interpolacji. Jeśli segment klatki przejścia z zakresu od 0 do 10 przez dany okres 5 sekund, animacji dane wyjściowe obejmują następujące wartości w określonym razy:  
  
|Godzina|Wartość wyjściowa|  
|----------|------------------|  
|0|0|  
|1|0|  
|2|0|  
|3|0|  
|4|0|  
|4.25|0|  
|4.5|0|  
|5|10|  
  
 Zwróć uwagę, jak animacji nie zmienia jej wartość wyjściowa aż do zakończenia bardzo trwania segmentu.  
  
 Splined interpolacji jest bardziej złożony. Opisano w następnej sekcji.  
  
<a name="anim_spline"></a>   
### <a name="splined-interpolation"></a>Splined interpolacji  
 Splined interpolacji może służyć do osiągnięcia, realistyczne więcej efektów chronometrażu. Animacje są często używane do naśladującej efekty występujące w świecie rzeczywistym, deweloperzy mogą muszą drobne kontroli przyspieszenia i prędkości obiektów i zamknij manipulowania segmentów chronometrażu. Ramek kluczowych krzywej składanej umożliwiają animować z interpolacji splined. Z innych klatek kluczowych określ <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> i <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>. Z krzywymi składanymi klatek kluczowych, należy także określić <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A>. W poniższym przykładzie przedstawiono składanej jednej ramki klucza dla <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>. Powiadomienie <xref:System.Windows.Media.Animation.KeySpline> właściwość; która jest, co sprawia, że klatek kluczowych krzywej składanej różne od innych typów klatek kluczowych.  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 Trzeciego krzywej Beziera jest zdefiniowana przez dwa punkty kontrolne, punkt początkowy i punkt końcowy. <xref:System.Windows.Media.Animation.KeySpline> Właściwość klatek kluczowych krzywej składanej określa punkt kontrolny krzywej Beziera, rozszerzający z (0,0) (1,1). Pierwszy punkt kontrolny określa współczynnik pierwszej połowy krzywej Beziera krzywej, a drugi punkt kontrolny określa współczynnik drugiej połowie segmentu krzywej Beziera krzywej. Wynikowa krzywej opisuje szybkość zmian dla tej ramki kluczowych krzywej składanej. Większe krzywej szybsze klatki zmienia jego wartości. Jak krzywej pobiera płaska, klatek kluczowych wolniej zmienia jego wartości.  
  
 Można na przykład <xref:System.Windows.Media.Animation.KeySpline> do symulowania trajektorii fizycznych, takich jak objętych limitu górnego lub odbijania im dostęp lub zastosować inne "do jej obsługi ułatwiają w" i "do jej obsługi ułatwiają" efekty animacji ruchu. Dla efektów interakcji użytkownika, jak zanikanie tło lub formantu przycisku odbicia mogą być stosowane splined interpolacji przyspieszenia lub zmniejsz częstotliwość zmian dla animacji w określony sposób.  
  
 W poniższym przykładzie <xref:System.Windows.Media.Animation.KeySpline> 1,0 0,1, który tworzy następujące krzywą Beziera.  
  
 ![Krzywej Beziera](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyspline-0-1-1-0.png "graphicsmm_keyspline_0_1_1_0")  
Kluczowych krzywej składanej z punktów kontrolnych (0.0, 1.0) i (1.0, 0.0)  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 Ta ramka klucza animuje szybko po jego rozpoczyna się, spowalnia, a następnie przyspiesza ponownie przed zakończeniem jej.  
  
 W poniższym przykładzie <xref:System.Windows.Media.Animation.KeySpline> z 0.75,1.0 0.5,0.25, który tworzy następujące krzywą Beziera.  
  
 ![Krzywej Beziera](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyspline-025-050-075-10.png "graphicsmm_keyspline_025_050_075_10")  
Kluczowych krzywej składanej za pomocą formantu punktów (0,25, 0,5) i (0,75, 1.0)  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexampleinline3)]  
  
 Ponieważ łuku krzywej Beziera zmienia niewielkie, to klatki animuje prawie stałą szybkością; go spowalnia nieco kierunku jej końcu.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> do animowania pozycja prostokąta. Ponieważ <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> używa <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> obiekty przejścia między każdą wartość klatki używa splined interpolacji.  
  
 [!code-xaml[keyframes_ovw_snippet#SplinedInterpolationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#splinedinterpolationexample)]  
  
 Splined interpolacji może być trudne do zrozumienia; eksperymentowanie z różnymi ustawieniami może pomóc. [Klucza krzywej składanej animacji próbki](http://go.microsoft.com/fwlink/?LinkID=160011) umożliwia zmienianie wartości klucza krzywej składanej i sprawdzić działanie ma na animacji.  
  
<a name="combininginterpolationmethods"></a>   
### <a name="combining-interpolation-methods"></a>Łączenie metody interpolacji  
 Za pomocą klucza ramek interpolacji różnych typów w jednego klatek kluczowych animacji. Po dwóch klatek kluczowych animacji z różnych potrzeby interpolacji wykonaj siebie nawzajem, metodę interpolacji drugiej ramki klucza służy do tworzenia przejścia z pierwszej wartości przez drugą.  
  
 W poniższym przykładzie <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> utworzeniu tego używa interpolacji liniowej, splined i dyskretnych.  
  
 [!code-xaml[keyframes_ovw_snippet#ComboInterpolationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#combointerpolationexample)]  
  
<a name="keytimes"></a>   
## <a name="more-about-duration-and-key-times"></a>Więcej informacji na temat czas i czas klucza  
 Podobnie jak inne animacje mają klucz poklatkowych <xref:System.Windows.Duration> właściwości. Oprócz określenia animacji <xref:System.Windows.Duration>, należy określić, jaka część tego czasu trwania znajduje się do każdego klatki. Można to zrobić, opisujący <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> dla każdego klatek kluczowych animacji. Każdy klatki <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> Określa, kiedy kończy się tym klatki.  
  
 <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> Właściwość nie określa, jak długo odgrywa czas klucza. Ilość czasu, który pełni klatek kluczowych zależy od zakończenia klatek kluczowych, kiedy zakończył się poprzedniej ramki klucza i czas trwania animacji. Czasy klucza można określić jako wartość czasu, wartość procentowa lub specjalnych wartości <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> lub <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>.  
  
 Na poniższej liście opisano różne sposoby określenie czasu klucza.  
  
### <a name="timespan-values"></a>Wartości TimeSpan  
 Możesz użyć <xref:System.TimeSpan> wartości określające <xref:System.Windows.Media.Animation.KeyTime>. Wartość powinna być większa lub równa 0 i mniejsza niż czas trwania animacji. W poniższym przykładzie przedstawiono animacji o czasie trwania 10 sekund i cztery klatek kluczowych, których czas klucza są określone jako wartości czasu.  
  
-   Pierwszy klatki animuje z podstawową wartość 100 przez pierwsze 3 sekundy kończy w momencie = 0:0:03.  
  
-   Drugi klatki animuje od 100 do 200. Rozpoczyna się po zakończeniu pierwszego klatki (w czasie = 3 sekundy) i odtworzenie 5 sekund, koniec czas = 0:0:8.  
  
-   Trzeci klatki animuje od 200 do 500. Rozpoczyna się po zakończeniu drugiego klatki (czas = 8 sekund) i odtworzenie 1 sekundy, koniec czas = 0:0:9.  
  
-   Czwarty klatki animuje z 500 do 600. Rozpoczyna się po zakończeniu trzeci klatki (w czasie = 9 sekund) i odtworzenie 1 sekundy, koniec czas = 0:0:10.  
  
 [!code-xaml[keyframes_ovw_snippet#TimeSpanKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#timespankeytimeexample)]  
  
### <a name="percentage-values"></a>Wartości procentowe  
 Wartość procentowa Określa, że klatek kluczowych kończy się na określoną wartość procentową animacji <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], określ wartość procentową jako numer, a następnie `%` symbolu. W kodzie, użyj <xref:System.Windows.Media.Animation.KeyTime.FromPercent%2A> — metoda i przekaż go <xref:System.Double> wskazujący procent. Wartość musi być większa lub równa 0 i mniejsza niż 100 procent. W poniższym przykładzie przedstawiono animacji o czasie trwania 10 sekund i cztery klatek kluczowych, których czas klucza są określone jako wartości procentowe.  
  
-   Pierwszy klatki animuje z podstawową wartość 100 przez pierwsze 3 sekundy kończy w momencie = 0:0:3.  
  
-   Drugi klatki animuje od 100 do 200. Rozpoczyna się po zakończeniu pierwszego klatki (w czasie = 3 sekundy) i odtworzenie 5 sekund, koniec czas = 0:0:8 (0,8 * 10 = 8).  
  
-   Trzeci klatki animuje od 200 do 500. Rozpoczyna się po zakończeniu drugiego klatki (czas = 8 sekund) i odtworzenie 1 sekundy, koniec czas = 0:0:9 (0,9 * 10 = 9).  
  
-   Czwarty klatki animuje z 500 do 600. Rozpoczyna się po zakończeniu trzeci klatki (w czasie = 9 sekund) i odtworzenie 1 sekundy, koniec czas = 0:0:10 (1 * 10 = 10).  
  
 [!code-xaml[keyframes_ovw_snippet#PercentageKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#percentagekeytimeexample)]  
  
### <a name="special-value-uniform"></a>Specjalna wartość, Uniform  
 Użyj <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> chronometrażu, jeśli chcesz, aby każdy klatki się zająć tyle samo czasu.  
  
 A <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> czas klucza dzieli dostępny czas jednakowo przez liczbę klatek kluczowych, aby określić czas zakończenia każdej klatki. W poniższym przykładzie przedstawiono animacji o czasie trwania 10 sekund i cztery klatek kluczowych, którego klucz czasu są określane jako <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>.  
  
-   Pierwszy klatki animuje z podstawową wartość 100 za pośrednictwem pierwszego sekundach 2,5 kończy w momencie = 0:0:2.5.  
  
-   Drugi klatki animuje od 100 do 200. Rozpoczyna się po zakończeniu pierwszego klatki (w czasie = 2,5 sekund) i odtworzenie około 2,5 sekund, koniec czas = 0:0:5.  
  
-   Trzeci klatki animuje od 200 do 500. Rozpoczyna się po zakończeniu drugiego klatki (w czasie = 5 sekund) i odtworzenie 2,5 sekund, koniec czas = 0:0:7.5.  
  
-   Czwarty klatki animuje z 500 do 600. Rozpoczyna się po zakończeniu drugiego klatki (w czasie = 7.5 sekund) i odtworzenie 2,5 sekund, koniec czas = 0:0:1.  
  
 [!code-xaml[keyframes_ovw_snippet#UniformKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#uniformkeytimeexample)]  
  
### <a name="special-value-paced"></a>Specjalna wartość użytkownika  
 Użyj <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> chronometrażu można animować przy stałym.  
  
 A <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> czas klucza przydziela dostępny czas w zależności od długości każdego z klatek kluczowych, aby określić czas trwania każdej ramce.  Zapewni to zachowanie prędkość lub tempie animacji pozostaje stała.  W poniższym przykładzie przedstawiono animacji o czasie trwania 10 sekund i trzy klatek kluczowych, którego klucz czasu są określane jako <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>.  
  
 [!code-xaml[keyframes_ovw_snippet#PacedKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#pacedkeytimeexample)]  
  
 Należy zauważyć, że w przypadku klucza czas ostatniego klatek kluczowych <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> lub <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>, czas jego rozpoznać klucza zostanie ustawiona na 100 procent. Jeśli pierwszy klatek kluczowych animacji klatkę jest realizowanych, czas jego rozpoznać klucza będzie równa 0. (Kolekcja klatki zawiera tylko jednego klatek kluczowych i jest realizowanych klatki, jego rozpoznać klucza będzie ustawić wartość do 100 procent.)  
  
 Różne klatek kluczowych w obrębie jednego klatek kluczowych animacji może używać typów inny czas klucza.  
  
<a name="combiningkeytimes"></a>   
## <a name="combining-key-times-out-of-order-key-frames"></a>Łączenie razy klucza, klucz poza kolejnością ramki  
 Można użyć klatek kluczowych z różnymi <xref:System.Windows.Media.Animation.KeyTime> typów animacji tej samej wartości. I jest zalecane, Dodaj klatek kluczowych w kolejności, w którym należy odtworzyć, nie jest konieczne. Synchronizację system jest w stanie rozpoznawania klatek kluczowych poza kolejnością. Klatek kluczowych z nieprawidłową razy klucza są ignorowane.  
  
 Poniższa lista zawiera opis procedury za pomocą której czas klucza jest rozwiązany klatek kluczowych animacji ramki klucza.  
  
1.  Rozwiąż <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> wartości.  
  
2.  Określić, że animacja *całkowity czas interpolacji*, łączny czas trwania animacji ramki klucza do ukończenia iteracji do przodu.  
  
    1.  Jeśli animacji <xref:System.Windows.Media.Animation.Timeline.Duration%2A> nie jest <xref:System.Windows.Duration.Automatic%2A> lub <xref:System.Windows.Duration.Forever%2A>, czas interpolacji całkowita jest wartością animacji <xref:System.Windows.Media.Animation.Timeline.Duration%2A> właściwości.  
  
    2.  W przeciwnym razie interpolacji całkowity czas jest największy <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> wartość między jego klatek kluczowych, jeśli takie istnieją.  
  
    3.  W przeciwnym razie wartość całkowita interpolacji czasu wynosi 1 s.  
  
3.  Użyj wartości czasu całkowita interpolacji do rozpoznania <xref:System.Windows.Media.Animation.KeyTimeType.Percent> <xref:System.Windows.Media.Animation.KeyTime> wartości.  
  
4.  Rozwiąż ostatniego klatki, jeśli jeszcze nie zostało rozwiązane w poprzednich krokach. Jeśli <xref:System.Windows.Media.Animation.KeyTime> ostatniego jest klatki <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> lub <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>, czas jego rozwiązane będzie równa interpolacji całkowity czas.  
  
     Jeśli <xref:System.Windows.Media.Animation.KeyTime> pierwszej ramki klucza jest <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> i to animacji ma więcej niż na klatek kluczowych Rozwiąż jego <xref:System.Windows.Media.Animation.KeyTime> do zera; wartości, jeśli istnieje tylko jednego klatek kluczowych i jego <xref:System.Windows.Media.Animation.KeyTime> wartość jest <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>, jest ono rozwiązane do całkowitej interpolacji godzina, zgodnie z opisem w poprzednim kroku.  
  
5.  Rozwiąż pozostałych <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> wartości: każdego otrzymują one równa część dostępny czas.  W trakcie tego procesu nierozpoznane <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> wartości tymczasowo są traktowane jako <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> wartości i get tymczasowej rozpoznać czasu.  
  
6.  Rozwiąż <xref:System.Windows.Media.Animation.KeyTime> wartości klatek kluczowych z nieokreśloną razy klucza przy użyciu klucza ramek zadeklarowany najbliżej nich, które zostały rozwiązane <xref:System.Windows.Media.Animation.KeyTime> wartości.  
  
7.  Rozwiąż pozostałych <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> wartości. <xref:System.Windows.Media.Animation.KeyTime.Paced%2A><xref:System.Windows.Media.Animation.KeyTime> użyj <xref:System.Windows.Media.Animation.KeyTime> wartości sąsiadujących klucza ramek, aby określić czas rozwiązane.  Celem jest zapewnienie stałej wokół klatek kluczowych rozpoznać czasu prędkość animacji.  
  
8.  Sortowanie klatek kluczowych w kolejności rozpoznać czasu (klucz podstawowy) i kolejność deklaracji (klucz pomocniczy), tj., użyj stabilna sortowania oparte na rozwiązaniu klatki <xref:System.Windows.Media.Animation.KeyTime> wartości.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Animation.KeyTime>  
 <xref:System.Windows.Media.Animation.KeySpline>  
 <xref:System.Windows.Media.Animation.Timeline>  
 [Przykładowe animacji klucza krzywymi składanymi](http://go.microsoft.com/fwlink/?LinkID=160011)  
 [Klatek kluczowych animacji próbki](http://go.microsoft.com/fwlink/?LinkID=160012)  
 [Animacja — omówienie](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Scenorys — omówienie](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Klucz ramki — tematy porad](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)  
 [Omówienie zachowania chronometrażu](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)
