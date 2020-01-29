---
title: 'Porady: modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania'
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
ms.openlocfilehash: 9bb094ce0b7945f23a2e9b8614e56c9492d5f832
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736027"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a>Porady: modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania (Formularze systemu Windows)
Jeśli używasz kontrolki <xref:System.Windows.Forms.PictureBox> Windows Forms w formularzu, możesz ustawić właściwość <xref:System.Windows.Forms.PictureBox.SizeMode%2A> na:  
  
- Wyrównaj górny lewy róg obrazu za pomocą lewego górnego rogu kontrolki  
  
- Wyśrodkuj obraz w kontrolce  
  
- Dostosuj rozmiar kontrolki do obrazu wyświetlanego  
  
- Rozciągnij wszystkie wyświetlane obrazy, aby dopasować je do formantu  
  
 Rozciąganie obrazu (szczególnie jednego w formacie mapy bitowej) może spowodować utratę jakości obrazu. Pliki, które są listami instrukcji graficznych służących do rysowania obrazów w czasie wykonywania, są lepiej dopasowane do rozciągania niż mapy bitowe.  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a>Aby ustawić właściwość SizeMode w czasie wykonywania  
  
1. Ustaw <xref:System.Windows.Forms.PictureBox.SizeMode%2A> na <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (wartość domyślna), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>lub <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>. <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> oznacza, że obraz jest umieszczany w lewym górnym rogu kontrolki. Jeśli obraz jest większy niż kontrolka, jego dolna i prawa krawędź są przycinane. <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> oznacza, że obraz jest wyśrodkowany w formancie; Jeśli obraz jest większy niż kontrolka, obramowania na zewnątrz obrazu są obcinane. <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> oznacza, że rozmiar kontrolki jest dopasowywany do rozmiaru obrazu. <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> jest odwrotna i oznacza, że rozmiar obrazu jest dopasowywany do rozmiaru formantu.  
  
     W poniższym przykładzie ścieżką ustawioną dla lokalizacji obrazu jest folder Moje dokumenty. Dzieje się tak, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać ten katalog. Pozwala to również użytkownikom z minimalnymi poziomami dostępu do systemu w celu bezpiecznego uruchomienia aplikacji. W poniższym przykładzie założono, że formularz z kontrolką <xref:System.Windows.Forms.PictureBox> został już dodany.  
  
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
- [Instrukcje: dodawanie zdjęcia przy użyciu narzędzia Projektant](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [PictureBox, kontrolka — omówienie](picturebox-control-overview-windows-forms.md)
- [Instrukcje: ustawienie obrazów w czasie wykonywania](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox, kontrolka](picturebox-control-windows-forms.md)
