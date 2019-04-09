---
title: 'Instrukcje: Wyzwalanie animacji w przypadku zmiany wartości właściwości'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], starting when property values change
- triggering animation [WPF]
- Storyboards [WPF], starting when property values change
ms.assetid: 12399c21-0300-4f4f-9e3a-d92d9907e5f5
ms.openlocfilehash: 7e3eecedf7d464eeb8e4f60f2f05fa06d2e23e09
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080712"
---
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a>Instrukcje: Wyzwalanie animacji w przypadku zmiany wartości właściwości
W tym przykładzie pokazano, jak używać <xref:System.Windows.Trigger> można uruchomić <xref:System.Windows.Media.Animation.Storyboard> podczas zmiany wartości właściwości. Możesz użyć <xref:System.Windows.Trigger> wewnątrz <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, lub <xref:System.Windows.DataTemplate>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Trigger> animować <xref:System.Windows.UIElement.Opacity%2A> z <xref:System.Windows.Controls.Button> podczas jego <xref:System.Windows.UIElement.IsMouseOver%2A> staje się właściwość `true`.  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 Animacje stosowane przez właściwość <xref:System.Windows.Trigger> obiekty zachowują się w sposób bardziej skomplikowane niż <xref:System.Windows.EventTrigger> animacji lub animacje pracę, przy użyciu <xref:System.Windows.Media.Animation.Storyboard> metody.  One "przekazywanie" z animacjami zdefiniowane przez inne <xref:System.Windows.Trigger> obiektów, ale narzędzia compose z <xref:System.Windows.EventTrigger> i animacje wyzwalane przez metodę.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Trigger>
- [Przegląd Techniki animacji właściwości](property-animation-techniques-overview.md)
- [Przegląd Scenorysy](storyboards-overview.md)
