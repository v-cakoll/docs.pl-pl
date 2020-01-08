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
ms.openlocfilehash: 6cfce9a5b070a23ed9ac03473888bf572b61393b
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559641"
---
# <a name="how-to-animate-a-property-by-using-a-storyboard"></a>Jak animować właściwości przy użyciu scenorysu
Ten przykład pokazuje, jak używać <xref:System.Windows.Media.Animation.Storyboard> do animowania właściwości. Aby animować właściwość przy użyciu <xref:System.Windows.Media.Animation.Storyboard>, należy utworzyć animację dla każdej właściwości, którą chcesz animować, a także utworzyć <xref:System.Windows.Media.Animation.Storyboard>, która będzie zawierać animacje.  
  
 Typ właściwości określa typ animacji, która ma zostać użyta. Na przykład, aby animować właściwość, która pobiera <xref:System.Double> wartości, użyj <xref:System.Windows.Media.Animation.DoubleAnimation>. <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> i <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> dołączone właściwości określają obiekt i właściwość, do których zastosowano animację.  
  
 Aby rozpocząć scenorys w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], użyj akcji <xref:System.Windows.Media.Animation.BeginStoryboard> i <xref:System.Windows.EventTrigger>. <xref:System.Windows.EventTrigger> rozpoczyna akcję <xref:System.Windows.Media.Animation.BeginStoryboard>, gdy występuje zdarzenie określone przez jego właściwość <xref:System.Windows.EventTrigger.RoutedEvent%2A>. Akcja <xref:System.Windows.Media.Animation.BeginStoryboard> uruchamia <xref:System.Windows.Media.Animation.Storyboard>.  
  
 Poniższy przykład używa obiektów <xref:System.Windows.Media.Animation.Storyboard>, aby animować dwa <xref:System.Windows.Controls.Button> kontrolki. Aby zmienić rozmiar pierwszego przycisku, jego <xref:System.Windows.FrameworkElement.Width%2A> jest animowany. Aby zmienić kolor drugiego przycisku, właściwość <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> służy do ustawiania <xref:System.Windows.Controls.Control.Background%2A> animowanego przycisku.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[AnimatePropertyStoryboards#1](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
> Chociaż animacje mogą wskazywać zarówno obiekt <xref:System.Windows.FrameworkElement>, jak <xref:System.Windows.Controls.Control> lub <xref:System.Windows.Controls.Panel>, a obiekt <xref:System.Windows.Freezable>, taki jak <xref:System.Windows.Media.Brush> lub <xref:System.Windows.Media.Transform>, tylko elementy struktury mają właściwość <xref:System.Windows.FrameworkElement.Name%2A>. Aby przypisać nazwę do elementu Freezable, który może być celem animacji, użyj [dyrektywy x:Name](../../../desktop-wpf/xaml-services/xname-directive.md), jak pokazano w poprzednim przykładzie.  
  
 Jeśli używasz kodu, musisz utworzyć <xref:System.Windows.NameScope> dla <xref:System.Windows.FrameworkElement> i zarejestrować nazwy obiektów do animacji przy użyciu tego <xref:System.Windows.FrameworkElement>. Aby uruchomić animacje w kodzie, użyj akcji <xref:System.Windows.Media.Animation.BeginStoryboard> z <xref:System.Windows.EventTrigger>. Opcjonalnie można użyć programu obsługi zdarzeń i metody <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> <xref:System.Windows.Media.Animation.Storyboard>. Poniższy przykład pokazuje, jak używać metody <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>.  
  
 [!code-csharp[AnimatePropertyStoryboards#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 Aby uzyskać więcej informacji na temat animacji i scenorysów, zobacz [Omówienie animacji](animation-overview.md).  
  
 Jeśli używasz kodu, nie możesz używać <xref:System.Windows.Media.Animation.Storyboard> obiektów w celu animowania właściwości. Aby uzyskać więcej informacji i przykładów, zobacz [Animuj a Property bez używania scenorysu](how-to-animate-a-property-without-using-a-storyboard.md) i [Animuj Właściwość za pomocą AnimationClock](how-to-animate-a-property-by-using-an-animationclock.md).
