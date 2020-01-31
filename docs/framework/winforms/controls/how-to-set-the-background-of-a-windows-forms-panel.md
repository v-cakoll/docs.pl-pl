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
ms.openlocfilehash: ba2619354403793aea7ca15d43649da9637079a6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744742"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a><span data-ttu-id="526de-102">Porady: ustawianie tła panelu formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="526de-102">How to: Set the Background of a Windows Forms Panel</span></span>
<span data-ttu-id="526de-103">Kontrolka <xref:System.Windows.Forms.Panel> Windows Forms może wyświetlać zarówno kolor tła, jak i obraz tła.</span><span class="sxs-lookup"><span data-stu-id="526de-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="526de-104">Właściwość <xref:System.Windows.Forms.Control.BackColor%2A> ustawia kolor tła zawartych kontrolek, takich jak etykiety i przyciski radiowe.</span><span class="sxs-lookup"><span data-stu-id="526de-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for the contained controls, such as labels and radio buttons.</span></span> <span data-ttu-id="526de-105">Jeśli właściwość <xref:System.Windows.Forms.Control.BackgroundImage%2A> nie jest ustawiona, wybór <xref:System.Windows.Forms.Control.BackColor%2A> wypełni cały panel.</span><span class="sxs-lookup"><span data-stu-id="526de-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill the entire panel.</span></span> <span data-ttu-id="526de-106">Jeśli właściwość <xref:System.Windows.Forms.Control.BackgroundImage%2A> jest ustawiona, obraz zostanie wyświetlony za zawartymi kontrolkami.</span><span class="sxs-lookup"><span data-stu-id="526de-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the contained controls.</span></span>  
  
### <a name="to-set-the-background-programmatically"></a><span data-ttu-id="526de-107">Aby programowo ustawić tło</span><span class="sxs-lookup"><span data-stu-id="526de-107">To set the background programmatically</span></span>  
  
1. <span data-ttu-id="526de-108">Ustaw właściwość <xref:System.Windows.Forms.Control.BackColor%2A> panelu na wartość typu <xref:System.Drawing.Color?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="526de-108">Set the panel's <xref:System.Windows.Forms.Control.BackColor%2A> property to a value of type <xref:System.Drawing.Color?displayProperty=nameWithType>.</span></span>  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. <span data-ttu-id="526de-109">Ustaw właściwość <xref:System.Windows.Forms.Control.BackgroundImage%2A> panelu przy użyciu metody <xref:System.Drawing.Image.FromFile%2A> klasy <xref:System.Drawing.Image?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="526de-109">Set the panel's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image?displayProperty=nameWithType> class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="526de-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="526de-110">See also</span></span>

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="526de-111">Panel, kontrolka</span><span class="sxs-lookup"><span data-stu-id="526de-111">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="526de-112">Panel, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="526de-112">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
