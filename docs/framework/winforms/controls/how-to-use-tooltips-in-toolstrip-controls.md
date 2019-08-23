---
title: 'Instrukcje: użycie elementu ToolTips w kontrolkach ToolStrip'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
ms.openlocfilehash: 3f383b6cccba7825637ea65a0e13280b91b406c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939732"
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a><span data-ttu-id="90bd4-102">Instrukcje: użycie elementu ToolTips w kontrolkach ToolStrip</span><span class="sxs-lookup"><span data-stu-id="90bd4-102">How to: Use ToolTips in ToolStrip Controls</span></span>
<span data-ttu-id="90bd4-103">Możesz <xref:System.Windows.Forms.ToolTip> wyświetlić odpowiedni <xref:System.Windows.Forms.ToolStrip> formant, ustawiając <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> właściwość kontrolki na `true`.</span><span class="sxs-lookup"><span data-stu-id="90bd4-103">You can display a <xref:System.Windows.Forms.ToolTip> for the <xref:System.Windows.Forms.ToolStrip> control you want by setting the control's <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property to `true`.</span></span>  
  
### <a name="to-display-a-tooltip"></a><span data-ttu-id="90bd4-104">Aby wyświetlić etykietkę narzędzia</span><span class="sxs-lookup"><span data-stu-id="90bd4-104">To display a ToolTip</span></span>  
  
- <span data-ttu-id="90bd4-105">Ustaw właściwość formantu na `true`. <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A></span><span class="sxs-lookup"><span data-stu-id="90bd4-105">Set the <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property of the control to `true`.</span></span>  
  
     <span data-ttu-id="90bd4-106">Wartość <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> domyślna to `true`, <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> a wartość <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> domyślna to .`false`</span><span class="sxs-lookup"><span data-stu-id="90bd4-106">The default value of <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> is `true`, and the default value of <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> is `false`.</span></span>  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a><span data-ttu-id="90bd4-107">Aby użyć właściwości ToolTipText dla tekstu etykietki narzędzia element ToolStripButton</span><span class="sxs-lookup"><span data-stu-id="90bd4-107">To use the ToolTipText property for the ToolTip text of a ToolStripButton</span></span>  
  
1. <span data-ttu-id="90bd4-108">Ustaw właściwość przycisku na `true`. <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A></span><span class="sxs-lookup"><span data-stu-id="90bd4-108">Set the <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property of the button to `true`.</span></span>  
  
2. <span data-ttu-id="90bd4-109">Ustaw właściwość przycisku na `false`. <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="90bd4-109">Set the <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> property of the button to `false`.</span></span>  
  
     <span data-ttu-id="90bd4-110">`AutoToolTip` Właściwość jest `true` domyślnie dla <xref:System.Windows.Forms.ToolStripButton>, i<xref:System.Windows.Forms.ToolStripDropDownButton>. <xref:System.Windows.Forms.ToolStripSplitButton></span><span class="sxs-lookup"><span data-stu-id="90bd4-110">The `AutoToolTip` property is `true` by default for <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, and <xref:System.Windows.Forms.ToolStripSplitButton>.</span></span>  
  
     <span data-ttu-id="90bd4-111">A <xref:System.Windows.Forms.ToolStripButton> domyślnie używa `Text` swojej właściwości dla <xref:System.Windows.Forms.ToolTip> tekstu.</span><span class="sxs-lookup"><span data-stu-id="90bd4-111">A <xref:System.Windows.Forms.ToolStripButton> uses its `Text` property for the <xref:System.Windows.Forms.ToolTip> text by default.</span></span> <span data-ttu-id="90bd4-112">Użyj tej procedury, aby wyświetlić niestandardowy tekst w <xref:System.Windows.Forms.ToolStripButton>. <xref:System.Windows.Forms.ToolTip></span><span class="sxs-lookup"><span data-stu-id="90bd4-112">Use this procedure to display custom text in a <xref:System.Windows.Forms.ToolStripButton><xref:System.Windows.Forms.ToolTip>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="90bd4-113">Jeśli ustawisz <xref:System.Windows.Forms.ToolStripItemDisplayStyle> <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> opcję lub <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, na przycisku nie będzie wyświetlany tekst, ale etykietka narzędzia nadal pojawia się.</span><span class="sxs-lookup"><span data-stu-id="90bd4-113">If you set <xref:System.Windows.Forms.ToolStripItemDisplayStyle> to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, no text will appear on the button, but the tool tip still appears.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90bd4-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90bd4-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>
- <xref:System.Windows.Forms.ToolStripButton>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- <xref:System.Windows.Forms.ToolStripSplitButton>
- [<span data-ttu-id="90bd4-115">ToolStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="90bd4-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
