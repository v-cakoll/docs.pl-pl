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
ms.openlocfilehash: fea813d7b9fe585e35b729b8b64e3a5f414ef76d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141969"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a>Porady: modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania (Formularze systemu Windows)
Jeśli używasz formantu Windows Forms <xref:System.Windows.Forms.PictureBox> w <xref:System.Windows.Forms.PictureBox.SizeMode%2A> formularzu, można ustawić właściwość na nim:  
  
- Wyrównaj lewy górny róg obrazu z lewym górnym rogu formantu  
  
- Wyśrodkuj obraz w formancie  
  
- Dostosuj rozmiar formantu do wyświetlanego obrazu  
  
- Rozciągnij dowolny obraz, który wyświetli, aby dopasować go do  
  
 Rozciąganie obrazu (zwłaszcza w formacie bitmapowym) może spowodować utratę jakości obrazu. Metafile, które są listami instrukcji graficznych do rysowania obrazów w czasie wykonywania, lepiej nadają się do rozciągania niż mapy bitowe.  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a>Aby ustawić właściwość SizeMode w czasie wykonywania  
  
1. Ustaw <xref:System.Windows.Forms.PictureBox.SizeMode%2A> <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> na (domyślnie), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>lub <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>. <xref:System.Windows.Forms.PictureBoxSizeMode.Normal>oznacza, że obraz jest umieszczony w lewym górnym rogu formantu; jeśli obraz jest większy niż formant, jego dolna i prawa krawędź są przycinane. <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>oznacza, że obraz jest wyśrodkowany w formancie; jeśli obraz jest większy niż formant, krawędzie zewnętrzne obrazu zostaną przycięte. <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>oznacza, że rozmiar formantu jest dostosowany do rozmiaru obrazu. <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>jest odwrotna i oznacza, że rozmiar obrazu jest dostosowany do rozmiaru formantu.  
  
     W poniższym przykładzie ścieżką ustawioną dla lokalizacji obrazu jest folder Moje dokumenty. Odbywa się to, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać ten katalog. Umożliwia to również użytkownikom z minimalnymi poziomami dostępu do systemu bezpieczne uruchamianie aplikacji. Poniższy przykład zakłada formularz <xref:System.Windows.Forms.PictureBox> z formantu już dodane.  
  
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

- <xref:System.Windows.Forms.PictureBox>
- [Instrukcje: dodawanie zdjęcia przy użyciu narzędzia Projektant](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [PictureBox — Informacje o formancie](picturebox-control-overview-windows-forms.md)
- [Instrukcje: ustawienie obrazów w czasie wykonywania](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox — Formant](picturebox-control-windows-forms.md)
