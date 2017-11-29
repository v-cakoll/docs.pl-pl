---
title: "Porady: zmienianie wyglądu tekstu i obrazów elementów ToolStrip w formularzach systemu Windows"
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
- ToolStrip control [Windows Forms], appearance
- toolbars [Windows Forms], images
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], appearance
- ToolStrip control [Windows Forms], images
- ToolStrip control [Windows Forms], text
- toolbars [Windows Forms], text
ms.assetid: d62dc9d1-2edd-4dfa-aed7-1335d6e13d86
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1d926ce74db9723b6248dbb123513ca38d4adb1d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a><span data-ttu-id="ebfb1-102">Porady: zmienianie wyglądu tekstu i obrazów elementów ToolStrip w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ebfb1-102">How to: Change the Appearance of ToolStrip Text and Images in Windows Forms</span></span>
<span data-ttu-id="ebfb1-103">Można kontrolować, czy tekst i obrazy są wyświetlane na <xref:System.Windows.Forms.ToolStripItem> i jak są wyrównane względem siebie i <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="ebfb1-103">You can control whether text and images are displayed on a <xref:System.Windows.Forms.ToolStripItem> and how they are aligned relative to each other and the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a><span data-ttu-id="ebfb1-104">Aby zdefiniować, co jest wyświetlane na element ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="ebfb1-104">To define what is displayed on a ToolStripItem</span></span>  
  
-   <span data-ttu-id="ebfb1-105">Ustaw <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> na żądaną wartość.</span><span class="sxs-lookup"><span data-stu-id="ebfb1-105">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to the desired value.</span></span> <span data-ttu-id="ebfb1-106">Możliwości są `Image`, `ImageAndText`, `None`, i `Text`.</span><span class="sxs-lookup"><span data-stu-id="ebfb1-106">The possibilities are `Image`, `ImageAndText`, `None`, and `Text`.</span></span> <span data-ttu-id="ebfb1-107">Wartość domyślna to `ImageAndText`.</span><span class="sxs-lookup"><span data-stu-id="ebfb1-107">The default is `ImageAndText`.</span></span>  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a><span data-ttu-id="ebfb1-108">Wyrównanie tekstu na element ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="ebfb1-108">To align text on a ToolStripItem</span></span>  
  
-   <span data-ttu-id="ebfb1-109">Ustaw <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> na żądaną wartość.</span><span class="sxs-lookup"><span data-stu-id="ebfb1-109">Set the <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> property to the desired value.</span></span> <span data-ttu-id="ebfb1-110">Możliwości są dowolną kombinację góry, drugie i u dołu po lewej, wyśrodkowanie i po prawej.</span><span class="sxs-lookup"><span data-stu-id="ebfb1-110">The possibilities are any combination of top, middle, and bottom with left, center, and right.</span></span> <span data-ttu-id="ebfb1-111">Wartość domyślna to `MiddleCenter`.</span><span class="sxs-lookup"><span data-stu-id="ebfb1-111">The default is `MiddleCenter`.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a><span data-ttu-id="ebfb1-112">Aby wyrównać obraz na element ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="ebfb1-112">To align an image on a ToolStripItem</span></span>  
  
-   <span data-ttu-id="ebfb1-113">Ustaw <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> na żądaną wartość.</span><span class="sxs-lookup"><span data-stu-id="ebfb1-113">Set the <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> property to the desired value.</span></span> <span data-ttu-id="ebfb1-114">Możliwości są dowolną kombinację góry, drugie i u dołu po lewej, wyśrodkowanie i po prawej.</span><span class="sxs-lookup"><span data-stu-id="ebfb1-114">The possibilities are any combination of top, middle, and bottom with left, center, and right.</span></span> <span data-ttu-id="ebfb1-115">Wartość domyślna to `MiddleLeft`.</span><span class="sxs-lookup"><span data-stu-id="ebfb1-115">The default is `MiddleLeft`.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a><span data-ttu-id="ebfb1-116">Aby zdefiniować sposób wyświetlania ToolStripItem tekst i obrazy względem siebie</span><span class="sxs-lookup"><span data-stu-id="ebfb1-116">To define how ToolStripItem text and images are displayed relative to each other</span></span>  
  
-   <span data-ttu-id="ebfb1-117">Ustaw <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> na żądaną wartość.</span><span class="sxs-lookup"><span data-stu-id="ebfb1-117">Set the <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> property to the desired value.</span></span> <span data-ttu-id="ebfb1-118">Możliwości są `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, i `TextBeforeImage`.</span><span class="sxs-lookup"><span data-stu-id="ebfb1-118">The possibilities are `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, and `TextBeforeImage`.</span></span> <span data-ttu-id="ebfb1-119">Wartość domyślna to `ImageBeforeText`.</span><span class="sxs-lookup"><span data-stu-id="ebfb1-119">The default is `ImageBeforeText`.</span></span>  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ebfb1-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ebfb1-120">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 [<span data-ttu-id="ebfb1-121">Informacje o formancie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ebfb1-121">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="ebfb1-122">ToolStrip — architektura formantu</span><span class="sxs-lookup"><span data-stu-id="ebfb1-122">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="ebfb1-123">Podsumowanie technologii formantów ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ebfb1-123">ToolStrip Technology Summary</span></span>](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
