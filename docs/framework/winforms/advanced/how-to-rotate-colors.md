---
title: 'Porady: obracanie kolorów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], rotating
- examples [Windows Forms], rotating colors
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
ms.openlocfilehash: 8d2717dd7b819e963126072279b361fda02188bc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111338"
---
# <a name="how-to-rotate-colors"></a><span data-ttu-id="4a94a-102">Porady: obracanie kolorów</span><span class="sxs-lookup"><span data-stu-id="4a94a-102">How to: Rotate Colors</span></span>
<span data-ttu-id="4a94a-103">Obrót w czterowymiarowej przestrzeni kolorów jest trudny do wizualizacji.</span><span class="sxs-lookup"><span data-stu-id="4a94a-103">Rotation in a four-dimensional color space is difficult to visualize.</span></span> <span data-ttu-id="4a94a-104">Możemy ułatwić wizualizację obrotu, zgadzając się na utrzymanie jednego ze składników koloru na stałym miejscu.</span><span class="sxs-lookup"><span data-stu-id="4a94a-104">We can make it easier to visualize rotation by agreeing to keep one of the color components fixed.</span></span> <span data-ttu-id="4a94a-105">Załóżmy, że zgadzamy się, aby utrzymać składnik alfa stały na 1 (całkowicie nieprzezroczyste).</span><span class="sxs-lookup"><span data-stu-id="4a94a-105">Suppose we agree to keep the alpha component fixed at 1 (fully opaque).</span></span> <span data-ttu-id="4a94a-106">Następnie możemy wizualizować trójwymiarową przestrzeń kolorów z czerwonymi, zielonymi i niebieskimi osiami, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="4a94a-106">Then we can visualize a three-dimensional color space with red, green, and blue axes as shown in the following illustration.</span></span>  
  
 ![Ilustracja przedstawiająca obrót z osiami czerwonymi, zielonymi i niebieskimi.](./media/how-to-rotate-colors/rotation-red-green-blue-axes.gif)  
  
 <span data-ttu-id="4a94a-108">Kolor można traktować jako punkt w przestrzeni 3D.</span><span class="sxs-lookup"><span data-stu-id="4a94a-108">A color can be thought of as a point in 3D space.</span></span> <span data-ttu-id="4a94a-109">Na przykład punkt (1, 0, 0) w przestrzeni reprezentuje kolor czerwony, a punkt (0, 1, 0) w przestrzeni reprezentuje kolor zielony.</span><span class="sxs-lookup"><span data-stu-id="4a94a-109">For example, the point (1, 0, 0) in space represents the color red, and the point (0, 1, 0) in space represents the color green.</span></span>  
  
 <span data-ttu-id="4a94a-110">Na poniższej ilustracji pokazano, co to znaczy obrócić kolor (1, 0, 0) pod kątem 60 stopni w płaszczyźnie czerwono-zielonej.</span><span class="sxs-lookup"><span data-stu-id="4a94a-110">The following illustration shows what it means to rotate the color (1, 0, 0) through an angle of 60 degrees in the Red-Green plane.</span></span> <span data-ttu-id="4a94a-111">Obrót w płaszczyźnie równoległej do płaszczyzny czerwono-zielonej można traktować jako obrót wokół niebieskiej osi.</span><span class="sxs-lookup"><span data-stu-id="4a94a-111">Rotation in a plane parallel to the Red-Green plane can be thought of as rotation about the blue axis.</span></span>  
  
 ![Ilustracja przedstawiająca obrót wokół niebieskiej osi.](./media/how-to-rotate-colors/rotation-about-blue-axis.gif)  
  
 <span data-ttu-id="4a94a-113">Na poniższej ilustracji pokazano, jak zainicjować macierz kolorów w celu wykonywania obrotów dotyczących każdej z trzech osi współrzędnych (czerwonej, zielonej, niebieskiej):</span><span class="sxs-lookup"><span data-stu-id="4a94a-113">The following illustration shows how to initialize a color matrix to perform rotations about each of the three coordinate axes (red, green, blue):</span></span>  
  
 ![Zainicjować macierz kolorów, aby wykonać obroty około trzech osi.](./media/how-to-rotate-colors/rotation-about-three-axes.gif)  
  
## <a name="example"></a><span data-ttu-id="4a94a-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="4a94a-115">Example</span></span>  
 <span data-ttu-id="4a94a-116">W poniższym przykładzie obraz, który jest cały jeden kolor (1, 0, 0,6) i stosuje obrót 60 stopni wokół niebieskiej osi.</span><span class="sxs-lookup"><span data-stu-id="4a94a-116">The following example takes an image that is all one color (1, 0, 0.6) and applies a 60-degree rotation about the blue axis.</span></span> <span data-ttu-id="4a94a-117">Kąt obrotu jest zmieciony w płaszczyźnie równoległej do płaszczyzny czerwono-zielonej.</span><span class="sxs-lookup"><span data-stu-id="4a94a-117">The angle of the rotation is swept out in a plane that is parallel to the red-green plane.</span></span>  
  
 <span data-ttu-id="4a94a-118">Na poniższej ilustracji przedstawiono oryginalny obraz po lewej stronie i obrócony kolor obrazu po prawej stronie:</span><span class="sxs-lookup"><span data-stu-id="4a94a-118">The following illustration shows the original image on the left and the color-rotated image on the right:</span></span>  
  
 ![Ilustracja przedstawiająca oryginalny obraz i obraz obrócony kolorem.](./media/how-to-rotate-colors/original-color-rotated-images.png)  
  
 <span data-ttu-id="4a94a-120">Na poniższej ilustracji przedstawiono wizualizację obrotu kolorów wykonaną w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="4a94a-120">The following illustration shows a visualization of the color rotation performed in the following code:</span></span>
  
 ![Ilustracja przedstawiająca wizualizację obrotu kolorów.](./media/how-to-rotate-colors/visualization-color-rotation.gif)  
  
 [!code-csharp[System.Drawing.RotateColors#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4a94a-122">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="4a94a-122">Compiling the Code</span></span>  
 <span data-ttu-id="4a94a-123">Powyższy przykład jest przeznaczony do użytku z <xref:System.Windows.Forms.PaintEventArgs> `e`formularzami systemu Windows <xref:System.Windows.Forms.Control.Paint> i wymaga , który jest parametrem obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4a94a-123">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="4a94a-124">Zastąp `RotationInput.bmp` nazwą pliku obrazu i ścieżką prawidłową w systemie.</span><span class="sxs-lookup"><span data-stu-id="4a94a-124">Replace `RotationInput.bmp` with an image file name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a94a-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4a94a-125">See also</span></span>

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="4a94a-126">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4a94a-126">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="4a94a-127">Ponowne kolorowanie obrazów</span><span class="sxs-lookup"><span data-stu-id="4a94a-127">Recoloring Images</span></span>](recoloring-images.md)
