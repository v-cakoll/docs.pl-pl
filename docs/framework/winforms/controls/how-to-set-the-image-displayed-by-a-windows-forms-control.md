---
title: "Porady: ustawianie obrazu wyświetlanego przez formant formularzy systemu Windows"
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
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4bf42fc90e19cbac0f165b59c0c6d3dfb7456b5a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a>Porady: ustawianie obrazu wyświetlanego przez formant formularzy systemu Windows
Kilka formantów formularzy systemu Windows można wyświetlić obrazy. Obrazy te można ikony, które Objaśnienie przeznaczenia formantu, takie jak ikoną dyskietki na przycisku określające **zapisać** polecenia. Alternatywnie ikony może być obrazy tła, aby mieć kontrolę wygląd i zachowanie, które mają.  
  
### <a name="to-set-the-image-displayed-by-a-control"></a>Aby ustawić obrazu wyświetlanego przez formant  
  
1.  Ustawianie formantu `Image` lub `BackgroundImage` dla właściwości typu obiektu <xref:System.Drawing.Image>. Ogólnie rzecz biorąc, użytkownik będzie można ładowanie obrazu z pliku za pomocą <xref:System.Drawing.Image.FromFile%2A> metody.  
  
     W poniższym przykładzie kodu, ścieżka ustawiona dla lokalizacji obrazu jest **Moje obrazy** folderu. Ten katalog zawiera większość komputerów z systemem operacyjnym Windows. Dzięki temu użytkownicy z poziomami dostępu minimalny system można bezpiecznie uruchomić aplikację. Poniższy przykład kodu wymaga już formularza z <xref:System.Windows.Forms.PictureBox> dodano formant.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Image.FromFile%2A>  
 <xref:System.Drawing.Image>  
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>
