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
ms.openlocfilehash: 99bde4fac7b3057358c7e6a8550efdb4cc351eb0
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037881"
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a>Instrukcje: Ustawianie obrazu wyświetlanego przez kontrolkę Windows Forms

Kilka kontrolek Windows Forms może wyświetlać obrazy. Te obrazy mogą być ikonami, które wyjaśniają przeznaczenie kontrolki, na przykład ikona dyskietki na przycisku oznaczającego polecenie **Zapisz** . Alternatywnie, ikony mogą być obrazami tła, aby nadać formantowi wygląd i zachowanie.

## <a name="to-set-the-image-displayed-by-a-control"></a>Aby ustawić obraz wyświetlany przez kontrolkę

1. Ustaw kontrolkę `Image` lub `BackgroundImage` właściwość na obiekt typu <xref:System.Drawing.Image>. Ogólnie rzecz biorąc, zostanie załadowany obraz z pliku za pomocą <xref:System.Drawing.Image.FromFile%2A> metody.

     W poniższym przykładzie kodu ścieżka ustawiona dla lokalizacji obrazu jest folderem **Moje obrazy** . Większość komputerów z systemem operacyjnym Windows będzie zawierać ten katalog. Dzięki temu użytkownicy mający minimalne poziomy dostępu do systemu mogą bezpiecznie uruchamiać aplikację. Poniższy przykład kodu wymaga, aby formularz z <xref:System.Windows.Forms.PictureBox> dodaną kontrolką został już dodany.

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
