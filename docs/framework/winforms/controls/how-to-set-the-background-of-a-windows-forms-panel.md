---
title: ustawianie tła panelu
description: Dowiedz się, jak ustawić kolor tła i obraz tła panelu Windows Forms przy użyciu narzędzia Projektant.
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
ms.openlocfilehash: 109ff6184de9c79d1576207bbeb29ad939670b6f
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173383"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel"></a>Porady: ustawianie tła panelu formularzy systemu Windows
<xref:System.Windows.Forms.Panel>Kontrolka Windows Forms może wyświetlać zarówno kolor tła, jak i obraz tła. <xref:System.Windows.Forms.Control.BackColor%2A>Właściwość ustawia kolor tła zawartych kontrolek, takich jak etykiety i przyciski radiowe. Jeśli <xref:System.Windows.Forms.Control.BackgroundImage%2A> Właściwość nie jest ustawiona, <xref:System.Windows.Forms.Control.BackColor%2A> Zaznaczenie spowoduje wypełnienie całego panelu. Jeśli <xref:System.Windows.Forms.Control.BackgroundImage%2A> Właściwość jest ustawiona, obraz zostanie wyświetlony za zawartymi kontrolkami.  
  
### <a name="to-set-the-background-programmatically"></a>Aby programowo ustawić tło  
  
1. Ustaw <xref:System.Windows.Forms.Control.BackColor%2A> Właściwość panelu na wartość typu <xref:System.Drawing.Color?displayProperty=nameWithType> .  
  
    ```vb  
    Panel1.BackColor = Color.AliceBlue  
    ```  
  
    ```csharp  
    panel1.BackColor = Color.AliceBlue;  
    ```  
  
    ```cpp  
    panel1->BackColor = Color::AliceBlue;  
    ```  
  
2. Ustaw <xref:System.Windows.Forms.Control.BackgroundImage%2A> Właściwość panelu przy użyciu <xref:System.Drawing.Image.FromFile%2A> metody <xref:System.Drawing.Image?displayProperty=nameWithType> klasy.  
  
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
