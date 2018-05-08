---
title: 'Porady: ustawienie obrazów w czasie wykonywania (Formularze systemu Windows)'
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
ms.openlocfilehash: fedddf56966c3ab11a1dfb20c1d4cbd8a45fb1a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a>Porady: ustawienie obrazów w czasie wykonywania (Formularze systemu Windows)
Można programowo Ustawianie obrazu wyświetlanego przez program Windows Forms <xref:System.Windows.Forms.PictureBox> formantu.  
  
### <a name="to-set-a-picture-programmatically"></a>Aby ustawić programowo obrazu  
  
-   Ustaw <xref:System.Windows.Forms.PictureBox.Image%2A> za pomocą właściwości <xref:System.Drawing.Image.FromFile%2A> metody <xref:System.Drawing.Image> klasy.  
  
     W poniższym przykładzie ścieżka zestawu dla lokalizacji obrazu jest folder Moje dokumenty. Tej operacji, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać tego katalogu. To umożliwia użytkownikom z poziomami dostępu minimalny system bezpiecznego uruchamiania aplikacji. W poniższym przykładzie założono formularza z <xref:System.Windows.Forms.PictureBox> kontroli już dodany.  
  
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
  
### <a name="to-clear-a-graphic"></a>Aby wyczyścić grafiki  
  
-   Po pierwsze zwalniają pamięć używana przez obraz, a następnie wyczyść grafiki. Wyrzucanie elementów bezużytecznych zwolnić pamięć później w przypadku zarządzania pamięcią problem.  
  
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
    >  Aby uzyskać więcej informacji o tym, dlaczego należy używać <xref:System.Drawing.Image.Dispose%2A> metody w ten sposób, zobacz [czyszczenie zasobów niezarządzanych](../../../../docs/standard/garbage-collection/unmanaged.md).  
  
     Ten kod spowoduje wyczyszczenie obrazu, nawet jeśli grafiki został załadowany do formantu w czasie projektowania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.PictureBox>  
 <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>  
 [PictureBox, kontrolka — omówienie](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [Instrukcje: dodawanie zdjęcia przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)  
 [Instrukcje: modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)  
 [PictureBox, kontrolka](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
