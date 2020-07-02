---
title: Grafika i rysowanie
description: Zapoznaj się z obiektami graficznymi, piórem, pędzlem i kolorami oraz sposobem wykonywania takich zadań, jak rysowanie kształtów, rysowanie tekstu lub wyświetlanie obrazów w Windows Forms.
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: 58d8cde6aa102225cf9e3c342efe37218c818307
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618405"
---
# <a name="graphics-and-drawing-in-windows-forms"></a><span data-ttu-id="908ca-103">Grafika i rysowanie w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="908ca-103">Graphics and Drawing in Windows Forms</span></span>
<span data-ttu-id="908ca-104">Środowisko uruchomieniowe języka wspólnego używa zaawansowanej implementacji interfejsu GDI+ systemu Windows GDI (GDI).</span><span class="sxs-lookup"><span data-stu-id="908ca-104">The common language runtime uses an advanced implementation of the Windows Graphics Device Interface (GDI) called GDI+.</span></span> <span data-ttu-id="908ca-105">Za pomocą interfejsu GDI+ można tworzyć grafiki, rysować tekst i manipulować obrazami graficznymi jako obiektami.</span><span class="sxs-lookup"><span data-stu-id="908ca-105">With GDI+ you can create graphics, draw text, and manipulate graphical images as objects.</span></span> <span data-ttu-id="908ca-106">Interfejs GDI+ został zaprojektowany w celu zapewnienia wydajności i prostoty użycia.</span><span class="sxs-lookup"><span data-stu-id="908ca-106">GDI+ is designed to offer performance and ease of use.</span></span> <span data-ttu-id="908ca-107">Można użyć GDI+ do renderowania graficznych obrazów na Windows Forms i kontrolek.</span><span class="sxs-lookup"><span data-stu-id="908ca-107">You can use GDI+ to render graphical images on Windows Forms and controls.</span></span> <span data-ttu-id="908ca-108">Chociaż nie można używać interfejsu GDI+ bezpośrednio w formularzach sieci Web, można wyświetlać obrazy graficzne za pomocą kontrolki serwer sieci Web obrazu.</span><span class="sxs-lookup"><span data-stu-id="908ca-108">Although you cannot use GDI+ directly on Web Forms, you can display graphical images through the Image Web Server control.</span></span>  
  
 <span data-ttu-id="908ca-109">W tej sekcji znajdziesz tematy, które wprowadzają Podstawy programowania GDI+.</span><span class="sxs-lookup"><span data-stu-id="908ca-109">In this section, you will find topics that introduce the fundamentals of GDI+ programming.</span></span> <span data-ttu-id="908ca-110">Chociaż nie jest to wyczerpujące odwołanie, ta sekcja zawiera informacje o <xref:System.Drawing.Graphics> <xref:System.Drawing.Pen> obiektach,, <xref:System.Drawing.Brush> i i <xref:System.Drawing.Color> wyjaśnia, jak wykonywać takie zadania jako kształty rysowania, rysowania tekstu lub wyświetlania obrazów.</span><span class="sxs-lookup"><span data-stu-id="908ca-110">Although not intended to be a comprehensive reference, this section includes information about the <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, and <xref:System.Drawing.Color> objects, and explains how to perform such tasks as drawing shapes, drawing text, or displaying images.</span></span> <span data-ttu-id="908ca-111">Aby uzyskać więcej informacji, zobacz [Informacje o interfejsie GDI+](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span><span class="sxs-lookup"><span data-stu-id="908ca-111">For more information, see [GDI+ Reference](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span></span>  
  
 <span data-ttu-id="908ca-112">Jeśli chcesz od razu rozpocząć pracę, zobacz [wprowadzenie z programowaniem grafiki](getting-started-with-graphics-programming.md).</span><span class="sxs-lookup"><span data-stu-id="908ca-112">If you'd like to jump in and get started right away, see [Getting Started with Graphics Programming](getting-started-with-graphics-programming.md).</span></span> <span data-ttu-id="908ca-113">Zawiera ona tematy dotyczące sposobu używania kodu do rysowania linii, kształtów, tekstu i innych informacji w formularzach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="908ca-113">It has topics on how to use code to draw lines, shapes, text, and more on Windows forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="908ca-114">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="908ca-114">In This Section</span></span>  
 [<span data-ttu-id="908ca-115">Grafika — omówienie</span><span class="sxs-lookup"><span data-stu-id="908ca-115">Graphics Overview</span></span>](graphics-overview-windows-forms.md)  
 <span data-ttu-id="908ca-116">Zawiera wprowadzenie do klas zarządzanych związanych z grafikią.</span><span class="sxs-lookup"><span data-stu-id="908ca-116">Provides an introduction to the graphics-related managed classes.</span></span>  
  
 [<span data-ttu-id="908ca-117">Informacje o kodzie zarządzanym GDI+</span><span class="sxs-lookup"><span data-stu-id="908ca-117">About GDI+ Managed Code</span></span>](about-gdi-managed-code.md)  
 <span data-ttu-id="908ca-118">Zawiera informacje o zarządzanych klasach GDI+.</span><span class="sxs-lookup"><span data-stu-id="908ca-118">Provides information about the managed GDI+ classes.</span></span>  
  
 [<span data-ttu-id="908ca-119">Używanie zarządzanych klas grafiki</span><span class="sxs-lookup"><span data-stu-id="908ca-119">Using Managed Graphics Classes</span></span>](using-managed-graphics-classes.md)  
 <span data-ttu-id="908ca-120">Pokazuje, jak wykonać różne zadania przy użyciu klas zarządzanych GDI+.</span><span class="sxs-lookup"><span data-stu-id="908ca-120">Demonstrates how to complete a variety of tasks using the GDI+ managed classes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="908ca-121">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="908ca-121">Reference</span></span>  
 <xref:System.Drawing>  
 <span data-ttu-id="908ca-122">Zapewnia dostęp do podstawowych funkcji graficznych interfejsu GDI+.</span><span class="sxs-lookup"><span data-stu-id="908ca-122">Provides access to GDI+ basic graphics functionality.</span></span>  
  
 <xref:System.Drawing.Drawing2D>  
 <span data-ttu-id="908ca-123">Zapewnia zaawansowane funkcje grafiki dwuwymiarowej i wektorowej.</span><span class="sxs-lookup"><span data-stu-id="908ca-123">Provides advanced two-dimensional and vector graphics functionality.</span></span>  
  
 <xref:System.Drawing.Imaging>  
 <span data-ttu-id="908ca-124">Zapewnia zaawansowane funkcje obrazu GDI+.</span><span class="sxs-lookup"><span data-stu-id="908ca-124">Provides advanced GDI+ imaging functionality.</span></span>  
  
 <xref:System.Drawing.Text>  
 <span data-ttu-id="908ca-125">Zapewnia zaawansowane funkcje typografii interfejsu GDI+.</span><span class="sxs-lookup"><span data-stu-id="908ca-125">Provides advanced GDI+ typography functionality.</span></span> <span data-ttu-id="908ca-126">Klasy w tej przestrzeni nazw mogą służyć do tworzenia i używania kolekcji czcionek.</span><span class="sxs-lookup"><span data-stu-id="908ca-126">The classes in this namespace can be used to create and use collections of fonts.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="908ca-127">Oferuje funkcje drukowania.</span><span class="sxs-lookup"><span data-stu-id="908ca-127">Provides printing functionality.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="908ca-128">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="908ca-128">Related Sections</span></span>  
 [<span data-ttu-id="908ca-129">Malowanie i renderowanie kontrolki niestandardowej</span><span class="sxs-lookup"><span data-stu-id="908ca-129">Custom Control Painting and Rendering</span></span>](../controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="908ca-130">Szczegóły dotyczące zapewniania kodu dla kontrolek rysowania.</span><span class="sxs-lookup"><span data-stu-id="908ca-130">Details how to provide code for painting controls.</span></span>
