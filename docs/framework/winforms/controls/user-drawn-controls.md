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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947956"
---
# <a name="user-drawn-controls"></a><span data-ttu-id="c60c4-102">Formanty rysowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="c60c4-102">User-Drawn Controls</span></span>
<span data-ttu-id="c60c4-103">.NET Framework umożliwia łatwe tworzenie własnych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="c60c4-103">The .NET Framework provides you with the ability to easily develop your own controls.</span></span> <span data-ttu-id="c60c4-104">Można utworzyć kontrolkę użytkownika, który jest zestaw standardowych kontrolek powiązane przez kod, lub można zaprojektować kontrolki od podstaw w górę.</span><span class="sxs-lookup"><span data-stu-id="c60c4-104">You can create a user control, which is a set of standard controls bound together by code, or you can design your own control from the ground up.</span></span> <span data-ttu-id="c60c4-105">Dziedziczenie umożliwia nawet utworzyć formant, który dziedziczy istniejący formant i dodać do jej nieodłączne funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="c60c4-105">You can even use inheritance to create a control that inherits from an existing control and add to its inherent functionality.</span></span> <span data-ttu-id="c60c4-106">Niezależnie od podejścia, możesz użyć programu .NET Framework zapewnia funkcje do rysowania niestandardowy interfejs graficzny dla dowolnego formantu, który tworzysz.</span><span class="sxs-lookup"><span data-stu-id="c60c4-106">Whatever approach you use, the .NET Framework provides the functionality to draw a custom graphical interface for any control you create.</span></span>  
  
 <span data-ttu-id="c60c4-107">Malowanie kontrolki odbywa się przez wykonywanie kodu w formancie <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c60c4-107">Painting of a control is accomplished by the execution of code in the control's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="c60c4-108">Pojedynczy argument <xref:System.Windows.Forms.Control.OnPaint%2A> metodą jest <xref:System.Windows.Forms.PaintEventArgs> obiektu, który zawiera wszystkie informacje i funkcje wymagane do renderowania kontrolki.</span><span class="sxs-lookup"><span data-stu-id="c60c4-108">The single argument of the <xref:System.Windows.Forms.Control.OnPaint%2A> method is a <xref:System.Windows.Forms.PaintEventArgs> object that provides all of the information and functionality required to render your control.</span></span> <span data-ttu-id="c60c4-109"><xref:System.Windows.Forms.PaintEventArgs> Zapewnia jako właściwości dwa obiekty jednostki, które będą używane w czasie renderowania kontrolki:</span><span class="sxs-lookup"><span data-stu-id="c60c4-109">The <xref:System.Windows.Forms.PaintEventArgs> provides as properties two principal objects that will be used in the rendering of your control:</span></span>  
  
- <span data-ttu-id="c60c4-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> Obiekt - prostokąt, który reprezentuje część kontrolki, z którego będą pobierane.</span><span class="sxs-lookup"><span data-stu-id="c60c4-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object - the rectangle that represents the part of the control that will be drawn.</span></span> <span data-ttu-id="c60c4-111">Może to być całą formantu lub część formantu w zależności od tego, jak kontrolka jest rysowana.</span><span class="sxs-lookup"><span data-stu-id="c60c4-111">This can be the entire control, or part of the control depending on how the control is drawn.</span></span>  
  
- <span data-ttu-id="c60c4-112"><xref:System.Drawing.Graphics> Obiekt - hermetyzuje kilka zorientowane na grafiki obiektów i metod, które udostępniają funkcje, które są niezbędne narysować swoją kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="c60c4-112"><xref:System.Drawing.Graphics> object - encapsulates several graphics-oriented objects and methods that provide the functionality necessary to draw your control.</span></span>  
  
 <span data-ttu-id="c60c4-113">Aby uzyskać więcej informacji na temat <xref:System.Drawing.Graphics> obiektu oraz sposób jej stosowania, patrz [jak: Tworzenie obiektów graficznych do rysowania](../advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="c60c4-113">For more information on the <xref:System.Drawing.Graphics> object and how to use it, see [How to: Create Graphics Objects for Drawing](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
 <span data-ttu-id="c60c4-114"><xref:System.Windows.Forms.Control.OnPaint%2A> Zdarzenie jest wywoływane zawsze wtedy, gdy kontrolka jest rysowana lub odświeżane na ekranie i <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> obiekt reprezentuje prostokąt, w którym odbędzie się malowania.</span><span class="sxs-lookup"><span data-stu-id="c60c4-114">The <xref:System.Windows.Forms.Control.OnPaint%2A> event is fired whenever the control is drawn or refreshed on the screen, and the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object represents the rectangle in which painting will take place.</span></span> <span data-ttu-id="c60c4-115">Jeśli kontrolka całego musi zostać odświeżona, <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> będzie reprezentować rozmiar całego formantu.</span><span class="sxs-lookup"><span data-stu-id="c60c4-115">If the entire control needs to be refreshed, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> will represent the size of the entire control.</span></span> <span data-ttu-id="c60c4-116">Jeśli tylko część formantu musi zostać odświeżona, jednak <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> obiektu będzie reprezentować region, który ma być narysowany ponownie.</span><span class="sxs-lookup"><span data-stu-id="c60c4-116">If only part of the control needs to be refreshed, however, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object will represent only the region that needs to be redrawn.</span></span> <span data-ttu-id="c60c4-117">Przykładem takiej sytuacji będzie, gdy formant został częściowo zasłonięte przez inny formant lub formularzy w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c60c4-117">An example of such a case would be when a control was partially obscured by another control or form in the user interface.</span></span>  
  
 <span data-ttu-id="c60c4-118">Gdy dziedziczenie z <xref:System.Windows.Forms.Control> klasy, konieczne jest przesłonięcie <xref:System.Windows.Forms.Control.OnPaint%2A> metody i podać kod renderowania grafiki w ciągu.</span><span class="sxs-lookup"><span data-stu-id="c60c4-118">When inheriting from the <xref:System.Windows.Forms.Control> class, you must override the <xref:System.Windows.Forms.Control.OnPaint%2A> method and provide graphics-rendering code within.</span></span> <span data-ttu-id="c60c4-119">Jeśli chcesz podać niestandardowy interfejs graficzny umożliwiający kontrolkę użytkownika lub kontrolkę, która jest dziedziczone, możesz także to zrobić przez zastąpienie <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c60c4-119">If you want to provide a custom graphical interface to a user control or an inherited control, you can also do so by overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="c60c4-120">Poniżej przedstawiono przykład:</span><span class="sxs-lookup"><span data-stu-id="c60c4-120">An example is shown below:</span></span>  
  
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
  
 <span data-ttu-id="c60c4-121">Poprzedni przykład przedstawia sposób renderowania formantu za pomocą bardzo prosty graficzną reprezentację.</span><span class="sxs-lookup"><span data-stu-id="c60c4-121">The preceding example demonstrates how to render a control with a very simple graphical representation.</span></span> <span data-ttu-id="c60c4-122">Wywołuje <xref:System.Windows.Forms.Control.OnPaint%2A> metody klasy bazowej, tworzy <xref:System.Drawing.Pen> obiektu za pomocą którego do rysowania, a na koniec rysuje na wielokropek w prostokącie określona przez <xref:System.Windows.Forms.Control.Location%2A> i <xref:System.Windows.Forms.Control.Size%2A> formantu.</span><span class="sxs-lookup"><span data-stu-id="c60c4-122">It calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class, it creates a <xref:System.Drawing.Pen> object with which to draw, and finally draws an ellipse in the rectangle determined by the <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Size%2A> of the control.</span></span> <span data-ttu-id="c60c4-123">Mimo że większość kodu renderowania będzie znacznie bardziej skomplikowane niż to, w tym przykładzie pokazano użycie <xref:System.Drawing.Graphics> obiektów znajdujących się w obrębie <xref:System.Windows.Forms.PaintEventArgs> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c60c4-123">Although most rendering code will be significantly more complicated than this, this example demonstrates the use of the <xref:System.Drawing.Graphics> object contained within the <xref:System.Windows.Forms.PaintEventArgs> object.</span></span> <span data-ttu-id="c60c4-124">Należy pamiętać, że jeśli dziedziczą z klasy, która już zawiera graficzną reprezentację, takie jak <xref:System.Windows.Forms.UserControl> lub <xref:System.Windows.Forms.Button>i nie chcesz zintegrować tę reprezentację Twojego renderowanie, nie należy wywołać klasy bazowej <xref:System.Windows.Forms.Control.OnPaint%2A> Metoda.</span><span class="sxs-lookup"><span data-stu-id="c60c4-124">Note that if you are inheriting from a class that already has a graphical representation, such as <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Button>, and you do not wish to incorporate that representation into your rendering, you should not call your base class's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
 <span data-ttu-id="c60c4-125">Kod w <xref:System.Windows.Forms.Control.OnPaint%2A> metody kontroli nad będą wykonywane podczas pierwszych rysowania kontrolki i zawsze wtedy, gdy jest on odświeżany.</span><span class="sxs-lookup"><span data-stu-id="c60c4-125">The code in the <xref:System.Windows.Forms.Control.OnPaint%2A> method of your control will execute when the control is first drawn, and whenever it is refreshed.</span></span> <span data-ttu-id="c60c4-126">Aby upewnić się, że formant jest odświeżana, za każdym razem, gdy zmiany jego rozmiaru, Dodaj następujący wiersz do konstruktora kontrolki:</span><span class="sxs-lookup"><span data-stu-id="c60c4-126">To ensure that your control is redrawn every time it is resized, add the following line to the constructor of your control:</span></span>  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
>  <span data-ttu-id="c60c4-127">Użyj <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> właściwości, aby zaimplementować formant prostokątny.</span><span class="sxs-lookup"><span data-stu-id="c60c4-127">Use the <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> property to implement a non-rectangular control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c60c4-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c60c4-128">See also</span></span>

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [<span data-ttu-id="c60c4-129">Instrukcje: Tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="c60c4-129">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="c60c4-130">Kontrolki składników</span><span class="sxs-lookup"><span data-stu-id="c60c4-130">Constituent Controls</span></span>](constituent-controls.md)
- [<span data-ttu-id="c60c4-131">Różne typy kontrolek niestandardowych</span><span class="sxs-lookup"><span data-stu-id="c60c4-131">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
