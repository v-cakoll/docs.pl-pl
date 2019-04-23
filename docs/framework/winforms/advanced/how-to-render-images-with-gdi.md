---
title: 'Instrukcje: Renderowanie obrazów za pomocą GDI+'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], creating
- GDI+, rendering existing images
ms.assetid: c128b79a-3e31-47d8-9e66-3470f570a056
ms.openlocfilehash: e038da545bb3f56cc757710bcaa93aa2c86bfa67
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342553"
---
# <a name="how-to-render-images-with-gdi"></a><span data-ttu-id="86bb5-102">Instrukcje: Renderowanie obrazów za pomocą GDI+</span><span class="sxs-lookup"><span data-stu-id="86bb5-102">How to: Render Images with GDI+</span></span>
<span data-ttu-id="86bb5-103">Możesz użyć [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] renderowanie obrazów, które istnieją w postaci plików w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="86bb5-103">You can use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to render images that exist as files in your applications.</span></span> <span data-ttu-id="86bb5-104">Można to zrobić, tworząc nowy obiekt <xref:System.Drawing.Image> klasy (takie jak <xref:System.Drawing.Bitmap>), tworzenie <xref:System.Drawing.Graphics> obiekt, który odwołuje się do powierzchni rysowania, którego chcesz użyć, a podczas wywoływania <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="86bb5-104">You do this by creating a new object of an <xref:System.Drawing.Image> class (such as <xref:System.Drawing.Bitmap>), creating a <xref:System.Drawing.Graphics> object that refers to the drawing surface you want to use, and calling the <xref:System.Drawing.Graphics.DrawImage%2A> method of the <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="86bb5-105">Obraz będą rysowane na powierzchnię rysunku, reprezentowane przez klasę grafiki.</span><span class="sxs-lookup"><span data-stu-id="86bb5-105">The image will be painted onto the drawing surface represented by the graphics class.</span></span> <span data-ttu-id="86bb5-106">Można użyć edytora obrazów, aby tworzyć i edytować pliki obrazów w czasie projektowania i renderowania je za pomocą [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="86bb5-106">You can use the Image Editor to create and edit image files at design time, and render them with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] at run time.</span></span> <span data-ttu-id="86bb5-107">Aby uzyskać więcej informacji, zobacz [edytor obrazów dla ikon](/cpp/windows/image-editor-for-icons).</span><span class="sxs-lookup"><span data-stu-id="86bb5-107">For more information, see [Image Editor for Icons](/cpp/windows/image-editor-for-icons).</span></span>  
  
### <a name="to-render-an-image-with-gdi"></a><span data-ttu-id="86bb5-108">Aby renderować obraz za pomocą GDI +</span><span class="sxs-lookup"><span data-stu-id="86bb5-108">To render an image with GDI+</span></span>  
  
1. <span data-ttu-id="86bb5-109">Utwórz obiekt reprezentujący obraz, który chcesz wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="86bb5-109">Create an object representing the image you want to display.</span></span> <span data-ttu-id="86bb5-110">Ten obiekt musi należeć do klasy, która dziedziczy po elemencie <xref:System.Drawing.Image>, takich jak <xref:System.Drawing.Bitmap> lub <xref:System.Drawing.Imaging.Metafile>.</span><span class="sxs-lookup"><span data-stu-id="86bb5-110">This object must be a member of a class that inherits from <xref:System.Drawing.Image>, such as <xref:System.Drawing.Bitmap> or <xref:System.Drawing.Imaging.Metafile>.</span></span> <span data-ttu-id="86bb5-111">Przykład przedstawiono:</span><span class="sxs-lookup"><span data-stu-id="86bb5-111">An example is shown:</span></span>  
  
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
  
2. <span data-ttu-id="86bb5-112">Utwórz <xref:System.Drawing.Graphics> obiekt, który reprezentuje powierzchnię rysunku, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="86bb5-112">Create a <xref:System.Drawing.Graphics> object that represents the drawing surface you want to use.</span></span> <span data-ttu-id="86bb5-113">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie obiektów graficznych do rysowania](how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="86bb5-113">For more information, see [How to: Create Graphics Objects for Drawing](how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
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
  
3. <span data-ttu-id="86bb5-114">Wywołaj <xref:System.Drawing.Graphics.DrawImage%2A> obiektów graficznych do renderowania obrazu.</span><span class="sxs-lookup"><span data-stu-id="86bb5-114">Call the <xref:System.Drawing.Graphics.DrawImage%2A> of your graphics object to render the image.</span></span> <span data-ttu-id="86bb5-115">Należy określić obraz, który ma być rysowany oraz współrzędne, w którym ma być rysowany.</span><span class="sxs-lookup"><span data-stu-id="86bb5-115">You must specify both the image to be drawn, and the coordinates where it is to be drawn.</span></span>  
  
    ```vb  
    g.DrawImage(myBitmap, 1, 1)  
    ```  
  
    ```csharp  
    g.DrawImage(myBitmap, 1, 1);  
    ```  
  
    ```cpp  
    g->DrawImage(myBitmap, 1, 1);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="86bb5-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86bb5-116">See also</span></span>

- [<span data-ttu-id="86bb5-117">Wprowadzenie do programowania grafiki</span><span class="sxs-lookup"><span data-stu-id="86bb5-117">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="86bb5-118">Instrukcje: Tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="86bb5-118">How to: Create Graphics Objects for Drawing</span></span>](how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="86bb5-119">Pióra, linie i prostokąty w GDI+</span><span class="sxs-lookup"><span data-stu-id="86bb5-119">Pens, Lines, and Rectangles in GDI+</span></span>](pens-lines-and-rectangles-in-gdi.md)
- [<span data-ttu-id="86bb5-120">Instrukcje: Rysowanie tekstu w formularzu Windows</span><span class="sxs-lookup"><span data-stu-id="86bb5-120">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)
- [<span data-ttu-id="86bb5-121">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="86bb5-121">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="86bb5-122">Linie rysunku lub zamkniętych figur</span><span class="sxs-lookup"><span data-stu-id="86bb5-122">Drawing Lines or Closed Figures</span></span>](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)
- [<span data-ttu-id="86bb5-123">Edytor obrazów dla ikon</span><span class="sxs-lookup"><span data-stu-id="86bb5-123">Image Editor for Icons</span></span>](/cpp/windows/image-editor-for-icons)
