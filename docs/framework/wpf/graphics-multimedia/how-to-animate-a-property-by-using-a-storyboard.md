---
title: Jak animować właściwości przy użyciu scenorysu
description: Enliven interfejs użytkownika, używając animacji i scenorysów dla właściwości w Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], Storyboards
- Storyboards [WPF], animation
ms.assetid: f4a314e9-1da2-4367-85fc-1232487efa7a
ms.openlocfilehash: f21b606751b845905a7bde6d3a7658b214369cc6
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853741"
---
# <a name="how-to-animate-a-property-by-using-a-storyboard"></a>Jak animować właściwości przy użyciu scenorysu
Ten przykład pokazuje, jak używać <xref:System.Windows.Media.Animation.Storyboard> do animowania właściwości. Aby animować właściwość przy użyciu <xref:System.Windows.Media.Animation.Storyboard> , Utwórz animację dla każdej właściwości, którą chcesz animować, a także Utwórz, <xref:System.Windows.Media.Animation.Storyboard> aby zawierała animacje.  
  
 Typ właściwości określa typ animacji, która ma zostać użyta. Na przykład, aby animować właściwość, która pobiera <xref:System.Double> wartości, użyj <xref:System.Windows.Media.Animation.DoubleAnimation> . <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>I <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> dołączone właściwości określają obiekt i właściwość, do których zastosowano animację.  
  
 Aby rozpocząć scenorys w programie [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , należy użyć <xref:System.Windows.Media.Animation.BeginStoryboard> akcji i <xref:System.Windows.EventTrigger> . <xref:System.Windows.EventTrigger>Rozpoczyna akcję, <xref:System.Windows.Media.Animation.BeginStoryboard> gdy występuje zdarzenie określone za pomocą jego <xref:System.Windows.EventTrigger.RoutedEvent%2A> właściwości. <xref:System.Windows.Media.Animation.BeginStoryboard>Akcja uruchamia <xref:System.Windows.Media.Animation.Storyboard> .  
  
 Poniższy przykład używa <xref:System.Windows.Media.Animation.Storyboard> obiektów do animacji dwóch <xref:System.Windows.Controls.Button> kontrolek. Aby zmienić rozmiar pierwszego przycisku, <xref:System.Windows.FrameworkElement.Width%2A> jest on animowany. Aby zmienić kolor drugiego przycisku, <xref:System.Windows.Media.SolidColorBrush.Color%2A> Właściwość <xref:System.Windows.Media.SolidColorBrush> jest używana do ustawiania <xref:System.Windows.Controls.Control.Background%2A> animowanego przycisku.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[AnimatePropertyStoryboards#1](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
> Chociaż animacje mogą <xref:System.Windows.FrameworkElement> dotyczyć zarówno obiektu, jak i <xref:System.Windows.Controls.Control> , jak <xref:System.Windows.Controls.Panel> i <xref:System.Windows.Freezable> obiektu, takiego jak <xref:System.Windows.Media.Brush> lub <xref:System.Windows.Media.Transform> , tylko elementy struktury mają <xref:System.Windows.FrameworkElement.Name%2A> Właściwość. Aby przypisać nazwę do elementu Freezable, który może być celem animacji, użyj [dyrektywy x:Name](../../../desktop-wpf/xaml-services/xname-directive.md), jak pokazano w poprzednim przykładzie.  
  
 Jeśli używasz kodu, musisz utworzyć <xref:System.Windows.NameScope> dla a <xref:System.Windows.FrameworkElement> i zarejestrować nazwy obiektów, które mają być animowane <xref:System.Windows.FrameworkElement> . Aby uruchomić animacje w kodzie, użyj <xref:System.Windows.Media.Animation.BeginStoryboard> akcji z <xref:System.Windows.EventTrigger> . Opcjonalnie można użyć programu obsługi zdarzeń i <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody <xref:System.Windows.Media.Animation.Storyboard> . Poniższy przykład pokazuje, jak używać <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody.  
  
 [!code-csharp[AnimatePropertyStoryboards#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 Aby uzyskać więcej informacji na temat animacji i scenorysów, zobacz [Omówienie animacji](animation-overview.md).  
  
 Jeśli używasz kodu, nie możesz używać <xref:System.Windows.Media.Animation.Storyboard> obiektów w celu animowania właściwości. Aby uzyskać więcej informacji i przykładów, zobacz [Animuj a Property bez używania scenorysu](how-to-animate-a-property-without-using-a-storyboard.md) i [Animuj Właściwość za pomocą AnimationClock](how-to-animate-a-property-by-using-an-animationclock.md).
