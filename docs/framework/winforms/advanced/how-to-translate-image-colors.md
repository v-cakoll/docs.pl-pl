---
title: 'Porady: przesuwanie kolorów obrazu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], changing colors
- images [Windows Forms], changing colors
- image colors [Windows Forms]
ms.assetid: 2106fb9a-4d60-4dcf-9220-9f189a6c4d19
ms.openlocfilehash: 48f506f76ff6e9ca648822d073b6f6a852b9ca8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522539"
---
# <a name="how-to-translate-image-colors"></a><span data-ttu-id="772ad-102">Porady: przesuwanie kolorów obrazu</span><span class="sxs-lookup"><span data-stu-id="772ad-102">How to: Translate Image Colors</span></span>
<span data-ttu-id="772ad-103">Tłumaczenie dodaje wartość do przynajmniej jednej z czterech składowych.</span><span class="sxs-lookup"><span data-stu-id="772ad-103">A translation adds a value to one or more of the four color components.</span></span> <span data-ttu-id="772ad-104">Wpisów macierzy kolorów, które reprezentują tłumaczenia są podane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="772ad-104">The color matrix entries that represent translations are given in the following table.</span></span>  
  
|<span data-ttu-id="772ad-105">Składnik do tłumaczenia</span><span class="sxs-lookup"><span data-stu-id="772ad-105">Component to be translated</span></span>|<span data-ttu-id="772ad-106">Wpis macierzy</span><span class="sxs-lookup"><span data-stu-id="772ad-106">Matrix entry</span></span>|  
|--------------------------------|------------------|  
|<span data-ttu-id="772ad-107">czerwony</span><span class="sxs-lookup"><span data-stu-id="772ad-107">Red</span></span>|<span data-ttu-id="772ad-108">[4][0]</span><span class="sxs-lookup"><span data-stu-id="772ad-108">[4][0]</span></span>|  
|<span data-ttu-id="772ad-109">zielony</span><span class="sxs-lookup"><span data-stu-id="772ad-109">Green</span></span>|<span data-ttu-id="772ad-110">[4][1]</span><span class="sxs-lookup"><span data-stu-id="772ad-110">[4][1]</span></span>|  
|<span data-ttu-id="772ad-111">niebieski</span><span class="sxs-lookup"><span data-stu-id="772ad-111">Blue</span></span>|<span data-ttu-id="772ad-112">[4][2]</span><span class="sxs-lookup"><span data-stu-id="772ad-112">[4][2]</span></span>|  
|<span data-ttu-id="772ad-113">Alpha</span><span class="sxs-lookup"><span data-stu-id="772ad-113">Alpha</span></span>|<span data-ttu-id="772ad-114">[4][3]</span><span class="sxs-lookup"><span data-stu-id="772ad-114">[4][3]</span></span>|  
  
## <a name="example"></a><span data-ttu-id="772ad-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="772ad-115">Example</span></span>  
 <span data-ttu-id="772ad-116">Poniższy przykład tworzy <xref:System.Drawing.Image> obiektów z pliku ColorBars.bmp.</span><span class="sxs-lookup"><span data-stu-id="772ad-116">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars.bmp.</span></span> <span data-ttu-id="772ad-117">Następnie kod dodaje 0,75 do składnika czerwony każdego piksela obrazu.</span><span class="sxs-lookup"><span data-stu-id="772ad-117">Then the code adds 0.75 to the red component of each pixel in the image.</span></span> <span data-ttu-id="772ad-118">Oryginalnego obrazu jest rysowane obok przekształcone obrazu.</span><span class="sxs-lookup"><span data-stu-id="772ad-118">The original image is drawn alongside the transformed image.</span></span>  
  
 <span data-ttu-id="772ad-119">Na poniższej ilustracji przedstawiono oryginalnego obrazu po lewej stronie i przekształcony obraz po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="772ad-119">The following illustration shows the original image on the left and the transformed image on the right.</span></span>  
  
 <span data-ttu-id="772ad-120">![Translacja kolorów](../../../../docs/framework/winforms/advanced/media/colortrans2.png "colortrans2")</span><span class="sxs-lookup"><span data-stu-id="772ad-120">![Translate Colors](../../../../docs/framework/winforms/advanced/media/colortrans2.png "colortrans2")</span></span>  
  
 <span data-ttu-id="772ad-121">W poniższej tabeli wymieniono wektory kolor słupków cztery przed i po translacji czerwony.</span><span class="sxs-lookup"><span data-stu-id="772ad-121">The following table lists the color vectors for the four bars before and after the red translation.</span></span> <span data-ttu-id="772ad-122">Należy pamiętać, że maksymalna wartość dla składnika kolor jest 1, składnika czerwony w drugim wierszu nie zmienia się.</span><span class="sxs-lookup"><span data-stu-id="772ad-122">Note that because the maximum value for a color component is 1, the red component in the second row does not change.</span></span> <span data-ttu-id="772ad-123">(Podobnie, wartość minimalna dla składnika kolor jest 0).</span><span class="sxs-lookup"><span data-stu-id="772ad-123">(Similarly, the minimum value for a color component is 0.)</span></span>  
  
|<span data-ttu-id="772ad-124">Oryginał</span><span class="sxs-lookup"><span data-stu-id="772ad-124">Original</span></span>|<span data-ttu-id="772ad-125">Tłumaczenie</span><span class="sxs-lookup"><span data-stu-id="772ad-125">Translated</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="772ad-126">Czarne (0, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="772ad-126">Black (0, 0, 0, 1)</span></span>|<span data-ttu-id="772ad-127">(0.75, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="772ad-127">(0.75, 0, 0, 1)</span></span>|  
|<span data-ttu-id="772ad-128">Czerwony (1, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="772ad-128">Red (1, 0, 0, 1)</span></span>|<span data-ttu-id="772ad-129">(1, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="772ad-129">(1, 0, 0, 1)</span></span>|  
|<span data-ttu-id="772ad-130">Kolor zielony (0, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="772ad-130">Green (0, 1, 0, 1)</span></span>|<span data-ttu-id="772ad-131">(0.75, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="772ad-131">(0.75, 1, 0, 1)</span></span>|  
|<span data-ttu-id="772ad-132">Niebieski (0, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="772ad-132">Blue (0, 0, 1, 1)</span></span>|<span data-ttu-id="772ad-133">(0.75, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="772ad-133">(0.75, 0, 1, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.RecoloringImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.RecoloringImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="772ad-134">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="772ad-134">Compiling the Code</span></span>  
 <span data-ttu-id="772ad-135">Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="772ad-135">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="772ad-136">Zastąp `ColorBars.bmp` nazwę pliku obrazu oraz ścieżki, które są prawidłowe w tym systemie.</span><span class="sxs-lookup"><span data-stu-id="772ad-136">Replace `ColorBars.bmp` with an image file name and path that are valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="772ad-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="772ad-137">See Also</span></span>  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [<span data-ttu-id="772ad-138">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="772ad-138">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="772ad-139">Ponowne kolorowanie obrazów</span><span class="sxs-lookup"><span data-stu-id="772ad-139">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)
