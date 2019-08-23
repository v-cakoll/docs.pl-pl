---
title: 'Instrukcje: Ustaw obrazy w czasie wykonywania (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- pictures [Windows Forms], setting display
- examples [Windows Forms], PictureBox control
- bitmaps [Windows Forms], displaying in PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding images
- images [Windows Forms], adding with PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 18ca41d0-68a5-4660-985e-a6c1fbc01d76
ms.openlocfilehash: 99d78a275c8ad8f55d9b0832a794545b65da7e20
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917527"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a>Instrukcje: Ustaw obrazy w czasie wykonywania (Windows Forms)
Można programowo ustawić obraz wyświetlany przez kontrolkę Windows Forms <xref:System.Windows.Forms.PictureBox> .  
  
### <a name="to-set-a-picture-programmatically"></a>Aby programowo ustawić obraz  
  
- Ustaw właściwość przy użyciu <xref:System.Drawing.Image>metodyklasy. <xref:System.Drawing.Image.FromFile%2A> <xref:System.Windows.Forms.PictureBox.Image%2A>  
  
     W poniższym przykładzie ścieżką ustawioną dla lokalizacji obrazu jest folder Moje dokumenty. Dzieje się tak, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać ten katalog. Pozwala to również użytkownikom z minimalnymi poziomami dostępu do systemu w celu bezpiecznego uruchomienia aplikacji. W poniższym przykładzie założono, że formularz <xref:System.Windows.Forms.PictureBox> z kontrolką został już dodany.  
  
    ```vb  
    Private Sub LoadNewPict()  
       ' You should replace the bold image   
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadNewPict(){  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    }  
    ```  
  
    ```cpp  
    private:  
       void LoadNewPict()  
       {  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
### <a name="to-clear-a-graphic"></a>Aby wyczyścić grafikę  
  
- Po pierwsze zwolnij pamięć używaną przez obraz, a następnie wyczyść grafikę. Wyrzucanie elementów bezużytecznych zwalnia pamięć później, jeśli zarządzanie pamięcią zostanie problemem.  
  
    ```vb  
    If Not (PictureBox1.Image Is Nothing) Then  
       PictureBox1.Image.Dispose()  
       PictureBox1.Image = Nothing  
    End If  
    ```  
  
    ```csharp  
    if (pictureBox1.Image != null)   
    {  
       pictureBox1.Image.Dispose();  
       pictureBox1.Image = null;  
    }  
    ```  
  
    ```cpp  
    if (pictureBox1->Image != nullptr)  
    {  
       pictureBox1->Image->Dispose();  
       pictureBox1->Image = nullptr;  
    }  
    ```  
  
    > [!NOTE]
    > Aby uzyskać więcej informacji na temat tego, dlaczego <xref:System.Drawing.Image.Dispose%2A> należy używać metody w ten sposób, zobacz [Oczyszczanie zasobów niezarządzanych](../../../standard/garbage-collection/unmanaged.md).  
  
     Ten kod spowoduje wyczyszczenie obrazu nawet wtedy, gdy grafika została załadowana do kontrolki w czasie projektowania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [PictureBox, kontrolka — omówienie](picturebox-control-overview-windows-forms.md)
- [Instrukcje: Ładowanie obrazu przy użyciu narzędzia Projektant](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [Instrukcje: Modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [PictureBox, kontrolka](picturebox-control-windows-forms.md)
