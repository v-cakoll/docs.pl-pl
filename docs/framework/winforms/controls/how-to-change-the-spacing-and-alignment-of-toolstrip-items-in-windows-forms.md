---
title: 'Instrukcje: zmienianie odstępów i wyrównania elementów ToolStrip w formularzach systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: bed943466348447e30947c170e27027f324342c6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59323177"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a><span data-ttu-id="c7500-102">Instrukcje: zmienianie odstępów i wyrównania elementów ToolStrip w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c7500-102">How to: Change the Spacing and Alignment of ToolStrip Items in Windows Forms</span></span>
<span data-ttu-id="c7500-103"><xref:System.Windows.Forms.ToolStrip> Kontroli w pełni obsługuje układ funkcje, takie jak rozmiary, odstępy między <xref:System.Windows.Forms.ToolStripItem> formantów względem siebie, rozmieszczenie kontrolek w <xref:System.Windows.Forms.ToolStrip>i odstępy kontroli względem <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="c7500-103">The <xref:System.Windows.Forms.ToolStrip> control fully supports layout features such as sizing, the spacing of <xref:System.Windows.Forms.ToolStripItem> controls relative to each other, the arrangement of controls on the <xref:System.Windows.Forms.ToolStrip>, and the spacing of controls relative to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
 <span data-ttu-id="c7500-104">Ponieważ wartość domyślną <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> właściwość `true`, formanty mają rozmiar automatycznie, chyba że <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="c7500-104">Because the default value of the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property is `true`, controls are sized automatically unless you set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false`.</span></span>  
  
### <a name="to-manually-size-a-toolstripitem"></a><span data-ttu-id="c7500-105">Aby ręcznie rozmiar elementu ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="c7500-105">To manually size a ToolStripItem</span></span>  
  
1. <span data-ttu-id="c7500-106">Ustaw <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> właściwość `false` skojarzonego formantu.</span><span class="sxs-lookup"><span data-stu-id="c7500-106">Set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false` for the associated control.</span></span>  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2. <span data-ttu-id="c7500-107">Ustaw <xref:System.Windows.Forms.ToolStripItem.Size%2A> właściwości w sposób skojarzonych z nim <xref:System.Windows.Forms.ToolStripItem>.</span><span class="sxs-lookup"><span data-stu-id="c7500-107">Set the <xref:System.Windows.Forms.ToolStripItem.Size%2A> property the way you want for the associated <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a><span data-ttu-id="c7500-108">Aby ustawić odstępy elementu ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="c7500-108">To set the spacing of a ToolStripItem</span></span>  
  
1. <span data-ttu-id="c7500-109">Wstawianie odpowiednie wartości, w pikselach, <xref:System.Windows.Forms.ToolStripItem.Margin%2A> właściwości skojarzonego formantu.</span><span class="sxs-lookup"><span data-stu-id="c7500-109">Insert the desired values, in pixels, into the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property of the associated control.</span></span>  
  
     <span data-ttu-id="c7500-110">Wartości <xref:System.Windows.Forms.ToolStripItem.Margin%2A> właściwość Określ odstępy między elementem a sąsiadujących elementów w następującej kolejności: Po lewej stronie, górnej, prawej strony i dolnej.</span><span class="sxs-lookup"><span data-stu-id="c7500-110">The values of the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property specify the spacing between the item and adjacent items in this order: Left, Top, Right, and Bottom.</span></span>  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a><span data-ttu-id="c7500-111">Aby wyrównać elementu ToolStripItem w prawą stronę ToolStrip</span><span class="sxs-lookup"><span data-stu-id="c7500-111">To align a ToolStripItem to the right side of the ToolStrip</span></span>  
  
1. <span data-ttu-id="c7500-112">Ustaw <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> właściwość <xref:System.Windows.Forms.ToolStripItemAlignment.Right> skojarzonego formantu.</span><span class="sxs-lookup"><span data-stu-id="c7500-112">Set the <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> property to <xref:System.Windows.Forms.ToolStripItemAlignment.Right> for the associated control.</span></span> <span data-ttu-id="c7500-113">Domyślnie <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> ustawiono <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, która wyrównuje kontrolki do lewej części <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="c7500-113">By default, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> is set to <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, which aligns controls to the left side of the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a><span data-ttu-id="c7500-114">Aby rozmieścić elementy paska narzędzi na pasku narzędzi</span><span class="sxs-lookup"><span data-stu-id="c7500-114">To arrange ToolStrip items on the ToolStrip</span></span>  
  
-   <span data-ttu-id="c7500-115">Ustaw <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> właściwości na wartość <xref:System.Windows.Forms.ToolStripLayoutStyle> przewidzianą.</span><span class="sxs-lookup"><span data-stu-id="c7500-115">Set the <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> property to the value of <xref:System.Windows.Forms.ToolStripLayoutStyle> that you want.</span></span>  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c7500-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7500-116">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.Layout>
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>
- <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>
- <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>
- <xref:System.Windows.Forms.ToolStripItem.Placement%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [<span data-ttu-id="c7500-117">ToolStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="c7500-117">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="c7500-118">ToolStrip, kontrolka — architektura</span><span class="sxs-lookup"><span data-stu-id="c7500-118">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="c7500-119">ToolStrip — podsumowanie informacji o technologii</span><span class="sxs-lookup"><span data-stu-id="c7500-119">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
