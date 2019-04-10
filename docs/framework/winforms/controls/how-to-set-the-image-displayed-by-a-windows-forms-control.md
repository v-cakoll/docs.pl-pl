---
title: 'Instrukcje: ustawianie obrazu wyświetlanego przez kontrolkę formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
ms.openlocfilehash: 1de835bda5ac906837ac3fbd97b87f68f14d1953
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59333928"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a>Instrukcje: ustawianie obrazu wyświetlanego przez kontrolkę formularzy systemu Windows
Kilka kontrolek Windows Forms można wyświetlać obrazy. Obrazy te można ikony, które wyjaśnienie przeznaczenia kontrolki, takie jak ikonę dyskietki na przycisku określające elementy **Zapisz** polecenia. Alternatywnie ikony może być obrazów tła do zapewnienia kontroli, wygląd i zachowanie, które chcesz.  
  
### <a name="to-set-the-image-displayed-by-a-control"></a>Aby ustawić obrazu wyświetlanego przez kontrolkę  
  
1. Ustaw dla formantu `Image` lub `BackgroundImage` właściwość do obiektu typu <xref:System.Drawing.Image>. Ogólnie rzecz biorąc, można będzie się ładuje obraz z pliku przy użyciu <xref:System.Drawing.Image.FromFile%2A> metody.  
  
     W poniższym przykładzie kodu ścieżkę zestawu dla lokalizacji obrazu jest **Moje obrazy** folderu. Większość komputerów z systemem operacyjnym Windows będzie zawierać tego katalogu. Umożliwia także użytkownikom minimalny system poziomy dostępu do bezpiecznego uruchamiania aplikacji. Poniższy przykład kodu wymaga jeszcze formularza z <xref:System.Windows.Forms.PictureBox> dodane kontrolki.  
  
    ```vb  
    ' Replace the image named below  
    ' with an icon of your own choosing.  
    PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.MyPictures) _  
       & "\Image.gif")  
    ```  
  
    ```csharp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.MyPictures)  
       + @"\Image.gif");  
    ```  
  
    ```cpp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    pictureBox1->Image = Image::FromFile(String::Concat  
       (System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::MyPictures),  
       "\\Image.gif"));  
    ```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Image.FromFile%2A>
- <xref:System.Drawing.Image>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
