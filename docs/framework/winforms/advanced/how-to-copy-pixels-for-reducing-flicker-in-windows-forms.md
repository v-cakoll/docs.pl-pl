---
title: 'Instrukcje: kopiowanie pikseli w celu zmniejszenia migotania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitblt
- graphics [Windows Forms], copying
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing flicker
- pixels [Windows Forms], copying
- flicker
- bit-block transfer
ms.assetid: 33b76910-13a3-4521-be98-5c097341ae3b
ms.openlocfilehash: 299041e7038d5bd5b9824d668b3f47d842030ac7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746484"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a>Porady: kopiowanie pikseli w celi zmniejszenia migotania w formularzach systemu Windows
W przypadku animowania prostej grafiki użytkownicy mogą czasami napotkać migotanie lub inne niepożądane efekty wizualne. Jednym ze sposobów ograniczenia tego problemu jest użycie w grafice procesu "BitBlt". BitBlt to "bit-Block transfer" danych koloru z prostokąta początkowego pikseli do docelowego prostokąta pikseli.  
  
 W Windows Forms BitBlt jest realizowana przy użyciu metody <xref:System.Drawing.Graphics.CopyFromScreen%2A> klasy <xref:System.Drawing.Graphics>. W parametrach metody należy określić źródło i miejsce docelowe (jako punkty), rozmiar obszaru, który ma zostać skopiowany, oraz obiekt graficzny używany do rysowania nowego kształtu.  
  
 W poniższym przykładzie kształt jest rysowany w formularzu w jego obsłudze zdarzeń <xref:System.Windows.Forms.Control.Paint>. Następnie do duplikowania kształtu zostanie użyta metoda <xref:System.Drawing.Graphics.CopyFromScreen%2A>.  
  
> [!NOTE]
> Ustawienie właściwości <xref:System.Windows.Forms.Control.DoubleBuffered%2A> formularza na `true` spowoduje, że kod oparty na grafice w zdarzeniu <xref:System.Windows.Forms.Control.Paint> będzie dwukrotnie buforowany. Chociaż nie będzie to miało dostrzegalnego wzrostu wydajności podczas korzystania z poniższego kodu, należy pamiętać o tym, kiedy pracujesz z bardziej złożonym kodem operowania grafiki.  
  
## <a name="example"></a>Przykład  
  
```vb  
Private Sub Form1_Paint(ByVal sender As Object, ByVal e As _  
    System.Windows.Forms.PaintEventArgs) Handles MyBase.Paint  
    ' Draw a circle with a bar on top.  
        e.Graphics.FillEllipse(Brushes.DarkBlue, New Rectangle _  
             (10, 10, 60, 60))  
        e.Graphics.FillRectangle(Brushes.Khaki, New Rectangle _  
             (20, 30, 60, 10))  
    ' Copy the graphic to a new location.  
        e.Graphics.CopyFromScreen(New Point(10, 10), New Point _  
             (100, 100), New Size(70, 70))  
End Sub  
```  
  
```csharp  
private void Form1_Paint(System.Object sender,  
    System.Windows.Forms.PaintEventArgs e)  
        {  
        e.Graphics.FillEllipse(Brushes.DarkBlue, new  
            Rectangle(10,10,60,60));  
        e.Graphics.FillRectangle(Brushes.Khaki, new  
            Rectangle(20,30,60,10));  
        e.Graphics.CopyFromScreen(new Point(10, 10), new Point(100, 100),   
            new Size(70, 70));  
}  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Powyższy kod jest uruchamiany w programie obsługi zdarzeń <xref:System.Windows.Forms.Control.Paint> formularza, aby grafika była zachowywana po odrysowaniu formularza. W związku z tym nie należy wywoływać metod związanych z grafiki w programie obsługi zdarzeń <xref:System.Windows.Forms.Form.Load>, ponieważ narysowana zawartość nie zostanie ponownie narysowana, jeśli rozmiar formularza zostanie zmieniony lub zasłonięty przez inny formularz.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Rysowanie linii i kształtów za pomocą pióra](using-a-pen-to-draw-lines-and-shapes.md)
