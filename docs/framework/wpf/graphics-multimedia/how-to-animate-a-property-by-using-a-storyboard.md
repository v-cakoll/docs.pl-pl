---
title: Jak animować właściwości przy użyciu scenorysu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], Storyboards
- Storyboards [WPF], animation
ms.assetid: f4a314e9-1da2-4367-85fc-1232487efa7a
ms.openlocfilehash: 7e67fb07a05d474999515a678fd72ac6b96953c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-a-property-by-using-a-storyboard"></a>Jak animować właściwości przy użyciu scenorysu
Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.Animation.Storyboard> do animowania właściwości. Do animowania właściwości przy użyciu <xref:System.Windows.Media.Animation.Storyboard>, utworzyć animację dla każdej właściwości, która ma zostać animować, a także utworzyć <xref:System.Windows.Media.Animation.Storyboard> zawiera animacji.  
  
 Typ właściwości określa typ animacji do użycia. Na przykład w celu animowania właściwości, która przyjmuje <xref:System.Double> wartości, użyj <xref:System.Windows.Media.Animation.DoubleAnimation>. <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> i <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> określ dołączone właściwości obiektu i właściwości, do którego zastosowano animacji.  
  
 Aby uruchomić scenorysu w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], użyj <xref:System.Windows.Media.Animation.BeginStoryboard> akcji i <xref:System.Windows.EventTrigger>. <xref:System.Windows.EventTrigger> Rozpoczyna się <xref:System.Windows.Media.Animation.BeginStoryboard> akcji, gdy zdarzenie jest określony przez jego <xref:System.Windows.EventTrigger.RoutedEvent%2A> właściwość występuje. <xref:System.Windows.Media.Animation.BeginStoryboard> Uruchamia akcji <xref:System.Windows.Media.Animation.Storyboard>.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.Storyboard> obiektów do animowania dwa <xref:System.Windows.Controls.Button> kontrolki. Aby wprowadzić zmiany w rozmiarze przycisku pierwszej jego <xref:System.Windows.FrameworkElement.Width%2A> jest animowany. Aby przycisk drugi kolor, <xref:System.Windows.Media.SolidColorBrush.Color%2A> właściwość <xref:System.Windows.Media.SolidColorBrush> służy do ustawiania <xref:System.Windows.Controls.Control.Background%2A> przycisku, który jest animowany.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[AnimatePropertyStoryboards#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
>  Mimo że oba celem może być animacje <xref:System.Windows.FrameworkElement> obiektów, takich jak <xref:System.Windows.Controls.Control> lub <xref:System.Windows.Controls.Panel>, a <xref:System.Windows.Freezable> obiektów, takich jak <xref:System.Windows.Media.Brush> lub <xref:System.Windows.Media.Transform>, mieć tylko elementy framework <xref:System.Windows.FrameworkElement.Name%2A> właściwości. Aby przypisać nazwę do obiektu freezable, dzięki czemu mogą być objęci animacji, należy użyć [x: Name — dyrektywa](../../../../docs/framework/xaml-services/x-name-directive.md), tak jak w poprzednim przykładzie.  
  
 Jeśli używasz kodu, należy utworzyć <xref:System.Windows.NameScope> dla <xref:System.Windows.FrameworkElement> i zarejestrować nazwy obiektów do animowania z tym <xref:System.Windows.FrameworkElement>. Aby uruchomić animacji w kodzie, użyj <xref:System.Windows.Media.Animation.BeginStoryboard> akcji o <xref:System.Windows.EventTrigger>. Opcjonalnie można użyć programu obsługi zdarzeń i <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody <xref:System.Windows.Media.Animation.Storyboard>. Poniższy przykład przedstawia użycie <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody.  
  
 [!code-csharp[AnimatePropertyStoryboards#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 Aby uzyskać więcej informacji na temat animacji i scenorys, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 W przypadku użycia kodu nie są ograniczone do przy użyciu <xref:System.Windows.Media.Animation.Storyboard> obiektów w celu animowania właściwości. Aby uzyskać dodatkowe informacje i przykłady, zobacz [animowania właściwości bez Using scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md) i [animować właściwości przy użyciu AnimationClock](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-an-animationclock.md).
