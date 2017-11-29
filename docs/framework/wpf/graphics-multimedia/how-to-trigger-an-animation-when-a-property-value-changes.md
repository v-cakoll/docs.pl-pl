---
title: "Jak wyzwolić animację kiedy ulega zmianie wartość właściwości"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], starting when property values change
- triggering animation [WPF]
- Storyboards [WPF], starting when property values change
ms.assetid: 12399c21-0300-4f4f-9e3a-d92d9907e5f5
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4d722be0f0367f7e6e98ef1c8451ce58ee28fedd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a><span data-ttu-id="d02f6-102">Jak wyzwolić animację kiedy ulega zmianie wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="d02f6-102">How to: Trigger an Animation When a Property Value Changes</span></span>
<span data-ttu-id="d02f6-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Trigger> uruchomić <xref:System.Windows.Media.Animation.Storyboard> podczas zmiany wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="d02f6-103">This example shows how to use a <xref:System.Windows.Trigger> to start a <xref:System.Windows.Media.Animation.Storyboard> when a property value changes.</span></span> <span data-ttu-id="d02f6-104">Można użyć <xref:System.Windows.Trigger> wewnątrz <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, lub <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="d02f6-104">You can use a <xref:System.Windows.Trigger> inside a <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, or <xref:System.Windows.DataTemplate>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d02f6-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="d02f6-105">Example</span></span>  
 <span data-ttu-id="d02f6-106">W poniższym przykładzie użyto <xref:System.Windows.Trigger> do animowania <xref:System.Windows.UIElement.Opacity%2A> z <xref:System.Windows.Controls.Button> po jego <xref:System.Windows.UIElement.IsMouseOver%2A> staje się właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="d02f6-106">The following example uses a <xref:System.Windows.Trigger> to animate the <xref:System.Windows.UIElement.Opacity%2A> of a <xref:System.Windows.Controls.Button> when its <xref:System.Windows.UIElement.IsMouseOver%2A> property becomes `true`.</span></span>  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 <span data-ttu-id="d02f6-107">Animacje zastosowane przez właściwość <xref:System.Windows.Trigger> obiekty zachowują się w sposób bardziej złożone niż <xref:System.Windows.EventTrigger> animacje lub animacje uruchomić za pomocą <xref:System.Windows.Media.Animation.Storyboard> metod.</span><span class="sxs-lookup"><span data-stu-id="d02f6-107">Animations applied by property <xref:System.Windows.Trigger> objects behave in a more complex fashion than <xref:System.Windows.EventTrigger> animations or animations started using <xref:System.Windows.Media.Animation.Storyboard> methods.</span></span>  <span data-ttu-id="d02f6-108">Ich "przekazaniem" animacji zdefiniowany przez inne <xref:System.Windows.Trigger> obiektów, ale tworzą z <xref:System.Windows.EventTrigger> i animacje wyzwalane metody.</span><span class="sxs-lookup"><span data-stu-id="d02f6-108">They "handoff" with animations defined by other <xref:System.Windows.Trigger> objects, but compose with <xref:System.Windows.EventTrigger> and method-triggered animations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d02f6-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d02f6-109">See Also</span></span>  
 <xref:System.Windows.Trigger>  
 [<span data-ttu-id="d02f6-110">Omówienie techniki animacji właściwość</span><span class="sxs-lookup"><span data-stu-id="d02f6-110">Property Animation Techniques Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [<span data-ttu-id="d02f6-111">Scenorys — omówienie</span><span class="sxs-lookup"><span data-stu-id="d02f6-111">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
