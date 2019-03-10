---
title: 'Instrukcje: Obracanie kolorów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], rotating
- examples [Windows Forms], rotating colors
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
ms.openlocfilehash: cb3824d8a5a5674b83124301dbfbd5a3ba60effa
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720621"
---
# <a name="how-to-rotate-colors"></a>Instrukcje: Obracanie kolorów
Obrót przestrzeni kolorów czterowymiarowego jest trudny do wizualizacji. Firma Microsoft może ułatwić wizualizacji obrotu zgadzając się zachować jeden ze składników koloru, stałej. Załóżmy, że firma Microsoft zobowiązuje się do zachowania ustalony na 1 składnik alfa (całkowicie nieprzezroczyste). Firma Microsoft następnie wizualizować przestrzeń kolorów trójwymiarowej za pomocą czerwonego, zielonego i niebieskiego osi, jak pokazano na poniższej ilustracji.  
  
 ![Ponowne kolorowanie](./media/recoloring03.gif "recoloring03")  
  
 Kolor, który można traktować jako punktów w przestrzeni 3D. Na przykład punkt (1, 0, 0), w obszarze reprezentuje kolor czerwony, a punkt (0, 1, 0), w obszarze reprezentuje kolor zielony.  
  
 Poniższa ilustracja przedstawia się pod kątem 60 stopni na płaszczyźnie czerwony zielony oznacza obracanie kolorów (1, 0, 0). Obrót równolegle płaszczyzny do płaszczyzny czerwonego mogą być uważane za obrót wokół osi niebieski.  
  
 ![Ponowne kolorowanie](./media/recoloring04.gif "recoloring04")  
  
 Na poniższej ilustracji pokazano, jak zainicjować macierzy kolorów do wykonania wymiany o każdej z trzech osi współrzędnych (czerwony, zielony, niebieski).  
  
 ![Ponowne kolorowanie](./media/recoloring05.gif "recoloring05")  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera obraz, który jednego koloru (1, 0, 0.6) oraz będzie miało zastosowanie 60 stopni niebieski osi. Kąt obrotu przechwytywana się na płaszczyźnie, który jest zbliżony do płaszczyzny czerwony zielony.  
  
 Poniższa ilustracja przedstawia oryginalny obraz po lewej i obracać kolor obraz po prawej stronie.  
  
 ![Obracanie kolorów](./media/colortrans5.png "colortrans5")  
  
 Na poniższej ilustracji przedstawiono wizualizację obracanie kolorów wykonywane w poniższym kodzie.  
  
 ![Ponowne kolorowanie](./media/recoloring06.gif "recoloring06")  
  
 [!code-csharp[System.Drawing.RotateColors#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń. Zastąp `RotationInput.bmp` przy użyciu nazwy pliku obrazu i ścieżki prawidłowy w tym systemie.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Ponowne kolorowanie obrazów](recoloring-images.md)
