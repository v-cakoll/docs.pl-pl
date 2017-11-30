---
title: "Używanie czcionek i tekstu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing in Windows Forms
- examples [Windows Forms], fonts and text
- fonts [Windows Forms], using in Windows Forms
- strings [Windows Forms], drawing in Windows Forms
ms.assetid: d43640f3-da94-4df2-a29d-a9d021a1c069
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c18dde7265a07eb45e0211a882b19acc6342e924
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="using-fonts-and-text"></a><span data-ttu-id="63cb2-102">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="63cb2-102">Using Fonts and Text</span></span>
<span data-ttu-id="63cb2-103">Istnieje kilka klas oferowane przez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] i [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] dla Rysowanie tekstu w formularzach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="63cb2-103">There are several classes offered by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] for drawing text on Windows Forms.</span></span> <span data-ttu-id="63cb2-104">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> Klasa ma kilka <xref:System.Drawing.Graphics.DrawString%2A> metod, które pozwalają określić różne funkcje tekstu, na przykład lokalizacji obwiedni prostokąta, czcionki i format.</span><span class="sxs-lookup"><span data-stu-id="63cb2-104">The [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> class has several <xref:System.Drawing.Graphics.DrawString%2A> methods that allow you to specify various features of text, such as location, bounding rectangle, font, and format.</span></span> <span data-ttu-id="63cb2-105">Ponadto rysowania i pomiar tekst z [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] przy użyciu statycznych <xref:System.Windows.Forms.TextRenderer.DrawText%2A> i <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> metody oferowane przez `TextRenderer` klasy.</span><span class="sxs-lookup"><span data-stu-id="63cb2-105">In addition, you can draw and measure text with [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] using the static <xref:System.Windows.Forms.TextRenderer.DrawText%2A> and <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> methods offered by the `TextRenderer` class.</span></span> <span data-ttu-id="63cb2-106">[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] Metody umożliwiają również określenie lokalizacji, czcionki i format.</span><span class="sxs-lookup"><span data-stu-id="63cb2-106">The [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] methods also allow you to specify location, font, and format.</span></span> <span data-ttu-id="63cb2-107">Można wybrać [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] lub [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] do renderowania tekstu; jednak [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] zwykle zapewnia większą wydajność i dokładniejsze pomiaru tekstu.</span><span class="sxs-lookup"><span data-stu-id="63cb2-107">You can choose either [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] or [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] for text rendering; however, [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] generally offers better performance and more accurate text measuring.</span></span> <span data-ttu-id="63cb2-108">Inne klasy, które składają się z renderowaniem tekstu obejmują `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, i `TextFormatFlags`.</span><span class="sxs-lookup"><span data-stu-id="63cb2-108">Other classes that contribute to text rendering include `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, and `TextFormatFlags`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="63cb2-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="63cb2-109">In This Section</span></span>  
 [<span data-ttu-id="63cb2-110">Porady: tworzenie rodzin czcionek i czcionek</span><span class="sxs-lookup"><span data-stu-id="63cb2-110">How to: Construct Font Families and Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 <span data-ttu-id="63cb2-111">Przedstawia sposób tworzenia `Font` i `FontFamily` obiektów.</span><span class="sxs-lookup"><span data-stu-id="63cb2-111">Shows how to create `Font` and `FontFamily` objects.</span></span>  
  
 [<span data-ttu-id="63cb2-112">Porady: Rysowanie tekstu w określonej lokalizacji</span><span class="sxs-lookup"><span data-stu-id="63cb2-112">How to: Draw Text at a Specified Location</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)  
 <span data-ttu-id="63cb2-113">Opisuje sposób Rysowanie tekstu w niektórych lokalizacji przy użyciu [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] i [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63cb2-113">Describes how to draw text in a certain location using [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 [<span data-ttu-id="63cb2-114">Porady: Rysowanie zawiniętego tekstu w prostokącie</span><span class="sxs-lookup"><span data-stu-id="63cb2-114">How to: Draw Wrapped Text in a Rectangle</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)  
 <span data-ttu-id="63cb2-115">Wyjaśniono, jak rysowanie tekstu w prostokącie przy użyciu [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] i [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63cb2-115">Explains how to draw text in a rectangle using [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 [<span data-ttu-id="63cb2-116">Porady: Rysowanie tekstu z GDI</span><span class="sxs-lookup"><span data-stu-id="63cb2-116">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 <span data-ttu-id="63cb2-117">Pokazuje, jak używać [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] rysowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="63cb2-117">Demonstrates how to use [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] for drawing text.</span></span>  
  
 [<span data-ttu-id="63cb2-118">Porady: wyrównywanie narysowanego tekstu</span><span class="sxs-lookup"><span data-stu-id="63cb2-118">How to: Align Drawn Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-align-drawn-text.md)  
 <span data-ttu-id="63cb2-119">Pokazuje sposób formatowania [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] i [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] tekstu.</span><span class="sxs-lookup"><span data-stu-id="63cb2-119">Shows how to format [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] text.</span></span>  
  
 [<span data-ttu-id="63cb2-120">Porady: tworzenie pionowego tekstu</span><span class="sxs-lookup"><span data-stu-id="63cb2-120">How to: Create Vertical Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-vertical-text.md)  
 <span data-ttu-id="63cb2-121">Opisuje sposób Rysuj tekst wyrównany z [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63cb2-121">Describes how to draw vertically aligned text with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
 [<span data-ttu-id="63cb2-122">Porady: ustawienie pozycji tabulatorów w rysowanym tekście</span><span class="sxs-lookup"><span data-stu-id="63cb2-122">How to: Set Tab Stops in Drawn Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-tab-stops-in-drawn-text.md)  
 <span data-ttu-id="63cb2-123">Pokazuje sposób Rysowanie tekstu za pomocą tabulatorów ze [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63cb2-123">Shows how draw text with tab stops with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
 [<span data-ttu-id="63cb2-124">Porady: Wyliczanie zainstalowanych czcionek</span><span class="sxs-lookup"><span data-stu-id="63cb2-124">How to: Enumerate Installed Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-enumerate-installed-fonts.md)  
 <span data-ttu-id="63cb2-125">Wyjaśniono, jak wyświetlić listę nazw zainstalowanych czcionek.</span><span class="sxs-lookup"><span data-stu-id="63cb2-125">Explains how to list the names of installed fonts.</span></span>  
  
 [<span data-ttu-id="63cb2-126">Porady: Tworzenie prywatnej kolekcji czcionek</span><span class="sxs-lookup"><span data-stu-id="63cb2-126">How to: Create a Private Font Collection</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-private-font-collection.md)  
 <span data-ttu-id="63cb2-127">Opisuje sposób tworzenia <xref:System.Drawing.Text.PrivateFontCollection> obiektu.</span><span class="sxs-lookup"><span data-stu-id="63cb2-127">Describes how to create a <xref:System.Drawing.Text.PrivateFontCollection> object.</span></span>  
  
 [<span data-ttu-id="63cb2-128">Porady: uzyskiwanie miar czcionek</span><span class="sxs-lookup"><span data-stu-id="63cb2-128">How to: Obtain Font Metrics</span></span>](../../../../docs/framework/winforms/advanced/how-to-obtain-font-metrics.md)  
 <span data-ttu-id="63cb2-129">Przedstawia sposób uzyskiwanie miar czcionek, takie jak komórki wzrastająca i spadku.</span><span class="sxs-lookup"><span data-stu-id="63cb2-129">Shows how to obtain font metrics such as cell ascent and descent.</span></span>  
  
 [<span data-ttu-id="63cb2-130">Porady: stosowanie antyaliasingu do tekstu</span><span class="sxs-lookup"><span data-stu-id="63cb2-130">How to: Use Antialiasing with Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)  
 <span data-ttu-id="63cb2-131">Wyjaśniono, jak używać antyaliasing podczas rysowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="63cb2-131">Explains how to use antialiasing when drawing text.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="63cb2-132">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="63cb2-132">Reference</span></span>  
 <xref:System.Drawing.Font>  
 <span data-ttu-id="63cb2-133">Ta klasa opisuje i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="63cb2-133">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.FontFamily>  
 <span data-ttu-id="63cb2-134">Ta klasa opisuje i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="63cb2-134">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 <span data-ttu-id="63cb2-135">Ta klasa opisuje i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="63cb2-135">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextRenderer>  
 <span data-ttu-id="63cb2-136">Ta klasa opisuje i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="63cb2-136">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 <span data-ttu-id="63cb2-137">Ta klasa opisuje i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="63cb2-137">Describes this class and contains links to all of its members.</span></span>
