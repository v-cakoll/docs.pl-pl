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
ms.openlocfilehash: 6f36914387519b027fcf4cb6bf1e7654e551b3eb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59328026"
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a><span data-ttu-id="aa80c-102">Instrukcje: wyrównywanie i rozciąganie kontrolki w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="aa80c-102">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>
<span data-ttu-id="aa80c-103">Wyrównywanie i rozciąganie kontrolek w <xref:System.Windows.Forms.TableLayoutPanel> z <xref:System.Windows.Forms.Control.Anchor%2A> i <xref:System.Windows.Forms.Control.Dock%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="aa80c-103">You can align and stretch controls in a <xref:System.Windows.Forms.TableLayoutPanel> with the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa80c-104">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="aa80c-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="aa80c-105">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="aa80c-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="aa80c-106">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="aa80c-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-align-and-stretch-a-control"></a><span data-ttu-id="aa80c-107">Aby wyrównać i stretch kontrolki</span><span class="sxs-lookup"><span data-stu-id="aa80c-107">To align and stretch a control</span></span>  
  
1. <span data-ttu-id="aa80c-108">Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> z kontrolować **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="aa80c-108">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2. <span data-ttu-id="aa80c-109">Przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do lewej górnej komórki <xref:System.Windows.Forms.TableLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="aa80c-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="aa80c-110"><xref:System.Windows.Forms.Button> Kontroli jest wyśrodkowywana w komórce.</span><span class="sxs-lookup"><span data-stu-id="aa80c-110">The <xref:System.Windows.Forms.Button> control is centered in the cell.</span></span>  
  
3. <span data-ttu-id="aa80c-111">Ustaw wartość <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `Left,Right`.</span><span class="sxs-lookup"><span data-stu-id="aa80c-111">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left,Right`.</span></span> <span data-ttu-id="aa80c-112"><xref:System.Windows.Forms.Button> Kontrolować odcinkach, aby dopasować szerokości krawędzi komórki.</span><span class="sxs-lookup"><span data-stu-id="aa80c-112">The <xref:System.Windows.Forms.Button> control stretches to match the width of the cell.</span></span>  
  
4. <span data-ttu-id="aa80c-113">Ustaw wartość <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `Top,Bottom`.</span><span class="sxs-lookup"><span data-stu-id="aa80c-113">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top,Bottom`.</span></span> <span data-ttu-id="aa80c-114"><xref:System.Windows.Forms.Button> Kontrolować odcinkach, aby dopasować wysokość komórki.</span><span class="sxs-lookup"><span data-stu-id="aa80c-114">The <xref:System.Windows.Forms.Button> control stretches to match the height of the cell.</span></span>  
  
5. <span data-ttu-id="aa80c-115">Ustaw wartość <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="aa80c-115">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="aa80c-116"><xref:System.Windows.Forms.Button> Kontroli rozwija do wypełnienia komórki.</span><span class="sxs-lookup"><span data-stu-id="aa80c-116">The <xref:System.Windows.Forms.Button> control expands to fill the cell.</span></span>  
  
6. <span data-ttu-id="aa80c-117">Ustaw wartość <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="aa80c-117">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.None>.</span></span> <span data-ttu-id="aa80c-118"><xref:System.Windows.Forms.Button> Formant powraca do oryginalnego rozmiaru i przechodzi do lewego górnego rogu komórki.</span><span class="sxs-lookup"><span data-stu-id="aa80c-118">The <xref:System.Windows.Forms.Button> control returns to its original size and moves to the upper-left corner of the cell.</span></span> <span data-ttu-id="aa80c-119">**Windows Forms Designer** ustawił <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `Top, Left`.</span><span class="sxs-lookup"><span data-stu-id="aa80c-119">The **Windows Forms Designer** has set the <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Left`.</span></span>  
  
7. <span data-ttu-id="aa80c-120">Ustaw wartość <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `Bottom,Right`.</span><span class="sxs-lookup"><span data-stu-id="aa80c-120">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Bottom,Right`.</span></span> <span data-ttu-id="aa80c-121"><xref:System.Windows.Forms.Button> Kontrola przechodzi do prawego dolnego rogu komórki.</span><span class="sxs-lookup"><span data-stu-id="aa80c-121">The <xref:System.Windows.Forms.Button> control moves to the lower-right corner of the cell.</span></span>  
  
8. <span data-ttu-id="aa80c-122">Ustaw wartość <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość <xref:System.Windows.Forms.AnchorStyles.None>.</span><span class="sxs-lookup"><span data-stu-id="aa80c-122">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to <xref:System.Windows.Forms.AnchorStyles.None>.</span></span> <span data-ttu-id="aa80c-123"><xref:System.Windows.Forms.Button> Sterowania przechodzi na środku komórki.</span><span class="sxs-lookup"><span data-stu-id="aa80c-123">The <xref:System.Windows.Forms.Button> control moves to the center of the cell.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa80c-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aa80c-124">See also</span></span>

- [<span data-ttu-id="aa80c-125">TableLayoutPanel — kontrolka</span><span class="sxs-lookup"><span data-stu-id="aa80c-125">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
