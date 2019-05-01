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
ms.openlocfilehash: 7a8286fb741effaf668b87e90da04f79d1490de2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61960943"
---
# <a name="alpha-blending-lines-and-fills"></a><span data-ttu-id="244d1-102">Przenikanie alfa linii i wypełnień</span><span class="sxs-lookup"><span data-stu-id="244d1-102">Alpha Blending Lines and Fills</span></span>
<span data-ttu-id="244d1-103">W [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], kolor, który jest wartością 32-bitowych 8 bitów dla alpha, czerwony, zielony i niebieski.</span><span class="sxs-lookup"><span data-stu-id="244d1-103">In [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], a color is a 32-bit value with 8 bits each for alpha, red, green, and blue.</span></span> <span data-ttu-id="244d1-104">Wartość alfa odpowiadającą wskazuje Przezroczystość koloru — zakres, do których kolor jest zmieszana kolorem tła.</span><span class="sxs-lookup"><span data-stu-id="244d1-104">The alpha value indicates the transparency of the color — the extent to which the color is blended with the background color.</span></span> <span data-ttu-id="244d1-105">Wartości alfa z zakresu od 0 do 255, gdzie 0 reprezentuje w pełni przezroczyste kolor, a 255 reprezentuje kolor, który całkowicie nieprzezroczyste.</span><span class="sxs-lookup"><span data-stu-id="244d1-105">Alpha values range from 0 through 255, where 0 represents a fully transparent color, and 255 represents a fully opaque color.</span></span>  
  
 <span data-ttu-id="244d1-106">Przenikanie alfa jest poszczególne piksele mieszania danych koloru źródłowego i tła.</span><span class="sxs-lookup"><span data-stu-id="244d1-106">Alpha blending is a pixel-by-pixel blending of source and background color data.</span></span> <span data-ttu-id="244d1-107">Każdy z trzech składników koloru danego źródła (czerwony, zielony, niebieski) jest zmieszana przy użyciu odpowiadającego składnika koloru tła, zgodnie z następującą formułę:</span><span class="sxs-lookup"><span data-stu-id="244d1-107">Each of the three components (red, green, blue) of a given source color is blended with the corresponding component of the background color according to the following formula:</span></span>  
  
 <span data-ttu-id="244d1-108">displayColor = sourceColor × alpha / 255 + backgroundColor × (255 – alpha) / 255</span><span class="sxs-lookup"><span data-stu-id="244d1-108">displayColor = sourceColor × alpha / 255 + backgroundColor × (255 – alpha) / 255</span></span>  
  
 <span data-ttu-id="244d1-109">Na przykład załóżmy, że składnik czerwony kolor źródłowy jest 150 i czerwony składnik kolor tła to 100.</span><span class="sxs-lookup"><span data-stu-id="244d1-109">For example, suppose the red component of the source color is 150 and the red component of the background color is 100.</span></span> <span data-ttu-id="244d1-110">Jeśli wartość alfa odpowiadającą jest równy 200, składnik czerwony kolor wynikowy jest obliczana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="244d1-110">If the alpha value is 200, the red component of the resultant color is calculated as follows:</span></span>  
  
 <span data-ttu-id="244d1-111">150 × 200 / 255 + 100 × (255 – 200) / 255 = 139</span><span class="sxs-lookup"><span data-stu-id="244d1-111">150 × 200 / 255 + 100 × (255 – 200) / 255 = 139</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="244d1-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="244d1-112">In This Section</span></span>  
 [<span data-ttu-id="244d1-113">Instrukcje: Rysowanie nieprzezroczystych i półprzezroczystych linii</span><span class="sxs-lookup"><span data-stu-id="244d1-113">How to: Draw Opaque and Semitransparent Lines</span></span>](how-to-draw-opaque-and-semitransparent-lines.md)  
 <span data-ttu-id="244d1-114">Pokazuje, jak rysowanie linii mieszane alfa.</span><span class="sxs-lookup"><span data-stu-id="244d1-114">Shows how to draw alpha-blended lines.</span></span>  
  
 [<span data-ttu-id="244d1-115">Instrukcje: Rysowanie za pomocą nieprzezroczystych i półprzezroczystych pędzli</span><span class="sxs-lookup"><span data-stu-id="244d1-115">How to: Draw with Opaque and Semitransparent Brushes</span></span>](how-to-draw-with-opaque-and-semitransparent-brushes.md)  
 <span data-ttu-id="244d1-116">Wyjaśnia, jak mieszania alfa, przy użyciu pędzli.</span><span class="sxs-lookup"><span data-stu-id="244d1-116">Explains how to alpha-blend with brushes.</span></span>  
  
 [<span data-ttu-id="244d1-117">Instrukcje: Stosowanie trybu składania do sterowania przenikaniem alfa</span><span class="sxs-lookup"><span data-stu-id="244d1-117">How to: Use Compositing Mode to Control Alpha Blending</span></span>](how-to-use-compositing-mode-to-control-alpha-blending.md)  
 <span data-ttu-id="244d1-118">W tym artykule opisano sposób sterowania przenikaniem alfa, za pomocą <xref:System.Drawing.Drawing2D.CompositingMode>.</span><span class="sxs-lookup"><span data-stu-id="244d1-118">Describes how to control alpha blending using <xref:System.Drawing.Drawing2D.CompositingMode>.</span></span>  
  
 [<span data-ttu-id="244d1-119">Instrukcje: Stosowanie macierzy kolorów ustawiania wartości alfa na obrazach</span><span class="sxs-lookup"><span data-stu-id="244d1-119">How to: Use a Color Matrix to Set Alpha Values in Images</span></span>](how-to-use-a-color-matrix-to-set-alpha-values-in-images.md)  
 <span data-ttu-id="244d1-120">Opis sposobu użycia <xref:System.Drawing.Imaging.ColorMatrix> obiektu do sterowania przenikaniem alfa.</span><span class="sxs-lookup"><span data-stu-id="244d1-120">Explains how to use a <xref:System.Drawing.Imaging.ColorMatrix> object to control alpha blending.</span></span>
