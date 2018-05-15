---
title: 'Porady: stosowanie trybu składania do sterowania przenikaniem alfa'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- alpha blending [Windows Forms], compositing
- colors [Windows Forms], blending
- colors [Windows Forms], controlling transparency
ms.assetid: f331df2d-b395-4b0a-95be-24fec8c9bbb5
ms.openlocfilehash: 55c6db1029c6823652ac29fca46f6f8dc4ec40d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-compositing-mode-to-control-alpha-blending"></a><span data-ttu-id="20758-102">Porady: stosowanie trybu składania do sterowania przenikaniem alfa</span><span class="sxs-lookup"><span data-stu-id="20758-102">How to: Use Compositing Mode to Control Alpha Blending</span></span>
<span data-ttu-id="20758-103">Może to być razy, gdy chcesz utworzyć ukrytej mapy bitowej, który ma następującą charakterystykę:</span><span class="sxs-lookup"><span data-stu-id="20758-103">There may be times when you want to create an off-screen bitmap that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="20758-104">Kolory przyjmują wartości alfa, które są mniej niż 255.</span><span class="sxs-lookup"><span data-stu-id="20758-104">Colors have alpha values that are less than 255.</span></span>  
  
-   <span data-ttu-id="20758-105">Kolory nie są alfa mieszane ze sobą, podczas tworzenia mapy bitowej.</span><span class="sxs-lookup"><span data-stu-id="20758-105">Colors are not alpha blended with each other as you create the bitmap.</span></span>  
  
-   <span data-ttu-id="20758-106">Podczas wyświetlania mapy bitowej Zakończono kolorów w mapie bitowej są przenikaniem przy użyciu kolorów tła na urządzenia wyświetlającego alfa.</span><span class="sxs-lookup"><span data-stu-id="20758-106">When you display the finished bitmap, colors in the bitmap are alpha blended with the background colors on the display device.</span></span>  
  
 <span data-ttu-id="20758-107">Aby utworzyć mapę bitową, należy utworzyć pusty <xref:System.Drawing.Bitmap> obiekt, a następnie utworzyć <xref:System.Drawing.Graphics> obiektu oparte na tej mapy bitowej.</span><span class="sxs-lookup"><span data-stu-id="20758-107">To create such a bitmap, construct a blank <xref:System.Drawing.Bitmap> object, and then construct a <xref:System.Drawing.Graphics> object based on that bitmap.</span></span> <span data-ttu-id="20758-108">Ustawianie trybu składania <xref:System.Drawing.Graphics> do obiektu <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="20758-108">Set the compositing mode of the <xref:System.Drawing.Graphics> object to <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20758-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="20758-109">Example</span></span>  
 <span data-ttu-id="20758-110">Poniższy przykład tworzy <xref:System.Drawing.Graphics> na podstawie obiektu <xref:System.Drawing.Bitmap> obiektu.</span><span class="sxs-lookup"><span data-stu-id="20758-110">The following example creates a <xref:System.Drawing.Graphics> object based on a <xref:System.Drawing.Bitmap> object.</span></span> <span data-ttu-id="20758-111">W kodzie użyto <xref:System.Drawing.Graphics> obiektu wraz z dwóch półprzezroczystych pędzli (alfa = 160) do malowania mapy bitowej.</span><span class="sxs-lookup"><span data-stu-id="20758-111">The code uses the <xref:System.Drawing.Graphics> object along with two semitransparent brushes (alpha = 160) to paint on the bitmap.</span></span> <span data-ttu-id="20758-112">Kod wypełnia red elipsy i elipsy zielony, przy użyciu półprzezroczystych pędzli.</span><span class="sxs-lookup"><span data-stu-id="20758-112">The code fills a red ellipse and a green ellipse using the semitransparent brushes.</span></span> <span data-ttu-id="20758-113">Zielony elipsy pokrywa się czerwone elipsy, ale zielonego nie jest przejściowe z czerwonym, ponieważ tryb składania <xref:System.Drawing.Graphics> obiektu ma ustawioną wartość <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>.</span><span class="sxs-lookup"><span data-stu-id="20758-113">The green ellipse overlaps the red ellipse, but the green is not blended with the red because the compositing mode of the <xref:System.Drawing.Graphics> object is set to <xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>.</span></span>  
  
 <span data-ttu-id="20758-114">Kod rysuje mapy bitowej na ekranie dwa razy: raz na białe tło i raz w różnych kolorach tła.</span><span class="sxs-lookup"><span data-stu-id="20758-114">The code draws the bitmap on the screen twice: once on a white background and once on a multicolored background.</span></span> <span data-ttu-id="20758-115">Pikseli w mapie bitowej będących częścią dwie elipsy ma składnika alfa 160, więc wielokropek są mieszane z kolorów tła na ekranie.</span><span class="sxs-lookup"><span data-stu-id="20758-115">The pixels in the bitmap that are part of the two ellipses have an alpha component of 160, so the ellipses are blended with the background colors on the screen.</span></span>  
  
 <span data-ttu-id="20758-116">Na poniższej ilustracji przedstawiono dane wyjściowe w przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="20758-116">The following illustration shows the output of the code example.</span></span> <span data-ttu-id="20758-117">Należy pamiętać, że wielokropek są mieszane w tle, ale nie są one mieszane ze sobą.</span><span class="sxs-lookup"><span data-stu-id="20758-117">Note that the ellipses are blended with the background, but they are not blended with each other.</span></span>  
  
 <span data-ttu-id="20758-118">![Źródło kopiowania](../../../../docs/framework/winforms/advanced/media/sourcecopy.png "sourcecopy")</span><span class="sxs-lookup"><span data-stu-id="20758-118">![Source Copy](../../../../docs/framework/winforms/advanced/media/sourcecopy.png "sourcecopy")</span></span>  
  
 <span data-ttu-id="20758-119">Przykładowy kod zawiera tej instrukcji:</span><span class="sxs-lookup"><span data-stu-id="20758-119">The code example contains this statement:</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.AlphaBlending#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#41)]  
  
 <span data-ttu-id="20758-120">Wielokropek na przejściowe, ze sobą, a także w tle, zmienić tej instrukcji do następującego:</span><span class="sxs-lookup"><span data-stu-id="20758-120">If you want the ellipses to be blended with each other as well as with the background, change that statement to the following:</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.AlphaBlending#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#42)]  
  
 <span data-ttu-id="20758-121">Na poniższej ilustracji przedstawiono dane wyjściowe poprawione kodu.</span><span class="sxs-lookup"><span data-stu-id="20758-121">The following illustration shows the output of the revised code.</span></span>  
  
 <span data-ttu-id="20758-122">![Źródło przez](../../../../docs/framework/winforms/advanced/media/sourceover.png "sourceover")</span><span class="sxs-lookup"><span data-stu-id="20758-122">![Source Over](../../../../docs/framework/winforms/advanced/media/sourceover.png "sourceover")</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#43)]
 [!code-vb[System.Drawing.AlphaBlending#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#43)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="20758-123">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="20758-123">Compiling the Code</span></span>  
 <span data-ttu-id="20758-124">Powyższy przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="20758-124">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20758-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="20758-125">See Also</span></span>  
 <xref:System.Drawing.Color.FromArgb%2A>  
 [<span data-ttu-id="20758-126">Przenikanie alfa linii i wypełnień</span><span class="sxs-lookup"><span data-stu-id="20758-126">Alpha Blending Lines and Fills</span></span>](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
