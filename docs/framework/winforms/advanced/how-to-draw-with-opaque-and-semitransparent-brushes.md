---
title: 'Instrukcje: Rysowanie za pomocą nieprzezroczystych i półprzezroczystych pędzli'
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
ms.openlocfilehash: a302b8bf978afcead5768fadeb6336c1ece986ec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100933"
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a>Instrukcje: Rysowanie za pomocą nieprzezroczystych i półprzezroczystych pędzli
Po wypełnieniu kształtu, należy przekazać <xref:System.Drawing.Brush> obiektu do jednej z metod wypełnienia <xref:System.Drawing.Graphics> klasy. Jeden parametr <xref:System.Drawing.SolidBrush.%23ctor%2A> Konstruktor jest <xref:System.Drawing.Color> obiektu. Do wypełnienia kształtu nieprzezroczysty, ustaw składnik alfa koloru do 255. Aby wypełnić półprzezroczystych kształtu, ustaw składnik alfa dowolną wartość od 1 do 254.  
  
 Po wypełnieniu półprzezroczystych kształt, kolor kształtu jest zmieszana przy użyciu kolorów tła. Składnik alfa określa, jak są zmieszane kształt i kolor tła; wartości alfa niemal 0 ważniejsze na kolory tła i wartości alfa niemal 255 umieścić więcej wagi na kolor kształtu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera mapę bitową i następnie wypełnia trzy wielokropek, które nakładają się na mapę bitową. Pierwszy elipsy używa składnik alfa, 255, więc jest nieprzezroczysta. Wielokropek drugi i trzeci Użyj składnik alfa, 128, dzięki czemu są one półprzezroczystych; obraz tła za pośrednictwem wielokropek jest widoczny. Wywołanie, które ustawia <xref:System.Drawing.Graphics.CompositingQuality%2A> właściwości powoduje, że mieszanie trzeci ikonę wielokropka, aby to zrobić w połączeniu z korekcji gamma.  

 [!code-csharp[System.Drawing.AlphaBlending#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  

 Na poniższej ilustracji przedstawiono dane wyjściowe następujący kod: 
  
 ![Ilustracja przedstawiająca nieprzezroczystych i półprzezroczystych danych wyjściowych.](./media/how-to-draw-with-opaque-and-semitransparent-brushes/compositingquality-ellipse-semitransparent.png)  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs>`e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz także

- [Grafika i rysowanie w formularzach systemu Windows](graphics-and-drawing-in-windows-forms.md)
- [Przenikanie alfa linii i wypełnień](alpha-blending-lines-and-fills.md)
- [Instrukcje: ustawienie przezroczystego tła kontrolki](../controls/how-to-give-your-control-a-transparent-background.md)
- [Instrukcje: Rysowanie nieprzezroczystych i półprzezroczystych linii](how-to-draw-opaque-and-semitransparent-lines.md)
