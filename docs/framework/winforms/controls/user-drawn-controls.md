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
ms.openlocfilehash: 26b4f062c120bf543a5e597fc8c734e8cc336bd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="user-drawn-controls"></a><span data-ttu-id="75aa0-102">Formanty rysowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="75aa0-102">User-Drawn Controls</span></span>
<span data-ttu-id="75aa0-103">.NET Framework umożliwia łatwy sposób tworzyć własne kontrolki.</span><span class="sxs-lookup"><span data-stu-id="75aa0-103">The .NET Framework provides you with the ability to easily develop your own controls.</span></span> <span data-ttu-id="75aa0-104">Formant użytkownika, który jest zestaw standardowych formantów powiązane przez kod, można utworzyć lub zapasową można projektować formantu od podstaw.</span><span class="sxs-lookup"><span data-stu-id="75aa0-104">You can create a user control, which is a set of standard controls bound together by code, or you can design your own control from the ground up.</span></span> <span data-ttu-id="75aa0-105">Dziedziczenie umożliwia nawet utworzyć formant, który dziedziczy z istniejącego formantu i dodać do jego działanie związane.</span><span class="sxs-lookup"><span data-stu-id="75aa0-105">You can even use inheritance to create a control that inherits from an existing control and add to its inherent functionality.</span></span> <span data-ttu-id="75aa0-106">Niezależnie od podejście, możesz użyć programu .NET Framework udostępnia funkcje umożliwiające rysowanie niestandardowego interfejsu graficznego dla każdego formantu, którą utworzysz.</span><span class="sxs-lookup"><span data-stu-id="75aa0-106">Whatever approach you use, the .NET Framework provides the functionality to draw a custom graphical interface for any control you create.</span></span>  
  
 <span data-ttu-id="75aa0-107">Malowanie formantu odbywa się za wykonywanie kodu w formancie <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="75aa0-107">Painting of a control is accomplished by the execution of code in the control's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="75aa0-108">Pojedynczy argument <xref:System.Windows.Forms.Control.OnPaint%2A> jest metoda <xref:System.Windows.Forms.PaintEventArgs> obiekt, który zawiera wszystkie informacje i funkcje wymagane do renderowania formantu.</span><span class="sxs-lookup"><span data-stu-id="75aa0-108">The single argument of the <xref:System.Windows.Forms.Control.OnPaint%2A> method is a <xref:System.Windows.Forms.PaintEventArgs> object that provides all of the information and functionality required to render your control.</span></span> <span data-ttu-id="75aa0-109"><xref:System.Windows.Forms.PaintEventArgs> Zapewnia jako właściwości dwa obiekty główne, które będą używane podczas renderowania formantu:</span><span class="sxs-lookup"><span data-stu-id="75aa0-109">The <xref:System.Windows.Forms.PaintEventArgs> provides as properties two principal objects that will be used in the rendering of your control:</span></span>  
  
-   <span data-ttu-id="75aa0-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> Obiekt - przedstawiającą formant, który będzie rysowany prostokąta.</span><span class="sxs-lookup"><span data-stu-id="75aa0-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object - the rectangle that represents the part of the control that will be drawn.</span></span> <span data-ttu-id="75aa0-111">Może to być całą formant lub część formantu w zależności od tego, jak kontrolka jest rysowane.</span><span class="sxs-lookup"><span data-stu-id="75aa0-111">This can be the entire control, or part of the control depending on how the control is drawn.</span></span>  
  
-   <span data-ttu-id="75aa0-112"><xref:System.Drawing.Graphics> Obiekt - hermetyzuje kilka zorientowane na grafiki obiekty i metody udostępniające funkcje niezbędne do rysowania formantu.</span><span class="sxs-lookup"><span data-stu-id="75aa0-112"><xref:System.Drawing.Graphics> object - encapsulates several graphics-oriented objects and methods that provide the functionality necessary to draw your control.</span></span>  
  
 <span data-ttu-id="75aa0-113">Aby uzyskać więcej informacji na temat <xref:System.Drawing.Graphics> obiektu i sposobu jego używania, zobacz [porady: Tworzenie obiektów graficznych do rysowania](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="75aa0-113">For more information on the <xref:System.Drawing.Graphics> object and how to use it, see [How to: Create Graphics Objects for Drawing](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
 <span data-ttu-id="75aa0-114"><xref:System.Windows.Forms.Control.OnPaint%2A> Zdarzenie jest wywoływane zawsze, gdy formant jest rysowany lub odświeżenie na ekranie i <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> obiekt reprezentuje prostokąt, w którym odbędzie się malowania.</span><span class="sxs-lookup"><span data-stu-id="75aa0-114">The <xref:System.Windows.Forms.Control.OnPaint%2A> event is fired whenever the control is drawn or refreshed on the screen, and the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object represents the rectangle in which painting will take place.</span></span> <span data-ttu-id="75aa0-115">Jeśli cały formant wymaga odświeżenia, <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> reprezentuje rozmiar całego formantu.</span><span class="sxs-lookup"><span data-stu-id="75aa0-115">If the entire control needs to be refreshed, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> will represent the size of the entire control.</span></span> <span data-ttu-id="75aa0-116">Jeśli tylko część formant wymaga odświeżenia, jednak <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> obiekt reprezentuje region, który musi zostać narysowany ponownie.</span><span class="sxs-lookup"><span data-stu-id="75aa0-116">If only part of the control needs to be refreshed, however, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object will represent only the region that needs to be redrawn.</span></span> <span data-ttu-id="75aa0-117">Przykładem takiego przypadku może dochodzić do formantu został częściowo zasłonięty przez inny formant lub formularza w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="75aa0-117">An example of such a case would be when a control was partially obscured by another control or form in the user interface.</span></span>  
  
 <span data-ttu-id="75aa0-118">Podczas dziedziczenia z <xref:System.Windows.Forms.Control> klasy, należy zastąpić <xref:System.Windows.Forms.Control.OnPaint%2A> — metoda i podaj kod renderowania grafiki w.</span><span class="sxs-lookup"><span data-stu-id="75aa0-118">When inheriting from the <xref:System.Windows.Forms.Control> class, you must override the <xref:System.Windows.Forms.Control.OnPaint%2A> method and provide graphics-rendering code within.</span></span> <span data-ttu-id="75aa0-119">Jeśli chcesz podać niestandardowy interfejs graficzny kontrolkę użytkownika lub formant dziedziczony, możesz też to zrobić przez zastąpienie <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="75aa0-119">If you want to provide a custom graphical interface to a user control or an inherited control, you can also do so by overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="75aa0-120">Poniżej przedstawiono przykład:</span><span class="sxs-lookup"><span data-stu-id="75aa0-120">An example is shown below:</span></span>  
  
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
  
 <span data-ttu-id="75aa0-121">Poprzednim przykładzie pokazano sposób renderowania formantu o bardzo proste graficzną reprezentację.</span><span class="sxs-lookup"><span data-stu-id="75aa0-121">The preceding example demonstrates how to render a control with a very simple graphical representation.</span></span> <span data-ttu-id="75aa0-122">Wywołuje <xref:System.Windows.Forms.Control.OnPaint%2A> metody klasy podstawowej, tworzy <xref:System.Drawing.Pen> obiekt z do rysowania, a na koniec rysuje jako elipsy w prostokącie określona przez <xref:System.Windows.Forms.Control.Location%2A> i <xref:System.Windows.Forms.Control.Size%2A> formantu.</span><span class="sxs-lookup"><span data-stu-id="75aa0-122">It calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class, it creates a <xref:System.Drawing.Pen> object with which to draw, and finally draws an ellipse in the rectangle determined by the <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Size%2A> of the control.</span></span> <span data-ttu-id="75aa0-123">Mimo że większość renderowania kodu będzie znacznie bardziej skomplikowane niż ta, przykładzie przedstawiono użycie <xref:System.Drawing.Graphics> zawartych w obiekcie <xref:System.Windows.Forms.PaintEventArgs> obiektu.</span><span class="sxs-lookup"><span data-stu-id="75aa0-123">Although most rendering code will be significantly more complicated than this, this example demonstrates the use of the <xref:System.Drawing.Graphics> object contained within the <xref:System.Windows.Forms.PaintEventArgs> object.</span></span> <span data-ttu-id="75aa0-124">Należy pamiętać, że jeśli są dziedziczy z klasy, która ma już graficzną reprezentację, takich jak <xref:System.Windows.Forms.UserControl> lub <xref:System.Windows.Forms.Button>i nie chcesz, aby zastosować tego reprezentacja w Twojej renderowanie, nie należy wywoływać klasy podstawowej <xref:System.Windows.Forms.Control.OnPaint%2A> Metoda.</span><span class="sxs-lookup"><span data-stu-id="75aa0-124">Note that if you are inheriting from a class that already has a graphical representation, such as <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Button>, and you do not wish to incorporate that representation into your rendering, you should not call your base class's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
 <span data-ttu-id="75aa0-125">Kod w <xref:System.Windows.Forms.Control.OnPaint%2A> metody formantu wykona narysować kontrolki jest najpierw, a w każdym przypadku, gdy jego odświeżanie.</span><span class="sxs-lookup"><span data-stu-id="75aa0-125">The code in the <xref:System.Windows.Forms.Control.OnPaint%2A> method of your control will execute when the control is first drawn, and whenever it is refreshed.</span></span> <span data-ttu-id="75aa0-126">Aby upewnić się, że formant jest odświeżana za każdym razem, gdy zostanie zmieniony rozmiar, Dodaj następujący wiersz do konstruktora formantu:</span><span class="sxs-lookup"><span data-stu-id="75aa0-126">To ensure that your control is redrawn every time it is resized, add the following line to the constructor of your control:</span></span>  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
>  <span data-ttu-id="75aa0-127">Użyj <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> właściwości do zaimplementowania nieregularnych formantu.</span><span class="sxs-lookup"><span data-stu-id="75aa0-127">Use the <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> property to implement a non-rectangular control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75aa0-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="75aa0-128">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Region%2A>  
 <xref:System.Windows.Forms.ControlStyles>  
 <xref:System.Drawing.Graphics>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <xref:System.Windows.Forms.PaintEventArgs>  
 [<span data-ttu-id="75aa0-129">Instrukcje: tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="75aa0-129">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="75aa0-130">Kontrolki składników</span><span class="sxs-lookup"><span data-stu-id="75aa0-130">Constituent Controls</span></span>](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 [<span data-ttu-id="75aa0-131">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="75aa0-131">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
