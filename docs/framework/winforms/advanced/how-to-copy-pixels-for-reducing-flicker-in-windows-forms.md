---
title: 'Porady: kopiowanie pikseli w celi zmniejszenia migotania w formularzach systemu Windows'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8ed463b41d3c2a51b0f9be3d4ddabfd2d54a3c07
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a>Porady: kopiowanie pikseli w celi zmniejszenia migotania w formularzach systemu Windows
Podczas animować proste grafiki, użytkownicy czasami może wystąpić, migotania lub innych niepożądanych skutków visual. Jednym ze sposobów ograniczenia tego problemu jest użycie procesu "bitblt" grafiki. BitBlt jest "blok bitowy transferem" dane koloru z prostokąt pochodzenia pikseli do docelowy prostokąt pikseli.  
  
 W przypadku formularzy systemu Windows bitblt odbywa się przy użyciu <xref:System.Drawing.Graphics.CopyFromScreen%2A> metody <xref:System.Drawing.Graphics> klasy. W parametrach metody określić źródło i miejsca docelowego (punkty), rozmiar obszaru do skopiowania i obiektu graphics używany do rysowania nowy kształt.  
  
 W poniższym przykładzie narysować kształt formularza w jego <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń. Następnie <xref:System.Drawing.Graphics.CopyFromScreen%2A> metoda jest używana do zduplikowane kształtu.  
  
> [!NOTE]
>  Ustawienie formularza <xref:System.Windows.Forms.Control.DoubleBuffered%2A> właściwości `true` spowoduje, że kod na podstawie grafiki <xref:System.Windows.Forms.Control.Paint> zdarzeń można podwójnie buforowany. Gdy nie będzie to miało żadnych wzrost wydajności discernable przy użyciu poniższy kod, jest coś należy wziąć pod uwagę podczas pracy z bardziej złożonego kodu manipulowania grafiki.  
  
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
 Powyższy kod jest uruchamiany w postaci <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń, aby utrwalić grafiki, gdy formularz jest narysowany ponownie. Tak, nie należy wywoływać metody powiązane grafiki <xref:System.Windows.Forms.Form.Load> program obsługi zdarzeń, ponieważ narysowanego zawartość zostanie nie narysowania Jeśli zmiany rozmiaru lub zostanie przesłonięty przez inny formularz formularza.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.CopyPixelOperation>  
 <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>  
 [Grafika i rysowanie w formularzach systemu Windows](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Rysowanie linii i kształtów za pomocą pióra](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
