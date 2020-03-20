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
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a>Porady: ustawianie tła panelu formularzy systemu Windows
Formant <xref:System.Windows.Forms.Panel> Formularze systemu Windows może wyświetlać zarówno kolor tła, jak i obraz tła. Właściwość <xref:System.Windows.Forms.Control.BackColor%2A> ustawia kolor tła dla zawartych formantów, takich jak etykiety i przyciski radiowe. Jeśli <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwość nie jest <xref:System.Windows.Forms.Control.BackColor%2A> ustawiona, zaznaczenie wypełni cały panel. Jeśli <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwość jest ustawiona, obraz będzie wyświetlany za zawartymi formantami.  
  
### <a name="to-set-the-background-programmatically"></a>Aby zaprogramować tło  
  
1. Ustaw <xref:System.Windows.Forms.Control.BackColor%2A> właściwość panelu na wartość <xref:System.Drawing.Color?displayProperty=nameWithType>typu .  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. Ustaw <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwość panelu przy <xref:System.Drawing.Image.FromFile%2A> użyciu <xref:System.Drawing.Image?displayProperty=nameWithType> metody klasy.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Panel — Formant](panel-control-windows-forms.md)
- [Panel, kontrolka — omówienie](panel-control-overview-windows-forms.md)
