---
title: 'Instrukcje: Rysowanie nieprzezroczystych i półprzezroczystych linii'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- transparency [Windows Forms], lines
- lines [Windows Forms], drawing alpha blended
- alpha blending [Windows Forms], drawing lines
ms.assetid: 8f2508af-f495-4223-b5cc-646cbbb520eb
ms.openlocfilehash: 210916bbaf437d8f71b07e8107eb0cdc0989ea42
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58465623"
---
# <a name="how-to-draw-opaque-and-semitransparent-lines"></a><span data-ttu-id="482f6-102">Instrukcje: Rysowanie nieprzezroczystych i półprzezroczystych linii</span><span class="sxs-lookup"><span data-stu-id="482f6-102">How to: Draw Opaque and Semitransparent Lines</span></span>
<span data-ttu-id="482f6-103">Po narysowaniu linii, należy przekazać <xref:System.Drawing.Pen> obiekt <xref:System.Drawing.Graphics.DrawLine%2A> metody <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="482f6-103">When you draw a line, you must pass a <xref:System.Drawing.Pen> object to the <xref:System.Drawing.Graphics.DrawLine%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="482f6-104">Jeden z parametrów <xref:System.Drawing.Pen.%23ctor%2A> Konstruktor jest <xref:System.Drawing.Color> obiektu.</span><span class="sxs-lookup"><span data-stu-id="482f6-104">One of the parameters of the <xref:System.Drawing.Pen.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object.</span></span> <span data-ttu-id="482f6-105">Aby narysować linię nieprzezroczysty, ustaw składnik alfa koloru do 255.</span><span class="sxs-lookup"><span data-stu-id="482f6-105">To draw an opaque line, set the alpha component of the color to 255.</span></span> <span data-ttu-id="482f6-106">Aby narysować linię półprzezroczystych, należy ustawić składnik alfa na wartość od 1 do 254.</span><span class="sxs-lookup"><span data-stu-id="482f6-106">To draw a semitransparent line, set the alpha component to any value from 1 through 254.</span></span>  
  
 <span data-ttu-id="482f6-107">Kiedy rysujesz półprzezroczystych linii w tle koloru linii jest zmieszana przy użyciu kolorów tła.</span><span class="sxs-lookup"><span data-stu-id="482f6-107">When you draw a semitransparent line over a background, the color of the line is blended with the colors of the background.</span></span> <span data-ttu-id="482f6-108">Składnik alfa określa, jak kolory tła i wiersza są mieszane; wartości alfa niemal 0 ważniejsze na kolory tła i wartości alfa niemal 255 umieścić więcej wagi na kolor linii.</span><span class="sxs-lookup"><span data-stu-id="482f6-108">The alpha component specifies how the line and background colors are mixed; alpha values near 0 place more weight on the background colors, and alpha values near 255 place more weight on the line color.</span></span>  
  
## <a name="example"></a><span data-ttu-id="482f6-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="482f6-109">Example</span></span>  
 <span data-ttu-id="482f6-110">Poniższy przykład pobiera mapę bitową i następnie pobiera trzy wiersze, korzystających z mapy bitowej jako tło.</span><span class="sxs-lookup"><span data-stu-id="482f6-110">The following example draws a bitmap and then draws three lines that use the bitmap as a background.</span></span> <span data-ttu-id="482f6-111">Pierwszy wiersz używa składnik alfa, 255, więc jest nieprzezroczysta.</span><span class="sxs-lookup"><span data-stu-id="482f6-111">The first line uses an alpha component of 255, so it is opaque.</span></span> <span data-ttu-id="482f6-112">Wiersze drugi i trzeci Użyj składnik alfa, 128, dzięki czemu są one półprzezroczystych; Możesz zobaczyć obraz tła za pośrednictwem wierszy.</span><span class="sxs-lookup"><span data-stu-id="482f6-112">The second and third lines use an alpha component of 128, so they are semitransparent; you can see the background image through the lines.</span></span> <span data-ttu-id="482f6-113">Instrukcja, która ustawia <xref:System.Drawing.Graphics.CompositingQuality%2A> właściwości powoduje, że mieszanie trzeci wiersz do wykonania w połączeniu z korekcji gamma.</span><span class="sxs-lookup"><span data-stu-id="482f6-113">The statement that sets the <xref:System.Drawing.Graphics.CompositingQuality%2A> property causes the blending for the third line to be done in conjunction with gamma correction.</span></span>  
  
 [!code-csharp[System.Drawing.AlphaBlending#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.AlphaBlending#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#11)]  
  
 <span data-ttu-id="482f6-114">Na poniższej ilustracji przedstawiono dane wyjściowe następujący kod:</span><span class="sxs-lookup"><span data-stu-id="482f6-114">The following illustration shows the output of the following code:</span></span>  
  
 ![Ilustracja przedstawiająca nieprzezroczystych i półprzezroczystych danych wyjściowych](./media/how-to-draw-opaque-and-semitransparent-lines/opaque-semitransparent-lines.png)  

## <a name="compiling-the-code"></a><span data-ttu-id="482f6-116">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="482f6-116">Compiling the Code</span></span>  
 <span data-ttu-id="482f6-117">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="482f6-117">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="482f6-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="482f6-118">See also</span></span>
- [<span data-ttu-id="482f6-119">Przenikanie alfa linii i wypełnień</span><span class="sxs-lookup"><span data-stu-id="482f6-119">Alpha Blending Lines and Fills</span></span>](alpha-blending-lines-and-fills.md)
- [<span data-ttu-id="482f6-120">Instrukcje: Zachować kontrolę z przezroczystym tłem</span><span class="sxs-lookup"><span data-stu-id="482f6-120">How to: Give Your Control a Transparent Background</span></span>](../controls/how-to-give-your-control-a-transparent-background.md)
- [<span data-ttu-id="482f6-121">Instrukcje: Rysowanie za pomocą nieprzezroczystych i półprzezroczystych pędzli</span><span class="sxs-lookup"><span data-stu-id="482f6-121">How to: Draw with Opaque and Semitransparent Brushes</span></span>](how-to-draw-with-opaque-and-semitransparent-brushes.md)
