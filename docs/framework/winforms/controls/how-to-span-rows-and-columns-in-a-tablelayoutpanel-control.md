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
ms.openlocfilehash: a78286be8ef64212d945b3cb11a2963d5a1b2e79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535350"
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a><span data-ttu-id="b4f68-102">Porady: obejmowanie rzędów i kolumn w formancie TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="b4f68-102">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>
<span data-ttu-id="b4f68-103">Formanty w <xref:System.Windows.Forms.TableLayoutPanel> formant może obejmować sąsiadujących wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="b4f68-103">Controls in a <xref:System.Windows.Forms.TableLayoutPanel> control can span adjacent rows and columns.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4f68-104">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="b4f68-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b4f68-105">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="b4f68-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b4f68-106">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="b4f68-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-span-columns-and-rows"></a><span data-ttu-id="b4f68-107">Zakresu kolumn i wierszy</span><span class="sxs-lookup"><span data-stu-id="b4f68-107">To span columns and rows</span></span>  
  
1.  <span data-ttu-id="b4f68-108">Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> kontrolować z **przybornika** na formularzu.</span><span class="sxs-lookup"><span data-stu-id="b4f68-108">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="b4f68-109">Przeciągnij <xref:System.Windows.Forms.Button> kontrolować z **przybornika** do lewej górnej komórki <xref:System.Windows.Forms.TableLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="b4f68-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
3.  <span data-ttu-id="b4f68-110">Ustaw <xref:System.Windows.Forms.Button> formantu **ColumnSpan** właściwości **2**.</span><span class="sxs-lookup"><span data-stu-id="b4f68-110">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **2**.</span></span> <span data-ttu-id="b4f68-111">Należy pamiętać, że <xref:System.Windows.Forms.Button> kontroli obejmuje w pierwszej i drugiej kolumnie.</span><span class="sxs-lookup"><span data-stu-id="b4f68-111">Note that the <xref:System.Windows.Forms.Button> control spans the first and second columns.</span></span>  
  
4.  <span data-ttu-id="b4f68-112">Ustaw <xref:System.Windows.Forms.Button> formantu **RowSpan** właściwości **2**.</span><span class="sxs-lookup"><span data-stu-id="b4f68-112">Set the <xref:System.Windows.Forms.Button> control's **RowSpan** property to **2**.</span></span> <span data-ttu-id="b4f68-113">Należy pamiętać, że <xref:System.Windows.Forms.Button> kontroli obejmuje pierwszym i drugim wierszu.</span><span class="sxs-lookup"><span data-stu-id="b4f68-113">Note that the <xref:System.Windows.Forms.Button> control spans the first and second rows.</span></span>  
  
5.  <span data-ttu-id="b4f68-114">Ustaw <xref:System.Windows.Forms.Button> formantu **ColumnSpan** właściwości **1**.</span><span class="sxs-lookup"><span data-stu-id="b4f68-114">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **1**.</span></span> <span data-ttu-id="b4f68-115">Należy pamiętać, że <xref:System.Windows.Forms.Button> kontroli przenosi do pierwszej kolumny i obejmuje pierwszym i drugim wierszu.</span><span class="sxs-lookup"><span data-stu-id="b4f68-115">Note that the <xref:System.Windows.Forms.Button> control moves into the first column and spans the first and second rows.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4f68-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4f68-116">See Also</span></span>  
 [<span data-ttu-id="b4f68-117">TableLayoutPanel, kontrolka</span><span class="sxs-lookup"><span data-stu-id="b4f68-117">TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
