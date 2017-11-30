---
title: "Rysowanie, pozycjonowanie i klonowanie obrazów w GDI+"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a3ba716a36280d2ac08dae907abbdbe05e563dfc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="drawing-positioning-and-cloning-images-in-gdi"></a>Rysowanie, pozycjonowanie i klonowanie obrazów w GDI+
Można użyć <xref:System.Drawing.Bitmap> można użyć klasy ładowanie i wyświetlanie obrazów rastrowych, a <xref:System.Drawing.Imaging.Metafile> klasy ładowanie i wyświetlanie obrazów wektora. <xref:System.Drawing.Bitmap> i <xref:System.Drawing.Imaging.Metafile> klasy dziedziczą <xref:System.Drawing.Image> klasy. Do wyświetlania obrazu wektora, potrzebujesz wystąpienia <xref:System.Drawing.Graphics> klasy i <xref:System.Drawing.Imaging.Metafile>. Aby wyświetlić obraz, należy wystąpienie <xref:System.Drawing.Graphics> klasy i <xref:System.Drawing.Bitmap>. Wystąpienie <xref:System.Drawing.Graphics> klasa udostępnia <xref:System.Drawing.Graphics.DrawImage%2A> metodę, która odbiera <xref:System.Drawing.Imaging.Metafile> lub <xref:System.Drawing.Bitmap> jako argument.  
  
## <a name="file-types-and-cloning"></a>Typy plików i klonowania  
 Poniższy przykładowy kod przedstawia sposób tworzenia <xref:System.Drawing.Bitmap> z pliku Climber.jpg i wyświetla mapy bitowej. Punkt docelowy dla lewego górnego rogu obrazu (10, 10), jest określona w parametrach drugiego i trzeciego.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#11)]  
  
 Na poniższej ilustracji przedstawiono obrazu.  
  
 ![Obraz przykładowej](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art04.gif "AboutGdip03_Art04")  
  
 Można utworzyć <xref:System.Drawing.Bitmap> obiektów z wielu grafiki formaty plików: BMP, GIF, JPEG, EXIF, PNG, TIFF i IKONA.  
  
 Poniższy przykładowy kod przedstawia sposób tworzenia <xref:System.Drawing.Bitmap> obiekty z różnych typów plików, a następnie wyświetla map bitowych.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#12)]  
  
 <xref:System.Drawing.Bitmap> Klasa udostępnia <xref:System.Drawing.Bitmap.Clone%2A> metodę, która umożliwia wykonanie kopii istniejącego <xref:System.Drawing.Bitmap>. <xref:System.Drawing.Bitmap.Clone%2A> Metoda ma parametr prostokąt źródłowego, który służy do określenia część oryginalnego mapy bitowej, który chcesz skopiować. W poniższym przykładzie przedstawiono sposób tworzenia <xref:System.Drawing.Bitmap> w klonowania w górnej połowie istniejące <xref:System.Drawing.Bitmap>. Następnie oba obrazy są rysowane.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#13)]  
  
 Na poniższej ilustracji przedstawiono dwa obrazy.  
  
 ![Przycinanie](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art05.gif "AboutGdip03_Art05")  
  
## <a name="see-also"></a>Zobacz też  
 [Obrazy, mapy bitowe i metapliki](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Porady: Tworzenie obiektów graficznych do rysowania](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Praca z obrazami, mapami bitowymi, ikony i metapliki](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
