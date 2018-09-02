---
title: 'Porady: obejmowanie rzędów i kolumn w formancie TableLayoutPanel'
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
ms.openlocfilehash: 5363e7a7def8d2593d3ac474deb9d3d7b77d3912
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401293"
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a><span data-ttu-id="29c6f-102">Porady: obejmowanie rzędów i kolumn w formancie TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="29c6f-102">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>
<span data-ttu-id="29c6f-103">Kontrolki w <xref:System.Windows.Forms.TableLayoutPanel> kontrolki mogą znajdować się na sąsiadujących wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="29c6f-103">Controls in a <xref:System.Windows.Forms.TableLayoutPanel> control can span adjacent rows and columns.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29c6f-104">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="29c6f-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="29c6f-105">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="29c6f-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="29c6f-106">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="29c6f-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-span-columns-and-rows"></a><span data-ttu-id="29c6f-107">Obejmować kolumnami i wierszami</span><span class="sxs-lookup"><span data-stu-id="29c6f-107">To span columns and rows</span></span>  
  
1.  <span data-ttu-id="29c6f-108">Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> z kontrolować **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="29c6f-108">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="29c6f-109">Przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do lewej górnej komórki <xref:System.Windows.Forms.TableLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="29c6f-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
3.  <span data-ttu-id="29c6f-110">Ustaw <xref:System.Windows.Forms.Button> kontrolki **ColumnSpan** właściwości **2**.</span><span class="sxs-lookup"><span data-stu-id="29c6f-110">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **2**.</span></span> <span data-ttu-id="29c6f-111">Należy pamiętać, że <xref:System.Windows.Forms.Button> kontroli obejmuje pierwsza i druga kolumna.</span><span class="sxs-lookup"><span data-stu-id="29c6f-111">Note that the <xref:System.Windows.Forms.Button> control spans the first and second columns.</span></span>  
  
4.  <span data-ttu-id="29c6f-112">Ustaw <xref:System.Windows.Forms.Button> kontrolki **RowSpan** właściwości **2**.</span><span class="sxs-lookup"><span data-stu-id="29c6f-112">Set the <xref:System.Windows.Forms.Button> control's **RowSpan** property to **2**.</span></span> <span data-ttu-id="29c6f-113">Należy pamiętać, że <xref:System.Windows.Forms.Button> kontroli rozciąga się pierwszym i drugim wierszu.</span><span class="sxs-lookup"><span data-stu-id="29c6f-113">Note that the <xref:System.Windows.Forms.Button> control spans the first and second rows.</span></span>  
  
5.  <span data-ttu-id="29c6f-114">Ustaw <xref:System.Windows.Forms.Button> kontrolki **ColumnSpan** właściwości **1**.</span><span class="sxs-lookup"><span data-stu-id="29c6f-114">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **1**.</span></span> <span data-ttu-id="29c6f-115">Należy pamiętać, że <xref:System.Windows.Forms.Button> kontrola przechodzi do pierwszej kolumny i obejmuje pierwszym i drugim wierszu.</span><span class="sxs-lookup"><span data-stu-id="29c6f-115">Note that the <xref:System.Windows.Forms.Button> control moves into the first column and spans the first and second rows.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29c6f-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29c6f-116">See Also</span></span>  
 [<span data-ttu-id="29c6f-117">TableLayoutPanel, kontrolka</span><span class="sxs-lookup"><span data-stu-id="29c6f-117">TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
