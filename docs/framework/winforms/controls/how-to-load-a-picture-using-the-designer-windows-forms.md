---
title: "Porady: dodawanie zdjęcia przy użyciu narzędzia Projektant (formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9049bf5f9467401bff098459b8f5ed55c1ee1975
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a>Porady: dodawanie zdjęcia przy użyciu narzędzia Projektant (formularze systemu Windows)
Windows Forms <xref:System.Windows.Forms.PictureBox> sterowania, można załadować i wyświetlić obraz w formularzu w czasie projektowania, ustawiając <xref:System.Windows.Forms.PictureBox.Image%2A> właściwości nieprawidłowy obraz. W poniższej tabeli przedstawiono typy plików akceptowane.  
  
|Typ|Rozszerzenie nazwy pliku|  
|----------|-------------------------|  
|Mapy bitowej|BMP|  
|Ikona|ICO|  
|GIF|GIF|  
|Metaplik|.wmf|  
|JPEG|jpg|  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-a-picture-at-design-time"></a>Aby wyświetlić obraz w czasie projektowania  
  
1.  Rysuj <xref:System.Windows.Forms.PictureBox> kontrolkę w formularzu.  
  
2.  W oknie właściwości, wybierz <xref:System.Windows.Forms.PictureBox.Image%2A> właściwości, a następnie kliknij przycisk wielokropka, aby wyświetlić **Otwórz** okno dialogowe.  
  
3.  Jeśli szukasz dla określonego typu pliku (na przykład GIF), wybierz go w **pliki typu** pole.  
  
4.  Wybierz plik, który chcesz wyświetlić.  
  
### <a name="to-clear-the-picture-at-design-time"></a>Aby wyczyścić obrazu w czasie projektowania  
  
1.  Na **właściwości** wybierz <xref:System.Windows.Forms.PictureBox.Image%2A> właściwości i kliknij prawym przyciskiem myszy mały obraz miniatury, który wydaje się po lewej stronie nazwy obiektu obrazu. Wybierz **zresetować**.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.PictureBox>  
 [Informacje o formancie PictureBox](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [Porady: modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)  
 [Porady: ustawienie obrazów w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)  
 [PictureBox — formant](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
