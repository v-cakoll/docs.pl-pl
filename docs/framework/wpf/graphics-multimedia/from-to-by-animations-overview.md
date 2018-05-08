---
title: Od do przez animacje — omówienie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], From/to/by
- From/to/by animation
ms.assetid: 516fce0a-e7f8-49b8-b018-53b3d409a8a3
ms.openlocfilehash: 3095ec2c6307faaaa8049f23fffb5909cb3042d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="fromtoby-animations-overview"></a>Przegląd Cechy animacji od/do/przez
W tym temacie opisano sposób korzystania z lub do/przez animacje do animowania właściwości zależności. From lub do/przez animację tworzy przejścia między dwiema wartościami.  
  
<a name="prereq"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zrozumieć, w tym temacie, należy się zapoznać z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcje animacji. Aby obejrzeć wprowadzenie do funkcji animacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="whatisanimation"></a>   
## <a name="what-is-a-fromtoby-animation"></a>Animacja z lub do/przez co to jest?  
 From lub do/przez animacji jest typem <xref:System.Windows.Media.Animation.AnimationTimeline> tworzącą przejścia między wartość początkową i końcową wartość. Ilość czasu, który przejścia wymagany do ukończenia jest określany przez <xref:System.Windows.Media.Animation.Timeline.Duration%2A> tego animacji.  
  
 Możesz zastosować From/do/przez animacji właściwość przy użyciu <xref:System.Windows.Media.Animation.Storyboard> w kodzie znaczników oraz kod lub za pomocą <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> w kodzie. Można także użyć do utworzenia animacji From/To/By <xref:System.Windows.Media.Animation.AnimationClock> i zastosować je do co najmniej jednej właściwości. Aby uzyskać więcej informacji na temat różnych metod do zastosowania animacji, zobacz [— Przegląd właściwości animacji techniki](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
 Z lub do/przez animacje może mieć nie więcej niż dwóch wartości docelowych. Jeśli potrzebujesz animacji, które ma więcej niż dwóch wartości docelowych, należy użyć animacji ramki klucza. Klucz poklatkowych są opisane w [klucza ramki animacji omówienie](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
<a name="animation_types"></a>   
## <a name="fromtoby-animation-types"></a>Typy z lub do/przez animacji  
 Ponieważ animacje Generowanie wartości właściwości, istnieją typy innej animacji dla różnych typach właściwości. Aby animować właściwości, która przyjmuje <xref:System.Double>, takich jak <xref:System.Windows.FrameworkElement.Width%2A> właściwości elementu, użyj animacji tworzącego <xref:System.Double> wartości. Aby animować właściwości, która przyjmuje <xref:System.Windows.Point>, użyj animacji tworzącego <xref:System.Windows.Point> wartości i tak dalej.  
  
 Klasy z/do/przez animację należą do <xref:System.Windows.Media.Animation> przestrzeni nazw i korzystać z następującą konwencją nazewnictwa:  
  
 *\<Typ >* `Animation`  
  
 Gdzie  *\<typu >* jest typ wartości, które animuje klasy.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia następujące z lub do/przez animację klasy.  
  
|Typ właściwości|Odpowiednie z lub do/przez klasy animacji|  
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
## <a name="target-values"></a>Wartości docelowych  
 From lub do/przez animację tworzy przejście między dwóch wartości docelowych. Często, aby określić wartość początkową (ustaw go za pomocą <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości) i wartości końcowej (ustaw go za pomocą <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości). Jednak można dodawać tylko wartości początkowej, wartości docelowej lub wartość przesunięcia. W takich przypadkach animacji uzyskuje brakuje wartości docelowej z właściwości, która jest animowanej. Na poniższej liście opisano różne sposoby, aby określić wartości docelowe animacji.  
  
-   **Wartość początkowa**  
  
     Użyj <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości, jeśli chcesz jawnie określić wartości początkowej animacji. Można użyć <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości samodzielnie lub z <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> lub <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości. Jeśli określisz tylko <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości, przejść animacji z tę wartość do wartości podstawowej animowanej właściwości.  
  
-   **Wartość końcowa**  
  
     Aby określić wartości końcowej animacji, użyj jej <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości. Jeśli używasz <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości samodzielnie, animacji uzyskuje wartość początkową właściwość, która jest animowanej lub z danych wyjściowych innej animacji, która jest stosowana do tej samej właściwości. Można użyć <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości wraz z <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwość, aby jawnie określić początkową i końcową dla animacji.  
  
-   **Wartość przesunięcia**  
  
     <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Właściwość umożliwia określenie przesunięcia zamiast jawnego rozpoczęcia lub zakończenia wartość dla animacji. <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Określa właściwości animacji, o ile animacji zostanie zmieniona wartość w czasie jego trwania. Można użyć <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości samodzielnie lub z <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości. Jeśli określisz tylko <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości animacji, dodaje wartość przesunięcia podstawową wartość właściwości lub dane wyjściowe innej animacji.  
  
<a name="examples"></a>   
## <a name="using-fromtoby-values"></a>Używając wartości z lub do/przez  
 W poniższych sekcjach opisano sposób użycia <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości razem lub oddzielnie.  
  
 Przykłady w tej sekcji każdym użyciu <xref:System.Windows.Media.Animation.DoubleAnimation>, który jest typem z lub do/przez animacji, aby animować <xref:System.Windows.FrameworkElement.Width%2A> właściwość <xref:System.Windows.Shapes.Rectangle> czyli 10 wysokiej pikselach niezależnych od urządzenia i 100 szeroki pikselach niezależnych od urządzenia.  
  
 Mimo że w każdym przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimation>, do i przez właściwości wszystkich From lub do/przez animacje zachowują się tak samo. Mimo że każda z tych przykładów używa <xref:System.Windows.Media.Animation.Storyboard>, korzystając z lub do/przez animacje w inny sposób. Aby uzyskać więcej informacji, zobacz [— Przegląd właściwości animacji techniki](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
### <a name="fromto"></a>Z/na  
 Podczas ustawiania <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> wartości ze sobą, realizowany animacji z określonym przez wartość <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości na wartość określoną przez <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości.  
  
 W poniższym przykładzie <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwość <xref:System.Windows.Media.Animation.DoubleAnimation> 50 i jego <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości do 300. W związku z tym <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> jest animowany od 50 do 300.  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### <a name="to"></a>Do  
 Podczas ustawiania tylko <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwości, realizowany animacji z wartości podstawowej animowanej właściwości lub dane wyjściowe Tworzenie animacji, która wcześniej została zastosowana do tej samej właściwości określonym przez wartość <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> Właściwość.  
  
 ("Tworzenie animacji" odwołuje się do <xref:System.Windows.Media.Animation.ClockState.Active> lub <xref:System.Windows.Media.Animation.ClockState.Filling> animacji, które wcześniej zostały zastosowane do tej samej właściwości, która jest nadal obowiązują, gdy bieżący animacja została zastosowana za pomocą <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> zachowanie przekazaniem.)  
  
 Poniższy przykład przedstawia tylko <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> właściwość <xref:System.Windows.Media.Animation.DoubleAnimation> 300. Nie podano żadnej wartości początkowej, <xref:System.Windows.Media.Animation.DoubleAnimation> używa podstawowej wartości (w 100) <xref:System.Windows.FrameworkElement.Width%2A> właściwość jako jego wartość początkową. <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> jest animowany od 100 do wartości docelowej animacji 300.  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### <a name="by"></a>Przez  
 Podczas ustawiania tylko <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości animacji, realizowany animacji od wartości podstawowej animowanej jest właściwości lub z danych wyjściowych sumie tę wartość i wartość, która jest określona przez tworzenie animacji <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> Właściwość.  
  
 Poniższy przykład przedstawia tylko <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwość <xref:System.Windows.Media.Animation.DoubleAnimation> 300. Ponieważ przykładzie nie określa wartość początkową <xref:System.Windows.Media.Animation.DoubleAnimation> używa podstawowej wartości <xref:System.Windows.FrameworkElement.Width%2A> właściwość, 100, jako jego wartość początkową. Wartość końcowa jest ustalany przez dodanie <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> wartość animacji 300 na wartość początkową 100:400. W związku z tym <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> jest animowany od 100 do 400.  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### <a name="fromby"></a>Z lub przez  
 Podczas ustawiania <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości animacji, realizowany animacji z określonym przez wartość <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości na wartość określoną przez sumę <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości.  
  
 W poniższym przykładzie <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwość <xref:System.Windows.Media.Animation.DoubleAnimation> 50 i jego <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości do 300. Wartość końcowa jest ustalany przez dodanie <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> wartość animacji 300 na wartość początkową 50:350. W związku z tym <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> jest animowany od 50 do 350.  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### <a name="from"></a>Z  
 Po określeniu się tylko <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> wartość animacji, realizowany animacji z określonym przez wartość <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwości, do wartości podstawowej animowanej jest właściwości lub dane wyjściowe Tworzenie animacji.  
  
 Poniższy przykład przedstawia tylko <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> właściwość <xref:System.Windows.Media.Animation.DoubleAnimation> do 50. Nie podano żadnej wartości końcowej, <xref:System.Windows.Media.Animation.DoubleAnimation> używa podstawowej wartości <xref:System.Windows.FrameworkElement.Width%2A> właściwość, 100, jako jego wartości końcowej. <xref:System.Windows.FrameworkElement.Width%2A> z <xref:System.Windows.Shapes.Rectangle> jest animowany od 50 do wartości podstawowej <xref:System.Windows.FrameworkElement.Width%2A> właściwości, 100.  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### <a name="toby"></a>Aby/przez  
 Jeżeli wartość <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> i <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwości animacji <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> właściwość jest ignorowana.  
  
<a name="otheranimationtypes"></a>   
## <a name="other-animation-types"></a>Inne typy animacji  
 Z lub do/przez animacje nie są jedynym typem animacje który [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] udostępnia: zapewnia także klucz poklatkowych oraz ścieżki animacji.  
  
-   Animacja ramki klucza animuje wzdłuż dowolną liczbę wartości docelowe, oznaczone przy użyciu klucza ramki. Aby uzyskać więcej informacji, zobacz [klucza ramki animacji omówienie](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
-   Animacja ścieżki generuje dane wyjściowe wartości z <xref:System.Windows.Media.PathGeometry>. Aby uzyskać więcej informacji, zobacz [omówienie animacje ścieżki](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Umożliwia także tworzenie własnych typów animacji niestandardowej. Aby uzyskać więcej informacji, zobacz [omówienie animacji niestandardowej](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Animation.Timeline>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Scenorysy — przegląd](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Animacje kluczowych klatek — przegląd](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Animacje ścieżki — przegląd](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)  
 [Niestandardowe animacje — przegląd](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md)  
 [Z, aby i przykładowe wartości docelowej animacji](http://go.microsoft.com/fwlink/?LinkID=159988)
