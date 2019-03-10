---
title: 'Instrukcje: Użycie elementu ToolTips w formantach ToolStrip'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
ms.openlocfilehash: 7177daef469f6c601cfa468c6437deb9653ffc85
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707472"
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a><span data-ttu-id="6e46b-102">Instrukcje: Użycie elementu ToolTips w formantach ToolStrip</span><span class="sxs-lookup"><span data-stu-id="6e46b-102">How to: Use ToolTips in ToolStrip Controls</span></span>
<span data-ttu-id="6e46b-103">Możesz wyświetlić <xref:System.Windows.Forms.ToolTip> dla <xref:System.Windows.Forms.ToolStrip> kontrolkę, która przez ustawienie jego <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="6e46b-103">You can display a <xref:System.Windows.Forms.ToolTip> for the <xref:System.Windows.Forms.ToolStrip> control you want by setting the control's <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property to `true`.</span></span>  
  
### <a name="to-display-a-tooltip"></a><span data-ttu-id="6e46b-104">Aby wyświetlić etykietkę narzędzia</span><span class="sxs-lookup"><span data-stu-id="6e46b-104">To display a ToolTip</span></span>  
  
-   <span data-ttu-id="6e46b-105">Ustaw <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> właściwości formantu, aby `true`.</span><span class="sxs-lookup"><span data-stu-id="6e46b-105">Set the <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property of the control to `true`.</span></span>  
  
     <span data-ttu-id="6e46b-106">Wartość domyślna <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> jest `true`i wartość domyślną <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> i <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> jest `false`.</span><span class="sxs-lookup"><span data-stu-id="6e46b-106">The default value of <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> is `true`, and the default value of <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> is `false`.</span></span>  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a><span data-ttu-id="6e46b-107">Aby użyć właściwości ToolTipText element ToolStripButton tekst etykietki narzędzia</span><span class="sxs-lookup"><span data-stu-id="6e46b-107">To use the ToolTipText property for the ToolTip text of a ToolStripButton</span></span>  
  
1.  <span data-ttu-id="6e46b-108">Ustaw <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> właściwości przycisku `true`.</span><span class="sxs-lookup"><span data-stu-id="6e46b-108">Set the <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> property of the button to `true`.</span></span>  
  
2.  <span data-ttu-id="6e46b-109">Ustaw <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> właściwości przycisku `false`.</span><span class="sxs-lookup"><span data-stu-id="6e46b-109">Set the <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> property of the button to `false`.</span></span>  
  
     <span data-ttu-id="6e46b-110">`AutoToolTip` Właściwość `true` domyślnie <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, i <xref:System.Windows.Forms.ToolStripSplitButton>.</span><span class="sxs-lookup"><span data-stu-id="6e46b-110">The `AutoToolTip` property is `true` by default for <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, and <xref:System.Windows.Forms.ToolStripSplitButton>.</span></span>  
  
     <span data-ttu-id="6e46b-111">A <xref:System.Windows.Forms.ToolStripButton> używa jej `Text` właściwość <xref:System.Windows.Forms.ToolTip> tekst domyślnie.</span><span class="sxs-lookup"><span data-stu-id="6e46b-111">A <xref:System.Windows.Forms.ToolStripButton> uses its `Text` property for the <xref:System.Windows.Forms.ToolTip> text by default.</span></span> <span data-ttu-id="6e46b-112">Użyj tej procedury, aby wyświetlić niestandardowy tekst w <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="6e46b-112">Use this procedure to display custom text in a <xref:System.Windows.Forms.ToolStripButton><xref:System.Windows.Forms.ToolTip>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e46b-113">Jeśli ustawisz <xref:System.Windows.Forms.ToolStripItemDisplayStyle> do <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> lub <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, nie jest wyświetlany tekst na przycisku, ale nadal pojawi się etykietka narzędzia.</span><span class="sxs-lookup"><span data-stu-id="6e46b-113">If you set <xref:System.Windows.Forms.ToolStripItemDisplayStyle> to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> or <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, no text will appear on the button, but the tool tip still appears.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e46b-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6e46b-114">See also</span></span>
- <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>
- <xref:System.Windows.Forms.ToolStripButton>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- <xref:System.Windows.Forms.ToolStripSplitButton>
- [<span data-ttu-id="6e46b-115">ToolStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="6e46b-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
