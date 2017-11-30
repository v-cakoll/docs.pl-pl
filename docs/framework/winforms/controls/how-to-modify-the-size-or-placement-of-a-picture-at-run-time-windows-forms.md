---
title: "Porady: modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania (Formularze systemu Windows)"
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
- images [Windows Forms], controlling placement in PictureBox control [Windows Forms]
- examples [Windows Forms], PictureBox control
- PictureBox control [Windows Forms], picture size and alignment
- pictures [Windows Forms], controlling placement in PictureBox control [Windows Forms]
ms.assetid: d0b332a3-fae2-4891-957c-dc3e17743326
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: df67871b0b133297a6f53ff9e4a42c7630a5f56d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a>Porady: modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania (Formularze systemu Windows)
Jeśli używasz interfejsu Windows Forms <xref:System.Windows.Forms.PictureBox> kontrolki na formularzu, można ustawić <xref:System.Windows.Forms.PictureBox.SizeMode%2A> właściwości w celu:  
  
-   Wyrównanie obrazu lewym górnym rogu z lewym górnym rogu formantu  
  
-   Centrum obrazów w formancie  
  
-   Dopasuj rozmiar formantu w celu dopasowania obraz, który zawiera  
  
-   Rozciąganie obrazu wyświetla do rozmiaru formantu  
  
 Rozciąganie obrazu (szczególnie jeden format mapy bitowej) może spowodować utratę jakości obrazu. Metapliki, które list grafiki instrukcje dotyczące rysowanie obrazów w czasie wykonywania, są lepiej dostosowane do rozciągania niż map bitowych.  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a>Można ustawić właściwości SizeMode w czasie wykonywania  
  
1.  Ustaw <xref:System.Windows.Forms.PictureBox.SizeMode%2A> do <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (ustawienie domyślne), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, lub <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>. <xref:System.Windows.Forms.PictureBoxSizeMode.Normal>oznacza, że obraz jest umieszczany w formantu lewego górnego rogu; Jeśli obraz jest większy niż formant, jego dolnej i prawej krawędzi są obcinane. <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>oznacza, że obraz jest wyśrodkowywany względem kontroli. Jeśli obraz jest większy niż formant, zewnętrznej krawędzi obrazu są obcinane. <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>oznacza, że rozmiar formantu zostanie dopasowana do rozmiaru obrazu. <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>jest odwrotna i oznacza, że rozmiar obrazu jest dostosowana do rozmiaru formantu.  
  
     W poniższym przykładzie ścieżka zestawu dla lokalizacji obrazu jest folder Moje dokumenty. Tej operacji, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać tego katalogu. To umożliwia użytkownikom z poziomami dostępu minimalny system bezpiecznego uruchamiania aplikacji. W poniższym przykładzie założono formularza z <xref:System.Windows.Forms.PictureBox> kontroli już dodany.  
  
    ```vb  
    Private Sub StretchPic()  
       ' Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage  
       ' Load the picture into the control.  
       ' You should replace the bold image   
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void StretchPic(){  
       // Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage;  
       // Load the picture into the control.  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\Image.gif")  
    }  
    ```  
  
    ```cpp  
    private:  
       void StretchPic()  
       {  
          // Stretch the picture to fit the control.  
          pictureBox1->SizeMode = PictureBoxSizeMode::StretchImage;  
          // Load the picture into the control.  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.PictureBox>  
 [Porady: Dodawanie zdjęcia przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)  
 [Informacje o formancie PictureBox](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [Porady: ustawienie obrazów w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)  
 [PictureBox — formant](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
