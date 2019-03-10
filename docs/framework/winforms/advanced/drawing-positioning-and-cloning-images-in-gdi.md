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
ms.openlocfilehash: 9682c7be5956680556defd698cb97e8f4b1a7f50
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724671"
---
# <a name="drawing-positioning-and-cloning-images-in-gdi"></a><span data-ttu-id="2a5ba-102">Rysowanie, pozycjonowanie i klonowanie obrazów w GDI+</span><span class="sxs-lookup"><span data-stu-id="2a5ba-102">Drawing, Positioning, and Cloning Images in GDI+</span></span>
<span data-ttu-id="2a5ba-103">Możesz użyć <xref:System.Drawing.Bitmap> klasy, ładowania oraz wyświetlania obrazów rastrowych, na które mogą używać <xref:System.Drawing.Imaging.Metafile> klasy, ładowania oraz wyświetlania obrazów wektora.</span><span class="sxs-lookup"><span data-stu-id="2a5ba-103">You can use the <xref:System.Drawing.Bitmap> class to load and display raster images, and you can use the <xref:System.Drawing.Imaging.Metafile> class to load and display vector images.</span></span> <span data-ttu-id="2a5ba-104"><xref:System.Drawing.Bitmap> i <xref:System.Drawing.Imaging.Metafile> klasy dziedziczą <xref:System.Drawing.Image> klasy.</span><span class="sxs-lookup"><span data-stu-id="2a5ba-104">The <xref:System.Drawing.Bitmap> and <xref:System.Drawing.Imaging.Metafile> classes inherit from the <xref:System.Drawing.Image> class.</span></span> <span data-ttu-id="2a5ba-105">Aby wyświetlić obraz wektora, potrzebujesz wystąpienie <xref:System.Drawing.Graphics> klasy i <xref:System.Drawing.Imaging.Metafile>.</span><span class="sxs-lookup"><span data-stu-id="2a5ba-105">To display a vector image, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Imaging.Metafile>.</span></span> <span data-ttu-id="2a5ba-106">Aby wyświetlić obraz, potrzebujesz wystąpienie <xref:System.Drawing.Graphics> klasy i <xref:System.Drawing.Bitmap>.</span><span class="sxs-lookup"><span data-stu-id="2a5ba-106">To display a raster image, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Bitmap>.</span></span> <span data-ttu-id="2a5ba-107">Wystąpienie <xref:System.Drawing.Graphics> klasa udostępnia <xref:System.Drawing.Graphics.DrawImage%2A> metody, która odbiera <xref:System.Drawing.Imaging.Metafile> lub <xref:System.Drawing.Bitmap> jako argument.</span><span class="sxs-lookup"><span data-stu-id="2a5ba-107">The instance of the <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.DrawImage%2A> method, which receives the <xref:System.Drawing.Imaging.Metafile> or <xref:System.Drawing.Bitmap> as an argument.</span></span>  
  
## <a name="file-types-and-cloning"></a><span data-ttu-id="2a5ba-108">Typy plików i klonowanie</span><span class="sxs-lookup"><span data-stu-id="2a5ba-108">File Types and Cloning</span></span>  
 <span data-ttu-id="2a5ba-109">Poniższy przykład kodu pokazuje sposób tworzenia <xref:System.Drawing.Bitmap> z pliku Climber.jpg i wyświetla mapę bitową.</span><span class="sxs-lookup"><span data-stu-id="2a5ba-109">The following code example shows how to construct a <xref:System.Drawing.Bitmap> from the file Climber.jpg and displays the bitmap.</span></span> <span data-ttu-id="2a5ba-110">Punkt docelowy dla lewego górnego rogu obrazu (10, 10), jest określony w parametrach drugiego i trzeciego.</span><span class="sxs-lookup"><span data-stu-id="2a5ba-110">The destination point for the upper-left corner of the image, (10, 10), is specified in the second and third parameters.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#11)]  
  
 <span data-ttu-id="2a5ba-111">Poniższa ilustracja przedstawia obrazu.</span><span class="sxs-lookup"><span data-stu-id="2a5ba-111">The following illustration shows the image.</span></span>  
  
 <span data-ttu-id="2a5ba-112">![Obraz przykładowej](./media/aboutgdip03-art04.gif "AboutGdip03_Art04")</span><span class="sxs-lookup"><span data-stu-id="2a5ba-112">![Image Sample](./media/aboutgdip03-art04.gif "AboutGdip03_Art04")</span></span>  
  
 <span data-ttu-id="2a5ba-113">Można skonstruować <xref:System.Drawing.Bitmap> obiektów z wielu grafiki formaty plików: BMP, GIF, JPEG, EXIF, PNG, TIFF i IKONA.</span><span class="sxs-lookup"><span data-stu-id="2a5ba-113">You can construct <xref:System.Drawing.Bitmap> objects from a variety of graphics file formats: BMP, GIF, JPEG, EXIF, PNG, TIFF, and ICON.</span></span>  
  
 <span data-ttu-id="2a5ba-114">Poniższy przykład kodu pokazuje sposób tworzenia <xref:System.Drawing.Bitmap> obiekty z różnych typów plików, a następnie wyświetla map bitowych.</span><span class="sxs-lookup"><span data-stu-id="2a5ba-114">The following code example shows how to construct <xref:System.Drawing.Bitmap> objects from a variety of file types and then displays the bitmaps.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#12)]  
  
 <span data-ttu-id="2a5ba-115"><xref:System.Drawing.Bitmap> Klasa udostępnia <xref:System.Drawing.Bitmap.Clone%2A> metody użytej do utworzenia kopii istniejącego <xref:System.Drawing.Bitmap>.</span><span class="sxs-lookup"><span data-stu-id="2a5ba-115">The <xref:System.Drawing.Bitmap> class provides a <xref:System.Drawing.Bitmap.Clone%2A> method that you can use to make a copy of an existing <xref:System.Drawing.Bitmap>.</span></span> <span data-ttu-id="2a5ba-116"><xref:System.Drawing.Bitmap.Clone%2A> Metoda ma parametr prostokąta źródłowego używanego do określania część oryginalnego mapy bitowej, który chcesz skopiować.</span><span class="sxs-lookup"><span data-stu-id="2a5ba-116">The <xref:System.Drawing.Bitmap.Clone%2A> method has a source rectangle parameter that you can use to specify the portion of the original bitmap that you want to copy.</span></span> <span data-ttu-id="2a5ba-117">Poniższy przykład kodu pokazuje sposób tworzenia <xref:System.Drawing.Bitmap> przez Sklonowanie istniejącego w górnej połowie <xref:System.Drawing.Bitmap>.</span><span class="sxs-lookup"><span data-stu-id="2a5ba-117">The following code example shows how to create a <xref:System.Drawing.Bitmap> by cloning the top half of an existing <xref:System.Drawing.Bitmap>.</span></span> <span data-ttu-id="2a5ba-118">Następnie są rysowane oba obrazy.</span><span class="sxs-lookup"><span data-stu-id="2a5ba-118">Then both images are drawn.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#13)]  
  
 <span data-ttu-id="2a5ba-119">Poniższa ilustracja przedstawia dwa obrazy.</span><span class="sxs-lookup"><span data-stu-id="2a5ba-119">The following illustration shows the two images.</span></span>  
  
 <span data-ttu-id="2a5ba-120">![Przycinanie](./media/aboutgdip03-art05.gif "AboutGdip03_Art05")</span><span class="sxs-lookup"><span data-stu-id="2a5ba-120">![Cropping](./media/aboutgdip03-art05.gif "AboutGdip03_Art05")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a5ba-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a5ba-121">See also</span></span>
- [<span data-ttu-id="2a5ba-122">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="2a5ba-122">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="2a5ba-123">Instrukcje: Tworzenie obiektów graficznych do rysowania</span><span class="sxs-lookup"><span data-stu-id="2a5ba-123">How to: Create Graphics Objects for Drawing</span></span>](how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="2a5ba-124">Praca z obrazami, mapami bitowymi, ikonami i metaplikami</span><span class="sxs-lookup"><span data-stu-id="2a5ba-124">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
