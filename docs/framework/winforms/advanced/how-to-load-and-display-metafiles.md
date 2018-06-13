---
title: 'Porady: ładowanie i wyświetlanie metaplików'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], metafiles
- metafiles [Windows Forms], displaying
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
ms.openlocfilehash: c2b0a89966100077d5a72edc11822c356d2de1b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522773"
---
# <a name="how-to-load-and-display-metafiles"></a>Porady: ładowanie i wyświetlanie metaplików
<xref:System.Drawing.Imaging.Metafile> Klasy, która dziedziczy <xref:System.Drawing.Image> klasy, metody do rejestrowania, wyświetlanie i badanie wektor obrazów.  
  
## <a name="example"></a>Przykład  
 Aby wyświetlić obraz wektora (metaplik) na ekranie, należy <xref:System.Drawing.Imaging.Metafile> obiektu i <xref:System.Drawing.Graphics> obiektu. Przekaż nazwę pliku (lub strumień) do <xref:System.Drawing.Imaging.Metafile> konstruktora. Po utworzeniu <xref:System.Drawing.Imaging.Metafile> obiektu, który przekazać <xref:System.Drawing.Imaging.Metafile> do obiektu <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> obiektu.  
  
 W przykładzie jest tworzony <xref:System.Drawing.Imaging.Metafile> obiektów z pliku EMF (rozszerzony metaplik), a następnie Rysuje obraz z jego lewego górnego rogu na (60, 10).  
  
 Na poniższej ilustracji przedstawiono metaplik rysowana w określonej lokalizacji.  
  
 ![Pozycja obrazu](../../../../docs/framework/winforms/advanced/media/imageposition2.png "imageposition2")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z obrazami, mapami bitowymi, ikonami i metaplikami](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
