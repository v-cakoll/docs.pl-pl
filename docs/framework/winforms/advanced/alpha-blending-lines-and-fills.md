---
title: Przenikanie alfa linii i wypełnień
ms.date: 03/30/2017
helpviewer_keywords:
- lines [Windows Forms], adding transparency
- examples [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with lines
- alpha blending
- lines [Windows Forms], alpha blending
- fills [Windows Forms], alpha blending
- alpha blending [Windows Forms], using with fills
- shapes [Windows Forms], adding transparency
ms.assetid: 5440f48c-3ac9-44c3-b170-c1c110bdbab8
ms.openlocfilehash: f58fa2d105492c6c72d3d6906c3c35f89130fe91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="alpha-blending-lines-and-fills"></a><span data-ttu-id="312f8-102">Przenikanie alfa linii i wypełnień</span><span class="sxs-lookup"><span data-stu-id="312f8-102">Alpha Blending Lines and Fills</span></span>
<span data-ttu-id="312f8-103">W [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], kolor jest 32-bitową wartość z 8 bitów dla alpha, czerwony, zielony i niebieski.</span><span class="sxs-lookup"><span data-stu-id="312f8-103">In [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], a color is a 32-bit value with 8 bits each for alpha, red, green, and blue.</span></span> <span data-ttu-id="312f8-104">Wartości alfa wskazuje Przezroczystość koloru — zakresu, do którego kolor mieszania kolorem tła.</span><span class="sxs-lookup"><span data-stu-id="312f8-104">The alpha value indicates the transparency of the color — the extent to which the color is blended with the background color.</span></span> <span data-ttu-id="312f8-105">Wartości alfa należą do zakresu od 0 do 255, gdzie 0 oznacza całkowicie przezroczysty kolor, a 255 reprezentuje kolor całkowicie nieprzezroczyste.</span><span class="sxs-lookup"><span data-stu-id="312f8-105">Alpha values range from 0 through 255, where 0 represents a fully transparent color, and 255 represents a fully opaque color.</span></span>  
  
 <span data-ttu-id="312f8-106">Przenikanie alfa jest mieszanie poszczególne piksele dane koloru źródłowego i tła.</span><span class="sxs-lookup"><span data-stu-id="312f8-106">Alpha blending is a pixel-by-pixel blending of source and background color data.</span></span> <span data-ttu-id="312f8-107">Wszystkie trzy składniki (czerwony, zielony, niebieski) koloru danego źródła jest mieszane z odpowiadającego składnika kolor tła według następującego wzoru:</span><span class="sxs-lookup"><span data-stu-id="312f8-107">Each of the three components (red, green, blue) of a given source color is blended with the corresponding component of the background color according to the following formula:</span></span>  
  
 <span data-ttu-id="312f8-108">displayColor = sourceColor × alfa / 255 + x backgroundColor (255 — alfa) / 255</span><span class="sxs-lookup"><span data-stu-id="312f8-108">displayColor = sourceColor × alpha / 255 + backgroundColor × (255 – alpha) / 255</span></span>  
  
 <span data-ttu-id="312f8-109">Na przykład załóżmy, że składnik red koloru źródłowego jest 150 i kolor tła składnika czerwony to 100.</span><span class="sxs-lookup"><span data-stu-id="312f8-109">For example, suppose the red component of the source color is 150 and the red component of the background color is 100.</span></span> <span data-ttu-id="312f8-110">Jeśli alfa wartość 200, składnika czerwony wynikowe koloru jest obliczana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="312f8-110">If the alpha value is 200, the red component of the resultant color is calculated as follows:</span></span>  
  
 <span data-ttu-id="312f8-111">150 × 200 / 255 + 100 × (255 – 200) / 255 = 139</span><span class="sxs-lookup"><span data-stu-id="312f8-111">150 × 200 / 255 + 100 × (255 – 200) / 255 = 139</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="312f8-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="312f8-112">In This Section</span></span>  
 [<span data-ttu-id="312f8-113">Instrukcje: rysowanie nieprzezroczystych i półprzezroczystych linii</span><span class="sxs-lookup"><span data-stu-id="312f8-113">How to: Draw Opaque and Semitransparent Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)  
 <span data-ttu-id="312f8-114">Pokazuje, jak do rysowania linii przenikaniem alfa.</span><span class="sxs-lookup"><span data-stu-id="312f8-114">Shows how to draw alpha-blended lines.</span></span>  
  
 [<span data-ttu-id="312f8-115">Instrukcje: rysowanie za pomocą nieprzezroczystych i półprzezroczystych pędzli</span><span class="sxs-lookup"><span data-stu-id="312f8-115">How to: Draw with Opaque and Semitransparent Brushes</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-with-opaque-and-semitransparent-brushes.md)  
 <span data-ttu-id="312f8-116">Wyjaśniono, jak program blend alfa pędzli.</span><span class="sxs-lookup"><span data-stu-id="312f8-116">Explains how to alpha-blend with brushes.</span></span>  
  
 [<span data-ttu-id="312f8-117">Instrukcje: stosowanie trybu składania do sterowania przenikaniem alfa</span><span class="sxs-lookup"><span data-stu-id="312f8-117">How to: Use Compositing Mode to Control Alpha Blending</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-compositing-mode-to-control-alpha-blending.md)  
 <span data-ttu-id="312f8-118">Zawiera opis sposobu kontrolowania przenikanie alfa przy użyciu <xref:System.Drawing.Drawing2D.CompositingMode>.</span><span class="sxs-lookup"><span data-stu-id="312f8-118">Describes how to control alpha blending using <xref:System.Drawing.Drawing2D.CompositingMode>.</span></span>  
  
 [<span data-ttu-id="312f8-119">Instrukcje: stosowanie macierzy kolorów ustawiania wartości alfa na obrazach</span><span class="sxs-lookup"><span data-stu-id="312f8-119">How to: Use a Color Matrix to Set Alpha Values in Images</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-color-matrix-to-set-alpha-values-in-images.md)  
 <span data-ttu-id="312f8-120">Wyjaśniono, jak używać <xref:System.Drawing.Imaging.ColorMatrix> obiekt do kontrolowania przenikanie alfa.</span><span class="sxs-lookup"><span data-stu-id="312f8-120">Explains how to use a <xref:System.Drawing.Imaging.ColorMatrix> object to control alpha blending.</span></span>
