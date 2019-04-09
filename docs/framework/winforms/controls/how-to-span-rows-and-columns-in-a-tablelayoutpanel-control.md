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
ms.openlocfilehash: 2b2a46bf53dd6ec9bc93a74cca37dffaaaf79751
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193138"
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a><span data-ttu-id="11887-102">Instrukcje: obejmowanie rzędów i kolumn w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="11887-102">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>
<span data-ttu-id="11887-103">Kontrolki w <xref:System.Windows.Forms.TableLayoutPanel> kontrolki mogą znajdować się na sąsiadujących wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="11887-103">Controls in a <xref:System.Windows.Forms.TableLayoutPanel> control can span adjacent rows and columns.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11887-104">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="11887-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="11887-105">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="11887-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="11887-106">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="11887-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-span-columns-and-rows"></a><span data-ttu-id="11887-107">Obejmować kolumnami i wierszami</span><span class="sxs-lookup"><span data-stu-id="11887-107">To span columns and rows</span></span>  
  
1.  <span data-ttu-id="11887-108">Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> z kontrolować **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="11887-108">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="11887-109">Przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do lewej górnej komórki <xref:System.Windows.Forms.TableLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="11887-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
3.  <span data-ttu-id="11887-110">Ustaw <xref:System.Windows.Forms.Button> kontrolki **ColumnSpan** właściwości **2**.</span><span class="sxs-lookup"><span data-stu-id="11887-110">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **2**.</span></span> <span data-ttu-id="11887-111">Należy pamiętać, że <xref:System.Windows.Forms.Button> kontroli obejmuje pierwsza i druga kolumna.</span><span class="sxs-lookup"><span data-stu-id="11887-111">Note that the <xref:System.Windows.Forms.Button> control spans the first and second columns.</span></span>  
  
4.  <span data-ttu-id="11887-112">Ustaw <xref:System.Windows.Forms.Button> kontrolki **RowSpan** właściwości **2**.</span><span class="sxs-lookup"><span data-stu-id="11887-112">Set the <xref:System.Windows.Forms.Button> control's **RowSpan** property to **2**.</span></span> <span data-ttu-id="11887-113">Należy pamiętać, że <xref:System.Windows.Forms.Button> kontroli rozciąga się pierwszym i drugim wierszu.</span><span class="sxs-lookup"><span data-stu-id="11887-113">Note that the <xref:System.Windows.Forms.Button> control spans the first and second rows.</span></span>  
  
5.  <span data-ttu-id="11887-114">Ustaw <xref:System.Windows.Forms.Button> kontrolki **ColumnSpan** właściwości **1**.</span><span class="sxs-lookup"><span data-stu-id="11887-114">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **1**.</span></span> <span data-ttu-id="11887-115">Należy pamiętać, że <xref:System.Windows.Forms.Button> kontrola przechodzi do pierwszej kolumny i obejmuje pierwszym i drugim wierszu.</span><span class="sxs-lookup"><span data-stu-id="11887-115">Note that the <xref:System.Windows.Forms.Button> control moves into the first column and spans the first and second rows.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11887-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11887-116">See also</span></span>

- [<span data-ttu-id="11887-117">TableLayoutPanel — kontrolka</span><span class="sxs-lookup"><span data-stu-id="11887-117">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
