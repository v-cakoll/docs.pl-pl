---
title: Przegląd Animacja kluczowych klatek
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], key-frame
- key frames [WPF], about key-frame animations
- multiple animation target values [WPF]
ms.assetid: 10028f97-bb63-41fc-b8ad-663dac7ea203
ms.openlocfilehash: eda91ab6d81150749dc542139949fb92684c0fe1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785817"
---
# <a name="key-frame-animations-overview"></a>Przegląd Animacja kluczowych klatek
W tym temacie przedstawiono Animacja kluczowych klatek. Animacje kluczowych klatek — umożliwiają animowanie za pomocą więcej niż dwóch wartości docelowych i kontrolować metodę interpolacji animacji.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć, w tym omówieniu, należy się zapoznać z [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] animacje i osi czasu. Aby zapoznać się z wprowadzeniem do animacji, zobacz [Przegląd animacja](animation-overview.md). Pomaga również należy zapoznać się z od/do/przez animacji. Aby uzyskać więcej informacji zobacz Omówienie animacji From/To/By.  
  
<a name="whatisakeyframeanimation"></a>   
## <a name="what-is-a-key-frame-animation"></a>Co to jest animacja kluczowych klatek?  
 Jak od/do/przez animację, animacji kluczowych klatek animuje wartość właściwości docelowej. Tworzy przejścia między jego wartości docelowych za pośrednictwem jego <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. Jednakże podczas od/do/przez animację tworzy przejście między dwiema wartościami, jednej animacji kluczowych klatek można tworzyć przejścia między dowolną liczbę wartości docelowych. W odróżnieniu od od/do/przez animację, animacji klatek kluczowych ma nie From, aby lub za pomocą właściwości, za pomocą którego można ustawić wartości docelowej. Wartości docelowe animacji kluczowych klatek są opisane za pomocą obiektów klatek kluczowych (dlatego termin, "animacji kluczowych klatek"). Aby określić wartości docelowych animacji, tworzenia obiektów klatek kluczowych i dodać je do animacji <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> kolekcji. Po uruchomieniu animacji przechodzi między ramek, wskazana.  
  
 Oprócz obsługi wielu wartości docelowych, niektóre metody kluczowych klatek nawet obsługuje wiele metod interpolacji. Metoda interpolacji animacji definiuje, jak przechodzi od jednej wartości do następnej. Istnieją trzy typy interpolations: dyskretnych, liniowej i splined.  
  
 Aby animować za pomocą animacji kluczowych klatek, są wykonaj następujące czynności.  
  
- Deklarowanie animacji i określ jej <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, podobnie jak w przypadku animacji od/do/przez.  
  
- Dla każdej wartości docelowej, należy utworzyć klatek kluczowych odpowiedniego typu, ustaw dla niego wartość i <xref:System.Windows.Media.Animation.KeyTime>i dodaj go do animacji <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> kolekcji.  
  
- Skojarz animacji z właściwością tak samo jak w przypadku usługi od/do/przez animację. Aby uzyskać więcej informacji na temat zastosowania animacji do właściwości przy użyciu scenorysu, zobacz [Przegląd Scenorysy](storyboards-overview.md).  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> animować <xref:System.Windows.Shapes.Rectangle> element do czterech różnych lokalizacji.  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
 Takich jak od/do/przez animację, animacji kluczowych klatek można zastosować do właściwości przy użyciu <xref:System.Windows.Media.Animation.Storyboard> znaczników i kodu lub za pomocą <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> w kodzie. Można także użyć do tworzenia animacji kluczowych klatek <xref:System.Windows.Media.Animation.AnimationClock> i zastosować je do co najmniej jednej właściwości. Aby uzyskać więcej informacji na temat różnych metod do zastosowania animacji, zobacz [Przegląd techniki animacji właściwości](property-animation-techniques-overview.md).  
  
<a name="animation_types"></a>   
## <a name="key-frame-animation-types"></a>Typy animacji kluczowych klatek  
 Animacje generować wartości właściwości, dlatego są typy inną animację dla różnych typach właściwości. Aby animować właściwości, która przyjmuje <xref:System.Double> (np. element <xref:System.Windows.FrameworkElement.Width%2A> właściwości), użyj animacji, która tworzy <xref:System.Double> wartości. Aby animować właściwości, która przyjmuje <xref:System.Windows.Point>, użyj animacji, która tworzy <xref:System.Windows.Point> wartości i tak dalej.  
  
 Klasy animacji kluczowych klatek należą do <xref:System.Windows.Media.Animation> przestrzeni nazw i przestrzegaj następująca Konwencja nazewnictwa:  
  
 *\<Typ >* `AnimationUsingKeyFrames`  
  
 Gdzie  *\<typ >* ma typ wartości, które animuje klasy.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera następujące klasy animacji kluczowych klatek.  
  
|Typ właściwości|Odpowiednią klasę animacji od/do/przez|Obsługiwane metody interpolacji|  
|-------------------|------------------------------------------------|-------------------------------------|  
|<xref:System.Boolean>|<xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>|Dyskretne|  
|<xref:System.Byte>|<xref:System.Windows.Media.Animation.ByteAnimationUsingKeyFrames>|Dyskretnych, liniowej, Splined|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|Dyskretnych, liniowej, Splined|  
|<xref:System.Decimal>|<xref:System.Windows.Media.Animation.DecimalAnimationUsingKeyFrames>|Dyskretnych, liniowej, Splined|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|Dyskretnych, liniowej, Splined|  
|<xref:System.Int16>|<xref:System.Windows.Media.Animation.Int16AnimationUsingKeyFrames>|Dyskretnych, liniowej, Splined|  
|<xref:System.Int32>|<xref:System.Windows.Media.Animation.Int32AnimationUsingKeyFrames>|Dyskretnych, liniowej, Splined|  
|<xref:System.Int64>|<xref:System.Windows.Media.Animation.Int64AnimationUsingKeyFrames>|Dyskretnych, liniowej, Splined|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames>|Dyskretne|  
|<xref:System.Object>|<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>|Dyskretne|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|Dyskretnych, liniowej, Splined|  
|<xref:System.Windows.Media.Media3D.Quaternion>|<xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames>|Dyskretnych, liniowej, Splined|  
|<xref:System.Windows.Rect>|<xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>|Dyskretnych, liniowej, Splined|  
|<xref:System.Windows.Media.Media3D.Rotation3D>|<xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames>|Dyskretnych, liniowej, Splined|  
|<xref:System.Single>|<xref:System.Windows.Media.Animation.SingleAnimationUsingKeyFrames>|Dyskretnych, liniowej, Splined|  
|<xref:System.String>|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|Dyskretne|  
|<xref:System.Windows.Size>|<xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>|Dyskretnych, liniowej, Splined|  
|<xref:System.Windows.Thickness>|<xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames>|Dyskretnych, liniowej, Splined|  
|<xref:System.Windows.Media.Media3D.Vector3D>|<xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames>|Dyskretnych, liniowej, Splined|  
|<xref:System.Windows.Vector>|<xref:System.Windows.Media.Animation.VectorAnimationUsingKeyFrames>|Dyskretnych, liniowej, Splined|  
  
<a name="animation_target_values"></a>   
## <a name="target-values-key-frames-and-key-times"></a>Dotyczą wartości (klatek kluczowych) i czas klucza  
 Tak, jak istnieją różne rodzaje Animacja kluczowych klatek animowania różnych typach właściwości, dostępne są także różne rodzaje ramek kluczowych obiektów: jeden dla każdego typu wartości animowane i metodę interpolacji obsługiwane. Typy ramek kluczowych stosować się do następującej konwencji nazewnictwa:  
  
 *\<InterpolationMethod >\<typ >* `KeyFrame`  
  
 Gdzie  *\<InterpolationMethod >* jest metodą interpolacji używa klatek kluczowych i  *\<typ >* ma typ wartości, które animuje klasy. Animacja kluczowych klatek, który obsługuje wszystkich interpolację trzech metod będzie mieć trzy typy klatek kluczowych, które są dostępne. Na przykład, można użyć trzy typy kluczy ramki za pomocą <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>: <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>, <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>, i <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>. (Interpolacji metody są opisane szczegółowo w dalszej części tego tematu).  
  
 Głównym celem klatka kluczowa jest zdefiniowanie <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> i <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>. Każdy typ ramki kluczowe udostępnia te dwie właściwości.  
  
- <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> Właściwość określa wartość docelowa dla tego kluczowych klatek.  
  
- <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> Właściwość określa, kiedy (w ramach animacji <xref:System.Windows.Media.Animation.Timeline.Duration%2A>) klatek kluczowych <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> zostanie osiągnięty.  
  
 Po rozpoczęciu animacji klatek kluczowych iteruje przez jej klatek kluczowych w kolejności, zdefiniowanych przez ich <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> właściwości.  
  
- Jeśli w czasie 0 jest bez klucza ramki, animacji tworzy przejście między bieżącą wartość właściwości docelowej i <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> pierwszej ramki kluczowe; w przeciwnym razie animacji danych wyjściowych wartość staje się wartość pierwszej ramki kluczowe.  
  
- Animacja tworzy przejście między <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> z klatkami kluczowymi pierwszego i drugiego za pomocą metody interpolacji określony przez drugi klatek kluczowych. Przejście rozpoczyna się od pierwszej ramki kluczowe <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> i kończy się po drugiej ramki kluczowe <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> zostanie osiągnięty.  
  
- Animacja będzie się powtarzać, tworząc przejścia między każdym kolejnych klatek kluczowych i jego poprzedniej ramki kluczowe.  
  
- Ponadto, przejścia do animacji do wartości klatek kluczowych największy czas klucza jest równa lub mniejsza niż animacji <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.  
  
 Jeśli animacji <xref:System.Windows.Media.Animation.Timeline.Duration%2A> jest <xref:System.Windows.Duration.Automatic%2A> lub jego <xref:System.Windows.Media.Animation.Timeline.Duration%2A> jest taki sam, jak czas ostatniej ramki kluczowe zakończenia animacji. W przeciwnym razie, jeśli animacji <xref:System.Windows.Duration> jest większa niż wartość klucza czasu ostatniej ramki kluczowe przechowuje animacji, wartość klucza ramki, dopóki osiągnie koniec jego <xref:System.Windows.Duration>. Podobnie jak wszystkie animacje korzysta animacji kluczowych klatek jego <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> właściwości w celu określenia, czy posiada on końcowa wartość po osiągnięciu końca jego okresu aktywności. Aby uzyskać więcej informacji, zobacz [zachowania chronometrażu — Przegląd](timing-behaviors-overview.md).  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> obiektu zdefiniowane w poprzednim przykładzie, aby zademonstrować sposób, w jaki <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> i <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> pracy właściwości.  
  
- Pierwszej ramki kluczowe natychmiast ustawia wartość danych wyjściowych animacji do 0.  
  
- Drugi klatek kluczowych animuje z zakresu od 0 do 350. Uruchamia się po zakończeniu pierwszego klatek kluczowych (czas = 0 sekund) i będzie odtwarzany na 2 sekundy, a kończąc na czas = 0:0:2.  
  
- Trzeci klatek kluczowych animuje od 350 do 50. Jego uruchomieniu, gdy kończy się druga klatek kluczowych (w momencie = 2 sekundy) i będzie odtwarzany na 5 sekund, kończąc na czas = 0:0:7.  
  
- Czwarty klatek kluczowych animuje od 50 do 200. Uruchamia się po zakończeniu trzeci klatek kluczowych (w momencie = 7 sekund) i będzie odtwarzany na 1 sekundę, a kończąc na czas = 0:0:8.  
  
- Ponieważ <xref:System.Windows.Media.Animation.Timeline.Duration%2A> właściwości animacji został ustawiony na 10 sekund, animacja przechowuje wartość końcowej dla dwóch sekund przed zakończenia w czasie = 0:0:10.  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
<a name="interpolationmethods"></a>   
## <a name="interpolation-methods"></a>Metody interpolacji  
 Poprzednich sekcji wspomnieć, że niektórych animacji kluczowych klatek obsługuje wiele metod interpolacji. Interpolacji animacji w tym artykule opisano sposób animacji przechodzi między wartościami w czasie jego trwania. Wybranie typu klatek kluczowych pomocą animacji, można zdefiniować metodę interpolacji dla tego segmentu klatek kluczowych. Istnieją trzy różne rodzaje metod interpolacji: liniowego, odrębny i splined.  
  
### <a name="linear-interpolation"></a>Interpolacji liniowej  
 Przy użyciu interpolacji liniowej animacji w miarę stałą prędkością, czasu trwania segmentu. Na przykład, jeśli segment klatek kluczowych przejścia z zakresu od 0 do 10 dany okres 5 sekund, animacja zwróci następujące wartości w określonym razy:  
  
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
  
### <a name="discrete-interpolation"></a>Dyskretne interpolacji  
 Przy użyciu interpolacji dyskretnych funkcja animacji przechodzi z jednej wartości do następnego bez interpolacji. Jeśli segment klatek kluczowych przejścia z zakresu od 0 do 10 dany okres 5 sekund, animacja zwróci następujące wartości w określonym razy:  
  
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
  
 Zwróć uwagę, jak animacji nie zmienia jej wartość danych wyjściowych do czasu zakończenia bardzo czas trwania segmentu.  
  
 Interpolacja splined jest bardziej złożona. Jest on opisany w następnej sekcji.  
  
<a name="anim_spline"></a>   
### <a name="splined-interpolation"></a>Splined interpolacji  
 Splined interpolacji można osiągnąć bardziej realistycznego efekty chronometrażu. Animacje tak często są używane do naśladowania efekty, które występują w świecie rzeczywistym, deweloperzy mogą muszą pracownikom działu kontroli przyspieszenia i opóźnienia obiektów i zamknij manipulowania segmentów chronometrażu. Ramek kluczowych krzywej składanej umożliwiają animowanie z interpolacją splined. W przypadku innych klatek kluczowych można określić <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> i <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>. Przy użyciu klatek kluczowych krzywej składanej, należy także określić <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A>. W poniższym przykładzie pokazano jednego z krzywymi składanymi ramki kluczowe dla <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>. Zwróć uwagę <xref:System.Windows.Media.Animation.KeySpline> właściwość; która jest, co sprawia, że klatek kluczowych krzywej składanej różni się od innych rodzajów klatek kluczowych.  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 Krzywą Beziera trzeciego stopnia jest definiowany przez dwa punkty kontrolne, punkt początkowy i punkt końcowy. <xref:System.Windows.Media.Animation.KeySpline> Właściwość krzywej składanej ramki kluczowe definiuje punkt kontrolny krzywej Beziera, który rozciąga się od (0,0) (1,1). Pierwszy punkt kontrolny kontroluje współczynnik w pierwszej połowie krzywą Beziera krzywej, a drugi punkt kontrolny kontroluje współczynnik w drugiej połowie segmentu krzywej Beziera krzywej. Wynikowy krzywej w tym artykule opisano szybkość zmian dla tej ramki kluczowych krzywej składanej. Większe krzywej, tym szybsze klatek kluczowych zmienia jego wartości. Ponieważ krzywej pobiera płaski, klatek kluczowych wolniej zmienia jego wartości.  
  
 Można na przykład <xref:System.Windows.Media.Animation.KeySpline> do symulacji trajektorii fizycznych, takich jak woda objętych lub odbijania kulki lub zastosowania innych "jej obsługi ułatwiają realizację w" i "przyśpiesz tempo zmian" efekty animacjach ruchu. Dla efektów interakcji użytkownika, jak zanikanie tło lub kontrolki przycisku odbicia mogą być stosowane splined interpolacji, aby przyspieszyć lub spowolnić proces zmiany dla animacji w określony sposób.  
  
 W poniższym przykładzie określono <xref:System.Windows.Media.Animation.KeySpline> 1,0 0,1, co powoduje utworzenie następujących krzywą Beziera.  
  
 ![Krzywa Beziera](./media/graphicsmm-keyspline-0-1-1-0.png "graphicsmm_keyspline_0_1_1_0")  
Kluczowych krzywej składanej przy użyciu punktów kontrolnych (0.0, 1.0) i (1.0, 0.0)  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 Tej ramki kluczowe animuje szybko po jego rozpoczyna się, spowalnia, a następnie przyspiesza ponownie przed zakończeniem jej.  
  
 W poniższym przykładzie określono <xref:System.Windows.Media.Animation.KeySpline> z 0.75,1.0 0.5,0.25, co powoduje utworzenie następujących krzywą Beziera.  
  
 ![Krzywa Beziera](./media/graphicsmm-keyspline-025-050-075-10.png "graphicsmm_keyspline_025_050_075_10")  
Kluczowych krzywej składanej kontrolką punkty (0,25, 0,5) i (0,75, 1.0)  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexampleinline3)]  
  
 Ponieważ łuku krzywej Beziera zmienia się bardzo niewiele, tej ramki kluczowe animuje stawki prawie stały; go spowalnia nieco kierunku jej końcu.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> animować pozycja prostokąta. Ponieważ <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> używa <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> obiektów, przejście pomiędzy każdej wartości kluczowych klatek używa splined interpolacji.  
  
 [!code-xaml[keyframes_ovw_snippet#SplinedInterpolationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#splinedinterpolationexample)]  
  
 Interpolacja splined może być trudne do zrozumienia; eksperymentowanie z różnymi ustawieniami może pomóc. [Przykład animacji z krzywymi składanymi klucz](https://go.microsoft.com/fwlink/?LinkID=160011) pozwala Ci zmienić wartości klucza z krzywymi składanymi i wyświetlić wynik, ma to na animacji.  
  
<a name="combininginterpolationmethods"></a>   
### <a name="combining-interpolation-methods"></a>Łącząc metody interpolacji  
 Za pomocą klatek kluczowych interpolacji różnych typów w animacji jednej ramki kluczowe. Po dwóch animacji klatek kluczowych przy użyciu różnych interpolations postępuj zgodnie z sobą, metodę interpolacji drugiej ramki kluczowe służy do tworzenia przejścia z pierwsza wartość do drugiego.  
  
 W poniższym przykładzie <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> utworzeniu tej używa interpolacji liniowej splined i dyskretnych.  
  
 [!code-xaml[keyframes_ovw_snippet#ComboInterpolationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#combointerpolationexample)]  
  
<a name="keytimes"></a>   
## <a name="more-about-duration-and-key-times"></a>Więcej informacji o czasie trwania i czasy klucza  
 Podobnie jak inne animacji mają Animacja kluczowych klatek <xref:System.Windows.Duration> właściwości. Oprócz określenia animacji <xref:System.Windows.Duration>, należy określić, jaka część za ten czas, znajduje się na każdej ramce klucza. Możesz to zrobić poprzez opisanie <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> dla każdego z użyciem klatek kluczowych animacji. Każdej ramki kluczowe <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> Określa, kiedy kończy się tym klatek kluczowych.  
  
 <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> Właściwość nie określa, jak długo odgrywa czas klucza. Ilość czasu, który odtwarzania klatek kluczowych zależy od kiedy kończy się klatek kluczowych, kiedy zakończył się poprzedniej ramki kluczowe i czas trwania animacji. Czas klucza może być określony jako wartość czasu, wartość procentowa, lub specjalnych wartości <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> lub <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>.  
  
 Na poniższej liście opisano różne sposoby określania czasu klucza.  
  
### <a name="timespan-values"></a>Wartości TimeSpan  
 Możesz użyć <xref:System.TimeSpan> wartości określające <xref:System.Windows.Media.Animation.KeyTime>. Wartość powinna być większa lub równa 0 i mniejsza niż czas trwania animacji. Poniższy przykład pokazuje animacji o czasie trwania 10 sekund i cztery klatki kluczowe, których czas klucza są określone jako wartości typu time.  
  
- Animuje pierwszej ramki kluczowe od wartości bazowej do 100 przez pierwsze 3 sekundach, kończąc na czas = 0:0:03.  
  
- Drugi klatek kluczowych animuje od 100 do 200. Uruchamia się po zakończeniu pierwszego klatek kluczowych (w momencie = 3 sekundy) i odtwarzany na 5 sekund, kończąc na czas = 0:0:8.  
  
- Trzeci klatek kluczowych animuje z 200 do 500. Jego uruchomieniu, gdy kończy się druga klatek kluczowych (w momencie = 8 sekund) i będzie odtwarzany na 1 sekundę, a kończąc na czas = 0:0:9.  
  
- Czwarty klatek kluczowych animacji od 500 do 600. Uruchamia się po zakończeniu trzeci klatek kluczowych (w momencie = sekund 9) i będzie odtwarzany na 1 sekundę, a kończąc na czas = 0:0:10.  
  
 [!code-xaml[keyframes_ovw_snippet#TimeSpanKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#timespankeytimeexample)]  
  
### <a name="percentage-values"></a>Wartości procentowe  
 Wartość procentowa Określa, że klatek kluczowych kończy się na wartość procentową animacji <xref:System.Windows.Media.Animation.Timeline.Duration%2A>. W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], określ wartość procentową jako numer, a następnie `%` symboli. W kodzie, należy użyć <xref:System.Windows.Media.Animation.KeyTime.FromPercent%2A> metody i przekazać go <xref:System.Double> określającą procent. Wartość musi być większa lub równa 0 i mniejsza niż 100 procent. Poniższy przykład pokazuje animacji o czasie trwania 10 sekund i cztery klatki kluczowe, których czas klucza są określone jako wartości procentowe.  
  
- Animuje pierwszej ramki kluczowe od wartości bazowej do 100 przez pierwsze 3 sekundach, kończąc na czas = 0:0:3.  
  
- Drugi klatek kluczowych animuje od 100 do 200. Uruchamia się po zakończeniu pierwszego klatek kluczowych (w momencie = 3 sekundy) i odtwarzany na 5 sekund, kończąc na czas = 0:0:8 (0,8 * 10 = 8).  
  
- Trzeci klatek kluczowych animuje z 200 do 500. Jego uruchomieniu, gdy kończy się druga klatek kluczowych (w momencie = 8 sekund) i będzie odtwarzany na 1 sekundę, a kończąc na czas = 0:0:9 (0,9 * 10 = 9).  
  
- Czwarty klatek kluczowych animacji od 500 do 600. Uruchamia się po zakończeniu trzeci klatek kluczowych (w momencie = sekund 9) i będzie odtwarzany na 1 sekundę, a kończąc na czas = 0:0:10 (1 * 10 = 10).  
  
 [!code-xaml[keyframes_ovw_snippet#PercentageKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#percentagekeytimeexample)]  
  
### <a name="special-value-uniform"></a>Specjalna wartość, Uniform  
 Użyj <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> czasu, jeśli chcesz, aby każdy klatek kluczowych się zająć tyle samo czasu.  
  
 A <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> kluczowym dzieli czas dostępności równie przez liczbę klatek kluczowych, aby określić czas zakończenia każdego klatek kluczowych. W poniższym przykładzie pokazano animacji o czasie trwania 10 sekund i cztery klatki kluczowe, których klucz czasu są określane jako <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>.  
  
- Animuje pierwszej ramki kluczowe od wartości bazowej do 100 za pośrednictwem w ciągu pierwszych 2,5 sekund, kończąc na czas = 0:0:2.5.  
  
- Drugi klatek kluczowych animuje od 100 do 200. Uruchamia się po zakończeniu pierwszego klatek kluczowych (w momencie = 2,5 sekund) i odtwarzany przez około 2,5 sekund, kończąc na czas = 0:0:5.  
  
- Trzeci klatek kluczowych animuje z 200 do 500. Jego uruchomieniu, gdy kończy się druga klatek kluczowych (w momencie = 5 sekund) i odtwarzany 2,5 sekund, kończąc na czas = 0:0:7.5.  
  
- Czwarty klatek kluczowych animacji od 500 do 600. Jego uruchomieniu, gdy kończy się druga klatek kluczowych (w momencie = 7.5 sekund) i odtwarzany 2,5 sekund, kończąc na czas = 0:0:1.  
  
 [!code-xaml[keyframes_ovw_snippet#UniformKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#uniformkeytimeexample)]  
  
### <a name="special-value-paced"></a>Specjalna wartość, realizowany  
 Użyj <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> czasu, gdy chcesz animować stałą prędkością.  
  
 A <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> kluczowym przydziela czas dostępności długość każdego z klatkami kluczowymi Aby określić czas trwania każdej ramce.  Zapewni to zachowanie prędkość lub tempie animacji pozostaje stała.  W poniższym przykładzie pokazano animacji o czasie trwania 10 sekund i trzy klatki kluczowe, których klucz czasu są określane jako <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>.  
  
 [!code-xaml[keyframes_ovw_snippet#PacedKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#pacedkeytimeexample)]  
  
 Należy zauważyć, że jeśli czas klucza ostatniej ramki kluczowe jest <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> lub <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>, jego usunięciu czas klucza zostanie ustawiony na 100 procent. Jeśli pierwszy klatek kluczowych animacji wieloma ramkami jest realizowany, jego usunięciu czas klucza będzie równa 0. (Jeśli kolekcja klatek kluczowych zawiera tylko jednej ramki kluczowe i jest realizowany klatek kluczowych, jego usunięciu czas klucza zostanie ustawiona do 100 procent.)  
  
 Różne klatek kluczowych w obrębie jednej ramki kluczowe animacji może używać typów inny czas klucza.  
  
<a name="combiningkeytimes"></a>   
## <a name="combining-key-times-out-of-order-key-frames"></a>Łącząc czas klucza, klucz poza kolejnością ramek  
 Za pomocą klatek kluczowych różnych <xref:System.Windows.Media.Animation.KeyTime> typów animacji tej samej wartości. I chociaż jest to zalecane Dodaj klatek kluczowych w kolejności, w którym powinna być odtwarzana, nie jest konieczne. Animacja i chronometraż system jest w stanie rozwiązywania poza kolejnością klatek kluczowych. Klatki kluczowe nieprawidłowy czas klucza są ignorowane.  
  
 Na poniższej liście opisano procedury, za pomocą którego klucza czasu są rozwiązywane ramek kluczowych animacji kluczowych klatek.  
  
1. Rozwiąż <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> wartości.  
  
2. Określić animacji *całkowity czas interpolacji*, całkowity czas potrzebny do ukończenia iteracji do przodu animacji kluczowych klatek.  
  
    1. Jeśli animacji <xref:System.Windows.Media.Animation.Timeline.Duration%2A> nie <xref:System.Windows.Duration.Automatic%2A> lub <xref:System.Windows.Duration.Forever%2A>, Czas całkowity interpolacji to wartość zmiennej animacji <xref:System.Windows.Media.Animation.Timeline.Duration%2A> właściwości.  
  
    2. W przeciwnym razie jest największy czas całkowity interpolacji <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> wartość określoną wśród jej klatek kluczowych, jeśli takie istnieją.  
  
    3. W przeciwnym razie całkowitej interpolacji czasu wynosi 1 s.  
  
3. Użyj interpolacji łączna wartość czasu można rozpoznać <xref:System.Windows.Media.Animation.KeyTimeType.Percent> <xref:System.Windows.Media.Animation.KeyTime> wartości.  
  
4. Rozwiąż ostatniej ramki kluczowe, jeśli jeszcze nie został rozwiązany w poprzednich krokach. Jeśli <xref:System.Windows.Media.Animation.KeyTime> ostatniej ramki kluczowe jest <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> lub <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>, czas jego usunięciu będzie równy czasowi interpolacji całkowitej.  
  
     Jeśli <xref:System.Windows.Media.Animation.KeyTime> pierwszej ramki kluczowe jest <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> i tą animację ma więcej niż na klatek kluczowych rozwiązać jego <xref:System.Windows.Media.Animation.KeyTime> wartość równa zeru; Jeśli istnieje tylko jeden klatek kluczowych i jego <xref:System.Windows.Media.Animation.KeyTime> wartość jest <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>, jest ono rozwiązane w sumie interpolacji czasu, zgodnie z opisem w poprzednim kroku.  
  
5. Rozwiąż pozostałe <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> wartości: każdy posiadają równa część dostępny czas.  W trakcie tego procesu nierozpoznanych <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> wartości tymczasowo są traktowane jako <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> wartości i get tymczasowego rozwiązane czasu.  
  
6. Rozwiąż <xref:System.Windows.Media.Animation.KeyTime> wartości kluczowych klatek z nieokreślony czas klucza przy użyciu klatek kluczowych zadeklarowana najbliżej nich, które zostały rozwiązane <xref:System.Windows.Media.Animation.KeyTime> wartości.  
  
7. Rozwiąż pozostałe <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> wartości. <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> Użyj <xref:System.Windows.Media.Animation.KeyTime> wartości między sąsiednimi klucza ramek, aby określić czas rozwiązania.  Celem jest zapewnienie stałej w czasie zbliżonym do czasu rozwiązania klatek kluczowych szybkość animacji.  
  
8. Sortowanie klatek kluczowych w kolejności czas rozwiązania (klucz podstawowy) i kolejności deklaracji (klucz pomocniczy), czyli, użyj stabilne sortowanie oparte na rozwiązany klatek kluczowych <xref:System.Windows.Media.Animation.KeyTime> wartości.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Animation.KeyTime>
- <xref:System.Windows.Media.Animation.KeySpline>
- <xref:System.Windows.Media.Animation.Timeline>
- [Przykład animacji klucza z krzywymi składanymi](https://go.microsoft.com/fwlink/?LinkID=160011)
- [Przykład animacji klatki kluczowej](https://go.microsoft.com/fwlink/?LinkID=160012)
- [Animacja — przegląd](animation-overview.md)
- [Scenorysy — przegląd](storyboards-overview.md)
- [Klatki kluczowe — tematy z instrukcjami](key-frame-animation-how-to-topics.md)
- [Zachowania chronometrażu — przegląd](timing-behaviors-overview.md)
