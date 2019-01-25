---
title: 'Instrukcje: Rysowanie linii wypełnionej teksturą'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], texture
- drawing lines [Windows Forms], texture
ms.assetid: dc9118cc-f3c2-42e5-8173-f46d41d18fd5
ms.openlocfilehash: 65d830ca2d01c63288ef73b6b3a3a94f328fe32b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676249"
---
# <a name="how-to-draw-a-line-filled-with-a-texture"></a>Instrukcje: Rysowanie linii wypełnionej teksturą
Zamiast Rysowanie linii za pomocą jednolitego koloru, można narysować linię z teksturą. Rysowanie linii i krzywych teksturą, należy utworzyć <xref:System.Drawing.TextureBrush> obiektu i przekaż go <xref:System.Drawing.TextureBrush> obiekt <xref:System.Drawing.Pen.%23ctor%2A> konstruktora. Mapy bitowej skojarzone z pędzla tekstury jest używany do kafelka na płaszczyźnie (niewidocznie), a gdy Pióro rysuje linię lub krzywą, pociągnięcia pióra odkrywa niektórych pikseli tekstury fragmentacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Drawing.Bitmap> obiektu na podstawie pliku `Texture1.jpg`. Tej mapy bitowej służy do konstruowania <xref:System.Drawing.TextureBrush> obiektu, a <xref:System.Drawing.TextureBrush> obiekt jest używany do utworzenia <xref:System.Drawing.Pen> obiektu. Wywołanie <xref:System.Drawing.Graphics.DrawImage%2A> rysuje mapę bitową z jego lewego górnego rogu w (0, 0). Wywołanie <xref:System.Drawing.Graphics.DrawEllipse%2A> używa <xref:System.Drawing.Pen> obiektu, aby narysować elipsę teksturą.  
  
 Na poniższej ilustracji zawiera mapę bitową i teksturą elipsy.  
  
 ![Pióra](../../../../docs/framework/winforms/advanced/media/pens7.png "pens7")  
  
 [!code-csharp[System.Drawing.UsingAPen#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.UsingAPen#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Tworzenie formularza Windows i obsłużyć formularza <xref:System.Windows.Forms.Control.Paint> zdarzeń. Wklej poprzedni kod z gałęzią <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń. Zastąp `Texture.jpg` obrazem prawidłowy w tym systemie.  
  
## <a name="see-also"></a>Zobacz także
- [Rysowanie linii i kształtów za pomocą pióra](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
- [Grafika i rysowanie w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
