---
title: 'Instrukcje: Wypełnianie kształtów teksturą obrazu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using with brushes
- bitmaps [Windows Forms], using texture
- shapes [Windows Forms], filling with images
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
ms.openlocfilehash: 89ebad6773b076514f5a745db653e0e0a18d4b48
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708447"
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a>Instrukcje: Wypełnianie kształtów teksturą obrazu
Możesz wypełnić kształt zamknięty tekstury za pomocą <xref:System.Drawing.Image> klasy i <xref:System.Drawing.TextureBrush> klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wypełnia elipsę z obrazem. Ten kod tworzy <xref:System.Drawing.Image> obiektu, a następnie przekazuje adres, który <xref:System.Drawing.Image> obiekt jako argumentu do <xref:System.Drawing.TextureBrush.%23ctor%2A> konstruktora. Trzecią instrukcję, skaluje obraz, a czwarty instrukcji wypełnia elipsę z powtarzających się kopii skalowanych obrazu.  
  
 W poniższym kodzie <xref:System.Drawing.TextureBrush.Transform%2A> właściwość zawiera przekształcenie, które jest zastosowany do obrazu przed jej rysowania. Załóżmy, że oryginalny obraz ma 640 pikseli szerokości i wysokości 480 pikseli. Transformacja zmniejsza obraz do 75 x 75 przez ustawienie poziomie i pionie wartości skalowania.  
  
> [!NOTE]
>  W poniższym przykładzie rozmiar obrazu jest 75 x 75%, i rozmiaru elipsy wynosi 150 x 250. Ponieważ obraz, który jest mniejszy niż elipsy, który wypełnia ją, wielokropka jest rozmieszczany przy użyciu obrazu. Fragmentacji oznacza, że obraz jest powtarzany w poziomie i w pionie do granicy kształt zostanie osiągnięty. Aby uzyskać więcej informacji na temat fragmentacji, zobacz [jak: Kafelek kształtu obrazem](how-to-tile-a-shape-with-an-image.md).  
  
 [!code-csharp[System.Drawing.UsingABrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także
- [Używanie pędzla do wypełniania kształtów](using-a-brush-to-fill-shapes.md)
