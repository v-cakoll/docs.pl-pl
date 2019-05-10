---
title: 'Instrukcje: wyrównywanie i rozciąganie kontrolki w kontrolce TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms], stretching controls
- controls [Windows Forms], stretching
- controls [Windows Forms], aligning
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
ms.openlocfilehash: fd32593bcad9e3f3ef93edee8aa2659d423f9feb
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210361"
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a><span data-ttu-id="d9bc2-102">Instrukcje: wyrównywanie i rozciąganie kontrolki w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="d9bc2-102">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>

<span data-ttu-id="d9bc2-103">Wyrównywanie i rozciąganie kontrolek w <xref:System.Windows.Forms.TableLayoutPanel> z <xref:System.Windows.Forms.Control.Anchor%2A> i <xref:System.Windows.Forms.Control.Dock%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d9bc2-103">You can align and stretch controls in a <xref:System.Windows.Forms.TableLayoutPanel> with the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties.</span></span>

## <a name="align-and-stretch-a-control"></a><span data-ttu-id="d9bc2-104">Wyrównaj i rozciągnij kontrolki</span><span class="sxs-lookup"><span data-stu-id="d9bc2-104">Align and stretch a control</span></span>

1. <span data-ttu-id="d9bc2-105">W programie Visual Studio przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> z kontrolować **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="d9bc2-105">In Visual Studio, drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>

2. <span data-ttu-id="d9bc2-106">Przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do lewej górnej komórki <xref:System.Windows.Forms.TableLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="d9bc2-106">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="d9bc2-107"><xref:System.Windows.Forms.Button> Kontroli jest wyśrodkowywana w komórce.</span><span class="sxs-lookup"><span data-stu-id="d9bc2-107">The <xref:System.Windows.Forms.Button> control is centered in the cell.</span></span>

3. <span data-ttu-id="d9bc2-108">Ustaw wartość <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `Left,Right`.</span><span class="sxs-lookup"><span data-stu-id="d9bc2-108">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left,Right`.</span></span> <span data-ttu-id="d9bc2-109"><xref:System.Windows.Forms.Button> Kontrolować odcinkach, aby dopasować szerokości krawędzi komórki.</span><span class="sxs-lookup"><span data-stu-id="d9bc2-109">The <xref:System.Windows.Forms.Button> control stretches to match the width of the cell.</span></span>

4. <span data-ttu-id="d9bc2-110">Ustaw wartość <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `Top,Bottom`.</span><span class="sxs-lookup"><span data-stu-id="d9bc2-110">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top,Bottom`.</span></span> <span data-ttu-id="d9bc2-111"><xref:System.Windows.Forms.Button> Kontrolować odcinkach, aby dopasować wysokość komórki.</span><span class="sxs-lookup"><span data-stu-id="d9bc2-111">The <xref:System.Windows.Forms.Button> control stretches to match the height of the cell.</span></span>

5. <span data-ttu-id="d9bc2-112">Ustaw wartość <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="d9bc2-112">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="d9bc2-113"><xref:System.Windows.Forms.Button> Kontroli rozwija do wypełnienia komórki.</span><span class="sxs-lookup"><span data-stu-id="d9bc2-113">The <xref:System.Windows.Forms.Button> control expands to fill the cell.</span></span>

6. <span data-ttu-id="d9bc2-114">Ustaw wartość <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="d9bc2-114">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.None>.</span></span> <span data-ttu-id="d9bc2-115"><xref:System.Windows.Forms.Button> Formant powraca do oryginalnego rozmiaru i przechodzi do lewego górnego rogu komórki.</span><span class="sxs-lookup"><span data-stu-id="d9bc2-115">The <xref:System.Windows.Forms.Button> control returns to its original size and moves to the upper-left corner of the cell.</span></span> <span data-ttu-id="d9bc2-116">**Windows Forms Designer** ustawił <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `Top, Left`.</span><span class="sxs-lookup"><span data-stu-id="d9bc2-116">The **Windows Forms Designer** has set the <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Left`.</span></span>

7. <span data-ttu-id="d9bc2-117">Ustaw wartość <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `Bottom,Right`.</span><span class="sxs-lookup"><span data-stu-id="d9bc2-117">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Bottom,Right`.</span></span> <span data-ttu-id="d9bc2-118"><xref:System.Windows.Forms.Button> Kontrola przechodzi do prawego dolnego rogu komórki.</span><span class="sxs-lookup"><span data-stu-id="d9bc2-118">The <xref:System.Windows.Forms.Button> control moves to the lower-right corner of the cell.</span></span>

8. <span data-ttu-id="d9bc2-119">Ustaw wartość <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość <xref:System.Windows.Forms.AnchorStyles.None>.</span><span class="sxs-lookup"><span data-stu-id="d9bc2-119">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to <xref:System.Windows.Forms.AnchorStyles.None>.</span></span> <span data-ttu-id="d9bc2-120"><xref:System.Windows.Forms.Button> Sterowania przechodzi na środku komórki.</span><span class="sxs-lookup"><span data-stu-id="d9bc2-120">The <xref:System.Windows.Forms.Button> control moves to the center of the cell.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9bc2-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9bc2-121">See also</span></span>

- [<span data-ttu-id="d9bc2-122">TableLayoutPanel, kontrolka</span><span class="sxs-lookup"><span data-stu-id="d9bc2-122">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
