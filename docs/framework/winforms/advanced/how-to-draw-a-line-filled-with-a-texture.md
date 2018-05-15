---
title: 'Porady: rysowanie linii wypełnionej teksturą'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], texture
- drawing lines [Windows Forms], texture
ms.assetid: dc9118cc-f3c2-42e5-8173-f46d41d18fd5
ms.openlocfilehash: 1895c752340d8d764205b5a32b9af0861303841a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-a-line-filled-with-a-texture"></a><span data-ttu-id="89717-102">Porady: rysowanie linii wypełnionej teksturą</span><span class="sxs-lookup"><span data-stu-id="89717-102">How to: Draw a Line Filled with a Texture</span></span>
<span data-ttu-id="89717-103">Zamiast rysowania linii jednolitym kolorem, można Rysowanie linii z tekstury.</span><span class="sxs-lookup"><span data-stu-id="89717-103">Instead of drawing a line with a solid color, you can draw a line with a texture.</span></span> <span data-ttu-id="89717-104">Rysowanie linii i krzywych teksturą, Utwórz <xref:System.Drawing.TextureBrush> obiektu i przekazać który <xref:System.Drawing.TextureBrush> do obiektu <xref:System.Drawing.Pen.%23ctor%2A> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="89717-104">To draw lines and curves with a texture, create a <xref:System.Drawing.TextureBrush> object, and pass that <xref:System.Drawing.TextureBrush> object to a <xref:System.Drawing.Pen.%23ctor%2A> constructor.</span></span> <span data-ttu-id="89717-105">Mapa bitowa skojarzone z pędzla tekstury służy do kafelka płaszczyzny (sposób niewidoczny), i gdy Pióro rysuje linię lub krzywą, obrysu pióra odkrywa niektórych pikseli tekstury sąsiadującym.</span><span class="sxs-lookup"><span data-stu-id="89717-105">The bitmap associated with the texture brush is used to tile the plane (invisibly), and when the pen draws a line or curve, the stroke of the pen uncovers certain pixels of the tiled texture.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89717-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="89717-106">Example</span></span>  
 <span data-ttu-id="89717-107">Poniższy przykład tworzy <xref:System.Drawing.Bitmap> obiektów z pliku `Texture1.jpg`.</span><span class="sxs-lookup"><span data-stu-id="89717-107">The following example creates a <xref:System.Drawing.Bitmap> object from the file `Texture1.jpg`.</span></span> <span data-ttu-id="89717-108">Tej mapy bitowej jest używany do tworzenia <xref:System.Drawing.TextureBrush> obiektu, a <xref:System.Drawing.TextureBrush> obiekt jest używany do utworzenia <xref:System.Drawing.Pen> obiektu.</span><span class="sxs-lookup"><span data-stu-id="89717-108">That bitmap is used to construct a <xref:System.Drawing.TextureBrush> object, and the <xref:System.Drawing.TextureBrush> object is used to construct a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="89717-109">Wywołanie <xref:System.Drawing.Graphics.DrawImage%2A> rysuje mapy bitowej z jego lewego górnego rogu na (0, 0).</span><span class="sxs-lookup"><span data-stu-id="89717-109">The call to <xref:System.Drawing.Graphics.DrawImage%2A> draws the bitmap with its upper-left corner at (0, 0).</span></span> <span data-ttu-id="89717-110">Wywołanie <xref:System.Drawing.Graphics.DrawEllipse%2A> używa <xref:System.Drawing.Pen> obiektu do rysowania teksturą elipsy.</span><span class="sxs-lookup"><span data-stu-id="89717-110">The call to <xref:System.Drawing.Graphics.DrawEllipse%2A> uses the <xref:System.Drawing.Pen> object to draw a textured ellipse.</span></span>  
  
 <span data-ttu-id="89717-111">Na poniższej ilustracji przedstawiono mapy bitowej i teksturą elipsy.</span><span class="sxs-lookup"><span data-stu-id="89717-111">The following illustration shows the bitmap and the textured ellipse.</span></span>  
  
 <span data-ttu-id="89717-112">![Pióra](../../../../docs/framework/winforms/advanced/media/pens7.png "pens7")</span><span class="sxs-lookup"><span data-stu-id="89717-112">![Pens](../../../../docs/framework/winforms/advanced/media/pens7.png "pens7")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.UsingAPen#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="89717-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="89717-113">Compiling the Code</span></span>  
 <span data-ttu-id="89717-114">Tworzenie formularza systemu Windows i obsługiwać formularza <xref:System.Windows.Forms.Control.Paint> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="89717-114">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="89717-115">Wklej poprzedni kod do <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="89717-115">Paste the preceding code into the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="89717-116">Zastąp `Texture.jpg` wraz z obrazem, które są prawidłowe w tym systemie.</span><span class="sxs-lookup"><span data-stu-id="89717-116">Replace `Texture.jpg` with an image valid on your system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89717-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89717-117">See Also</span></span>  
 [<span data-ttu-id="89717-118">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="89717-118">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="89717-119">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="89717-119">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
