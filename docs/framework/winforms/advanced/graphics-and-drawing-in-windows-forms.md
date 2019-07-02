---
title: Grafika i rysowanie w formularzach systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: e110203605c31f90f71c949f81c18ebf464d52eb
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505538"
---
# <a name="graphics-and-drawing-in-windows-forms"></a><span data-ttu-id="b19e7-102">Grafika i rysowanie w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b19e7-102">Graphics and Drawing in Windows Forms</span></span>
<span data-ttu-id="b19e7-103">Środowisko uruchomieniowe języka wspólnego używa zaawansowanych implementację programu Windows GDI Graphics Device Interface () o nazwie GDI +.</span><span class="sxs-lookup"><span data-stu-id="b19e7-103">The common language runtime uses an advanced implementation of the Windows Graphics Device Interface (GDI) called GDI+.</span></span> <span data-ttu-id="b19e7-104">Za pomocą GDI + można utworzyć grafiki, rysować tekst i obrazy graficzne jako obiekty manipulowania.</span><span class="sxs-lookup"><span data-stu-id="b19e7-104">With GDI+ you can create graphics, draw text, and manipulate graphical images as objects.</span></span> <span data-ttu-id="b19e7-105">GDI + jest przeznaczony do oferty, wydajność i łatwość użycia.</span><span class="sxs-lookup"><span data-stu-id="b19e7-105">GDI+ is designed to offer performance and ease of use.</span></span> <span data-ttu-id="b19e7-106">Umożliwia GDI + renderowanie obrazów graficznych na Windows Forms i formanty.</span><span class="sxs-lookup"><span data-stu-id="b19e7-106">You can use GDI+ to render graphical images on Windows Forms and controls.</span></span> <span data-ttu-id="b19e7-107">Mimo że nie można użyć interfejsu GDI + bezpośrednio na formularzach sieci Web, możesz wyświetlić obrazy za pomocą kontrolki serwera sieci Web obrazu.</span><span class="sxs-lookup"><span data-stu-id="b19e7-107">Although you cannot use GDI+ directly on Web Forms, you can display graphical images through the Image Web Server control.</span></span>  
  
 <span data-ttu-id="b19e7-108">W tej sekcji znajdziesz tematów, które wprowadzają podstawy programowania w GDI +.</span><span class="sxs-lookup"><span data-stu-id="b19e7-108">In this section, you will find topics that introduce the fundamentals of GDI+ programming.</span></span> <span data-ttu-id="b19e7-109">Mimo że nie mają być wyczerpujące Kompendium, ta sekcja zawiera informacje o <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, i <xref:System.Drawing.Color> obiektów i wyjaśniono, jak wykonywać takie zadania jak rysowanie kształtów, tekstu, rysowania lub Wyświetlanie obrazów.</span><span class="sxs-lookup"><span data-stu-id="b19e7-109">Although not intended to be a comprehensive reference, this section includes information about the <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, and <xref:System.Drawing.Color> objects, and explains how to perform such tasks as drawing shapes, drawing text, or displaying images.</span></span> <span data-ttu-id="b19e7-110">Aby uzyskać więcej informacji, zobacz [GDI + odwołanie](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span><span class="sxs-lookup"><span data-stu-id="b19e7-110">For more information, see [GDI+ Reference](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span></span>  
  
 <span data-ttu-id="b19e7-111">Jeśli chcesz od razu, a następnie od razu rozpocząć, zobacz [wprowadzenie do programowania grafiki](getting-started-with-graphics-programming.md).</span><span class="sxs-lookup"><span data-stu-id="b19e7-111">If you'd like to jump in and get started right away, see [Getting Started with Graphics Programming](getting-started-with-graphics-programming.md).</span></span> <span data-ttu-id="b19e7-112">Tematy w nim na temat sposobu Rysowanie linii, kształtów, tekstu i tylko na formularzach Windows forms za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="b19e7-112">It has topics on how to use code to draw lines, shapes, text, and more on Windows forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b19e7-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b19e7-113">In This Section</span></span>  
 [<span data-ttu-id="b19e7-114">Grafika — omówienie</span><span class="sxs-lookup"><span data-stu-id="b19e7-114">Graphics Overview</span></span>](graphics-overview-windows-forms.md)  
 <span data-ttu-id="b19e7-115">Wprowadzenie do klas zarządzanych powiązane grafiki.</span><span class="sxs-lookup"><span data-stu-id="b19e7-115">Provides an introduction to the graphics-related managed classes.</span></span>  
  
 [<span data-ttu-id="b19e7-116">Informacje o kodzie zarządzanym GDI+</span><span class="sxs-lookup"><span data-stu-id="b19e7-116">About GDI+ Managed Code</span></span>](about-gdi-managed-code.md)  
 <span data-ttu-id="b19e7-117">Zawiera informacje dotyczące zarządzanych klas GDI +.</span><span class="sxs-lookup"><span data-stu-id="b19e7-117">Provides information about the managed GDI+ classes.</span></span>  
  
 [<span data-ttu-id="b19e7-118">Używanie zarządzanych klas grafiki</span><span class="sxs-lookup"><span data-stu-id="b19e7-118">Using Managed Graphics Classes</span></span>](using-managed-graphics-classes.md)  
 <span data-ttu-id="b19e7-119">Pokazuje, jak Pełna różnych zadań z użyciem interfejsu GDI + zarządzanych klas.</span><span class="sxs-lookup"><span data-stu-id="b19e7-119">Demonstrates how to complete a variety of tasks using the GDI+ managed classes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b19e7-120">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="b19e7-120">Reference</span></span>  
 <xref:System.Drawing>  
 <span data-ttu-id="b19e7-121">Zapewnia dostęp do funkcji podstawowych grafiki w GDI +.</span><span class="sxs-lookup"><span data-stu-id="b19e7-121">Provides access to GDI+ basic graphics functionality.</span></span>  
  
 <xref:System.Drawing.Drawing2D>  
 <span data-ttu-id="b19e7-122">Zapewnia zaawansowane dwuwymiarowej i wektorowej funkcje graficzne.</span><span class="sxs-lookup"><span data-stu-id="b19e7-122">Provides advanced two-dimensional and vector graphics functionality.</span></span>  
  
 <xref:System.Drawing.Imaging>  
 <span data-ttu-id="b19e7-123">Zapewnia zaawansowane GDI + funkcje obsługi obrazów.</span><span class="sxs-lookup"><span data-stu-id="b19e7-123">Provides advanced GDI+ imaging functionality.</span></span>  
  
 <xref:System.Drawing.Text>  
 <span data-ttu-id="b19e7-124">Zapewnia zaawansowane funkcje typografii interfejsu GDI +.</span><span class="sxs-lookup"><span data-stu-id="b19e7-124">Provides advanced GDI+ typography functionality.</span></span> <span data-ttu-id="b19e7-125">Klasy w tej przestrzeni nazw może służyć do tworzenia i używania kolekcji czcionek.</span><span class="sxs-lookup"><span data-stu-id="b19e7-125">The classes in this namespace can be used to create and use collections of fonts.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="b19e7-126">Oferuje funkcję drukowania.</span><span class="sxs-lookup"><span data-stu-id="b19e7-126">Provides printing functionality.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b19e7-127">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="b19e7-127">Related Sections</span></span>  
 [<span data-ttu-id="b19e7-128">Malowanie i renderowanie kontrolki niestandardowej</span><span class="sxs-lookup"><span data-stu-id="b19e7-128">Custom Control Painting and Rendering</span></span>](../controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="b19e7-129">Szczegółowo opisuje sposób udostępniania kodu rysowania formantów.</span><span class="sxs-lookup"><span data-stu-id="b19e7-129">Details how to provide code for painting controls.</span></span>
