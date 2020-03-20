---
title: 'Jak: Zmiana odstępów i wyrównania elementów Paska narzędzi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 550ac1660a077e8d766a01bfa8d102c07f0fbfeb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182229"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a><span data-ttu-id="67272-102">Porady: zmienianie odstępów i wyrównania elementów ToolStrip w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="67272-102">How to: Change the Spacing and Alignment of ToolStrip Items in Windows Forms</span></span>
<span data-ttu-id="67272-103">Formant <xref:System.Windows.Forms.ToolStrip> w pełni obsługuje funkcje układu, <xref:System.Windows.Forms.ToolStripItem> takie jak zmiana rozmiaru, odstępy <xref:System.Windows.Forms.ToolStrip>formantów względem siebie, rozmieszczenie formantów na , i odstępy formantów względem <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="67272-103">The <xref:System.Windows.Forms.ToolStrip> control fully supports layout features such as sizing, the spacing of <xref:System.Windows.Forms.ToolStripItem> controls relative to each other, the arrangement of controls on the <xref:System.Windows.Forms.ToolStrip>, and the spacing of controls relative to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
 <span data-ttu-id="67272-104"><xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> Ponieważ domyślną wartością `true`właściwości jest , formanty <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> są `false`zmieniane automatycznie, chyba że właściwość zostanie ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="67272-104">Because the default value of the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property is `true`, controls are sized automatically unless you set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false`.</span></span>  
  
### <a name="to-manually-size-a-toolstripitem"></a><span data-ttu-id="67272-105">Aby ręcznie rozmiar ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="67272-105">To manually size a ToolStripItem</span></span>  
  
1. <span data-ttu-id="67272-106">Ustaw <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> właściwość `false` na skojarzony formant.</span><span class="sxs-lookup"><span data-stu-id="67272-106">Set the <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> property to `false` for the associated control.</span></span>  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2. <span data-ttu-id="67272-107">Ustaw <xref:System.Windows.Forms.ToolStripItem.Size%2A> właściwość w odpowiedni sposób <xref:System.Windows.Forms.ToolStripItem>dla skojarzonego .</span><span class="sxs-lookup"><span data-stu-id="67272-107">Set the <xref:System.Windows.Forms.ToolStripItem.Size%2A> property the way you want for the associated <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a><span data-ttu-id="67272-108">Aby ustawić odstępy między narzędziami ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="67272-108">To set the spacing of a ToolStripItem</span></span>  
  
1. <span data-ttu-id="67272-109">Wstaw żądane wartości w pikselach do <xref:System.Windows.Forms.ToolStripItem.Margin%2A> właściwości skojarzonego formantu.</span><span class="sxs-lookup"><span data-stu-id="67272-109">Insert the desired values, in pixels, into the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property of the associated control.</span></span>  
  
     <span data-ttu-id="67272-110">Wartości <xref:System.Windows.Forms.ToolStripItem.Margin%2A> właściwości określają odstępy między elementem a sąsiednimi elementami w następującej kolejności: Lewy, U góry, Prawy i Dolny.</span><span class="sxs-lookup"><span data-stu-id="67272-110">The values of the <xref:System.Windows.Forms.ToolStripItem.Margin%2A> property specify the spacing between the item and adjacent items in this order: Left, Top, Right, and Bottom.</span></span>  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a><span data-ttu-id="67272-111">Aby wyrównać narzędzie ToolStripItem do prawej strony paska narzędzi</span><span class="sxs-lookup"><span data-stu-id="67272-111">To align a ToolStripItem to the right side of the ToolStrip</span></span>  
  
1. <span data-ttu-id="67272-112">Ustaw <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> właściwość <xref:System.Windows.Forms.ToolStripItemAlignment.Right> na skojarzony formant.</span><span class="sxs-lookup"><span data-stu-id="67272-112">Set the <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> property to <xref:System.Windows.Forms.ToolStripItemAlignment.Right> for the associated control.</span></span> <span data-ttu-id="67272-113">Domyślnie <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> jest ustawiona na <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, która wyrównuje formanty do lewej strony pliku <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="67272-113">By default, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> is set to <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, which aligns controls to the left side of the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a><span data-ttu-id="67272-114">Aby rozmieścić elementy Paska narzędzi na pasie narzędziowym</span><span class="sxs-lookup"><span data-stu-id="67272-114">To arrange ToolStrip items on the ToolStrip</span></span>  
  
- <span data-ttu-id="67272-115">Ustaw <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> właściwość na <xref:System.Windows.Forms.ToolStripLayoutStyle> żądaną wartość.</span><span class="sxs-lookup"><span data-stu-id="67272-115">Set the <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> property to the value of <xref:System.Windows.Forms.ToolStripLayoutStyle> that you want.</span></span>  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="67272-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="67272-116">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.Layout>
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>
- <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>
- <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>
- <xref:System.Windows.Forms.ToolStripItem.Placement%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [<span data-ttu-id="67272-117">ToolStrip — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="67272-117">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="67272-118">ToolStrip — Architektura formantu</span><span class="sxs-lookup"><span data-stu-id="67272-118">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="67272-119">Podsumowanie informacji o technologii formantów ToolStrip</span><span class="sxs-lookup"><span data-stu-id="67272-119">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
