---
title: 'Jak: Kopiowanie pikseli w celu zmniejszenia migotania'
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
ms.openlocfilehash: a25295532d7123d92bcacc6828d3e8cfcc839d6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182590"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a>Porady: kopiowanie pikseli w celi zmniejszenia migotania w formularzach systemu Windows
Podczas animowania prostej grafiki użytkownicy mogą czasami napotkać migotanie lub inne niepożądane efekty wizualne. Jednym ze sposobów ograniczenia tego problemu jest użycie procesu "bitblt" na grafice. Bitblt jest "bit-block transfer" danych kolorów z prostokąta pochodzenia pikseli do prostokąta docelowego pikseli.  
  
 W formularzu Windows Form bitblt <xref:System.Drawing.Graphics.CopyFromScreen%2A> jest <xref:System.Drawing.Graphics> realizowany przy użyciu metody klasy. W parametrach metody należy określić źródło i miejsce docelowe (jako punkty), rozmiar obszaru, który ma zostać skopiowany, oraz obiekt graficzny używany do rysowania nowego kształtu.  
  
 W poniższym przykładzie kształt jest rysowany <xref:System.Windows.Forms.Control.Paint> na formularzu w jego programie obsługi zdarzeń. Następnie <xref:System.Drawing.Graphics.CopyFromScreen%2A> metoda jest używana do duplikowania kształtu.  
  
> [!NOTE]
> Ustawienie <xref:System.Windows.Forms.Control.DoubleBuffered%2A> właściwości formularza spowoduje, `true` że kod oparty <xref:System.Windows.Forms.Control.Paint> na grafice w zdarzeniu będzie buforowany dwukrotnie. Chociaż nie będzie to miało żadnych zauważalnych wzrost wydajności podczas korzystania z kodu poniżej, jest to coś, o czym należy pamiętać podczas pracy z bardziej złożonym kodem manipulacji grafiką.  
  
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
 Powyższy kod jest uruchamiany <xref:System.Windows.Forms.Control.Paint> w programie obsługi zdarzeń formularza, dzięki czemu grafika będzie zachowywana po ponownym narysowaniu formularza. W związku z tym nie należy <xref:System.Windows.Forms.Form.Load> wywoływać metod związanych z grafiką w programie obsługi zdarzeń, ponieważ narysowana zawartość nie zostanie ponownie narysowana, jeśli formularz zostanie zmieniona lub zasłonięta przez inny formularz.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Rysowanie linii i kształtów za pomocą pióra](using-a-pen-to-draw-lines-and-shapes.md)
