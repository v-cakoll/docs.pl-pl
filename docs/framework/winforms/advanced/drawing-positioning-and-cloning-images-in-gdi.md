---
title: Rysowanie, pozycjonowanie i klonowanie obrazów w GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- raster images [Windows Forms]
- images [Windows Forms], positioning
- drawing [Windows Forms], images
- drawing [Windows Forms], raster images
- images [Windows Forms], cloning
- images [Windows Forms], drawing
- GDI+, drawing images
- GDI+, cloning images
- GDI+, positioning images
ms.assetid: 09f0c07a-19c0-43b4-90a2-862a10545ce8
ms.openlocfilehash: 5ff502884874e21e8f34acb2f15db4c651a0a273
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="drawing-positioning-and-cloning-images-in-gdi"></a><span data-ttu-id="8d117-102">Rysowanie, pozycjonowanie i klonowanie obrazów w GDI+</span><span class="sxs-lookup"><span data-stu-id="8d117-102">Drawing, Positioning, and Cloning Images in GDI+</span></span>
<span data-ttu-id="8d117-103">Można użyć <xref:System.Drawing.Bitmap> można użyć klasy ładowanie i wyświetlanie obrazów rastrowych, a <xref:System.Drawing.Imaging.Metafile> klasy ładowanie i wyświetlanie obrazów wektora.</span><span class="sxs-lookup"><span data-stu-id="8d117-103">You can use the <xref:System.Drawing.Bitmap> class to load and display raster images, and you can use the <xref:System.Drawing.Imaging.Metafile> class to load and display vector images.</span></span> <span data-ttu-id="8d117-104"><xref:System.Drawing.Bitmap> i <xref:System.Drawing.Imaging.Metafile> klasy dziedziczą <xref:System.Drawing.Image> klasy.</span><span class="sxs-lookup"><span data-stu-id="8d117-104">The <xref:System.Drawing.Bitmap> and <xref:System.Drawing.Imaging.Metafile> classes inherit from the <xref:System.Drawing.Image> class.</span></span> <span data-ttu-id="8d117-105">Do wyświetlania obrazu wektora, potrzebujesz wystąpienia <xref:System.Drawing.Graphics> klasy i <xref:System.Drawing.Imaging.Metafile>.</span><span class="sxs-lookup"><span data-stu-id="8d117-105">To display a vector image, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Imaging.Metafile>.</span></span> <span data-ttu-id="8d117-106">Aby wyświetlić obraz, należy wystąpienie <xref:System.Drawing.Graphics> klasy i <xref:System.Drawing.Bitmap>.</span><span class="sxs-lookup"><span data-stu-id="8d117-106">To display a raster image, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Bitmap>.</span></span> <span data-ttu-id="8d117-107">Wystąpienie <xref:System.Drawing.Graphics> klasa udostępnia <xref:System.Drawing.Graphics.DrawImage%2A> metodę, która odbiera <xref:System.Drawing.Imaging.Metafile> lub <xref:System.Drawing.Bitmap> jako argument.</span><span class="sxs-lookup"><span data-stu-id="8d117-107">The instance of the <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.DrawImage%2A> method, which receives the <xref:System.Drawing.Imaging.Metafile> or <xref:System.Drawing.Bitmap> as an argument.</span></span>  
  
## <a name="file-types-and-cloning"></a><span data-ttu-id="8d117-108">Typy plików i klonowania</span><span class="sxs-lookup"><span data-stu-id="8d117-108">File Types and Cloning</span></span>  
 <span data-ttu-id="8d117-109">Poniższy przykładowy kod przedstawia sposób tworzenia <xref:System.Drawing.Bitmap> z pliku Climber.jpg i wyświetla mapy bitowej.</span><span class="sxs-lookup"><span data-stu-id="8d117-109">The following code example shows how to construct a <xref:System.Drawing.Bitmap> from the file Climber.jpg and displays the bitmap.</span></span> <span data-ttu-id="8d117-110">Punkt docelowy dla lewego górnego rogu obrazu (10, 10), jest określona w parametrach drugiego i trzeciego.</span><span class="sxs-lookup"><span data-stu-id="8d117-110">The destination point for the upper-left corner of the image, (10, 10), is specified in the second and third parameters.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#11)]  
  
 <span data-ttu-id="8d117-111">Na poniższej ilustracji przedstawiono obrazu.</span><span class="sxs-lookup"><span data-stu-id="8d117-111">The following illustration shows the image.</span></span>  
  
 <span data-ttu-id="8d117-112">![Obraz przykładowej](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art04.gif "AboutGdip03_Art04")</span><span class="sxs-lookup"><span data-stu-id="8d117-112">![Image Sample](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art04.gif "AboutGdip03_Art04")</span></span>  
  
 <span data-ttu-id="8d117-113">Można utworzyć <xref:System.Drawing.Bitmap> obiektów z wielu grafiki formaty plików: BMP, GIF, JPEG, EXIF, PNG, TIFF i IKONA.</span><span class="sxs-lookup"><span data-stu-id="8d117-113">You can construct <xref:System.Drawing.Bitmap> objects from a variety of graphics file formats: BMP, GIF, JPEG, EXIF, PNG, TIFF, and ICON.</span></span>  
  
 <span data-ttu-id="8d117-114">Poniższy przykładowy kod przedstawia sposób tworzenia <xref:System.Drawing.Bitmap> obiekty z różnych typów plików, a następnie wyświetla map bitowych.</span><span class="sxs-lookup"><span data-stu-id="8d117-114">The following code example shows how to construct <xref:System.Drawing.Bitmap> objects from a variety of file types and then displays the bitmaps.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#12)]  
  
 <span data-ttu-id="8d117-115"><xref:System.Drawing.Bitmap> Klasa udostępnia <xref:System.Drawing.Bitmap.Clone%2A> metodę, która umożliwia wykonanie kopii istniejącego <xref:System.Drawing.Bitmap>.</span><span class="sxs-lookup"><span data-stu-id="8d117-115">The <xref:System.Drawing.Bitmap> class provides a <xref:System.Drawing.Bitmap.Clone%2A> method that you can use to make a copy of an existing <xref:System.Drawing.Bitmap>.</span></span> <span data-ttu-id="8d117-116"><xref:System.Drawing.Bitmap.Clone%2A> Metoda ma parametr prostokąt źródłowego, który służy do określenia część oryginalnego mapy bitowej, który chcesz skopiować.</span><span class="sxs-lookup"><span data-stu-id="8d117-116">The <xref:System.Drawing.Bitmap.Clone%2A> method has a source rectangle parameter that you can use to specify the portion of the original bitmap that you want to copy.</span></span> <span data-ttu-id="8d117-117">W poniższym przykładzie przedstawiono sposób tworzenia <xref:System.Drawing.Bitmap> w klonowania w górnej połowie istniejące <xref:System.Drawing.Bitmap>.</span><span class="sxs-lookup"><span data-stu-id="8d117-117">The following code example shows how to create a <xref:System.Drawing.Bitmap> by cloning the top half of an existing <xref:System.Drawing.Bitmap>.</span></span> <span data-ttu-id="8d117-118">Następnie oba obrazy są rysowane.</span><span class="sxs-lookup"><span data-stu-id="8d117-118">Then both images are drawn.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#13)]  
  
 <span data-ttu-id="8d117-119">Na poniższej ilustracji przedstawiono dwa obrazy.</span><span class="sxs-lookup"><span data-stu-id="8d117-119">The following illustration shows the two images.</span></span>  
  
 <span data-ttu-id="8d117-120">![Przycinanie](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art05.gif "AboutGdip03_Art05")</span><span class="sxs-lookup"><span data-stu-id="8d117-120">![Cropping](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art05.gif "AboutGdip03_Art05")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d117-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8d117-121">See Also</span></span>  
 [<span data-ttu-id="8d117-122">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="8d117-122">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="8d117-123">Instrukcje: tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="8d117-123">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="8d117-124">Praca z obrazami, mapami bitowymi, ikonami i metaplikami</span><span class="sxs-lookup"><span data-stu-id="8d117-124">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
