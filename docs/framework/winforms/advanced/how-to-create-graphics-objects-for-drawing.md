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
ms.openlocfilehash: a21e049cb91ec29bcd46eb04efd78487da9a6317
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497035"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a><span data-ttu-id="5b62a-102">Instrukcje: Tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="5b62a-102">How to: Create Graphics Objects for Drawing</span></span>
<span data-ttu-id="5b62a-103">Zanim można narysować linie i kształty, renderowanie tekstu, lub wyświetlanie obrazów i manipulowania nimi za pomocą [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], musisz utworzyć <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5b62a-103">Before you can draw lines and shapes, render text, or display and manipulate images with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you need to create a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="5b62a-104"><xref:System.Drawing.Graphics> Obiekt reprezentuje [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] rysowania powierzchni i jest obiekt, który jest używany do tworzenia obrazów graficznych.</span><span class="sxs-lookup"><span data-stu-id="5b62a-104">The <xref:System.Drawing.Graphics> object represents a [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] drawing surface, and is the object that is used to create graphical images.</span></span>  
  
 <span data-ttu-id="5b62a-105">W pracy z grafikami znajdują się dwa kroki:</span><span class="sxs-lookup"><span data-stu-id="5b62a-105">There are two steps in working with graphics:</span></span>  
  
1.  <span data-ttu-id="5b62a-106">Tworzenie <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5b62a-106">Creating a <xref:System.Drawing.Graphics> object.</span></span>  
  
2.  <span data-ttu-id="5b62a-107">Za pomocą <xref:System.Drawing.Graphics> obiektu rysowanie linii i kształtów, tekstu, renderowanie lub wyświetlania obrazów i manipulowania nimi.</span><span class="sxs-lookup"><span data-stu-id="5b62a-107">Using the <xref:System.Drawing.Graphics> object to draw lines and shapes, render text, or display and manipulate images.</span></span>  
  
## <a name="creating-a-graphics-object"></a><span data-ttu-id="5b62a-108">Tworzenie obiektów graficznych</span><span class="sxs-lookup"><span data-stu-id="5b62a-108">Creating a Graphics Object</span></span>  
 <span data-ttu-id="5b62a-109">Obiekt grafiki można utworzyć na wiele sposobów.</span><span class="sxs-lookup"><span data-stu-id="5b62a-109">A graphics object can be created in a variety of ways.</span></span>  
  
#### <a name="to-create-a-graphics-object"></a><span data-ttu-id="5b62a-110">Aby utworzyć obiekt grafiki</span><span class="sxs-lookup"><span data-stu-id="5b62a-110">To create a graphics object</span></span>  
  
-   <span data-ttu-id="5b62a-111">Odbieranie odwołanie do obiektu grafiki jako część <xref:System.Windows.Forms.PaintEventArgs> w <xref:System.Windows.Forms.Control.Paint> zdarzeń formularza lub formantu.</span><span class="sxs-lookup"><span data-stu-id="5b62a-111">Receive a reference to a graphics object as part of the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event of a form or control.</span></span> <span data-ttu-id="5b62a-112">Jest to zazwyczaj, jak uzyskać odwołanie do obiektu grafiki podczas tworzenia kodu rysowania dla formantu.</span><span class="sxs-lookup"><span data-stu-id="5b62a-112">This is usually how you obtain a reference to a graphics object when creating painting code for a control.</span></span> <span data-ttu-id="5b62a-113">Podobnie, można również uzyskać obiekt graficzny jako właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> podczas obsługi <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenie <xref:System.Drawing.Printing.PrintDocument>.</span><span class="sxs-lookup"><span data-stu-id="5b62a-113">Similarly, you can also obtain a graphics object as a property of the <xref:System.Drawing.Printing.PrintPageEventArgs> when handling the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event for a <xref:System.Drawing.Printing.PrintDocument>.</span></span>  
  
     <span data-ttu-id="5b62a-114">—lub—</span><span class="sxs-lookup"><span data-stu-id="5b62a-114">-or-</span></span>  
  
-   <span data-ttu-id="5b62a-115">Wywołaj <xref:System.Windows.Forms.Control.CreateGraphics%2A> metoda formantu lub formularz, aby uzyskać odwołanie do <xref:System.Drawing.Graphics> obiekt, który reprezentuje powierzchni do rysowania tego formularza lub formantu.</span><span class="sxs-lookup"><span data-stu-id="5b62a-115">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span> <span data-ttu-id="5b62a-116">Użyj tej metody, jeśli chcesz rysować na formularza lub formantu, który już istnieje.</span><span class="sxs-lookup"><span data-stu-id="5b62a-116">Use this method if you want to draw on a form or control that already exists.</span></span>  
  
     <span data-ttu-id="5b62a-117">—lub—</span><span class="sxs-lookup"><span data-stu-id="5b62a-117">-or-</span></span>  
  
-   <span data-ttu-id="5b62a-118">Tworzenie <xref:System.Drawing.Graphics> obiekt z dowolnego obiektu, który dziedziczy z <xref:System.Drawing.Image>.</span><span class="sxs-lookup"><span data-stu-id="5b62a-118">Create a <xref:System.Drawing.Graphics> object from any object that inherits from <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="5b62a-119">Takie podejście jest przydatne, jeśli chcesz zmienić istniejącego obrazu.</span><span class="sxs-lookup"><span data-stu-id="5b62a-119">This approach is useful when you want to alter an already existing image.</span></span>  
  
     <span data-ttu-id="5b62a-120">Poniższe sekcje zawierają szczegółowe informacje o każdej z tych procesów.</span><span class="sxs-lookup"><span data-stu-id="5b62a-120">The following sections give details about each of these processes.</span></span>  
  
## <a name="painteventargs-in-the-paint-event-handler"></a><span data-ttu-id="5b62a-121">PaintEventArgs w obsłudze zdarzeń malowania</span><span class="sxs-lookup"><span data-stu-id="5b62a-121">PaintEventArgs in the Paint Event Handler</span></span>  
 <span data-ttu-id="5b62a-122">Podczas programowania <xref:System.Windows.Forms.PaintEventHandler> dla formantów lub <xref:System.Drawing.Printing.PrintDocument.PrintPage> dla <xref:System.Drawing.Printing.PrintDocument>, obiekt graficzny jest dostarczana jako jedna z właściwości obiektu <xref:System.Windows.Forms.PaintEventArgs> lub <xref:System.Drawing.Printing.PrintPageEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="5b62a-122">When programming the <xref:System.Windows.Forms.PaintEventHandler> for controls or the <xref:System.Drawing.Printing.PrintDocument.PrintPage> for a <xref:System.Drawing.Printing.PrintDocument>, a graphics object is provided as one of the properties of <xref:System.Windows.Forms.PaintEventArgs> or <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a><span data-ttu-id="5b62a-123">Aby uzyskać odwołanie do obiektu grafiki z PaintEventArgs w zdarzenie malowania</span><span class="sxs-lookup"><span data-stu-id="5b62a-123">To obtain a reference to a Graphics object from the PaintEventArgs in the Paint event</span></span>  
  
1.  <span data-ttu-id="5b62a-124">Zadeklaruj <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5b62a-124">Declare the <xref:System.Drawing.Graphics> object.</span></span>  
  
2.  <span data-ttu-id="5b62a-125">Przypisz zmienną do odwoływania się do <xref:System.Drawing.Graphics> przekazano obiekt jako część <xref:System.Windows.Forms.PaintEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="5b62a-125">Assign the variable to refer to the <xref:System.Drawing.Graphics> object passed as part of the <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
3.  <span data-ttu-id="5b62a-126">Wstaw kod do malowania formularza lub formantu.</span><span class="sxs-lookup"><span data-stu-id="5b62a-126">Insert code to paint the form or control.</span></span>  
  
     <span data-ttu-id="5b62a-127">Poniższy przykład pokazuje, jak utworzyć odwołanie do <xref:System.Drawing.Graphics> obiektu z <xref:System.Windows.Forms.PaintEventArgs> w <xref:System.Windows.Forms.Control.Paint> zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="5b62a-127">The following example shows how to reference a <xref:System.Drawing.Graphics> object from the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event:</span></span>  
  
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
  
## <a name="creategraphics-method"></a><span data-ttu-id="5b62a-128">Metodę CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="5b62a-128">CreateGraphics Method</span></span>  
 <span data-ttu-id="5b62a-129">Można również użyć <xref:System.Windows.Forms.Control.CreateGraphics%2A> metoda formantu lub formularz, aby uzyskać odwołanie do <xref:System.Drawing.Graphics> obiekt, który reprezentuje powierzchni do rysowania tego formularza lub formantu.</span><span class="sxs-lookup"><span data-stu-id="5b62a-129">You can also use the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span>  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a><span data-ttu-id="5b62a-130">Aby utworzyć obiekt graficzny z metodę CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="5b62a-130">To create a Graphics object with the CreateGraphics method</span></span>  
  
-   <span data-ttu-id="5b62a-131">Wywołaj <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody formularza lub formantu, na którym ma być renderowany grafiki.</span><span class="sxs-lookup"><span data-stu-id="5b62a-131">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of the form or control upon which you want to render graphics.</span></span>  
  
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
  
## <a name="create-from-an-image-object"></a><span data-ttu-id="5b62a-132">Tworzenie na podstawie obiektu obrazu</span><span class="sxs-lookup"><span data-stu-id="5b62a-132">Create from an Image Object</span></span>  
 <span data-ttu-id="5b62a-133">Ponadto można utworzyć obiekt grafiki z dowolnych obiektów, która pochodzi od klasy <xref:System.Drawing.Image> klasy.</span><span class="sxs-lookup"><span data-stu-id="5b62a-133">Additionally, you can create a graphics object from any object that derives from the <xref:System.Drawing.Image> class.</span></span>  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a><span data-ttu-id="5b62a-134">Aby utworzyć obiekt grafiki z obrazu</span><span class="sxs-lookup"><span data-stu-id="5b62a-134">To create a Graphics object from an Image</span></span>  
  
-   <span data-ttu-id="5b62a-135">Wywołaj <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> metody, podając nazwę zmiennej obrazu, z którego chcesz utworzyć <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5b62a-135">Call the <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> method, supplying the name of the Image variable from which you want to create a <xref:System.Drawing.Graphics> object.</span></span>  
  
     <span data-ttu-id="5b62a-136">Poniższy przykład pokazuje, jak używać <xref:System.Drawing.Bitmap> obiektu:</span><span class="sxs-lookup"><span data-stu-id="5b62a-136">The following example shows how to use a <xref:System.Drawing.Bitmap> object:</span></span>  
  
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
>  <span data-ttu-id="5b62a-137">Można tworzyć tylko <xref:System.Drawing.Graphics> obiektów z nieindeksowanym .bmp — pliki, takie jak pliki .bmp 16-bitowych, 24-bitowego i 32-bitowych.</span><span class="sxs-lookup"><span data-stu-id="5b62a-137">You can only create <xref:System.Drawing.Graphics> objects from nonindexed .bmp files, such as 16-bit, 24-bit, and 32-bit .bmp files.</span></span> <span data-ttu-id="5b62a-138">Każdego piksela nieindeksowanych .bmp — pliki zawiera kolor, w przeciwieństwie do pikseli .bmp indeksowane pliki, które przechowywania indeksu tabeli kolorów.</span><span class="sxs-lookup"><span data-stu-id="5b62a-138">Each pixel of nonindexed .bmp files holds a color, in contrast to pixels of indexed .bmp files, which hold an index to a color table.</span></span>  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a><span data-ttu-id="5b62a-139">Rysowanie i manipulowanie nimi kształtów i obrazów</span><span class="sxs-lookup"><span data-stu-id="5b62a-139">Drawing and Manipulating Shapes and Images</span></span>  
 <span data-ttu-id="5b62a-140">Po jego utworzeniu <xref:System.Drawing.Graphics> obiekt może służyć do rysowania linii i kształtów, renderowanie tekstu, lub wyświetlanie obrazów i manipulowania nimi.</span><span class="sxs-lookup"><span data-stu-id="5b62a-140">After it is created, a <xref:System.Drawing.Graphics> object may be used to draw lines and shapes, render text, or display and manipulate images.</span></span> <span data-ttu-id="5b62a-141">Obiekty główne, które są używane z <xref:System.Drawing.Graphics> obiekt są:</span><span class="sxs-lookup"><span data-stu-id="5b62a-141">The principal objects that are used with the <xref:System.Drawing.Graphics> object are:</span></span>  
  
-   <span data-ttu-id="5b62a-142"><xref:System.Drawing.Pen> Klasy — Rysowanie linii, kształtów lub renderowania inne oświadczenia geometrycznych.</span><span class="sxs-lookup"><span data-stu-id="5b62a-142">The <xref:System.Drawing.Pen> class—Used for drawing lines, outlining shapes, or rendering other geometric representations.</span></span>  
  
-   <span data-ttu-id="5b62a-143"><xref:System.Drawing.Brush> Klasy — używany do wypełniania obszarów grafiki, takie jak wypełnione kształty, obrazy i tekst.</span><span class="sxs-lookup"><span data-stu-id="5b62a-143">The <xref:System.Drawing.Brush> class—Used for filling areas of graphics, such as filled shapes, images, or text.</span></span>  
  
-   <span data-ttu-id="5b62a-144"><xref:System.Drawing.Font> Klasy — zawiera opis co kształty do użycia podczas renderowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="5b62a-144">The <xref:System.Drawing.Font> class—Provides a description of what shapes to use when rendering text.</span></span>  
  
-   <span data-ttu-id="5b62a-145"><xref:System.Drawing.Color> Struktury — reprezentuje różne kolory do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="5b62a-145">The <xref:System.Drawing.Color> structure—Represents the different colors to display.</span></span>  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a><span data-ttu-id="5b62a-146">Aby użyć obiektu grafiki, utworzonych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="5b62a-146">To use the Graphics object you have created</span></span>  
  
-   <span data-ttu-id="5b62a-147">Praca z odpowiedniego obiektu wymienionych powyżej, aby narysować, co jest potrzebne.</span><span class="sxs-lookup"><span data-stu-id="5b62a-147">Work with the appropriate object listed above to draw what you need.</span></span>  
  
     <span data-ttu-id="5b62a-148">Więcej informacji znajduje się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="5b62a-148">For more information, see the following topics:</span></span>  
  
    |<span data-ttu-id="5b62a-149">Do renderowania</span><span class="sxs-lookup"><span data-stu-id="5b62a-149">To render</span></span>|<span data-ttu-id="5b62a-150">Zobacz</span><span class="sxs-lookup"><span data-stu-id="5b62a-150">See</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="5b62a-151">wiersze</span><span class="sxs-lookup"><span data-stu-id="5b62a-151">Lines</span></span>|[<span data-ttu-id="5b62a-152">Instrukcje: Rysuj linię w formularzu Windows</span><span class="sxs-lookup"><span data-stu-id="5b62a-152">How to: Draw a Line on a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-on-a-windows-form.md)|  
    |<span data-ttu-id="5b62a-153">Kształty</span><span class="sxs-lookup"><span data-stu-id="5b62a-153">Shapes</span></span>|[<span data-ttu-id="5b62a-154">Instrukcje: Rysowanie konturu kształtu</span><span class="sxs-lookup"><span data-stu-id="5b62a-154">How to: Draw an Outlined Shape</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)|  
    |<span data-ttu-id="5b62a-155">Tekst</span><span class="sxs-lookup"><span data-stu-id="5b62a-155">Text</span></span>|[<span data-ttu-id="5b62a-156">Instrukcje: Rysowanie tekstu w formularzu Windows</span><span class="sxs-lookup"><span data-stu-id="5b62a-156">How to: Draw Text on a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-on-a-windows-form.md)|  
    |<span data-ttu-id="5b62a-157">Obrazy</span><span class="sxs-lookup"><span data-stu-id="5b62a-157">Images</span></span>|[<span data-ttu-id="5b62a-158">Instrukcje: Renderowanie obrazów za pomocą GDI +</span><span class="sxs-lookup"><span data-stu-id="5b62a-158">How to: Render Images with GDI+</span></span>](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a><span data-ttu-id="5b62a-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b62a-159">See also</span></span>
- [<span data-ttu-id="5b62a-160">Wprowadzenie do programowania grafiki</span><span class="sxs-lookup"><span data-stu-id="5b62a-160">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)
- [<span data-ttu-id="5b62a-161">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5b62a-161">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="5b62a-162">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="5b62a-162">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)
- [<span data-ttu-id="5b62a-163">Instrukcje: Renderowanie obrazów za pomocą GDI +</span><span class="sxs-lookup"><span data-stu-id="5b62a-163">How to: Render Images with GDI+</span></span>](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)
