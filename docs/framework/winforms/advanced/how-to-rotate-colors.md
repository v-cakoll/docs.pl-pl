---
title: 'Porady: obracanie kolorów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], rotating
- examples [Windows Forms], rotating colors
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
ms.openlocfilehash: 8d2717dd7b819e963126072279b361fda02188bc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111338"
---
# <a name="how-to-rotate-colors"></a>Porady: obracanie kolorów
Obrót w czterowymiarowej przestrzeni kolorów jest trudny do wizualizacji. Możemy ułatwić wizualizację obrotu, zgadzając się na utrzymanie jednego ze składników koloru na stałym miejscu. Załóżmy, że zgadzamy się, aby utrzymać składnik alfa stały na 1 (całkowicie nieprzezroczyste). Następnie możemy wizualizować trójwymiarową przestrzeń kolorów z czerwonymi, zielonymi i niebieskimi osiami, jak pokazano na poniższej ilustracji.  
  
 ![Ilustracja przedstawiająca obrót z osiami czerwonymi, zielonymi i niebieskimi.](./media/how-to-rotate-colors/rotation-red-green-blue-axes.gif)  
  
 Kolor można traktować jako punkt w przestrzeni 3D. Na przykład punkt (1, 0, 0) w przestrzeni reprezentuje kolor czerwony, a punkt (0, 1, 0) w przestrzeni reprezentuje kolor zielony.  
  
 Na poniższej ilustracji pokazano, co to znaczy obrócić kolor (1, 0, 0) pod kątem 60 stopni w płaszczyźnie czerwono-zielonej. Obrót w płaszczyźnie równoległej do płaszczyzny czerwono-zielonej można traktować jako obrót wokół niebieskiej osi.  
  
 ![Ilustracja przedstawiająca obrót wokół niebieskiej osi.](./media/how-to-rotate-colors/rotation-about-blue-axis.gif)  
  
 Na poniższej ilustracji pokazano, jak zainicjować macierz kolorów w celu wykonywania obrotów dotyczących każdej z trzech osi współrzędnych (czerwonej, zielonej, niebieskiej):  
  
 ![Zainicjować macierz kolorów, aby wykonać obroty około trzech osi.](./media/how-to-rotate-colors/rotation-about-three-axes.gif)  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie obraz, który jest cały jeden kolor (1, 0, 0,6) i stosuje obrót 60 stopni wokół niebieskiej osi. Kąt obrotu jest zmieciony w płaszczyźnie równoległej do płaszczyzny czerwono-zielonej.  
  
 Na poniższej ilustracji przedstawiono oryginalny obraz po lewej stronie i obrócony kolor obrazu po prawej stronie:  
  
 ![Ilustracja przedstawiająca oryginalny obraz i obraz obrócony kolorem.](./media/how-to-rotate-colors/original-color-rotated-images.png)  
  
 Na poniższej ilustracji przedstawiono wizualizację obrotu kolorów wykonaną w następującym kodzie:
  
 ![Ilustracja przedstawiająca wizualizację obrotu kolorów.](./media/how-to-rotate-colors/visualization-color-rotation.gif)  
  
 [!code-csharp[System.Drawing.RotateColors#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Powyższy przykład jest przeznaczony do użytku z <xref:System.Windows.Forms.PaintEventArgs> `e`formularzami systemu Windows <xref:System.Windows.Forms.Control.Paint> i wymaga , który jest parametrem obsługi zdarzeń. Zastąp `RotationInput.bmp` nazwą pliku obrazu i ścieżką prawidłową w systemie.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Ponowne kolorowanie obrazów](recoloring-images.md)
