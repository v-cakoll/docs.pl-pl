---
title: Grafika i rysowanie w formularzach systemu Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b2e8bde5d1c2904723282f03a815f17c5cc7622d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="graphics-and-drawing-in-windows-forms"></a><span data-ttu-id="6f649-102">Grafika i rysowanie w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6f649-102">Graphics and Drawing in Windows Forms</span></span>
<span data-ttu-id="6f649-103">Środowisko uruchomieniowe języka wspólnego używa zaawansowane stosowania graficzny interfejs urządzenia z systemem Windows ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) o nazwie [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6f649-103">The common language runtime uses an advanced implementation of the Windows Graphics Device Interface ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) called [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="6f649-104">Z [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] można tworzyć grafiki, rysowanie tekstu i manipulowania obrazy jako obiekty.</span><span class="sxs-lookup"><span data-stu-id="6f649-104">With [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] you can create graphics, draw text, and manipulate graphical images as objects.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="6f649-105">zaprojektowano w celu zapewnienia wydajności i łatwość użycia.</span><span class="sxs-lookup"><span data-stu-id="6f649-105"> is designed to offer performance and ease of use.</span></span> <span data-ttu-id="6f649-106">Można użyć [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] do renderowania obrazy na i formantów formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6f649-106">You can use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to render graphical images on Windows Forms and controls.</span></span> <span data-ttu-id="6f649-107">Mimo że nie można użyć [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] bezpośrednio na formularzach sieci Web, można wyświetlić obrazy za pomocą kontrolki serwera sieci Web obrazu.</span><span class="sxs-lookup"><span data-stu-id="6f649-107">Although you cannot use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] directly on Web Forms, you can display graphical images through the Image Web Server control.</span></span>  
  
 <span data-ttu-id="6f649-108">W tej sekcji znajdziesz tematy, które podstawy [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] programowania.</span><span class="sxs-lookup"><span data-stu-id="6f649-108">In this section, you will find topics that introduce the fundamentals of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] programming.</span></span> <span data-ttu-id="6f649-109">Mimo że nie mają być odwołaniem kompleksowe, ta sekcja zawiera informacje o <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, i <xref:System.Drawing.Color> obiekty i wyjaśniono, jak wykonywać takie zadania jak rysowanie kształtów Rysowanie tekstu, lub Wyświetlanie obrazów.</span><span class="sxs-lookup"><span data-stu-id="6f649-109">Although not intended to be a comprehensive reference, this section includes information about the <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, and <xref:System.Drawing.Color> objects, and explains how to perform such tasks as drawing shapes, drawing text, or displaying images.</span></span> <span data-ttu-id="6f649-110">Aby uzyskać więcej informacji, zobacz [GDI + odwołanie](https://msdn.microsoft.com/library/vs/alm/ms533799.aspx).</span><span class="sxs-lookup"><span data-stu-id="6f649-110">For more information, see [GDI+ Reference](https://msdn.microsoft.com/library/vs/alm/ms533799.aspx).</span></span>  
  
 <span data-ttu-id="6f649-111">Jeśli chcesz przejść w i rozpocząć pracę od razu, zobacz [wprowadzenie do programowania grafiki](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md).</span><span class="sxs-lookup"><span data-stu-id="6f649-111">If you'd like to jump in and get started right away, see [Getting Started with Graphics Programming](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md).</span></span> <span data-ttu-id="6f649-112">Ma ona tematy dotyczące sposobu używania kodu do rysowania linii, kształtów, tekst i więcej informacji na temat formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6f649-112">It has topics on how to use code to draw lines, shapes, text, and more on Windows forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6f649-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="6f649-113">In This Section</span></span>  
 [<span data-ttu-id="6f649-114">Przegląd grafiki</span><span class="sxs-lookup"><span data-stu-id="6f649-114">Graphics Overview</span></span>](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 <span data-ttu-id="6f649-115">Wprowadzenie do zarządzanej klasy powiązane grafiki.</span><span class="sxs-lookup"><span data-stu-id="6f649-115">Provides an introduction to the graphics-related managed classes.</span></span>  
  
 [<span data-ttu-id="6f649-116">Kodzie zarządzanym GDI + — informacje</span><span class="sxs-lookup"><span data-stu-id="6f649-116">About GDI+ Managed Code</span></span>](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 <span data-ttu-id="6f649-117">Zawiera informacje o zarządzanych [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] klasy.</span><span class="sxs-lookup"><span data-stu-id="6f649-117">Provides information about the managed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes.</span></span>  
  
 [<span data-ttu-id="6f649-118">Używanie zarządzanych klas grafiki</span><span class="sxs-lookup"><span data-stu-id="6f649-118">Using Managed Graphics Classes</span></span>](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 <span data-ttu-id="6f649-119">Pokazuje, jak wykonywać różne zadania przy użyciu [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] zarządzanych klas.</span><span class="sxs-lookup"><span data-stu-id="6f649-119">Demonstrates how to complete a variety of tasks using the [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] managed classes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6f649-120">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="6f649-120">Reference</span></span>  
 <xref:System.Drawing>  
 <span data-ttu-id="6f649-121">Zapewnia dostęp do [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funkcje graficzne podstawowe.</span><span class="sxs-lookup"><span data-stu-id="6f649-121">Provides access to [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] basic graphics functionality.</span></span>  
  
 <xref:System.Drawing.Drawing2D>  
 <span data-ttu-id="6f649-122">Udostępnia zaawansowane dwuwymiarowa i wektorów funkcje graficzne.</span><span class="sxs-lookup"><span data-stu-id="6f649-122">Provides advanced two-dimensional and vector graphics functionality.</span></span>  
  
 <xref:System.Drawing.Imaging>  
 <span data-ttu-id="6f649-123">Udostępnia zaawansowane [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funkcje obsługi obrazów.</span><span class="sxs-lookup"><span data-stu-id="6f649-123">Provides advanced [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] imaging functionality.</span></span>  
  
 <xref:System.Drawing.Text>  
 <span data-ttu-id="6f649-124">Udostępnia zaawansowane [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] typografii funkcji.</span><span class="sxs-lookup"><span data-stu-id="6f649-124">Provides advanced [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] typography functionality.</span></span> <span data-ttu-id="6f649-125">Klasy w tej przestrzeni nazw może służyć do tworzenia i używania kolekcji czcionek.</span><span class="sxs-lookup"><span data-stu-id="6f649-125">The classes in this namespace can be used to create and use collections of fonts.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="6f649-126">Udostępnia funkcję drukowania.</span><span class="sxs-lookup"><span data-stu-id="6f649-126">Provides printing functionality.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6f649-127">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="6f649-127">Related Sections</span></span>  
 [<span data-ttu-id="6f649-128">Malowanie i renderowanie formantu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="6f649-128">Custom Control Painting and Rendering</span></span>](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="6f649-129">Szczegółowe informacje dotyczące Podaj kod rysowania formantów.</span><span class="sxs-lookup"><span data-stu-id="6f649-129">Details how to provide code for painting controls.</span></span>
