---
title: 'Porady: dodawanie zdjęcia przy użyciu narzędzia Projektant'
description: Dowiedz się, jak za pomocą formantu PictureBox Windows Forms załadować i wyświetlić obraz w formularzu w czasie projektowania.
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: a05ffe19412fc7a4e3e02f01336d89cce39fac8a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325592"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>Porady: dodawanie zdjęcia przy użyciu narzędzia Projektant (formularze systemu Windows)

Za pomocą <xref:System.Windows.Forms.PictureBox> kontrolki Windows Forms można załadować i wyświetlić obraz w formularzu w czasie projektowania, ustawiając <xref:System.Windows.Forms.PictureBox.Image%2A> Właściwość na prawidłowy obraz. W poniższej tabeli przedstawiono akceptowalne typy plików.

|Typ|Rozszerzenie nazwy pliku|
|---|---|
|Mapy|bmp|
|Ikona|. ico|
|GIF|gif|
|Metafile|. wmf|
|JPEG|jpg|

## <a name="to-display-a-picture-at-design-time"></a>Aby wyświetlić obraz w czasie projektowania

1. Narysuj <xref:System.Windows.Forms.PictureBox> kontrolkę w formularzu.

2. W oknie **Właściwości** wybierz <xref:System.Windows.Forms.PictureBox.Image%2A> Właściwość, a następnie wybierz przycisk wielokropka, aby wyświetlić okno dialogowe **Otwórz** .

3. Jeśli szukasz określonego typu pliku (na przykład plików GIF), wybierz go w polu **Pliki typu** .

4. Wybierz plik, który chcesz wyświetlić.

## <a name="to-clear-the-picture-at-design-time"></a>Aby wyczyścić obraz w czasie projektowania

1. W oknie **Właściwości** wybierz <xref:System.Windows.Forms.PictureBox.Image%2A> Właściwość. Kliknij prawym przyciskiem myszy mały obraz miniatury, który pojawia się po lewej stronie nazwy obiektu obrazu, a następnie wybierz polecenie **Zresetuj**.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.PictureBox>
- [PictureBox — Informacje o formancie](picturebox-control-overview-windows-forms.md)
- [Instrukcje: modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [Instrukcje: ustawienie obrazów w czasie wykonywania](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox — Formant](picturebox-control-windows-forms.md)
