---
title: 'Instrukcje: Ładowanie obrazu przy użyciu narzędzia Projektant (Windows Forms)'
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 818bc63b5b3bea6c73804f716a72ba3cd1a62b4c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039679"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>Instrukcje: Ładowanie obrazu przy użyciu narzędzia Projektant (Windows Forms)

Za pomocą kontrolki Windows Forms <xref:System.Windows.Forms.PictureBox> można załadować i wyświetlić obraz w formularzu w czasie projektowania, <xref:System.Windows.Forms.PictureBox.Image%2A> ustawiając właściwość na prawidłowy obraz. W poniższej tabeli przedstawiono akceptowalne typy plików.

|Typ|Rozszerzenie nazwy pliku|
|---|---|
|Mapy|.bmp|
|Ikona|.ico|
|GIF|.gif|
|Metafile|.wmf|
|JPEG|.jpg|

## <a name="to-display-a-picture-at-design-time"></a>Aby wyświetlić obraz w czasie projektowania

1. Narysuj <xref:System.Windows.Forms.PictureBox> kontrolkę w formularzu.

2. W oknie **Właściwości** wybierz <xref:System.Windows.Forms.PictureBox.Image%2A> właściwość, a następnie wybierz przycisk wielokropka, aby wyświetlić okno dialogowe **Otwórz** .

3. Jeśli szukasz określonego typu pliku (na przykład plików GIF), wybierz go w polu **Pliki typu** .

4. Wybierz plik, który chcesz wyświetlić.

## <a name="to-clear-the-picture-at-design-time"></a>Aby wyczyścić obraz w czasie projektowania

1. W oknie **Właściwości** wybierz <xref:System.Windows.Forms.PictureBox.Image%2A> właściwość. Kliknij prawym przyciskiem myszy mały obraz miniatury, który pojawia się po lewej stronie nazwy obiektu obrazu, a następnie wybierz polecenie **Zresetuj**.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.PictureBox>
- [PictureBox, kontrolka — omówienie](picturebox-control-overview-windows-forms.md)
- [Instrukcje: Modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [Instrukcje: Ustawianie obrazów w czasie wykonywania](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox, kontrolka](picturebox-control-windows-forms.md)
