---
title: 'Instrukcje: Ładowanie i wyświetlanie metaplików'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], metafiles
- metafiles [Windows Forms], displaying
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
ms.openlocfilehash: 121f285a95d0169db79bdc302d80dba03b3b40c2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720046"
---
# <a name="how-to-load-and-display-metafiles"></a>Instrukcje: Ładowanie i wyświetlanie metaplików
<xref:System.Drawing.Imaging.Metafile> Klasy, która dziedziczy po elemencie <xref:System.Drawing.Image> klasy, zawiera metody służące do rejestrowania, wyświetlanie i badanie obrazy wektorowe.  
  
## <a name="example"></a>Przykład  
 Aby wyświetlić obraz wektora (metaplik) na ekranie, należy <xref:System.Drawing.Imaging.Metafile> obiektu i <xref:System.Drawing.Graphics> obiektu. Przekazać nazwę pliku (lub strumienia) do <xref:System.Drawing.Imaging.Metafile> konstruktora. Po utworzeniu <xref:System.Drawing.Imaging.Metafile> obiektów, przekaż go <xref:System.Drawing.Imaging.Metafile> obiekt <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> obiektu.  
  
 W przykładzie jest tworzony <xref:System.Drawing.Imaging.Metafile> obiektu z pliku EMF (rozszerzony metaplik) i następnie Rysuje obraz z jego lewego górnego rogu w (60, 10).  
  
 Poniższa ilustracja przedstawia metaplik rysowane w określonej lokalizacji.  
  
 ![Pozycja obrazu](./media/imageposition2.png "imageposition2")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także
- [Praca z obrazami, mapami bitowymi, ikonami i metaplikami](working-with-images-bitmaps-icons-and-metafiles.md)
