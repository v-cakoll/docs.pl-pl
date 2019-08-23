---
title: 'Instrukcje: Tworzenie obiektów graficznych do rysowania'
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
ms.openlocfilehash: 3d3ab62896f6b799cd38a8180b90f33125a9929b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964341"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a><span data-ttu-id="8d489-102">Instrukcje: Tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="8d489-102">How to: Create Graphics Objects for Drawing</span></span>
<span data-ttu-id="8d489-103">Aby można było rysować linie i kształty, renderować tekst lub wyświetlać i manipulować obrazami za pomocą interfejsu GDI+, należy utworzyć <xref:System.Drawing.Graphics> obiekt.</span><span class="sxs-lookup"><span data-stu-id="8d489-103">Before you can draw lines and shapes, render text, or display and manipulate images with GDI+, you need to create a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="8d489-104"><xref:System.Drawing.Graphics> Obiekt reprezentuje powierzchnię rysowania GDI+ i jest obiektem, który jest używany do tworzenia obrazów graficznych.</span><span class="sxs-lookup"><span data-stu-id="8d489-104">The <xref:System.Drawing.Graphics> object represents a GDI+ drawing surface, and is the object that is used to create graphical images.</span></span>  
  
 <span data-ttu-id="8d489-105">Istnieją dwa kroki pracy z grafiką:</span><span class="sxs-lookup"><span data-stu-id="8d489-105">There are two steps in working with graphics:</span></span>  
  
1. <span data-ttu-id="8d489-106"><xref:System.Drawing.Graphics> Tworzenie obiektu.</span><span class="sxs-lookup"><span data-stu-id="8d489-106">Creating a <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="8d489-107"><xref:System.Drawing.Graphics> Używanie obiektu do rysowania linii i kształtów, renderowania tekstu lub wyświetlania obrazów i manipulowania nimi.</span><span class="sxs-lookup"><span data-stu-id="8d489-107">Using the <xref:System.Drawing.Graphics> object to draw lines and shapes, render text, or display and manipulate images.</span></span>  
  
## <a name="creating-a-graphics-object"></a><span data-ttu-id="8d489-108">Tworzenie obiektu graficznego</span><span class="sxs-lookup"><span data-stu-id="8d489-108">Creating a Graphics Object</span></span>  
 <span data-ttu-id="8d489-109">Obiekt grafiki można utworzyć na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="8d489-109">A graphics object can be created in a variety of ways.</span></span>  
  
#### <a name="to-create-a-graphics-object"></a><span data-ttu-id="8d489-110">Aby utworzyć obiekt grafiki</span><span class="sxs-lookup"><span data-stu-id="8d489-110">To create a graphics object</span></span>  
  
- <span data-ttu-id="8d489-111">Odbierz odwołanie do obiektu grafiki <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> w ramach zdarzenia formularza lub kontrolki.</span><span class="sxs-lookup"><span data-stu-id="8d489-111">Receive a reference to a graphics object as part of the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event of a form or control.</span></span> <span data-ttu-id="8d489-112">Jest to zazwyczaj sposób uzyskiwania odwołania do obiektu grafiki podczas tworzenia kodu rysowania dla kontrolki.</span><span class="sxs-lookup"><span data-stu-id="8d489-112">This is usually how you obtain a reference to a graphics object when creating painting code for a control.</span></span> <span data-ttu-id="8d489-113">Podobnie, można również uzyskać obiekt grafiki jako właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> podczas <xref:System.Drawing.Printing.PrintDocument.PrintPage> obsługi zdarzenia dla elementu <xref:System.Drawing.Printing.PrintDocument>.</span><span class="sxs-lookup"><span data-stu-id="8d489-113">Similarly, you can also obtain a graphics object as a property of the <xref:System.Drawing.Printing.PrintPageEventArgs> when handling the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event for a <xref:System.Drawing.Printing.PrintDocument>.</span></span>  
  
     <span data-ttu-id="8d489-114">—lub—</span><span class="sxs-lookup"><span data-stu-id="8d489-114">-or-</span></span>  
  
- <span data-ttu-id="8d489-115">Wywołaj <xref:System.Drawing.Graphics> metodę kontrolki lub formularza, aby uzyskać odwołanie do obiektu, który reprezentuje powierzchnię rysowania tego formantu lub formularza. <xref:System.Windows.Forms.Control.CreateGraphics%2A></span><span class="sxs-lookup"><span data-stu-id="8d489-115">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span> <span data-ttu-id="8d489-116">Użyj tej metody, jeśli chcesz rysować na formularzu lub kontrolce, która już istnieje.</span><span class="sxs-lookup"><span data-stu-id="8d489-116">Use this method if you want to draw on a form or control that already exists.</span></span>  
  
     <span data-ttu-id="8d489-117">—lub—</span><span class="sxs-lookup"><span data-stu-id="8d489-117">-or-</span></span>  
  
- <span data-ttu-id="8d489-118">Utwórz obiekt z dowolnego obiektu, który dziedziczy z <xref:System.Drawing.Image>. <xref:System.Drawing.Graphics></span><span class="sxs-lookup"><span data-stu-id="8d489-118">Create a <xref:System.Drawing.Graphics> object from any object that inherits from <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="8d489-119">Takie podejście jest przydatne, gdy chcesz zmienić już istniejący obraz.</span><span class="sxs-lookup"><span data-stu-id="8d489-119">This approach is useful when you want to alter an already existing image.</span></span>  
  
     <span data-ttu-id="8d489-120">Poniższe sekcje zawierają szczegółowe informacje o każdym z tych procesów.</span><span class="sxs-lookup"><span data-stu-id="8d489-120">The following sections give details about each of these processes.</span></span>  
  
## <a name="painteventargs-in-the-paint-event-handler"></a><span data-ttu-id="8d489-121">PaintEventArgs w programie obsługi zdarzeń programu Paint</span><span class="sxs-lookup"><span data-stu-id="8d489-121">PaintEventArgs in the Paint Event Handler</span></span>  
 <span data-ttu-id="8d489-122"><xref:System.Windows.Forms.PaintEventHandler> Gdy programowanie <xref:System.Drawing.Printing.PrintPageEventArgs>dla kontrolek <xref:System.Drawing.Printing.PrintDocument.PrintPage> lub dla obiektu a <xref:System.Drawing.Printing.PrintDocument>, obiekt grafiki <xref:System.Windows.Forms.PaintEventArgs> jest udostępniany jako jedna z właściwości lub.</span><span class="sxs-lookup"><span data-stu-id="8d489-122">When programming the <xref:System.Windows.Forms.PaintEventHandler> for controls or the <xref:System.Drawing.Printing.PrintDocument.PrintPage> for a <xref:System.Drawing.Printing.PrintDocument>, a graphics object is provided as one of the properties of <xref:System.Windows.Forms.PaintEventArgs> or <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a><span data-ttu-id="8d489-123">Aby uzyskać odwołanie do obiektu grafiki z PaintEventArgs w zdarzeniu Paint</span><span class="sxs-lookup"><span data-stu-id="8d489-123">To obtain a reference to a Graphics object from the PaintEventArgs in the Paint event</span></span>  
  
1. <span data-ttu-id="8d489-124">Zadeklaruj <xref:System.Drawing.Graphics> obiekt.</span><span class="sxs-lookup"><span data-stu-id="8d489-124">Declare the <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="8d489-125">Przypisz zmienną, aby odwołać <xref:System.Drawing.Graphics> się do obiektu przesyłanego jako część <xref:System.Windows.Forms.PaintEventArgs>elementu.</span><span class="sxs-lookup"><span data-stu-id="8d489-125">Assign the variable to refer to the <xref:System.Drawing.Graphics> object passed as part of the <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
3. <span data-ttu-id="8d489-126">Wstaw kod, aby malować formularz lub kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="8d489-126">Insert code to paint the form or control.</span></span>  
  
     <span data-ttu-id="8d489-127">Poniższy przykład pokazuje, <xref:System.Drawing.Graphics> jak odwoływać się do obiektu <xref:System.Windows.Forms.PaintEventArgs> ze <xref:System.Windows.Forms.Control.Paint> zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="8d489-127">The following example shows how to reference a <xref:System.Drawing.Graphics> object from the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event:</span></span>  
  
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
  
## <a name="creategraphics-method"></a><span data-ttu-id="8d489-128">Metoda xmlgraphics</span><span class="sxs-lookup"><span data-stu-id="8d489-128">CreateGraphics Method</span></span>  
 <span data-ttu-id="8d489-129">Można również użyć <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody kontrolki lub formularza, aby uzyskać odwołanie <xref:System.Drawing.Graphics> do obiektu, który reprezentuje powierzchnię rysowania tego formantu lub formularza.</span><span class="sxs-lookup"><span data-stu-id="8d489-129">You can also use the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span>  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a><span data-ttu-id="8d489-130">Aby utworzyć obiekt grafiki przy użyciu metody xmlgraphics</span><span class="sxs-lookup"><span data-stu-id="8d489-130">To create a Graphics object with the CreateGraphics method</span></span>  
  
- <span data-ttu-id="8d489-131">Wywołaj <xref:System.Windows.Forms.Control.CreateGraphics%2A> metodę formularza lub kontrolki, na której chcesz renderować grafikę.</span><span class="sxs-lookup"><span data-stu-id="8d489-131">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of the form or control upon which you want to render graphics.</span></span>  
  
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
  
## <a name="create-from-an-image-object"></a><span data-ttu-id="8d489-132">Utwórz na podstawie obiektu obrazu</span><span class="sxs-lookup"><span data-stu-id="8d489-132">Create from an Image Object</span></span>  
 <span data-ttu-id="8d489-133">Ponadto można utworzyć obiekt grafiki z dowolnego obiektu, który pochodzi od <xref:System.Drawing.Image> klasy.</span><span class="sxs-lookup"><span data-stu-id="8d489-133">Additionally, you can create a graphics object from any object that derives from the <xref:System.Drawing.Image> class.</span></span>  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a><span data-ttu-id="8d489-134">Aby utworzyć obiekt grafiki z obrazu</span><span class="sxs-lookup"><span data-stu-id="8d489-134">To create a Graphics object from an Image</span></span>  
  
- <span data-ttu-id="8d489-135">Wywołaj <xref:System.Drawing.Graphics> metodę, podając nazwę zmiennej obrazu, z której chcesz utworzyć obiekt. <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8d489-135">Call the <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> method, supplying the name of the Image variable from which you want to create a <xref:System.Drawing.Graphics> object.</span></span>  
  
     <span data-ttu-id="8d489-136">Poniższy przykład pokazuje, <xref:System.Drawing.Bitmap> jak używać obiektu:</span><span class="sxs-lookup"><span data-stu-id="8d489-136">The following example shows how to use a <xref:System.Drawing.Bitmap> object:</span></span>  
  
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
> <span data-ttu-id="8d489-137">Można tworzyć <xref:System.Drawing.Graphics> tylko obiekty z nieindeksowanych plików BMP, takich jak 16-bitowe, 24-bitowe i 32-bitowe pliki BMP.</span><span class="sxs-lookup"><span data-stu-id="8d489-137">You can only create <xref:System.Drawing.Graphics> objects from nonindexed .bmp files, such as 16-bit, 24-bit, and 32-bit .bmp files.</span></span> <span data-ttu-id="8d489-138">Każdy piksel nieindeksowanych plików BMP posiada kolor, w przeciwieństwie do pikseli indeksowanych plików BMP, które przechowują indeks tabeli koloru.</span><span class="sxs-lookup"><span data-stu-id="8d489-138">Each pixel of nonindexed .bmp files holds a color, in contrast to pixels of indexed .bmp files, which hold an index to a color table.</span></span>  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a><span data-ttu-id="8d489-139">Rysowanie i manipulowanie kształtami i obrazami</span><span class="sxs-lookup"><span data-stu-id="8d489-139">Drawing and Manipulating Shapes and Images</span></span>  
 <span data-ttu-id="8d489-140">Po jego utworzeniu <xref:System.Drawing.Graphics> obiekt może być używany do rysowania linii i kształtów, renderowania tekstu lub wyświetlania obrazów i manipulowania nimi.</span><span class="sxs-lookup"><span data-stu-id="8d489-140">After it is created, a <xref:System.Drawing.Graphics> object may be used to draw lines and shapes, render text, or display and manipulate images.</span></span> <span data-ttu-id="8d489-141">Obiekty główne, które są używane z <xref:System.Drawing.Graphics> obiektem:</span><span class="sxs-lookup"><span data-stu-id="8d489-141">The principal objects that are used with the <xref:System.Drawing.Graphics> object are:</span></span>  
  
- <span data-ttu-id="8d489-142"><xref:System.Drawing.Pen> Klasa — używana do rysowania linii, tworzenia konspektów kształtów lub renderowania innych reprezentacji geometrycznych.</span><span class="sxs-lookup"><span data-stu-id="8d489-142">The <xref:System.Drawing.Pen> class—Used for drawing lines, outlining shapes, or rendering other geometric representations.</span></span>  
  
- <span data-ttu-id="8d489-143"><xref:System.Drawing.Brush> Klasa — używana do wypełniania obszarów grafiki, takich jak wypełnione kształty, obrazy lub tekst.</span><span class="sxs-lookup"><span data-stu-id="8d489-143">The <xref:System.Drawing.Brush> class—Used for filling areas of graphics, such as filled shapes, images, or text.</span></span>  
  
- <span data-ttu-id="8d489-144"><xref:System.Drawing.Font> Klasa — zawiera opis kształtów, które mają być używane podczas renderowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="8d489-144">The <xref:System.Drawing.Font> class—Provides a description of what shapes to use when rendering text.</span></span>  
  
- <span data-ttu-id="8d489-145"><xref:System.Drawing.Color> Struktura — reprezentuje różne kolory do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="8d489-145">The <xref:System.Drawing.Color> structure—Represents the different colors to display.</span></span>  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a><span data-ttu-id="8d489-146">Aby użyć utworzonego obiektu graficznego</span><span class="sxs-lookup"><span data-stu-id="8d489-146">To use the Graphics object you have created</span></span>  
  
- <span data-ttu-id="8d489-147">Pracuj z odpowiednim obiektem wymienionym powyżej, aby narysować to, czego potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="8d489-147">Work with the appropriate object listed above to draw what you need.</span></span>  
  
     <span data-ttu-id="8d489-148">Więcej informacji znajduje się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="8d489-148">For more information, see the following topics:</span></span>  
  
    |<span data-ttu-id="8d489-149">Aby renderować</span><span class="sxs-lookup"><span data-stu-id="8d489-149">To render</span></span>|<span data-ttu-id="8d489-150">Zobacz</span><span class="sxs-lookup"><span data-stu-id="8d489-150">See</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="8d489-151">Wiersze</span><span class="sxs-lookup"><span data-stu-id="8d489-151">Lines</span></span>|[<span data-ttu-id="8d489-152">Instrukcje: Rysuj linię w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8d489-152">How to: Draw a Line on a Windows Form</span></span>](how-to-draw-a-line-on-a-windows-form.md)|  
    |<span data-ttu-id="8d489-153">Kształty</span><span class="sxs-lookup"><span data-stu-id="8d489-153">Shapes</span></span>|[<span data-ttu-id="8d489-154">Instrukcje: Rysowanie konturu kształtu</span><span class="sxs-lookup"><span data-stu-id="8d489-154">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)|  
    |<span data-ttu-id="8d489-155">Tekst</span><span class="sxs-lookup"><span data-stu-id="8d489-155">Text</span></span>|[<span data-ttu-id="8d489-156">Instrukcje: Rysuj tekst w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8d489-156">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)|  
    |<span data-ttu-id="8d489-157">Obrazy</span><span class="sxs-lookup"><span data-stu-id="8d489-157">Images</span></span>|[<span data-ttu-id="8d489-158">Instrukcje: Renderowanie obrazów za pomocą interfejsu GDI+</span><span class="sxs-lookup"><span data-stu-id="8d489-158">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a><span data-ttu-id="8d489-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8d489-159">See also</span></span>

- [<span data-ttu-id="8d489-160">Wprowadzenie do programowania grafiki</span><span class="sxs-lookup"><span data-stu-id="8d489-160">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="8d489-161">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8d489-161">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="8d489-162">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="8d489-162">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="8d489-163">Instrukcje: Renderowanie obrazów za pomocą interfejsu GDI+</span><span class="sxs-lookup"><span data-stu-id="8d489-163">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
