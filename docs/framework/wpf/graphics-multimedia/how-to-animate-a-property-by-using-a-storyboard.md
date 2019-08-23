---
title: 'Instrukcje: Animowanie właściwości przy użyciu scenorysu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], Storyboards
- Storyboards [WPF], animation
ms.assetid: f4a314e9-1da2-4367-85fc-1232487efa7a
ms.openlocfilehash: a7a2656d84d37d3e2726df009a07ccf29661df07
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963042"
---
# <a name="how-to-animate-a-property-by-using-a-storyboard"></a>Instrukcje: Animowanie właściwości przy użyciu scenorysu
Ten przykład pokazuje, <xref:System.Windows.Media.Animation.Storyboard> jak używać do animowania właściwości. Aby animować właściwość przy użyciu <xref:System.Windows.Media.Animation.Storyboard>, Utwórz animację dla każdej właściwości, którą chcesz animować, a także <xref:System.Windows.Media.Animation.Storyboard> Utwórz, aby zawierała animacje.  
  
 Typ właściwości określa typ animacji, która ma zostać użyta. Na przykład, aby animować właściwość, która pobiera <xref:System.Double> wartości, <xref:System.Windows.Media.Animation.DoubleAnimation>Użyj. <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> I<xref:System.Windows.Media.Animation.Storyboard.TargetProperty> dołączone właściwości określają obiekt i właściwość, do których zastosowano animację.  
  
 Aby rozpocząć scenorys w programie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], <xref:System.Windows.Media.Animation.BeginStoryboard> należy użyć akcji i <xref:System.Windows.EventTrigger>. Rozpoczyna akcję, gdy występuje zdarzenie określone za pomocą jego <xref:System.Windows.EventTrigger.RoutedEvent%2A> właściwości. <xref:System.Windows.Media.Animation.BeginStoryboard> <xref:System.Windows.EventTrigger> <xref:System.Windows.Media.Animation.BeginStoryboard> Akcja<xref:System.Windows.Media.Animation.Storyboard>uruchamia.  
  
 Poniższy przykład używa <xref:System.Windows.Media.Animation.Storyboard> obiektów do animacji dwóch <xref:System.Windows.Controls.Button> kontrolek. Aby zmienić rozmiar pierwszego przycisku, jest on <xref:System.Windows.FrameworkElement.Width%2A> animowany. Aby zmienić kolor drugiego przycisku, <xref:System.Windows.Media.SolidColorBrush.Color%2A> Właściwość <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Controls.Control.Background%2A> jest używana do ustawiania animowanego przycisku.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[AnimatePropertyStoryboards#1](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
> Chociaż animacje mogą dotyczyć zarówno <xref:System.Windows.FrameworkElement> obiektu, <xref:System.Windows.Controls.Control> jak <xref:System.Windows.Controls.Panel>i <xref:System.Windows.Media.Brush> , jak i <xref:System.Windows.Freezable> obiektu <xref:System.Windows.FrameworkElement.Name%2A> , takiego jak lub <xref:System.Windows.Media.Transform>, tylko elementy struktury mają właściwość. Aby przypisać nazwę do elementu Freezable, który może być celem animacji, użyj [dyrektywy x:Name](../../xaml-services/x-name-directive.md), jak pokazano w poprzednim przykładzie.  
  
 Jeśli używasz kodu, musisz utworzyć <xref:System.Windows.NameScope> <xref:System.Windows.FrameworkElement> dla a i zarejestrować nazwy obiektów, które <xref:System.Windows.FrameworkElement>mają być animowane. Aby uruchomić animacje w kodzie, użyj <xref:System.Windows.Media.Animation.BeginStoryboard> akcji <xref:System.Windows.EventTrigger>z. Opcjonalnie można użyć programu obsługi zdarzeń i <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> <xref:System.Windows.Media.Animation.Storyboard>metody. Poniższy przykład pokazuje, <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> jak używać metody.  
  
 [!code-csharp[AnimatePropertyStoryboards#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 Aby uzyskać więcej informacji na temat animacji i scenorysów, zobacz [Omówienie animacji](animation-overview.md).  
  
 Jeśli używasz kodu, nie możesz używać <xref:System.Windows.Media.Animation.Storyboard> obiektów w celu animowania właściwości. Aby uzyskać więcej informacji i przykładów, zobacz [Animuj a Property bez używania scenorysu](how-to-animate-a-property-without-using-a-storyboard.md) i [Animuj Właściwość za pomocą AnimationClock](how-to-animate-a-property-by-using-an-animationclock.md).
