---
title: 'Instrukcje: Obracanie, odzwierciedlanie i pochylanie obrazów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], reflecting
- images [Windows Forms], rotating
- images [Windows Forms], skewing
ms.assetid: a3bf97eb-63ed-425a-ba07-dcc65efb567c
ms.openlocfilehash: 505028c491228ffdf9c11d0c71dcd5e1afdc5103
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59114052"
---
# <a name="how-to-rotate-reflect-and-skew-images"></a><span data-ttu-id="3721e-102">Instrukcje: Obracanie, odzwierciedlanie i pochylanie obrazów</span><span class="sxs-lookup"><span data-stu-id="3721e-102">How to: Rotate, Reflect, and Skew Images</span></span>
<span data-ttu-id="3721e-103">Można obracanie, odzwierciedlanie i pochylanie obrazów, określając docelowe punkty narożników lewym, prawym górnym rogu i lewym dolnym oryginalnego obrazu.</span><span class="sxs-lookup"><span data-stu-id="3721e-103">You can rotate, reflect, and skew an image by specifying destination points for the upper-left, upper-right, and lower-left corners of the original image.</span></span> <span data-ttu-id="3721e-104">Docelowe trzy punkty określają affine — przekształcenia, które mapuje równoległobok oryginalny obraz prostokątny.</span><span class="sxs-lookup"><span data-stu-id="3721e-104">The three destination points determine an affine transformation that maps the original rectangular image to a parallelogram.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3721e-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="3721e-105">Example</span></span>  
 <span data-ttu-id="3721e-106">Załóżmy, że oryginalny obraz jest prostokąt z lewego górnego rogu w (0, 0), w prawym górnym rogu w (100, 0) i lewego dolnego rogu w (0, 50).</span><span class="sxs-lookup"><span data-stu-id="3721e-106">For example, suppose the original image is a rectangle with upper-left corner at (0, 0), upper-right corner at (100, 0), and lower-left corner at (0, 50).</span></span> <span data-ttu-id="3721e-107">Teraz załóżmy, że możesz mapować te trzy wskazuje docelowe punkty w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="3721e-107">Now suppose you map those three points to destination points as follows.</span></span>  
  
|<span data-ttu-id="3721e-108">Oryginalny punkt</span><span class="sxs-lookup"><span data-stu-id="3721e-108">Original point</span></span>|<span data-ttu-id="3721e-109">Docelowy punkt</span><span class="sxs-lookup"><span data-stu-id="3721e-109">Destination point</span></span>|  
|--------------------|-----------------------|  
|<span data-ttu-id="3721e-110">Lewa górna (0, 0)</span><span class="sxs-lookup"><span data-stu-id="3721e-110">Upper-left (0, 0)</span></span>|<span data-ttu-id="3721e-111">(200, 20)</span><span class="sxs-lookup"><span data-stu-id="3721e-111">(200, 20)</span></span>|  
|<span data-ttu-id="3721e-112">W prawym górnym (100, 0)</span><span class="sxs-lookup"><span data-stu-id="3721e-112">Upper-right (100, 0)</span></span>|<span data-ttu-id="3721e-113">(110, 100)</span><span class="sxs-lookup"><span data-stu-id="3721e-113">(110, 100)</span></span>|  
|<span data-ttu-id="3721e-114">Lewej dolnej (0, 50)</span><span class="sxs-lookup"><span data-stu-id="3721e-114">Lower-left (0, 50)</span></span>|<span data-ttu-id="3721e-115">(250, 30)</span><span class="sxs-lookup"><span data-stu-id="3721e-115">(250, 30)</span></span>|  
  
 <span data-ttu-id="3721e-116">Na poniższej ilustracji pokazuje oryginalny obraz i obraz, który mapowany do równoległobok.</span><span class="sxs-lookup"><span data-stu-id="3721e-116">The following illustration shows the original image and the image mapped to the parallelogram.</span></span> <span data-ttu-id="3721e-117">Oryginalny obraz ma zostały nierówne, zostaną uwzględnione, obracać i translacji.</span><span class="sxs-lookup"><span data-stu-id="3721e-117">The original image has been skewed, reflected, rotated, and translated.</span></span> <span data-ttu-id="3721e-118">Oś x wzdłuż górnej krawędzi oryginalny obraz jest mapowany na wierszu, który jest uruchamiany za pośrednictwem (200, 20) i (110, 100).</span><span class="sxs-lookup"><span data-stu-id="3721e-118">The x-axis along the top edge of the original image is mapped to the line that runs through (200, 20) and (110, 100).</span></span> <span data-ttu-id="3721e-119">Oś y wzdłuż lewej krawędzi oryginalny obraz jest mapowany na wierszu, który jest uruchamiany za pośrednictwem (200, 20) i (250, 30).</span><span class="sxs-lookup"><span data-stu-id="3721e-119">The y-axis along the left edge of the original image is mapped to the line that runs through (200, 20) and (250, 30).</span></span>  
  
 ![Oryginalny obraz i obraz, który mapowany do równoległobok.](./media/how-to-rotate-reflect-and-skew-images/reflected-skewed-rotated-illustration.gif)  
  
 <span data-ttu-id="3721e-121">Na poniższej ilustracji przedstawiono podobne przekształcenie zastosowane do obrazu fotograficzne:</span><span class="sxs-lookup"><span data-stu-id="3721e-121">The following illustration shows a similar transformation applied to a photographic image:</span></span>  
  
 ![Obraz obiekt climber i obraz mapowane na równoległobok.](./media/how-to-rotate-reflect-and-skew-images/reflected-skewed-rotated-photo.png)  
  
 <span data-ttu-id="3721e-123">Na poniższej ilustracji przedstawiono podobne przekształcenie zastosowane do metaplik:</span><span class="sxs-lookup"><span data-stu-id="3721e-123">The following illustration shows a similar transformation applied to a metafile:</span></span>  
  
 ![Ilustracja kształtów, tekstu i że mapowane na równoległobok.](./media/how-to-rotate-reflect-and-skew-images/reflected-skewed-rotated-metafile.png)  
  
 <span data-ttu-id="3721e-125">Poniższy przykład tworzy obrazy z pierwszą ilustracją.</span><span class="sxs-lookup"><span data-stu-id="3721e-125">The following example produces the images shown in the first illustration.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.WorkingWithImages#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3721e-126">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="3721e-126">Compiling the Code</span></span>  
 <span data-ttu-id="3721e-127">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs>`e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3721e-127">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="3721e-128">Upewnij się zastąpić `Stripes.bmp` ze ścieżką do obrazu, który jest prawidłowy w tym systemie.</span><span class="sxs-lookup"><span data-stu-id="3721e-128">Make sure to replace `Stripes.bmp` with the path to an image that is valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3721e-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3721e-129">See also</span></span>

- [<span data-ttu-id="3721e-130">Praca z obrazami, mapami bitowymi, ikonami i metaplikami</span><span class="sxs-lookup"><span data-stu-id="3721e-130">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
