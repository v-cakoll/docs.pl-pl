---
title: "Porady: zmienianie odstępów i wyrównania elementów ToolStrip w formularzach systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 42ae53e143942201359baebdfa8929647e7e35cd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a><span data-ttu-id="e2667-102">Porady: zmienianie odstępów i wyrównania elementów ToolStrip w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e2667-102">How to: Change the Spacing and Alignment of ToolStrip Items in Windows Forms</span></span>
<span data-ttu-id="e2667-103"><xref:System.Windows.Forms.ToolStrip> Kontroli w pełni obsługuje układ funkcje, takie jak zmiany rozmiaru, odstępy <xref:System.Windows.Forms.ToolStripItem> formantów względem siebie, rozmieszczenie formantów w <xref:System.Windows.Forms.ToolStrip>i odstępy formantów względem <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="e2667-103">The <xref:System.Windows.Forms.ToolStrip> control fully supports layout features such as sizing, the spacing of <xref:System.Windows.Forms.ToolStripItem> controls relative to each other, the arrangement of controls on the <xref:System.Windows.Forms.ToolStrip>, and the spacing of controls relative to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
 <span data-ttu-id="e2667-104">Ponieważ domyślna wartość <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> właściwość jest `true`, formanty mają rozmiar automatycznie, chyba że ustawisz <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> właściwości `false`.</span><span class="sxs-lookup"><span data-stu-id="e2667-104">Because the default value of the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property is `true`, controls are sized automatically unless you set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false`.</span></span>  
  
### <a name="to-manually-size-a-toolstripitem"></a><span data-ttu-id="e2667-105">Aby ręcznie rozmiar elementu ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="e2667-105">To manually size a ToolStripItem</span></span>  
  
1.  <span data-ttu-id="e2667-106">Ustaw <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> właściwości `false` skojarzonego formantu.</span><span class="sxs-lookup"><span data-stu-id="e2667-106">Set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false` for the associated control.</span></span>  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2.  <span data-ttu-id="e2667-107">Ustaw <xref:System.Windows.Forms.ToolStripItem.Size%2A> właściwości skojarzonych z nim sposób <xref:System.Windows.Forms.ToolStripItem>.</span><span class="sxs-lookup"><span data-stu-id="e2667-107">Set the <xref:System.Windows.Forms.ToolStripItem.Size%2A> property the way you want for the associated <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a><span data-ttu-id="e2667-108">Aby ustawić odstępy elementu ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="e2667-108">To set the spacing of a ToolStripItem</span></span>  
  
1.  <span data-ttu-id="e2667-109">Włóż odpowiednie wartości w pikselach <xref:System.Windows.Forms.ToolStripItem.Margin%2A> właściwości skojarzony formant.</span><span class="sxs-lookup"><span data-stu-id="e2667-109">Insert the desired values, in pixels, into the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property of the associated control.</span></span>  
  
     <span data-ttu-id="e2667-110">Wartości <xref:System.Windows.Forms.ToolStripItem.Margin%2A> właściwości Określ odstępy między elementem a sąsiadujących elementów w następującej kolejności: po lewej, górnej, prawej i dolnej.</span><span class="sxs-lookup"><span data-stu-id="e2667-110">The values of the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property specify the spacing between the item and adjacent items in this order: Left, Top, Right, and Bottom.</span></span>  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a><span data-ttu-id="e2667-111">Aby wyrównać ToolStripItem do prawej krawędzi elementu ToolStrip</span><span class="sxs-lookup"><span data-stu-id="e2667-111">To align a ToolStripItem to the right side of the ToolStrip</span></span>  
  
1.  <span data-ttu-id="e2667-112">Ustaw <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> właściwości <xref:System.Windows.Forms.ToolStripItemAlignment.Right> skojarzonego formantu.</span><span class="sxs-lookup"><span data-stu-id="e2667-112">Set the <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> property to <xref:System.Windows.Forms.ToolStripItemAlignment.Right> for the associated control.</span></span> <span data-ttu-id="e2667-113">Domyślnie <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> ustawiono <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, która wyrównuje kontrolki do lewej strony <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="e2667-113">By default, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> is set to <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, which aligns controls to the left side of the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a><span data-ttu-id="e2667-114">Aby zorganizować elementów ToolStrip w elemencie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="e2667-114">To arrange ToolStrip items on the ToolStrip</span></span>  
  
-   <span data-ttu-id="e2667-115">Ustaw <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> właściwości do wartości <xref:System.Windows.Forms.ToolStripLayoutStyle> żądany.</span><span class="sxs-lookup"><span data-stu-id="e2667-115">Set the <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> property to the value of <xref:System.Windows.Forms.ToolStripLayoutStyle> that you want.</span></span>  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e2667-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e2667-116">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.Control.Layout>  
 <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>  
 <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>  
 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>  
 <xref:System.Windows.Forms.ToolStripItem.Placement%2A>  
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>  
 [<span data-ttu-id="e2667-117">Informacje o formancie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="e2667-117">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="e2667-118">ToolStrip — architektura formantu</span><span class="sxs-lookup"><span data-stu-id="e2667-118">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="e2667-119">Podsumowanie technologii formantów ToolStrip</span><span class="sxs-lookup"><span data-stu-id="e2667-119">ToolStrip Technology Summary</span></span>](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
