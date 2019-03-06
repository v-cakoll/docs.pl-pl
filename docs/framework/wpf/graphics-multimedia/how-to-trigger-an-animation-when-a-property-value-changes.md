---
title: 'Instrukcje: Wyzwól animację kiedy ulega zmianie wartość właściwości'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], starting when property values change
- triggering animation [WPF]
- Storyboards [WPF], starting when property values change
ms.assetid: 12399c21-0300-4f4f-9e3a-d92d9907e5f5
ms.openlocfilehash: 87f7525755556301fec3f00da612fc5262f1f533
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356146"
---
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a>Instrukcje: Wyzwól animację kiedy ulega zmianie wartość właściwości
W tym przykładzie pokazano, jak używać <xref:System.Windows.Trigger> można uruchomić <xref:System.Windows.Media.Animation.Storyboard> podczas zmiany wartości właściwości. Możesz użyć <xref:System.Windows.Trigger> wewnątrz <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, lub <xref:System.Windows.DataTemplate>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Trigger> animować <xref:System.Windows.UIElement.Opacity%2A> z <xref:System.Windows.Controls.Button> podczas jego <xref:System.Windows.UIElement.IsMouseOver%2A> staje się właściwość `true`.  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 Animacje stosowane przez właściwość <xref:System.Windows.Trigger> obiekty zachowują się w sposób bardziej skomplikowane niż <xref:System.Windows.EventTrigger> animacji lub animacje pracę, przy użyciu <xref:System.Windows.Media.Animation.Storyboard> metody.  One "przekazywanie" z animacjami zdefiniowane przez inne <xref:System.Windows.Trigger> obiektów, ale narzędzia compose z <xref:System.Windows.EventTrigger> i animacje wyzwalane przez metodę.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Trigger>
- [Techniki animacji właściwości — przegląd](property-animation-techniques-overview.md)
- [Scenorysy — przegląd](storyboards-overview.md)
