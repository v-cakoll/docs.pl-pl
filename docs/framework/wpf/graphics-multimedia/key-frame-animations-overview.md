---
title: Przegląd Animacja kluczowych klatek
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], key-frame
- key frames [WPF], about key-frame animations
- multiple animation target values [WPF]
ms.assetid: 10028f97-bb63-41fc-b8ad-663dac7ea203
ms.openlocfilehash: be815ca522cf18ea2403ea7af5549ceaf922854e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186681"
---
# <a name="key-frame-animations-overview"></a>Przegląd Animacja kluczowych klatek
W tym temacie przedstawiono animacje klatek kluczowych. Animacje klatek kluczowych umożliwiają animowanie przy użyciu więcej niż dwóch wartości docelowych i sterowanie metodą interpolacji animacji.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć ten przegląd, należy [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zapoznać się z animacji i osi czasu. Aby zapoznać się z wprowadzeniem do animacji, zobacz [Omówienie animacji](animation-overview.md). Pomaga również zapoznać się z animacjami Od/Do/Przez. Aby uzyskać więcej informacji, zobacz Przegląd animacji od/do/według.  
  
<a name="whatisakeyframeanimation"></a>
## <a name="what-is-a-key-frame-animation"></a>Co to jest animacja klatki kluczowej?  
 Podobnie jak animacja Od/Do/Przez animacja klatki kluczowej animuje wartość właściwości docelowej. Tworzy przejście między wartościami docelowymi nad jego <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Jednak podczas gdy animacja Od/Do/Przez tworzy przejście między dwiema wartościami, pojedyncza animacja klatki kluczowej może tworzyć przejścia między dowolną liczbą wartości docelowych. W przeciwieństwie do animacji Od/Do/Przez animacji klatki kluczowej nie ma od, do lub przez właściwości, z którymi można ustawić swoje wartości docelowe. Wartości docelowe animacji klatki kluczowej są opisane przy użyciu obiektów klatek kluczowych (stąd termin "animacja klatki kluczowej"). Aby określić wartości docelowe animacji, należy utworzyć obiekty klatek <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> kluczowych i dodać je do kolekcji animacji. Po uruchomieniu animacji przechodzi między określonymi klatkami.  
  
 Oprócz obsługi wielu wartości docelowych niektóre metody klatki kluczowej obsługują nawet wiele metod interpolacji. Metoda interpolacji animacji definiuje sposób przechodzenia z jednej wartości do następnej. Istnieją trzy typy interpolacji: dyskretny, liniowy i splined.  
  
 Aby animować animację klatki kluczowej, wykonaj następujące kroki.  
  
- Zadeklaruj <xref:System.Windows.Media.Animation.Timeline.Duration%2A>animację i określ jej , tak jak w przypadku animacji from/to/by.  
  
- Dla każdej wartości docelowej należy utworzyć klatkę kluczową <xref:System.Windows.Media.Animation.KeyTime>odpowiedniego typu, ustawić jej <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> wartość i , i dodać ją do kolekcji animacji.  
  
- Skojarz animację z właściwością, tak jak w animacji Od/Do/Przez. Aby uzyskać więcej informacji na temat stosowania animacji do właściwości przy użyciu scenorysu, zobacz [Omówienie scenoki](storyboards-overview.md).  
  
 W poniższym przykładzie <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> użyto <xref:System.Windows.Shapes.Rectangle> a do animowania elementu do czterech różnych lokalizacji.  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
 Podobnie jak od/do/przez animacji, animacji klatki kluczowej można <xref:System.Windows.Media.Animation.Storyboard> zastosować do właściwości przy <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> użyciu w znaczników i kodu lub przy użyciu metody w kodzie. Można również użyć animacji klatki <xref:System.Windows.Media.Animation.AnimationClock> kluczowej, aby utworzyć i zastosować ją do jednej lub więcej właściwości. Aby uzyskać więcej informacji na temat różnych metod stosowania animacji, zobacz [Omówienie technik animacji właściwości](property-animation-techniques-overview.md).  
  
<a name="animation_types"></a>
## <a name="key-frame-animation-types"></a>Typy animacji klatki kluczowej  
 Ponieważ animacje generują wartości właściwości, istnieją różne typy animacji dla różnych typów właściwości. Aby animować właściwość, która ma <xref:System.Double> (na przykład <xref:System.Windows.FrameworkElement.Width%2A> właściwości elementu), <xref:System.Double> należy użyć animacji, która tworzy wartości. Aby animować właściwość, która przyjmuje <xref:System.Windows.Point>program <xref:System.Windows.Point> , należy użyć animacji, która tworzy wartości i tak dalej.  
  
 Klasy animacji klatki kluczowej należą do obszaru <xref:System.Windows.Media.Animation> nazw i są zgodne z następującą konwencją nazewnictwa:  
  
 * \<>typu*`AnimationUsingKeyFrames`  
  
 Gdzie * \<Type>* jest typem wartości, który animuje klasę.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawiera następujące klasy animacji klatki kluczowej.  
  
|Typ właściwości|Odpowiadająca klasa animacji od/do/według animacji|Obsługiwane metody interpolacji|  
|-------------------|------------------------------------------------|-------------------------------------|  
|<xref:System.Boolean>|<xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>|Dyskretnych|  
|<xref:System.Byte>|<xref:System.Windows.Media.Animation.ByteAnimationUsingKeyFrames>|Dyskretny, Liniowy, Splined|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|Dyskretny, Liniowy, Splined|  
|<xref:System.Decimal>|<xref:System.Windows.Media.Animation.DecimalAnimationUsingKeyFrames>|Dyskretny, Liniowy, Splined|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|Dyskretny, Liniowy, Splined|  
|<xref:System.Int16>|<xref:System.Windows.Media.Animation.Int16AnimationUsingKeyFrames>|Dyskretny, Liniowy, Splined|  
|<xref:System.Int32>|<xref:System.Windows.Media.Animation.Int32AnimationUsingKeyFrames>|Dyskretny, Liniowy, Splined|  
|<xref:System.Int64>|<xref:System.Windows.Media.Animation.Int64AnimationUsingKeyFrames>|Dyskretny, Liniowy, Splined|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames>|Dyskretnych|  
|<xref:System.Object>|<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>|Dyskretnych|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|Dyskretny, Liniowy, Splined|  
|<xref:System.Windows.Media.Media3D.Quaternion>|<xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames>|Dyskretny, Liniowy, Splined|  
|<xref:System.Windows.Rect>|<xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>|Dyskretny, Liniowy, Splined|  
|<xref:System.Windows.Media.Media3D.Rotation3D>|<xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames>|Dyskretny, Liniowy, Splined|  
|<xref:System.Single>|<xref:System.Windows.Media.Animation.SingleAnimationUsingKeyFrames>|Dyskretny, Liniowy, Splined|  
|<xref:System.String>|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|Dyskretnych|  
|<xref:System.Windows.Size>|<xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>|Dyskretny, Liniowy, Splined|  
|<xref:System.Windows.Thickness>|<xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames>|Dyskretny, Liniowy, Splined|  
|<xref:System.Windows.Media.Media3D.Vector3D>|<xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames>|Dyskretny, Liniowy, Splined|  
|<xref:System.Windows.Vector>|<xref:System.Windows.Media.Animation.VectorAnimationUsingKeyFrames>|Dyskretny, Liniowy, Splined|  
  
<a name="animation_target_values"></a>
## <a name="target-values-key-frames-and-key-times"></a>Wartości docelowe (klatki kluczowe) i czasy kluczy  
 Podobnie jak istnieją różne typy animacji klatek kluczowych do animowania różnych typów właściwości, istnieją również różne typy obiektów klatki kluczowej: po jednym dla każdego typu animowanej wartości i obsługiwanej metody interpolacji. Typy klatek kluczowych są zgodne z następującą konwencją nazewnictwa:  
  
 *>\<typu>>interpolacji \<*`KeyFrame`  
  
 Gdzie * \<InterpolationMethod>* jest metodą interpolacji, której używa klatka kluczowa, a * \<type>* jest typem wartości, którą klasy animuje. Animacja klatki kluczowej, która obsługuje wszystkie trzy metody interpolacji, będzie miała trzy typy klatek kluczowych, których można użyć. Na przykład można użyć trzech typów <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>klatek <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>kluczowych <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>z : <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>, , i . (Metody interpolacji są szczegółowo opisane w dalszej części).  
  
 Głównym celem klatki kluczowej jest <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> określenie <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>a i a . Każdy typ klatki kluczowej zapewnia te dwie właściwości.  
  
- Właściwość <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> określa wartość docelową dla tej klatki kluczowej.  
  
- Właściwość <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> określa, kiedy (w <xref:System.Windows.Media.Animation.Timeline.Duration%2A>animacji) zostanie <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> osiągnięta klatka kluczowa.  
  
 Po rozpoczęciu animacji klatki kluczowej iteruje za pośrednictwem <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> jego klatek kluczowych w kolejności zdefiniowanej przez ich właściwości.  
  
- Jeśli nie ma żadnej klatki kluczowej w czasie 0, animacja tworzy <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> przejście między bieżącą wartością właściwości docelowej a pierwszą klatką kluczową; w przeciwnym razie wartość wyjściowa animacji staje się wartością pierwszej klatki kluczowej.  
  
- Animacja tworzy przejście <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> między pierwszą i drugą klatką kluczową przy użyciu metody interpolacji określonej przez drugą klatkę kluczową. Przejście rozpoczyna się od pierwszej klatki kluczowej <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> i kończy <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> się po osiągnięciu drugiej klatki kluczowej.  
  
- Animacja jest kontynuowana, tworząc przejścia między każdą kolejną klatką kluczową a jej poprzednią klatką kluczową.  
  
- Na koniec animacja przechodzi do wartości klatki kluczowej z największym czasem klucza, który <xref:System.Windows.Media.Animation.Timeline.Duration%2A>jest równy lub mniejszy niż animacja .  
  
 Jeśli animacja <xref:System.Windows.Media.Animation.Timeline.Duration%2A> jest <xref:System.Windows.Duration.Automatic%2A> lub <xref:System.Windows.Media.Animation.Timeline.Duration%2A> jej jest równa czas ostatniej klatki kluczowej, animacja kończy. W przeciwnym razie, <xref:System.Windows.Duration> jeśli animacja jest większa niż czas klucza ostatniej klatki kluczowej, animacja <xref:System.Windows.Duration>przechowuje wartość klatki kluczowej, dopóki nie osiągnie końca jego . Podobnie jak wszystkie animacje animacji klatki kluczowej używa jego <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> właściwości, aby ustalić, czy posiada wartość końcową, gdy osiągnie koniec aktywnego okresu. Aby uzyskać więcej informacji, zobacz [Omówienie zachowań chronometrażu](timing-behaviors-overview.md).  
  
 W poniższym przykładzie użyto obiektu zdefiniowanego <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> w <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> poprzednim przykładzie, aby zademonstrować, jak działają właściwości i.  
  
- Pierwsza klatka kluczowa natychmiast ustawia wartość wyjściową animacji na 0.  
  
- Druga klatka kluczowa animuje od 0 do 350. Rozpoczyna się po zakończeniu pierwszej klatki kluczowej (w czasie = 0 sekund) i jest odtwarzany przez 2 sekundy, kończąc na czasie = 0:0:2.  
  
- Trzecia klatka kluczowa ożywia od 350 do 50. Rozpoczyna się po zakończeniu drugiej klatki kluczowej (w czasie = 2 sekundy) i jest odtwarzany przez 5 sekund, kończąc na czasie = 0:0:7.  
  
- Czwarta klatka kluczowa ożywia od 50 do 200. Rozpoczyna się po zakończeniu trzeciej klatki kluczowej (w czasie = 7 sekund) i jest odtwarzany przez 1 sekundę, kończąc na czasie = 0:0:8.  
  
- Ponieważ <xref:System.Windows.Media.Animation.Timeline.Duration%2A> właściwość animacji została ustawiona na 10 sekund, animacja przechowuje swoją wartość końcową przez dwie sekundy przed zakończeniem w czasie = 0:0:10.  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
<a name="interpolationmethods"></a>
## <a name="interpolation-methods"></a>Metody interpolacji  
 W poprzednich sekcjach wspomniano, że niektóre animacje klatek kluczowych obsługują wiele metod interpolacji. Interpolacja animacji opisuje, jak animacja przechodzi między wartościami w czasie jej trwania. Wybierając typ klatki kluczowej używany z animacją, można zdefiniować metodę interpolacji dla tego segmentu klatki kluczowej. Istnieją trzy różne typy metod interpolacji: liniowy, dyskretny i splined.  
  
### <a name="linear-interpolation"></a>Interpolacja liniowa  
 Dzięki interpolacji liniowej animacja rozwija się ze stałą szybkością czasu trwania segmentu. Na przykład jeśli segment klatki kluczowej przechodzi od 0 do 10 w czasie trwania 5 sekund, animacja będzie wyprowadzać następujące wartości w określonych godzinach:  
  
|Time|Wartość wyjściowa|  
|----------|------------------|  
|0|0|  
|1|2|  
|2|4|  
|3|6|  
|4|8|  
|4.25|8.5|  
|4.5|9|  
|5|10|  
  
### <a name="discrete-interpolation"></a>Interpolacja dyskretna  
 W dyskretnej interpolacji funkcja animacji przeskakuje z jednej wartości do następnej bez interpolacji. Jeśli segment klatki kluczowej zostanie przesunie się z 0 do 10 w czasie trwania 5 sekund, animacja wysunie następujące wartości w określonych godzinach:  
  
|Time|Wartość wyjściowa|  
|----------|------------------|  
|0|0|  
|1|0|  
|2|0|  
|3|0|  
|4|0|  
|4.25|0|  
|4.5|0|  
|5|10|  
  
 Zwróć uwagę, jak animacja nie zmienia jego wartość wyjściowa do samego końca czasu trwania segmentu.  
  
 Interpolacja splined jest bardziej złożona. Jest to opisane w następnej sekcji.  
  
<a name="anim_spline"></a>
### <a name="splined-interpolation"></a>Interpolacja splined  
 Interpolacja splined może być wykorzystana do osiągnięcia bardziej realistycznych efektów czasowych. Ponieważ animacje są tak często używane do naśladowania efektów, które występują w świecie rzeczywistym, deweloperzy mogą wymagać precyzyjnej kontroli przyspieszenia i spowolnienia obiektów i ścisłej manipulacji segmentów chronometrażu. Klatki kluczowe splajnu umożliwiają animowanie z interpolacją splined. W przypadku innych klatek <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> kluczowych <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>należy określić przycisk i . Za pomocą klatki kluczowej splajnu można również określić . <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> W poniższym przykładzie przedstawiono pojedynczą klatkę kluczową splajnu dla pliku <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>. Zwróć <xref:System.Windows.Media.Animation.KeySpline> uwagę na właściwość; to właśnie sprawia, że klatka kluczowa splajnu różni się od innych typów klatek kluczowych.  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 Sześcienna krzywa Beziera jest definiowana przez punkt początkowy, punkt końcowy i dwa punkty kontrolne. Właściwość <xref:System.Windows.Media.Animation.KeySpline> klatki kluczowej splajnu definiuje dwa punkty kontrolne krzywej Beziera, która rozciąga się od (0,0) do (1,1). Pierwszy punkt kontrolny steruje współczynnikiem krzywej pierwszej połowy krzywej Beziera, a drugi punkt kontrolny steruje współczynnikiem krzywej drugiej połowy segmentu Beziera. Wynikowa krzywa opisuje szybkość zmiany dla tej klatki kluczowej splajnu. Im bardziej stroma krzywa, tym szybciej klatka kluczowa zmienia swoje wartości. Gdy krzywa staje się bardziej płaska, klatka kluczowa zmienia swoje wartości wolniej.  
  
 Możesz użyć <xref:System.Windows.Media.Animation.KeySpline> do symulacji fizycznych trajektorii, takich jak spadająca woda lub odbijające się kulki, lub zastosować inne efekty "łatwość" i "złagodzić" do animacji ruchu. W przypadku efektów interakcji użytkownika, takich jak zanikanie tła lub odbicie przycisku sterującego, można zastosować interpolację splined, aby przyspieszyć lub spowolnić tempo zmian animacji w określony sposób.  
  
 Poniższy przykład określa <xref:System.Windows.Media.Animation.KeySpline> 0,1 1,0, który tworzy następującą krzywą Beziera.  
  
 ![Krzywa Beziera](./media/graphicsmm-keyspline-0-1-1-0.png "graphicsmm_keyspline_0_1_1_0")  
Kluczowy splajn z punktami kontrolnymi (0,0, 1,0) i (1,0, 0,0)  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 Ta klatka kluczowa animuje się szybko po jej rozpoczęciu, spowalnia, a następnie przyspiesza ponownie przed jej zakończeniem.  
  
 Poniższy przykład określa <xref:System.Windows.Media.Animation.KeySpline> 0,5,0,25 0,75,1,0, który tworzy następującą krzywą Beziera.  
  
 ![Krzywa Beziera](./media/graphicsmm-keyspline-025-050-075-10.png "graphicsmm_keyspline_025_050_075_10")  
Kluczowy splajn z punktami kontrolnymi (0,25, 0,5) i (0,75, 1,0)  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexampleinline3)]  
  
 Ponieważ krzywizna krzywej Beziera zmienia się bardzo mało, ta klatka kluczowa animuje się z niemal stałą szybkością; spowalnia nieco w kierunku samego końca.  
  
 W poniższym przykładzie użyto a <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> do animowania położenia prostokąta. Ponieważ <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> używa <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> obiektów, przejście między każdą wartością klatki kluczowej używa splined interpolacji.  
  
 [!code-xaml[keyframes_ovw_snippet#SplinedInterpolationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#splinedinterpolationexample)]  
  
 Interpolacja splined może być trudne do zrozumienia; eksperymentowanie z różnymi ustawieniami może pomóc. [Przykład animacji splajnu klucza](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/KeySplineAnimations) umożliwia zmianę wartości splajnu klucza i wyświetlenie wyniku animacji.  
  
<a name="combininginterpolationmethods"></a>
### <a name="combining-interpolation-methods"></a>Łączenie metod interpolacji  
 W animacji pojedynczej klatki kluczowej można używać klatek kluczowych z różnymi typami interpolacji. Gdy dwie animacje klatek kluczowych z różnymi interpolacjami podążają za sobą, metoda interpolacji drugiej klatki kluczowej jest używana do tworzenia przejścia od pierwszej wartości do drugiej.  
  
 W poniższym przykładzie <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> tworzony jest, który używa interpolacji liniowej, splined i dyskretnej.  
  
 [!code-xaml[keyframes_ovw_snippet#ComboInterpolationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#combointerpolationexample)]  
  
<a name="keytimes"></a>
## <a name="more-about-duration-and-key-times"></a>Więcej informacji o czas trwania i czasy kluczy  
 Podobnie jak inne animacje, animacje <xref:System.Windows.Duration> klatek kluczowych mają właściwość. Oprócz określenia animacji <xref:System.Windows.Duration>, należy określić, jaka część tego czasu trwania jest podana do każdej klatki kluczowej. Można to zrobić, <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> opisując dla każdej z animacji klatek kluczowych. Każda klatka <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> kluczowa określa, kiedy kończy się ta klatka kluczowa.  
  
 Właściwość <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> nie określa, jak długo rozgrywa się czas klucza. Czas odtwarzania klatki kluczowej zależy od czasu zakończenia klatki kluczowej, zakończenia poprzedniej klatki kluczowej i czasu trwania animacji. Czasy klucza mogą być określone jako wartość czasu, <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>wartość procentowa lub jako wartości specjalne lub .  
  
 Na poniższej liście opisano różne sposoby określania czasów klucza.  
  
### <a name="timespan-values"></a>Wartości timespan  
 Można użyć <xref:System.TimeSpan> wartości, <xref:System.Windows.Media.Animation.KeyTime>aby określić . Wartość powinna być większa lub równa 0 i mniejsza lub równa czas trwania animacji. W poniższym przykładzie przedstawiono animację o czasie trwania 10 sekund i cztery klatki kluczowe, których czasy klucza są określone jako wartości czasu.  
  
- Pierwsza klatka kluczowa animuje wartość bazową do 100 w ciągu pierwszych 3 sekund, kończąc na czasie = 0:0:03.  
  
- Druga klatka kluczowa ożywia od 100 do 200. Rozpoczyna się po zakończeniu pierwszej klatki kluczowej (w czasie = 3 sekundy) i jest odtwarzany przez 5 sekund, kończąc na czasie = 0:0:8.  
  
- Trzecia klatka kluczowa ożywia od 200 do 500. Rozpoczyna się po zakończeniu drugiej klatki kluczowej (w czasie = 8 sekund) i jest odtwarzany przez 1 sekundę, kończąc na czasie = 0:0:9.  
  
- Czwarta klatka kluczowa ożywia od 500 do 600. Rozpoczyna się po zakończeniu trzeciej klatki kluczowej (w czasie = 9 sekund) i jest odtwarzany przez 1 sekundę, kończąc na czasie = 0:0:10.  
  
 [!code-xaml[keyframes_ovw_snippet#TimeSpanKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#timespankeytimeexample)]  
  
### <a name="percentage-values"></a>Wartości procentowe  
 Wartość procentowa określa, że klatka kluczowa kończy się <xref:System.Windows.Media.Animation.Timeline.Duration%2A>w pewnym procentie animacji . W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]obszarze , należy określić wartość `%` procentową jako liczbę, po której następuje symbol. W kodzie należy <xref:System.Windows.Media.Animation.KeyTime.FromPercent%2A> użyć metody <xref:System.Double> i przekazać go wskazując procent. Wartość musi być większa lub równa 0 i mniejsza lub równa 100 procent. W poniższym przykładzie przedstawiono animację o czasie trwania 10 sekund i cztery klatki kluczowe, których czasy klucza są określone jako wartości procentowe.  
  
- Pierwsza klatka kluczowa animuje wartość bazową do 100 w ciągu pierwszych 3 sekund, kończąc na czasie = 0:0:3.  
  
- Druga klatka kluczowa ożywia od 100 do 200. Rozpoczyna się po zakończeniu pierwszej klatki kluczowej (w czasie = 3 sekundy) i jest odtwarzany przez 5 sekund, kończąc na czasie = 0:0:8 (0,8 * 10 = 8).  
  
- Trzecia klatka kluczowa ożywia od 200 do 500. Rozpoczyna się po zakończeniu drugiej klatki kluczowej (w czasie = 8 sekund) i jest odtwarzany przez 1 sekundę, kończąc na czasie = 0:0:9 (0,9 * 10 = 9).  
  
- Czwarta klatka kluczowa ożywia od 500 do 600. Rozpoczyna się po zakończeniu trzeciej klatki kluczowej (w czasie = 9 sekund) i jest odtwarzany przez 1 sekundę, kończąc na czasie = 0:0:10 (1 * 10 = 10).  
  
 [!code-xaml[keyframes_ovw_snippet#PercentageKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#percentagekeytimeexample)]  
  
### <a name="special-value-uniform"></a>Wartość specjalna, jednolita  
 Użyj <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> chronometrażu, jeśli chcesz, aby każda klatka kluczowa zająć taką samą ilość czasu.  
  
 Czas <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> klucza dzieli dostępny czas równo przez liczbę klatek kluczowych w celu określenia czasu zakończenia każdej klatki kluczowej. W poniższym przykładzie przedstawiono animację o czasie trwania 10 sekund <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>i cztery klatki kluczowe, których czasy klucza są określone jako .  
  
- Pierwsza klatka kluczowa animuje wartość bazową do 100 w ciągu pierwszych 2,5 sekundy, kończąc na czasie = 0:0:2.5.  
  
- Druga klatka kluczowa ożywia od 100 do 200. Rozpoczyna się po zakończeniu pierwszej klatki kluczowej (w czasie = 2,5 sekundy) i jest odtwarzany przez około 2,5 sekundy, kończąc na czasie = 0:0:5.  
  
- Trzecia klatka kluczowa ożywia od 200 do 500. Rozpoczyna się po zakończeniu drugiej klatki kluczowej (w czasie = 5 sekund) i jest odtwarzany przez 2,5 sekundy, kończąc na czasie = 0:0:7.5.  
  
- Czwarta klatka kluczowa ożywia od 500 do 600. Rozpoczyna się po zakończeniu drugiej klatki kluczowej (w czasie = 7,5 sekundy) i jest odtwarzany przez 2,5 sekundy, kończąc na czasie = 0:0:1.  
  
 [!code-xaml[keyframes_ovw_snippet#UniformKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#uniformkeytimeexample)]  
  
### <a name="special-value-paced"></a>Wartość specjalna, paced  
 Czas <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> należy używać, gdy chcesz animować ze stałą szybkością.  
  
 Czas <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> klucza przydziela dostępny czas w zależności od długości każdej z klatek kluczowych, aby określić czas trwania każdej klatki.  Zapewni to zachowanie, że prędkość lub tempo animacji pozostaje stała.  W poniższym przykładzie przedstawiono animację o czasie trwania 10 sekund <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>i trzy klatki kluczowe, których czasy klucza są określone jako .  
  
 [!code-xaml[keyframes_ovw_snippet#PacedKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#pacedkeytimeexample)]  
  
 Należy zauważyć, że jeśli ostatni czas <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> klucza klatki kluczowej jest lub <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>, jego rozwiązany czas klucza zostanie ustawiony na 100 procent. Jeśli pierwsza klatka kluczowa w animacji wieloklatkowej jest w tempie, jej rozwiązany czas klucza zostanie ustawiony na 0. (Jeśli kolekcja klatek kluczowych zawiera tylko jedną klatkę kluczową i jest to klatka kluczowa w tempie, jej rozwiązany czas klucza zostanie ustawiony na 100 procent).  
  
 Różne klatki kluczowe w jednej animacji klatki kluczowej mogą używać różnych typów czasu kluczy.  
  
<a name="combiningkeytimes"></a>
## <a name="combining-key-times-out-of-order-key-frames"></a>Łączenie kluczowych czasów, ramek kluczowych poza kolejnością  
 W tej samej animacji można używać klatek kluczowych o różnych <xref:System.Windows.Media.Animation.KeyTime> typach wartości. I chociaż zaleca się dodawanie klatek kluczowych w kolejności, w jakiej powinny grać, nie jest to konieczne. System animacji i chronometrażu jest w stanie rozwiązać poza kolejnością klatek kluczowych. Klatki kluczowe z nieprawidłowymi czasami kluczy są ignorowane.  
  
 Na poniższej liście opisano procedurę, za pomocą której czasy klucza są rozpoznawane dla klatek kluczowych animacji klatki kluczowej.  
  
1. Rozwiąż <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> wartości.  
  
2. Określ całkowity *czas interpolacji*animacji , całkowity czas potrzebny animacji klatki kluczowej do ukończenia iteracji do przodu.  
  
    1. Jeśli <xref:System.Windows.Media.Animation.Timeline.Duration%2A> animacja <xref:System.Windows.Duration.Automatic%2A> nie jest <xref:System.Windows.Duration.Forever%2A>lub , całkowity czas interpolacji jest <xref:System.Windows.Media.Animation.Timeline.Duration%2A> wartością właściwości animacji.  
  
    2. W przeciwnym razie całkowity czas <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> interpolacji jest największą wartością określoną wśród jego klatek kluczowych, jeśli istnieje.  
  
    3. W przeciwnym razie całkowity czas interpolacji wynosi 1 sekundę.  
  
3. Użyj całkowitej wartości czasu <xref:System.Windows.Media.Animation.KeyTimeType.Percent> <xref:System.Windows.Media.Animation.KeyTime> interpolacji, aby rozpoznać wartości.  
  
4. Rozwiąż ostatnią klatkę kluczową, jeśli nie została jeszcze rozwiązana w poprzednich krokach. Jeśli <xref:System.Windows.Media.Animation.KeyTime> ostatnia klatka <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> kluczowa <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>jest lub , jej rozwiązany czas będzie równy całkowitemu czasowi interpolacji.  
  
     Jeśli <xref:System.Windows.Media.Animation.KeyTime> pierwsza klatka kluczowa <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> jest i ta animacja ma więcej <xref:System.Windows.Media.Animation.KeyTime> niż na klatkach kluczowych, rozwiązać jego wartość do zera; jeśli istnieje tylko jedna klatka kluczowa, a jej <xref:System.Windows.Media.Animation.KeyTime> wartość jest <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>, jest rozpoznawana do całkowitego czasu interpolacji, jak opisano w poprzednim kroku.  
  
5. Rozwiąż pozostałe <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> wartości: każdy z nich otrzymuje równy udział w dostępnym czasie.  Podczas tego procesu <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> nierozwiązane wartości są <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> tymczasowo traktowane jako wartości i uzyskać tymczasowy czas rozwiązany.  
  
6. Rozwiąż <xref:System.Windows.Media.Animation.KeyTime> wartości klatek kluczowych z nieokreślonymi czasami kluczy, używając ramek <xref:System.Windows.Media.Animation.KeyTime> kluczowych zadeklarowanych najbliżej nich, które mają rozpoznane wartości.  
  
7. Rozwiąż pozostałe <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> wartości. <xref:System.Windows.Media.Animation.KeyTime.Paced%2A><xref:System.Windows.Media.Animation.KeyTime> użyj <xref:System.Windows.Media.Animation.KeyTime> wartości sąsiednich klatek kluczowych, aby określić ich rozwiązany czas.  Celem jest zapewnienie, że prędkość animacji jest stała wokół czasu rozwiązany tej klatki kluczowej.  
  
8. Sortuj klatki kluczowe w kolejności rozpoznanego czasu (klucz podstawowy) i kolejności deklaracji (klucz pomocniczy), czyli <xref:System.Windows.Media.Animation.KeyTime> użyj stabilnego sortowania opartego na rozwiązanych wartościach ramki kluczowej.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Animation.KeyTime>
- <xref:System.Windows.Media.Animation.KeySpline>
- <xref:System.Windows.Media.Animation.Timeline>
- [Przykład animacji splajnu](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/KeySplineAnimations)
- [Przykład animacji klatki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012)
- [Przegląd Animacja](animation-overview.md)
- [Przegląd Scenorysy](storyboards-overview.md)
- [Klatki kluczowe — tematy z instrukcjami](key-frame-animation-how-to-topics.md)
- [Przegląd Zachowania chronometrażu](timing-behaviors-overview.md)
