---
title: "Porady: wypełnianie kształtów teksturą obrazu"
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
helpviewer_keywords:
- images [Windows Forms], using with brushes
- bitmaps [Windows Forms], using texture
- shapes [Windows Forms], filling with images
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7b5ef87762b08daa973237e7b3da1068640e08bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a><span data-ttu-id="ce6ab-102">Porady: wypełnianie kształtów teksturą obrazu</span><span class="sxs-lookup"><span data-stu-id="ce6ab-102">How to: Fill a Shape with an Image Texture</span></span>
<span data-ttu-id="ce6ab-103">Możesz wpisać kształtu zamkniętego teksturą przy użyciu <xref:System.Drawing.Image> klasy i <xref:System.Drawing.TextureBrush> klasy.</span><span class="sxs-lookup"><span data-stu-id="ce6ab-103">You can fill a closed shape with a texture by using the <xref:System.Drawing.Image> class and the <xref:System.Drawing.TextureBrush> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce6ab-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ce6ab-104">Example</span></span>  
 <span data-ttu-id="ce6ab-105">Poniższy przykład wypełnia elipsę z obrazem.</span><span class="sxs-lookup"><span data-stu-id="ce6ab-105">The following example fills an ellipse with an image.</span></span> <span data-ttu-id="ce6ab-106">Tworzy kod <xref:System.Drawing.Image> obiekt, a następnie przekazuje adres, który <xref:System.Drawing.Image> obiektu jako argument <xref:System.Drawing.TextureBrush.%23ctor%2A> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="ce6ab-106">The code constructs an <xref:System.Drawing.Image> object, and then passes the address of that <xref:System.Drawing.Image> object as an argument to a <xref:System.Drawing.TextureBrush.%23ctor%2A> constructor.</span></span> <span data-ttu-id="ce6ab-107">Trzeci instrukcji skaluje obraz i czwarty instrukcji wypełnia elipsy powtarzane kopie skalowanie obrazu.</span><span class="sxs-lookup"><span data-stu-id="ce6ab-107">The third statement scales the image, and the fourth statement fills the ellipse with repeated copies of the scaled image.</span></span>  
  
 <span data-ttu-id="ce6ab-108">W poniższym kodzie <xref:System.Drawing.TextureBrush.Transform%2A> właściwość zawiera transformacji zastosowanych do obrazu przed narysowaniem go.</span><span class="sxs-lookup"><span data-stu-id="ce6ab-108">In the following code, the <xref:System.Drawing.TextureBrush.Transform%2A> property contains the transformation that is applied to the image before it is drawn.</span></span> <span data-ttu-id="ce6ab-109">Załóżmy, że oryginalny obraz ma 640 pikseli szerokości i wysokości 480 pikseli.</span><span class="sxs-lookup"><span data-stu-id="ce6ab-109">Assume that the original image has a width of 640 pixels and a height of 480 pixels.</span></span> <span data-ttu-id="ce6ab-110">Transformacja zmniejsza obraz do 75 × 75 przez ustawienie wartości skalowania poziomie i w pionie.</span><span class="sxs-lookup"><span data-stu-id="ce6ab-110">The transform shrinks the image to 75×75 by setting the horizontal and vertical scaling values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce6ab-111">W poniższym przykładzie rozmiar obrazu jest 75 × 75 i rozmiaru elipsy wynosi 150 x 250.</span><span class="sxs-lookup"><span data-stu-id="ce6ab-111">In the following example, the image size is 75×75, and the ellipse size is 150×250.</span></span> <span data-ttu-id="ce6ab-112">Ponieważ obrazu jest mniejszy niż elipsy, który jest jego wypełniania, elipsy jest rozmieszczany przy użyciu obrazu.</span><span class="sxs-lookup"><span data-stu-id="ce6ab-112">Because the image is smaller than the ellipse it is filling, the ellipse is tiled with the image.</span></span> <span data-ttu-id="ce6ab-113">Ustawianie widoku kafelków oznacza, że obraz jest powtarzany w poziomie i w pionie do granicy kształt zostanie osiągnięty.</span><span class="sxs-lookup"><span data-stu-id="ce6ab-113">Tiling means that the image is repeated horizontally and vertically until the boundary of the shape is reached.</span></span> <span data-ttu-id="ce6ab-114">Aby uzyskać więcej informacji na temat fragmentu, zobacz [porady: kafelka kształtu obrazem](../../../../docs/framework/winforms/advanced/how-to-tile-a-shape-with-an-image.md).</span><span class="sxs-lookup"><span data-stu-id="ce6ab-114">For more information about tiling, see [How to: Tile a Shape with an Image](../../../../docs/framework/winforms/advanced/how-to-tile-a-shape-with-an-image.md).</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ce6ab-115">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ce6ab-115">Compiling the Code</span></span>  
 <span data-ttu-id="ce6ab-116">Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ce6ab-116">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce6ab-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce6ab-117">See Also</span></span>  
 [<span data-ttu-id="ce6ab-118">Używanie pędzla do wypełniania kształtów</span><span class="sxs-lookup"><span data-stu-id="ce6ab-118">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
