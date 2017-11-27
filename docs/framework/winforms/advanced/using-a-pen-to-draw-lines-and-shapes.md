---
title: "Rysowanie linii i kształtów za pomocą pióra"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- drawing
ms.assetid: 8a7542ab-3e9e-443f-8405-2d6053528e20
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0913dc2745e1b244e4b03c0e6b946441a401c5b1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="using-a-pen-to-draw-lines-and-shapes"></a><span data-ttu-id="ddd96-102">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="ddd96-102">Using a Pen to Draw Lines and Shapes</span></span>
<span data-ttu-id="ddd96-103">Użyj [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] `Pen` obiekty do rysowania segmenty linii, krzywych i konturów kształtów.</span><span class="sxs-lookup"><span data-stu-id="ddd96-103">Use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] `Pen` objects to draw line segments, curves, and the outlines of shapes.</span></span> <span data-ttu-id="ddd96-104">W tej sekcji *wiersza* odwołuje się do żadnego z tych opcji, chyba że określono oznacza segment linii.</span><span class="sxs-lookup"><span data-stu-id="ddd96-104">In this section, *line* refers to any of these, unless specified to mean only a line segment.</span></span> <span data-ttu-id="ddd96-105">Ustaw właściwości pióra do kontrolowania kolor, szerokość, wyrównanie i styl linii z tym pióra.</span><span class="sxs-lookup"><span data-stu-id="ddd96-105">Set the properties of a pen to control the color, width, alignment, and style of lines drawn with that pen.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ddd96-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ddd96-106">In This Section</span></span>  
 [<span data-ttu-id="ddd96-107">Porady: Rysowanie linii za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="ddd96-107">How to: Use a Pen to Draw Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-pen-to-draw-lines.md)  
 <span data-ttu-id="ddd96-108">Wyjaśniono, jak do rysowania linii.</span><span class="sxs-lookup"><span data-stu-id="ddd96-108">Explains how to draw lines.</span></span>  
  
 [<span data-ttu-id="ddd96-109">Porady: Rysowanie prostokątów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="ddd96-109">How to: Use a Pen to Draw Rectangles</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-pen-to-draw-rectangles.md)  
 <span data-ttu-id="ddd96-110">Opisuje sposób Rysowanie prostokątów.</span><span class="sxs-lookup"><span data-stu-id="ddd96-110">Describes how to draw rectangles.</span></span>  
  
 [<span data-ttu-id="ddd96-111">Porady: Ustawianie szerokości i wyrównania pióra</span><span class="sxs-lookup"><span data-stu-id="ddd96-111">How to: Set Pen Width and Alignment</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md)  
 <span data-ttu-id="ddd96-112">Wyjaśniono, jak zmienić szerokości i wyrównania `Pen` obiektu.</span><span class="sxs-lookup"><span data-stu-id="ddd96-112">Explains how to change the width and alignment of a `Pen` object.</span></span>  
  
 [<span data-ttu-id="ddd96-113">Porady: Rysowanie linii z zakończeniem linii</span><span class="sxs-lookup"><span data-stu-id="ddd96-113">How to: Draw a Line with Line Caps</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-with-line-caps.md)  
 <span data-ttu-id="ddd96-114">Opisuje sposób dodawania zakończenia podczas rysowania linii.</span><span class="sxs-lookup"><span data-stu-id="ddd96-114">Describes how to add end caps when drawing a line.</span></span>  
  
 [<span data-ttu-id="ddd96-115">Porady: łączenie linii</span><span class="sxs-lookup"><span data-stu-id="ddd96-115">How to: Join Lines</span></span>](../../../../docs/framework/winforms/advanced/how-to-join-lines.md)  
 <span data-ttu-id="ddd96-116">Pokazuje, jak sprzęgać dwa wiersze.</span><span class="sxs-lookup"><span data-stu-id="ddd96-116">Shows how to join two lines.</span></span>  
  
 [<span data-ttu-id="ddd96-117">Porady: Rysowanie niestandardowej linii kreskowanej</span><span class="sxs-lookup"><span data-stu-id="ddd96-117">How to: Draw a Custom Dashed Line</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-custom-dashed-line.md)  
 <span data-ttu-id="ddd96-118">Opisuje sposób Rysuj linię kropkowaną.</span><span class="sxs-lookup"><span data-stu-id="ddd96-118">Describes how to draw a dashed line.</span></span>  
  
 [<span data-ttu-id="ddd96-119">Porady: Rysowanie linii wypełnionej teksturą</span><span class="sxs-lookup"><span data-stu-id="ddd96-119">How to: Draw a Line Filled with a Texture</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-filled-with-a-texture.md)  
 <span data-ttu-id="ddd96-120">Wyjaśniono, jak rysowanie linii wypełnione tekstury.</span><span class="sxs-lookup"><span data-stu-id="ddd96-120">Explains how to draw a texture-filled line.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ddd96-121">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="ddd96-121">Reference</span></span>  
 <xref:System.Drawing.Pen>  
 <span data-ttu-id="ddd96-122">Ta klasa opisuje i zawiera łącza do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="ddd96-122">Describes this class and has links to all its members.</span></span>
