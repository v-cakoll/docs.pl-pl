---
title: 'Porady: dodawanie zdjęcia przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 12b90d561a18fcffaafb9c45b7fa6be6dd060215
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736324"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>Porady: dodawanie zdjęcia przy użyciu narzędzia Projektant (formularze systemu Windows)

Za pomocą kontrolki <xref:System.Windows.Forms.PictureBox> Windows Forms można załadować i wyświetlić obraz w formularzu w czasie projektowania, ustawiając właściwość <xref:System.Windows.Forms.PictureBox.Image%2A> na prawidłowy obraz. W poniższej tabeli przedstawiono akceptowalne typy plików.

|Typ|Rozszerzenie nazwy pliku|
|---|---|
|Mapy|.bmp|
|Ikona|.ico|
|GIF|.gif|
|Metafile|.wmf|
|JPEG|.jpg|

## <a name="to-display-a-picture-at-design-time"></a>Aby wyświetlić obraz w czasie projektowania

1. Narysuj kontrolkę <xref:System.Windows.Forms.PictureBox> w formularzu.

2. W oknie **Właściwości** wybierz właściwość <xref:System.Windows.Forms.PictureBox.Image%2A>, a następnie wybierz przycisk wielokropka, aby wyświetlić okno dialogowe **otwieranie** .

3. Jeśli szukasz określonego typu pliku (na przykład plików GIF), wybierz go w polu **Pliki typu** .

4. Wybierz plik, który chcesz wyświetlić.

## <a name="to-clear-the-picture-at-design-time"></a>Aby wyczyścić obraz w czasie projektowania

1. W oknie **Właściwości** wybierz właściwość <xref:System.Windows.Forms.PictureBox.Image%2A>. Kliknij prawym przyciskiem myszy mały obraz miniatury, który pojawia się po lewej stronie nazwy obiektu obrazu, a następnie wybierz polecenie **Zresetuj**.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.PictureBox>
- [PictureBox, kontrolka — omówienie](picturebox-control-overview-windows-forms.md)
- [Instrukcje: modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [Instrukcje: ustawienie obrazów w czasie wykonywania](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox, kontrolka](picturebox-control-windows-forms.md)
