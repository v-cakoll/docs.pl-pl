---
title: 'Instrukcje: Obracanie kolorów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], rotating
- examples [Windows Forms], rotating colors
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
ms.openlocfilehash: 6c4f41504911e94673707d99d804fad5b228599e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54503078"
---
# <a name="how-to-rotate-colors"></a><span data-ttu-id="485bd-102">Instrukcje: Obracanie kolorów</span><span class="sxs-lookup"><span data-stu-id="485bd-102">How to: Rotate Colors</span></span>
<span data-ttu-id="485bd-103">Obrót przestrzeni kolorów czterowymiarowego jest trudny do wizualizacji.</span><span class="sxs-lookup"><span data-stu-id="485bd-103">Rotation in a four-dimensional color space is difficult to visualize.</span></span> <span data-ttu-id="485bd-104">Firma Microsoft może ułatwić wizualizacji obrotu zgadzając się zachować jeden ze składników koloru, stałej.</span><span class="sxs-lookup"><span data-stu-id="485bd-104">We can make it easier to visualize rotation by agreeing to keep one of the color components fixed.</span></span> <span data-ttu-id="485bd-105">Załóżmy, że firma Microsoft zobowiązuje się do zachowania ustalony na 1 składnik alfa (całkowicie nieprzezroczyste).</span><span class="sxs-lookup"><span data-stu-id="485bd-105">Suppose we agree to keep the alpha component fixed at 1 (fully opaque).</span></span> <span data-ttu-id="485bd-106">Firma Microsoft następnie wizualizować przestrzeń kolorów trójwymiarowej za pomocą czerwonego, zielonego i niebieskiego osi, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="485bd-106">Then we can visualize a three-dimensional color space with red, green, and blue axes as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="485bd-107">![Ponowne kolorowanie](../../../../docs/framework/winforms/advanced/media/recoloring03.gif "recoloring03")</span><span class="sxs-lookup"><span data-stu-id="485bd-107">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring03.gif "recoloring03")</span></span>  
  
 <span data-ttu-id="485bd-108">Kolor, który można traktować jako punktów w przestrzeni 3D.</span><span class="sxs-lookup"><span data-stu-id="485bd-108">A color can be thought of as a point in 3-D space.</span></span> <span data-ttu-id="485bd-109">Na przykład punkt (1, 0, 0), w obszarze reprezentuje kolor czerwony, a punkt (0, 1, 0), w obszarze reprezentuje kolor zielony.</span><span class="sxs-lookup"><span data-stu-id="485bd-109">For example, the point (1, 0, 0) in space represents the color red, and the point (0, 1, 0) in space represents the color green.</span></span>  
  
 <span data-ttu-id="485bd-110">Poniższa ilustracja przedstawia się pod kątem 60 stopni na płaszczyźnie czerwony zielony oznacza obracanie kolorów (1, 0, 0).</span><span class="sxs-lookup"><span data-stu-id="485bd-110">The following illustration shows what it means to rotate the color (1, 0, 0) through an angle of 60 degrees in the Red-Green plane.</span></span> <span data-ttu-id="485bd-111">Obrót równolegle płaszczyzny do płaszczyzny czerwonego mogą być uważane za obrót wokół osi niebieski.</span><span class="sxs-lookup"><span data-stu-id="485bd-111">Rotation in a plane parallel to the Red-Green plane can be thought of as rotation about the blue axis.</span></span>  
  
 <span data-ttu-id="485bd-112">![Ponowne kolorowanie](../../../../docs/framework/winforms/advanced/media/recoloring04.gif "recoloring04")</span><span class="sxs-lookup"><span data-stu-id="485bd-112">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring04.gif "recoloring04")</span></span>  
  
 <span data-ttu-id="485bd-113">Na poniższej ilustracji pokazano, jak zainicjować macierzy kolorów do wykonania wymiany o każdej z trzech osi współrzędnych (czerwony, zielony, niebieski).</span><span class="sxs-lookup"><span data-stu-id="485bd-113">The following illustration shows how to initialize a color matrix to perform rotations about each of the three coordinate axes (red, green, blue).</span></span>  
  
 <span data-ttu-id="485bd-114">![Ponowne kolorowanie](../../../../docs/framework/winforms/advanced/media/recoloring05.gif "recoloring05")</span><span class="sxs-lookup"><span data-stu-id="485bd-114">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring05.gif "recoloring05")</span></span>  
  
## <a name="example"></a><span data-ttu-id="485bd-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="485bd-115">Example</span></span>  
 <span data-ttu-id="485bd-116">Poniższy przykład pobiera obraz, który jednego koloru (1, 0, 0.6) oraz będzie miało zastosowanie 60 stopni niebieski osi.</span><span class="sxs-lookup"><span data-stu-id="485bd-116">The following example takes an image that is all one color (1, 0, 0.6) and applies a 60-degree rotation about the blue axis.</span></span> <span data-ttu-id="485bd-117">Kąt obrotu przechwytywana się na płaszczyźnie, który jest zbliżony do płaszczyzny czerwony zielony.</span><span class="sxs-lookup"><span data-stu-id="485bd-117">The angle of the rotation is swept out in a plane that is parallel to the red-green plane.</span></span>  
  
 <span data-ttu-id="485bd-118">Poniższa ilustracja przedstawia oryginalny obraz po lewej i obracać kolor obraz po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="485bd-118">The following illustration shows the original image on the left and the color-rotated image on the right.</span></span>  
  
 <span data-ttu-id="485bd-119">![Obracanie kolorów](../../../../docs/framework/winforms/advanced/media/colortrans5.png "colortrans5")</span><span class="sxs-lookup"><span data-stu-id="485bd-119">![Rotate Colors](../../../../docs/framework/winforms/advanced/media/colortrans5.png "colortrans5")</span></span>  
  
 <span data-ttu-id="485bd-120">Na poniższej ilustracji przedstawiono wizualizację obracanie kolorów wykonywane w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="485bd-120">The following illustration shows a visualization of the color rotation performed in the following code.</span></span>  
  
 <span data-ttu-id="485bd-121">![Ponowne kolorowanie](../../../../docs/framework/winforms/advanced/media/recoloring06.gif "recoloring06")</span><span class="sxs-lookup"><span data-stu-id="485bd-121">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring06.gif "recoloring06")</span></span>  
  
 [!code-csharp[System.Drawing.RotateColors#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="485bd-122">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="485bd-122">Compiling the Code</span></span>  
 <span data-ttu-id="485bd-123">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="485bd-123">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="485bd-124">Zastąp `RotationInput.bmp` przy użyciu nazwy pliku obrazu i ścieżki prawidłowy w tym systemie.</span><span class="sxs-lookup"><span data-stu-id="485bd-124">Replace `RotationInput.bmp` with an image file name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="485bd-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="485bd-125">See also</span></span>
- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="485bd-126">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="485bd-126">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="485bd-127">Ponowne kolorowanie obrazów</span><span class="sxs-lookup"><span data-stu-id="485bd-127">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)
