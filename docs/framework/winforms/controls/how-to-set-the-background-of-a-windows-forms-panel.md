---
title: "Porady: ustawianie tła panelu formularzy systemu Windows"
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
- cpp
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: 096cbd8d-45cc-47b8-b1ef-a27f60ea8be0
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 60a1c89375ac7ce9bdefaa051b51ac50be861903
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a><span data-ttu-id="efc8f-102">Porady: ustawianie tła panelu formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="efc8f-102">How to: Set the Background of a Windows Forms Panel</span></span>
<span data-ttu-id="efc8f-103">Formularze systemu Windows <xref:System.Windows.Forms.Panel> formant może wyświetlać zarówno kolor tła i obraz tła.</span><span class="sxs-lookup"><span data-stu-id="efc8f-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="efc8f-104"><xref:System.Windows.Forms.Control.BackColor%2A> Właściwość ustawia kolor tła formantów zawartych w niej, takich jak etykiety i przycisków radiowych.</span><span class="sxs-lookup"><span data-stu-id="efc8f-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for the contained controls, such as labels and radio buttons.</span></span> <span data-ttu-id="efc8f-105">Jeśli <xref:System.Windows.Forms.Control.BackgroundImage%2A> nie ustawiono właściwości <xref:System.Windows.Forms.Control.BackColor%2A> wyboru spowoduje wypełnienie cały panel.</span><span class="sxs-lookup"><span data-stu-id="efc8f-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill the entire panel.</span></span> <span data-ttu-id="efc8f-106">Jeśli <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwość jest ustawiona, obrazu będzie wyświetlany za formanty zawarte.</span><span class="sxs-lookup"><span data-stu-id="efc8f-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the contained controls.</span></span>  
  
### <a name="to-set-the-background-programmatically"></a><span data-ttu-id="efc8f-107">Aby ustawić programowo w tle</span><span class="sxs-lookup"><span data-stu-id="efc8f-107">To set the background programmatically</span></span>  
  
1.  <span data-ttu-id="efc8f-108">Ustaw panelu <xref:System.Windows.Forms.Control.BackColor%2A> właściwości na wartość typu <xref:System.Drawing.Color?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="efc8f-108">Set the panel's <xref:System.Windows.Forms.Control.BackColor%2A> property to a value of type <xref:System.Drawing.Color?displayProperty=nameWithType>.</span></span>  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2.  <span data-ttu-id="efc8f-109">Ustaw panelu <xref:System.Windows.Forms.Control.BackgroundImage%2A> za pomocą właściwości <xref:System.Drawing.Image.FromFile%2A> metody <xref:System.Drawing.Image?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="efc8f-109">Set the panel's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image?displayProperty=nameWithType> class.</span></span>  
  
    ```vb  
    ' You should replace the bolded image   
    ' in the sample below with an image of your own choosing.  
    Panel1.BackgroundImage = Image.FromFile _  
        (System.Environment.GetFolderPath _  
        (System.Environment.SpecialFolder.Personal) _  
        & "\Image.gif")  
    ```  
  
    ```csharp  
    // You should replace the bolded image   
    // in the sample below with an image of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    panel1.BackgroundImage = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    ```  
  
    ```cpp  
    // You should replace the bolded image   
    // in the sample below with an image of your own choosing.  
    panel1->BackgroundImage = Image::FromFile(String::Concat(  
       System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\Image.gif"));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="efc8f-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="efc8f-110">See Also</span></span>  
 <xref:System.Windows.Forms.Control.BackColor%2A>  
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>  
 [<span data-ttu-id="efc8f-111">Panel — formant</span><span class="sxs-lookup"><span data-stu-id="efc8f-111">Panel Control</span></span>](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)  
 [<span data-ttu-id="efc8f-112">Panel — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="efc8f-112">Panel Control Overview</span></span>](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)
