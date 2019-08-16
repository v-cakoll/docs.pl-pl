---
title: 'Instrukcje: obejmowanie rzędów i kolumn w kontrolce TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns
helpviewer_keywords:
- columns [Windows Forms], spanning
- merging cells
- TableLayoutPanel control [Windows Forms], spanning rows and columns
- rows [Windows Forms], spanning
- cells [Windows Forms], merging
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
ms.openlocfilehash: a215b2b4e05bab5c81d2779d4b67d5b9d57b6ba5
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039701"
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a><span data-ttu-id="c759f-102">Instrukcje: obejmowanie rzędów i kolumn w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="c759f-102">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>
<span data-ttu-id="c759f-103">Kontrolki w <xref:System.Windows.Forms.TableLayoutPanel> kontrolce mogą obejmować sąsiadujące wiersze i kolumny.</span><span class="sxs-lookup"><span data-stu-id="c759f-103">Controls in a <xref:System.Windows.Forms.TableLayoutPanel> control can span adjacent rows and columns.</span></span>

## <a name="to-span-columns-and-rows"></a><span data-ttu-id="c759f-104">Aby rozpiętie kolumn i wierszy</span><span class="sxs-lookup"><span data-stu-id="c759f-104">To span columns and rows</span></span>

1. <span data-ttu-id="c759f-105">Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.TableLayoutPanel></span><span class="sxs-lookup"><span data-stu-id="c759f-105">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="c759f-106">Przeciągnij kontrolkę z **przybornika** do <xref:System.Windows.Forms.TableLayoutPanel> lewej górnej komórki formantu. <xref:System.Windows.Forms.Button></span><span class="sxs-lookup"><span data-stu-id="c759f-106">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

3. <span data-ttu-id="c759f-107">Ustaw właściwość **ColumnSpan**kontrolki na 2 <xref:System.Windows.Forms.Button> .</span><span class="sxs-lookup"><span data-stu-id="c759f-107">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **2**.</span></span> <span data-ttu-id="c759f-108">Należy zauważyć, <xref:System.Windows.Forms.Button> że formant obejmuje pierwszą i drugą kolumnę.</span><span class="sxs-lookup"><span data-stu-id="c759f-108">Note that the <xref:System.Windows.Forms.Button> control spans the first and second columns.</span></span>

4. <span data-ttu-id="c759f-109">Ustaw właściwość **RowSpan**kontrolki na 2 <xref:System.Windows.Forms.Button> .</span><span class="sxs-lookup"><span data-stu-id="c759f-109">Set the <xref:System.Windows.Forms.Button> control's **RowSpan** property to **2**.</span></span> <span data-ttu-id="c759f-110">Należy zauważyć, <xref:System.Windows.Forms.Button> że formant obejmuje pierwszy i drugi wiersz.</span><span class="sxs-lookup"><span data-stu-id="c759f-110">Note that the <xref:System.Windows.Forms.Button> control spans the first and second rows.</span></span>

5. <span data-ttu-id="c759f-111">Ustaw właściwość **ColumnSpan**kontrolki na 1 <xref:System.Windows.Forms.Button> .</span><span class="sxs-lookup"><span data-stu-id="c759f-111">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **1**.</span></span> <span data-ttu-id="c759f-112">Należy zauważyć, <xref:System.Windows.Forms.Button> że formant jest przenoszony do pierwszej kolumny i rozciąga się na pierwszy i drugi wiersz.</span><span class="sxs-lookup"><span data-stu-id="c759f-112">Note that the <xref:System.Windows.Forms.Button> control moves into the first column and spans the first and second rows.</span></span>

## <a name="see-also"></a><span data-ttu-id="c759f-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c759f-113">See also</span></span>

- [<span data-ttu-id="c759f-114">TableLayoutPanel, kontrolka</span><span class="sxs-lookup"><span data-stu-id="c759f-114">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
