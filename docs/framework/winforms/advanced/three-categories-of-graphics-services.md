---
title: "Trzy kategorie usług grafiki"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- imaging
- graphics [Windows Forms], categories
- 2-D vector graphics
- vector graphics
- typography
ms.assetid: 068c0ef3-f6ee-4d58-a7b6-eb2531ead408
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 305ffae04b6f1ddb94081f8a6ee334f8195caba3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="three-categories-of-graphics-services"></a><span data-ttu-id="c35ed-102">Trzy kategorie usług grafiki</span><span class="sxs-lookup"><span data-stu-id="c35ed-102">Three Categories of Graphics Services</span></span>
<span data-ttu-id="c35ed-103">Oferty grafiki w formularzach systemu Windows można podzielić na następujące trzy kategorie:</span><span class="sxs-lookup"><span data-stu-id="c35ed-103">The graphics offerings in Windows Forms fall into the following three broad categories:</span></span>  
  
-   <span data-ttu-id="c35ed-104">Grafika wektorowa dwuwymiarowa (2-D)</span><span class="sxs-lookup"><span data-stu-id="c35ed-104">Two-dimensional (2-D) vector graphics</span></span>  
  
-   <span data-ttu-id="c35ed-105">Tworzenie obrazów</span><span class="sxs-lookup"><span data-stu-id="c35ed-105">Imaging</span></span>  
  
-   <span data-ttu-id="c35ed-106">Typografia</span><span class="sxs-lookup"><span data-stu-id="c35ed-106">Typography</span></span>  
  
## <a name="2-d-vector-graphics"></a><span data-ttu-id="c35ed-107">Grafika wektorowa 2-D</span><span class="sxs-lookup"><span data-stu-id="c35ed-107">2-D Vector Graphics</span></span>  
 <span data-ttu-id="c35ed-108">Grafika wektorowa dwuwymiarowa są w nim elementów podstawowych; przykład linii, krzywych i rysunki; które zostały określone przez zestawy punktów na układ współrzędnych.</span><span class="sxs-lookup"><span data-stu-id="c35ed-108">Two-dimensional vector graphics are primitives; such as lines, curves, and figures; that are specified by sets of points on a coordinate system.</span></span> <span data-ttu-id="c35ed-109">Na przykład prostej jest określony przez jego dwa punkty końcowe i prostokąt jest określona przez punkt, podając lokalizację jego lewego górnego rogu oraz pary numerów nadanie szerokości i wysokości.</span><span class="sxs-lookup"><span data-stu-id="c35ed-109">For example, a straight line is specified by its two endpoints, and a rectangle is specified by a point giving the location of its upper-left corner and a pair of numbers giving its width and height.</span></span> <span data-ttu-id="c35ed-110">Proste ścieżki jest określany przez tablicę punktów, które są połączone liniami proste.</span><span class="sxs-lookup"><span data-stu-id="c35ed-110">A simple path is specified by an array of points that are connected by straight lines.</span></span> <span data-ttu-id="c35ed-111">Krzywej Beziera jest krzywą zaawansowane określony przez formant cztery punkty.</span><span class="sxs-lookup"><span data-stu-id="c35ed-111">A Bézier spline is a sophisticated curve specified by four control points.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="c35ed-112">zawiera klasy i struktury, w których są przechowywane informacje o podstawowych, samodzielnie, klasy, które przechowywania informacji na temat sposobu będzie rysowany podstawowych i klasy, które faktycznie nie.</span><span class="sxs-lookup"><span data-stu-id="c35ed-112"> provides classes and structures that store information about the primitives themselves, classes that store information about how the primitives will be drawn, and classes that actually do the drawing.</span></span> <span data-ttu-id="c35ed-113">Na przykład <xref:System.Drawing.Rectangle> struktury przechowuje lokalizacja i rozmiar prostokąta; <xref:System.Drawing.Pen> klasy przechowuje informacje dotyczące wiersza kolor, szerokość linii i styl linii; i <xref:System.Drawing.Graphics> klasa zawiera metody służące do rysowania linii, prostokąty, ścieżki, a inne rysunki.</span><span class="sxs-lookup"><span data-stu-id="c35ed-113">For example, the <xref:System.Drawing.Rectangle> structure stores the location and size of a rectangle; the <xref:System.Drawing.Pen> class stores information about line color, line width, and line style; and the <xref:System.Drawing.Graphics> class has methods for drawing lines, rectangles, paths, and other figures.</span></span> <span data-ttu-id="c35ed-114">Istnieją również kilka <xref:System.Drawing.Brush> klasy, które przechowują informacje na temat zamknięte rysunki i ścieżki będzie wypełniona kolorów lub wzorce.</span><span class="sxs-lookup"><span data-stu-id="c35ed-114">There are also several <xref:System.Drawing.Brush> classes that store information about how closed figures and paths will be filled with colors or patterns.</span></span>  
  
 <span data-ttu-id="c35ed-115">Obraz wektora, czyli sekwencji poleceń grafiki, można rejestrować w metaplik.</span><span class="sxs-lookup"><span data-stu-id="c35ed-115">You can record a vector image, which is a sequence of graphics commands, in a metafile.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="c35ed-116">udostępnia <xref:System.Drawing.Imaging.Metafile> klasy rejestrowania, wyświetlanie i zapisywania metapliki.</span><span class="sxs-lookup"><span data-stu-id="c35ed-116"> provides the <xref:System.Drawing.Imaging.Metafile> class for recording, displaying, and saving metafiles.</span></span> <span data-ttu-id="c35ed-117">Z <xref:System.Drawing.Imaging.MetafileHeader> i <xref:System.Drawing.Imaging.MetaHeader> klasy, możesz sprawdzić danych przechowywanych w nagłówku metaplik.</span><span class="sxs-lookup"><span data-stu-id="c35ed-117">With the <xref:System.Drawing.Imaging.MetafileHeader> and <xref:System.Drawing.Imaging.MetaHeader> classes, you can inspect the data stored in a metafile header.</span></span>  
  
## <a name="imaging"></a><span data-ttu-id="c35ed-118">Tworzenie obrazów</span><span class="sxs-lookup"><span data-stu-id="c35ed-118">Imaging</span></span>  
 <span data-ttu-id="c35ed-119">Niektóre rodzaje obrazy są trudne lub niemożliwe do wyświetlenia techniki grafiki wektorowej.</span><span class="sxs-lookup"><span data-stu-id="c35ed-119">Certain kinds of pictures are difficult or impossible to display with the techniques of vector graphics.</span></span> <span data-ttu-id="c35ed-120">Na przykład obrazów na przycisków paska narzędzi i obrazy, które są wyświetlane jako ikony są trudne do określenia jako kolekcje linii i krzywych.</span><span class="sxs-lookup"><span data-stu-id="c35ed-120">For example, the pictures on toolbar buttons and the pictures that appear as icons are difficult to specify as collections of lines and curves.</span></span> <span data-ttu-id="c35ed-121">O wysokiej rozdzielczości cyfrowych fotografii stadium wiele baseball nawet trudniej jest tworzenie techniki wektora.</span><span class="sxs-lookup"><span data-stu-id="c35ed-121">A high-resolution digital photograph of a crowded baseball stadium is even more difficult to create with vector techniques.</span></span> <span data-ttu-id="c35ed-122">Obrazy tego typu są przechowywane jako mapy bitowe, które są tablice liczb, które reprezentują kolory poszczególnych punktów na ekranie.</span><span class="sxs-lookup"><span data-stu-id="c35ed-122">Images of this type are stored as bitmaps, which are arrays of numbers that represent the colors of individual dots on the screen.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="c35ed-123">udostępnia <xref:System.Drawing.Bitmap> klasy wyświetlanie, manipulowanie i Zapisywanie map bitowych.</span><span class="sxs-lookup"><span data-stu-id="c35ed-123"> provides the <xref:System.Drawing.Bitmap> class for displaying, manipulating, and saving bitmaps.</span></span>  
  
## <a name="typography"></a><span data-ttu-id="c35ed-124">Typografia</span><span class="sxs-lookup"><span data-stu-id="c35ed-124">Typography</span></span>  
 <span data-ttu-id="c35ed-125">Typografia jest wyświetlanie tekstu w różnych czcionek, rozmiarów i style.</span><span class="sxs-lookup"><span data-stu-id="c35ed-125">Typography is the display of text in a variety of fonts, sizes, and styles.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="c35ed-126">zapewnia zaawansowaną obsługę tego złożone zadania.</span><span class="sxs-lookup"><span data-stu-id="c35ed-126"> provides extensive support for this complex task.</span></span> <span data-ttu-id="c35ed-127">Jedną z nowych funkcji w [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] antialiasingu subpixel, który zawiera tekst renderowany na ekranie LCD płynniejszy wyglądu.</span><span class="sxs-lookup"><span data-stu-id="c35ed-127">One of the new features in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] is subpixel antialiasing, which gives text rendered on an LCD screen a smoother appearance.</span></span>  
  
 <span data-ttu-id="c35ed-128">Ponadto program Windows Forms oferuje możliwość Rysowanie tekstu za pomocą [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] możliwości w jego <xref:System.Windows.Forms.TextRenderer> klasy.</span><span class="sxs-lookup"><span data-stu-id="c35ed-128">In addition, Windows Forms offers the option to draw text with [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] capabilities in its <xref:System.Windows.Forms.TextRenderer> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c35ed-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c35ed-129">See Also</span></span>  
 [<span data-ttu-id="c35ed-130">Grafika — omówienie</span><span class="sxs-lookup"><span data-stu-id="c35ed-130">Graphics Overview</span></span>](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 [<span data-ttu-id="c35ed-131">Informacje o kodzie zarządzanym GDI+</span><span class="sxs-lookup"><span data-stu-id="c35ed-131">About GDI+ Managed Code</span></span>](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 [<span data-ttu-id="c35ed-132">Używanie zarządzanych klas grafiki</span><span class="sxs-lookup"><span data-stu-id="c35ed-132">Using Managed Graphics Classes</span></span>](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)
