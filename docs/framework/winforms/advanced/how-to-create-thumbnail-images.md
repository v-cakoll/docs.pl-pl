---
title: 'Instrukcje: Tworzenie obrazów miniatur'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thumbnail images [Windows Forms], creating
- images [Windows Forms], creating thumbnails
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
ms.openlocfilehash: 79b6258e7e6d7f16cc7a1e32a0c99dfe0eaeaa0c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144017"
---
# <a name="how-to-create-thumbnail-images"></a><span data-ttu-id="bd430-102">Instrukcje: Tworzenie obrazów miniatur</span><span class="sxs-lookup"><span data-stu-id="bd430-102">How to: Create Thumbnail Images</span></span>
<span data-ttu-id="bd430-103">Obraz miniatury jest mały wersję obrazu.</span><span class="sxs-lookup"><span data-stu-id="bd430-103">A thumbnail image is a small version of an image.</span></span> <span data-ttu-id="bd430-104">Możesz utworzyć obraz miniatury, przez wywołanie metody <xref:System.Drawing.Image.GetThumbnailImage%2A> metody <xref:System.Drawing.Image> obiektu.</span><span class="sxs-lookup"><span data-stu-id="bd430-104">You can create a thumbnail image by calling the <xref:System.Drawing.Image.GetThumbnailImage%2A> method of an <xref:System.Drawing.Image> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd430-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="bd430-105">Example</span></span>  
 <span data-ttu-id="bd430-106">Poniższy przykład tworzy <xref:System.Drawing.Image> obiekt z pliku JPG.</span><span class="sxs-lookup"><span data-stu-id="bd430-106">The following example constructs an <xref:System.Drawing.Image> object from a JPG file.</span></span> <span data-ttu-id="bd430-107">Oryginalny obraz ma 640 pikseli szerokości i wysokości 479 pikseli.</span><span class="sxs-lookup"><span data-stu-id="bd430-107">The original image has a width of 640 pixels and a height of 479 pixels.</span></span> <span data-ttu-id="bd430-108">Ten kod tworzy obraz miniatury, który ma 100 pikseli szerokości i wysokości 100 pikseli.</span><span class="sxs-lookup"><span data-stu-id="bd430-108">The code creates a thumbnail image that has a width of 100 pixels and a height of 100 pixels.</span></span>  
  
 <span data-ttu-id="bd430-109">Poniższa ilustracja przedstawia obraz miniatury.</span><span class="sxs-lookup"><span data-stu-id="bd430-109">The following illustration shows the thumbnail image.</span></span>  
  
 <span data-ttu-id="bd430-110">![Obraz miniatury](./media/thumbnail1.png "Thumbnail1")</span><span class="sxs-lookup"><span data-stu-id="bd430-110">![Thumbnail Image](./media/thumbnail1.png "Thumbnail1")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd430-111">W tym przykładzie metody wywołania zwrotnego jest zadeklarowana, ale nigdy używane.</span><span class="sxs-lookup"><span data-stu-id="bd430-111">In this example, a callback method is declared, but never used.</span></span> <span data-ttu-id="bd430-112">To obsługuje wszystkie wersje interfejsu GDI +.</span><span class="sxs-lookup"><span data-stu-id="bd430-112">This supports all versions of GDI+.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bd430-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="bd430-113">Compiling the Code</span></span>  
 <span data-ttu-id="bd430-114">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="bd430-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="bd430-115">Aby uruchomić przykład, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="bd430-115">To run the example, follow these steps:</span></span>  
  
1.  <span data-ttu-id="bd430-116">Tworzenie nowej aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="bd430-116">Create a new Windows Forms application.</span></span>  
  
2.  <span data-ttu-id="bd430-117">Dodaj przykładowy kod do formularza.</span><span class="sxs-lookup"><span data-stu-id="bd430-117">Add the example code to the form.</span></span>  
  
3.  <span data-ttu-id="bd430-118">Utwórz procedurę obsługi w formularzu <xref:System.Windows.Forms.Control.Paint> zdarzeń</span><span class="sxs-lookup"><span data-stu-id="bd430-118">Create a handler for the form's <xref:System.Windows.Forms.Control.Paint> event</span></span>  
  
4.  <span data-ttu-id="bd430-119">W <xref:System.Windows.Forms.Control.Paint> program obsługi, wywołanie `GetThumbnail` metody i przekazać `e` dla <xref:System.Windows.Forms.PaintEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="bd430-119">In the <xref:System.Windows.Forms.Control.Paint> handler, call the `GetThumbnail` method and pass `e` for <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
5.  <span data-ttu-id="bd430-120">Znajdź plik obrazu, który ma się miniaturę.</span><span class="sxs-lookup"><span data-stu-id="bd430-120">Find an image file that you want to make a thumbnail of.</span></span>  
  
6.  <span data-ttu-id="bd430-121">W `GetThumbnail` metody, określ ścieżkę i nazwę obrazu pliku.</span><span class="sxs-lookup"><span data-stu-id="bd430-121">In the `GetThumbnail` method, specify the path and file name to your image.</span></span>  
  
7.  <span data-ttu-id="bd430-122">Naciśnij klawisz F5, aby uruchomić przykład.</span><span class="sxs-lookup"><span data-stu-id="bd430-122">Press F5 to run the example.</span></span>  
  
     <span data-ttu-id="bd430-123">W formularzu pojawi się miniaturę 100 x 100.</span><span class="sxs-lookup"><span data-stu-id="bd430-123">A 100 by 100 thumbnail image appears on the form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd430-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd430-124">See also</span></span>

- [<span data-ttu-id="bd430-125">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="bd430-125">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="bd430-126">Praca z obrazami, mapami bitowymi, ikonami i metaplikami</span><span class="sxs-lookup"><span data-stu-id="bd430-126">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
