---
title: Formanty rysowane przez użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user-drawn
- OnPaint method [Windows Forms]
- user-drawn controls [Windows Forms]
ms.assetid: 034af4b5-457f-4160-a937-22891817faa8
ms.openlocfilehash: c68c8c88376cfe7295962264c466030115f2f3db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182010"
---
# <a name="user-drawn-controls"></a>Formanty rysowane przez użytkownika
.NET Framework zapewnia możliwość łatwego tworzenia własnych formantów. Można utworzyć formant użytkownika, który jest zestawem standardowych formantów połączonych ze sobą kodem lub można zaprojektować własny formant od podstaw. Można nawet użyć dziedziczenia, aby utworzyć formant, który dziedziczy z istniejącego formantu i dodać do jego funkcji. Niezależnie od używanego podejścia program .NET Framework udostępnia funkcje rysowania niestandardowego interfejsu graficznego dla każdego utworzonego formantu.  
  
 Malowanie formantu odbywa się przez wykonanie kodu <xref:System.Windows.Forms.Control.OnPaint%2A> w metodzie formantu. Pojedynczy argument <xref:System.Windows.Forms.Control.OnPaint%2A> metody jest <xref:System.Windows.Forms.PaintEventArgs> obiektem, który zawiera wszystkie informacje i funkcje wymagane do renderowania kontroli. Udostępnia <xref:System.Windows.Forms.PaintEventArgs> jako właściwości dwa główne obiekty, które będą używane w renderowaniu formantu:  
  
- <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>object - prostokąt reprezentujący część formantu, która zostanie narysowana. Może to być cały formant lub część formantu w zależności od sposobu rysowania formantu.  
  
- <xref:System.Drawing.Graphics>object - hermetyzuje kilka obiektów zorientowanych na grafikę i metody, które zapewniają funkcjonalność niezbędną do narysowania formantu.  
  
 Aby uzyskać więcej <xref:System.Drawing.Graphics> informacji na temat obiektu i sposobu jego używania, zobacz [Jak: Tworzenie obiektów graficznych do rysowania](../advanced/how-to-create-graphics-objects-for-drawing.md).  
  
 Zdarzenie <xref:System.Windows.Forms.Control.OnPaint%2A> jest uruchamiane za każdym razem, gdy formant <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> jest rysowany lub odświeżany na ekranie, a obiekt reprezentuje prostokąt, w którym będzie odbywać się malowanie. Jeśli cały formant musi zostać <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> odświeżony, będzie reprezentować rozmiar całego formantu. Jeśli tylko część formantu musi zostać odświeżona, <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> obiekt będzie reprezentować tylko region, który musi zostać ponownie narysowany. Przykładem takiego przypadku może być, gdy formant został częściowo zasłonięte przez inny formant lub formularz w interfejsie użytkownika.  
  
 Podczas dziedziczenia <xref:System.Windows.Forms.Control> z klasy, należy <xref:System.Windows.Forms.Control.OnPaint%2A> zastąpić metodę i podać kod renderowania grafiki w ramach. Jeśli chcesz zapewnić niestandardowy interfejs graficzny do formantu użytkownika lub formantu dziedziczonego, można również to zrobić, zastępując <xref:System.Windows.Forms.Control.OnPaint%2A> metodę. Przykład przedstawiono poniżej:  
  
```vb  
Protected Overrides Sub OnPaint(ByVal e As PaintEventArgs)  
   ' Call the OnPaint method of the base class.  
   MyBase.OnPaint(e)  
  
   ' Declare and instantiate a drawing pen.  
   Using myPen As System.Drawing.Pen = New System.Drawing.Pen(Color.Aqua)  
      ' Draw an aqua rectangle in the rectangle represented by the control.  
      e.Graphics.DrawRectangle(myPen, New Rectangle(Me.Location, Me.Size))  
   End Using
End Sub  
```  
  
```csharp  
protected override void OnPaint(PaintEventArgs e)  
{  
   // Call the OnPaint method of the base class.  
   base.OnPaint(e);  
  
   // Declare and instantiate a new pen.  
   using (System.Drawing.Pen myPen = new System.Drawing.Pen(Color.Aqua))  
   {
      // Draw an aqua rectangle in the rectangle represented by the control.  
      e.Graphics.DrawRectangle(myPen, new Rectangle(this.Location,
         this.Size));  
   }
}  
```  
  
 W poprzednim przykładzie pokazano, jak renderować formant z bardzo prostą reprezentacją graficzną. Wywołuje <xref:System.Windows.Forms.Control.OnPaint%2A> metodę klasy podstawowej, tworzy <xref:System.Drawing.Pen> obiekt, z którym można rysować, a na końcu rysuje elipsę w prostokącie określonym przez <xref:System.Windows.Forms.Control.Location%2A> i <xref:System.Windows.Forms.Control.Size%2A> formantu. Chociaż większość kodu renderowania będzie znacznie bardziej skomplikowane niż to, <xref:System.Drawing.Graphics> w tym przykładzie pokazuje użycie obiektu znajdującego <xref:System.Windows.Forms.PaintEventArgs> się w obiekcie. Należy zauważyć, że jeśli dziedziczenie z klasy, która ma <xref:System.Windows.Forms.UserControl> <xref:System.Windows.Forms.Button>już graficzne przedstawienie, takie jak lub , i nie chcesz włączyć tej <xref:System.Windows.Forms.Control.OnPaint%2A> reprezentacji do renderowania, nie należy wywoływać metody klasy podstawowej.  
  
 Kod w <xref:System.Windows.Forms.Control.OnPaint%2A> metodzie formantu zostanie wykonany, gdy formant jest po raz pierwszy rysowany i gdy jest odświeżany. Aby upewnić się, że formant jest ponownie rysowany za każdym razem, gdy jest zmieniany, dodaj następujący wiersz do konstruktora formantu:  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
> Użyj <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> właściwości, aby zaimplementować formant nie prostokątny.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [Instrukcje: tworzenie obiektów graficznych do rysowania](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [Formanty składników](constituent-controls.md)
- [Różne typy kontrolek niestandardowych](varieties-of-custom-controls.md)
