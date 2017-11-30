---
title: 'Porady: dzielenie okna w poziomie'
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
- SplitContainer control [Windows Forms], horizontal splitter
- splitter windows [Windows Forms], changing splitter orientation
- splitter windows [Windows Forms], horizontal
- windows [Windows Forms], splitting horizontally
ms.assetid: a1f74f29-048c-4723-85fa-b9d375ab8f4b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 02133cc38221b23ea1e2b14bfd0bbcf1987ab532
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-split-a-window-horizontally"></a><span data-ttu-id="220a3-102">Porady: dzielenie okna w poziomie</span><span class="sxs-lookup"><span data-stu-id="220a3-102">How to: Split a Window Horizontally</span></span>
<span data-ttu-id="220a3-103">Poniższy przykład kodu sprawia, że podziału, która dzieli <xref:System.Windows.Forms.SplitContainer> poziome formantu.</span><span class="sxs-lookup"><span data-stu-id="220a3-103">The following code example makes the splitter that divides the <xref:System.Windows.Forms.SplitContainer> control horizontal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="220a3-104"><xref:System.Windows.Forms.SplitContainer.Orientation%2A> Właściwość <xref:System.Windows.Forms.SplitContainer> kontroli określa kierunek rozdzielacza, a nie samego formantu.</span><span class="sxs-lookup"><span data-stu-id="220a3-104">The <xref:System.Windows.Forms.SplitContainer.Orientation%2A> property of the <xref:System.Windows.Forms.SplitContainer> control determines the direction of the splitter, not of the control itself.</span></span>  
  
### <a name="to-split-a-window-horizontally"></a><span data-ttu-id="220a3-105">Aby Dzielenie okna w poziomie</span><span class="sxs-lookup"><span data-stu-id="220a3-105">To split a window horizontally</span></span>  
  
1.  <span data-ttu-id="220a3-106">W procedurze, ustaw <xref:System.Windows.Forms.SplitContainer.Orientation%2A> właściwość <xref:System.Windows.Forms.SplitContainer> formant <xref:System.Windows.Forms.Orientation.Horizontal>.</span><span class="sxs-lookup"><span data-stu-id="220a3-106">Within a procedure, set the <xref:System.Windows.Forms.SplitContainer.Orientation%2A> property of the <xref:System.Windows.Forms.SplitContainer> control to <xref:System.Windows.Forms.Orientation.Horizontal>.</span></span>  
  
    ```vb  
    Sub ShowSplitContainer()  
        Dim splitContainer1 as new SplitContainer()  
        splitContainer1.BorderStyle = BorderStyle.Fixed3D  
        splitContainer1.Location = New System.Drawing.Point(74, 20)  
        splitContainer1.Name = "DemoSplitContainer"  
        splitContainer1.Size = New System.Drawing.Size(212, 435)  
        splitContainer1.TabIndex = 0  
        splitContainer1.Orientation = Orientation.Horizontal  
        Controls.Add(splitContainer1)  
    End Sub  
    ```  
  
    ```csharp  
    public void showSplitContainer()  
    {  
        SplitContainer splitContainer1 = new SplitContainer ();  
        splitContainer1.BorderStyle = BorderStyle.Fixed3D;  
        splitContainer1.Location = new System.Drawing.Point (74, 20);  
        splitContainer1.Name = "DemoSplitContainer";  
        splitContainer1.Size = new System.Drawing.Size (212, 435);  
        splitContainer1.TabIndex = 0;  
        splitContainer1.Orientation = Orientation.Horizontal;  
        this.Controls.Add (splitContainer1);  
  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="220a3-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="220a3-107">See Also</span></span>  
 <xref:System.Windows.Forms.SplitContainer>  
 [<span data-ttu-id="220a3-108">SplitContainer — formant</span><span class="sxs-lookup"><span data-stu-id="220a3-108">SplitContainer Control</span></span>](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
