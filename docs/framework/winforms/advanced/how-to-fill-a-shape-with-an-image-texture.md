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
ms.openlocfilehash: 42c456137f84c6fa657ba5a09727eae052a45376
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911687"
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a>Instrukcje: Wypełnianie kształtów teksturą obrazu
Można wypełnić zamknięty kształt teksturą, używając <xref:System.Drawing.Image> klasy <xref:System.Drawing.TextureBrush> i klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wypełnia wielokropek obrazem. Kod konstruuje <xref:System.Drawing.Image> obiekt, a następnie przekazuje adres tego <xref:System.Drawing.Image> obiektu <xref:System.Drawing.TextureBrush.%23ctor%2A> jako argument do konstruktora. Trzecia instrukcja skaluje obraz, a czwarta instrukcja wypełnia elipsę powtarzanymi kopiami obrazu skalowanego.  
  
 W poniższym kodzie <xref:System.Drawing.TextureBrush.Transform%2A> Właściwość zawiera transformację, która została zastosowana do obrazu przed jego narysowaniem. Załóżmy, że oryginalny obraz ma szerokość 640 pikseli i wysokość 480 pikseli. Transformacja zmniejsza obraz do 75 × 75, ustawiając wartości skalowania w poziomie i w pionie.  
  
> [!NOTE]
> W poniższym przykładzie rozmiar obrazu wynosi 75 × 75, a rozmiar elipsy wynosi 150 × 250. Ponieważ obraz jest mniejszy niż Elipsa, która jest wypełniana, wielokropek jest rozmieszczany z obrazem. Dzielenie oznacza, że obraz jest powtarzany w poziomie i w pionie do momentu osiągnięcia granicy kształtu. Aby uzyskać więcej informacji na temat dzielenia [, zobacz How to: Tworzenie kafelka kształtu przy użyciu](how-to-tile-a-shape-with-an-image.md)obrazu.  
  
 [!code-csharp[System.Drawing.UsingABrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użycia z Windows Forms i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który <xref:System.Windows.Forms.Control.Paint> jest parametrem programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także

- [Używanie pędzla do wypełniania kształtów](using-a-brush-to-fill-shapes.md)
