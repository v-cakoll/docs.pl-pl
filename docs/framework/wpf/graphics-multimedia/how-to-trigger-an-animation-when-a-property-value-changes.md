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
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a><span data-ttu-id="23f7d-102">Instrukcje: Wyzwól animację kiedy ulega zmianie wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="23f7d-102">How to: Trigger an Animation When a Property Value Changes</span></span>
<span data-ttu-id="23f7d-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Trigger> można uruchomić <xref:System.Windows.Media.Animation.Storyboard> podczas zmiany wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="23f7d-103">This example shows how to use a <xref:System.Windows.Trigger> to start a <xref:System.Windows.Media.Animation.Storyboard> when a property value changes.</span></span> <span data-ttu-id="23f7d-104">Możesz użyć <xref:System.Windows.Trigger> wewnątrz <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, lub <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="23f7d-104">You can use a <xref:System.Windows.Trigger> inside a <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, or <xref:System.Windows.DataTemplate>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23f7d-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="23f7d-105">Example</span></span>  
 <span data-ttu-id="23f7d-106">W poniższym przykładzie użyto <xref:System.Windows.Trigger> animować <xref:System.Windows.UIElement.Opacity%2A> z <xref:System.Windows.Controls.Button> podczas jego <xref:System.Windows.UIElement.IsMouseOver%2A> staje się właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="23f7d-106">The following example uses a <xref:System.Windows.Trigger> to animate the <xref:System.Windows.UIElement.Opacity%2A> of a <xref:System.Windows.Controls.Button> when its <xref:System.Windows.UIElement.IsMouseOver%2A> property becomes `true`.</span></span>  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 <span data-ttu-id="23f7d-107">Animacje stosowane przez właściwość <xref:System.Windows.Trigger> obiekty zachowują się w sposób bardziej skomplikowane niż <xref:System.Windows.EventTrigger> animacji lub animacje pracę, przy użyciu <xref:System.Windows.Media.Animation.Storyboard> metody.</span><span class="sxs-lookup"><span data-stu-id="23f7d-107">Animations applied by property <xref:System.Windows.Trigger> objects behave in a more complex fashion than <xref:System.Windows.EventTrigger> animations or animations started using <xref:System.Windows.Media.Animation.Storyboard> methods.</span></span>  <span data-ttu-id="23f7d-108">One "przekazywanie" z animacjami zdefiniowane przez inne <xref:System.Windows.Trigger> obiektów, ale narzędzia compose z <xref:System.Windows.EventTrigger> i animacje wyzwalane przez metodę.</span><span class="sxs-lookup"><span data-stu-id="23f7d-108">They "handoff" with animations defined by other <xref:System.Windows.Trigger> objects, but compose with <xref:System.Windows.EventTrigger> and method-triggered animations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23f7d-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23f7d-109">See also</span></span>
- <xref:System.Windows.Trigger>
- [<span data-ttu-id="23f7d-110">Techniki animacji właściwości — przegląd</span><span class="sxs-lookup"><span data-stu-id="23f7d-110">Property Animation Techniques Overview</span></span>](property-animation-techniques-overview.md)
- [<span data-ttu-id="23f7d-111">Scenorysy — przegląd</span><span class="sxs-lookup"><span data-stu-id="23f7d-111">Storyboards Overview</span></span>](storyboards-overview.md)
