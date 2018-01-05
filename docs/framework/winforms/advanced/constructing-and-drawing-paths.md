---
title: "Konstruowanie i rysowanie ścieżek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- paths [Windows Forms], drawing
- drawing paths [Windows Forms]
- graphics paths [Windows Forms], creating
- graphics paths [Windows Forms], drawing
- examples [Windows Forms], drawing paths
ms.assetid: f16ec921-56cf-46d1-9741-d7316ad06b23
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e6cec2356159b59e58ac6785a2988df7b2fac0e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="constructing-and-drawing-paths"></a><span data-ttu-id="4b124-102">Konstruowanie i rysowanie ścieżek</span><span class="sxs-lookup"><span data-stu-id="4b124-102">Constructing and Drawing Paths</span></span>
<span data-ttu-id="4b124-103">Ścieżka jest sekwencję elementów podstawowych grafiki (wiersze, prostokąty krzywych, tekst i podobnych), które można wykonywać na nich operacji i rysowane jako pojedyncza jednostka.</span><span class="sxs-lookup"><span data-stu-id="4b124-103">A path is a sequence of graphics primitives (lines, rectangles, curves, text, and the like) that can be manipulated and drawn as a single unit.</span></span> <span data-ttu-id="4b124-104">Ścieżkę można podzielić na *rysunki* otwarty lub zamknięty.</span><span class="sxs-lookup"><span data-stu-id="4b124-104">A path can be divided into *figures* that are either open or closed.</span></span> <span data-ttu-id="4b124-105">Ilustracja może zawierać kilka elementów podstawowych.</span><span class="sxs-lookup"><span data-stu-id="4b124-105">A figure can contain several primitives.</span></span>  
  
 <span data-ttu-id="4b124-106">Ścieżkę można zdefiniować, wywołując <xref:System.Drawing.Graphics.DrawPath%2A> metody <xref:System.Drawing.Graphics> klasy i można wpisać ścieżkę przez wywołanie metody <xref:System.Drawing.Graphics.FillPath%2A> metody <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="4b124-106">You can draw a path by calling the <xref:System.Drawing.Graphics.DrawPath%2A> method of the <xref:System.Drawing.Graphics> class, and you can fill a path by calling the <xref:System.Drawing.Graphics.FillPath%2A> method of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4b124-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="4b124-107">In This Section</span></span>  
 [<span data-ttu-id="4b124-108">Instrukcje: tworzenie figur z linii, krzywych i kształtów</span><span class="sxs-lookup"><span data-stu-id="4b124-108">How to: Create Figures from Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-figures-from-lines-curves-and-shapes.md)  
 <span data-ttu-id="4b124-109">Przedstawia sposób użycia <xref:System.Drawing.Drawing2D.GraphicsPath> można utworzyć wartości.</span><span class="sxs-lookup"><span data-stu-id="4b124-109">Shows how to use a <xref:System.Drawing.Drawing2D.GraphicsPath> to create figures.</span></span>  
  
 [<span data-ttu-id="4b124-110">Instrukcje: wypełnianie otwartych figur</span><span class="sxs-lookup"><span data-stu-id="4b124-110">How to: Fill Open Figures</span></span>](../../../../docs/framework/winforms/advanced/how-to-fill-open-figures.md)  
 <span data-ttu-id="4b124-111">Wyjaśniono, jak wypełnienia <xref:System.Drawing.Drawing2D.GraphicsPath>.</span><span class="sxs-lookup"><span data-stu-id="4b124-111">Explains how to fill a <xref:System.Drawing.Drawing2D.GraphicsPath>.</span></span>  
  
 [<span data-ttu-id="4b124-112">Instrukcje: spłaszczanie ścieżki krzywej do linii</span><span class="sxs-lookup"><span data-stu-id="4b124-112">How to: Flatten a Curved Path into a Line</span></span>](../../../../docs/framework/winforms/advanced/how-to-flatten-a-curved-path-into-a-line.md)  
 <span data-ttu-id="4b124-113">Pokazuje, jak spłaszczanie <xref:System.Drawing.Drawing2D.GraphicsPath>.</span><span class="sxs-lookup"><span data-stu-id="4b124-113">Shows how to flatten a <xref:System.Drawing.Drawing2D.GraphicsPath>.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4b124-114">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="4b124-114">Reference</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 <span data-ttu-id="4b124-115">Ta klasa opisuje i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="4b124-115">Describes this class and contains links to all of its members.</span></span>
