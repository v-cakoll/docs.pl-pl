---
title: 'Instrukcje: Wypełnianie kształtów teksturą obrazu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using with brushes
- bitmaps [Windows Forms], using texture
- shapes [Windows Forms], filling with images
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
ms.openlocfilehash: 42c456137f84c6fa657ba5a09727eae052a45376
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911687"
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a><span data-ttu-id="1d470-102">Instrukcje: Wypełnianie kształtów teksturą obrazu</span><span class="sxs-lookup"><span data-stu-id="1d470-102">How to: Fill a Shape with an Image Texture</span></span>
<span data-ttu-id="1d470-103">Można wypełnić zamknięty kształt teksturą, używając <xref:System.Drawing.Image> klasy <xref:System.Drawing.TextureBrush> i klasy.</span><span class="sxs-lookup"><span data-stu-id="1d470-103">You can fill a closed shape with a texture by using the <xref:System.Drawing.Image> class and the <xref:System.Drawing.TextureBrush> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d470-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d470-104">Example</span></span>  
 <span data-ttu-id="1d470-105">Poniższy przykład wypełnia wielokropek obrazem.</span><span class="sxs-lookup"><span data-stu-id="1d470-105">The following example fills an ellipse with an image.</span></span> <span data-ttu-id="1d470-106">Kod konstruuje <xref:System.Drawing.Image> obiekt, a następnie przekazuje adres tego <xref:System.Drawing.Image> obiektu <xref:System.Drawing.TextureBrush.%23ctor%2A> jako argument do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="1d470-106">The code constructs an <xref:System.Drawing.Image> object, and then passes the address of that <xref:System.Drawing.Image> object as an argument to a <xref:System.Drawing.TextureBrush.%23ctor%2A> constructor.</span></span> <span data-ttu-id="1d470-107">Trzecia instrukcja skaluje obraz, a czwarta instrukcja wypełnia elipsę powtarzanymi kopiami obrazu skalowanego.</span><span class="sxs-lookup"><span data-stu-id="1d470-107">The third statement scales the image, and the fourth statement fills the ellipse with repeated copies of the scaled image.</span></span>  
  
 <span data-ttu-id="1d470-108">W poniższym kodzie <xref:System.Drawing.TextureBrush.Transform%2A> Właściwość zawiera transformację, która została zastosowana do obrazu przed jego narysowaniem.</span><span class="sxs-lookup"><span data-stu-id="1d470-108">In the following code, the <xref:System.Drawing.TextureBrush.Transform%2A> property contains the transformation that is applied to the image before it is drawn.</span></span> <span data-ttu-id="1d470-109">Załóżmy, że oryginalny obraz ma szerokość 640 pikseli i wysokość 480 pikseli.</span><span class="sxs-lookup"><span data-stu-id="1d470-109">Assume that the original image has a width of 640 pixels and a height of 480 pixels.</span></span> <span data-ttu-id="1d470-110">Transformacja zmniejsza obraz do 75 × 75, ustawiając wartości skalowania w poziomie i w pionie.</span><span class="sxs-lookup"><span data-stu-id="1d470-110">The transform shrinks the image to 75×75 by setting the horizontal and vertical scaling values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1d470-111">W poniższym przykładzie rozmiar obrazu wynosi 75 × 75, a rozmiar elipsy wynosi 150 × 250.</span><span class="sxs-lookup"><span data-stu-id="1d470-111">In the following example, the image size is 75×75, and the ellipse size is 150×250.</span></span> <span data-ttu-id="1d470-112">Ponieważ obraz jest mniejszy niż Elipsa, która jest wypełniana, wielokropek jest rozmieszczany z obrazem.</span><span class="sxs-lookup"><span data-stu-id="1d470-112">Because the image is smaller than the ellipse it is filling, the ellipse is tiled with the image.</span></span> <span data-ttu-id="1d470-113">Dzielenie oznacza, że obraz jest powtarzany w poziomie i w pionie do momentu osiągnięcia granicy kształtu.</span><span class="sxs-lookup"><span data-stu-id="1d470-113">Tiling means that the image is repeated horizontally and vertically until the boundary of the shape is reached.</span></span> <span data-ttu-id="1d470-114">Aby uzyskać więcej informacji na temat dzielenia [, zobacz How to: Tworzenie kafelka kształtu przy użyciu](how-to-tile-a-shape-with-an-image.md)obrazu.</span><span class="sxs-lookup"><span data-stu-id="1d470-114">For more information about tiling, see [How to: Tile a Shape with an Image](how-to-tile-a-shape-with-an-image.md).</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1d470-115">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="1d470-115">Compiling the Code</span></span>  
 <span data-ttu-id="1d470-116">Poprzedni przykład jest przeznaczony do użycia z Windows Forms i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który <xref:System.Windows.Forms.Control.Paint> jest parametrem programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1d470-116">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d470-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d470-117">See also</span></span>

- [<span data-ttu-id="1d470-118">Używanie pędzla do wypełniania kształtów</span><span class="sxs-lookup"><span data-stu-id="1d470-118">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
