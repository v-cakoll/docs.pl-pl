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
ms.openlocfilehash: bf1e09548ff9bc4eb650048eb21a9c300f3f6405
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601782"
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a>Instrukcje: Wypełnianie kształtów teksturą obrazu
Możesz wypełnić kształt zamknięty tekstury za pomocą <xref:System.Drawing.Image> klasy i <xref:System.Drawing.TextureBrush> klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wypełnia elipsę z obrazem. Ten kod tworzy <xref:System.Drawing.Image> obiektu, a następnie przekazuje adres, który <xref:System.Drawing.Image> obiekt jako argumentu do <xref:System.Drawing.TextureBrush.%23ctor%2A> konstruktora. Trzecią instrukcję, skaluje obraz, a czwarty instrukcji wypełnia elipsę z powtarzających się kopii skalowanych obrazu.  
  
 W poniższym kodzie <xref:System.Drawing.TextureBrush.Transform%2A> właściwość zawiera przekształcenie, które jest zastosowany do obrazu przed jej rysowania. Załóżmy, że oryginalny obraz ma 640 pikseli szerokości i wysokości 480 pikseli. Transformacja zmniejsza obraz do 75 x 75 przez ustawienie poziomie i pionie wartości skalowania.  
  
> [!NOTE]
>  W poniższym przykładzie rozmiar obrazu jest 75 x 75%, i rozmiaru elipsy wynosi 150 x 250. Ponieważ obraz, który jest mniejszy niż elipsy, który wypełnia ją, wielokropka jest rozmieszczany przy użyciu obrazu. Fragmentacji oznacza, że obraz jest powtarzany w poziomie i w pionie do granicy kształt zostanie osiągnięty. Aby uzyskać więcej informacji na temat fragmentacji, zobacz [jak: Kafelek kształtu obrazem](../../../../docs/framework/winforms/advanced/how-to-tile-a-shape-with-an-image.md).  
  
 [!code-csharp[System.Drawing.UsingABrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także
- [Używanie pędzla do wypełniania kształtów](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
