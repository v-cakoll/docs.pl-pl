---
title: "Jak przyspieszyć lub zwolnić animację"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- decelerating animation [WPF]
- accelerating animation [WPF]
- animation [WPF], accelerating
- animation [WPF], decelerating
ms.assetid: 4f383b2c-f94d-4a4e-9a06-f56f5dae95f9
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f4820f312ca8d404123710321a9f45bff1545f10
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-accelerate-or-decelerate-an-animation"></a><span data-ttu-id="2ace0-102">Jak przyspieszyć lub zwolnić animację</span><span class="sxs-lookup"><span data-stu-id="2ace0-102">How to: Accelerate or Decelerate an Animation</span></span>
<span data-ttu-id="2ace0-103">W tym przykładzie pokazano, jak animacja przyspieszenia i zwalnia wraz z upływem czasu.</span><span class="sxs-lookup"><span data-stu-id="2ace0-103">This example demonstrates how to make an animation accelerate and decelerate over time.</span></span> <span data-ttu-id="2ace0-104">W poniższym przykładzie kilka prostokąty animowanych przez animacje z różnymi <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> i <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> ustawienia.</span><span class="sxs-lookup"><span data-stu-id="2ace0-104">In the following example, several rectangles are animated by animations with different <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> and <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ace0-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="2ace0-105">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AccelDecelExample.xaml#1)]  
  
 <span data-ttu-id="2ace0-106">W tym przykładzie kodu zostało pominięte.</span><span class="sxs-lookup"><span data-stu-id="2ace0-106">Code has been omitted from this example.</span></span> <span data-ttu-id="2ace0-107">Aby uzyskać kompletny kod, zobacz [przykład zachowania chronometrażu animacji](http://go.microsoft.com/fwlink/?LinkID=159970).</span><span class="sxs-lookup"><span data-stu-id="2ace0-107">For the complete code, see the [Animation Timing Behavior Sample](http://go.microsoft.com/fwlink/?LinkID=159970).</span></span>
