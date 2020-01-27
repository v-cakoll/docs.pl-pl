---
title: 'Instrukcje: Zmienianie odstępów i wyrównania elementów ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 805fbac5fe33071006f29692d503e5c57eacd765
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746562"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a><span data-ttu-id="e4260-102">Porady: zmienianie odstępów i wyrównania elementów ToolStrip w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e4260-102">How to: Change the Spacing and Alignment of ToolStrip Items in Windows Forms</span></span>
<span data-ttu-id="e4260-103">Kontrolka <xref:System.Windows.Forms.ToolStrip> w pełni obsługuje funkcje układu, takie jak rozmiar, odstępy <xref:System.Windows.Forms.ToolStripItem> formantów względem siebie, rozmieszczenie formantów na <xref:System.Windows.Forms.ToolStrip>oraz odstępy kontrolek względem <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="e4260-103">The <xref:System.Windows.Forms.ToolStrip> control fully supports layout features such as sizing, the spacing of <xref:System.Windows.Forms.ToolStripItem> controls relative to each other, the arrangement of controls on the <xref:System.Windows.Forms.ToolStrip>, and the spacing of controls relative to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
 <span data-ttu-id="e4260-104">Ponieważ wartość domyślna właściwości <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> jest `true`, rozmiary formantów są ustawiane automatycznie, o ile Właściwość <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> nie zostanie ustawiona na `false`.</span><span class="sxs-lookup"><span data-stu-id="e4260-104">Because the default value of the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property is `true`, controls are sized automatically unless you set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false`.</span></span>  
  
### <a name="to-manually-size-a-toolstripitem"></a><span data-ttu-id="e4260-105">Aby ręcznie zmienić rozmiar elementu ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="e4260-105">To manually size a ToolStripItem</span></span>  
  
1. <span data-ttu-id="e4260-106">Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> na `false` dla skojarzonej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="e4260-106">Set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false` for the associated control.</span></span>  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2. <span data-ttu-id="e4260-107">Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.Size%2A> w odpowiedni sposób dla <xref:System.Windows.Forms.ToolStripItem>skojarzonych.</span><span class="sxs-lookup"><span data-stu-id="e4260-107">Set the <xref:System.Windows.Forms.ToolStripItem.Size%2A> property the way you want for the associated <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a><span data-ttu-id="e4260-108">Aby ustawić odstępy elementu ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="e4260-108">To set the spacing of a ToolStripItem</span></span>  
  
1. <span data-ttu-id="e4260-109">Wstaw odpowiednie wartości (w pikselach) do właściwości <xref:System.Windows.Forms.ToolStripItem.Margin%2A> skojarzonej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="e4260-109">Insert the desired values, in pixels, into the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property of the associated control.</span></span>  
  
     <span data-ttu-id="e4260-110">Wartości właściwości <xref:System.Windows.Forms.ToolStripItem.Margin%2A> określają odstępy między elementem i sąsiadującymi elementami w tej kolejności: od lewej, do góry, do prawej i u dołu.</span><span class="sxs-lookup"><span data-stu-id="e4260-110">The values of the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property specify the spacing between the item and adjacent items in this order: Left, Top, Right, and Bottom.</span></span>  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a><span data-ttu-id="e4260-111">Aby wyrównać Element ToolStripItem do prawej strony elementu ToolStrip</span><span class="sxs-lookup"><span data-stu-id="e4260-111">To align a ToolStripItem to the right side of the ToolStrip</span></span>  
  
1. <span data-ttu-id="e4260-112">Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> na <xref:System.Windows.Forms.ToolStripItemAlignment.Right> dla skojarzonej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="e4260-112">Set the <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> property to <xref:System.Windows.Forms.ToolStripItemAlignment.Right> for the associated control.</span></span> <span data-ttu-id="e4260-113">Domyślnie <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> jest ustawiona na <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, co oznacza, że kontrolki są wyrównane do lewej strony <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="e4260-113">By default, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> is set to <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, which aligns controls to the left side of the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a><span data-ttu-id="e4260-114">Aby rozmieścić elementy ToolStrip na pasku narzędzi</span><span class="sxs-lookup"><span data-stu-id="e4260-114">To arrange ToolStrip items on the ToolStrip</span></span>  
  
- <span data-ttu-id="e4260-115">Ustaw właściwość <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> na wartość <xref:System.Windows.Forms.ToolStripLayoutStyle>, która ma zostać wybrana.</span><span class="sxs-lookup"><span data-stu-id="e4260-115">Set the <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> property to the value of <xref:System.Windows.Forms.ToolStripLayoutStyle> that you want.</span></span>  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e4260-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4260-116">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.Layout>
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>
- <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>
- <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>
- <xref:System.Windows.Forms.ToolStripItem.Placement%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [<span data-ttu-id="e4260-117">ToolStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="e4260-117">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="e4260-118">ToolStrip, kontrolka — architektura</span><span class="sxs-lookup"><span data-stu-id="e4260-118">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="e4260-119">ToolStrip — podsumowanie informacji o technologii</span><span class="sxs-lookup"><span data-stu-id="e4260-119">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
