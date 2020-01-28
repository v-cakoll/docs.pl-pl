---
title: Grafika i rysowanie
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: 10ad18d38c84f6e447601ab6c8bf1a953dabb7cf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746404"
---
# <a name="graphics-and-drawing-in-windows-forms"></a><span data-ttu-id="23f3d-102">Grafika i rysowanie w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="23f3d-102">Graphics and Drawing in Windows Forms</span></span>
<span data-ttu-id="23f3d-103">Środowisko uruchomieniowe języka wspólnego używa zaawansowanej implementacji interfejsu GDI+ systemu Windows GDI (GDI).</span><span class="sxs-lookup"><span data-stu-id="23f3d-103">The common language runtime uses an advanced implementation of the Windows Graphics Device Interface (GDI) called GDI+.</span></span> <span data-ttu-id="23f3d-104">Za pomocą interfejsu GDI+ można tworzyć grafiki, rysować tekst i manipulować obrazami graficznymi jako obiektami.</span><span class="sxs-lookup"><span data-stu-id="23f3d-104">With GDI+ you can create graphics, draw text, and manipulate graphical images as objects.</span></span> <span data-ttu-id="23f3d-105">Interfejs GDI+ został zaprojektowany w celu zapewnienia wydajności i prostoty użycia.</span><span class="sxs-lookup"><span data-stu-id="23f3d-105">GDI+ is designed to offer performance and ease of use.</span></span> <span data-ttu-id="23f3d-106">Można użyć GDI+ do renderowania graficznych obrazów na Windows Forms i kontrolek.</span><span class="sxs-lookup"><span data-stu-id="23f3d-106">You can use GDI+ to render graphical images on Windows Forms and controls.</span></span> <span data-ttu-id="23f3d-107">Chociaż nie można używać interfejsu GDI+ bezpośrednio w formularzach sieci Web, można wyświetlać obrazy graficzne za pomocą kontrolki serwer sieci Web obrazu.</span><span class="sxs-lookup"><span data-stu-id="23f3d-107">Although you cannot use GDI+ directly on Web Forms, you can display graphical images through the Image Web Server control.</span></span>  
  
 <span data-ttu-id="23f3d-108">W tej sekcji znajdziesz tematy, które wprowadzają Podstawy programowania GDI+.</span><span class="sxs-lookup"><span data-stu-id="23f3d-108">In this section, you will find topics that introduce the fundamentals of GDI+ programming.</span></span> <span data-ttu-id="23f3d-109">Chociaż nie jest to wyczerpujące odwołanie, ta sekcja zawiera informacje dotyczące <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>i <xref:System.Drawing.Color> obiektów oraz wyjaśnia sposób wykonywania takich zadań jak rysowanie kształtów, rysowanie tekstu lub wyświetlanie obrazów.</span><span class="sxs-lookup"><span data-stu-id="23f3d-109">Although not intended to be a comprehensive reference, this section includes information about the <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, and <xref:System.Drawing.Color> objects, and explains how to perform such tasks as drawing shapes, drawing text, or displaying images.</span></span> <span data-ttu-id="23f3d-110">Aby uzyskać więcej informacji, zobacz [Informacje o interfejsie GDI+](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span><span class="sxs-lookup"><span data-stu-id="23f3d-110">For more information, see [GDI+ Reference](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span></span>  
  
 <span data-ttu-id="23f3d-111">Jeśli chcesz od razu rozpocząć pracę, zobacz [wprowadzenie z programowaniem grafiki](getting-started-with-graphics-programming.md).</span><span class="sxs-lookup"><span data-stu-id="23f3d-111">If you'd like to jump in and get started right away, see [Getting Started with Graphics Programming](getting-started-with-graphics-programming.md).</span></span> <span data-ttu-id="23f3d-112">Zawiera ona tematy dotyczące sposobu używania kodu do rysowania linii, kształtów, tekstu i innych informacji w formularzach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="23f3d-112">It has topics on how to use code to draw lines, shapes, text, and more on Windows forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="23f3d-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="23f3d-113">In This Section</span></span>  
 [<span data-ttu-id="23f3d-114">Grafika — omówienie</span><span class="sxs-lookup"><span data-stu-id="23f3d-114">Graphics Overview</span></span>](graphics-overview-windows-forms.md)  
 <span data-ttu-id="23f3d-115">Zawiera wprowadzenie do klas zarządzanych związanych z grafikią.</span><span class="sxs-lookup"><span data-stu-id="23f3d-115">Provides an introduction to the graphics-related managed classes.</span></span>  
  
 [<span data-ttu-id="23f3d-116">Informacje o kodzie zarządzanym GDI+</span><span class="sxs-lookup"><span data-stu-id="23f3d-116">About GDI+ Managed Code</span></span>](about-gdi-managed-code.md)  
 <span data-ttu-id="23f3d-117">Zawiera informacje o zarządzanych klasach GDI+.</span><span class="sxs-lookup"><span data-stu-id="23f3d-117">Provides information about the managed GDI+ classes.</span></span>  
  
 [<span data-ttu-id="23f3d-118">Używanie zarządzanych klas grafiki</span><span class="sxs-lookup"><span data-stu-id="23f3d-118">Using Managed Graphics Classes</span></span>](using-managed-graphics-classes.md)  
 <span data-ttu-id="23f3d-119">Pokazuje, jak wykonać różne zadania przy użyciu klas zarządzanych GDI+.</span><span class="sxs-lookup"><span data-stu-id="23f3d-119">Demonstrates how to complete a variety of tasks using the GDI+ managed classes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="23f3d-120">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="23f3d-120">Reference</span></span>  
 <xref:System.Drawing>  
 <span data-ttu-id="23f3d-121">Zapewnia dostęp do podstawowych funkcji graficznych interfejsu GDI+.</span><span class="sxs-lookup"><span data-stu-id="23f3d-121">Provides access to GDI+ basic graphics functionality.</span></span>  
  
 <xref:System.Drawing.Drawing2D>  
 <span data-ttu-id="23f3d-122">Zapewnia zaawansowane funkcje grafiki dwuwymiarowej i wektorowej.</span><span class="sxs-lookup"><span data-stu-id="23f3d-122">Provides advanced two-dimensional and vector graphics functionality.</span></span>  
  
 <xref:System.Drawing.Imaging>  
 <span data-ttu-id="23f3d-123">Zapewnia zaawansowane funkcje obrazu GDI+.</span><span class="sxs-lookup"><span data-stu-id="23f3d-123">Provides advanced GDI+ imaging functionality.</span></span>  
  
 <xref:System.Drawing.Text>  
 <span data-ttu-id="23f3d-124">Zapewnia zaawansowane funkcje typografii interfejsu GDI+.</span><span class="sxs-lookup"><span data-stu-id="23f3d-124">Provides advanced GDI+ typography functionality.</span></span> <span data-ttu-id="23f3d-125">Klasy w tej przestrzeni nazw mogą służyć do tworzenia i używania kolekcji czcionek.</span><span class="sxs-lookup"><span data-stu-id="23f3d-125">The classes in this namespace can be used to create and use collections of fonts.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="23f3d-126">Oferuje funkcje drukowania.</span><span class="sxs-lookup"><span data-stu-id="23f3d-126">Provides printing functionality.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="23f3d-127">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="23f3d-127">Related Sections</span></span>  
 [<span data-ttu-id="23f3d-128">Malowanie i renderowanie kontrolki niestandardowej</span><span class="sxs-lookup"><span data-stu-id="23f3d-128">Custom Control Painting and Rendering</span></span>](../controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="23f3d-129">Szczegóły dotyczące zapewniania kodu dla kontrolek rysowania.</span><span class="sxs-lookup"><span data-stu-id="23f3d-129">Details how to provide code for painting controls.</span></span>
