---
title: 'Instrukcje: Ustawianie tła panelu formularzy Windows'
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
ms.openlocfilehash: 289a91481c832a36b4b77d56ba6b18921ef02d5b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228011"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a><span data-ttu-id="c7449-102">Instrukcje: Ustawianie tła panelu formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="c7449-102">How to: Set the Background of a Windows Forms Panel</span></span>
<span data-ttu-id="c7449-103">Formularze Windows <xref:System.Windows.Forms.Panel> formant może wyświetlić kolor tła i obraz tła.</span><span class="sxs-lookup"><span data-stu-id="c7449-103">A Windows Forms <xref:System.Windows.Forms.Panel> control can display both a background color and a background image.</span></span> <span data-ttu-id="c7449-104"><xref:System.Windows.Forms.Control.BackColor%2A> Właściwość ustawia kolor tła dla zawartych w nim formantów, takich jak etykiety i przycisków radiowych.</span><span class="sxs-lookup"><span data-stu-id="c7449-104">The <xref:System.Windows.Forms.Control.BackColor%2A> property sets the background color for the contained controls, such as labels and radio buttons.</span></span> <span data-ttu-id="c7449-105">Jeśli <xref:System.Windows.Forms.Control.BackgroundImage%2A> nie ustawiono właściwości <xref:System.Windows.Forms.Control.BackColor%2A> wybór wypełni całą panelu.</span><span class="sxs-lookup"><span data-stu-id="c7449-105">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is not set, the <xref:System.Windows.Forms.Control.BackColor%2A> selection will fill the entire panel.</span></span> <span data-ttu-id="c7449-106">Jeśli <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwość jest ustawiona, obraz, który pojawi się za zaporą zawartych w nim formantów.</span><span class="sxs-lookup"><span data-stu-id="c7449-106">If the <xref:System.Windows.Forms.Control.BackgroundImage%2A> property is set, the image will be displayed behind the contained controls.</span></span>  
  
### <a name="to-set-the-background-programmatically"></a><span data-ttu-id="c7449-107">Aby programowo ustawić tło</span><span class="sxs-lookup"><span data-stu-id="c7449-107">To set the background programmatically</span></span>  
  
1.  <span data-ttu-id="c7449-108">Ustaw panelu <xref:System.Windows.Forms.Control.BackColor%2A> właściwości na wartość typu <xref:System.Drawing.Color?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c7449-108">Set the panel's <xref:System.Windows.Forms.Control.BackColor%2A> property to a value of type <xref:System.Drawing.Color?displayProperty=nameWithType>.</span></span>  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2.  <span data-ttu-id="c7449-109">Ustaw panelu <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwość za pomocą <xref:System.Drawing.Image.FromFile%2A> metody <xref:System.Drawing.Image?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="c7449-109">Set the panel's <xref:System.Windows.Forms.Control.BackgroundImage%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image?displayProperty=nameWithType> class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c7449-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7449-110">See also</span></span>

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [<span data-ttu-id="c7449-111">Panel, kontrolka</span><span class="sxs-lookup"><span data-stu-id="c7449-111">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="c7449-112">Panel, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="c7449-112">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
