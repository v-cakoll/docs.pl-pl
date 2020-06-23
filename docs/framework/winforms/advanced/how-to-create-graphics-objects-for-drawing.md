---
title: 'Porady: tworzenie obiektów graficznych do rysowania'
description: Zapoznaj się teraz, aby utworzyć obiekt graficzny, który jest potrzebny do rysowania linii i kształtów, renderowania tekstu lub wyświetlania obrazów i manipulowania nimi przy użyciu interfejsu GDI+.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], creating
- images [Windows Forms], creating
- GDI+, creating images
ms.assetid: 162861f9-f050-445e-8abb-b2c43a918b8b
ms.openlocfilehash: 1a0884c1e9956dc6f4608e32372deeea24ef4670
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903210"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a><span data-ttu-id="17212-103">Porady: tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="17212-103">How to: Create Graphics Objects for Drawing</span></span>
<span data-ttu-id="17212-104">Aby można było rysować linie i kształty, renderować tekst lub wyświetlać i manipulować obrazami za pomocą interfejsu GDI+, należy utworzyć <xref:System.Drawing.Graphics> obiekt.</span><span class="sxs-lookup"><span data-stu-id="17212-104">Before you can draw lines and shapes, render text, or display and manipulate images with GDI+, you need to create a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="17212-105"><xref:System.Drawing.Graphics>Obiekt reprezentuje powierzchnię rysowania GDI+ i jest obiektem, który jest używany do tworzenia obrazów graficznych.</span><span class="sxs-lookup"><span data-stu-id="17212-105">The <xref:System.Drawing.Graphics> object represents a GDI+ drawing surface, and is the object that is used to create graphical images.</span></span>  
  
 <span data-ttu-id="17212-106">Istnieją dwa kroki pracy z grafiką:</span><span class="sxs-lookup"><span data-stu-id="17212-106">There are two steps in working with graphics:</span></span>  
  
1. <span data-ttu-id="17212-107">Tworzenie <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="17212-107">Creating a <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="17212-108">Używanie <xref:System.Drawing.Graphics> obiektu do rysowania linii i kształtów, renderowania tekstu lub wyświetlania obrazów i manipulowania nimi.</span><span class="sxs-lookup"><span data-stu-id="17212-108">Using the <xref:System.Drawing.Graphics> object to draw lines and shapes, render text, or display and manipulate images.</span></span>  
  
## <a name="creating-a-graphics-object"></a><span data-ttu-id="17212-109">Tworzenie obiektu graficznego</span><span class="sxs-lookup"><span data-stu-id="17212-109">Creating a Graphics Object</span></span>  
 <span data-ttu-id="17212-110">Obiekt grafiki można utworzyć na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="17212-110">A graphics object can be created in a variety of ways.</span></span>  
  
#### <a name="to-create-a-graphics-object"></a><span data-ttu-id="17212-111">Aby utworzyć obiekt grafiki</span><span class="sxs-lookup"><span data-stu-id="17212-111">To create a graphics object</span></span>  
  
- <span data-ttu-id="17212-112">Odbierz odwołanie do obiektu grafiki <xref:System.Windows.Forms.PaintEventArgs> w ramach <xref:System.Windows.Forms.Control.Paint> zdarzenia formularza lub kontrolki.</span><span class="sxs-lookup"><span data-stu-id="17212-112">Receive a reference to a graphics object as part of the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event of a form or control.</span></span> <span data-ttu-id="17212-113">Jest to zazwyczaj sposób uzyskiwania odwołania do obiektu grafiki podczas tworzenia kodu rysowania dla kontrolki.</span><span class="sxs-lookup"><span data-stu-id="17212-113">This is usually how you obtain a reference to a graphics object when creating painting code for a control.</span></span> <span data-ttu-id="17212-114">Podobnie, można również uzyskać obiekt grafiki jako właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> podczas obsługi <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenia dla elementu <xref:System.Drawing.Printing.PrintDocument> .</span><span class="sxs-lookup"><span data-stu-id="17212-114">Similarly, you can also obtain a graphics object as a property of the <xref:System.Drawing.Printing.PrintPageEventArgs> when handling the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event for a <xref:System.Drawing.Printing.PrintDocument>.</span></span>  
  
     <span data-ttu-id="17212-115">-lub-</span><span class="sxs-lookup"><span data-stu-id="17212-115">-or-</span></span>  
  
- <span data-ttu-id="17212-116">Wywołaj <xref:System.Windows.Forms.Control.CreateGraphics%2A> metodę kontrolki lub formularza, aby uzyskać odwołanie do <xref:System.Drawing.Graphics> obiektu, który reprezentuje powierzchnię rysowania tego formantu lub formularza.</span><span class="sxs-lookup"><span data-stu-id="17212-116">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span> <span data-ttu-id="17212-117">Użyj tej metody, jeśli chcesz rysować na formularzu lub kontrolce, która już istnieje.</span><span class="sxs-lookup"><span data-stu-id="17212-117">Use this method if you want to draw on a form or control that already exists.</span></span>  
  
     <span data-ttu-id="17212-118">-lub-</span><span class="sxs-lookup"><span data-stu-id="17212-118">-or-</span></span>  
  
- <span data-ttu-id="17212-119">Utwórz <xref:System.Drawing.Graphics> obiekt z dowolnego obiektu, który dziedziczy z <xref:System.Drawing.Image> .</span><span class="sxs-lookup"><span data-stu-id="17212-119">Create a <xref:System.Drawing.Graphics> object from any object that inherits from <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="17212-120">Takie podejście jest przydatne, gdy chcesz zmienić już istniejący obraz.</span><span class="sxs-lookup"><span data-stu-id="17212-120">This approach is useful when you want to alter an already existing image.</span></span>  
  
     <span data-ttu-id="17212-121">Poniższe sekcje zawierają szczegółowe informacje o każdym z tych procesów.</span><span class="sxs-lookup"><span data-stu-id="17212-121">The following sections give details about each of these processes.</span></span>  
  
## <a name="painteventargs-in-the-paint-event-handler"></a><span data-ttu-id="17212-122">PaintEventArgs w programie obsługi zdarzeń programu Paint</span><span class="sxs-lookup"><span data-stu-id="17212-122">PaintEventArgs in the Paint Event Handler</span></span>  
 <span data-ttu-id="17212-123">Gdy programowanie <xref:System.Windows.Forms.PaintEventHandler> dla kontrolek lub <xref:System.Drawing.Printing.PrintDocument.PrintPage> dla obiektu a <xref:System.Drawing.Printing.PrintDocument> , obiekt grafiki jest udostępniany jako jedna z właściwości <xref:System.Windows.Forms.PaintEventArgs> lub <xref:System.Drawing.Printing.PrintPageEventArgs> .</span><span class="sxs-lookup"><span data-stu-id="17212-123">When programming the <xref:System.Windows.Forms.PaintEventHandler> for controls or the <xref:System.Drawing.Printing.PrintDocument.PrintPage> for a <xref:System.Drawing.Printing.PrintDocument>, a graphics object is provided as one of the properties of <xref:System.Windows.Forms.PaintEventArgs> or <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a><span data-ttu-id="17212-124">Aby uzyskać odwołanie do obiektu grafiki z PaintEventArgs w zdarzeniu Paint</span><span class="sxs-lookup"><span data-stu-id="17212-124">To obtain a reference to a Graphics object from the PaintEventArgs in the Paint event</span></span>  
  
1. <span data-ttu-id="17212-125">Zadeklaruj <xref:System.Drawing.Graphics> obiekt.</span><span class="sxs-lookup"><span data-stu-id="17212-125">Declare the <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="17212-126">Przypisz zmienną, aby odwołać się do <xref:System.Drawing.Graphics> obiektu przesyłanego jako część elementu <xref:System.Windows.Forms.PaintEventArgs> .</span><span class="sxs-lookup"><span data-stu-id="17212-126">Assign the variable to refer to the <xref:System.Drawing.Graphics> object passed as part of the <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
3. <span data-ttu-id="17212-127">Wstaw kod, aby malować formularz lub kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="17212-127">Insert code to paint the form or control.</span></span>  
  
     <span data-ttu-id="17212-128">Poniższy przykład pokazuje, jak odwoływać się do <xref:System.Drawing.Graphics> obiektu ze <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="17212-128">The following example shows how to reference a <xref:System.Drawing.Graphics> object from the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event:</span></span>  
  
    ```vb  
    Private Sub Form1_Paint(sender As Object, pe As PaintEventArgs) Handles _  
       MyBase.Paint  
       ' Declares the Graphics object and sets it to the Graphics object  
       ' supplied in the PaintEventArgs.  
       Dim g As Graphics = pe.Graphics  
       ' Insert code to paint the form here.  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Paint(object sender,
       System.Windows.Forms.PaintEventArgs pe)
    {  
       // Declares the Graphics object and sets it to the Graphics object  
       // supplied in the PaintEventArgs.  
       Graphics g = pe.Graphics;  
       // Insert code to paint the form here.  
    }  
    ```  
  
    ```cpp  
    private:  
       void Form1_Paint(System::Object ^ sender,  
          System::Windows::Forms::PaintEventArgs ^ pe)  
       {  
          // Declares the Graphics object and sets it to the Graphics object  
          // supplied in the PaintEventArgs.  
          Graphics ^ g = pe->Graphics;  
          // Insert code to paint the form here.  
       }  
    ```  
  
## <a name="creategraphics-method"></a><span data-ttu-id="17212-129">Metoda xmlgraphics</span><span class="sxs-lookup"><span data-stu-id="17212-129">CreateGraphics Method</span></span>  
 <span data-ttu-id="17212-130">Można również użyć <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody kontrolki lub formularza, aby uzyskać odwołanie do <xref:System.Drawing.Graphics> obiektu, który reprezentuje powierzchnię rysowania tego formantu lub formularza.</span><span class="sxs-lookup"><span data-stu-id="17212-130">You can also use the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span>  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a><span data-ttu-id="17212-131">Aby utworzyć obiekt grafiki przy użyciu metody xmlgraphics</span><span class="sxs-lookup"><span data-stu-id="17212-131">To create a Graphics object with the CreateGraphics method</span></span>  
  
- <span data-ttu-id="17212-132">Wywołaj <xref:System.Windows.Forms.Control.CreateGraphics%2A> metodę formularza lub kontrolki, na której chcesz renderować grafikę.</span><span class="sxs-lookup"><span data-stu-id="17212-132">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of the form or control upon which you want to render graphics.</span></span>  
  
    ```vb  
    Dim g as Graphics  
    ' Sets g to a Graphics object representing the drawing surface of the  
    ' control or form g is a member of.  
    g = Me.CreateGraphics  
    ```  
  
    ```csharp  
    Graphics g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this.CreateGraphics();  
    ```  
  
    ```cpp  
    Graphics ^ g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this->CreateGraphics();  
    ```  
  
## <a name="create-from-an-image-object"></a><span data-ttu-id="17212-133">Utwórz na podstawie obiektu obrazu</span><span class="sxs-lookup"><span data-stu-id="17212-133">Create from an Image Object</span></span>  
 <span data-ttu-id="17212-134">Ponadto można utworzyć obiekt grafiki z dowolnego obiektu, który pochodzi od <xref:System.Drawing.Image> klasy.</span><span class="sxs-lookup"><span data-stu-id="17212-134">Additionally, you can create a graphics object from any object that derives from the <xref:System.Drawing.Image> class.</span></span>  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a><span data-ttu-id="17212-135">Aby utworzyć obiekt grafiki z obrazu</span><span class="sxs-lookup"><span data-stu-id="17212-135">To create a Graphics object from an Image</span></span>  
  
- <span data-ttu-id="17212-136">Wywołaj <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> metodę, podając nazwę zmiennej obrazu, z której chcesz utworzyć <xref:System.Drawing.Graphics> obiekt.</span><span class="sxs-lookup"><span data-stu-id="17212-136">Call the <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> method, supplying the name of the Image variable from which you want to create a <xref:System.Drawing.Graphics> object.</span></span>  
  
     <span data-ttu-id="17212-137">Poniższy przykład pokazuje, jak używać <xref:System.Drawing.Bitmap> obiektu:</span><span class="sxs-lookup"><span data-stu-id="17212-137">The following example shows how to use a <xref:System.Drawing.Bitmap> object:</span></span>  
  
    ```vb  
    Dim myBitmap as New Bitmap("C:\Documents and Settings\Joe\Pics\myPic.bmp")  
    Dim g as Graphics = Graphics.FromImage(myBitmap)  
    ```  
  
    ```csharp  
    Bitmap myBitmap = new Bitmap(@"C:\Documents and
       Settings\Joe\Pics\myPic.bmp");  
    Graphics g = Graphics.FromImage(myBitmap);  
    ```  
  
    ```cpp  
    Bitmap ^ myBitmap = gcnew  
       Bitmap("D:\\Documents and Settings\\Joe\\Pics\\myPic.bmp");  
    Graphics ^ g = Graphics::FromImage(myBitmap);  
    ```  
  
> [!NOTE]
> <span data-ttu-id="17212-138">Można tworzyć tylko <xref:System.Drawing.Graphics> obiekty z nieindeksowanych plików BMP, takich jak 16-bitowe, 24-bitowe i 32-bitowe pliki BMP.</span><span class="sxs-lookup"><span data-stu-id="17212-138">You can only create <xref:System.Drawing.Graphics> objects from nonindexed .bmp files, such as 16-bit, 24-bit, and 32-bit .bmp files.</span></span> <span data-ttu-id="17212-139">Każdy piksel nieindeksowanych plików BMP posiada kolor, w przeciwieństwie do pikseli indeksowanych plików BMP, które przechowują indeks tabeli koloru.</span><span class="sxs-lookup"><span data-stu-id="17212-139">Each pixel of nonindexed .bmp files holds a color, in contrast to pixels of indexed .bmp files, which hold an index to a color table.</span></span>  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a><span data-ttu-id="17212-140">Rysowanie i manipulowanie kształtami i obrazami</span><span class="sxs-lookup"><span data-stu-id="17212-140">Drawing and Manipulating Shapes and Images</span></span>  
 <span data-ttu-id="17212-141">Po jego utworzeniu <xref:System.Drawing.Graphics> obiekt może być używany do rysowania linii i kształtów, renderowania tekstu lub wyświetlania obrazów i manipulowania nimi.</span><span class="sxs-lookup"><span data-stu-id="17212-141">After it is created, a <xref:System.Drawing.Graphics> object may be used to draw lines and shapes, render text, or display and manipulate images.</span></span> <span data-ttu-id="17212-142">Obiekty główne, które są używane z <xref:System.Drawing.Graphics> obiektem:</span><span class="sxs-lookup"><span data-stu-id="17212-142">The principal objects that are used with the <xref:System.Drawing.Graphics> object are:</span></span>  
  
- <span data-ttu-id="17212-143"><xref:System.Drawing.Pen>Klasa — używana do rysowania linii, tworzenia konspektów kształtów lub renderowania innych reprezentacji geometrycznych.</span><span class="sxs-lookup"><span data-stu-id="17212-143">The <xref:System.Drawing.Pen> class—Used for drawing lines, outlining shapes, or rendering other geometric representations.</span></span>  
  
- <span data-ttu-id="17212-144"><xref:System.Drawing.Brush>Klasa — używana do wypełniania obszarów grafiki, takich jak wypełnione kształty, obrazy lub tekst.</span><span class="sxs-lookup"><span data-stu-id="17212-144">The <xref:System.Drawing.Brush> class—Used for filling areas of graphics, such as filled shapes, images, or text.</span></span>  
  
- <span data-ttu-id="17212-145"><xref:System.Drawing.Font>Klasa — zawiera opis kształtów, które mają być używane podczas renderowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="17212-145">The <xref:System.Drawing.Font> class—Provides a description of what shapes to use when rendering text.</span></span>  
  
- <span data-ttu-id="17212-146"><xref:System.Drawing.Color>Struktura — reprezentuje różne kolory do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="17212-146">The <xref:System.Drawing.Color> structure—Represents the different colors to display.</span></span>  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a><span data-ttu-id="17212-147">Aby użyć utworzonego obiektu graficznego</span><span class="sxs-lookup"><span data-stu-id="17212-147">To use the Graphics object you have created</span></span>  
  
- <span data-ttu-id="17212-148">Pracuj z odpowiednim obiektem wymienionym powyżej, aby narysować to, czego potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="17212-148">Work with the appropriate object listed above to draw what you need.</span></span>  
  
     <span data-ttu-id="17212-149">Aby uzyskać więcej informacji, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="17212-149">For more information, see the following topics:</span></span>  
  
    |<span data-ttu-id="17212-150">Aby renderować</span><span class="sxs-lookup"><span data-stu-id="17212-150">To render</span></span>|<span data-ttu-id="17212-151">Zobacz</span><span class="sxs-lookup"><span data-stu-id="17212-151">See</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="17212-152">Linie</span><span class="sxs-lookup"><span data-stu-id="17212-152">Lines</span></span>|[<span data-ttu-id="17212-153">Instrukcje: rysowanie linii w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="17212-153">How to: Draw a Line on a Windows Form</span></span>](how-to-draw-a-line-on-a-windows-form.md)|  
    |<span data-ttu-id="17212-154">Kształty</span><span class="sxs-lookup"><span data-stu-id="17212-154">Shapes</span></span>|[<span data-ttu-id="17212-155">Porady: rysowanie konturu kształtu</span><span class="sxs-lookup"><span data-stu-id="17212-155">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)|  
    |<span data-ttu-id="17212-156">Tekst</span><span class="sxs-lookup"><span data-stu-id="17212-156">Text</span></span>|[<span data-ttu-id="17212-157">Porady: rysowanie tekstu w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="17212-157">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)|  
    |<span data-ttu-id="17212-158">Obrazy</span><span class="sxs-lookup"><span data-stu-id="17212-158">Images</span></span>|[<span data-ttu-id="17212-159">Instrukcje: renderowanie obrazów za pomocą GDI+</span><span class="sxs-lookup"><span data-stu-id="17212-159">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a><span data-ttu-id="17212-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17212-160">See also</span></span>

- [<span data-ttu-id="17212-161">Wprowadzenie do programowania grafiki</span><span class="sxs-lookup"><span data-stu-id="17212-161">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="17212-162">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="17212-162">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="17212-163">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="17212-163">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="17212-164">Instrukcje: renderowanie obrazów za pomocą GDI+</span><span class="sxs-lookup"><span data-stu-id="17212-164">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
