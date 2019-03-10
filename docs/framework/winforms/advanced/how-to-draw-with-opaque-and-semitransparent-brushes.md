---
title: 'Instrukcje: Rysowanie za pomocą nieprzezroczystych i półprzezroczystych pędzli'
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
ms.openlocfilehash: ebb2f1008d267c4b5dcf36a7a4aae749fe73bb59
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716884"
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a><span data-ttu-id="06f72-102">Instrukcje: Rysowanie za pomocą nieprzezroczystych i półprzezroczystych pędzli</span><span class="sxs-lookup"><span data-stu-id="06f72-102">How to: Draw with Opaque and Semitransparent Brushes</span></span>
<span data-ttu-id="06f72-103">Po wypełnieniu kształtu, należy przekazać <xref:System.Drawing.Brush> obiektu do jednej z metod wypełnienia <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="06f72-103">When you fill a shape, you must pass a <xref:System.Drawing.Brush> object to one of the fill methods of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="06f72-104">Jeden parametr <xref:System.Drawing.SolidBrush.%23ctor%2A> Konstruktor jest <xref:System.Drawing.Color> obiektu.</span><span class="sxs-lookup"><span data-stu-id="06f72-104">The one parameter of the <xref:System.Drawing.SolidBrush.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object.</span></span> <span data-ttu-id="06f72-105">Do wypełnienia kształtu nieprzezroczysty, ustaw składnik alfa koloru do 255.</span><span class="sxs-lookup"><span data-stu-id="06f72-105">To fill an opaque shape, set the alpha component of the color to 255.</span></span> <span data-ttu-id="06f72-106">Aby wypełnić półprzezroczystych kształtu, ustaw składnik alfa dowolną wartość od 1 do 254.</span><span class="sxs-lookup"><span data-stu-id="06f72-106">To fill a semitransparent shape, set the alpha component to any value from 1 through 254.</span></span>  
  
 <span data-ttu-id="06f72-107">Po wypełnieniu półprzezroczystych kształt, kolor kształtu jest zmieszana przy użyciu kolorów tła.</span><span class="sxs-lookup"><span data-stu-id="06f72-107">When you fill a semitransparent shape, the color of the shape is blended with the colors of the background.</span></span> <span data-ttu-id="06f72-108">Składnik alfa określa, jak są zmieszane kształt i kolor tła; wartości alfa niemal 0 ważniejsze na kolory tła i wartości alfa niemal 255 umieścić więcej wagi na kolor kształtu.</span><span class="sxs-lookup"><span data-stu-id="06f72-108">The alpha component specifies how the shape and background colors are mixed; alpha values near 0 place more weight on the background colors, and alpha values near 255 place more weight on the shape color.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06f72-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="06f72-109">Example</span></span>  
 <span data-ttu-id="06f72-110">Poniższy przykład pobiera mapę bitową i następnie wypełnia trzy wielokropek, które nakładają się na mapę bitową.</span><span class="sxs-lookup"><span data-stu-id="06f72-110">The following example draws a bitmap and then fills three ellipses that overlap the bitmap.</span></span> <span data-ttu-id="06f72-111">Pierwszy elipsy używa składnik alfa, 255, więc jest nieprzezroczysta.</span><span class="sxs-lookup"><span data-stu-id="06f72-111">The first ellipse uses an alpha component of 255, so it is opaque.</span></span> <span data-ttu-id="06f72-112">Wielokropek drugi i trzeci Użyj składnik alfa, 128, dzięki czemu są one półprzezroczystych; obraz tła za pośrednictwem wielokropek jest widoczny.</span><span class="sxs-lookup"><span data-stu-id="06f72-112">The second and third ellipses use an alpha component of 128, so they are semitransparent; you can see the background image through the ellipses.</span></span> <span data-ttu-id="06f72-113">Wywołanie, które ustawia <xref:System.Drawing.Graphics.CompositingQuality%2A> właściwości powoduje, że mieszanie trzeci ikonę wielokropka, aby to zrobić w połączeniu z korekcji gamma.</span><span class="sxs-lookup"><span data-stu-id="06f72-113">The call that sets the <xref:System.Drawing.Graphics.CompositingQuality%2A> property causes the blending for the third ellipse to be done in conjunction with gamma correction.</span></span>  
  
 <span data-ttu-id="06f72-114">Poniższa ilustracja przedstawia dane wyjściowe następujący kod.</span><span class="sxs-lookup"><span data-stu-id="06f72-114">The following illustration shows the output of the following code.</span></span>  
  
 <span data-ttu-id="06f72-115">![Nieprzezroczystych i półprzezroczystych](./media/compqualellipse.png "compqualellipse")</span><span class="sxs-lookup"><span data-stu-id="06f72-115">![Opaque and Semitransparent](./media/compqualellipse.png "compqualellipse")</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="06f72-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="06f72-116">Compiling the Code</span></span>  
 <span data-ttu-id="06f72-117">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="06f72-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06f72-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06f72-118">See also</span></span>
- [<span data-ttu-id="06f72-119">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="06f72-119">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="06f72-120">Przenikanie alfa linii i wypełnień</span><span class="sxs-lookup"><span data-stu-id="06f72-120">Alpha Blending Lines and Fills</span></span>](alpha-blending-lines-and-fills.md)
- [<span data-ttu-id="06f72-121">Instrukcje: Zachować kontrolę z przezroczystym tłem</span><span class="sxs-lookup"><span data-stu-id="06f72-121">How to: Give Your Control a Transparent Background</span></span>](../controls/how-to-give-your-control-a-transparent-background.md)
- [<span data-ttu-id="06f72-122">Instrukcje: Rysowanie nieprzezroczystych i półprzezroczystych linii</span><span class="sxs-lookup"><span data-stu-id="06f72-122">How to: Draw Opaque and Semitransparent Lines</span></span>](how-to-draw-opaque-and-semitransparent-lines.md)
