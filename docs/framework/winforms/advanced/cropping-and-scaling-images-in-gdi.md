---
title: Przycinanie i skalowanie obrazów w GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, scaling images
- GDI+, cropping images
- images [Windows Forms], cropping
- compressing data [Windows Forms], images
- images [Windows Forms], expansion
- images [Windows Forms], scaling
- rectangles [Windows Forms], source
- rectangles [Windows Forms], destination
- images [Windows Forms], compression
ms.assetid: ad5daf26-005f-45bc-a2af-e0e97777a21a
ms.openlocfilehash: c3cdb06e99770808461f9266fb5f07df9074149b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183732"
---
# <a name="cropping-and-scaling-images-in-gdi"></a>Przycinanie i skalowanie obrazów w GDI+
Możesz użyć <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> klasy do rysowania i umieść wektor obrazów i obrazów rastrowych. <xref:System.Drawing.Graphics.DrawImage%2A> jest przeciążona metoda, dzięki czemu może dostarczyć argumentów na kilka sposobów.  
  
## <a name="drawimage-variations"></a>DrawImage — zmiany  
 Zmiana jednego <xref:System.Drawing.Graphics.DrawImage%2A> metoda otrzymuje <xref:System.Drawing.Bitmap> i <xref:System.Drawing.Rectangle>. Prostokąt Określa lokalizację docelową dla operacji rysowania; oznacza to, że Określa ona prostokąta do rysowania obrazu. Jeśli rozmiar prostokąta docelowego jest inna niż rozmiar oryginalnego obrazu, obraz, który jest skalowany w celu dopasowania prostokąta docelowego. Poniższy przykład kodu pokazuje sposób rysowania trzy razy ten sam obraz: drugi raz z bez skalowania, drugi raz z rozszerzenia a drugi raz z kompresji:  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 Poniższa ilustracja przedstawia trzy obrazy.  
  
 ![Skalowanie](./media/aboutgdip03-art06.gif "AboutGdip03_Art06")  
  
 Kilka odmian <xref:System.Drawing.Graphics.DrawImage%2A> metoda ma parametr prostokąta źródłowego, a także parametr prostokąta docelowego. Parametr prostokąta źródłowego określa część oryginalnego obrazu, aby narysować. Prostokąta docelowego określa prostokąta do rysowania część obrazu. Jeśli rozmiar prostokąta docelowego jest inna niż rozmiar prostokąta źródłowego, obraz jest skalowane w celu dopasowania prostokąta docelowego.  
  
 Poniższy przykład kodu pokazuje sposób tworzenia <xref:System.Drawing.Bitmap> z pliku Runner.jpg. Całego obrazu narysowany bez skalowania w (0, 0). Następnie niewielką część obrazu jest rysowana dwa razy: rozszerzenie raz przy użyciu kompresji i drugi raz.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 Na poniższej ilustracji pokazuje nieskalowanego obrazu i fragmenty skompresowane i rozwiniętej obrazu.  
  
 ![Przycinanie i skalowanie](./media/aboutgdip03-art07.gif "AboutGdip03_Art07")  
  
## <a name="see-also"></a>Zobacz także

- [Obrazy, mapy bitowe i metapliki](images-bitmaps-and-metafiles.md)
- [Praca z obrazami, mapami bitowymi, ikonami i metaplikami](working-with-images-bitmaps-icons-and-metafiles.md)
