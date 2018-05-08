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
ms.openlocfilehash: 258ef9cd5eb8d569b2982614e3087df730a18c57
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-rotate-colors"></a>Porady: obracanie kolorów
Obrót w miejscu color czterowymiarowego jest trudne do wizualizacji. Firma Microsoft może ułatwić do wizualizacji obrotu zgadzając się do jednego ze składników kolor stałej zachowania. Załóżmy, że firma Microsoft Zgadzam się składnika alfa ustalona na 1 (całkowicie nieprzezroczyste). Firma Microsoft następnie wizualizacji przestrzeni trójwymiarowej koloru z czerwonym, zielonemu i niebieskiemu osi, jak pokazano na poniższej ilustracji.  
  
 ![Ponowne kolorowanie](../../../../docs/framework/winforms/advanced/media/recoloring03.gif "recoloring03")  
  
 Kolor można traktować jako punktu 3-miejsca. Na przykład punkt (1, 0, 0), w miejsce reprezentuje kolor czerwony, a punkt (0, 1, 0), w miejsce reprezentuje kolor zielony.  
  
 Na poniższej ilustracji przedstawiono co obracanie kolorów (1, 0, 0) oznacza się pod kątem 60 stopni na płaszczyźnie czerwony zielony. Obracanie równolegle płaszczyzny płaszczyzny czerwony zielony można traktować jako obrót wokół osi niebieski.  
  
 ![Ponowne kolorowanie](../../../../docs/framework/winforms/advanced/media/recoloring04.gif "recoloring04")  
  
 Na poniższej ilustracji przedstawiono sposób inicjowania macierzy kolorów do wykonania obrotów o poszczególnych trzy osie współrzędnych (czerwony, zielony, niebieski).  
  
 ![Ponowne kolorowanie](../../../../docs/framework/winforms/advanced/media/recoloring05.gif "recoloring05")  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przyjmuje obrazu, który jest jeden kolor (1, 0, 0,6) i stosuje 60 stopni niebieski osi. Kąt obrotu przechwytywana wychodzących na płaszczyźnie jest zbliżony do płaszczyzny czerwony zielony.  
  
 Na poniższej ilustracji przedstawiono oryginalnego obrazu po lewej i obracać kolor obraz po prawej stronie.  
  
 ![Obracanie kolorów](../../../../docs/framework/winforms/advanced/media/colortrans5.png "colortrans5")  
  
 Na poniższej ilustracji przedstawiono wizualizację obracanie kolorów wykonywane w poniższym kodzie.  
  
 ![Ponowne kolorowanie](../../../../docs/framework/winforms/advanced/media/recoloring06.gif "recoloring06")  
  
 [!code-csharp[System.Drawing.RotateColors#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń. Zastąp `RotationInput.bmp` z nazwą pliku obrazu i ścieżki jest prawidłowy w tym systemie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [Grafika i rysowanie w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Ponowne kolorowanie obrazów](../../../../docs/framework/winforms/advanced/recoloring-images.md)
