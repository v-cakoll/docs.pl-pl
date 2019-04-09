---
title: 'Instrukcje: Rysowanie linii wypełnionej teksturą'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], texture
- drawing lines [Windows Forms], texture
ms.assetid: dc9118cc-f3c2-42e5-8173-f46d41d18fd5
ms.openlocfilehash: c0f90c298f48aeb96893bb09241faddc08d8a49d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186910"
---
# <a name="how-to-draw-a-line-filled-with-a-texture"></a><span data-ttu-id="7fd8c-102">Instrukcje: Rysowanie linii wypełnionej teksturą</span><span class="sxs-lookup"><span data-stu-id="7fd8c-102">How to: Draw a Line Filled with a Texture</span></span>
<span data-ttu-id="7fd8c-103">Zamiast Rysowanie linii za pomocą jednolitego koloru, można narysować linię z teksturą.</span><span class="sxs-lookup"><span data-stu-id="7fd8c-103">Instead of drawing a line with a solid color, you can draw a line with a texture.</span></span> <span data-ttu-id="7fd8c-104">Rysowanie linii i krzywych teksturą, należy utworzyć <xref:System.Drawing.TextureBrush> obiektu i przekaż go <xref:System.Drawing.TextureBrush> obiekt <xref:System.Drawing.Pen.%23ctor%2A> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="7fd8c-104">To draw lines and curves with a texture, create a <xref:System.Drawing.TextureBrush> object, and pass that <xref:System.Drawing.TextureBrush> object to a <xref:System.Drawing.Pen.%23ctor%2A> constructor.</span></span> <span data-ttu-id="7fd8c-105">Mapy bitowej skojarzone z pędzla tekstury jest używany do kafelka na płaszczyźnie (niewidocznie), a gdy Pióro rysuje linię lub krzywą, pociągnięcia pióra odkrywa niektórych pikseli tekstury fragmentacji.</span><span class="sxs-lookup"><span data-stu-id="7fd8c-105">The bitmap associated with the texture brush is used to tile the plane (invisibly), and when the pen draws a line or curve, the stroke of the pen uncovers certain pixels of the tiled texture.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7fd8c-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="7fd8c-106">Example</span></span>  
 <span data-ttu-id="7fd8c-107">Poniższy przykład tworzy <xref:System.Drawing.Bitmap> obiektu na podstawie pliku `Texture1.jpg`.</span><span class="sxs-lookup"><span data-stu-id="7fd8c-107">The following example creates a <xref:System.Drawing.Bitmap> object from the file `Texture1.jpg`.</span></span> <span data-ttu-id="7fd8c-108">Tej mapy bitowej służy do konstruowania <xref:System.Drawing.TextureBrush> obiektu, a <xref:System.Drawing.TextureBrush> obiekt jest używany do utworzenia <xref:System.Drawing.Pen> obiektu.</span><span class="sxs-lookup"><span data-stu-id="7fd8c-108">That bitmap is used to construct a <xref:System.Drawing.TextureBrush> object, and the <xref:System.Drawing.TextureBrush> object is used to construct a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="7fd8c-109">Wywołanie <xref:System.Drawing.Graphics.DrawImage%2A> rysuje mapę bitową z jego lewego górnego rogu w (0, 0).</span><span class="sxs-lookup"><span data-stu-id="7fd8c-109">The call to <xref:System.Drawing.Graphics.DrawImage%2A> draws the bitmap with its upper-left corner at (0, 0).</span></span> <span data-ttu-id="7fd8c-110">Wywołanie <xref:System.Drawing.Graphics.DrawEllipse%2A> używa <xref:System.Drawing.Pen> obiektu, aby narysować elipsę teksturą.</span><span class="sxs-lookup"><span data-stu-id="7fd8c-110">The call to <xref:System.Drawing.Graphics.DrawEllipse%2A> uses the <xref:System.Drawing.Pen> object to draw a textured ellipse.</span></span>  
  
 <span data-ttu-id="7fd8c-111">Poniższa ilustracja przedstawia, mapy bitowej i elipsy teksturą:</span><span class="sxs-lookup"><span data-stu-id="7fd8c-111">The following illustration shows the bitmap and the textured ellipse:</span></span>  
  
 ![Zrzut ekranu przedstawiający mapę bitową i teksturą elipsy.](./media/how-to-draw-a-line-filled-with-a-texture/bitmap-textured-ellipse.png)  
  
 [!code-csharp[System.Drawing.UsingAPen#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.UsingAPen#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7fd8c-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7fd8c-113">Compiling the Code</span></span>  
 <span data-ttu-id="7fd8c-114">Tworzenie formularza Windows i obsłużyć formularza <xref:System.Windows.Forms.Control.Paint> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7fd8c-114">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="7fd8c-115">Wklej poprzedni kod z gałęzią <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7fd8c-115">Paste the preceding code into the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="7fd8c-116">Zastąp `Texture.jpg` obrazem prawidłowy w tym systemie.</span><span class="sxs-lookup"><span data-stu-id="7fd8c-116">Replace `Texture.jpg` with an image valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fd8c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7fd8c-117">See also</span></span>

- [<span data-ttu-id="7fd8c-118">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="7fd8c-118">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="7fd8c-119">Grafika i rysowanie w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7fd8c-119">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
