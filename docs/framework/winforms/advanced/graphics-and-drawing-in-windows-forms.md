---
title: Grafika i rysowanie w formularzach systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
ms.openlocfilehash: 08f87436ade62bb54295b012a1c24dc177ea9667
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705431"
---
# <a name="graphics-and-drawing-in-windows-forms"></a><span data-ttu-id="35a0a-102">Grafika i rysowanie w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="35a0a-102">Graphics and Drawing in Windows Forms</span></span>
<span data-ttu-id="35a0a-103">Środowisko uruchomieniowe języka wspólnego używa zaawansowanych implementację graficzny interfejs urządzenia Windows ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) o nazwie [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="35a0a-103">The common language runtime uses an advanced implementation of the Windows Graphics Device Interface ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) called [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="35a0a-104">Za pomocą [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] tworzenia grafiki, rysować tekst i obrazy graficzne jako obiekty manipulowania.</span><span class="sxs-lookup"><span data-stu-id="35a0a-104">With [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] you can create graphics, draw text, and manipulate graphical images as objects.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="35a0a-105">jest przeznaczony do oferty, wydajność i łatwość użycia.</span><span class="sxs-lookup"><span data-stu-id="35a0a-105">is designed to offer performance and ease of use.</span></span> <span data-ttu-id="35a0a-106">Możesz użyć [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] do renderowania obrazy na Windows Forms i formanty.</span><span class="sxs-lookup"><span data-stu-id="35a0a-106">You can use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to render graphical images on Windows Forms and controls.</span></span> <span data-ttu-id="35a0a-107">Mimo że nie można użyć [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] bezpośrednio na formularzach sieci Web, można wyświetlić obrazy za pomocą kontrolki serwera sieci Web obrazu.</span><span class="sxs-lookup"><span data-stu-id="35a0a-107">Although you cannot use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] directly on Web Forms, you can display graphical images through the Image Web Server control.</span></span>  
  
 <span data-ttu-id="35a0a-108">W tej sekcji znajdziesz tematów, które wprowadzają podstawy [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] programowania.</span><span class="sxs-lookup"><span data-stu-id="35a0a-108">In this section, you will find topics that introduce the fundamentals of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] programming.</span></span> <span data-ttu-id="35a0a-109">Mimo że nie mają być wyczerpujące Kompendium, ta sekcja zawiera informacje o <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, i <xref:System.Drawing.Color> obiektów i wyjaśniono, jak wykonywać takie zadania jak rysowanie kształtów, tekstu, rysowania lub Wyświetlanie obrazów.</span><span class="sxs-lookup"><span data-stu-id="35a0a-109">Although not intended to be a comprehensive reference, this section includes information about the <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, and <xref:System.Drawing.Color> objects, and explains how to perform such tasks as drawing shapes, drawing text, or displaying images.</span></span> <span data-ttu-id="35a0a-110">Aby uzyskać więcej informacji, zobacz [GDI + odwołanie](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span><span class="sxs-lookup"><span data-stu-id="35a0a-110">For more information, see [GDI+ Reference](/windows/desktop/gdiplus/-gdiplus-class-gdi-reference).</span></span>  
  
 <span data-ttu-id="35a0a-111">Jeśli chcesz od razu, a następnie od razu rozpocząć, zobacz [wprowadzenie do programowania grafiki](getting-started-with-graphics-programming.md).</span><span class="sxs-lookup"><span data-stu-id="35a0a-111">If you'd like to jump in and get started right away, see [Getting Started with Graphics Programming](getting-started-with-graphics-programming.md).</span></span> <span data-ttu-id="35a0a-112">Tematy w nim na temat sposobu Rysowanie linii, kształtów, tekstu i tylko na formularzach Windows forms za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="35a0a-112">It has topics on how to use code to draw lines, shapes, text, and more on Windows forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="35a0a-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="35a0a-113">In This Section</span></span>  
 [<span data-ttu-id="35a0a-114">Grafika — omówienie</span><span class="sxs-lookup"><span data-stu-id="35a0a-114">Graphics Overview</span></span>](graphics-overview-windows-forms.md)  
 <span data-ttu-id="35a0a-115">Wprowadzenie do klas zarządzanych powiązane grafiki.</span><span class="sxs-lookup"><span data-stu-id="35a0a-115">Provides an introduction to the graphics-related managed classes.</span></span>  
  
 [<span data-ttu-id="35a0a-116">Informacje o kodzie zarządzanym GDI+</span><span class="sxs-lookup"><span data-stu-id="35a0a-116">About GDI+ Managed Code</span></span>](about-gdi-managed-code.md)  
 <span data-ttu-id="35a0a-117">Zawiera informacje dotyczące zarządzanych [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] klasy.</span><span class="sxs-lookup"><span data-stu-id="35a0a-117">Provides information about the managed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes.</span></span>  
  
 [<span data-ttu-id="35a0a-118">Używanie zarządzanych klas grafiki</span><span class="sxs-lookup"><span data-stu-id="35a0a-118">Using Managed Graphics Classes</span></span>](using-managed-graphics-classes.md)  
 <span data-ttu-id="35a0a-119">Pokazuje, jak wykonywać różne zadania przy użyciu [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] zarządzanych klas.</span><span class="sxs-lookup"><span data-stu-id="35a0a-119">Demonstrates how to complete a variety of tasks using the [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] managed classes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="35a0a-120">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="35a0a-120">Reference</span></span>  
 <xref:System.Drawing>  
 <span data-ttu-id="35a0a-121">Zapewnia dostęp do [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funkcje graficzne podstawowe.</span><span class="sxs-lookup"><span data-stu-id="35a0a-121">Provides access to [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] basic graphics functionality.</span></span>  
  
 <xref:System.Drawing.Drawing2D>  
 <span data-ttu-id="35a0a-122">Zapewnia zaawansowane dwuwymiarowej i wektorowej funkcje graficzne.</span><span class="sxs-lookup"><span data-stu-id="35a0a-122">Provides advanced two-dimensional and vector graphics functionality.</span></span>  
  
 <xref:System.Drawing.Imaging>  
 <span data-ttu-id="35a0a-123">Zapewnia zaawansowane [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funkcje obsługi obrazów.</span><span class="sxs-lookup"><span data-stu-id="35a0a-123">Provides advanced [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] imaging functionality.</span></span>  
  
 <xref:System.Drawing.Text>  
 <span data-ttu-id="35a0a-124">Zapewnia zaawansowane [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] typografii funkcji.</span><span class="sxs-lookup"><span data-stu-id="35a0a-124">Provides advanced [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] typography functionality.</span></span> <span data-ttu-id="35a0a-125">Klasy w tej przestrzeni nazw może służyć do tworzenia i używania kolekcji czcionek.</span><span class="sxs-lookup"><span data-stu-id="35a0a-125">The classes in this namespace can be used to create and use collections of fonts.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="35a0a-126">Oferuje funkcję drukowania.</span><span class="sxs-lookup"><span data-stu-id="35a0a-126">Provides printing functionality.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="35a0a-127">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="35a0a-127">Related Sections</span></span>  
 [<span data-ttu-id="35a0a-128">Malowanie i renderowanie kontrolki niestandardowej</span><span class="sxs-lookup"><span data-stu-id="35a0a-128">Custom Control Painting and Rendering</span></span>](../controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="35a0a-129">Szczegółowo opisuje sposób udostępniania kodu rysowania formantów.</span><span class="sxs-lookup"><span data-stu-id="35a0a-129">Details how to provide code for painting controls.</span></span>
