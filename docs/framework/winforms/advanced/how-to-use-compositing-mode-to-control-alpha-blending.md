---
title: 'Instrukcje: Stosowanie trybu składania do sterowania przenikaniem alfa'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- alpha blending [Windows Forms], compositing
- colors [Windows Forms], blending
- colors [Windows Forms], controlling transparency
ms.assetid: f331df2d-b395-4b0a-95be-24fec8c9bbb5
ms.openlocfilehash: 6863e59efa25323f80933bf8ab595316b430ef53
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590143"
---
# <a name="how-to-use-compositing-mode-to-control-alpha-blending"></a>Instrukcje: Stosowanie trybu składania do sterowania przenikaniem alfa
Mogą wystąpić sytuacje, gdy chcesz utworzyć poza ekranem mapy bitowej, która ma następujące cechy:  
  
- Kolory mają wartości alfa, które są mniej niż 255.  
  
- Kolory nie są alfa połączeniu ze sobą, jak tworzenie mapy bitowej.  
  
- Podczas wyświetlania mapy bitowej Zakończono kolorów w mapie bitowej są przenikaniem za pomocą kolorów tła na urządzenia wyświetlającego alfa.  
  
 Aby utworzyć mapę bitową, należy utworzyć pusty <xref:System.Drawing.Bitmap> obiektu, a następnie utworzyć <xref:System.Drawing.Graphics> obiektu oparte na tej mapy bitowej. Ustawianie trybu składania <xref:System.Drawing.Graphics> obiekt <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Drawing.Graphics> na podstawie obiektu <xref:System.Drawing.Bitmap> obiektu. Kod używa <xref:System.Drawing.Graphics> obiektu wraz z dwóch półprzezroczystych pędzli (alfa = 160) do malowania mapy bitowej. Kod wprowadza czerwony elipsy i zielony elipsy, przy użyciu półprzezroczystych pędzli. Zielony elipsy nakłada się na czerwony elipsy, ale zielony nie jest zmieszana z czerwonym, ponieważ tryb składania <xref:System.Drawing.Graphics> obiekt jest ustawiony na <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>.  
  
 Kod rysuje mapy bitowej na ekranie dwa razy: jeden raz na białym tle i jeden raz na tle różnych kolorach. Piksele w mapie bitowej, które są dostępne w ramach dwóch wielokropek ma składnik alfa 160, więc wielokropek są mieszane za pomocą kolorów tła na ekranie.  
  
 Poniższa ilustracja przedstawia dane wyjściowe w przykładzie kodu. Należy pamiętać, że wielokropek są mieszane w tle, ale nie są one mieszane ze sobą.  
  
 ![Diagram przedstawiający wielokropek mieszane w tle, nie siebie nawzajem.](./media/how-to-use-compositing-mode-to-control-alpha-blending/ellipses-blended-background.png)  
  
 Przykładowy kod zawiera tej instrukcji:  
  
 [!code-csharp[System.Drawing.AlphaBlending#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.AlphaBlending#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#41)]  
  
 Jeśli wielokropek, aby być mieszany ze sobą, a także w tle, należy zmienić tej instrukcji do następujących:  
  
 [!code-csharp[System.Drawing.AlphaBlending#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.AlphaBlending#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#42)]  
  
 Poniższa ilustracja przedstawia dane wyjściowe poprawiony kod.  
  
 ![Diagram przedstawiający wielokropek połączeniu ze sobą oraz z tła.](./media/how-to-use-compositing-mode-to-control-alpha-blending/blend-ellipses-background.png)  
  
 [!code-csharp[System.Drawing.AlphaBlending#43](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#43)]
 [!code-vb[System.Drawing.AlphaBlending#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#43)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.Color.FromArgb%2A>
- [Przenikanie alfa linii i wypełnień](alpha-blending-lines-and-fills.md)
