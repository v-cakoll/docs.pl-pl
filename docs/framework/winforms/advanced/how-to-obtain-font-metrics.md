---
title: 'Instrukcje: Uzyskiwanie miar czcionek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], obtaining metrics
- font metrics [Windows Forms], obtaining
ms.assetid: ff7c0616-67f7-4fa2-84ee-b8d642f2b09b
ms.openlocfilehash: 75177b609f14d335aa57aba77d647827f50a8692
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881852"
---
# <a name="how-to-obtain-font-metrics"></a><span data-ttu-id="d3977-102">Instrukcje: Uzyskiwanie miar czcionek</span><span class="sxs-lookup"><span data-stu-id="d3977-102">How to: Obtain Font Metrics</span></span>
<span data-ttu-id="d3977-103"><xref:System.Drawing.FontFamily> Klasa udostępnia następujące metody, które pobierają różne metryki dla kombinacji określonej rodziny/styl:</span><span class="sxs-lookup"><span data-stu-id="d3977-103">The <xref:System.Drawing.FontFamily> class provides the following methods that retrieve various metrics for a particular family/style combination:</span></span>  
  
- <span data-ttu-id="d3977-104"><xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="d3977-104"><xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)</span></span>  
  
- <span data-ttu-id="d3977-105"><xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="d3977-105"><xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)</span></span>  
  
- <span data-ttu-id="d3977-106"><xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="d3977-106"><xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)</span></span>  
  
- <span data-ttu-id="d3977-107"><xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="d3977-107"><xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)</span></span>  
  
 <span data-ttu-id="d3977-108">Liczby zwrócone przez te metody są w jednostkach projektowania czcionki, dzięki czemu są one niezależne od rozmiaru i jednostki określonego <xref:System.Drawing.Font> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d3977-108">The numbers returned by these methods are in font design units, so they are independent of the size and units of a particular <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="d3977-109">Na poniższej ilustracji przedstawiono różne metryki:</span><span class="sxs-lookup"><span data-stu-id="d3977-109">The following illustration shows the various metrics:</span></span>
  
 ![Ilustracja miar czcionek: ascent, zejścia i wierszami.](./media/how-to-obtain-font-metrics/various-font-metrics.png)  
  
## <a name="example"></a><span data-ttu-id="d3977-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3977-111">Example</span></span>  
 <span data-ttu-id="d3977-112">Poniższy przykład przedstawia metryki dla stylu normalnego rodziny czcionek Arial.</span><span class="sxs-lookup"><span data-stu-id="d3977-112">The following example displays the metrics for the regular style of the Arial font family.</span></span> <span data-ttu-id="d3977-113">Tworzy również kod <xref:System.Drawing.Font> obiektu (oparte na Arial rodziny) o rozmiarze 16 pikseli i wyświetla metryki (w pikselach) dla konkretnego <xref:System.Drawing.Font> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d3977-113">The code also creates a <xref:System.Drawing.Font> object (based on the Arial family) with size 16 pixels and displays the metrics (in pixels) for that particular <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="d3977-114">Na poniższej ilustracji przedstawiono dane wyjściowe przykładowego kodu:</span><span class="sxs-lookup"><span data-stu-id="d3977-114">The following illustration shows the output of the example code:</span></span>
  
 ![Przykładowe dane wyjściowe kodu czcionka Arial metryk.](./media/how-to-obtain-font-metrics/example-output-code-arial-font.png)  
  
 <span data-ttu-id="d3977-116">Należy pamiętać, pierwsze dwa wiersze danych wyjściowych na poprzedniej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="d3977-116">Note the first two lines of output in the preceding illustration.</span></span> <span data-ttu-id="d3977-117"><xref:System.Drawing.Font> Zwraca rozmiar 16 i <xref:System.Drawing.FontFamily> zwraca wysokość em 2048.</span><span class="sxs-lookup"><span data-stu-id="d3977-117">The <xref:System.Drawing.Font> object returns a size of 16, and the <xref:System.Drawing.FontFamily> object returns an em height of 2,048.</span></span> <span data-ttu-id="d3977-118">Te dwie wartości (16 i 2048) są kluczem do konwersji między jednostkami projektowania czcionki i jednostek (w tym przypadku pikselach) <xref:System.Drawing.Font> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d3977-118">These two numbers (16 and 2,048) are the key to converting between font design units and the units (in this case pixels) of the <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="d3977-119">Na przykład możesz przekształcić wzrastająca od projektowania jednostek do pikseli w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d3977-119">For example, you can convert the ascent from design units to pixels as follows:</span></span>  
  
 ![Formuła przedstawiający Konwersja jednostki projektu do pikseli](./media/how-to-obtain-font-metrics/convert-font-units-example.png)  
  
 <span data-ttu-id="d3977-121">Poniższy kod ustawia położenie tekstu w pionie, ustawiając <xref:System.Drawing.PointF.Y%2A> element członkowski danych <xref:System.Drawing.PointF> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d3977-121">The following code positions text vertically by setting the <xref:System.Drawing.PointF.Y%2A> data member of a <xref:System.Drawing.PointF> object.</span></span> <span data-ttu-id="d3977-122">Współrzędna y jest zwiększana o `font.Height` dla każdego nowego wiersza tekstu.</span><span class="sxs-lookup"><span data-stu-id="d3977-122">The y-coordinate is increased by `font.Height` for each new line of text.</span></span> <span data-ttu-id="d3977-123"><xref:System.Drawing.Font.Height%2A> Właściwość <xref:System.Drawing.Font> zwraca wierszami (w pikselach) dotyczące konkretnego <xref:System.Drawing.Font> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d3977-123">The <xref:System.Drawing.Font.Height%2A> property of a <xref:System.Drawing.Font> object returns the line spacing (in pixels) for that particular <xref:System.Drawing.Font> object.</span></span> <span data-ttu-id="d3977-124">W tym przykładzie numer zwrócone przez <xref:System.Drawing.Font.Height%2A> jest 19.</span><span class="sxs-lookup"><span data-stu-id="d3977-124">In this example, the number returned by <xref:System.Drawing.Font.Height%2A> is 19.</span></span> <span data-ttu-id="d3977-125">Należy pamiętać, że jest taki sam jak numer (z zaokrągleniem do liczby całkowitej), uzyskanego konwertując metryki odstępów między wierszami pikseli.</span><span class="sxs-lookup"><span data-stu-id="d3977-125">Note that this is the same as the number (rounded up to an integer) obtained by converting the line-spacing metric to pixels.</span></span>  
  
 <span data-ttu-id="d3977-126">Należy pamiętać, że wysokość em (nazywane również rozmiar rozmiar lub em) nie jest sumą i zejścia.</span><span class="sxs-lookup"><span data-stu-id="d3977-126">Note that the em height (also called size or em size) is not the sum of the ascent and the descent.</span></span> <span data-ttu-id="d3977-127">Suma i zejścia nosi nazwę wysokość komórki.</span><span class="sxs-lookup"><span data-stu-id="d3977-127">The sum of the ascent and the descent is called the cell height.</span></span> <span data-ttu-id="d3977-128">Wysokość komórki minus wiodących wewnętrznego jest równa wysokość em.</span><span class="sxs-lookup"><span data-stu-id="d3977-128">The cell height minus the internal leading is equal to the em height.</span></span> <span data-ttu-id="d3977-129">Wysokość komórki, a także wiodących zewnętrznych jest równe odstępy.</span><span class="sxs-lookup"><span data-stu-id="d3977-129">The cell height plus the external leading is equal to the line spacing.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.FontsAndText#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d3977-130">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d3977-130">Compiling the Code</span></span>  
 <span data-ttu-id="d3977-131">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="d3977-131">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3977-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3977-132">See also</span></span>

- [<span data-ttu-id="d3977-133">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d3977-133">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="d3977-134">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="d3977-134">Using Fonts and Text</span></span>](using-fonts-and-text.md)
