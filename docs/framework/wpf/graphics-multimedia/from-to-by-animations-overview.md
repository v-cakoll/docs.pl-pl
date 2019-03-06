---
title: Od do przez animacje — Przegląd
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], From/to/by
- From/to/by animation
ms.assetid: 516fce0a-e7f8-49b8-b018-53b3d409a8a3
ms.openlocfilehash: 40a37542d6151d05910bc033657d85c6a9f5483b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362763"
---
# <a name="fromtoby-animations-overview"></a>Przegląd Cechy animacji od/do/przez
W tym temacie opisano sposób użycia animacji od/do/przez animować właściwości zależności. Od/do/przez animację tworzy przejście między dwiema wartościami.  
  
<a name="prereq"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć, w tym temacie, należy się zapoznać z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcje animacji. Aby zapoznać się z wprowadzeniem do funkcji animacji, zobacz [Przegląd animacja](animation-overview.md).  
  
<a name="whatisanimation"></a>   
## <a name="what-is-a-fromtoby-animation"></a>Animacja od/do/przez co to jest?  
 Od/do/przez animacji jest typem <xref:System.Windows.Media.Animation.AnimationTimeline> tworząca przejścia między wartość początkową i końcową wartość. Ilość czasu, który trwa przejście jest określana przez <xref:System.Windows.Media.Animation.Timeline.Duration%2A> tej animacji.  
  
 Można zastosować od/do/przez animację z właściwością przy użyciu <xref:System.Windows.Media.Animation.Storyboard> w kodzie znaczników oraz kod lub przy użyciu <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> w kodzie. Można także użyć do tworzenia animacji From/To/By <xref:System.Windows.Media.Animation.AnimationClock> i zastosować je do co najmniej jednej właściwości. Aby uzyskać więcej informacji na temat różnych metod do zastosowania animacji, zobacz [Przegląd techniki animacji właściwości](property-animation-techniques-overview.md).  
  
 Animacje od/do/przez może mieć nie więcej niż dwóch wartości docelowych. Jeśli potrzebujesz animacji, który ma więcej niż dwóch wartości docelowych, należy użyć animacji kluczowych klatek. Animacja kluczowych klatek są opisane w [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md).  
  
<a name="animation_types"></a>   
## <a name="fromtoby-animation-types"></a>Typy animacji od/do/przez  
 Animacje generować wartości właściwości, dlatego są typy inną animację dla różnych typach właściwości. Aby animować właściwości, która przyjmuje <xref:System.Double>, takich jak <xref:System.Windows.FrameworkElement.Width%2A> właściwości elementu, użyj animacji, która tworzy <xref:System.Double> wartości. Aby animować właściwości, która przyjmuje <xref:System.Windows.Point>, użyj animacji, która tworzy <xref:System.Windows.Point> wartości i tak dalej.  
  
 Klasy animacji od/do/przez należą do <xref:System.Windows.Media.Animation> przestrzeni nazw i następująca Konwencja nazewnictwa:  
  
 *\<Typ >* `Animation`  
  
 Gdzie  *\<typ >* ma typ wartości, które animuje klasy.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia następujące od/do/przez animację klasy.  
  
|Typ właściwości|Odpowiednie od/do/przez klasy animacji|  
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
 Od/do/przez animację tworzy przejście między dwiema wartościami docelowego. Jest powszechne, aby określić wartość początkową (ustaw ją za pomocą <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości) i wartość końcową (ustaw ją za pomocą <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości). Jednak również można określić tylko wartości początkowej, wartości docelowej lub wartość przesunięcia. W takich przypadkach animacji uzyskuje brakuje wartości docelowej z właściwość, która jest jest animowany. Na poniższej liście opisano różne sposoby określania wartości docelowych animacji.  
  
-   **Wartość początkowa**  
  
     Użyj <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwość, jeśli chcesz jawnie określić wartości początkowej animacji. Możesz użyć <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości samodzielnie lub z <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> lub <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości. Jeśli określisz tylko <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwość, przejścia animacji z tę wartość do wartości bazowej właściwości animowany.  
  
-   **Wartość końcowa**  
  
     Aby określić wartość końcową animacji, użyj jej <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości. Jeśli używasz <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwość samodzielnie, animacji uzyskuje wartość początkową, właściwość, która jest jest animowany lub z danych wyjściowych inną animację, która jest stosowana do tej samej właściwości. Możesz użyć <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości wraz z <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwość, aby jawnie określić początkową i końcową wartością dla animacji.  
  
-   **Wartość przesunięcia**  
  
     <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Właściwość pozwala określić przesunięcie zamiast jawnego uruchamia się lub kończy wartości animacji. <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Właściwości animacji Określa, ile animacji zmienia wartość w czasie jego trwania. Możesz użyć <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości samodzielnie lub z <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości. Jeśli określisz tylko <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości animacji dodaje wartość przesunięcia do podstawowej wartości właściwości lub z danymi wyjściowymi inną animację.  
  
<a name="examples"></a>   
## <a name="using-fromtoby-values"></a>Przy użyciu wartości z/do/przez  
 W poniższych sekcjach opisano sposób użycia <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości razem lub oddzielnie.  
  
 Przykłady w tej sekcji każde użycie <xref:System.Windows.Media.Animation.DoubleAnimation>, który jest typem od/do/przez animację, aby animować <xref:System.Windows.FrameworkElement.Width%2A> właściwość <xref:System.Windows.Shapes.Rectangle> oznacza to 10 wysokiej pikselach niezależnych od urządzenia i 100 szerokiego pikselach niezależnych od urządzenia.  
  
 Mimo że w każdym przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimation>, od, do i przez właściwości wszystkich od/do/przez animacje zachowują się identycznie. Mimo że każda z tych przykładów używa <xref:System.Windows.Media.Animation.Storyboard>, można użyć animacji od/do/przez w inny sposób. Aby uzyskać więcej informacji, zobacz [Przegląd techniki animacji właściwości](property-animation-techniques-overview.md).  
  
### <a name="fromto"></a>Z i do  
 Po ustawieniu <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> ze sobą wartości w miarę animacji z wartości, który jest określony przez <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> wartość, która jest określona przez właściwość <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości.  
  
 Poniższy przykład ustawia <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwość <xref:System.Windows.Media.Animation.DoubleAnimation> 50 i jego <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości do 300. W rezultacie <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> jest animowany od 50 do 300.  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### <a name="to"></a>Zadanie  
 Po ustawieniu wartości po prostu <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwość, animacji w miarę od wartości bazowej animowany właściwości lub z danych wyjściowych, tworzenie animacji, która wcześniej została zastosowana do tej samej właściwości wartość, która jest określona przez <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> Właściwość.  
  
 ("Tworzenie animacji" odnosi się do <xref:System.Windows.Media.Animation.ClockState.Active> lub <xref:System.Windows.Media.Animation.ClockState.Filling> animacji, które wcześniej zostały zastosowane do tej samej właściwości, która jest nadal obowiązują, gdy zastosowano bieżącej animacji przy użyciu <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> zachowanie dotyczące przekazania.)  
  
 W poniższym przykładzie ustawiono po prostu <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwość <xref:System.Windows.Media.Animation.DoubleAnimation> 300. Ponieważ została określona żadna wartość początkową, <xref:System.Windows.Media.Animation.DoubleAnimation> używa podstawowej wartości (100) <xref:System.Windows.FrameworkElement.Width%2A> właściwość jako jego wartość początkową. <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> jest animowany od 100 do wartości docelowej animacji 300.  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### <a name="by"></a>Od  
 Po ustawieniu wartości po prostu <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości animacji, animacji w miarę z podstawową wartość właściwość, która jest jest animowany lub z danych wyjściowych, tworzenie animacji do sumy tej wartości i wartości, który jest określony przez <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Właściwość.  
  
 W poniższym przykładzie ustawiono po prostu <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwość <xref:System.Windows.Media.Animation.DoubleAnimation> 300. Ponieważ przykładu nie określa wartość początkową <xref:System.Windows.Media.Animation.DoubleAnimation> używa wartości bazowej <xref:System.Windows.FrameworkElement.Width%2A> właściwość, 100, jako jego wartość początkową. Wartość końcowa jest ustalany przez dodanie <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> wartości animacji, 300, jego wartość początkową 100: 400. W rezultacie <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> jest animowany od 100 do 400.  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### <a name="fromby"></a>Od/przez  
 Po ustawieniu <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości animacji, w miarę animacji z wartości, który jest określony przez <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości na wartość, która jest określona przez sumę <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości.  
  
 Poniższy przykład ustawia <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwość <xref:System.Windows.Media.Animation.DoubleAnimation> 50 i jego <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości do 300. Wartość końcowa jest ustalany przez dodanie <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> wartości animacji, 300, jego wartość początkową 50: 350. W rezultacie <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> jest animowany od 50 do 350.  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### <a name="from"></a>Z  
 Po określeniu się po prostu <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> wartości animacji, w miarę animacji z wartości, który jest określony przez <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości do podstawowej wartości właściwości, która jest jest animowany lub z danymi wyjściowymi Tworzenie animacji.  
  
 W poniższym przykładzie ustawiono po prostu <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwość <xref:System.Windows.Media.Animation.DoubleAnimation> do 50. Ponieważ została określona żadna wartość końcową, <xref:System.Windows.Media.Animation.DoubleAnimation> używa wartości bazowej <xref:System.Windows.FrameworkElement.Width%2A> właściwość, 100, jako jego wartość końcową. <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> jest animowany od 50 do podstawowej wartości <xref:System.Windows.FrameworkElement.Width%2A> właściwości 100.  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### <a name="toby"></a>Do/przez  
 Jeśli ustawisz zarówno <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości animacji, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwość jest ignorowana.  
  
<a name="otheranimationtypes"></a>   
## <a name="other-animation-types"></a>Inne typy animacji  
 Animacje od/do/przez nie są jedynym typem animacji, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia: zapewnia również animacjach kluczowych ramek i animacje ścieżki.  
  
-   Animacja kluczowych klatek animuje wzdłuż dowolną liczbę wartości docelowej, oznaczone przy użyciu klatek kluczowych. Aby uzyskać więcej informacji, zobacz [Przegląd Animacja kluczowych klatek](key-frame-animations-overview.md).  
  
-   Animacja ścieżki generuje wartości wyjściowe z <xref:System.Windows.Media.PathGeometry>. Aby uzyskać więcej informacji, zobacz [animacje ścieżki — Przegląd](path-animations-overview.md).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Umożliwia również tworzenie własnych typów animacji niestandardowej. Aby uzyskać więcej informacji, zobacz [niestandardowe animacje — Przegląd](custom-animations-overview.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Animacja — przegląd](animation-overview.md)
- [Scenorysy — przegląd](storyboards-overview.md)
- [Animacje kluczowych klatek — przegląd](key-frame-animations-overview.md)
- [Animacje ścieżki — przegląd](path-animations-overview.md)
- [Niestandardowe animacje — przegląd](custom-animations-overview.md)
- [Od, do i przez przykład wartości docelowej animacji](https://go.microsoft.com/fwlink/?LinkID=159988)
