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
ms.openlocfilehash: e3d1c2b681e98dc7c45467683924dd4022eb377e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937751"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a>Instrukcje: Kopiowanie pikseli w celi zmniejszenia migotania w formularzach systemu Windows
Kiedy animujemy grafiki proste, użytkownicy czasami mogą wystąpić migotania lub inne niepożądane efekty wizualne. Jednym ze sposobów ograniczenia tego problemu jest korzystać z procesu "bitblt" na element graficzny. BitBlt jest "blok bitowy transfer" kolorów danych ze źródła prostokąt pikseli do prostokąta docelowego pikseli.  
  
 Za pomocą interfejsu Windows Forms, bitblt odbywa się przy użyciu <xref:System.Drawing.Graphics.CopyFromScreen%2A> metody <xref:System.Drawing.Graphics> klasy. Parametry metody służy do określenia źródła i miejsca docelowego (punkty), rozmiar obszaru do skopiowania i obiekt grafiki, używany do rysowania nowy kształt.  
  
 W poniższym przykładzie narysować kształt w formularzu w jego <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń. Następnie <xref:System.Drawing.Graphics.CopyFromScreen%2A> metoda służy do duplikowanie kształtu.  
  
> [!NOTE]
>  Ustawienie formularza <xref:System.Windows.Forms.Control.DoubleBuffered%2A> właściwości `true` spowoduje, że kod na podstawie grafiki w <xref:System.Windows.Forms.Control.Paint> zdarzenie być podwójnym buforem. Chociaż nie będzie to miało znaczących korzyści wydajności zauważalny korzystając z poniższego kodu, jest coś, co należy pamiętać, pracując przy bardziej skomplikowanym kodzie manipulowania grafiki.  
  
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
 Powyższy kod jest uruchamiane w postaci <xref:System.Windows.Forms.Control.Paint> program obsługi zdarzeń, aby utrwalić grafiki, gdy formularz jest narysowany ponownie. W efekcie nie wywołuj metody dotyczące grafiki <xref:System.Windows.Forms.Form.Load> procedura obsługi zdarzeń, ponieważ rysowane zawartości nie będzie odświeżana, jeśli zmiany rozmiaru lub zasłonięte innej formy formularza.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Rysowanie linii i kształtów za pomocą pióra](using-a-pen-to-draw-lines-and-shapes.md)
