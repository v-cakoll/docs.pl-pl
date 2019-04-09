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
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a><span data-ttu-id="33c1c-102">Instrukcje: Wyzwalanie animacji w przypadku zmiany wartości właściwości</span><span class="sxs-lookup"><span data-stu-id="33c1c-102">How to: Trigger an Animation When a Property Value Changes</span></span>
<span data-ttu-id="33c1c-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Trigger> można uruchomić <xref:System.Windows.Media.Animation.Storyboard> podczas zmiany wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="33c1c-103">This example shows how to use a <xref:System.Windows.Trigger> to start a <xref:System.Windows.Media.Animation.Storyboard> when a property value changes.</span></span> <span data-ttu-id="33c1c-104">Możesz użyć <xref:System.Windows.Trigger> wewnątrz <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, lub <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="33c1c-104">You can use a <xref:System.Windows.Trigger> inside a <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, or <xref:System.Windows.DataTemplate>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33c1c-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="33c1c-105">Example</span></span>  
 <span data-ttu-id="33c1c-106">W poniższym przykładzie użyto <xref:System.Windows.Trigger> animować <xref:System.Windows.UIElement.Opacity%2A> z <xref:System.Windows.Controls.Button> podczas jego <xref:System.Windows.UIElement.IsMouseOver%2A> staje się właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="33c1c-106">The following example uses a <xref:System.Windows.Trigger> to animate the <xref:System.Windows.UIElement.Opacity%2A> of a <xref:System.Windows.Controls.Button> when its <xref:System.Windows.UIElement.IsMouseOver%2A> property becomes `true`.</span></span>  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 <span data-ttu-id="33c1c-107">Animacje stosowane przez właściwość <xref:System.Windows.Trigger> obiekty zachowują się w sposób bardziej skomplikowane niż <xref:System.Windows.EventTrigger> animacji lub animacje pracę, przy użyciu <xref:System.Windows.Media.Animation.Storyboard> metody.</span><span class="sxs-lookup"><span data-stu-id="33c1c-107">Animations applied by property <xref:System.Windows.Trigger> objects behave in a more complex fashion than <xref:System.Windows.EventTrigger> animations or animations started using <xref:System.Windows.Media.Animation.Storyboard> methods.</span></span>  <span data-ttu-id="33c1c-108">One "przekazywanie" z animacjami zdefiniowane przez inne <xref:System.Windows.Trigger> obiektów, ale narzędzia compose z <xref:System.Windows.EventTrigger> i animacje wyzwalane przez metodę.</span><span class="sxs-lookup"><span data-stu-id="33c1c-108">They "handoff" with animations defined by other <xref:System.Windows.Trigger> objects, but compose with <xref:System.Windows.EventTrigger> and method-triggered animations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33c1c-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33c1c-109">See also</span></span>

- <xref:System.Windows.Trigger>
- [<span data-ttu-id="33c1c-110">Przegląd Techniki animacji właściwości</span><span class="sxs-lookup"><span data-stu-id="33c1c-110">Property Animation Techniques Overview</span></span>](property-animation-techniques-overview.md)
- [<span data-ttu-id="33c1c-111">Przegląd Scenorysy</span><span class="sxs-lookup"><span data-stu-id="33c1c-111">Storyboards Overview</span></span>](storyboards-overview.md)
