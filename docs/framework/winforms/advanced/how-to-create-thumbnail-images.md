---
title: 'Porady: tworzenie obrazów miniatur'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thumbnail images [Windows Forms], creating
- images [Windows Forms], creating thumbnails
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
ms.openlocfilehash: 870ea223698e48438bd4dd08597d0a6ab79cec27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-thumbnail-images"></a><span data-ttu-id="be4a9-102">Porady: tworzenie obrazów miniatur</span><span class="sxs-lookup"><span data-stu-id="be4a9-102">How to: Create Thumbnail Images</span></span>
<span data-ttu-id="be4a9-103">Obraz miniatury jest małą wersję obrazu.</span><span class="sxs-lookup"><span data-stu-id="be4a9-103">A thumbnail image is a small version of an image.</span></span> <span data-ttu-id="be4a9-104">Obraz miniatury można utworzyć przez wywołanie metody <xref:System.Drawing.Image.GetThumbnailImage%2A> metody <xref:System.Drawing.Image> obiektu.</span><span class="sxs-lookup"><span data-stu-id="be4a9-104">You can create a thumbnail image by calling the <xref:System.Drawing.Image.GetThumbnailImage%2A> method of an <xref:System.Drawing.Image> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be4a9-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="be4a9-105">Example</span></span>  
 <span data-ttu-id="be4a9-106">Poniższy przykład tworzy <xref:System.Drawing.Image> obiekt z pliku JPG.</span><span class="sxs-lookup"><span data-stu-id="be4a9-106">The following example constructs an <xref:System.Drawing.Image> object from a JPG file.</span></span> <span data-ttu-id="be4a9-107">Oryginalny obraz ma 640 pikseli szerokości i wysokości 479 pikseli.</span><span class="sxs-lookup"><span data-stu-id="be4a9-107">The original image has a width of 640 pixels and a height of 479 pixels.</span></span> <span data-ttu-id="be4a9-108">Kod tworzy miniaturę, która zawiera 100 pikseli szerokości i wysokości 100 pikseli.</span><span class="sxs-lookup"><span data-stu-id="be4a9-108">The code creates a thumbnail image that has a width of 100 pixels and a height of 100 pixels.</span></span>  
  
 <span data-ttu-id="be4a9-109">Na poniższej ilustracji przedstawiono obraz miniatury.</span><span class="sxs-lookup"><span data-stu-id="be4a9-109">The following illustration shows the thumbnail image.</span></span>  
  
 <span data-ttu-id="be4a9-110">![Obraz miniatury](../../../../docs/framework/winforms/advanced/media/thumbnail1.png "Thumbnail1")</span><span class="sxs-lookup"><span data-stu-id="be4a9-110">![Thumbnail Image](../../../../docs/framework/winforms/advanced/media/thumbnail1.png "Thumbnail1")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be4a9-111">W tym przykładzie metoda wywołania zwrotnego jest zadeklarowana, ale nigdy używane.</span><span class="sxs-lookup"><span data-stu-id="be4a9-111">In this example, a callback method is declared, but never used.</span></span> <span data-ttu-id="be4a9-112">Obejmuje to obsługę wszystkich wersji GDI +.</span><span class="sxs-lookup"><span data-stu-id="be4a9-112">This supports all versions of GDI+.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="be4a9-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="be4a9-113">Compiling the Code</span></span>  
 <span data-ttu-id="be4a9-114">Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="be4a9-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="be4a9-115">Aby uruchomić przykład, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="be4a9-115">To run the example, follow these steps:</span></span>  
  
1.  <span data-ttu-id="be4a9-116">Tworzenie nowej aplikacji formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="be4a9-116">Create a new Windows Forms application.</span></span>  
  
2.  <span data-ttu-id="be4a9-117">Przykładowy kod należy dodać do formularza.</span><span class="sxs-lookup"><span data-stu-id="be4a9-117">Add the example code to the form.</span></span>  
  
3.  <span data-ttu-id="be4a9-118">Tworzenie programu obsługi dla formularza <xref:System.Windows.Forms.Control.Paint> zdarzeń</span><span class="sxs-lookup"><span data-stu-id="be4a9-118">Create a handler for the form's <xref:System.Windows.Forms.Control.Paint> event</span></span>  
  
4.  <span data-ttu-id="be4a9-119">W <xref:System.Windows.Forms.Control.Paint> obsługi, wywołaj `GetThumbnail` — metoda i przekazać `e` dla <xref:System.Windows.Forms.PaintEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="be4a9-119">In the <xref:System.Windows.Forms.Control.Paint> handler, call the `GetThumbnail` method and pass `e` for <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
5.  <span data-ttu-id="be4a9-120">Znajdź plik obrazu, który ma być miniaturę.</span><span class="sxs-lookup"><span data-stu-id="be4a9-120">Find an image file that you want to make a thumbnail of.</span></span>  
  
6.  <span data-ttu-id="be4a9-121">W `GetThumbnail` metody, określ ścieżkę i nazwę obrazu pliku.</span><span class="sxs-lookup"><span data-stu-id="be4a9-121">In the `GetThumbnail` method, specify the path and file name to your image.</span></span>  
  
7.  <span data-ttu-id="be4a9-122">Naciśnij klawisz F5, aby uruchomić w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="be4a9-122">Press F5 to run the example.</span></span>  
  
     <span data-ttu-id="be4a9-123">Obraz miniatury 100 na 100 pojawia się w formularzu.</span><span class="sxs-lookup"><span data-stu-id="be4a9-123">A 100 by 100 thumbnail image appears on the form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be4a9-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be4a9-124">See Also</span></span>  
 [<span data-ttu-id="be4a9-125">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="be4a9-125">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="be4a9-126">Praca z obrazami, mapami bitowymi, ikonami i metaplikami</span><span class="sxs-lookup"><span data-stu-id="be4a9-126">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
