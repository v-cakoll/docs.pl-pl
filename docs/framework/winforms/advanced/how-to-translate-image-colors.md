---
title: 'Instrukcje: Przesuwanie kolorów obrazu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], changing colors
- images [Windows Forms], changing colors
- image colors [Windows Forms]
ms.assetid: 2106fb9a-4d60-4dcf-9220-9f189a6c4d19
ms.openlocfilehash: 04e61383ef79b17ea6e1523588cd9593ec9b082c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59132642"
---
# <a name="how-to-translate-image-colors"></a><span data-ttu-id="54fde-102">Instrukcje: Przesuwanie kolorów obrazu</span><span class="sxs-lookup"><span data-stu-id="54fde-102">How to: Translate Image Colors</span></span>
<span data-ttu-id="54fde-103">Tłumaczenie dodaje wartość do przynajmniej jednej z czterech składowych.</span><span class="sxs-lookup"><span data-stu-id="54fde-103">A translation adds a value to one or more of the four color components.</span></span> <span data-ttu-id="54fde-104">Wpisów macierzy kolorów, które reprezentują tłumaczenia są podane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="54fde-104">The color matrix entries that represent translations are given in the following table.</span></span>  
  
|<span data-ttu-id="54fde-105">Składnik ma zostać poddany translacji</span><span class="sxs-lookup"><span data-stu-id="54fde-105">Component to be translated</span></span>|<span data-ttu-id="54fde-106">Wpis macierzy</span><span class="sxs-lookup"><span data-stu-id="54fde-106">Matrix entry</span></span>|  
|--------------------------------|------------------|  
|<span data-ttu-id="54fde-107">Czerwony</span><span class="sxs-lookup"><span data-stu-id="54fde-107">Red</span></span>|<span data-ttu-id="54fde-108">[4][0]</span><span class="sxs-lookup"><span data-stu-id="54fde-108">[4][0]</span></span>|  
|<span data-ttu-id="54fde-109">Zielony</span><span class="sxs-lookup"><span data-stu-id="54fde-109">Green</span></span>|<span data-ttu-id="54fde-110">[4][1]</span><span class="sxs-lookup"><span data-stu-id="54fde-110">[4][1]</span></span>|  
|<span data-ttu-id="54fde-111">Niebieski</span><span class="sxs-lookup"><span data-stu-id="54fde-111">Blue</span></span>|<span data-ttu-id="54fde-112">[4][2]</span><span class="sxs-lookup"><span data-stu-id="54fde-112">[4][2]</span></span>|  
|<span data-ttu-id="54fde-113">alfa</span><span class="sxs-lookup"><span data-stu-id="54fde-113">Alpha</span></span>|<span data-ttu-id="54fde-114">[4][3]</span><span class="sxs-lookup"><span data-stu-id="54fde-114">[4][3]</span></span>|  
  
## <a name="example"></a><span data-ttu-id="54fde-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="54fde-115">Example</span></span>  
 <span data-ttu-id="54fde-116">Poniższy przykład tworzy <xref:System.Drawing.Image> obiektu na podstawie pliku ColorBars.bmp.</span><span class="sxs-lookup"><span data-stu-id="54fde-116">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars.bmp.</span></span> <span data-ttu-id="54fde-117">Następnie kod dodaje wartość 0,75 do składnika czerwony każdego piksela na obrazie.</span><span class="sxs-lookup"><span data-stu-id="54fde-117">Then the code adds 0.75 to the red component of each pixel in the image.</span></span> <span data-ttu-id="54fde-118">Oryginalny obraz jest rysowany wraz z obrazu przekształcone.</span><span class="sxs-lookup"><span data-stu-id="54fde-118">The original image is drawn alongside the transformed image.</span></span>  
  
 <span data-ttu-id="54fde-119">Na poniższej ilustracji przedstawiono oryginalny obraz po lewej stronie i przekształcone obraz po prawej stronie:</span><span class="sxs-lookup"><span data-stu-id="54fde-119">The following illustration shows the original image on the left and the transformed image on the right:</span></span>  
  
 ![Zrzut ekranu przedstawiający obrazu oryginalnego i przekształcone.](./media/how-to-translate-image-colors/original-image-translate-colors.png)  
  
 <span data-ttu-id="54fde-121">W poniższej tabeli wymieniono wektorów kolor słupków cztery przed i po nim czerwony tłumaczenia.</span><span class="sxs-lookup"><span data-stu-id="54fde-121">The following table lists the color vectors for the four bars before and after the red translation.</span></span> <span data-ttu-id="54fde-122">Należy pamiętać, że maksymalna wartość dla składnika koloru jest 1, składnik czerwony, w drugim wierszu nie zmienia się.</span><span class="sxs-lookup"><span data-stu-id="54fde-122">Note that because the maximum value for a color component is 1, the red component in the second row does not change.</span></span> <span data-ttu-id="54fde-123">(Podobnie, wartość minimalna dla składnika koloru wynosi 0).</span><span class="sxs-lookup"><span data-stu-id="54fde-123">(Similarly, the minimum value for a color component is 0.)</span></span>  
  
|<span data-ttu-id="54fde-124">Oryginał</span><span class="sxs-lookup"><span data-stu-id="54fde-124">Original</span></span>|<span data-ttu-id="54fde-125">Tłumaczenie</span><span class="sxs-lookup"><span data-stu-id="54fde-125">Translated</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="54fde-126">Czarny (0, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="54fde-126">Black (0, 0, 0, 1)</span></span>|<span data-ttu-id="54fde-127">(0.75, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="54fde-127">(0.75, 0, 0, 1)</span></span>|  
|<span data-ttu-id="54fde-128">Czerwony (1, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="54fde-128">Red (1, 0, 0, 1)</span></span>|<span data-ttu-id="54fde-129">(1, 0, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="54fde-129">(1, 0, 0, 1)</span></span>|  
|<span data-ttu-id="54fde-130">Kolor zielony (0, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="54fde-130">Green (0, 1, 0, 1)</span></span>|<span data-ttu-id="54fde-131">(0.75, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="54fde-131">(0.75, 1, 0, 1)</span></span>|  
|<span data-ttu-id="54fde-132">Niebieski (0, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="54fde-132">Blue (0, 0, 1, 1)</span></span>|<span data-ttu-id="54fde-133">(0.75, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="54fde-133">(0.75, 0, 1, 1)</span></span>|  
  
 [!code-csharp[System.Drawing.RecoloringImages#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.RecoloringImages#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="54fde-134">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="54fde-134">Compiling the Code</span></span>  
 <span data-ttu-id="54fde-135">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="54fde-135">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="54fde-136">Zastąp `ColorBars.bmp` za pomocą nazwy pliku obrazu i ścieżki, które są prawidłowe w tym systemie.</span><span class="sxs-lookup"><span data-stu-id="54fde-136">Replace `ColorBars.bmp` with an image file name and path that are valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54fde-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54fde-137">See also</span></span>

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="54fde-138">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="54fde-138">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="54fde-139">Ponowne kolorowanie obrazów</span><span class="sxs-lookup"><span data-stu-id="54fde-139">Recoloring Images</span></span>](recoloring-images.md)
