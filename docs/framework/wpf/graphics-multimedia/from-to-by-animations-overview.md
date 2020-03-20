---
title: Informacje od animacji od-do-według
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], From/to/by
- From/to/by animation
ms.assetid: 516fce0a-e7f8-49b8-b018-53b3d409a8a3
ms.openlocfilehash: 135f01823d374b30f8d4d41762d2267a254f98c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186461"
---
# <a name="fromtoby-animations-overview"></a>Przegląd Cechy animacji od/do/przez
W tym temacie opisano sposób używania animacji Od/Do/Przez do animowania właściwości zależności. Animacja Od/Do/Przez tworzy przejście między dwiema wartościami.  
  
<a name="prereq"></a>
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć ten temat, należy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapoznać się z funkcjami animacji. Aby zapoznać się z wprowadzeniem do funkcji animacji, zobacz [Omówienie animacji](animation-overview.md).  
  
<a name="whatisanimation"></a>
## <a name="what-is-a-fromtoby-animation"></a>Co to jest animacja z/do/według?  
 A Od/Do/Przez animacji <xref:System.Windows.Media.Animation.AnimationTimeline> jest typem, który tworzy przejście między wartością początkową i wartością końcową. Czas potrzebny do ukończenia przejścia jest określany <xref:System.Windows.Media.Animation.Timeline.Duration%2A> przez tę animację.  
  
 Animację Od/Do/Przez do właściwości można zastosować <xref:System.Windows.Media.Animation.Storyboard> przy użyciu znaczników i <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> kodu lub przy użyciu metody w kodzie. Można również użyć From/To/By Animacja <xref:System.Windows.Media.Animation.AnimationClock> utworzyć i zastosować go do jednej lub więcej właściwości. Aby uzyskać więcej informacji na temat różnych metod stosowania animacji, zobacz [Omówienie technik animacji właściwości](property-animation-techniques-overview.md).  
  
 Animacje Od/Do/Przez mogą mieć nie więcej niż dwie wartości docelowe. Jeśli potrzebujesz animacji, która ma więcej niż dwie wartości docelowe, użyj animacji klatki kluczowej. Animacje klatek kluczowych są opisane w [omówienie animacji klatek kluczowych](key-frame-animations-overview.md).  
  
<a name="animation_types"></a>
## <a name="fromtoby-animation-types"></a>Typy animacji od/do/według animacji  
 Ponieważ animacje generują wartości właściwości, istnieją różne typy animacji dla różnych typów właściwości. Aby animować <xref:System.Double>właściwość, która <xref:System.Windows.FrameworkElement.Width%2A> przyjmuje , takich jak właściwość <xref:System.Double> elementu, należy użyć animacji, która tworzy wartości. Aby animować właściwość, która przyjmuje <xref:System.Windows.Point>program <xref:System.Windows.Point> , użyj animacji, która tworzy wartości i tak dalej.  
  
 Klasy animacji Od/Do/Według <xref:System.Windows.Media.Animation> należą do obszaru nazw i używają następującej konwencji nazewnictwa:  
  
 * \<>typu*`Animation`  
  
 Gdzie * \<Type>* jest typem wartości, który animuje klasę.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawiera następujące klasy animacji Od/Do/Przez.  
  
|Typ właściwości|Odpowiadająca klasa animacji Od/Do/Według|  
|-------------------|------------------------------------------------|  
|<xref:System.Byte>|<xref:System.Windows.Media.Animation.ByteAnimation>|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|  
|<xref:System.Decimal>|<xref:System.Windows.Media.Animation.DecimalAnimation>|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|  
|<xref:System.Int16>|<xref:System.Windows.Media.Animation.Int16Animation>|  
|<xref:System.Int32>|<xref:System.Windows.Media.Animation.Int32Animation>|  
|<xref:System.Int64>|<xref:System.Windows.Media.Animation.Int64Animation>|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|  
|<xref:System.Windows.Media.Media3D.Quaternion>|<xref:System.Windows.Media.Animation.QuaternionAnimation>|  
|<xref:System.Windows.Rect>|<xref:System.Windows.Media.Animation.RectAnimation>|  
|<xref:System.Windows.Media.Media3D.Rotation3D>|<xref:System.Windows.Media.Animation.Rotation3DAnimation>|  
|<xref:System.Single>|<xref:System.Windows.Media.Animation.SingleAnimation>|  
|<xref:System.Windows.Size>|<xref:System.Windows.Media.Animation.SizeAnimation>|  
|<xref:System.Windows.Thickness>|<xref:System.Windows.Media.Animation.ThicknessAnimation>|  
|<xref:System.Windows.Media.Media3D.Vector3D>|<xref:System.Windows.Media.Animation.Vector3DAnimation>|  
|<xref:System.Windows.Vector>|<xref:System.Windows.Media.Animation.VectorAnimation>|  
  
<a name="anim_values"></a>
## <a name="target-values"></a>Wartości docelowe  
 Animacja Od/Do/Przez tworzy przejście między dwiema wartościami docelowymi. Jest to typowe, aby określić wartość <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> początkową (ustawić go przy użyciu <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości) i wartość końcową (ustawić go przy użyciu właściwości). Można jednak również określić tylko wartość początkową, wartość docelową lub wartość przesunięcia. W takich przypadkach animacja uzyskuje brakującą wartość docelową z właściwości, która jest animowana. Na poniższej liście opisano różne sposoby określania wartości docelowych animacji.  
  
- **Wartość początkowa**  
  
     Użyj <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości, jeśli chcesz jawnie określić wartość początkową animacji. Z <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> obiektu można korzystać samodzielnie <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> lub <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> z właściwością lub. Jeśli określisz <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> tylko właściwość, animacja przechodzi z tej wartości do wartości podstawowej animowanej właściwości.  
  
- **Wartość końcowa**  
  
     Aby określić końcową wartość animacji, należy użyć jej <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości. Jeśli używasz <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości przez siebie, animacja uzyskuje jego wartość początkową z właściwości, która jest animowana lub z danych wyjściowych innej animacji, która jest stosowana do tej samej właściwości. Można użyć <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości wraz <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> z właściwością jawnie określić wartości początkowe i końcowe dla animacji.  
  
- **Wartość odsunięcia**  
  
     Właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> umożliwia określenie przesunięcia zamiast jawnej wartości początkowej lub zakończenia animacji. Właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> animacji określa, jak bardzo animacja zmienia wartość w czasie jej trwania. Z <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> obiektu można korzystać samodzielnie <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> lub w obiekcie. Jeśli określisz <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> tylko właściwość, animacja dodaje wartość odsunięcia do wartości podstawowej właściwości lub do danych wyjściowych innej animacji.  
  
<a name="examples"></a>
## <a name="using-fromtoby-values"></a>Używanie wartości Od/Do/Według  
 W poniższych sekcjach opisano <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>sposób <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> używania , i właściwości razem lub oddzielnie.  
  
 Przykłady w tej sekcji <xref:System.Windows.Media.Animation.DoubleAnimation>każdy użyć , który jest typem od/do/przez animacji, do animowania <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Shapes.Rectangle> właściwości, która jest 10 pikseli niezależnych od urządzenia wysoki i 100 pikseli niezależnych od urządzenia szerokości.  
  
 Chociaż każdy przykład <xref:System.Windows.Media.Animation.DoubleAnimation>używa , Od, Do i Przez właściwości wszystkich From/To/By animacje zachowują się identycznie. Chociaż każdy z tych przykładów używa <xref:System.Windows.Media.Animation.Storyboard>, można użyć From/To/By animacje w inny sposób. Aby uzyskać więcej informacji, zobacz [Omówienie technik animacji właściwości](property-animation-techniques-overview.md).  
  
### <a name="fromto"></a>Z/Do  
 Po ustawieniu <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> i wartości razem, animacja postępuje od <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> wartości, która jest określona <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> przez właściwość, do wartości, która jest określona przez właściwość.  
  
 W poniższym <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> przykładzie <xref:System.Windows.Media.Animation.DoubleAnimation> ustawia właściwość do <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 50 i jego właściwości do 300. W rezultacie, <xref:System.Windows.FrameworkElement.Width%2A> jest <xref:System.Windows.Shapes.Rectangle> animowany od 50 do 300.  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### <a name="to"></a>Do  
 Po ustawieniu <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> tylko właściwość, animacja postępuje od wartości podstawowej animowanej właściwości lub z danych wyjściowych animacji redagowania, która została <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> wcześniej zastosowana do tej samej właściwości, do wartości określonej przez właściwość.  
  
 ("Komponowanie animacji" odnosi <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.ClockState.Filling> się do lub animacji, które wcześniej stosowane do tej samej właściwości, <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> która jest nadal w mocy, gdy bieżąca animacja została zastosowana przy użyciu zachowania handoff.)  
  
 W poniższym <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> przykładzie ustawia <xref:System.Windows.Media.Animation.DoubleAnimation> tylko właściwość do 300. Ponieważ nie określono wartości <xref:System.Windows.Media.Animation.DoubleAnimation> początkowej, używa wartości podstawowej (100) <xref:System.Windows.FrameworkElement.Width%2A> właściwości jako jej wartości początkowej. Z <xref:System.Windows.FrameworkElement.Width%2A> jest <xref:System.Windows.Shapes.Rectangle> animowany od 100 do wartości docelowej animacji 300.  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### <a name="by"></a>Autor:  
 Po ustawieniu <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> tylko właściwość animacji, animacja postępuje od wartości podstawowej właściwości, która jest animowana lub z danych wyjściowych animacji redagowania do sumy tej wartości i wartość, która jest określona <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> przez właściwość.  
  
 W poniższym <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> przykładzie ustawia <xref:System.Windows.Media.Animation.DoubleAnimation> tylko właściwość do 300. Ponieważ w przykładzie nie określono <xref:System.Windows.Media.Animation.DoubleAnimation> wartości początkowej, używa <xref:System.Windows.FrameworkElement.Width%2A> wartości podstawowej właściwości 100 jako jej wartości początkowej. Wartość końcowa jest określana przez dodanie <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> wartości animacji, 300, do jej wartości początkowej, 100: 400. W rezultacie, <xref:System.Windows.FrameworkElement.Width%2A> jest <xref:System.Windows.Shapes.Rectangle> animowany od 100 do 400.  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### <a name="fromby"></a>Z/Przez  
 Po ustawieniu <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> i właściwości animacji, animacja postępuje od wartości, <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> która jest określona przez właściwość, <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> do wartości, która jest określona przez sumę i właściwości.  
  
 W poniższym <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> przykładzie <xref:System.Windows.Media.Animation.DoubleAnimation> ustawia właściwość do <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> 50 i jego właściwości do 300. Wartość końcowa jest określana przez dodanie <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> wartości animacji, 300, do jej wartości początkowej, 50: 350. W rezultacie, <xref:System.Windows.FrameworkElement.Width%2A> jest <xref:System.Windows.Shapes.Rectangle> animowany od 50 do 350.  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### <a name="from"></a>Z  
 Po określeniu <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> tylko wartość animacji, animacja postępuje od <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> wartości, która jest określona przez właściwość, do wartości podstawowej właściwości, która jest animowana lub do danych wyjściowych animacji redagowania.  
  
 W poniższym <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> przykładzie ustawia <xref:System.Windows.Media.Animation.DoubleAnimation> tylko właściwość do 50. Ponieważ nie określono wartości <xref:System.Windows.Media.Animation.DoubleAnimation> zakończenia, używa wartości <xref:System.Windows.FrameworkElement.Width%2A> podstawowej właściwości 100 jako jej wartości zakończenia. Jest <xref:System.Windows.FrameworkElement.Width%2A> animowany <xref:System.Windows.Shapes.Rectangle> od 50 do wartości <xref:System.Windows.FrameworkElement.Width%2A> podstawowej nieruchomości, 100.  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### <a name="toby"></a>Do/przez  
 Jeśli ustawisz <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> zarówno <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości i właściwości <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> animacji, właściwość jest ignorowana.  
  
<a name="otheranimationtypes"></a>
## <a name="other-animation-types"></a>Inne typy animacji  
 Animacje From/To/By nie są jedynym typem animacji, który [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapewnia: zapewnia również animacje klatek kluczowych i animacje ścieżek.  
  
- Animacja klatki kluczowej animuje wzdłuż dowolnej liczby wartości docelowych, opisanej za pomocą klatek kluczowych. Aby uzyskać więcej informacji, zobacz [Omówienie animacji klatek kluczowych](key-frame-animations-overview.md).  
  
- Animacja ścieżki generuje wartości <xref:System.Windows.Media.PathGeometry>wyjściowe z pliku . Aby uzyskać więcej informacji, zobacz [Omówienie animacji ścieżek](path-animations-overview.md).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]umożliwia również tworzenie własnych niestandardowych typów animacji. Aby uzyskać więcej informacji, zobacz [Omówienie animacji niestandardowych](custom-animations-overview.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Przegląd Animacja](animation-overview.md)
- [Przegląd Scenorysy](storyboards-overview.md)
- [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md)
- [Animacje ścieżki — przegląd](path-animations-overview.md)
- [Przegląd Niestandardowe animacje](custom-animations-overview.md)
- [Przykład wartości docelowych od, do i według animacji](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/TargetValues)
