---
title: 'Instrukcje: Rysowanie niestandardowej linii kreskowanej'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], custom
- lines [Windows Forms], drawing
- lines [Windows Forms], dashed
ms.assetid: cd0ed96a-cce4-47b9-b58a-3bae2e3d1bee
ms.openlocfilehash: 8dc1ad41cf8067bea5b811ca126ad29f5a600f69
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59109190"
---
# <a name="how-to-draw-a-custom-dashed-line"></a>Instrukcje: Rysowanie niestandardowej linii kreskowanej
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] dostępnych jest kilka typów dash, które są wymienione w <xref:System.Drawing.Drawing2D.DashStyle> wyliczenia. Jeśli te style standard dash nie spełnia Twoich potrzeb, można utworzyć wzorze kreskowym niestandardowych.  
  
## <a name="example"></a>Przykład  
 Rysowanie niestandardowej linii kreskowanej, umieścić długości kresek i spacji w tablicy, a następnie przypisać tablicę jako wartość <xref:System.Drawing.Pen.DashPattern%2A> właściwość <xref:System.Drawing.Pen> obiektu. Poniższy przykład pobiera niestandardowej linii kreskowanej oparte na tablicy `{5, 2, 15, 4}`. Jeśli elementy tablicy są mnożenia szerokość pióra, 5, możesz uzyskać `{25, 10, 75, 20}`. Łączniki wyświetlanych alternatywny o długości od 25 do 75 i spacje alternatywny o długości od 10 do 20.  
  
 Poniższa ilustracja przedstawia wynikowy linia przerywana. Należy zauważyć, że końcowej kreski, musi być krótsza niż 25 jednostek, tak, aby zakończyć w wierszu (405, 5).  
  
 ![Ilustracja przedstawiająca linia przerywana. ](./media/how-to-draw-a-custom-dashed-line/dashed-line-illustration.gif "pens6")  
  
 [!code-csharp[System.Drawing.UsingAPen#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.UsingAPen#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Tworzenie formularza Windows i obsłużyć formularza <xref:System.Windows.Forms.Control.Paint> zdarzeń. Wklej poprzedni kod z gałęzią <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz także

- [Rysowanie linii i kształtów za pomocą pióra](using-a-pen-to-draw-lines-and-shapes.md)
