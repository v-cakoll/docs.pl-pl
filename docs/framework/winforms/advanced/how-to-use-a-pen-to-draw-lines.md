---
title: 'Instrukcje: Rysowanie linii za pomocą pióra'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
ms.assetid: 0828c331-a438-4bdd-a4d6-3ef1e59e8795
ms.openlocfilehash: e24d02c2c6ab7537f968c013eb91838eb0bb812a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730935"
---
# <a name="how-to-use-a-pen-to-draw-lines"></a><span data-ttu-id="8c673-102">Instrukcje: Rysowanie linii za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="8c673-102">How to: Use a Pen to Draw Lines</span></span>
<span data-ttu-id="8c673-103">Rysowanie linii, potrzebujesz <xref:System.Drawing.Graphics> obiektu i <xref:System.Drawing.Pen> obiektu.</span><span class="sxs-lookup"><span data-stu-id="8c673-103">To draw lines, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="8c673-104"><xref:System.Drawing.Graphics> Obiektu <xref:System.Drawing.Graphics.DrawLine%2A> metody i <xref:System.Drawing.Pen> obiekt przechowuje funkcji, takich jak kolor i szerokość linii.</span><span class="sxs-lookup"><span data-stu-id="8c673-104">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawLine%2A> method, and the <xref:System.Drawing.Pen> object stores features of the line, such as color and width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c673-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="8c673-105">Example</span></span>  
 <span data-ttu-id="8c673-106">Poniższy przykład pobiera wiersz z (20, 10) do (300, 100).</span><span class="sxs-lookup"><span data-stu-id="8c673-106">The following example draws a line from (20, 10) to (300, 100).</span></span> <span data-ttu-id="8c673-107">Pierwsza instrukcja używa <xref:System.Drawing.Pen.%23ctor%2A> konstruktora klasy, aby utworzyć czarne pióro.</span><span class="sxs-lookup"><span data-stu-id="8c673-107">The first statement uses the <xref:System.Drawing.Pen.%23ctor%2A> class constructor to create a black pen.</span></span> <span data-ttu-id="8c673-108">Jeden argument przekazany do <xref:System.Drawing.Pen.%23ctor%2A> Konstruktor jest <xref:System.Drawing.Color> obiekt utworzony za pomocą <xref:System.Drawing.Color.FromArgb%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8c673-108">The one argument passed to the <xref:System.Drawing.Pen.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object created with the <xref:System.Drawing.Color.FromArgb%2A> method.</span></span> <span data-ttu-id="8c673-109">Wartości użyte do utworzenia <xref:System.Drawing.Color> obiektu — (255, 0, 0, 0) — odpowiadają alfa, czerwony, zielony i niebieski składników koloru.</span><span class="sxs-lookup"><span data-stu-id="8c673-109">The values used to create the <xref:System.Drawing.Color> object — (255, 0, 0, 0) — correspond to the alpha, red, green, and blue components of the color.</span></span> <span data-ttu-id="8c673-110">Wartości te definiują nieprzezroczysty czarny pióra.</span><span class="sxs-lookup"><span data-stu-id="8c673-110">These values define an opaque black pen.</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8c673-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="8c673-111">Compiling the Code</span></span>  
 <span data-ttu-id="8c673-112">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8c673-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c673-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c673-113">See also</span></span>
- <xref:System.Drawing.Pen>
- [<span data-ttu-id="8c673-114">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="8c673-114">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="8c673-115">Pióra, linie i prostokąty w GDI+</span><span class="sxs-lookup"><span data-stu-id="8c673-115">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
