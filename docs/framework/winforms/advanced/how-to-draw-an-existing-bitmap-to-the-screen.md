---
title: 'Instrukcje: Rysowanie istniejącej mapy bitowej na ekranie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], displaying in Windows Forms
- bitmaps [Windows Forms], loading in Windows Forms applications
- images [Windows Forms], displaying on Windows Forms
ms.assetid: 5bc558d7-b326-4050-a834-b8600da0de95
ms.openlocfilehash: d8c118d9561c0fe993228cb6bd8cebcd156d411d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586725"
---
# <a name="how-to-draw-an-existing-bitmap-to-the-screen"></a>Instrukcje: Rysowanie istniejącej mapy bitowej na ekranie
Istniejący obraz można łatwo rysować na ekranie. Najpierw należy utworzyć <xref:System.Drawing.Bitmap> obiektu za pomocą konstruktora mapy bitowej, który przyjmuje nazwę pliku <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>. Ten konstruktor akceptuje obrazów z kilku różnych formatach plików, w tym BMP, GIF, JPEG, PNG i TIFF. Po utworzeniu <xref:System.Drawing.Bitmap> obiektów, przekaż go <xref:System.Drawing.Bitmap> obiekt <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> obiektu.  
  
## <a name="example"></a>Przykład  
 Ten przykład tworzy <xref:System.Drawing.Bitmap> obiekt z pliku JPEG i następnie rysuje mapę bitową z jego lewego górnego rogu w (60, 10).  
  
 Poniższa ilustracja przedstawia mapy bitowej rysowane w określonej lokalizacji.  
  
 ![Pozycja obrazu](../../../../docs/framework/winforms/advanced/media/csimageposition1.png "csimageposition1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.WorkingWithImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także
- [Grafika i rysowanie w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [Praca z obrazami, mapami bitowymi, ikonami i metaplikami](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
