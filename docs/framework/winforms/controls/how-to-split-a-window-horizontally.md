---
title: 'Instrukcje: dzielenie okna w poziomie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SplitContainer control [Windows Forms], horizontal splitter
- splitter windows [Windows Forms], changing splitter orientation
- splitter windows [Windows Forms], horizontal
- windows [Windows Forms], splitting horizontally
ms.assetid: a1f74f29-048c-4723-85fa-b9d375ab8f4b
ms.openlocfilehash: a43d632a82678f362a1cdf6b3ee4486a8db5adde
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012935"
---
# <a name="how-to-split-a-window-horizontally"></a><span data-ttu-id="4e54d-102">Instrukcje: dzielenie okna w poziomie</span><span class="sxs-lookup"><span data-stu-id="4e54d-102">How to: Split a Window Horizontally</span></span>
<span data-ttu-id="4e54d-103">Poniższy przykład kodu tworzy podziału, która dzieli <xref:System.Windows.Forms.SplitContainer> kontrolki w poziomie.</span><span class="sxs-lookup"><span data-stu-id="4e54d-103">The following code example makes the splitter that divides the <xref:System.Windows.Forms.SplitContainer> control horizontal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e54d-104"><xref:System.Windows.Forms.SplitContainer.Orientation%2A> Właściwość <xref:System.Windows.Forms.SplitContainer> kontroli określa kierunek rozdzielacza, a nie sam formant.</span><span class="sxs-lookup"><span data-stu-id="4e54d-104">The <xref:System.Windows.Forms.SplitContainer.Orientation%2A> property of the <xref:System.Windows.Forms.SplitContainer> control determines the direction of the splitter, not of the control itself.</span></span>  
  
### <a name="to-split-a-window-horizontally"></a><span data-ttu-id="4e54d-105">Aby Dzielenie okna w poziomie</span><span class="sxs-lookup"><span data-stu-id="4e54d-105">To split a window horizontally</span></span>  
  
1. <span data-ttu-id="4e54d-106">W ramach procedury, należy ustawić <xref:System.Windows.Forms.SplitContainer.Orientation%2A> właściwość <xref:System.Windows.Forms.SplitContainer> kontrolę <xref:System.Windows.Forms.Orientation.Horizontal>.</span><span class="sxs-lookup"><span data-stu-id="4e54d-106">Within a procedure, set the <xref:System.Windows.Forms.SplitContainer.Orientation%2A> property of the <xref:System.Windows.Forms.SplitContainer> control to <xref:System.Windows.Forms.Orientation.Horizontal>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4e54d-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e54d-107">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="4e54d-108">SplitContainer, kontrolka</span><span class="sxs-lookup"><span data-stu-id="4e54d-108">SplitContainer Control</span></span>](splitcontainer-control-windows-forms.md)
