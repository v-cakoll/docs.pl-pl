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
ms.openlocfilehash: 6c17e0b2d023ccf80b0d32301b7ee6765edcae9f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424819"
---
# <a name="how-to-load-and-display-metafiles"></a>Porady: ładowanie i wyświetlanie metaplików
Klasa <xref:System.Drawing.Imaging.Metafile>, która dziedziczy z klasy <xref:System.Drawing.Image>, zapewnia metody rejestrowania, wyświetlania i badania obrazów wektorowych.  
  
## <a name="example"></a>Przykład  
 Aby wyświetlić obraz wektora (metaplik) na ekranie, potrzebny jest obiekt <xref:System.Drawing.Imaging.Metafile> i <xref:System.Drawing.Graphics> obiektu. Przekaż nazwę pliku (lub strumienia) do konstruktora <xref:System.Drawing.Imaging.Metafile>. Po utworzeniu obiektu <xref:System.Drawing.Imaging.Metafile>, Przekaż ten obiekt <xref:System.Drawing.Imaging.Metafile> do metody <xref:System.Drawing.Graphics.DrawImage%2A> obiektu <xref:System.Drawing.Graphics>.  
  
 Przykład tworzy obiekt <xref:System.Drawing.Imaging.Metafile> z pliku EMF (Enhanced Metafile), a następnie rysuje obraz w lewym górnym rogu w lokalizacji (60, 10).  
  
 Na poniższej ilustracji przedstawiono metaplik rysowany w określonej lokalizacji.  
  
 ![Zrzut ekranu przedstawiający położenie obrazu.](./media/how-to-load-and-display-metafiles/metafile-drawn-specified-location.png "imageposition2")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z Windows Forms i wymaga `e`<xref:System.Windows.Forms.PaintEventArgs>, który jest parametrem programu obsługi zdarzeń <xref:System.Windows.Forms.Control.Paint>.  
  
## <a name="see-also"></a>Zobacz także

- [Praca z obrazami, mapami bitowymi, ikonami i metaplikami](working-with-images-bitmaps-icons-and-metafiles.md)
