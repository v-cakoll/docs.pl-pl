---
title: "Formanty rysowane przez użytkownika"
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
- custom controls [Windows Forms], user-drawn
- OnPaint method [Windows Forms]
- user-drawn controls [Windows Forms]
ms.assetid: 034af4b5-457f-4160-a937-22891817faa8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 42f208d10b1c111f98af3c803148590466baddf0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="user-drawn-controls"></a>Formanty rysowane przez użytkownika
.NET Framework umożliwia łatwy sposób tworzyć własne kontrolki. Formant użytkownika, który jest zestaw standardowych formantów powiązane przez kod, można utworzyć lub zapasową można projektować formantu od podstaw. Dziedziczenie umożliwia nawet utworzyć formant, który dziedziczy z istniejącego formantu i dodać do jego działanie związane. Niezależnie od podejście, możesz użyć programu .NET Framework udostępnia funkcje umożliwiające rysowanie niestandardowego interfejsu graficznego dla każdego formantu, którą utworzysz.  
  
 Malowanie formantu odbywa się za wykonywanie kodu w formancie <xref:System.Windows.Forms.Control.OnPaint%2A> metody. Pojedynczy argument <xref:System.Windows.Forms.Control.OnPaint%2A> jest metoda <xref:System.Windows.Forms.PaintEventArgs> obiekt, który zawiera wszystkie informacje i funkcje wymagane do renderowania formantu. <xref:System.Windows.Forms.PaintEventArgs> Zapewnia jako właściwości dwa obiekty główne, które będą używane podczas renderowania formantu:  
  
-   <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>Obiekt - przedstawiającą formant, który będzie rysowany prostokąta. Może to być całą formant lub część formantu w zależności od tego, jak kontrolka jest rysowane.  
  
-   <xref:System.Drawing.Graphics>Obiekt - hermetyzuje kilka zorientowane na grafiki obiekty i metody udostępniające funkcje niezbędne do rysowania formantu.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Drawing.Graphics> obiektu i sposobu jego używania, zobacz [porady: Tworzenie obiektów graficznych do rysowania](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A> Zdarzenie jest wywoływane zawsze, gdy formant jest rysowany lub odświeżenie na ekranie i <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> obiekt reprezentuje prostokąt, w którym odbędzie się malowania. Jeśli cały formant wymaga odświeżenia, <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> reprezentuje rozmiar całego formantu. Jeśli tylko część formant wymaga odświeżenia, jednak <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> obiekt reprezentuje region, który musi zostać narysowany ponownie. Przykładem takiego przypadku może dochodzić do formantu został częściowo zasłonięty przez inny formant lub formularza w interfejsie użytkownika.  
  
 Podczas dziedziczenia z <xref:System.Windows.Forms.Control> klasy, należy zastąpić <xref:System.Windows.Forms.Control.OnPaint%2A> — metoda i podaj kod renderowania grafiki w. Jeśli chcesz podać niestandardowy interfejs graficzny kontrolkę użytkownika lub formant dziedziczony, możesz też to zrobić przez zastąpienie <xref:System.Windows.Forms.Control.OnPaint%2A> metody. Poniżej przedstawiono przykład:  
  
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
  
 Poprzednim przykładzie pokazano sposób renderowania formantu o bardzo proste graficzną reprezentację. Wywołuje <xref:System.Windows.Forms.Control.OnPaint%2A> metody klasy podstawowej, tworzy <xref:System.Drawing.Pen> obiekt z do rysowania, a na koniec rysuje jako elipsy w prostokącie określona przez <xref:System.Windows.Forms.Control.Location%2A> i <xref:System.Windows.Forms.Control.Size%2A> formantu. Mimo że większość renderowania kodu będzie znacznie bardziej skomplikowane niż ta, przykładzie przedstawiono użycie <xref:System.Drawing.Graphics> zawartych w obiekcie <xref:System.Windows.Forms.PaintEventArgs> obiektu. Należy pamiętać, że jeśli są dziedziczy z klasy, która ma już graficzną reprezentację, takich jak <xref:System.Windows.Forms.UserControl> lub <xref:System.Windows.Forms.Button>i nie chcesz, aby zastosować tego reprezentacja w Twojej renderowanie, nie należy wywoływać klasy podstawowej <xref:System.Windows.Forms.Control.OnPaint%2A> Metoda.  
  
 Kod w <xref:System.Windows.Forms.Control.OnPaint%2A> metody formantu wykona narysować kontrolki jest najpierw, a w każdym przypadku, gdy jego odświeżanie. Aby upewnić się, że formant jest odświeżana za każdym razem, gdy zostanie zmieniony rozmiar, Dodaj następujący wiersz do konstruktora formantu:  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
>  Użyj <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> właściwości do zaimplementowania nieregularnych formantu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Control.Region%2A>  
 <xref:System.Windows.Forms.ControlStyles>  
 <xref:System.Drawing.Graphics>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <xref:System.Windows.Forms.PaintEventArgs>  
 [Porady: Tworzenie obiektów graficznych do rysowania](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Formanty składników](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 [Różne typy formantów niestandardowych](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
