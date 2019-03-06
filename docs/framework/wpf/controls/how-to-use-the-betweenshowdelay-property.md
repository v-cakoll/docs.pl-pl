---
title: 'Instrukcje: Użyj właściwości BetweenShowDelay'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolTip control [WPF], BetweenShowDelay time property
- BetweenShowDelay time property [WPF]
ms.assetid: 984ea76d-f2a2-4326-a02e-f97ec3d036d6
ms.openlocfilehash: e0653fbcb8eb052b12be7344ffe239431b67a951
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370981"
---
# <a name="how-to-use-the-betweenshowdelay-property"></a><span data-ttu-id="eca5a-102">Instrukcje: Użyj właściwości BetweenShowDelay</span><span class="sxs-lookup"><span data-stu-id="eca5a-102">How to: Use the BetweenShowDelay Property</span></span>
<span data-ttu-id="eca5a-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> czasu właściwość tak, aby szybko są wyświetlane etykietki narzędzi — z opóźnieniem niewielkiego lub żadnego — gdy użytkownik przesuwa wskaźnik myszy z jednej etykietki narzędzia bezpośrednio do innego.</span><span class="sxs-lookup"><span data-stu-id="eca5a-103">This example shows how to use the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> time property so that tooltips appear quickly—with little or no delay—when a user moves the mouse pointer from one tooltip directly to another.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eca5a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="eca5a-104">Example</span></span>  
 <span data-ttu-id="eca5a-105">W poniższym przykładzie <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> właściwość jest ustawiona na sekundę (1000 milisekund) i <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> jest ustawiony na dwóch sekund (2000 MS) dla etykietki narzędzi w obu <xref:System.Windows.Shapes.Ellipse> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="eca5a-105">In the following example, the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> property is set to one second (1000 milliseconds) and the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> is set to two seconds (2000 milliseconds) for the tooltips of both <xref:System.Windows.Shapes.Ellipse> controls.</span></span> <span data-ttu-id="eca5a-106">Wyświetlić etykietkę narzędzia dla jednego z wielokropek, a następnie przenieś wskaźnik myszy do innego elipsę w ramach dwóch sekund i wstrzymania na nim, natychmiast wyświetla etykietkę narzędzia drugi elipsy.</span><span class="sxs-lookup"><span data-stu-id="eca5a-106">If you display the tooltip for one of the ellipses and then move the mouse pointer to another ellipse within two seconds and pause on it, the tooltip of the second ellipse displays immediately.</span></span>  
  
 <span data-ttu-id="eca5a-107">W jednym z następujących scenariuszy <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> ma zastosowanie, co powoduje, że etykietkę narzędzia dla drugiego ikonę wielokropka, aby czekać przed wygląda na to:</span><span class="sxs-lookup"><span data-stu-id="eca5a-107">In either of the following scenarios, the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> applies, which causes the tooltip for the second ellipse to wait one second before it appears:</span></span>  
  
-   <span data-ttu-id="eca5a-108">Jeśli czas wymagany na przeniesienie do drugiego przycisku jest więcej niż dwóch sekund.</span><span class="sxs-lookup"><span data-stu-id="eca5a-108">If the time it takes to move to the second button is more than two seconds.</span></span>  
  
-   <span data-ttu-id="eca5a-109">Jeśli etykietka narzędzia nie jest widoczny na początku przedział czasowy na potrzeby pierwszego elipsy.</span><span class="sxs-lookup"><span data-stu-id="eca5a-109">If the tooltip is not visible at the beginning of the time interval for the first ellipse.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
[!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
## <a name="see-also"></a><span data-ttu-id="eca5a-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eca5a-110">See also</span></span>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [<span data-ttu-id="eca5a-111">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="eca5a-111">How-to Topics</span></span>](tooltip-how-to-topics.md)
- [<span data-ttu-id="eca5a-112">ToolTip — omówienie</span><span class="sxs-lookup"><span data-stu-id="eca5a-112">ToolTip Overview</span></span>](tooltip-overview.md)
