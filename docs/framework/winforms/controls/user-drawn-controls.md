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
# <a name="user-drawn-controls"></a><span data-ttu-id="08b54-102">Formanty rysowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="08b54-102">User-Drawn Controls</span></span>
<span data-ttu-id="08b54-103">.NET Framework zapewnia możliwość łatwego tworzenia własnych formantów.</span><span class="sxs-lookup"><span data-stu-id="08b54-103">The .NET Framework provides you with the ability to easily develop your own controls.</span></span> <span data-ttu-id="08b54-104">Można utworzyć formant użytkownika, który jest zestawem standardowych formantów połączonych ze sobą kodem lub można zaprojektować własny formant od podstaw.</span><span class="sxs-lookup"><span data-stu-id="08b54-104">You can create a user control, which is a set of standard controls bound together by code, or you can design your own control from the ground up.</span></span> <span data-ttu-id="08b54-105">Można nawet użyć dziedziczenia, aby utworzyć formant, który dziedziczy z istniejącego formantu i dodać do jego funkcji.</span><span class="sxs-lookup"><span data-stu-id="08b54-105">You can even use inheritance to create a control that inherits from an existing control and add to its inherent functionality.</span></span> <span data-ttu-id="08b54-106">Niezależnie od używanego podejścia program .NET Framework udostępnia funkcje rysowania niestandardowego interfejsu graficznego dla każdego utworzonego formantu.</span><span class="sxs-lookup"><span data-stu-id="08b54-106">Whatever approach you use, the .NET Framework provides the functionality to draw a custom graphical interface for any control you create.</span></span>  
  
 <span data-ttu-id="08b54-107">Malowanie formantu odbywa się przez wykonanie kodu <xref:System.Windows.Forms.Control.OnPaint%2A> w metodzie formantu.</span><span class="sxs-lookup"><span data-stu-id="08b54-107">Painting of a control is accomplished by the execution of code in the control's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="08b54-108">Pojedynczy argument <xref:System.Windows.Forms.Control.OnPaint%2A> metody jest <xref:System.Windows.Forms.PaintEventArgs> obiektem, który zawiera wszystkie informacje i funkcje wymagane do renderowania kontroli.</span><span class="sxs-lookup"><span data-stu-id="08b54-108">The single argument of the <xref:System.Windows.Forms.Control.OnPaint%2A> method is a <xref:System.Windows.Forms.PaintEventArgs> object that provides all of the information and functionality required to render your control.</span></span> <span data-ttu-id="08b54-109">Udostępnia <xref:System.Windows.Forms.PaintEventArgs> jako właściwości dwa główne obiekty, które będą używane w renderowaniu formantu:</span><span class="sxs-lookup"><span data-stu-id="08b54-109">The <xref:System.Windows.Forms.PaintEventArgs> provides as properties two principal objects that will be used in the rendering of your control:</span></span>  
  
- <span data-ttu-id="08b54-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>object - prostokąt reprezentujący część formantu, która zostanie narysowana.</span><span class="sxs-lookup"><span data-stu-id="08b54-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object - the rectangle that represents the part of the control that will be drawn.</span></span> <span data-ttu-id="08b54-111">Może to być cały formant lub część formantu w zależności od sposobu rysowania formantu.</span><span class="sxs-lookup"><span data-stu-id="08b54-111">This can be the entire control, or part of the control depending on how the control is drawn.</span></span>  
  
- <span data-ttu-id="08b54-112"><xref:System.Drawing.Graphics>object - hermetyzuje kilka obiektów zorientowanych na grafikę i metody, które zapewniają funkcjonalność niezbędną do narysowania formantu.</span><span class="sxs-lookup"><span data-stu-id="08b54-112"><xref:System.Drawing.Graphics> object - encapsulates several graphics-oriented objects and methods that provide the functionality necessary to draw your control.</span></span>  
  
 <span data-ttu-id="08b54-113">Aby uzyskać więcej <xref:System.Drawing.Graphics> informacji na temat obiektu i sposobu jego używania, zobacz [Jak: Tworzenie obiektów graficznych do rysowania](../advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="08b54-113">For more information on the <xref:System.Drawing.Graphics> object and how to use it, see [How to: Create Graphics Objects for Drawing](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
 <span data-ttu-id="08b54-114">Zdarzenie <xref:System.Windows.Forms.Control.OnPaint%2A> jest uruchamiane za każdym razem, gdy formant <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> jest rysowany lub odświeżany na ekranie, a obiekt reprezentuje prostokąt, w którym będzie odbywać się malowanie.</span><span class="sxs-lookup"><span data-stu-id="08b54-114">The <xref:System.Windows.Forms.Control.OnPaint%2A> event is fired whenever the control is drawn or refreshed on the screen, and the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object represents the rectangle in which painting will take place.</span></span> <span data-ttu-id="08b54-115">Jeśli cały formant musi zostać <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> odświeżony, będzie reprezentować rozmiar całego formantu.</span><span class="sxs-lookup"><span data-stu-id="08b54-115">If the entire control needs to be refreshed, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> will represent the size of the entire control.</span></span> <span data-ttu-id="08b54-116">Jeśli tylko część formantu musi zostać odświeżona, <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> obiekt będzie reprezentować tylko region, który musi zostać ponownie narysowany.</span><span class="sxs-lookup"><span data-stu-id="08b54-116">If only part of the control needs to be refreshed, however, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object will represent only the region that needs to be redrawn.</span></span> <span data-ttu-id="08b54-117">Przykładem takiego przypadku może być, gdy formant został częściowo zasłonięte przez inny formant lub formularz w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="08b54-117">An example of such a case would be when a control was partially obscured by another control or form in the user interface.</span></span>  
  
 <span data-ttu-id="08b54-118">Podczas dziedziczenia <xref:System.Windows.Forms.Control> z klasy, należy <xref:System.Windows.Forms.Control.OnPaint%2A> zastąpić metodę i podać kod renderowania grafiki w ramach.</span><span class="sxs-lookup"><span data-stu-id="08b54-118">When inheriting from the <xref:System.Windows.Forms.Control> class, you must override the <xref:System.Windows.Forms.Control.OnPaint%2A> method and provide graphics-rendering code within.</span></span> <span data-ttu-id="08b54-119">Jeśli chcesz zapewnić niestandardowy interfejs graficzny do formantu użytkownika lub formantu dziedziczonego, można również to zrobić, zastępując <xref:System.Windows.Forms.Control.OnPaint%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="08b54-119">If you want to provide a custom graphical interface to a user control or an inherited control, you can also do so by overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="08b54-120">Przykład przedstawiono poniżej:</span><span class="sxs-lookup"><span data-stu-id="08b54-120">An example is shown below:</span></span>  
  
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
  
 <span data-ttu-id="08b54-121">W poprzednim przykładzie pokazano, jak renderować formant z bardzo prostą reprezentacją graficzną.</span><span class="sxs-lookup"><span data-stu-id="08b54-121">The preceding example demonstrates how to render a control with a very simple graphical representation.</span></span> <span data-ttu-id="08b54-122">Wywołuje <xref:System.Windows.Forms.Control.OnPaint%2A> metodę klasy podstawowej, tworzy <xref:System.Drawing.Pen> obiekt, z którym można rysować, a na końcu rysuje elipsę w prostokącie określonym przez <xref:System.Windows.Forms.Control.Location%2A> i <xref:System.Windows.Forms.Control.Size%2A> formantu.</span><span class="sxs-lookup"><span data-stu-id="08b54-122">It calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class, it creates a <xref:System.Drawing.Pen> object with which to draw, and finally draws an ellipse in the rectangle determined by the <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Size%2A> of the control.</span></span> <span data-ttu-id="08b54-123">Chociaż większość kodu renderowania będzie znacznie bardziej skomplikowane niż to, <xref:System.Drawing.Graphics> w tym przykładzie pokazuje użycie obiektu znajdującego <xref:System.Windows.Forms.PaintEventArgs> się w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="08b54-123">Although most rendering code will be significantly more complicated than this, this example demonstrates the use of the <xref:System.Drawing.Graphics> object contained within the <xref:System.Windows.Forms.PaintEventArgs> object.</span></span> <span data-ttu-id="08b54-124">Należy zauważyć, że jeśli dziedziczenie z klasy, która ma <xref:System.Windows.Forms.UserControl> <xref:System.Windows.Forms.Button>już graficzne przedstawienie, takie jak lub , i nie chcesz włączyć tej <xref:System.Windows.Forms.Control.OnPaint%2A> reprezentacji do renderowania, nie należy wywoływać metody klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="08b54-124">Note that if you are inheriting from a class that already has a graphical representation, such as <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Button>, and you do not wish to incorporate that representation into your rendering, you should not call your base class's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
 <span data-ttu-id="08b54-125">Kod w <xref:System.Windows.Forms.Control.OnPaint%2A> metodzie formantu zostanie wykonany, gdy formant jest po raz pierwszy rysowany i gdy jest odświeżany.</span><span class="sxs-lookup"><span data-stu-id="08b54-125">The code in the <xref:System.Windows.Forms.Control.OnPaint%2A> method of your control will execute when the control is first drawn, and whenever it is refreshed.</span></span> <span data-ttu-id="08b54-126">Aby upewnić się, że formant jest ponownie rysowany za każdym razem, gdy jest zmieniany, dodaj następujący wiersz do konstruktora formantu:</span><span class="sxs-lookup"><span data-stu-id="08b54-126">To ensure that your control is redrawn every time it is resized, add the following line to the constructor of your control:</span></span>  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
> <span data-ttu-id="08b54-127">Użyj <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> właściwości, aby zaimplementować formant nie prostokątny.</span><span class="sxs-lookup"><span data-stu-id="08b54-127">Use the <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> property to implement a non-rectangular control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08b54-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08b54-128">See also</span></span>

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [<span data-ttu-id="08b54-129">Instrukcje: tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="08b54-129">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="08b54-130">Formanty składników</span><span class="sxs-lookup"><span data-stu-id="08b54-130">Constituent Controls</span></span>](constituent-controls.md)
- [<span data-ttu-id="08b54-131">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="08b54-131">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
