---
title: 'Porady: tworzenie obiektów graficznych do rysowania'
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
ms.openlocfilehash: d591d65904484e33285e5db7aa99760f3e1909d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142436"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a><span data-ttu-id="2ed3d-102">Porady: tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="2ed3d-102">How to: Create Graphics Objects for Drawing</span></span>
<span data-ttu-id="2ed3d-103">Aby można było rysować linie i kształty, renderować tekst lub wyświetlać i <xref:System.Drawing.Graphics> manipulować obrazami za pomocą GDI+, należy utworzyć obiekt.</span><span class="sxs-lookup"><span data-stu-id="2ed3d-103">Before you can draw lines and shapes, render text, or display and manipulate images with GDI+, you need to create a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="2ed3d-104">Obiekt <xref:System.Drawing.Graphics> reprezentuje powierzchnię rysunku GDI+ i jest obiektem używanym do tworzenia obrazów graficznych.</span><span class="sxs-lookup"><span data-stu-id="2ed3d-104">The <xref:System.Drawing.Graphics> object represents a GDI+ drawing surface, and is the object that is used to create graphical images.</span></span>  
  
 <span data-ttu-id="2ed3d-105">Istnieją dwa kroki pracy z grafiką:</span><span class="sxs-lookup"><span data-stu-id="2ed3d-105">There are two steps in working with graphics:</span></span>  
  
1. <span data-ttu-id="2ed3d-106">Tworzenie <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="2ed3d-106">Creating a <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="2ed3d-107">Używanie <xref:System.Drawing.Graphics> obiektu do rysowania linii i kształtów, renderowania tekstu lub wyświetlania i manipulowania obrazami.</span><span class="sxs-lookup"><span data-stu-id="2ed3d-107">Using the <xref:System.Drawing.Graphics> object to draw lines and shapes, render text, or display and manipulate images.</span></span>  
  
## <a name="creating-a-graphics-object"></a><span data-ttu-id="2ed3d-108">Tworzenie obiektu graficznego</span><span class="sxs-lookup"><span data-stu-id="2ed3d-108">Creating a Graphics Object</span></span>  
 <span data-ttu-id="2ed3d-109">Obiekt graficzny można utworzyć na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="2ed3d-109">A graphics object can be created in a variety of ways.</span></span>  
  
#### <a name="to-create-a-graphics-object"></a><span data-ttu-id="2ed3d-110">Aby utworzyć obiekt graficzny</span><span class="sxs-lookup"><span data-stu-id="2ed3d-110">To create a graphics object</span></span>  
  
- <span data-ttu-id="2ed3d-111">Odbierz odwołanie do obiektu graficznego <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> jako część w przypadku formularza lub formantu.</span><span class="sxs-lookup"><span data-stu-id="2ed3d-111">Receive a reference to a graphics object as part of the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event of a form or control.</span></span> <span data-ttu-id="2ed3d-112">Jest to zwykle sposób uzyskania odwołania do obiektu graficznego podczas tworzenia kodu malowania formantu.</span><span class="sxs-lookup"><span data-stu-id="2ed3d-112">This is usually how you obtain a reference to a graphics object when creating painting code for a control.</span></span> <span data-ttu-id="2ed3d-113">Podobnie można również uzyskać obiekt graficzny jako właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> podczas <xref:System.Drawing.Printing.PrintDocument.PrintPage> obsługi <xref:System.Drawing.Printing.PrintDocument>zdarzenia dla .</span><span class="sxs-lookup"><span data-stu-id="2ed3d-113">Similarly, you can also obtain a graphics object as a property of the <xref:System.Drawing.Printing.PrintPageEventArgs> when handling the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event for a <xref:System.Drawing.Printing.PrintDocument>.</span></span>  
  
     <span data-ttu-id="2ed3d-114">— lub —</span><span class="sxs-lookup"><span data-stu-id="2ed3d-114">-or-</span></span>  
  
- <span data-ttu-id="2ed3d-115">Wywołanie <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody formantu lub formularza, <xref:System.Drawing.Graphics> aby uzyskać odwołanie do obiektu, który reprezentuje powierzchnię rysunku tego formantu lub formularza.</span><span class="sxs-lookup"><span data-stu-id="2ed3d-115">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span> <span data-ttu-id="2ed3d-116">Tej metody należy użyć, jeśli chcesz narysować formularz lub formant, który już istnieje.</span><span class="sxs-lookup"><span data-stu-id="2ed3d-116">Use this method if you want to draw on a form or control that already exists.</span></span>  
  
     <span data-ttu-id="2ed3d-117">— lub —</span><span class="sxs-lookup"><span data-stu-id="2ed3d-117">-or-</span></span>  
  
- <span data-ttu-id="2ed3d-118">Utwórz <xref:System.Drawing.Graphics> obiekt z dowolnego obiektu, który dziedziczy z . <xref:System.Drawing.Image></span><span class="sxs-lookup"><span data-stu-id="2ed3d-118">Create a <xref:System.Drawing.Graphics> object from any object that inherits from <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="2ed3d-119">Takie podejście jest przydatne, gdy chcesz zmienić już istniejący obraz.</span><span class="sxs-lookup"><span data-stu-id="2ed3d-119">This approach is useful when you want to alter an already existing image.</span></span>  
  
     <span data-ttu-id="2ed3d-120">W poniższych sekcjach podano szczegółowe informacje na temat każdego z tych procesów.</span><span class="sxs-lookup"><span data-stu-id="2ed3d-120">The following sections give details about each of these processes.</span></span>  
  
## <a name="painteventargs-in-the-paint-event-handler"></a><span data-ttu-id="2ed3d-121">PaintEventArgs w programie obsługi zdarzeń malowania</span><span class="sxs-lookup"><span data-stu-id="2ed3d-121">PaintEventArgs in the Paint Event Handler</span></span>  
 <span data-ttu-id="2ed3d-122">Podczas programowania <xref:System.Windows.Forms.PaintEventHandler> formanty <xref:System.Drawing.Printing.PrintDocument.PrintPage> lub <xref:System.Drawing.Printing.PrintDocument>fora obiekt graficzny jest dostarczany jako <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Drawing.Printing.PrintPageEventArgs>jedna z właściwości lub .</span><span class="sxs-lookup"><span data-stu-id="2ed3d-122">When programming the <xref:System.Windows.Forms.PaintEventHandler> for controls or the <xref:System.Drawing.Printing.PrintDocument.PrintPage> for a <xref:System.Drawing.Printing.PrintDocument>, a graphics object is provided as one of the properties of <xref:System.Windows.Forms.PaintEventArgs> or <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a><span data-ttu-id="2ed3d-123">Aby uzyskać odwołanie do obiektu Graphics z PaintEventArgs w paint zdarzenia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="2ed3d-123">To obtain a reference to a Graphics object from the PaintEventArgs in the Paint event</span></span>  
  
1. <span data-ttu-id="2ed3d-124">Zadeklaruj <xref:System.Drawing.Graphics> obiekt.</span><span class="sxs-lookup"><span data-stu-id="2ed3d-124">Declare the <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="2ed3d-125">Przypisz zmienną, <xref:System.Drawing.Graphics> aby odwoływać się <xref:System.Windows.Forms.PaintEventArgs>do obiektu przekazanego jako część pliku .</span><span class="sxs-lookup"><span data-stu-id="2ed3d-125">Assign the variable to refer to the <xref:System.Drawing.Graphics> object passed as part of the <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
3. <span data-ttu-id="2ed3d-126">Wstaw kod, aby pomalować formularz lub formant.</span><span class="sxs-lookup"><span data-stu-id="2ed3d-126">Insert code to paint the form or control.</span></span>  
  
     <span data-ttu-id="2ed3d-127">Poniższy przykład pokazuje, <xref:System.Drawing.Graphics> jak odwoływać się do obiektu z <xref:System.Windows.Forms.PaintEventArgs> w zdarzeniu: <xref:System.Windows.Forms.Control.Paint></span><span class="sxs-lookup"><span data-stu-id="2ed3d-127">The following example shows how to reference a <xref:System.Drawing.Graphics> object from the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event:</span></span>  
  
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
  
## <a name="creategraphics-method"></a><span data-ttu-id="2ed3d-128">Metoda CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="2ed3d-128">CreateGraphics Method</span></span>  
 <span data-ttu-id="2ed3d-129">Można również użyć <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody formantu lub formularza, <xref:System.Drawing.Graphics> aby uzyskać odwołanie do obiektu, który reprezentuje powierzchnię rysunku tego formantu lub formularza.</span><span class="sxs-lookup"><span data-stu-id="2ed3d-129">You can also use the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span>  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a><span data-ttu-id="2ed3d-130">Aby utworzyć obiekt Graphics za pomocą metody CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="2ed3d-130">To create a Graphics object with the CreateGraphics method</span></span>  
  
- <span data-ttu-id="2ed3d-131">Wywołanie <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody formularza lub formantu, na którym chcesz renderować grafikę.</span><span class="sxs-lookup"><span data-stu-id="2ed3d-131">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of the form or control upon which you want to render graphics.</span></span>  
  
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
  
## <a name="create-from-an-image-object"></a><span data-ttu-id="2ed3d-132">Tworzenie z obiektu obrazu</span><span class="sxs-lookup"><span data-stu-id="2ed3d-132">Create from an Image Object</span></span>  
 <span data-ttu-id="2ed3d-133">Ponadto można utworzyć obiekt graficzny z dowolnego obiektu, <xref:System.Drawing.Image> który pochodzi z klasy.</span><span class="sxs-lookup"><span data-stu-id="2ed3d-133">Additionally, you can create a graphics object from any object that derives from the <xref:System.Drawing.Image> class.</span></span>  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a><span data-ttu-id="2ed3d-134">Aby utworzyć obiekt Graphics na podstawie obrazu</span><span class="sxs-lookup"><span data-stu-id="2ed3d-134">To create a Graphics object from an Image</span></span>  
  
- <span data-ttu-id="2ed3d-135">Wywołanie <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> metody, podając nazwę Zmiennej Image, z <xref:System.Drawing.Graphics> której chcesz utworzyć obiekt.</span><span class="sxs-lookup"><span data-stu-id="2ed3d-135">Call the <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> method, supplying the name of the Image variable from which you want to create a <xref:System.Drawing.Graphics> object.</span></span>  
  
     <span data-ttu-id="2ed3d-136">W poniższym <xref:System.Drawing.Bitmap> przykładzie pokazano, jak używać obiektu:</span><span class="sxs-lookup"><span data-stu-id="2ed3d-136">The following example shows how to use a <xref:System.Drawing.Bitmap> object:</span></span>  
  
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
> <span data-ttu-id="2ed3d-137">Można tworzyć <xref:System.Drawing.Graphics> tylko obiekty z plików bmp nieindeksowanych, takie jak pliki 16-bitowe, 24-bitowe i 32-bitowe .bmp.</span><span class="sxs-lookup"><span data-stu-id="2ed3d-137">You can only create <xref:System.Drawing.Graphics> objects from nonindexed .bmp files, such as 16-bit, 24-bit, and 32-bit .bmp files.</span></span> <span data-ttu-id="2ed3d-138">Każdy piksel plików .bmp nonindexed posiada kolor, w przeciwieństwie do pikseli indeksowanych plików .bmp, które posiadają indeks do tabeli kolorów.</span><span class="sxs-lookup"><span data-stu-id="2ed3d-138">Each pixel of nonindexed .bmp files holds a color, in contrast to pixels of indexed .bmp files, which hold an index to a color table.</span></span>  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a><span data-ttu-id="2ed3d-139">Rysowanie i manipulowanie kształtami i obrazami</span><span class="sxs-lookup"><span data-stu-id="2ed3d-139">Drawing and Manipulating Shapes and Images</span></span>  
 <span data-ttu-id="2ed3d-140">Po utworzeniu <xref:System.Drawing.Graphics> obiektu można użyć obiektu do rysowania linii i kształtów, renderowania tekstu lub wyświetlania i manipulowania obrazami.</span><span class="sxs-lookup"><span data-stu-id="2ed3d-140">After it is created, a <xref:System.Drawing.Graphics> object may be used to draw lines and shapes, render text, or display and manipulate images.</span></span> <span data-ttu-id="2ed3d-141">Głównymi obiektami, które <xref:System.Drawing.Graphics> są używane z obiektem są:</span><span class="sxs-lookup"><span data-stu-id="2ed3d-141">The principal objects that are used with the <xref:System.Drawing.Graphics> object are:</span></span>  
  
- <span data-ttu-id="2ed3d-142">Klasa <xref:System.Drawing.Pen> — służy do rysowania linii, tworzenia kształtów lub renderowania innych reprezentacji geometrycznych.</span><span class="sxs-lookup"><span data-stu-id="2ed3d-142">The <xref:System.Drawing.Pen> class—Used for drawing lines, outlining shapes, or rendering other geometric representations.</span></span>  
  
- <span data-ttu-id="2ed3d-143">Klasa <xref:System.Drawing.Brush> — służy do wypełniania obszarów grafiki, takich jak wypełnione kształty, obrazy lub tekst.</span><span class="sxs-lookup"><span data-stu-id="2ed3d-143">The <xref:System.Drawing.Brush> class—Used for filling areas of graphics, such as filled shapes, images, or text.</span></span>  
  
- <span data-ttu-id="2ed3d-144">Klasa <xref:System.Drawing.Font> — zawiera opis kształtów, których należy używać podczas renderowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="2ed3d-144">The <xref:System.Drawing.Font> class—Provides a description of what shapes to use when rendering text.</span></span>  
  
- <span data-ttu-id="2ed3d-145">Struktura <xref:System.Drawing.Color> — reprezentuje różne kolory do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="2ed3d-145">The <xref:System.Drawing.Color> structure—Represents the different colors to display.</span></span>  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a><span data-ttu-id="2ed3d-146">Aby użyć utworzonego obiektu Graphics</span><span class="sxs-lookup"><span data-stu-id="2ed3d-146">To use the Graphics object you have created</span></span>  
  
- <span data-ttu-id="2ed3d-147">Pracuj z odpowiednim obiektem wymienionym powyżej, aby narysować to, czego potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="2ed3d-147">Work with the appropriate object listed above to draw what you need.</span></span>  
  
     <span data-ttu-id="2ed3d-148">Aby uzyskać więcej informacji, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="2ed3d-148">For more information, see the following topics:</span></span>  
  
    |<span data-ttu-id="2ed3d-149">Aby renderować</span><span class="sxs-lookup"><span data-stu-id="2ed3d-149">To render</span></span>|<span data-ttu-id="2ed3d-150">Zobacz</span><span class="sxs-lookup"><span data-stu-id="2ed3d-150">See</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="2ed3d-151">Linie</span><span class="sxs-lookup"><span data-stu-id="2ed3d-151">Lines</span></span>|[<span data-ttu-id="2ed3d-152">Instrukcje: rysowanie linii w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2ed3d-152">How to: Draw a Line on a Windows Form</span></span>](how-to-draw-a-line-on-a-windows-form.md)|  
    |<span data-ttu-id="2ed3d-153">Kształty</span><span class="sxs-lookup"><span data-stu-id="2ed3d-153">Shapes</span></span>|[<span data-ttu-id="2ed3d-154">Porady: rysowanie konturu kształtu</span><span class="sxs-lookup"><span data-stu-id="2ed3d-154">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)|  
    |<span data-ttu-id="2ed3d-155">Tekst</span><span class="sxs-lookup"><span data-stu-id="2ed3d-155">Text</span></span>|[<span data-ttu-id="2ed3d-156">Porady: rysowanie tekstu w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2ed3d-156">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)|  
    |<span data-ttu-id="2ed3d-157">Obrazy</span><span class="sxs-lookup"><span data-stu-id="2ed3d-157">Images</span></span>|[<span data-ttu-id="2ed3d-158">Instrukcje: renderowanie obrazów za pomocą GDI+</span><span class="sxs-lookup"><span data-stu-id="2ed3d-158">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a><span data-ttu-id="2ed3d-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ed3d-159">See also</span></span>

- [<span data-ttu-id="2ed3d-160">Wprowadzenie do programowania grafiki</span><span class="sxs-lookup"><span data-stu-id="2ed3d-160">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="2ed3d-161">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2ed3d-161">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="2ed3d-162">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="2ed3d-162">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="2ed3d-163">Instrukcje: renderowanie obrazów za pomocą GDI+</span><span class="sxs-lookup"><span data-stu-id="2ed3d-163">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
