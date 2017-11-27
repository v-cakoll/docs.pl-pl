---
title: "Jak obsłużyć załadowane zdarzenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], Loaded events
- events [WPF], Loaded
- Loaded events [WPF]
ms.assetid: 0cf8d003-8441-4df4-807a-6db09347e829
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 35376d3a759e326ae7de77657529c4bed5e38c37
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-a-loaded-event"></a><span data-ttu-id="cc256-102">Jak obsłużyć załadowane zdarzenie</span><span class="sxs-lookup"><span data-stu-id="cc256-102">How to: Handle a Loaded Event</span></span>
<span data-ttu-id="cc256-103">W tym przykładzie przedstawiono sposób obsługi <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> zdarzeń i odpowiednim scenariuszu obsługi tego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cc256-103">This example shows how to handle the <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> event, and an appropriate scenario for handling that event.</span></span> <span data-ttu-id="cc256-104">Tworzy program obsługi <xref:System.Windows.Controls.Button> załadowanie strony.</span><span class="sxs-lookup"><span data-stu-id="cc256-104">The handler  creates a <xref:System.Windows.Controls.Button> when the page loads.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc256-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="cc256-105">Example</span></span>  
 <span data-ttu-id="cc256-106">W poniższym przykładzie użyto [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] wraz z pliku CodeBehind.</span><span class="sxs-lookup"><span data-stu-id="cc256-106">The following example uses [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] together with a code-behind file.</span></span>  
  
 [!code-xaml[FELoaded#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FELoaded#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml.cs#handler)]
 [!code-vb[FELoaded#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FELoaded/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="cc256-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc256-107">See Also</span></span>  
 <xref:System.Windows.FrameworkElement>  
 [<span data-ttu-id="cc256-108">Zdarzenia okresu istnienia obiektu</span><span class="sxs-lookup"><span data-stu-id="cc256-108">Object Lifetime Events</span></span>](../../../../docs/framework/wpf/advanced/object-lifetime-events.md)  
 [<span data-ttu-id="cc256-109">Omówienie kierowane zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cc256-109">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="cc256-110">Tematy porad</span><span class="sxs-lookup"><span data-stu-id="cc256-110">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
