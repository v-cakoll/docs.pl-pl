---
title: 'Porady: ustawienie obrazów w czasie wykonywania'
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
ms.openlocfilehash: cd599ac7e07b5210f8bcff1ffbc76b3d9ee563d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182118"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a>Porady: ustawienie obrazów w czasie wykonywania (Formularze systemu Windows)
Obraz wyświetlany jest programowo za pomocą kontrolki Windows Forms. <xref:System.Windows.Forms.PictureBox>  
  
### <a name="to-set-a-picture-programmatically"></a>Aby zaprogramować obraz  
  
- Ustaw <xref:System.Windows.Forms.PictureBox.Image%2A> właściwość <xref:System.Drawing.Image.FromFile%2A> przy użyciu <xref:System.Drawing.Image> metody klasy.  
  
     W poniższym przykładzie ścieżką ustawioną dla lokalizacji obrazu jest folder Moje dokumenty. Odbywa się to, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać ten katalog. Umożliwia to również użytkownikom z minimalnymi poziomami dostępu do systemu bezpieczne uruchamianie aplikacji. Poniższy przykład zakłada formularz <xref:System.Windows.Forms.PictureBox> z formantu już dodane.  
  
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
  
- Najpierw zwolnij pamięć używaną przez obraz, a następnie wyczyść grafikę. Wyrzucanie elementów bezużytecznych spowoduje później zwolnić pamięć, jeśli zarządzanie pamięcią staje się problemem.  
  
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
    > Aby uzyskać więcej informacji na <xref:System.Drawing.Image.Dispose%2A> temat powodów, dla których należy użyć tej metody w ten sposób, zobacz [Czyszczenie zasobów niezarządzanych](../../../standard/garbage-collection/unmanaged.md).  
  
     Ten kod wyczyści obraz, nawet jeśli grafika została załadowana do formantu w czasie projektowania.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [PictureBox — Informacje o formancie](picturebox-control-overview-windows-forms.md)
- [Instrukcje: dodawanie zdjęcia przy użyciu narzędzia Projektant](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [Instrukcje: modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [PictureBox — Formant](picturebox-control-windows-forms.md)
