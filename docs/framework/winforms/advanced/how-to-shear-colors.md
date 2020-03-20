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
ms.openlocfilehash: 825e5a90ebb0d9df3b894ce7bd353e917b676939
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142397"
---
# <a name="how-to-shear-colors"></a><span data-ttu-id="834ab-102">Porady: zmienianie kolorów</span><span class="sxs-lookup"><span data-stu-id="834ab-102">How to: Shear Colors</span></span>
<span data-ttu-id="834ab-103">Ścinanie zwiększa lub zmniejsza komponent koloru o kwotę proporcjonalną do innego komponentu koloru.</span><span class="sxs-lookup"><span data-stu-id="834ab-103">Shearing increases or decreases a color component by an amount proportional to another color component.</span></span> <span data-ttu-id="834ab-104">Rozważmy na przykład transformację, w której czerwony składnik jest zwiększany o połowę wartości niebieskiego składnika.</span><span class="sxs-lookup"><span data-stu-id="834ab-104">For example, consider the transformation where the red component is increased by one half the value of the blue component.</span></span> <span data-ttu-id="834ab-105">W ramach takiej transformacji kolor (0,2, 0,5, 1) stałby się (0,7, 0,5, 1).</span><span class="sxs-lookup"><span data-stu-id="834ab-105">Under such a transformation, the color (0.2, 0.5, 1) would become (0.7, 0.5, 1).</span></span> <span data-ttu-id="834ab-106">Nowy czerwony komponent to 0,2 + (1/2)(1) = 0,7.</span><span class="sxs-lookup"><span data-stu-id="834ab-106">The new red component is 0.2 + (1/2)(1) = 0.7.</span></span>  
  
## <a name="example"></a><span data-ttu-id="834ab-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="834ab-107">Example</span></span>  
 <span data-ttu-id="834ab-108">Poniższy przykład tworzy <xref:System.Drawing.Image> obiekt z pliku ColorBars4.bmp.</span><span class="sxs-lookup"><span data-stu-id="834ab-108">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars4.bmp.</span></span> <span data-ttu-id="834ab-109">Następnie kod stosuje transformację ścinania opisaną w poprzednim akapicie do każdego piksela obrazu.</span><span class="sxs-lookup"><span data-stu-id="834ab-109">Then the code applies the shearing transformation described in the preceding paragraph to each pixel in the image.</span></span>  
  
 <span data-ttu-id="834ab-110">Na poniższej ilustracji przedstawiono oryginalny obraz po lewej stronie i ścięty obraz po prawej stronie:</span><span class="sxs-lookup"><span data-stu-id="834ab-110">The following illustration shows the original image on the left and the sheared image on the right:</span></span>
  
 ![Dwa kwadraty z kolorowymi paskami obok siebie ilustrujące oryginalny obraz i ścięty obraz.](./media/how-to-shear-colors/original-image-sheared-image.png)  
  
 <span data-ttu-id="834ab-112">W poniższej tabeli wymieniono wektory kolorów dla czterech pasków przed i po transformacji ścinania.</span><span class="sxs-lookup"><span data-stu-id="834ab-112">The following table lists the color vectors for the four bars before and after the shearing transformation.</span></span>  
  
|<span data-ttu-id="834ab-113">Oryginał</span><span class="sxs-lookup"><span data-stu-id="834ab-113">Original</span></span>|<span data-ttu-id="834ab-114">Ścięty</span><span class="sxs-lookup"><span data-stu-id="834ab-114">Sheared</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="834ab-115">(0, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="834ab-115">(0, 0, 1, 1)</span></span>|<span data-ttu-id="834ab-116">(0.5, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="834ab-116">(0.5, 0, 1, 1)</span></span>|  
|<span data-ttu-id="834ab-117">(0.5, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="834ab-117">(0.5, 1, 0.5, 1)</span></span>|<span data-ttu-id="834ab-118">(0.75, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="834ab-118">(0.75, 1, 0.5, 1)</span></span>|  
|<span data-ttu-id="834ab-119">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="834ab-119">(1, 1, 0, 1)</span></span>|<span data-ttu-id="834ab-120">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="834ab-120">(1, 1, 0, 1)</span></span>|  
|<span data-ttu-id="834ab-121">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="834ab-121">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="834ab-122">(0.6, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="834ab-122">(0.6, 0.4, 0.4, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.Misc3#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="834ab-123">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="834ab-123">Compiling the Code</span></span>  
 <span data-ttu-id="834ab-124">Powyższy przykład jest przeznaczony do użytku z <xref:System.Windows.Forms.PaintEventArgs> `e`formularzami systemu Windows <xref:System.Windows.Forms.Control.Paint> i wymaga , który jest parametrem obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="834ab-124">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="834ab-125">Zastąp `ColorBars.bmp` nazwą obrazu i ścieżką prawidłową w systemie.</span><span class="sxs-lookup"><span data-stu-id="834ab-125">Replace `ColorBars.bmp` with an image name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="834ab-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="834ab-126">See also</span></span>

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="834ab-127">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="834ab-127">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="834ab-128">Ponowne kolorowanie obrazów</span><span class="sxs-lookup"><span data-stu-id="834ab-128">Recoloring Images</span></span>](recoloring-images.md)
