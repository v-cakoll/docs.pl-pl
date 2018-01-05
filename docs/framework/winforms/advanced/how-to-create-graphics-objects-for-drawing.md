---
title: "Porady: tworzenie obiektów graficznych do rysowania"
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
- cpp
helpviewer_keywords:
- graphics [Windows Forms], creating
- images [Windows Forms], creating
- GDI+, creating images
ms.assetid: 162861f9-f050-445e-8abb-b2c43a918b8b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d4b626d3d87c6537b74b6d28e086303474ea2c3e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-graphics-objects-for-drawing"></a><span data-ttu-id="da577-102">Porady: tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="da577-102">How to: Create Graphics Objects for Drawing</span></span>
<span data-ttu-id="da577-103">Przed może wykonywać Rysowanie linii i kształtów, renderowania tekstu, lub wyświetlania i modyfikowania obrazów za pomocą [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], należy utworzyć <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="da577-103">Before you can draw lines and shapes, render text, or display and manipulate images with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you need to create a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="da577-104"><xref:System.Drawing.Graphics> Obiekt reprezentuje [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] powierzchni rysowania i jest obiekt, który służy do tworzenia obrazów graficznego.</span><span class="sxs-lookup"><span data-stu-id="da577-104">The <xref:System.Drawing.Graphics> object represents a [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] drawing surface, and is the object that is used to create graphical images.</span></span>  
  
 <span data-ttu-id="da577-105">Istnieją dwa kroki pracy z grafiki:</span><span class="sxs-lookup"><span data-stu-id="da577-105">There are two steps in working with graphics:</span></span>  
  
1.  <span data-ttu-id="da577-106">Tworzenie <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="da577-106">Creating a <xref:System.Drawing.Graphics> object.</span></span>  
  
2.  <span data-ttu-id="da577-107">Przy użyciu <xref:System.Drawing.Graphics> obiekt do rysowania linii i kształtów, renderowanie tekstu, lub wyświetlanie obrazów i manipulowania nimi.</span><span class="sxs-lookup"><span data-stu-id="da577-107">Using the <xref:System.Drawing.Graphics> object to draw lines and shapes, render text, or display and manipulate images.</span></span>  
  
## <a name="creating-a-graphics-object"></a><span data-ttu-id="da577-108">Tworzenie obiektów graficznych</span><span class="sxs-lookup"><span data-stu-id="da577-108">Creating a Graphics Object</span></span>  
 <span data-ttu-id="da577-109">Obiekt grafiki można tworzyć wiele sposobów.</span><span class="sxs-lookup"><span data-stu-id="da577-109">A graphics object can be created in a variety of ways.</span></span>  
  
#### <a name="to-create-a-graphics-object"></a><span data-ttu-id="da577-110">Aby utworzyć obiekt grafiki</span><span class="sxs-lookup"><span data-stu-id="da577-110">To create a graphics object</span></span>  
  
-   <span data-ttu-id="da577-111">Odbieranie odwołanie do obiektu graphics jako część <xref:System.Windows.Forms.PaintEventArgs> w <xref:System.Windows.Forms.Control.Paint> zdarzeń formularza lub kontrolki.</span><span class="sxs-lookup"><span data-stu-id="da577-111">Receive a reference to a graphics object as part of the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event of a form or control.</span></span> <span data-ttu-id="da577-112">Jest to zwykle, jak uzyskać odwołania do obiektu grafiki podczas tworzenia kodu malowanie kontrolki.</span><span class="sxs-lookup"><span data-stu-id="da577-112">This is usually how you obtain a reference to a graphics object when creating painting code for a control.</span></span> <span data-ttu-id="da577-113">Podobnie, możesz również uzyskać obiekt graphics jako właściwość <xref:System.Drawing.Printing.PrintPageEventArgs> podczas obsługi <xref:System.Drawing.Printing.PrintDocument.PrintPage> zdarzenia dla <xref:System.Drawing.Printing.PrintDocument>.</span><span class="sxs-lookup"><span data-stu-id="da577-113">Similarly, you can also obtain a graphics object as a property of the <xref:System.Drawing.Printing.PrintPageEventArgs> when handling the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event for a <xref:System.Drawing.Printing.PrintDocument>.</span></span>  
  
     <span data-ttu-id="da577-114">—lub—</span><span class="sxs-lookup"><span data-stu-id="da577-114">-or-</span></span>  
  
-   <span data-ttu-id="da577-115">Wywołanie <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody formantu lub formularza, aby uzyskać odwołania do <xref:System.Drawing.Graphics> obiekt, który reprezentuje powierzchni rysowania tego formantu lub formularza.</span><span class="sxs-lookup"><span data-stu-id="da577-115">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span> <span data-ttu-id="da577-116">Użyj tej metody, jeśli chcesz narysować na formularz lub formant, który już istnieje.</span><span class="sxs-lookup"><span data-stu-id="da577-116">Use this method if you want to draw on a form or control that already exists.</span></span>  
  
     <span data-ttu-id="da577-117">—lub—</span><span class="sxs-lookup"><span data-stu-id="da577-117">-or-</span></span>  
  
-   <span data-ttu-id="da577-118">Utwórz <xref:System.Drawing.Graphics> obiektu z dowolnych obiektów, która dziedziczy <xref:System.Drawing.Image>.</span><span class="sxs-lookup"><span data-stu-id="da577-118">Create a <xref:System.Drawing.Graphics> object from any object that inherits from <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="da577-119">Takie rozwiązanie jest przydatne, jeśli chcesz zmienić już istniejącego obrazu.</span><span class="sxs-lookup"><span data-stu-id="da577-119">This approach is useful when you want to alter an already existing image.</span></span>  
  
     <span data-ttu-id="da577-120">W poniższych sekcjach znajdują się szczegółowe informacje o każdym z tych procesów.</span><span class="sxs-lookup"><span data-stu-id="da577-120">The following sections give details about each of these processes.</span></span>  
  
## <a name="painteventargs-in-the-paint-event-handler"></a><span data-ttu-id="da577-121">PaintEventArgs w obsłudze zdarzeń malowania</span><span class="sxs-lookup"><span data-stu-id="da577-121">PaintEventArgs in the Paint Event Handler</span></span>  
 <span data-ttu-id="da577-122">Programowania <xref:System.Windows.Forms.PaintEventHandler> dla formantów lub <xref:System.Drawing.Printing.PrintDocument.PrintPage> dla <xref:System.Drawing.Printing.PrintDocument>, obiekt graphics jest dostępna jako jedna z właściwości obiektu <xref:System.Windows.Forms.PaintEventArgs> lub <xref:System.Drawing.Printing.PrintPageEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="da577-122">When programming the <xref:System.Windows.Forms.PaintEventHandler> for controls or the <xref:System.Drawing.Printing.PrintDocument.PrintPage> for a <xref:System.Drawing.Printing.PrintDocument>, a graphics object is provided as one of the properties of <xref:System.Windows.Forms.PaintEventArgs> or <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a><span data-ttu-id="da577-123">Aby uzyskać odwołanie do obiektu Graphics z PaintEventArgs w zdarzenie malowania</span><span class="sxs-lookup"><span data-stu-id="da577-123">To obtain a reference to a Graphics object from the PaintEventArgs in the Paint event</span></span>  
  
1.  <span data-ttu-id="da577-124">Deklarowanie <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="da577-124">Declare the <xref:System.Drawing.Graphics> object.</span></span>  
  
2.  <span data-ttu-id="da577-125">Przypisz do odwoływania się do zmiennej <xref:System.Drawing.Graphics> przekazano obiekt jako część <xref:System.Windows.Forms.PaintEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="da577-125">Assign the variable to refer to the <xref:System.Drawing.Graphics> object passed as part of the <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
3.  <span data-ttu-id="da577-126">Wstawianie kodu do malowania formularza lub kontrolki.</span><span class="sxs-lookup"><span data-stu-id="da577-126">Insert code to paint the form or control.</span></span>  
  
     <span data-ttu-id="da577-127">Poniższy przykład przedstawia sposób odwoływania się do <xref:System.Drawing.Graphics> obiekt z <xref:System.Windows.Forms.PaintEventArgs> w <xref:System.Windows.Forms.Control.Paint> zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="da577-127">The following example shows how to reference a <xref:System.Drawing.Graphics> object from the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event:</span></span>  
  
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
  
## <a name="creategraphics-method"></a><span data-ttu-id="da577-128">Metodę CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="da577-128">CreateGraphics Method</span></span>  
 <span data-ttu-id="da577-129">Można również użyć <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody formantu lub formularza, aby uzyskać odwołania do <xref:System.Drawing.Graphics> obiekt, który reprezentuje powierzchni rysowania tego formantu lub formularza.</span><span class="sxs-lookup"><span data-stu-id="da577-129">You can also use the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span>  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a><span data-ttu-id="da577-130">Aby utworzyć obiekt grafiki przy użyciu metody CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="da577-130">To create a Graphics object with the CreateGraphics method</span></span>  
  
-   <span data-ttu-id="da577-131">Wywołanie <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody formularza lub kontrolki, na którym ma być renderowany grafiki.</span><span class="sxs-lookup"><span data-stu-id="da577-131">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of the form or control upon which you want to render graphics.</span></span>  
  
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
  
## <a name="create-from-an-image-object"></a><span data-ttu-id="da577-132">Utwórz na podstawie obiektu obrazu</span><span class="sxs-lookup"><span data-stu-id="da577-132">Create from an Image Object</span></span>  
 <span data-ttu-id="da577-133">Ponadto można utworzyć obiektu graphics z dowolnych obiektów, która jest pochodną <xref:System.Drawing.Image> klasy.</span><span class="sxs-lookup"><span data-stu-id="da577-133">Additionally, you can create a graphics object from any object that derives from the <xref:System.Drawing.Image> class.</span></span>  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a><span data-ttu-id="da577-134">Aby utworzyć obiekt Graphics z obrazu</span><span class="sxs-lookup"><span data-stu-id="da577-134">To create a Graphics object from an Image</span></span>  
  
-   <span data-ttu-id="da577-135">Wywołanie <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> metody, podając nazwę zmiennej obrazu, w którym chcesz utworzyć <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="da577-135">Call the <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> method, supplying the name of the Image variable from which you want to create a <xref:System.Drawing.Graphics> object.</span></span>  
  
     <span data-ttu-id="da577-136">Poniższy przykład przedstawia użycie <xref:System.Drawing.Bitmap> obiektu:</span><span class="sxs-lookup"><span data-stu-id="da577-136">The following example shows how to use a <xref:System.Drawing.Bitmap> object:</span></span>  
  
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
>  <span data-ttu-id="da577-137">Można tworzyć tylko <xref:System.Drawing.Graphics> obiektów z plików nieindeksowanych bmp, takich jak pliki .bmp 16-bitowych, 24-bitowe i 32-bitowych.</span><span class="sxs-lookup"><span data-stu-id="da577-137">You can only create <xref:System.Drawing.Graphics> objects from nonindexed .bmp files, such as 16-bit, 24-bit, and 32-bit .bmp files.</span></span> <span data-ttu-id="da577-138">Każdy pikseli nieindeksowanych .bmp — pliki przechowuje kolor, w przeciwieństwie do pikseli indeksowanych .bmp plików, które mógł pomieścić indeksu tabeli kolorów.</span><span class="sxs-lookup"><span data-stu-id="da577-138">Each pixel of nonindexed .bmp files holds a color, in contrast to pixels of indexed .bmp files, which hold an index to a color table.</span></span>  
  
-  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a><span data-ttu-id="da577-139">Rysowanie i operowanie nimi kształtów i obrazów</span><span class="sxs-lookup"><span data-stu-id="da577-139">Drawing and Manipulating Shapes and Images</span></span>  
 <span data-ttu-id="da577-140">Po jego utworzeniu <xref:System.Drawing.Graphics> obiekt może służyć do rysowania linii i kształtów, renderowanie tekstu, lub wyświetlanie obrazów i manipulowania nimi.</span><span class="sxs-lookup"><span data-stu-id="da577-140">After it is created, a <xref:System.Drawing.Graphics> object may be used to draw lines and shapes, render text, or display and manipulate images.</span></span> <span data-ttu-id="da577-141">Obiekty główne, które są używane z <xref:System.Drawing.Graphics> obiektu są:</span><span class="sxs-lookup"><span data-stu-id="da577-141">The principal objects that are used with the <xref:System.Drawing.Graphics> object are:</span></span>  
  
-   <span data-ttu-id="da577-142"><xref:System.Drawing.Pen> Klasy — Rysowanie linii, kształtów lub renderowania innych reprezentacje geometrycznej.</span><span class="sxs-lookup"><span data-stu-id="da577-142">The <xref:System.Drawing.Pen> class—Used for drawing lines, outlining shapes, or rendering other geometric representations.</span></span>  
  
-   <span data-ttu-id="da577-143"><xref:System.Drawing.Brush> Klasy — używany do wypełniania obszarów grafiki, takie jak wypełnione kształty, obrazy i tekst.</span><span class="sxs-lookup"><span data-stu-id="da577-143">The <xref:System.Drawing.Brush> class—Used for filling areas of graphics, such as filled shapes, images, or text.</span></span>  
  
-   <span data-ttu-id="da577-144"><xref:System.Drawing.Font> Klasy — zawiera opis co kształty do użycia podczas renderowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="da577-144">The <xref:System.Drawing.Font> class—Provides a description of what shapes to use when rendering text.</span></span>  
  
-   <span data-ttu-id="da577-145"><xref:System.Drawing.Color> Struktury — reprezentuje różne kolory do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="da577-145">The <xref:System.Drawing.Color> structure—Represents the different colors to display.</span></span>  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a><span data-ttu-id="da577-146">Aby użyć obiektu Graphics został utworzony</span><span class="sxs-lookup"><span data-stu-id="da577-146">To use the Graphics object you have created</span></span>  
  
-   <span data-ttu-id="da577-147">Współpraca z odpowiedniego obiektu wymienionych powyżej, aby narysować, co jest potrzebne.</span><span class="sxs-lookup"><span data-stu-id="da577-147">Work with the appropriate object listed above to draw what you need.</span></span>  
  
     <span data-ttu-id="da577-148">Więcej informacji znajduje się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="da577-148">For more information, see the following topics:</span></span>  
  
    |<span data-ttu-id="da577-149">Do renderowania</span><span class="sxs-lookup"><span data-stu-id="da577-149">To render</span></span>|<span data-ttu-id="da577-150">Zobacz</span><span class="sxs-lookup"><span data-stu-id="da577-150">See</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="da577-151">wiersze</span><span class="sxs-lookup"><span data-stu-id="da577-151">Lines</span></span>|[<span data-ttu-id="da577-152">Instrukcje: rysowanie linii w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="da577-152">How to: Draw a Line on a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-on-a-windows-form.md)|  
    |<span data-ttu-id="da577-153">Kształty</span><span class="sxs-lookup"><span data-stu-id="da577-153">Shapes</span></span>|[<span data-ttu-id="da577-154">Instrukcje: rysowanie konturu kształtu</span><span class="sxs-lookup"><span data-stu-id="da577-154">How to: Draw an Outlined Shape</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)|  
    |<span data-ttu-id="da577-155">Tekst</span><span class="sxs-lookup"><span data-stu-id="da577-155">Text</span></span>|[<span data-ttu-id="da577-156">Instrukcje: rysowanie tekstu w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="da577-156">How to: Draw Text on a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-on-a-windows-form.md)|  
    |<span data-ttu-id="da577-157">Obrazy</span><span class="sxs-lookup"><span data-stu-id="da577-157">Images</span></span>|[<span data-ttu-id="da577-158">Instrukcje: renderowanie obrazów za pomocą GDI+</span><span class="sxs-lookup"><span data-stu-id="da577-158">How to: Render Images with GDI+</span></span>](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a><span data-ttu-id="da577-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da577-159">See Also</span></span>  
 [<span data-ttu-id="da577-160">Wprowadzenie do programowania grafiki</span><span class="sxs-lookup"><span data-stu-id="da577-160">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="da577-161">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="da577-161">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="da577-162">Linie, krzywe i kształty</span><span class="sxs-lookup"><span data-stu-id="da577-162">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="da577-163">Instrukcje: renderowanie obrazów za pomocą GDI+</span><span class="sxs-lookup"><span data-stu-id="da577-163">How to: Render Images with GDI+</span></span>](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)
