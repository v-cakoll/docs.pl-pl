---
title: 'Instrukcje: Zmienianie kolorów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
ms.openlocfilehash: bf645cf88c4905cd5cf47c2a6c7af088fa428c8a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954668"
---
# <a name="how-to-shear-colors"></a><span data-ttu-id="14b9a-102">Instrukcje: Zmienianie kolorów</span><span class="sxs-lookup"><span data-stu-id="14b9a-102">How to: Shear Colors</span></span>
<span data-ttu-id="14b9a-103">Pochylanie zwiększa lub zmniejsza składnika koloru o kwotę proporcjonalną do innego składnika koloru.</span><span class="sxs-lookup"><span data-stu-id="14b9a-103">Shearing increases or decreases a color component by an amount proportional to another color component.</span></span> <span data-ttu-id="14b9a-104">Na przykład należy wziąć pod uwagę transformacji, w której składnik czerwony jest zwiększana o połowę wartość składnik niebieski.</span><span class="sxs-lookup"><span data-stu-id="14b9a-104">For example, consider the transformation where the red component is increased by one half the value of the blue component.</span></span> <span data-ttu-id="14b9a-105">W obszarze takie przekształcenia kolorów (0,2, 0,5, 1) staną się (0,7, 0,5, 1).</span><span class="sxs-lookup"><span data-stu-id="14b9a-105">Under such a transformation, the color (0.2, 0.5, 1) would become (0.7, 0.5, 1).</span></span> <span data-ttu-id="14b9a-106">Nowy składnik czerwony jest wymagane 0,2 + (1/2)(1) = 0,7.</span><span class="sxs-lookup"><span data-stu-id="14b9a-106">The new red component is 0.2 + (1/2)(1) = 0.7.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14b9a-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="14b9a-107">Example</span></span>  
 <span data-ttu-id="14b9a-108">Poniższy przykład tworzy <xref:System.Drawing.Image> obiektu na podstawie pliku ColorBars4.bmp.</span><span class="sxs-lookup"><span data-stu-id="14b9a-108">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars4.bmp.</span></span> <span data-ttu-id="14b9a-109">Następnie kod stosuje transformację nożycy opisane w poprzednim akapicie do każdego piksela na obrazie.</span><span class="sxs-lookup"><span data-stu-id="14b9a-109">Then the code applies the shearing transformation described in the preceding paragraph to each pixel in the image.</span></span>  
  
 <span data-ttu-id="14b9a-110">Na poniższej ilustracji przedstawiono oryginalny obraz po lewej stronie i pochylone obraz po prawej stronie:</span><span class="sxs-lookup"><span data-stu-id="14b9a-110">The following illustration shows the original image on the left and the sheared image on the right:</span></span> 
  
 ![Dwa pola z kolorowe paski side-by-side pokazujący oryginalnego obrazu i pochylone obrazu.](./media/how-to-shear-colors/original-image-sheared-image.png)  
  
 <span data-ttu-id="14b9a-112">W poniższej tabeli wymieniono wektorów kolor słupków cztery przed i po nim nożycy transformacji.</span><span class="sxs-lookup"><span data-stu-id="14b9a-112">The following table lists the color vectors for the four bars before and after the shearing transformation.</span></span>  
  
|<span data-ttu-id="14b9a-113">Oryginał</span><span class="sxs-lookup"><span data-stu-id="14b9a-113">Original</span></span>|<span data-ttu-id="14b9a-114">Pochylono</span><span class="sxs-lookup"><span data-stu-id="14b9a-114">Sheared</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="14b9a-115">(0, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="14b9a-115">(0, 0, 1, 1)</span></span>|<span data-ttu-id="14b9a-116">(0.5, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="14b9a-116">(0.5, 0, 1, 1)</span></span>|  
|<span data-ttu-id="14b9a-117">(0.5, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="14b9a-117">(0.5, 1, 0.5, 1)</span></span>|<span data-ttu-id="14b9a-118">(0.75, 1, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="14b9a-118">(0.75, 1, 0.5, 1)</span></span>|  
|<span data-ttu-id="14b9a-119">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="14b9a-119">(1, 1, 0, 1)</span></span>|<span data-ttu-id="14b9a-120">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="14b9a-120">(1, 1, 0, 1)</span></span>|  
|<span data-ttu-id="14b9a-121">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="14b9a-121">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="14b9a-122">(0.6, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="14b9a-122">(0.6, 0.4, 0.4, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.Misc3#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="14b9a-123">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="14b9a-123">Compiling the Code</span></span>  
 <span data-ttu-id="14b9a-124">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="14b9a-124">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="14b9a-125">Zastąp `ColorBars.bmp` przy użyciu nazwy obrazu i ścieżki prawidłowy w tym systemie.</span><span class="sxs-lookup"><span data-stu-id="14b9a-125">Replace `ColorBars.bmp` with an image name and path valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14b9a-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14b9a-126">See also</span></span>

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="14b9a-127">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="14b9a-127">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="14b9a-128">Ponowne kolorowanie obrazów</span><span class="sxs-lookup"><span data-stu-id="14b9a-128">Recoloring Images</span></span>](recoloring-images.md)
