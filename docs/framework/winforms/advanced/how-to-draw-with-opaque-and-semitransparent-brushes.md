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
ms.openlocfilehash: 1e48bbd563f6377380848949325962b568fa432c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142410"
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a>Porady: rysowanie za pomocą nieprzezroczystych i półprzezroczystych pędzli
Podczas wypełniania kształtu należy <xref:System.Drawing.Brush> przekazać obiekt do jednej z <xref:System.Drawing.Graphics> metod wypełniania klasy. Jednym z parametrów <xref:System.Drawing.SolidBrush.%23ctor%2A> konstruktora <xref:System.Drawing.Color> jest obiekt. Aby wypełnić nieprzezroczysty kształt, należy ustawić składnik alfa koloru na 255. Aby wypełnić kształt półprzezroczysty, należy ustawić komponent alfa na dowolną wartość od 1 do 254.  
  
 Po wypełnieniu półprzezroczysty kształt kolor kształtu jest mieszany z kolorami tła. Składnik alfa określa sposób mieszania kolorów kształtu i tła; wartości alfa w pobliżu 0 umieścić większą wagę na kolorach tła, a wartości alfa w pobliżu 255 umieścić większą wagę na kolor kształtu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rysuje mapę bitową, a następnie wypełnia trzy elipsy, które nakładają się na mapę bitową. Pierwsza elipsa używa składnika alfa 255, więc jest nieprzezroczysta. Druga i trzecia elipsy używają składnika alfa 128, więc są półprzezroczysty; można zobaczyć obraz tła przez elipsy. Wywołanie, które <xref:System.Drawing.Graphics.CompositingQuality%2A> ustawia właściwość powoduje mieszania dla trzeciej elipsy, które mają być wykonane w połączeniu z poprawki gamma.  

 [!code-csharp[System.Drawing.AlphaBlending#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  

 Na poniższej ilustracji przedstawiono dane wyjściowe następującego kodu:
  
 ![Ilustracja przedstawiająca nieprzezroczyste i półprzezroczyste wyjście.](./media/how-to-draw-with-opaque-and-semitransparent-brushes/compositingquality-ellipse-semitransparent.png)  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Powyższy przykład jest przeznaczony do użytku z <xref:System.Windows.Forms.PaintEventArgs> `e`formularzami systemu Windows <xref:System.Windows.Forms.PaintEventHandler>i wymaga , który jest parametrem .  
  
## <a name="see-also"></a>Zobacz też

- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Przenikanie alfa linii i wypełnień](alpha-blending-lines-and-fills.md)
- [Porady: ustawienie przezroczystego tła formantu](../controls/how-to-give-your-control-a-transparent-background.md)
- [Instrukcje: rysowanie nieprzezroczystych i półprzezroczystych linii](how-to-draw-opaque-and-semitransparent-lines.md)
