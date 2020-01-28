---
title: 'Instrukcje: Zmienianie wyglądu tekstu i obrazów elementu ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], appearance
- toolbars [Windows Forms], images
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], appearance
- ToolStrip control [Windows Forms], images
- ToolStrip control [Windows Forms], text
- toolbars [Windows Forms], text
ms.assetid: d62dc9d1-2edd-4dfa-aed7-1335d6e13d86
ms.openlocfilehash: 7816e138e44554683c201895ece1f886ace8bfa6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746598"
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a><span data-ttu-id="d9b2a-102">Porady: zmienianie wyglądu tekstu i obrazów elementów ToolStrip w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d9b2a-102">How to: Change the Appearance of ToolStrip Text and Images in Windows Forms</span></span>
<span data-ttu-id="d9b2a-103">Można kontrolować, czy tekst i obrazy są wyświetlane na <xref:System.Windows.Forms.ToolStripItem> oraz jak są wyrównane względem siebie i <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="d9b2a-103">You can control whether text and images are displayed on a <xref:System.Windows.Forms.ToolStripItem> and how they are aligned relative to each other and the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a><span data-ttu-id="d9b2a-104">Aby zdefiniować elementy, które są wyświetlane w elementach ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="d9b2a-104">To define what is displayed on a ToolStripItem</span></span>  
  
- <span data-ttu-id="d9b2a-105">Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> na żądaną wartość.</span><span class="sxs-lookup"><span data-stu-id="d9b2a-105">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to the desired value.</span></span> <span data-ttu-id="d9b2a-106">Możliwości są `Image`, `ImageAndText`, `None`i `Text`.</span><span class="sxs-lookup"><span data-stu-id="d9b2a-106">The possibilities are `Image`, `ImageAndText`, `None`, and `Text`.</span></span> <span data-ttu-id="d9b2a-107">Wartość domyślna to `ImageAndText`.</span><span class="sxs-lookup"><span data-stu-id="d9b2a-107">The default is `ImageAndText`.</span></span>  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a><span data-ttu-id="d9b2a-108">Aby wyrównać tekst na ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="d9b2a-108">To align text on a ToolStripItem</span></span>  
  
- <span data-ttu-id="d9b2a-109">Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> na żądaną wartość.</span><span class="sxs-lookup"><span data-stu-id="d9b2a-109">Set the <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> property to the desired value.</span></span> <span data-ttu-id="d9b2a-110">Możliwości są dowolną kombinacją górnego, środkowego i dolnego z lewej, środkową i prawą.</span><span class="sxs-lookup"><span data-stu-id="d9b2a-110">The possibilities are any combination of top, middle, and bottom with left, center, and right.</span></span> <span data-ttu-id="d9b2a-111">Wartość domyślna to `MiddleCenter`.</span><span class="sxs-lookup"><span data-stu-id="d9b2a-111">The default is `MiddleCenter`.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a><span data-ttu-id="d9b2a-112">Aby wyrównać obraz na element ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="d9b2a-112">To align an image on a ToolStripItem</span></span>  
  
- <span data-ttu-id="d9b2a-113">Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> na żądaną wartość.</span><span class="sxs-lookup"><span data-stu-id="d9b2a-113">Set the <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> property to the desired value.</span></span> <span data-ttu-id="d9b2a-114">Możliwości są dowolną kombinacją górnego, środkowego i dolnego z lewej, środkową i prawą.</span><span class="sxs-lookup"><span data-stu-id="d9b2a-114">The possibilities are any combination of top, middle, and bottom with left, center, and right.</span></span> <span data-ttu-id="d9b2a-115">Wartość domyślna to `MiddleLeft`.</span><span class="sxs-lookup"><span data-stu-id="d9b2a-115">The default is `MiddleLeft`.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a><span data-ttu-id="d9b2a-116">Aby określić sposób wyświetlania tekstu i obrazów elementu ToolStripItem względem siebie</span><span class="sxs-lookup"><span data-stu-id="d9b2a-116">To define how ToolStripItem text and images are displayed relative to each other</span></span>  
  
- <span data-ttu-id="d9b2a-117">Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> na żądaną wartość.</span><span class="sxs-lookup"><span data-stu-id="d9b2a-117">Set the <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> property to the desired value.</span></span> <span data-ttu-id="d9b2a-118">Możliwe są `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`i `TextBeforeImage`.</span><span class="sxs-lookup"><span data-stu-id="d9b2a-118">The possibilities are `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, and `TextBeforeImage`.</span></span> <span data-ttu-id="d9b2a-119">Wartość domyślna to `ImageBeforeText`.</span><span class="sxs-lookup"><span data-stu-id="d9b2a-119">The default is `ImageBeforeText`.</span></span>  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d9b2a-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9b2a-120">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="d9b2a-121">ToolStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="d9b2a-121">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="d9b2a-122">ToolStrip, kontrolka — architektura</span><span class="sxs-lookup"><span data-stu-id="d9b2a-122">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="d9b2a-123">ToolStrip — podsumowanie informacji o technologii</span><span class="sxs-lookup"><span data-stu-id="d9b2a-123">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
