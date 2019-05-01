---
title: 'Instrukcje: Modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania (formularze Windows)'
ms.date: 03/30/2017
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
ms.openlocfilehash: d0a86d7fe53dba3da6bd63587561f82877bc2f06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913734"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a>Instrukcje: Modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania (formularze Windows)
Jeśli używasz formularzy Windows <xref:System.Windows.Forms.PictureBox> formantu w formularzu, można ustawić <xref:System.Windows.Forms.PictureBox.SizeMode%2A> właściwości na niej w celu:  
  
- Wyrównanie obrazu lewy górny róg za pomocą lewego górnego rogu kontrolki  
  
- Wyśrodkuj obraz w kontrolce  
  
- Dopasuj rozmiar formantu, aby dopasować go do jego wyświetlania  
  
- Rozciąganie dowolnego obrazu wyświetla do rozmiaru formantu  
  
 Rozciąganie obrazu (szczególnie jeden format mapy bitowej) może spowodować utratę jakości obrazu. Metapliki, które listy instrukcji grafiki rysowanie obrazów w czasie wykonywania, są lepiej dostosowane do rozciągania niż Mapy bitowe mają rozmiar.  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a>Aby ustawić właściwość SizeMode w czasie wykonywania  
  
1. Ustaw <xref:System.Windows.Forms.PictureBox.SizeMode%2A> do <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (ustawienie domyślne), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, lub <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>. <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> oznacza, że obraz jest umieszczany w formantu lewego górnego rogu; obraz, który jest większy niż formant, powoduje jej dolnej i prawej krawędzi. <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> oznacza, że obraz jest wyśrodkowywana względem kontroli. obraz, który jest większy niż formant, powoduje zewnętrznymi krawędziami obrazu. <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> oznacza to, że rozmiar formantu jest dostosowywana do rozmiaru obrazu. <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> jest odwrotna i oznacza, że rozmiar obrazu jest dostosowywana do rozmiaru formantu.  
  
     W poniższym przykładzie ścieżka lokalizacji obrazu jest folder Moje dokumenty. Jest to wykonywane, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać tego katalogu. Ponadto pozwala to użytkownikom z poziomami dostępu minimalny system bezpiecznego uruchamiania aplikacji. W poniższym przykładzie przyjęto założenie, formularz z <xref:System.Windows.Forms.PictureBox> formant został już dodany.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.PictureBox>
- [Instrukcje: Zdjęcia przy użyciu narzędzia Projektant](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [PictureBox, kontrolka — omówienie](picturebox-control-overview-windows-forms.md)
- [Instrukcje: Ustawienie obrazów w czasie wykonywania](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox, kontrolka](picturebox-control-windows-forms.md)
