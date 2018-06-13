---
title: 'Porady: rysowanie linii za pomocą pióra'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
ms.assetid: 0828c331-a438-4bdd-a4d6-3ef1e59e8795
ms.openlocfilehash: 6a728bcaf9946b2b92ce0ee97599f4c4fd0fea69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522988"
---
# <a name="how-to-use-a-pen-to-draw-lines"></a><span data-ttu-id="5232a-102">Porady: rysowanie linii za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="5232a-102">How to: Use a Pen to Draw Lines</span></span>
<span data-ttu-id="5232a-103">Do rysowania linii, należy <xref:System.Drawing.Graphics> obiektu i <xref:System.Drawing.Pen> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5232a-103">To draw lines, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="5232a-104"><xref:System.Drawing.Graphics> Zawiera obiekt <xref:System.Drawing.Graphics.DrawLine%2A> metody i <xref:System.Drawing.Pen> obiekt przechowuje funkcje wiersza, np. kolor i szerokość.</span><span class="sxs-lookup"><span data-stu-id="5232a-104">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawLine%2A> method, and the <xref:System.Drawing.Pen> object stores features of the line, such as color and width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5232a-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="5232a-105">Example</span></span>  
 <span data-ttu-id="5232a-106">Poniższy przykład rysuje z (20, 10) do (300, 100).</span><span class="sxs-lookup"><span data-stu-id="5232a-106">The following example draws a line from (20, 10) to (300, 100).</span></span> <span data-ttu-id="5232a-107">Pierwsza instrukcja używa <xref:System.Drawing.Pen.%23ctor%2A> konstruktora klasy w celu utworzenia czarny pióra.</span><span class="sxs-lookup"><span data-stu-id="5232a-107">The first statement uses the <xref:System.Drawing.Pen.%23ctor%2A> class constructor to create a black pen.</span></span> <span data-ttu-id="5232a-108">Jeden argument przekazany do <xref:System.Drawing.Pen.%23ctor%2A> Konstruktor jest <xref:System.Drawing.Color> utworzone za pomocą obiektu <xref:System.Drawing.Color.FromArgb%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5232a-108">The one argument passed to the <xref:System.Drawing.Pen.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object created with the <xref:System.Drawing.Color.FromArgb%2A> method.</span></span> <span data-ttu-id="5232a-109">Wartości użyte do utworzenia <xref:System.Drawing.Color> obiektu — (255, 0, 0, 0) — odpowiadają składniki alfa, czerwony, zielony i niebieski koloru.</span><span class="sxs-lookup"><span data-stu-id="5232a-109">The values used to create the <xref:System.Drawing.Color> object — (255, 0, 0, 0) — correspond to the alpha, red, green, and blue components of the color.</span></span> <span data-ttu-id="5232a-110">Te wartości definiują nieprzezroczyste czarne pióro.</span><span class="sxs-lookup"><span data-stu-id="5232a-110">These values define an opaque black pen.</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5232a-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5232a-111">Compiling the Code</span></span>  
 <span data-ttu-id="5232a-112">Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5232a-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5232a-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5232a-113">See Also</span></span>  
 <xref:System.Drawing.Pen>  
 [<span data-ttu-id="5232a-114">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="5232a-114">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="5232a-115">Pióra, linie i prostokąty w GDI+</span><span class="sxs-lookup"><span data-stu-id="5232a-115">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
