---
title: 'Instrukcje: Rysowanie nieprzezroczystych i półprzezroczystych linii'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- transparency [Windows Forms], lines
- lines [Windows Forms], drawing alpha blended
- alpha blending [Windows Forms], drawing lines
ms.assetid: 8f2508af-f495-4223-b5cc-646cbbb520eb
ms.openlocfilehash: 7408722dc13e83828cfca3f0615a2730e3c53461
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188269"
---
# <a name="how-to-draw-opaque-and-semitransparent-lines"></a>Instrukcje: Rysowanie nieprzezroczystych i półprzezroczystych linii
Po narysowaniu linii, należy przekazać <xref:System.Drawing.Pen> obiekt <xref:System.Drawing.Graphics.DrawLine%2A> metody <xref:System.Drawing.Graphics> klasy. Jeden z parametrów <xref:System.Drawing.Pen.%23ctor%2A> Konstruktor jest <xref:System.Drawing.Color> obiektu. Aby narysować linię nieprzezroczysty, ustaw składnik alfa koloru do 255. Aby narysować linię półprzezroczystych, należy ustawić składnik alfa na wartość od 1 do 254.  
  
 Kiedy rysujesz półprzezroczystych linii w tle koloru linii jest zmieszana przy użyciu kolorów tła. Składnik alfa określa, jak kolory tła i wiersza są mieszane; wartości alfa niemal 0 ważniejsze na kolory tła i wartości alfa niemal 255 umieścić więcej wagi na kolor linii.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera mapę bitową i następnie pobiera trzy wiersze, korzystających z mapy bitowej jako tło. Pierwszy wiersz używa składnik alfa, 255, więc jest nieprzezroczysta. Wiersze drugi i trzeci Użyj składnik alfa, 128, dzięki czemu są one półprzezroczystych; Możesz zobaczyć obraz tła za pośrednictwem wierszy. Instrukcja, która ustawia <xref:System.Drawing.Graphics.CompositingQuality%2A> właściwości powoduje, że mieszanie trzeci wiersz do wykonania w połączeniu z korekcji gamma.  
  
 [!code-csharp[System.Drawing.AlphaBlending#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.AlphaBlending#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#11)]  
  
 Na poniższej ilustracji przedstawiono dane wyjściowe następujący kod:  
  
 ![Ilustracja przedstawiająca nieprzezroczystych i półprzezroczystych danych wyjściowych](./media/how-to-draw-opaque-and-semitransparent-lines/opaque-semitransparent-lines.png)  

## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs>`e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także

- [Przenikanie alfa linii i wypełnień](alpha-blending-lines-and-fills.md)
- [Instrukcje: ustawienie przezroczystego tła kontrolki](../controls/how-to-give-your-control-a-transparent-background.md)
- [Instrukcje: Rysowanie za pomocą nieprzezroczystych i półprzezroczystych pędzli](how-to-draw-with-opaque-and-semitransparent-brushes.md)
