---
title: Rysowanie, pozycjonowanie i klonowanie obrazów w GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- raster images [Windows Forms]
- images [Windows Forms], positioning
- drawing [Windows Forms], images
- drawing [Windows Forms], raster images
- images [Windows Forms], cloning
- images [Windows Forms], drawing
- GDI+, drawing images
- GDI+, cloning images
- GDI+, positioning images
ms.assetid: 09f0c07a-19c0-43b4-90a2-862a10545ce8
ms.openlocfilehash: b5f98e7bdef9ff8ed0a4cd0e040cb92a31f30503
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59188451"
---
# <a name="drawing-positioning-and-cloning-images-in-gdi"></a>Rysowanie, pozycjonowanie i klonowanie obrazów w GDI+
Możesz użyć <xref:System.Drawing.Bitmap> klasy, ładowania oraz wyświetlania obrazów rastrowych, na które mogą używać <xref:System.Drawing.Imaging.Metafile> klasy, ładowania oraz wyświetlania obrazów wektora. <xref:System.Drawing.Bitmap> i <xref:System.Drawing.Imaging.Metafile> klasy dziedziczą <xref:System.Drawing.Image> klasy. Aby wyświetlić obraz wektora, potrzebujesz wystąpienie <xref:System.Drawing.Graphics> klasy i <xref:System.Drawing.Imaging.Metafile>. Aby wyświetlić obraz, potrzebujesz wystąpienie <xref:System.Drawing.Graphics> klasy i <xref:System.Drawing.Bitmap>. Wystąpienie <xref:System.Drawing.Graphics> klasa udostępnia <xref:System.Drawing.Graphics.DrawImage%2A> metody, która odbiera <xref:System.Drawing.Imaging.Metafile> lub <xref:System.Drawing.Bitmap> jako argument.  
  
## <a name="file-types-and-cloning"></a>Typy plików i klonowanie  
 Poniższy przykład kodu pokazuje sposób tworzenia <xref:System.Drawing.Bitmap> z pliku Climber.jpg i wyświetla mapę bitową. Punkt docelowy dla lewego górnego rogu obrazu (10, 10), jest określony w parametrach drugiego i trzeciego.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#11)]  
  
 Poniższa ilustracja przedstawia obrazu.  
  
 ![Obraz przykładowej](./media/aboutgdip03-art04.gif "AboutGdip03_Art04")  
  
 Można skonstruować <xref:System.Drawing.Bitmap> obiektów z wielu grafiki formaty plików: BMP, GIF, JPEG, EXIF, PNG, TIFF i IKONA.  
  
 Poniższy przykład kodu pokazuje sposób tworzenia <xref:System.Drawing.Bitmap> obiekty z różnych typów plików, a następnie wyświetla map bitowych.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#12)]  
  
 <xref:System.Drawing.Bitmap> Klasa udostępnia <xref:System.Drawing.Bitmap.Clone%2A> metody użytej do utworzenia kopii istniejącego <xref:System.Drawing.Bitmap>. <xref:System.Drawing.Bitmap.Clone%2A> Metoda ma parametr prostokąta źródłowego używanego do określania część oryginalnego mapy bitowej, który chcesz skopiować. Poniższy przykład kodu pokazuje sposób tworzenia <xref:System.Drawing.Bitmap> przez Sklonowanie istniejącego w górnej połowie <xref:System.Drawing.Bitmap>. Następnie są rysowane oba obrazy.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#13)]  
  
 Poniższa ilustracja przedstawia dwa obrazy.  
  
 ![Przycinanie](./media/aboutgdip03-art05.gif "AboutGdip03_Art05")  
  
## <a name="see-also"></a>Zobacz także

- [Obrazy, mapy bitowe i metapliki](images-bitmaps-and-metafiles.md)
- [Instrukcje: Tworzenie obiektów graficznych do rysowania](how-to-create-graphics-objects-for-drawing.md)
- [Praca z obrazami, mapami bitowymi, ikonami i metaplikami](working-with-images-bitmaps-icons-and-metafiles.md)
