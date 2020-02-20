---
title: Omówienie animacji od do do-przez
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], From/to/by
- From/to/by animation
ms.assetid: 516fce0a-e7f8-49b8-b018-53b3d409a8a3
ms.openlocfilehash: 661c035f55ba1fb550726d75921cd01a72b2eecc
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449013"
---
# <a name="fromtoby-animations-overview"></a>Przegląd Cechy animacji od/do/przez
W tym temacie opisano, jak używać animacji z/do/przez animacje do animowania właściwości zależności. Animacja od/do/przez tworzy przejście między dwiema wartościami.  
  
<a name="prereq"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć ten temat, należy zapoznać się z funkcjami animacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Aby zapoznać się z wprowadzeniem do funkcji animacji, zobacz [Omówienie animacji](animation-overview.md).  
  
<a name="whatisanimation"></a>   
## <a name="what-is-a-fromtoby-animation"></a>Co to jest animacja z/do/przez?  
 Animacja typu "od/do/przez" to typ <xref:System.Windows.Media.Animation.AnimationTimeline>, który tworzy przejście między wartością początkową a wartością końcową. Czas, przez jaki przejście będzie przebiegać, zależy od <xref:System.Windows.Media.Animation.Timeline.Duration%2A> tej animacji.  
  
 Do właściwości można zastosować animację od/do/przez użycie <xref:System.Windows.Media.Animation.Storyboard> w znacznikach i kodzie albo za pomocą metody <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> w kodzie. Możesz również użyć animacji od/do/przez, aby utworzyć <xref:System.Windows.Media.Animation.AnimationClock> i zastosować ją do jednej lub wielu właściwości. Aby uzyskać więcej informacji o różnych metodach stosowania animacji, zobacz [Omówienie technik animacji właściwości](property-animation-techniques-overview.md).  
  
 Animacje z/do/według animacji nie mogą mieć więcej niż dwóch wartości docelowych. Jeśli potrzebujesz animacji, która ma więcej niż dwie wartości docelowe, użyj animacji klatek kluczowych. Animacje kluczowych klatek są opisane w temacie [animacje klatek kluczowych — Omówienie](key-frame-animations-overview.md).  
  
<a name="animation_types"></a>   
## <a name="fromtoby-animation-types"></a>Typy animacji od/do/według  
 Ponieważ animacje generują wartości właściwości, istnieją różne typy animacji dla różnych typów właściwości. Aby animować właściwość, która pobiera <xref:System.Double>, na przykład właściwość <xref:System.Windows.FrameworkElement.Width%2A> elementu, użyj animacji, która generuje wartości <xref:System.Double>. Aby animować właściwość, która pobiera <xref:System.Windows.Point>, użyj animacji, która generuje wartości <xref:System.Windows.Point> i tak dalej.  
  
 Klasy animacji od/do/przez należą do przestrzeni nazw <xref:System.Windows.Media.Animation> i używają następującej konwencji nazewnictwa:  
  
 *> typu\<* `Animation`  
  
 Gdzie *typ\<>* jest typem wartości, który jest animowany przez klasę.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia następujące klasy animacji od/do/.  
  
|Typ właściwości|Odpowiadająca klasie animacji z/do/przez|  
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
 Animacja od/do/przez tworzy przejście między dwiema wartościami docelowymi. Często należy określić wartość początkową (ustawić ją przy użyciu właściwości <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>) i wartość końcową (ustawić ją przy użyciu właściwości <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>). Można jednak określić tylko wartość początkową, wartość docelową lub wartość przesunięcia. W takich przypadkach animacja uzyskuje brakującą wartość docelową ze animowanej właściwości. Na poniższej liście opisano różne sposoby określania wartości docelowych animacji.  
  
- **Wartość początkowa**  
  
     Użyj właściwości <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, jeśli chcesz jawnie określić wartość początkową animacji. Możesz użyć właściwości <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> przez samą siebie lub z właściwością <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> lub <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>. Jeśli określisz tylko Właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, przejścia animacji z tej wartości do wartości podstawowej animowanej właściwości.  
  
- **Wartość końcowa**  
  
     Aby określić wartość końcową animacji, użyj jej właściwości <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>. Jeśli używasz właściwości <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> samodzielnie, animacja uzyskuje jej wartość początkową z właściwości, która jest animowana lub z danych wyjściowych innej animacji, która jest stosowana do tej samej właściwości. Można użyć właściwości <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> razem z właściwością <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, aby jawnie określić wartości początkowe i końcowe animacji.  
  
- **Wartość przesunięcia**  
  
     Właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> pozwala określić przesunięcie zamiast jawnej wartości początkowej lub końcowej animacji. Właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> animacji określa, ile animacji zmienia wartość w czasie trwania. Możesz użyć właściwości <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> przez samą siebie lub z właściwością <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>. W przypadku określenia tylko właściwości <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> animacja dodaje wartość przesunięcia do wartości podstawowej właściwości lub do danych wyjściowych innej animacji.  
  
<a name="examples"></a>   
## <a name="using-fromtoby-values"></a>Używanie wartości z/do/przez  
 W poniższych sekcjach opisano, jak jednocześnie używać właściwości <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.  
  
 W przykładach w tej sekcji użyto <xref:System.Windows.Media.Animation.DoubleAnimation>, który jest typem animacji od/do/przez animację, aby animować Właściwość <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Shapes.Rectangle> z 10 niezależnymi pikselami o wysokim poziomie i 100.  
  
 Mimo że każdy przykład używa <xref:System.Windows.Media.Animation.DoubleAnimation>, właściwości od, do i ze wszystkich animacji między/do/przez animacje zachowują się identycznie. Chociaż każdy z tych przykładów używa <xref:System.Windows.Media.Animation.Storyboard>, można użyć animacji od/do/przez animacje w inny sposób. Aby uzyskać więcej informacji, zobacz [Omówienie technik animacji właściwości](property-animation-techniques-overview.md).  
  
### <a name="fromto"></a>Od/do  
 Po ustawieniu <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> wartości, animacja postępuje z wartości, która jest określona przez właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, do wartości, która jest określona przez właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>.  
  
 Poniższy przykład ustawia właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> <xref:System.Windows.Media.Animation.DoubleAnimation> na 50, a jej Właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> na 300. W efekcie <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Shapes.Rectangle> jest animowany od 50 do 300.  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### <a name="to"></a>Do  
 Po ustawieniu tylko właściwości <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> animacja postępuje z wartości podstawowej właściwości animowanej lub z danych wyjściowych animacji tworzenia, która została wcześniej zastosowana do tej samej właściwości, do wartości określonej przez właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>.  
  
 ("Animacja redagowania" odnosi się do <xref:System.Windows.Media.Animation.ClockState.Active> lub <xref:System.Windows.Media.Animation.ClockState.Filling> animacji, która została wcześniej zastosowana do tej samej właściwości, która nadal obowiązuje po zastosowaniu bieżącej animacji przy użyciu zachowania <xref:System.Windows.Media.Animation.HandoffBehavior.Compose>.)  
  
 W poniższym przykładzie ustawiono tylko <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> Właściwość <xref:System.Windows.Media.Animation.DoubleAnimation> na 300. Ponieważ nie określono wartości początkowej, <xref:System.Windows.Media.Animation.DoubleAnimation> używa wartości bazowej (100) właściwości <xref:System.Windows.FrameworkElement.Width%2A> jako wartości początkowej. <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Shapes.Rectangle> jest animowany od 100 do wartości docelowej animacji 300.  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### <a name="by"></a>Od  
 Po ustawieniu właściwości <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> animacji, animacja postępuje z wartości podstawowej animowanej właściwości lub z danych wyjściowych animacji tworzenia do sumy tej wartości i wartości, która jest określona przez właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.  
  
 W poniższym przykładzie ustawiono tylko <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Właściwość <xref:System.Windows.Media.Animation.DoubleAnimation> na 300. Ponieważ w przykładzie nie określono wartości początkowej, <xref:System.Windows.Media.Animation.DoubleAnimation> używa wartości bazowej właściwości <xref:System.Windows.FrameworkElement.Width%2A>, 100, jako wartości początkowej. Wartość końcowa jest określana przez dodanie <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> wartości animacji 300 do wartości początkowej, 100:400. W efekcie <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Shapes.Rectangle> jest animowany od 100 do 400.  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### <a name="fromby"></a>Od/do  
 Po ustawieniu właściwości <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> animacji, animacja postępuje z wartości, która jest określona przez właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, do wartości, która jest określona przez sumę właściwości <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.  
  
 Poniższy przykład ustawia właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> <xref:System.Windows.Media.Animation.DoubleAnimation> na 50, a jej Właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> na 300. Wartość końcowa jest określana przez dodanie <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> wartości animacji 300 do wartości początkowej, 50:350. W efekcie <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Shapes.Rectangle> jest animowany od 50 do 350.  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### <a name="from"></a>Z  
 Gdy określisz tylko <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> wartość animacji, animacja postępuje z wartości, która jest określona przez właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, do podstawowej wartości właściwości, która jest animowana lub do danych wyjściowych animacji tworzenia.  
  
 W poniższym przykładzie ustawiono tylko <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> Właściwość <xref:System.Windows.Media.Animation.DoubleAnimation> na 50. Ponieważ nie określono wartości końcowej, <xref:System.Windows.Media.Animation.DoubleAnimation> używa wartości bazowej właściwości <xref:System.Windows.FrameworkElement.Width%2A>, 100, jako jej wartości końcowej. <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Shapes.Rectangle> jest animowany od 50 do podstawowej wartości właściwości <xref:System.Windows.FrameworkElement.Width%2A>, 100.  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### <a name="toby"></a>Do/według  
 W przypadku ustawienia właściwości <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> animacji Właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> jest ignorowana.  
  
<a name="otheranimationtypes"></a>   
## <a name="other-animation-types"></a>Inne typy animacji  
 Animacje z/do/według animacji nie są jedynym typem animacji, które [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapewnia: zawiera również animacje klatek kluczowych i animacje ścieżek.  
  
- Animacja klatek kluczowych jest animowana wraz z dowolnymi wartościami docelowymi opisanymi przy użyciu klatek kluczowych. Aby uzyskać więcej informacji, zobacz [Omówienie animacji klatek kluczowych](key-frame-animations-overview.md).  
  
- Animacja ścieżki generuje wartości wyjściowe z <xref:System.Windows.Media.PathGeometry>. Aby uzyskać więcej informacji, zobacz [Omówienie animacji ścieżki](path-animations-overview.md).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] również umożliwia tworzenie własnych niestandardowych typów animacji. Aby uzyskać więcej informacji, zobacz [Omówienie niestandardowych animacji](custom-animations-overview.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Animacja — przegląd](animation-overview.md)
- [Scenorysy — przegląd](storyboards-overview.md)
- [Animacje kluczowych klatek — przegląd](key-frame-animations-overview.md)
- [Animacje ścieżki — przegląd](path-animations-overview.md)
- [Niestandardowe animacje — przegląd](custom-animations-overview.md)
- [Przykładowe wartości docelowe od, do i według animacji](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/TargetValues)
