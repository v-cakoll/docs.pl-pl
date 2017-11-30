---
title: "Porady: wypełnianie kształtów jednolitym kolorem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], adding to shapes
- shapes [Windows Forms], filling
ms.assetid: 06088b31-bac9-4ef3-9ebe-06c2c764d6df
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eb3e160392a903083386d9942f8e2cfe31ee89a4
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-fill-a-shape-with-a-solid-color"></a><span data-ttu-id="d8962-102">Porady: wypełnianie kształtów jednolitym kolorem</span><span class="sxs-lookup"><span data-stu-id="d8962-102">How to: Fill a Shape with a Solid Color</span></span>
<span data-ttu-id="d8962-103">Wypełnianie kształtów jednolitym kolorem, należy utworzyć <xref:System.Drawing.SolidBrush> obiekt, a następnie przekazać który <xref:System.Drawing.SolidBrush> obiektu jako argument metody fill <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="d8962-103">To fill a shape with a solid color, create a <xref:System.Drawing.SolidBrush> object, and then pass that <xref:System.Drawing.SolidBrush> object as an argument to one of the fill methods of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="d8962-104">Poniższy przykład pokazuje, jak do wypełnienia elipsy kolorem czerwonym.</span><span class="sxs-lookup"><span data-stu-id="d8962-104">The following example shows how to fill an ellipse with the color red.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8962-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8962-105">Example</span></span>  
 <span data-ttu-id="d8962-106">W poniższym kodzie <xref:System.Drawing.SolidBrush.%23ctor%2A> Konstruktor pobiera <xref:System.Drawing.Color> obiektu jako jej argument tylko.</span><span class="sxs-lookup"><span data-stu-id="d8962-106">In the following code, the <xref:System.Drawing.SolidBrush.%23ctor%2A> constructor takes a <xref:System.Drawing.Color> object as its only argument.</span></span> <span data-ttu-id="d8962-107">Wartości używane przez <xref:System.Drawing.Color.FromArgb%2A> metody reprezentują składniki alfa, czerwony, zielony i niebieski koloru.</span><span class="sxs-lookup"><span data-stu-id="d8962-107">The values used by the <xref:System.Drawing.Color.FromArgb%2A> method represent the alpha, red, green, and blue components of the color.</span></span> <span data-ttu-id="d8962-108">Każdy z tych wartości musi być z zakresu od 0 do 255.</span><span class="sxs-lookup"><span data-stu-id="d8962-108">Each of these values must be in the range 0 through 255.</span></span> <span data-ttu-id="d8962-109">Pierwszy 255 wskazuje, że kolor jest całkowicie nieprzezroczyste i drugi 255 oznacza, że składnik red jest na pełną intensywność.</span><span class="sxs-lookup"><span data-stu-id="d8962-109">The first 255 indicates that the color is fully opaque, and the second 255 indicates that the red component is at full intensity.</span></span> <span data-ttu-id="d8962-110">Dwa zera oznacza, że składniki zielonemu i niebieskiemu mieć intensywność 0.</span><span class="sxs-lookup"><span data-stu-id="d8962-110">The two zeros indicate that the green and blue components both have an intensity of 0.</span></span>  
  
 <span data-ttu-id="d8962-111">Cztery cyfry (0, 0, 100, 60) przekazany do <xref:System.Drawing.Graphics.FillEllipse%2A> metody Określ lokalizację i rozmiar prostokątem elipsy.</span><span class="sxs-lookup"><span data-stu-id="d8962-111">The four numbers (0, 0, 100, 60) passed to the <xref:System.Drawing.Graphics.FillEllipse%2A> method specify the location and size of the bounding rectangle for the ellipse.</span></span> <span data-ttu-id="d8962-112">Prostokąt ma lewym górnym rogu (0, 0), 100 szerokość i wysokość 60.</span><span class="sxs-lookup"><span data-stu-id="d8962-112">The rectangle has an upper-left corner of (0, 0), a width of 100, and a height of 60.</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingABrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d8962-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d8962-113">Compiling the Code</span></span>  
 <span data-ttu-id="d8962-114">Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d8962-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8962-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8962-115">See Also</span></span>  
 [<span data-ttu-id="d8962-116">Używanie pędzla do wypełniania kształtów</span><span class="sxs-lookup"><span data-stu-id="d8962-116">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
