---
title: Jak obsłużyć załadowane zdarzenie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], Loaded events
- events [WPF], Loaded
- Loaded events [WPF]
ms.assetid: 0cf8d003-8441-4df4-807a-6db09347e829
ms.openlocfilehash: 6f3520fc3bc2a64d76083af415588ff819890eb9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544199"
---
# <a name="how-to-handle-a-loaded-event"></a><span data-ttu-id="d36db-102">Jak obsłużyć załadowane zdarzenie</span><span class="sxs-lookup"><span data-stu-id="d36db-102">How to: Handle a Loaded Event</span></span>
<span data-ttu-id="d36db-103">W tym przykładzie przedstawiono sposób obsługi <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> zdarzeń i odpowiednim scenariuszu obsługi tego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d36db-103">This example shows how to handle the <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> event, and an appropriate scenario for handling that event.</span></span> <span data-ttu-id="d36db-104">Tworzy program obsługi <xref:System.Windows.Controls.Button> załadowanie strony.</span><span class="sxs-lookup"><span data-stu-id="d36db-104">The handler  creates a <xref:System.Windows.Controls.Button> when the page loads.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d36db-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="d36db-105">Example</span></span>  
 <span data-ttu-id="d36db-106">W poniższym przykładzie użyto [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] wraz z pliku CodeBehind.</span><span class="sxs-lookup"><span data-stu-id="d36db-106">The following example uses [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] together with a code-behind file.</span></span>  
  
 [!code-xaml[FELoaded#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FELoaded#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml.cs#handler)]
 [!code-vb[FELoaded#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FELoaded/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="d36db-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d36db-107">See Also</span></span>  
 <xref:System.Windows.FrameworkElement>  
 [<span data-ttu-id="d36db-108">Zdarzenia okresu istnienia obiektu</span><span class="sxs-lookup"><span data-stu-id="d36db-108">Object Lifetime Events</span></span>](../../../../docs/framework/wpf/advanced/object-lifetime-events.md)  
 [<span data-ttu-id="d36db-109">Przegląd zdarzeń trasowanych</span><span class="sxs-lookup"><span data-stu-id="d36db-109">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="d36db-110">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="d36db-110">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
