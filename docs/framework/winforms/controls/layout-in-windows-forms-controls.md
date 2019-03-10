---
title: Układ w formantach formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms]
- sizing [Windows Forms], automatic [Windows Forms]
- Margin property [Windows Forms]
- Padding property [Windows Forms]
ms.assetid: 99400e3a-720e-4f56-b68f-89df911a251c
ms.openlocfilehash: d1a3954c8eda87bdda9fa17df1bd2b3858c43619
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711333"
---
# <a name="layout-in-windows-forms-controls"></a><span data-ttu-id="d04d4-102">Układ w formantach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d04d4-102">Layout in Windows Forms Controls</span></span>

<span data-ttu-id="d04d4-103">Rozmieszczenie kontrolek w formularzu jest wysoki priorytet dla wielu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d04d4-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="d04d4-104"><xref:System.Windows.Forms?displayProperty=nameWithType> Przestrzeń nazw udostępnia wiele narzędzi układu, w tym celu.</span><span class="sxs-lookup"><span data-stu-id="d04d4-104">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace gives you many layout tools to accomplish this.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d04d4-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d04d4-105">In This Section</span></span>

<span data-ttu-id="d04d4-106">[AutoSize — Przegląd właściwości](autosize-property-overview.md)\\</span><span class="sxs-lookup"><span data-stu-id="d04d4-106">[AutoSize Property Overview](autosize-property-overview.md)\\</span></span>
<span data-ttu-id="d04d4-107">W tym artykule opisano <xref:System.Windows.Forms.Control.AutoSize%2A> właściwość i swojej roli w układzie.</span><span class="sxs-lookup"><span data-stu-id="d04d4-107">Describes the <xref:System.Windows.Forms.Control.AutoSize%2A> property and its role in layout.</span></span>

<span data-ttu-id="d04d4-108">[Margines i wypełnienie w formularzach Windows Forms, formanty](margin-and-padding-in-windows-forms-controls.md)\\</span><span class="sxs-lookup"><span data-stu-id="d04d4-108">[Margin and Padding in Windows Forms Controls](margin-and-padding-in-windows-forms-controls.md)\\</span></span>
<span data-ttu-id="d04d4-109">W tym artykule opisano <xref:System.Windows.Forms.Control.Margin%2A> i <xref:System.Windows.Forms.Control.Padding%2A> właściwości i ich ról w układzie.</span><span class="sxs-lookup"><span data-stu-id="d04d4-109">Describes the <xref:System.Windows.Forms.Control.Margin%2A> and <xref:System.Windows.Forms.Control.Padding%2A> properties and their roles in layout.</span></span>

<span data-ttu-id="d04d4-110">[Instrukcje: Wyrównywanie formantu z krawędziami formularzy](how-to-align-a-control-to-the-edges-of-forms.md)\\</span><span class="sxs-lookup"><span data-stu-id="d04d4-110">[How to: Align a Control to the Edges of Forms](how-to-align-a-control-to-the-edges-of-forms.md)\\</span></span>
<span data-ttu-id="d04d4-111">Pokazuje sposób użycia <xref:System.Windows.Forms.Control.Dock%2A> właściwość wyrównywanie formantu do krawędzi formularza zajmuje.</span><span class="sxs-lookup"><span data-stu-id="d04d4-111">Demonstrates how to use the <xref:System.Windows.Forms.Control.Dock%2A> property to align your control to the edge of the form it occupies.</span></span>

<span data-ttu-id="d04d4-112">[Instrukcje: Tworzenie obramowania Wokoło formularze Windows kontrolować za pomocą wypełnienia](how-to-create-a-border-around-a-windows-forms-control-using-padding.md)\\</span><span class="sxs-lookup"><span data-stu-id="d04d4-112">[How to: Create a Border Around a Windows Forms Control Using Padding](how-to-create-a-border-around-a-windows-forms-control-using-padding.md)\\</span></span>
<span data-ttu-id="d04d4-113">Pokazuje sposób użycia <xref:System.Windows.Forms.Control.Padding%2A> właściwości opisują formantu.</span><span class="sxs-lookup"><span data-stu-id="d04d4-113">Demonstrates how to use the <xref:System.Windows.Forms.Control.Padding%2A> property to outline a control.</span></span>

<span data-ttu-id="d04d4-114">[Instrukcje: Implementowanie aparatu niestandardowego układu](how-to-implement-a-custom-layout-engine.md)\\</span><span class="sxs-lookup"><span data-stu-id="d04d4-114">[How to: Implement a Custom Layout Engine](how-to-implement-a-custom-layout-engine.md)\\</span></span>
<span data-ttu-id="d04d4-115">Demonstruje sposób implementacji <xref:System.Windows.Forms.Layout.LayoutEngine> rozmieszczania kontrolek formularzy Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d04d4-115">Demonstrates how to implement a <xref:System.Windows.Forms.Layout.LayoutEngine> for arranging Windows Forms controls.</span></span>

## <a name="reference"></a><span data-ttu-id="d04d4-116">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="d04d4-116">Reference</span></span>

<xref:System.Windows.Forms.TableLayoutPanel>\
<span data-ttu-id="d04d4-117">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.TableLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="d04d4-117">Provides reference documentation for the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

<xref:System.Windows.Forms.FlowLayoutPanel>\
<span data-ttu-id="d04d4-118">Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.FlowLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="d04d4-118">Provides reference documentation for the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

## <a name="see-also"></a><span data-ttu-id="d04d4-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d04d4-119">See also</span></span>

- [<span data-ttu-id="d04d4-120">Instrukcje: Zakotwiczenie i dokowanie formantów podrzędnych w formancie FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="d04d4-120">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="d04d4-121">Instrukcje: Zakotwiczenie i dokowanie formantów podrzędnych w formancie TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="d04d4-121">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="d04d4-122">Instrukcje: Projektowanie układu formularzy Windows dobrze reagującego na lokalizację</span><span class="sxs-lookup"><span data-stu-id="d04d4-122">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [<span data-ttu-id="d04d4-123">Zachowanie AutoSize w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="d04d4-123">AutoSize Behavior in the TableLayoutPanel Control</span></span>](autosize-behavior-in-the-tablelayoutpanel-control.md)
