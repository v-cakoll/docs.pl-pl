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
ms.openlocfilehash: 91aa3e89e2ff6d20432dbc5e988f2877059b4cdd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523611"
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a><span data-ttu-id="ae39e-102">Porady: rysowanie za pomocą nieprzezroczystych i półprzezroczystych pędzli</span><span class="sxs-lookup"><span data-stu-id="ae39e-102">How to: Draw with Opaque and Semitransparent Brushes</span></span>
<span data-ttu-id="ae39e-103">Podczas wypełnienia kształtu, należy przekazać <xref:System.Drawing.Brush> obiektu do jednej z metod wypełnienia <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="ae39e-103">When you fill a shape, you must pass a <xref:System.Drawing.Brush> object to one of the fill methods of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="ae39e-104">Jeden parametr <xref:System.Drawing.SolidBrush.%23ctor%2A> Konstruktor jest <xref:System.Drawing.Color> obiektu.</span><span class="sxs-lookup"><span data-stu-id="ae39e-104">The one parameter of the <xref:System.Drawing.SolidBrush.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object.</span></span> <span data-ttu-id="ae39e-105">Aby wypełnić kształt nieprzezroczyste, należy ustawić składnika alfa koloru do 255.</span><span class="sxs-lookup"><span data-stu-id="ae39e-105">To fill an opaque shape, set the alpha component of the color to 255.</span></span> <span data-ttu-id="ae39e-106">Aby wypełnić półprzezroczystych kształtu, należy ustawić składnika alfa na wartość od 1 do 254.</span><span class="sxs-lookup"><span data-stu-id="ae39e-106">To fill a semitransparent shape, set the alpha component to any value from 1 through 254.</span></span>  
  
 <span data-ttu-id="ae39e-107">Po wypełnieniu półprzezroczystych kształtu kolor kształtu mieszania kolorów tła.</span><span class="sxs-lookup"><span data-stu-id="ae39e-107">When you fill a semitransparent shape, the color of the shape is blended with the colors of the background.</span></span> <span data-ttu-id="ae39e-108">Składnik alfa określa, jak kolory tła i kształtu mieszane; wartości alfa niemal 0 umieść ważniejsze na kolory tła i wartości alfa niemal 255 umieść ważniejsze na kolor kształtu.</span><span class="sxs-lookup"><span data-stu-id="ae39e-108">The alpha component specifies how the shape and background colors are mixed; alpha values near 0 place more weight on the background colors, and alpha values near 255 place more weight on the shape color.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae39e-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae39e-109">Example</span></span>  
 <span data-ttu-id="ae39e-110">W poniższym przykładzie map bitowych rysuje i następnie wypełnia wielokropek trzech, które nakładają się na mapy bitowej.</span><span class="sxs-lookup"><span data-stu-id="ae39e-110">The following example draws a bitmap and then fills three ellipses that overlap the bitmap.</span></span> <span data-ttu-id="ae39e-111">Pierwszy elipsy używa składnika alfa 255, tak aby zawierała nieprzezroczyste.</span><span class="sxs-lookup"><span data-stu-id="ae39e-111">The first ellipse uses an alpha component of 255, so it is opaque.</span></span> <span data-ttu-id="ae39e-112">Wielokropek drugiego i trzeciego Użyj składnika alfa 128, dzięki czemu są one półprzezroczystych; obraz tła za pośrednictwem wielokropek jest widoczny.</span><span class="sxs-lookup"><span data-stu-id="ae39e-112">The second and third ellipses use an alpha component of 128, so they are semitransparent; you can see the background image through the ellipses.</span></span> <span data-ttu-id="ae39e-113">Wywołanie, która ustawia <xref:System.Drawing.Graphics.CompositingQuality%2A> właściwość powodująca usunięcie mieszania trzeci elipsy w połączeniu z korekcja gamma.</span><span class="sxs-lookup"><span data-stu-id="ae39e-113">The call that sets the <xref:System.Drawing.Graphics.CompositingQuality%2A> property causes the blending for the third ellipse to be done in conjunction with gamma correction.</span></span>  
  
 <span data-ttu-id="ae39e-114">Na poniższej ilustracji przedstawiono dane wyjściowe poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="ae39e-114">The following illustration shows the output of the following code.</span></span>  
  
 <span data-ttu-id="ae39e-115">![Nieprzezroczystych i półprzezroczystych](../../../../docs/framework/winforms/advanced/media/compqualellipse.png "compqualellipse")</span><span class="sxs-lookup"><span data-stu-id="ae39e-115">![Opaque and Semitransparent](../../../../docs/framework/winforms/advanced/media/compqualellipse.png "compqualellipse")</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ae39e-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ae39e-116">Compiling the Code</span></span>  
 <span data-ttu-id="ae39e-117">Powyższy przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="ae39e-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae39e-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae39e-118">See Also</span></span>  
 [<span data-ttu-id="ae39e-119">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ae39e-119">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="ae39e-120">Przenikanie alfa linii i wypełnień</span><span class="sxs-lookup"><span data-stu-id="ae39e-120">Alpha Blending Lines and Fills</span></span>](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)  
 [<span data-ttu-id="ae39e-121">Instrukcje: ustawienie przezroczystego tła kontrolki</span><span class="sxs-lookup"><span data-stu-id="ae39e-121">How to: Give Your Control a Transparent Background</span></span>](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 [<span data-ttu-id="ae39e-122">Instrukcje: rysowanie nieprzezroczystych i półprzezroczystych linii</span><span class="sxs-lookup"><span data-stu-id="ae39e-122">How to: Draw Opaque and Semitransparent Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
