---
title: "Porady: renderowanie obrazów za pomocą GDI+"
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
- images [Windows Forms], creating
- GDI+, rendering existing images
ms.assetid: c128b79a-3e31-47d8-9e66-3470f570a056
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a6edc48c93f83611bdc2be5b7398ab0abe843407
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-render-images-with-gdi"></a><span data-ttu-id="ec67b-102">Porady: renderowanie obrazów za pomocą GDI+</span><span class="sxs-lookup"><span data-stu-id="ec67b-102">How to: Render Images with GDI+</span></span>
<span data-ttu-id="ec67b-103">Można użyć [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] renderowanie obrazów, które istnieje jako pliki w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ec67b-103">You can use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to render images that exist as files in your applications.</span></span> <span data-ttu-id="ec67b-104">Można to zrobić, tworząc nowy obiekt <xref:System.Drawing.Image> klasy (takich jak <xref:System.Drawing.Bitmap>), tworzenie <xref:System.Drawing.Graphics> obiekt, który odwołuje się do powierzchni rysowania, którego chcesz użyć i wywoływania <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="ec67b-104">You do this by creating a new object of an <xref:System.Drawing.Image> class (such as <xref:System.Drawing.Bitmap>), creating a <xref:System.Drawing.Graphics> object that refers to the drawing surface you want to use, and calling the <xref:System.Drawing.Graphics.DrawImage%2A> method of the <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="ec67b-105">Obraz będą rysowane na powierzchni rysowania reprezentowany przez klasę grafiki.</span><span class="sxs-lookup"><span data-stu-id="ec67b-105">The image will be painted onto the drawing surface represented by the graphics class.</span></span> <span data-ttu-id="ec67b-106">Użyj edytora obrazów do tworzenia i edytowania plików obrazów w czasie projektowania i renderowania je za pomocą [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ec67b-106">You can use the Image Editor to create and edit image files at design time, and render them with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] at run time.</span></span> <span data-ttu-id="ec67b-107">Aby uzyskać więcej informacji, zobacz [edytor obrazów dla ikon](/cpp/windows/image-editor-for-icons).</span><span class="sxs-lookup"><span data-stu-id="ec67b-107">For more information, see [Image Editor for Icons](/cpp/windows/image-editor-for-icons).</span></span>  
  
### <a name="to-render-an-image-with-gdi"></a><span data-ttu-id="ec67b-108">Aby renderować obraz z GDI +</span><span class="sxs-lookup"><span data-stu-id="ec67b-108">To render an image with GDI+</span></span>  
  
1.  <span data-ttu-id="ec67b-109">Utwórz obiekt reprezentujący obraz, który chcesz wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="ec67b-109">Create an object representing the image you want to display.</span></span> <span data-ttu-id="ec67b-110">Ten obiekt musi być elementem członkowskim klasy, która dziedziczy po <xref:System.Drawing.Image>, takich jak <xref:System.Drawing.Bitmap> lub <xref:System.Drawing.Imaging.Metafile>.</span><span class="sxs-lookup"><span data-stu-id="ec67b-110">This object must be a member of a class that inherits from <xref:System.Drawing.Image>, such as <xref:System.Drawing.Bitmap> or <xref:System.Drawing.Imaging.Metafile>.</span></span> <span data-ttu-id="ec67b-111">Przykład przedstawiono:</span><span class="sxs-lookup"><span data-stu-id="ec67b-111">An example is shown:</span></span>  
  
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
  
2.  <span data-ttu-id="ec67b-112">Utwórz <xref:System.Drawing.Graphics> obiekt, który reprezentuje powierzchni rysowania, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="ec67b-112">Create a <xref:System.Drawing.Graphics> object that represents the drawing surface you want to use.</span></span> <span data-ttu-id="ec67b-113">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie obiektów graficznych do rysowania](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="ec67b-113">For more information, see [How to: Create Graphics Objects for Drawing](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
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
  
3.  <span data-ttu-id="ec67b-114">Wywołanie <xref:System.Drawing.Graphics.DrawImage%2A> grafiki obiektu do renderowania obrazu.</span><span class="sxs-lookup"><span data-stu-id="ec67b-114">Call the <xref:System.Drawing.Graphics.DrawImage%2A> of your graphics object to render the image.</span></span> <span data-ttu-id="ec67b-115">Należy określić obraz, który ma być rysowany i współrzędne, w którym ma być rysowany.</span><span class="sxs-lookup"><span data-stu-id="ec67b-115">You must specify both the image to be drawn, and the coordinates where it is to be drawn.</span></span>  
  
    ```vb  
    g.DrawImage(myBitmap, 1, 1)  
    ```  
  
    ```csharp  
    g.DrawImage(myBitmap, 1, 1);  
    ```  
  
    ```cpp  
    g->DrawImage(myBitmap, 1, 1);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ec67b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ec67b-116">See Also</span></span>  
 [<span data-ttu-id="ec67b-117">Wprowadzenie do programowania grafiki</span><span class="sxs-lookup"><span data-stu-id="ec67b-117">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="ec67b-118">Instrukcje: tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="ec67b-118">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="ec67b-119">Pióra, linie i prostokąty w GDI+</span><span class="sxs-lookup"><span data-stu-id="ec67b-119">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)  
 [<span data-ttu-id="ec67b-120">Instrukcje: rysowanie tekstu w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ec67b-120">How to: Draw Text on a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-on-a-windows-form.md)  
 [<span data-ttu-id="ec67b-121">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ec67b-121">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="ec67b-122">Linie rysunku lub zamkniętych figur</span><span class="sxs-lookup"><span data-stu-id="ec67b-122">Drawing Lines or Closed Figures</span></span>](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)  
 [<span data-ttu-id="ec67b-123">Edytor obrazów dla ikon</span><span class="sxs-lookup"><span data-stu-id="ec67b-123">Image Editor for Icons</span></span>](/cpp/windows/image-editor-for-icons)
