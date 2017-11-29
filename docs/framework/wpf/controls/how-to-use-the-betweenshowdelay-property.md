---
title: "Jak użyć właściwości BetweenShowDelay"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolTip control [WPF], BetweenShowDelay time property
- BetweenShowDelay time property [WPF]
ms.assetid: 984ea76d-f2a2-4326-a02e-f97ec3d036d6
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dca6dc7c6238ef4accc921818090237d17ce1cbd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-betweenshowdelay-property"></a><span data-ttu-id="69c8a-102">Jak użyć właściwości BetweenShowDelay</span><span class="sxs-lookup"><span data-stu-id="69c8a-102">How to: Use the BetweenShowDelay Property</span></span>
<span data-ttu-id="69c8a-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> czasu właściwości elementy ToolTip będą wyświetlane szybko — z opóźnieniem niewielkiego lub żadnego — po użytkownik przesuwa wskaźnik myszy z jednego tooltip bezpośrednio do innego.</span><span class="sxs-lookup"><span data-stu-id="69c8a-103">This example shows how to use the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> time property so that tooltips appear quickly—with little or no delay—when a user moves the mouse pointer from one tooltip directly to another.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69c8a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="69c8a-104">Example</span></span>  
 <span data-ttu-id="69c8a-105">W poniższym przykładzie <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> właściwość jest ustawiona na 1 sekundę (1000 milisekund) i <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> jest ustawiony na dwóch sekund (2000 MS) dla etykietek narzędzi obu <xref:System.Windows.Shapes.Ellipse> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="69c8a-105">In the following example, the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> property is set to one second (1000 milliseconds) and the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> is set to two seconds (2000 milliseconds) for the tooltips of both <xref:System.Windows.Shapes.Ellipse> controls.</span></span> <span data-ttu-id="69c8a-106">Wyświetl etykietki narzędzia dla jednego z wielokropek, a następnie przenieś wskaźnik myszy do innego elipsy w dwóch sekund i Wstrzymaj na nim, etykietka narzędzia drugi elipsy Wyświetla natychmiast.</span><span class="sxs-lookup"><span data-stu-id="69c8a-106">If you display the tooltip for one of the ellipses and then move the mouse pointer to another ellipse within two seconds and pause on it, the tooltip of the second ellipse displays immediately.</span></span>  
  
 <span data-ttu-id="69c8a-107">W jednym z następujących scenariuszy <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> ma zastosowanie, co powoduje, że etykietkę narzędzia dla drugiego elipsy oczekiwania przed wygląda na to:</span><span class="sxs-lookup"><span data-stu-id="69c8a-107">In either of the following scenarios, the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> applies, which causes the tooltip for the second ellipse to wait one second before it appears:</span></span>  
  
-   <span data-ttu-id="69c8a-108">Jeśli czas potrzebny do przenoszenia do drugiego przycisku jest więcej niż dwie sekundy.</span><span class="sxs-lookup"><span data-stu-id="69c8a-108">If the time it takes to move to the second button is more than two seconds.</span></span>  
  
-   <span data-ttu-id="69c8a-109">Jeśli element tooltip nie jest widoczny na początku przedział czasu dla pierwszego elipsy.</span><span class="sxs-lookup"><span data-stu-id="69c8a-109">If the tooltip is not visible at the beginning of the time interval for the first ellipse.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
[!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
## <a name="see-also"></a><span data-ttu-id="69c8a-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69c8a-110">See Also</span></span>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [<span data-ttu-id="69c8a-111">Tematy porad</span><span class="sxs-lookup"><span data-stu-id="69c8a-111">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)  
 [<span data-ttu-id="69c8a-112">ToolTip — omówienie</span><span class="sxs-lookup"><span data-stu-id="69c8a-112">ToolTip Overview</span></span>](../../../../docs/framework/wpf/controls/tooltip-overview.md)
