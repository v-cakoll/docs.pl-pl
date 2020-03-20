---
title: ustawianie tła panelu
ms.date: 03/30/2017
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
ms.openlocfilehash: 36e552475334c25b9d5a6fafb82155c6ebcba266
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182109"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a><span data-ttu-id="303e5-102">Porady: ustawianie tła panelu formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="303e5-102">How to: Set the Background of a Windows Forms Panel</span></span>
<span data-ttu-id="303e5-103">Formant <xref:System.Windows.Forms.Panel> Formularze systemu Windows może wyświetlać zarówno kolor tła, jak i obraz tła.</span><span class="sxs-lookup"><span data-stu-id="303e5-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="303e5-104">Właściwość <xref:System.Windows.Forms.Control.BackColor%2A> ustawia kolor tła dla zawartych formantów, takich jak etykiety i przyciski radiowe.</span><span class="sxs-lookup"><span data-stu-id="303e5-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for the contained controls, such as labels and radio buttons.</span></span> <span data-ttu-id="303e5-105">Jeśli <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwość nie jest <xref:System.Windows.Forms.Control.BackColor%2A> ustawiona, zaznaczenie wypełni cały panel.</span><span class="sxs-lookup"><span data-stu-id="303e5-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill the entire panel.</span></span> <span data-ttu-id="303e5-106">Jeśli <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwość jest ustawiona, obraz będzie wyświetlany za zawartymi formantami.</span><span class="sxs-lookup"><span data-stu-id="303e5-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the contained controls.</span></span>  
  
### <a name="to-set-the-background-programmatically"></a><span data-ttu-id="303e5-107">Aby zaprogramować tło</span><span class="sxs-lookup"><span data-stu-id="303e5-107">To set the background programmatically</span></span>  
  
1. <span data-ttu-id="303e5-108">Ustaw <xref:System.Windows.Forms.Control.BackColor%2A> właściwość panelu na wartość <xref:System.Drawing.Color?displayProperty=nameWithType>typu .</span><span class="sxs-lookup"><span data-stu-id="303e5-108">Set the panel's <xref:System.Windows.Forms.Control.BackColor%2A> property to a value of type <xref:System.Drawing.Color?displayProperty=nameWithType>.</span></span>  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. <span data-ttu-id="303e5-109">Ustaw <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwość panelu przy <xref:System.Drawing.Image.FromFile%2A> użyciu <xref:System.Drawing.Image?displayProperty=nameWithType> metody klasy.</span><span class="sxs-lookup"><span data-stu-id="303e5-109">Set the panel's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image?displayProperty=nameWithType> class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="303e5-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="303e5-110">See also</span></span>

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="303e5-111">Panel — Formant</span><span class="sxs-lookup"><span data-stu-id="303e5-111">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="303e5-112">Panel, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="303e5-112">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
