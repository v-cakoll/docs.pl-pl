---
title: 'Porady: rysowanie za pomocą nieprzezroczystych i półprzezroczystych pędzli'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- semi-transparent shapes [Windows Forms], drawing
- transparency [Windows Forms], semi-transparent shapes
- alpha blending [Windows Forms], brush
- brushes [Windows Forms], using semi-transparent
ms.assetid: a4f6f6b8-3bc8-440a-84af-d62ef0f8ff40
ms.openlocfilehash: 91aa3e89e2ff6d20432dbc5e988f2877059b4cdd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a>Porady: rysowanie za pomocą nieprzezroczystych i półprzezroczystych pędzli
Podczas wypełnienia kształtu, należy przekazać <xref:System.Drawing.Brush> obiektu do jednej z metod wypełnienia <xref:System.Drawing.Graphics> klasy. Jeden parametr <xref:System.Drawing.SolidBrush.%23ctor%2A> Konstruktor jest <xref:System.Drawing.Color> obiektu. Aby wypełnić kształt nieprzezroczyste, należy ustawić składnika alfa koloru do 255. Aby wypełnić półprzezroczystych kształtu, należy ustawić składnika alfa na wartość od 1 do 254.  
  
 Po wypełnieniu półprzezroczystych kształtu kolor kształtu mieszania kolorów tła. Składnik alfa określa, jak kolory tła i kształtu mieszane; wartości alfa niemal 0 umieść ważniejsze na kolory tła i wartości alfa niemal 255 umieść ważniejsze na kolor kształtu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie map bitowych rysuje i następnie wypełnia wielokropek trzech, które nakładają się na mapy bitowej. Pierwszy elipsy używa składnika alfa 255, tak aby zawierała nieprzezroczyste. Wielokropek drugiego i trzeciego Użyj składnika alfa 128, dzięki czemu są one półprzezroczystych; obraz tła za pośrednictwem wielokropek jest widoczny. Wywołanie, która ustawia <xref:System.Drawing.Graphics.CompositingQuality%2A> właściwość powodująca usunięcie mieszania trzeci elipsy w połączeniu z korekcja gamma.  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe poniższy kod.  
  
 ![Nieprzezroczystych i półprzezroczystych](../../../../docs/framework/winforms/advanced/media/compqualellipse.png "compqualellipse")  
  
 [!code-csharp[System.Drawing.AlphaBlending#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Powyższy przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz też  
 [Grafika i rysowanie w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Przenikanie alfa linii i wypełnień](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)  
 [Instrukcje: ustawienie przezroczystego tła kontrolki](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 [Instrukcje: rysowanie nieprzezroczystych i półprzezroczystych linii](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
