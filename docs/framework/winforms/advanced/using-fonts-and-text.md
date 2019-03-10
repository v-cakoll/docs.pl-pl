---
title: Używanie czcionek i tekstu
ms.date: 03/30/2017
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing in Windows Forms
- examples [Windows Forms], fonts and text
- fonts [Windows Forms], using in Windows Forms
- strings [Windows Forms], drawing in Windows Forms
ms.assetid: d43640f3-da94-4df2-a29d-a9d021a1c069
ms.openlocfilehash: c9fe16752223203806c7d3828f632aad0cab0c28
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703373"
---
# <a name="using-fonts-and-text"></a><span data-ttu-id="0911b-102">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="0911b-102">Using Fonts and Text</span></span>
<span data-ttu-id="0911b-103">Istnieje kilka klas, oferowane przez [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] i [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] dla Rysowanie tekstu w formularzach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0911b-103">There are several classes offered by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] for drawing text on Windows Forms.</span></span> <span data-ttu-id="0911b-104">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> Klasy ma kilka <xref:System.Drawing.Graphics.DrawString%2A> metod, które pozwalają określić różne funkcje tekstu, takie jak lokalizacja, blokujących prostokąt, czcionki i formatowanie.</span><span class="sxs-lookup"><span data-stu-id="0911b-104">The [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> class has several <xref:System.Drawing.Graphics.DrawString%2A> methods that allow you to specify various features of text, such as location, bounding rectangle, font, and format.</span></span> <span data-ttu-id="0911b-105">Ponadto narysuj i mierzyć tekstu za pomocą [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] przy użyciu statycznych <xref:System.Windows.Forms.TextRenderer.DrawText%2A> i <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> metody oferowane przez `TextRenderer` klasy.</span><span class="sxs-lookup"><span data-stu-id="0911b-105">In addition, you can draw and measure text with [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] using the static <xref:System.Windows.Forms.TextRenderer.DrawText%2A> and <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> methods offered by the `TextRenderer` class.</span></span> <span data-ttu-id="0911b-106">[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] Metody pozwalają również określić lokalizację, czcionki i formatowanie.</span><span class="sxs-lookup"><span data-stu-id="0911b-106">The [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] methods also allow you to specify location, font, and format.</span></span> <span data-ttu-id="0911b-107">Możesz wybrać dowolną [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] lub [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] do renderowania tekstu; jednak [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] zwykle zapewnia większą wydajność i bardziej dokładne pomiary tekstu.</span><span class="sxs-lookup"><span data-stu-id="0911b-107">You can choose either [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] or [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] for text rendering; however, [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] generally offers better performance and more accurate text measuring.</span></span> <span data-ttu-id="0911b-108">Inne klasy, które przyczyniają się do renderowania tekstu obejmują `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, i `TextFormatFlags`.</span><span class="sxs-lookup"><span data-stu-id="0911b-108">Other classes that contribute to text rendering include `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, and `TextFormatFlags`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0911b-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="0911b-109">In This Section</span></span>  
 [<span data-ttu-id="0911b-110">Instrukcje: Tworzenie rodzin czcionek i czcionek</span><span class="sxs-lookup"><span data-stu-id="0911b-110">How to: Construct Font Families and Fonts</span></span>](how-to-construct-font-families-and-fonts.md)  
 <span data-ttu-id="0911b-111">Pokazuje, jak utworzyć `Font` i `FontFamily` obiektów.</span><span class="sxs-lookup"><span data-stu-id="0911b-111">Shows how to create `Font` and `FontFamily` objects.</span></span>  
  
 [<span data-ttu-id="0911b-112">Instrukcje: Rysowanie tekstu w określonej lokalizacji</span><span class="sxs-lookup"><span data-stu-id="0911b-112">How to: Draw Text at a Specified Location</span></span>](how-to-draw-text-at-a-specified-location.md)  
 <span data-ttu-id="0911b-113">W tym artykule opisano jak rysować tekst w określonych lokalizacji za pomocą [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] i [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0911b-113">Describes how to draw text in a certain location using [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 [<span data-ttu-id="0911b-114">Instrukcje: Rysowanie zawiniętego tekstu w prostokącie</span><span class="sxs-lookup"><span data-stu-id="0911b-114">How to: Draw Wrapped Text in a Rectangle</span></span>](how-to-draw-wrapped-text-in-a-rectangle.md)  
 <span data-ttu-id="0911b-115">Wyjaśnia, jak rysowanie tekstu w prostokącie za pomocą [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] i [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0911b-115">Explains how to draw text in a rectangle using [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 [<span data-ttu-id="0911b-116">Instrukcje: Rysowanie tekstu za pomocą GDI</span><span class="sxs-lookup"><span data-stu-id="0911b-116">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)  
 <span data-ttu-id="0911b-117">Pokazuje sposób użycia [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] rysowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="0911b-117">Demonstrates how to use [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] for drawing text.</span></span>  
  
 [<span data-ttu-id="0911b-118">Instrukcje: Wyrównywanie narysowanego tekstu</span><span class="sxs-lookup"><span data-stu-id="0911b-118">How to: Align Drawn Text</span></span>](how-to-align-drawn-text.md)  
 <span data-ttu-id="0911b-119">Pokazuje, jak sformatować [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] i [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] tekstu.</span><span class="sxs-lookup"><span data-stu-id="0911b-119">Shows how to format [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] text.</span></span>  
  
 [<span data-ttu-id="0911b-120">Instrukcje: Tworzenie pionowego tekstu</span><span class="sxs-lookup"><span data-stu-id="0911b-120">How to: Create Vertical Text</span></span>](how-to-create-vertical-text.md)  
 <span data-ttu-id="0911b-121">W tym artykule opisano jak rysować tekst wyrównany z [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0911b-121">Describes how to draw vertically aligned text with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
 [<span data-ttu-id="0911b-122">Instrukcje: Ustawienie pozycji tabulatorów w rysowanym tekście</span><span class="sxs-lookup"><span data-stu-id="0911b-122">How to: Set Tab Stops in Drawn Text</span></span>](how-to-set-tab-stops-in-drawn-text.md)  
 <span data-ttu-id="0911b-123">Pokazuje, jak rysowanie tekstu za pomocą tabulatorów ze [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0911b-123">Shows how draw text with tab stops with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
 [<span data-ttu-id="0911b-124">Instrukcje: Wyliczanie zainstalowanych czcionek</span><span class="sxs-lookup"><span data-stu-id="0911b-124">How to: Enumerate Installed Fonts</span></span>](how-to-enumerate-installed-fonts.md)  
 <span data-ttu-id="0911b-125">Wyjaśnia, jak wyświetlić listę nazw zainstalowanych czcionek.</span><span class="sxs-lookup"><span data-stu-id="0911b-125">Explains how to list the names of installed fonts.</span></span>  
  
 [<span data-ttu-id="0911b-126">Instrukcje: Tworzenie prywatnej kolekcji czcionek</span><span class="sxs-lookup"><span data-stu-id="0911b-126">How to: Create a Private Font Collection</span></span>](how-to-create-a-private-font-collection.md)  
 <span data-ttu-id="0911b-127">W tym artykule opisano sposób tworzenia <xref:System.Drawing.Text.PrivateFontCollection> obiektu.</span><span class="sxs-lookup"><span data-stu-id="0911b-127">Describes how to create a <xref:System.Drawing.Text.PrivateFontCollection> object.</span></span>  
  
 [<span data-ttu-id="0911b-128">Instrukcje: Uzyskiwanie miar czcionek</span><span class="sxs-lookup"><span data-stu-id="0911b-128">How to: Obtain Font Metrics</span></span>](how-to-obtain-font-metrics.md)  
 <span data-ttu-id="0911b-129">Pokazuje, jak uzyskiwanie miar czcionek, takie jak i zejścia komórki.</span><span class="sxs-lookup"><span data-stu-id="0911b-129">Shows how to obtain font metrics such as cell ascent and descent.</span></span>  
  
 [<span data-ttu-id="0911b-130">Instrukcje: Stosowanie antyaliasingu do tekstu</span><span class="sxs-lookup"><span data-stu-id="0911b-130">How to: Use Antialiasing with Text</span></span>](how-to-use-antialiasing-with-text.md)  
 <span data-ttu-id="0911b-131">Wyjaśnia, jak używać antyaliasing podczas rysowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="0911b-131">Explains how to use antialiasing when drawing text.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0911b-132">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="0911b-132">Reference</span></span>  
 <xref:System.Drawing.Font>  
 <span data-ttu-id="0911b-133">Zawiera opis tej klasy i zawiera łącza do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="0911b-133">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.FontFamily>  
 <span data-ttu-id="0911b-134">Zawiera opis tej klasy i zawiera łącza do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="0911b-134">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 <span data-ttu-id="0911b-135">Zawiera opis tej klasy i zawiera łącza do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="0911b-135">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextRenderer>  
 <span data-ttu-id="0911b-136">Zawiera opis tej klasy i zawiera łącza do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="0911b-136">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 <span data-ttu-id="0911b-137">Zawiera opis tej klasy i zawiera łącza do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="0911b-137">Describes this class and contains links to all of its members.</span></span>
