---
title: 'Instrukcje: Stosowanie trybu składania do sterowania przenikaniem alfa'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- alpha blending [Windows Forms], compositing
- colors [Windows Forms], blending
- colors [Windows Forms], controlling transparency
ms.assetid: f331df2d-b395-4b0a-95be-24fec8c9bbb5
ms.openlocfilehash: 1a5cf23890cd6183d92e33ec4e24f87c226e8ec3
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58462867"
---
# <a name="how-to-use-compositing-mode-to-control-alpha-blending"></a><span data-ttu-id="bcd2c-102">Instrukcje: Stosowanie trybu składania do sterowania przenikaniem alfa</span><span class="sxs-lookup"><span data-stu-id="bcd2c-102">How to: Use Compositing Mode to Control Alpha Blending</span></span>
<span data-ttu-id="bcd2c-103">Mogą wystąpić sytuacje, gdy chcesz utworzyć poza ekranem mapy bitowej, która ma następujące cechy:</span><span class="sxs-lookup"><span data-stu-id="bcd2c-103">There may be times when you want to create an off-screen bitmap that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="bcd2c-104">Kolory mają wartości alfa, które są mniej niż 255.</span><span class="sxs-lookup"><span data-stu-id="bcd2c-104">Colors have alpha values that are less than 255.</span></span>  
  
-   <span data-ttu-id="bcd2c-105">Kolory nie są alfa połączeniu ze sobą, jak tworzenie mapy bitowej.</span><span class="sxs-lookup"><span data-stu-id="bcd2c-105">Colors are not alpha blended with each other as you create the bitmap.</span></span>  
  
-   <span data-ttu-id="bcd2c-106">Podczas wyświetlania mapy bitowej Zakończono kolorów w mapie bitowej są przenikaniem za pomocą kolorów tła na urządzenia wyświetlającego alfa.</span><span class="sxs-lookup"><span data-stu-id="bcd2c-106">When you display the finished bitmap, colors in the bitmap are alpha blended with the background colors on the display device.</span></span>  
  
 <span data-ttu-id="bcd2c-107">Aby utworzyć mapę bitową, należy utworzyć pusty <xref:System.Drawing.Bitmap> obiektu, a następnie utworzyć <xref:System.Drawing.Graphics> obiektu oparte na tej mapy bitowej.</span><span class="sxs-lookup"><span data-stu-id="bcd2c-107">To create such a bitmap, construct a blank <xref:System.Drawing.Bitmap> object, and then construct a <xref:System.Drawing.Graphics> object based on that bitmap.</span></span> <span data-ttu-id="bcd2c-108">Ustawianie trybu składania <xref:System.Drawing.Graphics> obiekt <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bcd2c-108">Set the compositing mode of the <xref:System.Drawing.Graphics> object to <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcd2c-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="bcd2c-109">Example</span></span>  
 <span data-ttu-id="bcd2c-110">Poniższy przykład tworzy <xref:System.Drawing.Graphics> na podstawie obiektu <xref:System.Drawing.Bitmap> obiektu.</span><span class="sxs-lookup"><span data-stu-id="bcd2c-110">The following example creates a <xref:System.Drawing.Graphics> object based on a <xref:System.Drawing.Bitmap> object.</span></span> <span data-ttu-id="bcd2c-111">Kod używa <xref:System.Drawing.Graphics> obiektu wraz z dwóch półprzezroczystych pędzli (alfa = 160) do malowania mapy bitowej.</span><span class="sxs-lookup"><span data-stu-id="bcd2c-111">The code uses the <xref:System.Drawing.Graphics> object along with two semitransparent brushes (alpha = 160) to paint on the bitmap.</span></span> <span data-ttu-id="bcd2c-112">Kod wprowadza czerwony elipsy i zielony elipsy, przy użyciu półprzezroczystych pędzli.</span><span class="sxs-lookup"><span data-stu-id="bcd2c-112">The code fills a red ellipse and a green ellipse using the semitransparent brushes.</span></span> <span data-ttu-id="bcd2c-113">Zielony elipsy nakłada się na czerwony elipsy, ale zielony nie jest zmieszana z czerwonym, ponieważ tryb składania <xref:System.Drawing.Graphics> obiekt jest ustawiony na <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>.</span><span class="sxs-lookup"><span data-stu-id="bcd2c-113">The green ellipse overlaps the red ellipse, but the green is not blended with the red because the compositing mode of the <xref:System.Drawing.Graphics> object is set to <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>.</span></span>  
  
 <span data-ttu-id="bcd2c-114">Kod rysuje mapy bitowej na ekranie dwa razy: jeden raz na białym tle i jeden raz na tle różnych kolorach.</span><span class="sxs-lookup"><span data-stu-id="bcd2c-114">The code draws the bitmap on the screen twice: once on a white background and once on a multicolored background.</span></span> <span data-ttu-id="bcd2c-115">Piksele w mapie bitowej, które są dostępne w ramach dwóch wielokropek ma składnik alfa 160, więc wielokropek są mieszane za pomocą kolorów tła na ekranie.</span><span class="sxs-lookup"><span data-stu-id="bcd2c-115">The pixels in the bitmap that are part of the two ellipses have an alpha component of 160, so the ellipses are blended with the background colors on the screen.</span></span>  
  
 <span data-ttu-id="bcd2c-116">Poniższa ilustracja przedstawia dane wyjściowe w przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="bcd2c-116">The following illustration shows the output of the code example.</span></span> <span data-ttu-id="bcd2c-117">Należy pamiętać, że wielokropek są mieszane w tle, ale nie są one mieszane ze sobą.</span><span class="sxs-lookup"><span data-stu-id="bcd2c-117">Note that the ellipses are blended with the background, but they are not blended with each other.</span></span>  
  
 ![Diagram przedstawiający wielokropek mieszane w tle, nie siebie nawzajem.](./media/how-to-use-compositing-mode-to-control-alpha-blending/ellipses-blended-background.png)  
  
 <span data-ttu-id="bcd2c-119">Przykładowy kod zawiera tej instrukcji:</span><span class="sxs-lookup"><span data-stu-id="bcd2c-119">The code example contains this statement:</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.AlphaBlending#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#41)]  
  
 <span data-ttu-id="bcd2c-120">Jeśli wielokropek, aby być mieszany ze sobą, a także w tle, należy zmienić tej instrukcji do następujących:</span><span class="sxs-lookup"><span data-stu-id="bcd2c-120">If you want the ellipses to be blended with each other as well as with the background, change that statement to the following:</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.AlphaBlending#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#42)]  
  
 <span data-ttu-id="bcd2c-121">Poniższa ilustracja przedstawia dane wyjściowe poprawiony kod.</span><span class="sxs-lookup"><span data-stu-id="bcd2c-121">The following illustration shows the output of the revised code.</span></span>  
  
 ![Diagram przedstawiający wielokropek połączeniu ze sobą oraz z tła.](./media/how-to-use-compositing-mode-to-control-alpha-blending/blend-ellipses-background.png)  
  
 [!code-csharp[System.Drawing.AlphaBlending#43](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#43)]
 [!code-vb[System.Drawing.AlphaBlending#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#43)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bcd2c-123">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="bcd2c-123">Compiling the Code</span></span>  
 <span data-ttu-id="bcd2c-124">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="bcd2c-124">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcd2c-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bcd2c-125">See also</span></span>
- <xref:System.Drawing.Color.FromArgb%2A>
- [<span data-ttu-id="bcd2c-126">Przenikanie alfa linii i wypełnień</span><span class="sxs-lookup"><span data-stu-id="bcd2c-126">Alpha Blending Lines and Fills</span></span>](alpha-blending-lines-and-fills.md)
