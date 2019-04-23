---
title: 'Instrukcje: Wypełnianie kształtów jednolitym kolorem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], adding to shapes
- shapes [Windows Forms], filling
ms.assetid: 06088b31-bac9-4ef3-9ebe-06c2c764d6df
ms.openlocfilehash: d6fe7a252029ff80f21d99f7342fabb1d29fbe24
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211676"
---
# <a name="how-to-fill-a-shape-with-a-solid-color"></a><span data-ttu-id="57cda-102">Instrukcje: Wypełnianie kształtów jednolitym kolorem</span><span class="sxs-lookup"><span data-stu-id="57cda-102">How to: Fill a Shape with a Solid Color</span></span>
<span data-ttu-id="57cda-103">Wypełnianie kształtów jednolitym kolorem, należy utworzyć <xref:System.Drawing.SolidBrush> obiektu, a następnie przekaż go <xref:System.Drawing.SolidBrush> obiektu jako argumentu do jednej z metod wypełnienia <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="57cda-103">To fill a shape with a solid color, create a <xref:System.Drawing.SolidBrush> object, and then pass that <xref:System.Drawing.SolidBrush> object as an argument to one of the fill methods of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="57cda-104">Poniższy przykład pokazuje, jak można wypełnić elipsę kolorem czerwonym.</span><span class="sxs-lookup"><span data-stu-id="57cda-104">The following example shows how to fill an ellipse with the color red.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57cda-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="57cda-105">Example</span></span>  
 <span data-ttu-id="57cda-106">W poniższym kodzie <xref:System.Drawing.SolidBrush.%23ctor%2A> Konstruktor przyjmuje <xref:System.Drawing.Color> obiekt jako argument tylko.</span><span class="sxs-lookup"><span data-stu-id="57cda-106">In the following code, the <xref:System.Drawing.SolidBrush.%23ctor%2A> constructor takes a <xref:System.Drawing.Color> object as its only argument.</span></span> <span data-ttu-id="57cda-107">Wartości używane przez <xref:System.Drawing.Color.FromArgb%2A> metoda reprezentują alfa, czerwony, zielony i niebieski składników koloru.</span><span class="sxs-lookup"><span data-stu-id="57cda-107">The values used by the <xref:System.Drawing.Color.FromArgb%2A> method represent the alpha, red, green, and blue components of the color.</span></span> <span data-ttu-id="57cda-108">Każdy z tych wartości musi być z zakresu od 0 do 255.</span><span class="sxs-lookup"><span data-stu-id="57cda-108">Each of these values must be in the range 0 through 255.</span></span> <span data-ttu-id="57cda-109">Pierwszy 255 wskazuje, że kolor odpowiada pełnemu kryciu i drugi 255 wskazuje na to, że składnik czerwony jest w pełnej intensywności.</span><span class="sxs-lookup"><span data-stu-id="57cda-109">The first 255 indicates that the color is fully opaque, and the second 255 indicates that the red component is at full intensity.</span></span> <span data-ttu-id="57cda-110">Dwa zera wskazują, że składniki zielony i niebieski mają intensywność 0.</span><span class="sxs-lookup"><span data-stu-id="57cda-110">The two zeros indicate that the green and blue components both have an intensity of 0.</span></span>  
  
 <span data-ttu-id="57cda-111">Cztery cyfry (0, 0, 100, 60) przekazany do <xref:System.Drawing.Graphics.FillEllipse%2A> metoda Określ lokalizację i rozmiar prostokąt otaczający elipsy.</span><span class="sxs-lookup"><span data-stu-id="57cda-111">The four numbers (0, 0, 100, 60) passed to the <xref:System.Drawing.Graphics.FillEllipse%2A> method specify the location and size of the bounding rectangle for the ellipse.</span></span> <span data-ttu-id="57cda-112">Prostokąt ma lewego górnego rogu (0, 0), 100 szerokość i wysokość 60.</span><span class="sxs-lookup"><span data-stu-id="57cda-112">The rectangle has an upper-left corner of (0, 0), a width of 100, and a height of 60.</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingABrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="57cda-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="57cda-113">Compiling the Code</span></span>  
 <span data-ttu-id="57cda-114">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="57cda-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57cda-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57cda-115">See also</span></span>

- [<span data-ttu-id="57cda-116">Używanie pędzla do wypełniania kształtów</span><span class="sxs-lookup"><span data-stu-id="57cda-116">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
