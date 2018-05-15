---
title: 'Porady: obracanie, odzwierciedlanie i pochylanie obrazów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], reflecting
- images [Windows Forms], rotating
- images [Windows Forms], skewing
ms.assetid: a3bf97eb-63ed-425a-ba07-dcc65efb567c
ms.openlocfilehash: 7f580b4d3016f1ecedc33302fe57caeec5698aeb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-rotate-reflect-and-skew-images"></a><span data-ttu-id="20ab1-102">Porady: obracanie, odzwierciedlanie i pochylanie obrazów</span><span class="sxs-lookup"><span data-stu-id="20ab1-102">How to: Rotate, Reflect, and Skew Images</span></span>
<span data-ttu-id="20ab1-103">Można obracanie, odzwierciedlanie i pochylanie obrazów, określając punkty docelowe narożników lewym górnym, prawym górnym i lewym dolnym oryginalnego obrazu.</span><span class="sxs-lookup"><span data-stu-id="20ab1-103">You can rotate, reflect, and skew an image by specifying destination points for the upper-left, upper-right, and lower-left corners of the original image.</span></span> <span data-ttu-id="20ab1-104">Punkty docelowe trzy określają affine — przekształcenia mapowanego oryginalnego obrazu prostokątne równoległobok.</span><span class="sxs-lookup"><span data-stu-id="20ab1-104">The three destination points determine an affine transformation that maps the original rectangular image to a parallelogram.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20ab1-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="20ab1-105">Example</span></span>  
 <span data-ttu-id="20ab1-106">Załóżmy na przykład, oryginalnego obrazu jest prostokąt z lewym górnym rogu na (0, 0), prawym górnym rogu na (100, 0) i lewym dolnym rogu na (0, 50).</span><span class="sxs-lookup"><span data-stu-id="20ab1-106">For example, suppose the original image is a rectangle with upper-left corner at (0, 0), upper-right corner at (100, 0), and lower-left corner at (0, 50).</span></span> <span data-ttu-id="20ab1-107">Teraz załóżmy, że możesz mapować te trzy wskazuje punkty docelowe w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="20ab1-107">Now suppose you map those three points to destination points as follows.</span></span>  
  
|<span data-ttu-id="20ab1-108">Oryginalny punkt</span><span class="sxs-lookup"><span data-stu-id="20ab1-108">Original point</span></span>|<span data-ttu-id="20ab1-109">Punkt docelowy</span><span class="sxs-lookup"><span data-stu-id="20ab1-109">Destination point</span></span>|  
|--------------------|-----------------------|  
|<span data-ttu-id="20ab1-110">Lewej górnej (0, 0)</span><span class="sxs-lookup"><span data-stu-id="20ab1-110">Upper-left (0, 0)</span></span>|<span data-ttu-id="20ab1-111">(200, 20)</span><span class="sxs-lookup"><span data-stu-id="20ab1-111">(200, 20)</span></span>|  
|<span data-ttu-id="20ab1-112">Prawy górny (100, 0)</span><span class="sxs-lookup"><span data-stu-id="20ab1-112">Upper-right (100, 0)</span></span>|<span data-ttu-id="20ab1-113">(110, 100)</span><span class="sxs-lookup"><span data-stu-id="20ab1-113">(110, 100)</span></span>|  
|<span data-ttu-id="20ab1-114">Lewym dolnym (0, 50)</span><span class="sxs-lookup"><span data-stu-id="20ab1-114">Lower-left (0, 50)</span></span>|<span data-ttu-id="20ab1-115">(250, 30)</span><span class="sxs-lookup"><span data-stu-id="20ab1-115">(250, 30)</span></span>|  
  
 <span data-ttu-id="20ab1-116">Na poniższej ilustracji przedstawiono oryginalnego obrazu i mapowane na równoległobok obrazu.</span><span class="sxs-lookup"><span data-stu-id="20ab1-116">The following illustration shows the original image and the image mapped to the parallelogram.</span></span> <span data-ttu-id="20ab1-117">Oryginalny obraz ma został niesymetryczna, zostaną uwzględnione obracać i translacji.</span><span class="sxs-lookup"><span data-stu-id="20ab1-117">The original image has been skewed, reflected, rotated, and translated.</span></span> <span data-ttu-id="20ab1-118">Oś x wzdłuż górnej krawędzi oryginalnego obrazu jest zamapowana na wiersz, który jest uruchamiany za pośrednictwem (200, 20) i (110, 100).</span><span class="sxs-lookup"><span data-stu-id="20ab1-118">The x-axis along the top edge of the original image is mapped to the line that runs through (200, 20) and (110, 100).</span></span> <span data-ttu-id="20ab1-119">Oś y wzdłuż lewej krawędzi oryginalnego obrazu jest zamapowana na wiersz, który jest uruchamiany za pośrednictwem (200, 20) i (250, 30).</span><span class="sxs-lookup"><span data-stu-id="20ab1-119">The y-axis along the left edge of the original image is mapped to the line that runs through (200, 20) and (250, 30).</span></span>  
  
 <span data-ttu-id="20ab1-120">![Rozkłada](../../../../docs/framework/winforms/advanced/media/stripes1.gif "Stripes1")</span><span class="sxs-lookup"><span data-stu-id="20ab1-120">![Stripes](../../../../docs/framework/winforms/advanced/media/stripes1.gif "Stripes1")</span></span>  
  
 <span data-ttu-id="20ab1-121">Na poniższej ilustracji przedstawiono transformację podobne do fotograficzne obrazu.</span><span class="sxs-lookup"><span data-stu-id="20ab1-121">The following illustration shows a similar transformation applied to a photographic image.</span></span>  
  
 <span data-ttu-id="20ab1-122">![Przekształcony obiekt Climber](../../../../docs/framework/winforms/advanced/media/transformedclimber.png "TransformedClimber")</span><span class="sxs-lookup"><span data-stu-id="20ab1-122">![Transformed Climber](../../../../docs/framework/winforms/advanced/media/transformedclimber.png "TransformedClimber")</span></span>  
  
 <span data-ttu-id="20ab1-123">Na poniższej ilustracji przedstawiono transformację podobne dotyczą metaplik.</span><span class="sxs-lookup"><span data-stu-id="20ab1-123">The following illustration shows a similar transformation applied to a metafile.</span></span>  
  
 <span data-ttu-id="20ab1-124">![Przekształcone metaplik](../../../../docs/framework/winforms/advanced/media/transformedmetafile.png "TransformedMetafile")</span><span class="sxs-lookup"><span data-stu-id="20ab1-124">![Transformed Metafile](../../../../docs/framework/winforms/advanced/media/transformedmetafile.png "TransformedMetafile")</span></span>  
  
 <span data-ttu-id="20ab1-125">Poniższy przykład tworzy obrazy ilustracją pierwszy.</span><span class="sxs-lookup"><span data-stu-id="20ab1-125">The following example produces the images shown in the first illustration.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="20ab1-126">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="20ab1-126">Compiling the Code</span></span>  
 <span data-ttu-id="20ab1-127">Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="20ab1-127">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="20ab1-128">Upewnij się zastąpić `Stripes.bmp` ze ścieżką do obrazu, który jest prawidłowy w tym systemie.</span><span class="sxs-lookup"><span data-stu-id="20ab1-128">Make sure to replace `Stripes.bmp` with the path to an image that is valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20ab1-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="20ab1-129">See Also</span></span>  
 [<span data-ttu-id="20ab1-130">Praca z obrazami, mapami bitowymi, ikonami i metaplikami</span><span class="sxs-lookup"><span data-stu-id="20ab1-130">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
