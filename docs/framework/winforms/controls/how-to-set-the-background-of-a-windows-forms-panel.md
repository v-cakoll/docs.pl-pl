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
ms.openlocfilehash: b0cf7666e6d969b3d02d13e86eb45904307d3ce3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722688"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a>Instrukcje: Ustawianie tła panelu formularzy Windows
Formularze Windows <xref:System.Windows.Forms.Panel> formant może wyświetlić kolor tła i obraz tła. <xref:System.Windows.Forms.Control.BackColor%2A> Właściwość ustawia kolor tła dla zawartych w nim formantów, takich jak etykiety i przycisków radiowych. Jeśli <xref:System.Windows.Forms.Control.BackgroundImage%2A> nie ustawiono właściwości <xref:System.Windows.Forms.Control.BackColor%2A> wybór wypełni całą panelu. Jeśli <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwość jest ustawiona, obraz, który pojawi się za zaporą zawartych w nim formantów.  
  
### <a name="to-set-the-background-programmatically"></a>Aby programowo ustawić tło  
  
1.  Ustaw panelu <xref:System.Windows.Forms.Control.BackColor%2A> właściwości na wartość typu <xref:System.Drawing.Color?displayProperty=nameWithType>.  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2.  Ustaw panelu <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwość za pomocą <xref:System.Drawing.Image.FromFile%2A> metody <xref:System.Drawing.Image?displayProperty=nameWithType> klasy.  
  
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
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Panel, kontrolka](panel-control-windows-forms.md)
- [Panel, kontrolka — omówienie](panel-control-overview-windows-forms.md)
