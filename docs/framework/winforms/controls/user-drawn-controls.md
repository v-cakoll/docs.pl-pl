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
# <a name="user-drawn-controls"></a><span data-ttu-id="0ed4b-102">Formanty rysowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="0ed4b-102">User-Drawn Controls</span></span>
<span data-ttu-id="0ed4b-103">.NET Framework zapewnia możliwość łatwego tworzenia własnych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="0ed4b-103">The .NET Framework provides you with the ability to easily develop your own controls.</span></span> <span data-ttu-id="0ed4b-104">Można utworzyć kontrolkę użytkownika, która jest zestawem standardowych kontrolek powiązanych ze sobą za pomocą kodu lub można zaprojektować własny formant od podstaw.</span><span class="sxs-lookup"><span data-stu-id="0ed4b-104">You can create a user control, which is a set of standard controls bound together by code, or you can design your own control from the ground up.</span></span> <span data-ttu-id="0ed4b-105">Można nawet użyć dziedziczenia, aby utworzyć kontrolkę, która dziedziczy z istniejącej kontrolki i dodaje do jej funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="0ed4b-105">You can even use inheritance to create a control that inherits from an existing control and add to its inherent functionality.</span></span> <span data-ttu-id="0ed4b-106">Niezależnie od tego, z jakich sposobów korzystasz, .NET Framework zapewnia funkcjonalność do rysowania niestandardowego interfejsu graficznego dla każdej tworzonego formantu.</span><span class="sxs-lookup"><span data-stu-id="0ed4b-106">Whatever approach you use, the .NET Framework provides the functionality to draw a custom graphical interface for any control you create.</span></span>  
  
 <span data-ttu-id="0ed4b-107">Malowanie kontrolki odbywa się przez wykonanie kodu w <xref:System.Windows.Forms.Control.OnPaint%2A> metodzie formantu.</span><span class="sxs-lookup"><span data-stu-id="0ed4b-107">Painting of a control is accomplished by the execution of code in the control's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="0ed4b-108">Pojedynczy argument <xref:System.Windows.Forms.Control.OnPaint%2A> metody <xref:System.Windows.Forms.PaintEventArgs> jest obiektem, który zawiera wszystkie informacje i funkcje wymagane do renderowania formantu.</span><span class="sxs-lookup"><span data-stu-id="0ed4b-108">The single argument of the <xref:System.Windows.Forms.Control.OnPaint%2A> method is a <xref:System.Windows.Forms.PaintEventArgs> object that provides all of the information and functionality required to render your control.</span></span> <span data-ttu-id="0ed4b-109"><xref:System.Windows.Forms.PaintEventArgs> Zapewnia jako właściwości dwa obiekty główne, które będą używane podczas renderowania kontrolki:</span><span class="sxs-lookup"><span data-stu-id="0ed4b-109">The <xref:System.Windows.Forms.PaintEventArgs> provides as properties two principal objects that will be used in the rendering of your control:</span></span>  
  
- <span data-ttu-id="0ed4b-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>Object — prostokąt, który reprezentuje część kontrolki, która zostanie narysowana.</span><span class="sxs-lookup"><span data-stu-id="0ed4b-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object - the rectangle that represents the part of the control that will be drawn.</span></span> <span data-ttu-id="0ed4b-111">Może to być cała kontrolka lub część kontrolki w zależności od sposobu rysowania kontrolki.</span><span class="sxs-lookup"><span data-stu-id="0ed4b-111">This can be the entire control, or part of the control depending on how the control is drawn.</span></span>  
  
- <span data-ttu-id="0ed4b-112"><xref:System.Drawing.Graphics>Object — hermetyzuje kilka obiektów i metod zorientowanych na grafiki, które zapewniają funkcje niezbędne do narysowania kontrolki.</span><span class="sxs-lookup"><span data-stu-id="0ed4b-112"><xref:System.Drawing.Graphics> object - encapsulates several graphics-oriented objects and methods that provide the functionality necessary to draw your control.</span></span>  
  
 <span data-ttu-id="0ed4b-113">Aby uzyskać więcej informacji na <xref:System.Drawing.Graphics> temat obiektu i sposobu jego użycia, zobacz [How to: Utwórz obiekty graficzne do rysowania](../advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="0ed4b-113">For more information on the <xref:System.Drawing.Graphics> object and how to use it, see [How to: Create Graphics Objects for Drawing](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
 <span data-ttu-id="0ed4b-114">Zdarzenie jest wyzwalane za każdym razem, gdy kontrolka jest rysowana lub odświeżana na <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> ekranie, a obiekt reprezentuje prostokąt, w którym nastąpi malowanie. <xref:System.Windows.Forms.Control.OnPaint%2A></span><span class="sxs-lookup"><span data-stu-id="0ed4b-114">The <xref:System.Windows.Forms.Control.OnPaint%2A> event is fired whenever the control is drawn or refreshed on the screen, and the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object represents the rectangle in which painting will take place.</span></span> <span data-ttu-id="0ed4b-115">Jeśli cała kontrolka musi zostać odświeżona, <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> będzie reprezentować rozmiar całej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="0ed4b-115">If the entire control needs to be refreshed, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> will represent the size of the entire control.</span></span> <span data-ttu-id="0ed4b-116">Jeśli jednak <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> tylko część kontrolki wymaga odświeżenia, obiekt będzie reprezentował tylko region, który musi zostać narysowany ponownie.</span><span class="sxs-lookup"><span data-stu-id="0ed4b-116">If only part of the control needs to be refreshed, however, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object will represent only the region that needs to be redrawn.</span></span> <span data-ttu-id="0ed4b-117">Przykładem takiego przypadku może być, gdy kontrolka została częściowo zasłonięta przez inny formant lub formularz w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0ed4b-117">An example of such a case would be when a control was partially obscured by another control or form in the user interface.</span></span>  
  
 <span data-ttu-id="0ed4b-118">W przypadku dziedziczenia z <xref:System.Windows.Forms.Control> klasy należy <xref:System.Windows.Forms.Control.OnPaint%2A> zastąpić metodę i udostępnić kod renderowania grafiki w obrębie.</span><span class="sxs-lookup"><span data-stu-id="0ed4b-118">When inheriting from the <xref:System.Windows.Forms.Control> class, you must override the <xref:System.Windows.Forms.Control.OnPaint%2A> method and provide graphics-rendering code within.</span></span> <span data-ttu-id="0ed4b-119">Jeśli chcesz dostarczyć niestandardowy interfejs graficzny do kontrolki użytkownika lub dziedziczonej kontrolki, możesz to zrobić, zastępując <xref:System.Windows.Forms.Control.OnPaint%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="0ed4b-119">If you want to provide a custom graphical interface to a user control or an inherited control, you can also do so by overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="0ed4b-120">Poniżej przedstawiono przykład:</span><span class="sxs-lookup"><span data-stu-id="0ed4b-120">An example is shown below:</span></span>  
  
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
  
 <span data-ttu-id="0ed4b-121">W poprzednim przykładzie pokazano, jak renderować formant z bardzo prostą reprezentacją graficzną.</span><span class="sxs-lookup"><span data-stu-id="0ed4b-121">The preceding example demonstrates how to render a control with a very simple graphical representation.</span></span> <span data-ttu-id="0ed4b-122">Wywołuje <xref:System.Windows.Forms.Control.OnPaint%2A> metodę klasy bazowej, <xref:System.Drawing.Pen> tworzy obiekt, z którym należy narysować, i na koniec Rysuje elipsę w prostokącie określonym przez <xref:System.Windows.Forms.Control.Location%2A> i <xref:System.Windows.Forms.Control.Size%2A> kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="0ed4b-122">It calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class, it creates a <xref:System.Drawing.Pen> object with which to draw, and finally draws an ellipse in the rectangle determined by the <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Size%2A> of the control.</span></span> <span data-ttu-id="0ed4b-123">Chociaż większość kodu renderowania będzie znacznie bardziej skomplikowana niż ta, ten przykład demonstruje użycie <xref:System.Drawing.Graphics> obiektu zawartego <xref:System.Windows.Forms.PaintEventArgs> w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="0ed4b-123">Although most rendering code will be significantly more complicated than this, this example demonstrates the use of the <xref:System.Drawing.Graphics> object contained within the <xref:System.Windows.Forms.PaintEventArgs> object.</span></span> <span data-ttu-id="0ed4b-124">Należy pamiętać, że jeśli dziedziczą z klasy, która ma już reprezentację graficzną, taką <xref:System.Windows.Forms.UserControl> jak <xref:System.Windows.Forms.Button>lub, i nie chcesz dołączać tej reprezentacji do renderowania, nie należy <xref:System.Windows.Forms.Control.OnPaint%2A> wywoływać klasy bazowej Method.</span><span class="sxs-lookup"><span data-stu-id="0ed4b-124">Note that if you are inheriting from a class that already has a graphical representation, such as <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Button>, and you do not wish to incorporate that representation into your rendering, you should not call your base class's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
 <span data-ttu-id="0ed4b-125">Kod w <xref:System.Windows.Forms.Control.OnPaint%2A> metodzie formantu będzie wykonywany, gdy kontrolka zostanie narysowana po raz pierwszy, i za każdym razem, gdy zostanie odświeżony.</span><span class="sxs-lookup"><span data-stu-id="0ed4b-125">The code in the <xref:System.Windows.Forms.Control.OnPaint%2A> method of your control will execute when the control is first drawn, and whenever it is refreshed.</span></span> <span data-ttu-id="0ed4b-126">Aby upewnić się, że formant jest ponownie rysowany przy każdej zmianie rozmiaru, Dodaj następujący wiersz do konstruktora formantu:</span><span class="sxs-lookup"><span data-stu-id="0ed4b-126">To ensure that your control is redrawn every time it is resized, add the following line to the constructor of your control:</span></span>  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
> <span data-ttu-id="0ed4b-127">Użyj właściwości <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> , aby zaimplementować kontrolkę nieprostokątną.</span><span class="sxs-lookup"><span data-stu-id="0ed4b-127">Use the <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> property to implement a non-rectangular control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ed4b-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ed4b-128">See also</span></span>

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [<span data-ttu-id="0ed4b-129">Instrukcje: Tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="0ed4b-129">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="0ed4b-130">Kontrolki składników</span><span class="sxs-lookup"><span data-stu-id="0ed4b-130">Constituent Controls</span></span>](constituent-controls.md)
- [<span data-ttu-id="0ed4b-131">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="0ed4b-131">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
