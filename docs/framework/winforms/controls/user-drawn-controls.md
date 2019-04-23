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
ms.openlocfilehash: 06513fc44782c78d2d69b82130542949519c0107
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158447"
---
# <a name="user-drawn-controls"></a>Formanty rysowane przez użytkownika
.NET Framework umożliwia łatwe tworzenie własnych kontrolek. Można utworzyć kontrolkę użytkownika, który jest zestaw standardowych kontrolek powiązane przez kod, lub można zaprojektować kontrolki od podstaw w górę. Dziedziczenie umożliwia nawet utworzyć formant, który dziedziczy istniejący formant i dodać do jej nieodłączne funkcjonalność. Niezależnie od podejścia, możesz użyć programu .NET Framework zapewnia funkcje do rysowania niestandardowy interfejs graficzny dla dowolnego formantu, który tworzysz.  
  
 Malowanie kontrolki odbywa się przez wykonywanie kodu w formancie <xref:System.Windows.Forms.Control.OnPaint%2A> metody. Pojedynczy argument <xref:System.Windows.Forms.Control.OnPaint%2A> metodą jest <xref:System.Windows.Forms.PaintEventArgs> obiektu, który zawiera wszystkie informacje i funkcje wymagane do renderowania kontrolki. <xref:System.Windows.Forms.PaintEventArgs> Zapewnia jako właściwości dwa obiekty jednostki, które będą używane w czasie renderowania kontrolki:  
  
-   <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> Obiekt - prostokąt, który reprezentuje część kontrolki, z którego będą pobierane. Może to być całą formantu lub część formantu w zależności od tego, jak kontrolka jest rysowana.  
  
-   <xref:System.Drawing.Graphics> Obiekt - hermetyzuje kilka zorientowane na grafiki obiektów i metod, które udostępniają funkcje, które są niezbędne narysować swoją kontrolkę.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Drawing.Graphics> obiektu oraz sposób jej stosowania, patrz [jak: Tworzenie obiektów graficznych do rysowania](../advanced/how-to-create-graphics-objects-for-drawing.md).  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A> Zdarzenie jest wywoływane zawsze wtedy, gdy kontrolka jest rysowana lub odświeżane na ekranie i <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> obiekt reprezentuje prostokąt, w którym odbędzie się malowania. Jeśli kontrolka całego musi zostać odświeżona, <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> będzie reprezentować rozmiar całego formantu. Jeśli tylko część formantu musi zostać odświeżona, jednak <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> obiektu będzie reprezentować region, który ma być narysowany ponownie. Przykładem takiej sytuacji będzie, gdy formant został częściowo zasłonięte przez inny formant lub formularzy w interfejsie użytkownika.  
  
 Gdy dziedziczenie z <xref:System.Windows.Forms.Control> klasy, konieczne jest przesłonięcie <xref:System.Windows.Forms.Control.OnPaint%2A> metody i podać kod renderowania grafiki w ciągu. Jeśli chcesz podać niestandardowy interfejs graficzny umożliwiający kontrolkę użytkownika lub kontrolkę, która jest dziedziczone, możesz także to zrobić przez zastąpienie <xref:System.Windows.Forms.Control.OnPaint%2A> metody. Poniżej przedstawiono przykład:  
  
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
  
 Poprzedni przykład przedstawia sposób renderowania formantu za pomocą bardzo prosty graficzną reprezentację. Wywołuje <xref:System.Windows.Forms.Control.OnPaint%2A> metody klasy bazowej, tworzy <xref:System.Drawing.Pen> obiektu za pomocą którego do rysowania, a na koniec rysuje na wielokropek w prostokącie określona przez <xref:System.Windows.Forms.Control.Location%2A> i <xref:System.Windows.Forms.Control.Size%2A> formantu. Mimo że większość kodu renderowania będzie znacznie bardziej skomplikowane niż to, w tym przykładzie pokazano użycie <xref:System.Drawing.Graphics> obiektów znajdujących się w obrębie <xref:System.Windows.Forms.PaintEventArgs> obiektu. Należy pamiętać, że jeśli dziedziczą z klasy, która już zawiera graficzną reprezentację, takie jak <xref:System.Windows.Forms.UserControl> lub <xref:System.Windows.Forms.Button>i nie chcesz zintegrować tę reprezentację Twojego renderowanie, nie należy wywołać klasy bazowej <xref:System.Windows.Forms.Control.OnPaint%2A> Metoda.  
  
 Kod w <xref:System.Windows.Forms.Control.OnPaint%2A> metody kontroli nad będą wykonywane podczas pierwszych rysowania kontrolki i zawsze wtedy, gdy jest on odświeżany. Aby upewnić się, że formant jest odświeżana, za każdym razem, gdy zmiany jego rozmiaru, Dodaj następujący wiersz do konstruktora kontrolki:  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
>  Użyj <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> właściwości, aby zaimplementować formant prostokątny.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [Instrukcje: Tworzenie obiektów graficznych do rysowania](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [Kontrolki składników](constituent-controls.md)
- [Różne typy kontrolek niestandardowych](varieties-of-custom-controls.md)
