---
title: 'Porady: uzyskiwanie miar czcionek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], obtaining metrics
- font metrics [Windows Forms], obtaining
ms.assetid: ff7c0616-67f7-4fa2-84ee-b8d642f2b09b
ms.openlocfilehash: 3cc5ee303efe6c703a61eef6c7448979b487f6bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-obtain-font-metrics"></a><span data-ttu-id="35323-102">Porady: uzyskiwanie miar czcionek</span><span class="sxs-lookup"><span data-stu-id="35323-102">How to: Obtain Font Metrics</span></span>
<span data-ttu-id="35323-103"><xref:System.Drawing.FontFamily> Klasa udostępnia następujące metody pobierające różnych metryk dla określonej rodziny i stylu kombinacji:</span><span class="sxs-lookup"><span data-stu-id="35323-103">The <xref:System.Drawing.FontFamily> class provides the following methods that retrieve various metrics for a particular family/style combination:</span></span>  
  
-   <span data-ttu-id="35323-104"><xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="35323-104"><xref:System.Drawing.FontFamily.GetEmHeight%2A>(FontStyle)</span></span>  
  
-   <span data-ttu-id="35323-105"><xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="35323-105"><xref:System.Drawing.FontFamily.GetCellAscent%2A>(FontStyle)</span></span>  
  
-   <span data-ttu-id="35323-106"><xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="35323-106"><xref:System.Drawing.FontFamily.GetCellDescent%2A>(FontStyle)</span></span>  
  
-   <span data-ttu-id="35323-107"><xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)</span><span class="sxs-lookup"><span data-stu-id="35323-107"><xref:System.Drawing.FontFamily.GetLineSpacing%2A>(FontStyle)</span></span>  
  
 <span data-ttu-id="35323-108">Liczby zwrócone przez te metody znajdują się w jednostki projektu czcionki, dzięki czemu są one niezależnie od rozmiaru i jednostki konkretnej <xref:System.Drawing.Font> obiektu.</span><span class="sxs-lookup"><span data-stu-id="35323-108">The numbers returned by these methods are in font design units, so they are independent of the size and units of a particular <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="35323-109">Na poniższej ilustracji przedstawiono różne metryki.</span><span class="sxs-lookup"><span data-stu-id="35323-109">The following illustration shows the various metrics.</span></span>  
  
 <span data-ttu-id="35323-110">![Czcionki tekstu](../../../../docs/framework/winforms/advanced/media/fontstext7a.png "fontstext7A")</span><span class="sxs-lookup"><span data-stu-id="35323-110">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext7a.png "fontstext7A")</span></span>  
  
## <a name="example"></a><span data-ttu-id="35323-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="35323-111">Example</span></span>  
 <span data-ttu-id="35323-112">W poniższym przykładzie przedstawiono metryki regularne styl rodziny czcionek Arial.</span><span class="sxs-lookup"><span data-stu-id="35323-112">The following example displays the metrics for the regular style of the Arial font family.</span></span> <span data-ttu-id="35323-113">Kod tworzy również <xref:System.Drawing.Font> obiektu (w oparciu Arial rodziny) o rozmiarze 16 pikseli i przedstawia metryki (w pikselach) dla tego określonego <xref:System.Drawing.Font> obiektu.</span><span class="sxs-lookup"><span data-stu-id="35323-113">The code also creates a <xref:System.Drawing.Font> object (based on the Arial family) with size 16 pixels and displays the metrics (in pixels) for that particular <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="35323-114">Na poniższej ilustracji przedstawiono dane wyjściowe przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="35323-114">The following illustration shows the output of the example code.</span></span>  
  
 <span data-ttu-id="35323-115">![Czcionki tekstu](../../../../docs/framework/winforms/advanced/media/csfontstext8.png "csFontsText8")</span><span class="sxs-lookup"><span data-stu-id="35323-115">![Fonts Text](../../../../docs/framework/winforms/advanced/media/csfontstext8.png "csFontsText8")</span></span>  
  
 <span data-ttu-id="35323-116">Należy pamiętać, pierwsze dwa wiersze danych wyjściowych na powyższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="35323-116">Note the first two lines of output in the preceding illustration.</span></span> <span data-ttu-id="35323-117"><xref:System.Drawing.Font> o rozmiarze 16, podaje obiektu i <xref:System.Drawing.FontFamily> obiektu zwraca wysokość em 2048.</span><span class="sxs-lookup"><span data-stu-id="35323-117">The <xref:System.Drawing.Font> object returns a size of 16, and the <xref:System.Drawing.FontFamily> object returns an em height of 2,048.</span></span> <span data-ttu-id="35323-118">Te dwie liczb (16 i 2048) są kluczem do konwersji między jednostkami projektowania czcionki i jednostki (w tym przypadku pikselach) <xref:System.Drawing.Font> obiektu.</span><span class="sxs-lookup"><span data-stu-id="35323-118">These two numbers (16 and 2,048) are the key to converting between font design units and the units (in this case pixels) of the <xref:System.Drawing.Font> object.</span></span>  
  
 <span data-ttu-id="35323-119">Na przykład można konwertować wzrastająca z projektu jednostki do pikseli w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="35323-119">For example, you can convert the ascent from design units to pixels as follows:</span></span>  
  
 <span data-ttu-id="35323-120">![Czcionki tekstu](../../../../docs/framework/winforms/advanced/media/fontstext9.png "FontsText9")</span><span class="sxs-lookup"><span data-stu-id="35323-120">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext9.png "FontsText9")</span></span>  
  
 <span data-ttu-id="35323-121">Poniższy kod umieszcza tekst w pionie, ustawiając <xref:System.Drawing.PointF.Y%2A> elementu członkowskiego danych <xref:System.Drawing.PointF> obiektu.</span><span class="sxs-lookup"><span data-stu-id="35323-121">The following code positions text vertically by setting the <xref:System.Drawing.PointF.Y%2A> data member of a <xref:System.Drawing.PointF> object.</span></span> <span data-ttu-id="35323-122">Współrzędna y jest zwiększana o `font.Height` dla każdego nowego wiersza tekstu.</span><span class="sxs-lookup"><span data-stu-id="35323-122">The y-coordinate is increased by `font.Height` for each new line of text.</span></span> <span data-ttu-id="35323-123"><xref:System.Drawing.Font.Height%2A> Właściwość <xref:System.Drawing.Font> obiektu zwraca wierszami (w pikselach) dla tego określonego <xref:System.Drawing.Font> obiektu.</span><span class="sxs-lookup"><span data-stu-id="35323-123">The <xref:System.Drawing.Font.Height%2A> property of a <xref:System.Drawing.Font> object returns the line spacing (in pixels) for that particular <xref:System.Drawing.Font> object.</span></span> <span data-ttu-id="35323-124">W tym przykładzie numer zwrócone przez <xref:System.Drawing.Font.Height%2A> jest 19.</span><span class="sxs-lookup"><span data-stu-id="35323-124">In this example, the number returned by <xref:System.Drawing.Font.Height%2A> is 19.</span></span> <span data-ttu-id="35323-125">Należy pamiętać, że jest to ten sam numer (zaokrąglona w górę do liczby całkowitej) uzyskane konwertując Metryka odstępów między wierszami pikseli.</span><span class="sxs-lookup"><span data-stu-id="35323-125">Note that this is the same as the number (rounded up to an integer) obtained by converting the line-spacing metric to pixels.</span></span>  
  
 <span data-ttu-id="35323-126">Należy pamiętać, że wysokość em (nazywanych również rozmiar rozmiar lub em) nie jest sumą wzrastająca i spadku.</span><span class="sxs-lookup"><span data-stu-id="35323-126">Note that the em height (also called size or em size) is not the sum of the ascent and the descent.</span></span> <span data-ttu-id="35323-127">Suma wzrastająca i spadku jest nazywany wysokość komórki.</span><span class="sxs-lookup"><span data-stu-id="35323-127">The sum of the ascent and the descent is called the cell height.</span></span> <span data-ttu-id="35323-128">Wysokość komórki minus wewnętrzny początkowy jest równa wysokość elementu.</span><span class="sxs-lookup"><span data-stu-id="35323-128">The cell height minus the internal leading is equal to the em height.</span></span> <span data-ttu-id="35323-129">Wysokość komórki oraz wiodące zewnętrzne jest równa wierszami.</span><span class="sxs-lookup"><span data-stu-id="35323-129">The cell height plus the external leading is equal to the line spacing.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.FontsAndText#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="35323-130">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="35323-130">Compiling the Code</span></span>  
 <span data-ttu-id="35323-131">Powyższy przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="35323-131">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35323-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="35323-132">See Also</span></span>  
 [<span data-ttu-id="35323-133">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="35323-133">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="35323-134">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="35323-134">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
