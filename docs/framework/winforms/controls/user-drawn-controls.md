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
ms.openlocfilehash: 50036f5bef323368b4970a080ca7a70cf94252d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966485"
---
# <a name="user-drawn-controls"></a>Formanty rysowane przez użytkownika
.NET Framework zapewnia możliwość łatwego tworzenia własnych kontrolek. Można utworzyć kontrolkę użytkownika, która jest zestawem standardowych kontrolek powiązanych ze sobą za pomocą kodu lub można zaprojektować własny formant od podstaw. Można nawet użyć dziedziczenia, aby utworzyć kontrolkę, która dziedziczy z istniejącej kontrolki i dodaje do jej funkcjonalności. Niezależnie od tego, z jakich sposobów korzystasz, .NET Framework zapewnia funkcjonalność do rysowania niestandardowego interfejsu graficznego dla każdej tworzonego formantu.  
  
 Malowanie kontrolki odbywa się przez wykonanie kodu w <xref:System.Windows.Forms.Control.OnPaint%2A> metodzie formantu. Pojedynczy argument <xref:System.Windows.Forms.Control.OnPaint%2A> metody <xref:System.Windows.Forms.PaintEventArgs> jest obiektem, który zawiera wszystkie informacje i funkcje wymagane do renderowania formantu. <xref:System.Windows.Forms.PaintEventArgs> Zapewnia jako właściwości dwa obiekty główne, które będą używane podczas renderowania kontrolki:  
  
- <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>Object — prostokąt, który reprezentuje część kontrolki, która zostanie narysowana. Może to być cała kontrolka lub część kontrolki w zależności od sposobu rysowania kontrolki.  
  
- <xref:System.Drawing.Graphics>Object — hermetyzuje kilka obiektów i metod zorientowanych na grafiki, które zapewniają funkcje niezbędne do narysowania kontrolki.  
  
 Aby uzyskać więcej informacji na <xref:System.Drawing.Graphics> temat obiektu i sposobu jego użycia, zobacz [How to: Utwórz obiekty graficzne do rysowania](../advanced/how-to-create-graphics-objects-for-drawing.md).  
  
 Zdarzenie jest wyzwalane za każdym razem, gdy kontrolka jest rysowana lub odświeżana na <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> ekranie, a obiekt reprezentuje prostokąt, w którym nastąpi malowanie. <xref:System.Windows.Forms.Control.OnPaint%2A> Jeśli cała kontrolka musi zostać odświeżona, <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> będzie reprezentować rozmiar całej kontrolki. Jeśli jednak <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> tylko część kontrolki wymaga odświeżenia, obiekt będzie reprezentował tylko region, który musi zostać narysowany ponownie. Przykładem takiego przypadku może być, gdy kontrolka została częściowo zasłonięta przez inny formant lub formularz w interfejsie użytkownika.  
  
 W przypadku dziedziczenia z <xref:System.Windows.Forms.Control> klasy należy <xref:System.Windows.Forms.Control.OnPaint%2A> zastąpić metodę i udostępnić kod renderowania grafiki w obrębie. Jeśli chcesz dostarczyć niestandardowy interfejs graficzny do kontrolki użytkownika lub dziedziczonej kontrolki, możesz to zrobić, zastępując <xref:System.Windows.Forms.Control.OnPaint%2A> metodę. Poniżej przedstawiono przykład:  
  
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
  
 W poprzednim przykładzie pokazano, jak renderować formant z bardzo prostą reprezentacją graficzną. Wywołuje <xref:System.Windows.Forms.Control.OnPaint%2A> metodę klasy bazowej, <xref:System.Drawing.Pen> tworzy obiekt, z którym należy narysować, i na koniec Rysuje elipsę w prostokącie określonym przez <xref:System.Windows.Forms.Control.Location%2A> i <xref:System.Windows.Forms.Control.Size%2A> kontrolkę. Chociaż większość kodu renderowania będzie znacznie bardziej skomplikowana niż ta, ten przykład demonstruje użycie <xref:System.Drawing.Graphics> obiektu zawartego <xref:System.Windows.Forms.PaintEventArgs> w obiekcie. Należy pamiętać, że jeśli dziedziczą z klasy, która ma już reprezentację graficzną, taką <xref:System.Windows.Forms.UserControl> jak <xref:System.Windows.Forms.Button>lub, i nie chcesz dołączać tej reprezentacji do renderowania, nie należy <xref:System.Windows.Forms.Control.OnPaint%2A> wywoływać klasy bazowej Method.  
  
 Kod w <xref:System.Windows.Forms.Control.OnPaint%2A> metodzie formantu będzie wykonywany, gdy kontrolka zostanie narysowana po raz pierwszy, i za każdym razem, gdy zostanie odświeżony. Aby upewnić się, że formant jest ponownie rysowany przy każdej zmianie rozmiaru, Dodaj następujący wiersz do konstruktora formantu:  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
> Użyj właściwości <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> , aby zaimplementować kontrolkę nieprostokątną.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [Instrukcje: Tworzenie obiektów graficznych do rysowania](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [Kontrolki składników](constituent-controls.md)
- [Różne typy kontrolek niestandardowych](varieties-of-custom-controls.md)
