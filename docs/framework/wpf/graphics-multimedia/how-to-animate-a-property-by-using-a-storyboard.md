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
ms.openlocfilehash: f6064368b4f5e4fa8324b4039d734d4430cd9174
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761211"
---
# <a name="how-to-animate-a-property-by-using-a-storyboard"></a>Instrukcje: Animowanie właściwości przy użyciu scenorysu
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.Animation.Storyboard> animować właściwości. Aby animować właściwość przy użyciu <xref:System.Windows.Media.Animation.Storyboard>, utworzyć animację dla każdej właściwości, który chcesz animować, a także utworzyć <xref:System.Windows.Media.Animation.Storyboard> zawierać animacji.  
  
 Typ właściwości określa typ animacji do użycia. Na przykład, aby animować właściwości, która przyjmuje <xref:System.Double> wartości, należy użyć <xref:System.Windows.Media.Animation.DoubleAnimation>. <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> i <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> dołączonych właściwości określają obiektu i właściwości, do którego zastosowano animacji.  
  
 Aby rozpocząć scenorysu w [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], użyj <xref:System.Windows.Media.Animation.BeginStoryboard> akcji i <xref:System.Windows.EventTrigger>. <xref:System.Windows.EventTrigger> Rozpoczyna się <xref:System.Windows.Media.Animation.BeginStoryboard> akcję, gdy zdarzenie jest określony przez jego <xref:System.Windows.EventTrigger.RoutedEvent%2A> właściwość występuje. <xref:System.Windows.Media.Animation.BeginStoryboard> Rozpoczyna się akcja <xref:System.Windows.Media.Animation.Storyboard>.  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.Storyboard> obiektów animować dwa <xref:System.Windows.Controls.Button> kontrolki. Aby pierwszy przycisk, zmienić rozmiar, jego <xref:System.Windows.FrameworkElement.Width%2A> jest animowany. Aby drugi przycisk, zmienić kolor, <xref:System.Windows.Media.SolidColorBrush.Color%2A> właściwość <xref:System.Windows.Media.SolidColorBrush> służy do ustawiania <xref:System.Windows.Controls.Control.Background%2A> przycisku, który jest animowany.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[AnimatePropertyStoryboards#1](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
>  Mimo że animacje mogą kierować zarówno <xref:System.Windows.FrameworkElement> obiektów, takich jak <xref:System.Windows.Controls.Control> lub <xref:System.Windows.Controls.Panel>i <xref:System.Windows.Freezable> obiektów, takich jak <xref:System.Windows.Media.Brush> lub <xref:System.Windows.Media.Transform>, tylko w ramach elementy mają <xref:System.Windows.FrameworkElement.Name%2A> właściwości. Aby przypisać nazwę do freezable, dzięki czemu może być kierowany przez animację, należy użyć [x: Name — dyrektywa](../../xaml-services/x-name-directive.md), jak pokazano w poprzednim przykładzie.  
  
 Jeśli używasz kodu, należy utworzyć <xref:System.Windows.NameScope> dla <xref:System.Windows.FrameworkElement> i Zarejestruj nazwy obiektów, aby animować z tym <xref:System.Windows.FrameworkElement>. Aby rozpocząć animacji w kodzie, użyj <xref:System.Windows.Media.Animation.BeginStoryboard> akcji z <xref:System.Windows.EventTrigger>. Opcjonalnie można użyć procedury obsługi zdarzeń i <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody <xref:System.Windows.Media.Animation.Storyboard>. Poniższy przykład pokazuje, jak używać <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody.  
  
 [!code-csharp[AnimatePropertyStoryboards#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 Aby uzyskać więcej informacji na temat animacji i scenorysów, zobacz [Przegląd animacja](animation-overview.md).  
  
 W przypadku użycia kodu nie są ograniczone do korzystania z <xref:System.Windows.Media.Animation.Storyboard> obiektów, aby animować właściwości. Aby uzyskać więcej informacji i przykładów, zobacz [animować właściwości bez użycia scenorysu](how-to-animate-a-property-without-using-a-storyboard.md) i [animować właściwość przy użyciu AnimationClock](how-to-animate-a-property-by-using-an-animationclock.md).
