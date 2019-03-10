---
title: Rysowanie linii i kształtów za pomocą pióra
ms.date: 03/30/2017
helpviewer_keywords:
- pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- drawing
ms.assetid: 8a7542ab-3e9e-443f-8405-2d6053528e20
ms.openlocfilehash: 3846c59712cec6003c35f336714041544dec94b3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716293"
---
# <a name="using-a-pen-to-draw-lines-and-shapes"></a><span data-ttu-id="ebae8-102">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="ebae8-102">Using a Pen to Draw Lines and Shapes</span></span>
<span data-ttu-id="ebae8-103">Użyj [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] `Pen` obiektów, aby narysować segmenty linii, krzywych i przedstawiono kształtów.</span><span class="sxs-lookup"><span data-stu-id="ebae8-103">Use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] `Pen` objects to draw line segments, curves, and the outlines of shapes.</span></span> <span data-ttu-id="ebae8-104">W tej sekcji *wiersza* odwołuje się do dowolnego z tych opcji, chyba że określono oznacza segment linii.</span><span class="sxs-lookup"><span data-stu-id="ebae8-104">In this section, *line* refers to any of these, unless specified to mean only a line segment.</span></span> <span data-ttu-id="ebae8-105">Ustaw właściwości piórem do kontrolowania kolor, szerokość, wyrównania i styl linii za pomocą tego pióra.</span><span class="sxs-lookup"><span data-stu-id="ebae8-105">Set the properties of a pen to control the color, width, alignment, and style of lines drawn with that pen.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ebae8-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ebae8-106">In This Section</span></span>  
 [<span data-ttu-id="ebae8-107">Instrukcje: Rysowanie linii za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="ebae8-107">How to: Use a Pen to Draw Lines</span></span>](how-to-use-a-pen-to-draw-lines.md)  
 <span data-ttu-id="ebae8-108">Wyjaśnia, jak rysowanie linii.</span><span class="sxs-lookup"><span data-stu-id="ebae8-108">Explains how to draw lines.</span></span>  
  
 [<span data-ttu-id="ebae8-109">Instrukcje: Rysowanie prostokątów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="ebae8-109">How to: Use a Pen to Draw Rectangles</span></span>](how-to-use-a-pen-to-draw-rectangles.md)  
 <span data-ttu-id="ebae8-110">Opisuje sposób Rysowanie prostokątów.</span><span class="sxs-lookup"><span data-stu-id="ebae8-110">Describes how to draw rectangles.</span></span>  
  
 [<span data-ttu-id="ebae8-111">Instrukcje: Ustaw szerokości i wyrównania pióra</span><span class="sxs-lookup"><span data-stu-id="ebae8-111">How to: Set Pen Width and Alignment</span></span>](how-to-set-pen-width-and-alignment.md)  
 <span data-ttu-id="ebae8-112">Wyjaśnia, jak zmienić szerokości i wyrównania `Pen` obiektu.</span><span class="sxs-lookup"><span data-stu-id="ebae8-112">Explains how to change the width and alignment of a `Pen` object.</span></span>  
  
 [<span data-ttu-id="ebae8-113">Instrukcje: Rysowanie linii z zakończeniem linii</span><span class="sxs-lookup"><span data-stu-id="ebae8-113">How to: Draw a Line with Line Caps</span></span>](how-to-draw-a-line-with-line-caps.md)  
 <span data-ttu-id="ebae8-114">W tym artykule opisano sposób dodawania zakończenia podczas rysowania linii.</span><span class="sxs-lookup"><span data-stu-id="ebae8-114">Describes how to add end caps when drawing a line.</span></span>  
  
 [<span data-ttu-id="ebae8-115">Instrukcje: Łączenie linii</span><span class="sxs-lookup"><span data-stu-id="ebae8-115">How to: Join Lines</span></span>](how-to-join-lines.md)  
 <span data-ttu-id="ebae8-116">Pokazuje, jak połączyć dwa wiersze.</span><span class="sxs-lookup"><span data-stu-id="ebae8-116">Shows how to join two lines.</span></span>  
  
 [<span data-ttu-id="ebae8-117">Instrukcje: Rysowanie niestandardowej linii kreskowanej</span><span class="sxs-lookup"><span data-stu-id="ebae8-117">How to: Draw a Custom Dashed Line</span></span>](how-to-draw-a-custom-dashed-line.md)  
 <span data-ttu-id="ebae8-118">W tym artykule opisano, jak narysować linię przerywaną, co.</span><span class="sxs-lookup"><span data-stu-id="ebae8-118">Describes how to draw a dashed line.</span></span>  
  
 [<span data-ttu-id="ebae8-119">Instrukcje: Rysowanie linii wypełnionej teksturą</span><span class="sxs-lookup"><span data-stu-id="ebae8-119">How to: Draw a Line Filled with a Texture</span></span>](how-to-draw-a-line-filled-with-a-texture.md)  
 <span data-ttu-id="ebae8-120">Wyjaśnia, jak narysować linię wypełnione tekstury.</span><span class="sxs-lookup"><span data-stu-id="ebae8-120">Explains how to draw a texture-filled line.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ebae8-121">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="ebae8-121">Reference</span></span>  
 <xref:System.Drawing.Pen>  
 <span data-ttu-id="ebae8-122">Zawiera opis tej klasy i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="ebae8-122">Describes this class and has links to all its members.</span></span>
