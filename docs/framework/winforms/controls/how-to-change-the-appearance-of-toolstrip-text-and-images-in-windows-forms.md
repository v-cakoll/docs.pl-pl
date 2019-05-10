---
title: 'Instrukcje: zmienianie wyglądu tekstu i obrazów elementów ToolStrip w formularzach systemu Windows'
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
ms.openlocfilehash: cf2f332b17bf6ff5b6ffb7cbc2d5777649728ec6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650848"
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a><span data-ttu-id="0282c-102">Instrukcje: zmienianie wyglądu tekstu i obrazów elementów ToolStrip w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="0282c-102">How to: Change the Appearance of ToolStrip Text and Images in Windows Forms</span></span>
<span data-ttu-id="0282c-103">Można kontrolować, czy tekst i obrazy są wyświetlane na <xref:System.Windows.Forms.ToolStripItem> i jak są wyrównane względem siebie i <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="0282c-103">You can control whether text and images are displayed on a <xref:System.Windows.Forms.ToolStripItem> and how they are aligned relative to each other and the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a><span data-ttu-id="0282c-104">Aby zdefiniować, co jest wyświetlane na elementu ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="0282c-104">To define what is displayed on a ToolStripItem</span></span>  
  
- <span data-ttu-id="0282c-105">Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> właściwości na żądaną wartość.</span><span class="sxs-lookup"><span data-stu-id="0282c-105">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to the desired value.</span></span> <span data-ttu-id="0282c-106">Możliwości są `Image`, `ImageAndText`, `None`, i `Text`.</span><span class="sxs-lookup"><span data-stu-id="0282c-106">The possibilities are `Image`, `ImageAndText`, `None`, and `Text`.</span></span> <span data-ttu-id="0282c-107">Wartość domyślna to `ImageAndText`.</span><span class="sxs-lookup"><span data-stu-id="0282c-107">The default is `ImageAndText`.</span></span>  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a><span data-ttu-id="0282c-108">Aby wyrównać tekst na elementu ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="0282c-108">To align text on a ToolStripItem</span></span>  
  
- <span data-ttu-id="0282c-109">Ustaw <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> właściwości na żądaną wartość.</span><span class="sxs-lookup"><span data-stu-id="0282c-109">Set the <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> property to the desired value.</span></span> <span data-ttu-id="0282c-110">Możliwości są dowolną kombinację początku, środka i na dole z lewej strony, wyśrodkowanie i po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="0282c-110">The possibilities are any combination of top, middle, and bottom with left, center, and right.</span></span> <span data-ttu-id="0282c-111">Wartość domyślna to `MiddleCenter`.</span><span class="sxs-lookup"><span data-stu-id="0282c-111">The default is `MiddleCenter`.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a><span data-ttu-id="0282c-112">Aby wyrównać obrazu elementu ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="0282c-112">To align an image on a ToolStripItem</span></span>  
  
- <span data-ttu-id="0282c-113">Ustaw <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> właściwości na żądaną wartość.</span><span class="sxs-lookup"><span data-stu-id="0282c-113">Set the <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> property to the desired value.</span></span> <span data-ttu-id="0282c-114">Możliwości są dowolną kombinację początku, środka i na dole z lewej strony, wyśrodkowanie i po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="0282c-114">The possibilities are any combination of top, middle, and bottom with left, center, and right.</span></span> <span data-ttu-id="0282c-115">Wartość domyślna to `MiddleLeft`.</span><span class="sxs-lookup"><span data-stu-id="0282c-115">The default is `MiddleLeft`.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a><span data-ttu-id="0282c-116">Aby zdefiniować sposób wyświetlania ToolStripItem tekst i obrazy względem siebie</span><span class="sxs-lookup"><span data-stu-id="0282c-116">To define how ToolStripItem text and images are displayed relative to each other</span></span>  
  
- <span data-ttu-id="0282c-117">Ustaw <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> właściwości na żądaną wartość.</span><span class="sxs-lookup"><span data-stu-id="0282c-117">Set the <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> property to the desired value.</span></span> <span data-ttu-id="0282c-118">Możliwości są `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, i `TextBeforeImage`.</span><span class="sxs-lookup"><span data-stu-id="0282c-118">The possibilities are `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, and `TextBeforeImage`.</span></span> <span data-ttu-id="0282c-119">Wartość domyślna to `ImageBeforeText`.</span><span class="sxs-lookup"><span data-stu-id="0282c-119">The default is `ImageBeforeText`.</span></span>  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0282c-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0282c-120">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="0282c-121">ToolStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="0282c-121">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="0282c-122">ToolStrip, kontrolka — architektura</span><span class="sxs-lookup"><span data-stu-id="0282c-122">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="0282c-123">ToolStrip — podsumowanie informacji o technologii</span><span class="sxs-lookup"><span data-stu-id="0282c-123">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
