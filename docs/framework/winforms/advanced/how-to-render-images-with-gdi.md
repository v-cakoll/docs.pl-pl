---
title: 'Porady: renderowanie obrazów za pomocą GDI+'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], creating
- GDI+, rendering existing images
ms.assetid: c128b79a-3e31-47d8-9e66-3470f570a056
ms.openlocfilehash: fffe1f1052d7323d234985b7e752866f2e89657d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182502"
---
# <a name="how-to-render-images-with-gdi"></a><span data-ttu-id="96939-102">Porady: renderowanie obrazów za pomocą GDI+</span><span class="sxs-lookup"><span data-stu-id="96939-102">How to: Render Images with GDI+</span></span>
<span data-ttu-id="96939-103">Za pomocą GDI+ można renderować obrazy, które istnieją jako pliki w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="96939-103">You can use GDI+ to render images that exist as files in your applications.</span></span> <span data-ttu-id="96939-104">Można to zrobić, tworząc nowy <xref:System.Drawing.Image> obiekt klasy <xref:System.Drawing.Bitmap>(na przykład <xref:System.Drawing.Graphics> ), tworząc obiekt, który odwołuje się do <xref:System.Drawing.Graphics.DrawImage%2A> powierzchni rysunku, której chcesz użyć, i wywołując metodę <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="96939-104">You do this by creating a new object of an <xref:System.Drawing.Image> class (such as <xref:System.Drawing.Bitmap>), creating a <xref:System.Drawing.Graphics> object that refers to the drawing surface you want to use, and calling the <xref:System.Drawing.Graphics.DrawImage%2A> method of the <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="96939-105">Obraz zostanie pomalowany na powierzchni rysunku reprezentowanej przez klasę grafiki.</span><span class="sxs-lookup"><span data-stu-id="96939-105">The image will be painted onto the drawing surface represented by the graphics class.</span></span> <span data-ttu-id="96939-106">Za pomocą Edytora obrazów można tworzyć i edytować pliki obrazów w czasie projektowania oraz renderować je za pomocą interfejsu GDI+ w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="96939-106">You can use the Image Editor to create and edit image files at design time, and render them with GDI+ at run time.</span></span> <span data-ttu-id="96939-107">Aby uzyskać więcej informacji, zobacz [Edytor obrazów ikon](/cpp/windows/image-editor-for-icons).</span><span class="sxs-lookup"><span data-stu-id="96939-107">For more information, see [Image Editor for Icons](/cpp/windows/image-editor-for-icons).</span></span>  
  
### <a name="to-render-an-image-with-gdi"></a><span data-ttu-id="96939-108">Aby renderować obraz za pomocą GDI+</span><span class="sxs-lookup"><span data-stu-id="96939-108">To render an image with GDI+</span></span>  
  
1. <span data-ttu-id="96939-109">Utwórz obiekt reprezentujący obraz, który ma być wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="96939-109">Create an object representing the image you want to display.</span></span> <span data-ttu-id="96939-110">Ten obiekt musi być członkiem klasy, <xref:System.Drawing.Image>która <xref:System.Drawing.Bitmap> dziedziczy po , takich jak lub <xref:System.Drawing.Imaging.Metafile>.</span><span class="sxs-lookup"><span data-stu-id="96939-110">This object must be a member of a class that inherits from <xref:System.Drawing.Image>, such as <xref:System.Drawing.Bitmap> or <xref:System.Drawing.Imaging.Metafile>.</span></span> <span data-ttu-id="96939-111">Pokazany jest przykład:</span><span class="sxs-lookup"><span data-stu-id="96939-111">An example is shown:</span></span>  
  
    ```vb  
    ' Uses the System.Environment.GetFolderPath to get the path to the
    ' current user's MyPictures folder.  
    Dim myBitmap as New Bitmap _  
       (System.Environment.GetFolderPath _  
          (System.Environment.SpecialFolder.MyPictures))  
    ```  
  
    ```csharp  
    // Uses the System.Environment.GetFolderPath to get the path to the
    // current user's MyPictures folder.  
    Bitmap myBitmap = new Bitmap  
       (System.Environment.GetFolderPath  
          (System.Environment.SpecialFolder.MyPictures));  
    ```  
  
    ```cpp  
    // Uses the System.Environment.GetFolderPath to get the path to the
    // current user's MyPictures folder.  
    Bitmap^ myBitmap = gcnew Bitmap  
       (System::Environment::GetFolderPath  
          (System::Environment::SpecialFolder::MyPictures));  
    ```  
  
2. <span data-ttu-id="96939-112">Utwórz <xref:System.Drawing.Graphics> obiekt reprezentujący powierzchnię rysunku, której chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="96939-112">Create a <xref:System.Drawing.Graphics> object that represents the drawing surface you want to use.</span></span> <span data-ttu-id="96939-113">Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie obiektów graficznych do rysowania](how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="96939-113">For more information, see [How to: Create Graphics Objects for Drawing](how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
    ```vb  
    ' Creates a Graphics object that represents the drawing surface of
    ' Button1.  
    Dim g as Graphics = Button1.CreateGraphics  
    ```  
  
    ```csharp  
    // Creates a Graphics object that represents the drawing surface of
    // Button1.  
    Graphics g = Button1.CreateGraphics();  
    ```  
  
    ```cpp  
    // Creates a Graphics object that represents the drawing surface of
    // Button1.  
    Graphics^ g = button1->CreateGraphics();  
    ```  
  
3. <span data-ttu-id="96939-114">Wywołanie <xref:System.Drawing.Graphics.DrawImage%2A> obiektu graficznego, aby renderować obraz.</span><span class="sxs-lookup"><span data-stu-id="96939-114">Call the <xref:System.Drawing.Graphics.DrawImage%2A> of your graphics object to render the image.</span></span> <span data-ttu-id="96939-115">Należy określić zarówno obraz, który ma zostać narysowany, jak i współrzędne, w których ma zostać narysowany.</span><span class="sxs-lookup"><span data-stu-id="96939-115">You must specify both the image to be drawn, and the coordinates where it is to be drawn.</span></span>  
  
    ```vb  
    g.DrawImage(myBitmap, 1, 1)  
    ```  
  
    ```csharp  
    g.DrawImage(myBitmap, 1, 1);  
    ```  
  
    ```cpp  
    g->DrawImage(myBitmap, 1, 1);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="96939-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="96939-116">See also</span></span>

- [<span data-ttu-id="96939-117">Wprowadzenie do programowania grafiki</span><span class="sxs-lookup"><span data-stu-id="96939-117">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="96939-118">Instrukcje: tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="96939-118">How to: Create Graphics Objects for Drawing</span></span>](how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="96939-119">Pióra, linie i prostokąty w GDI+</span><span class="sxs-lookup"><span data-stu-id="96939-119">Pens, Lines, and Rectangles in GDI+</span></span>](pens-lines-and-rectangles-in-gdi.md)
- [<span data-ttu-id="96939-120">Porady: rysowanie tekstu w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="96939-120">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)
- [<span data-ttu-id="96939-121">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="96939-121">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="96939-122">Linie rysunku lub liczby zamknięte</span><span class="sxs-lookup"><span data-stu-id="96939-122">Drawing Lines or Closed Figures</span></span>](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)
- [<span data-ttu-id="96939-123">Edytor obrazów dla ikon</span><span class="sxs-lookup"><span data-stu-id="96939-123">Image Editor for Icons</span></span>](/cpp/windows/image-editor-for-icons)
