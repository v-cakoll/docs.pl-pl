---
title: 'Instrukcje: Kopiowanie pikseli w celi zmniejszenia migotania w formularzach systemu Windows'
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
ms.openlocfilehash: 5a18539153c64a5059d8079f6e245115b026bb91
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950148"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a>Instrukcje: Kopiowanie pikseli w celi zmniejszenia migotania w formularzach systemu Windows
W przypadku animowania prostej grafiki użytkownicy mogą czasami napotkać migotanie lub inne niepożądane efekty wizualne. Jednym ze sposobów ograniczenia tego problemu jest użycie w grafice procesu "BitBlt". BitBlt to "bit-Block transfer" danych koloru z prostokąta początkowego pikseli do docelowego prostokąta pikseli.  
  
 W Windows Forms BitBlt jest realizowana przy użyciu <xref:System.Drawing.Graphics.CopyFromScreen%2A> metody <xref:System.Drawing.Graphics> klasy. W parametrach metody należy określić źródło i miejsce docelowe (jako punkty), rozmiar obszaru, który ma zostać skopiowany, oraz obiekt graficzny używany do rysowania nowego kształtu.  
  
 W poniższym przykładzie kształt jest rysowany w formularzu w jego <xref:System.Windows.Forms.Control.Paint> obsłudze zdarzeń. <xref:System.Drawing.Graphics.CopyFromScreen%2A> Następnie metoda jest używana do duplikowania kształtu.  
  
> [!NOTE]
> Ustawienie <xref:System.Windows.Forms.Control.DoubleBuffered%2A> właściwości formularza na to spowoduje `true` , że kod graficzny w <xref:System.Windows.Forms.Control.Paint> zdarzeniu będzie znajdować się w podwójnym buforze. Chociaż nie będzie to miało dostrzegalnego wzrostu wydajności podczas korzystania z poniższego kodu, należy pamiętać o tym, kiedy pracujesz z bardziej złożonym kodem operowania grafiki.  
  
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
 Powyższy kod jest uruchamiany w programie obsługi <xref:System.Windows.Forms.Control.Paint> zdarzeń formularza, aby grafika była zachowywana po odrysowaniu formularza. W związku z tym nie należy wywoływać metod związanych z grafiki <xref:System.Windows.Forms.Form.Load> w programie obsługi zdarzeń, ponieważ narysowana zawartość nie zostanie ponownie narysowana, jeśli rozmiar formularza zostanie zmieniony lub zasłonięty przez inny formularz.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Rysowanie linii i kształtów za pomocą pióra](using-a-pen-to-draw-lines-and-shapes.md)
