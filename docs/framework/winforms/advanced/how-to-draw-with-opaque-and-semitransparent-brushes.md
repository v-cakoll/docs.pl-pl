---
title: 'Porady: rysowanie za pomocą nieprzezroczystych i półprzezroczystych pędzli'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- semi-transparent shapes [Windows Forms], drawing
- transparency [Windows Forms], semi-transparent shapes
- alpha blending [Windows Forms], brush
- brushes [Windows Forms], using semi-transparent
ms.assetid: a4f6f6b8-3bc8-440a-84af-d62ef0f8ff40
ms.openlocfilehash: 1e48bbd563f6377380848949325962b568fa432c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142410"
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a><span data-ttu-id="5f033-102">Porady: rysowanie za pomocą nieprzezroczystych i półprzezroczystych pędzli</span><span class="sxs-lookup"><span data-stu-id="5f033-102">How to: Draw with Opaque and Semitransparent Brushes</span></span>
<span data-ttu-id="5f033-103">Podczas wypełniania kształtu należy <xref:System.Drawing.Brush> przekazać obiekt do jednej z <xref:System.Drawing.Graphics> metod wypełniania klasy.</span><span class="sxs-lookup"><span data-stu-id="5f033-103">When you fill a shape, you must pass a <xref:System.Drawing.Brush> object to one of the fill methods of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="5f033-104">Jednym z parametrów <xref:System.Drawing.SolidBrush.%23ctor%2A> konstruktora <xref:System.Drawing.Color> jest obiekt.</span><span class="sxs-lookup"><span data-stu-id="5f033-104">The one parameter of the <xref:System.Drawing.SolidBrush.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object.</span></span> <span data-ttu-id="5f033-105">Aby wypełnić nieprzezroczysty kształt, należy ustawić składnik alfa koloru na 255.</span><span class="sxs-lookup"><span data-stu-id="5f033-105">To fill an opaque shape, set the alpha component of the color to 255.</span></span> <span data-ttu-id="5f033-106">Aby wypełnić kształt półprzezroczysty, należy ustawić komponent alfa na dowolną wartość od 1 do 254.</span><span class="sxs-lookup"><span data-stu-id="5f033-106">To fill a semitransparent shape, set the alpha component to any value from 1 through 254.</span></span>  
  
 <span data-ttu-id="5f033-107">Po wypełnieniu półprzezroczysty kształt kolor kształtu jest mieszany z kolorami tła.</span><span class="sxs-lookup"><span data-stu-id="5f033-107">When you fill a semitransparent shape, the color of the shape is blended with the colors of the background.</span></span> <span data-ttu-id="5f033-108">Składnik alfa określa sposób mieszania kolorów kształtu i tła; wartości alfa w pobliżu 0 umieścić większą wagę na kolorach tła, a wartości alfa w pobliżu 255 umieścić większą wagę na kolor kształtu.</span><span class="sxs-lookup"><span data-stu-id="5f033-108">The alpha component specifies how the shape and background colors are mixed; alpha values near 0 place more weight on the background colors, and alpha values near 255 place more weight on the shape color.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f033-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f033-109">Example</span></span>  
 <span data-ttu-id="5f033-110">Poniższy przykład rysuje mapę bitową, a następnie wypełnia trzy elipsy, które nakładają się na mapę bitową.</span><span class="sxs-lookup"><span data-stu-id="5f033-110">The following example draws a bitmap and then fills three ellipses that overlap the bitmap.</span></span> <span data-ttu-id="5f033-111">Pierwsza elipsa używa składnika alfa 255, więc jest nieprzezroczysta.</span><span class="sxs-lookup"><span data-stu-id="5f033-111">The first ellipse uses an alpha component of 255, so it is opaque.</span></span> <span data-ttu-id="5f033-112">Druga i trzecia elipsy używają składnika alfa 128, więc są półprzezroczysty; można zobaczyć obraz tła przez elipsy.</span><span class="sxs-lookup"><span data-stu-id="5f033-112">The second and third ellipses use an alpha component of 128, so they are semitransparent; you can see the background image through the ellipses.</span></span> <span data-ttu-id="5f033-113">Wywołanie, które <xref:System.Drawing.Graphics.CompositingQuality%2A> ustawia właściwość powoduje mieszania dla trzeciej elipsy, które mają być wykonane w połączeniu z poprawki gamma.</span><span class="sxs-lookup"><span data-stu-id="5f033-113">The call that sets the <xref:System.Drawing.Graphics.CompositingQuality%2A> property causes the blending for the third ellipse to be done in conjunction with gamma correction.</span></span>  

 [!code-csharp[System.Drawing.AlphaBlending#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  

 <span data-ttu-id="5f033-114">Na poniższej ilustracji przedstawiono dane wyjściowe następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="5f033-114">The following illustration shows the output of the following code:</span></span>
  
 ![Ilustracja przedstawiająca nieprzezroczyste i półprzezroczyste wyjście.](./media/how-to-draw-with-opaque-and-semitransparent-brushes/compositingquality-ellipse-semitransparent.png)  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5f033-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5f033-116">Compiling the Code</span></span>  
 <span data-ttu-id="5f033-117">Powyższy przykład jest przeznaczony do użytku z <xref:System.Windows.Forms.PaintEventArgs> `e`formularzami systemu Windows <xref:System.Windows.Forms.PaintEventHandler>i wymaga , który jest parametrem .</span><span class="sxs-lookup"><span data-stu-id="5f033-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f033-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f033-118">See also</span></span>

- [<span data-ttu-id="5f033-119">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5f033-119">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="5f033-120">Przenikanie alfa linii i wypełnień</span><span class="sxs-lookup"><span data-stu-id="5f033-120">Alpha Blending Lines and Fills</span></span>](alpha-blending-lines-and-fills.md)
- [<span data-ttu-id="5f033-121">Porady: ustawienie przezroczystego tła formantu</span><span class="sxs-lookup"><span data-stu-id="5f033-121">How to: Give Your Control a Transparent Background</span></span>](../controls/how-to-give-your-control-a-transparent-background.md)
- [<span data-ttu-id="5f033-122">Instrukcje: rysowanie nieprzezroczystych i półprzezroczystych linii</span><span class="sxs-lookup"><span data-stu-id="5f033-122">How to: Draw Opaque and Semitransparent Lines</span></span>](how-to-draw-opaque-and-semitransparent-lines.md)
