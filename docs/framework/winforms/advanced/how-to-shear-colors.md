---
title: 'Porady: zmienianie kolorów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
ms.openlocfilehash: 204f15ce44d5ad688be0ea9ac0fa4a90781b25dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-shear-colors"></a><span data-ttu-id="6cbfe-102">Porady: zmienianie kolorów</span><span class="sxs-lookup"><span data-stu-id="6cbfe-102">How to: Shear Colors</span></span>
<span data-ttu-id="6cbfe-103">Pochylanie zwiększa lub zmniejsza składnika kolor przez kwotę proporcjonalny do innego składnika kolorów.</span><span class="sxs-lookup"><span data-stu-id="6cbfe-103">Shearing increases or decreases a color component by an amount proportional to another color component.</span></span> <span data-ttu-id="6cbfe-104">Rozważmy na przykład przekształcania, gdzie składnika czerwony zwiększa się o połowę wartość składnika niebieski.</span><span class="sxs-lookup"><span data-stu-id="6cbfe-104">For example, consider the transformation where the red component is increased by one half the value of the blue component.</span></span> <span data-ttu-id="6cbfe-105">W takiej transformacji kolorów (0,2, 0,5, 1) może stać się (0,7, 0,5, 1).</span><span class="sxs-lookup"><span data-stu-id="6cbfe-105">Under such a transformation, the color (0.2, 0.5, 1) would become (0.7, 0.5, 1).</span></span> <span data-ttu-id="6cbfe-106">Nowy składnik red jest wymagane 0,2 + (1/2)(1) = 0,7.</span><span class="sxs-lookup"><span data-stu-id="6cbfe-106">The new red component is 0.2 + (1/2)(1) = 0.7.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cbfe-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="6cbfe-107">Example</span></span>  
 <span data-ttu-id="6cbfe-108">Poniższy przykład tworzy <xref:System.Drawing.Image> obiektów z pliku ColorBars4.bmp.</span><span class="sxs-lookup"><span data-stu-id="6cbfe-108">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars4.bmp.</span></span> <span data-ttu-id="6cbfe-109">Następnie kod stosuje transformację Ścinanie opisane w poprzednim akapicie do każdego piksela w obrazie.</span><span class="sxs-lookup"><span data-stu-id="6cbfe-109">Then the code applies the shearing transformation described in the preceding paragraph to each pixel in the image.</span></span>  
  
 <span data-ttu-id="6cbfe-110">Na poniższej ilustracji przedstawiono oryginalnego obrazu po lewej stronie i pochylone obraz po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="6cbfe-110">The following illustration shows the original image on the left and the sheared image on the right.</span></span>  
  
 <span data-ttu-id="6cbfe-111">![Zmienianie kolorów](../../../../docs/framework/winforms/advanced/media/colortrans6.png "colortrans6")</span><span class="sxs-lookup"><span data-stu-id="6cbfe-111">![Shear Colors](../../../../docs/framework/winforms/advanced/media/colortrans6.png "colortrans6")</span></span>  
  
 <span data-ttu-id="6cbfe-112">W poniższej tabeli wymieniono wektory kolor słupków cztery przed i po przekształceniu Ścinanie.</span><span class="sxs-lookup"><span data-stu-id="6cbfe-112">The following table lists the color vectors for the four bars before and after the shearing transformation.</span></span>  
  
|<span data-ttu-id="6cbfe-113">Oryginał</span><span class="sxs-lookup"><span data-stu-id="6cbfe-113">Original</span></span>|<span data-ttu-id="6cbfe-114">Ścięty</span><span class="sxs-lookup"><span data-stu-id="6cbfe-114">Sheared</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="6cbfe-115">(0, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="6cbfe-115">(0, 0, 1, 1)</span></span>|<span data-ttu-id="6cbfe-116">(0.5, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="6cbfe-116">(0.5, 0, 1, 1)</span></span>|  
|<span data-ttu-id="6cbfe-117">(0.5, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="6cbfe-117">(0.5, 1, 0.5, 1)</span></span>|<span data-ttu-id="6cbfe-118">(0.75, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="6cbfe-118">(0.75, 1, 0.5, 1)</span></span>|  
|<span data-ttu-id="6cbfe-119">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="6cbfe-119">(1, 1, 0, 1)</span></span>|<span data-ttu-id="6cbfe-120">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="6cbfe-120">(1, 1, 0, 1)</span></span>|  
|<span data-ttu-id="6cbfe-121">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="6cbfe-121">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="6cbfe-122">(0.6, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="6cbfe-122">(0.6, 0.4, 0.4, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.Misc3#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6cbfe-123">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6cbfe-123">Compiling the Code</span></span>  
 <span data-ttu-id="6cbfe-124">Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6cbfe-124">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="6cbfe-125">Zastąp `ColorBars.bmp` nazwę obrazu oraz ścieżki jest prawidłowy w tym systemie.</span><span class="sxs-lookup"><span data-stu-id="6cbfe-125">Replace `ColorBars.bmp` with an image name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cbfe-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6cbfe-126">See Also</span></span>  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [<span data-ttu-id="6cbfe-127">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6cbfe-127">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="6cbfe-128">Ponowne kolorowanie obrazów</span><span class="sxs-lookup"><span data-stu-id="6cbfe-128">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)
