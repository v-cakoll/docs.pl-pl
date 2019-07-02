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
ms.openlocfilehash: 73a4af5fe7367e777fcb83af8c84c09be91e5b1e
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505119"
---
# <a name="using-fonts-and-text"></a><span data-ttu-id="45703-102">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="45703-102">Using Fonts and Text</span></span>
<span data-ttu-id="45703-103">Istnieje kilka klas oferowana przez GDI + i z użyciem interfejsu GDI dla Rysowanie tekstu w formularzach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="45703-103">There are several classes offered by GDI+ and GDI for drawing text on Windows Forms.</span></span> <span data-ttu-id="45703-104">GDI + <xref:System.Drawing.Graphics> klasy ma kilka <xref:System.Drawing.Graphics.DrawString%2A> metod, które pozwalają określić różne funkcje tekstu, takie jak lokalizacja, blokujących prostokąt, czcionki i formatowanie.</span><span class="sxs-lookup"><span data-stu-id="45703-104">The GDI+ <xref:System.Drawing.Graphics> class has several <xref:System.Drawing.Graphics.DrawString%2A> methods that allow you to specify various features of text, such as location, bounding rectangle, font, and format.</span></span> <span data-ttu-id="45703-105">Ponadto narysuj i mierzyć tekstu z GDI przy użyciu statycznych <xref:System.Windows.Forms.TextRenderer.DrawText%2A> i <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> metody oferowane przez `TextRenderer` klasy.</span><span class="sxs-lookup"><span data-stu-id="45703-105">In addition, you can draw and measure text with GDI using the static <xref:System.Windows.Forms.TextRenderer.DrawText%2A> and <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> methods offered by the `TextRenderer` class.</span></span> <span data-ttu-id="45703-106">Metody interfejsu GDI pozwalają również określić lokalizację, czcionki i formatowanie.</span><span class="sxs-lookup"><span data-stu-id="45703-106">The GDI methods also allow you to specify location, font, and format.</span></span> <span data-ttu-id="45703-107">Możesz wybrać do renderowania tekstu; GDI lub GDI + jednak GDI ogólnie oferuje lepszą wydajność i bardziej dokładne pomiary tekstu.</span><span class="sxs-lookup"><span data-stu-id="45703-107">You can choose either GDI or GDI+ for text rendering; however, GDI generally offers better performance and more accurate text measuring.</span></span> <span data-ttu-id="45703-108">Inne klasy, które przyczyniają się do renderowania tekstu obejmują `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, i `TextFormatFlags`.</span><span class="sxs-lookup"><span data-stu-id="45703-108">Other classes that contribute to text rendering include `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, and `TextFormatFlags`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45703-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="45703-109">In This Section</span></span>  
 [<span data-ttu-id="45703-110">Instrukcje: Tworzenie rodzin czcionek i czcionek</span><span class="sxs-lookup"><span data-stu-id="45703-110">How to: Construct Font Families and Fonts</span></span>](how-to-construct-font-families-and-fonts.md)  
 <span data-ttu-id="45703-111">Pokazuje, jak utworzyć `Font` i `FontFamily` obiektów.</span><span class="sxs-lookup"><span data-stu-id="45703-111">Shows how to create `Font` and `FontFamily` objects.</span></span>  
  
 [<span data-ttu-id="45703-112">Instrukcje: Rysowanie tekstu w określonej lokalizacji</span><span class="sxs-lookup"><span data-stu-id="45703-112">How to: Draw Text at a Specified Location</span></span>](how-to-draw-text-at-a-specified-location.md)  
 <span data-ttu-id="45703-113">Opisuje sposób Rysowanie tekstu w określonej lokalizacji za pomocą GDI + i GDI.</span><span class="sxs-lookup"><span data-stu-id="45703-113">Describes how to draw text in a certain location using GDI+ and GDI.</span></span>  
  
 [<span data-ttu-id="45703-114">Instrukcje: Rysowanie zawiniętego tekstu w prostokącie</span><span class="sxs-lookup"><span data-stu-id="45703-114">How to: Draw Wrapped Text in a Rectangle</span></span>](how-to-draw-wrapped-text-in-a-rectangle.md)  
 <span data-ttu-id="45703-115">Wyjaśnia, jak rysowanie tekstu w prostokącie za pomocą GDI + i GDI.</span><span class="sxs-lookup"><span data-stu-id="45703-115">Explains how to draw text in a rectangle using GDI+ and GDI.</span></span>  
  
 [<span data-ttu-id="45703-116">Instrukcje: Rysowanie tekstu za pomocą GDI</span><span class="sxs-lookup"><span data-stu-id="45703-116">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)  
 <span data-ttu-id="45703-117">Pokazuje sposób użycia interfejsu GDI rysowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="45703-117">Demonstrates how to use GDI for drawing text.</span></span>  
  
 [<span data-ttu-id="45703-118">Instrukcje: Wyrównywanie narysowanego tekstu</span><span class="sxs-lookup"><span data-stu-id="45703-118">How to: Align Drawn Text</span></span>](how-to-align-drawn-text.md)  
 <span data-ttu-id="45703-119">Pokazuje sposób formatowania tekstu w GDI + i GDI.</span><span class="sxs-lookup"><span data-stu-id="45703-119">Shows how to format GDI+ and GDI text.</span></span>  
  
 [<span data-ttu-id="45703-120">Instrukcje: Tworzenie pionowego tekstu</span><span class="sxs-lookup"><span data-stu-id="45703-120">How to: Create Vertical Text</span></span>](how-to-create-vertical-text.md)  
 <span data-ttu-id="45703-121">W tym artykule opisano, jak rysować tekst wyrównany z użyciem interfejsu GDI +.</span><span class="sxs-lookup"><span data-stu-id="45703-121">Describes how to draw vertically aligned text with GDI+.</span></span>  
  
 [<span data-ttu-id="45703-122">Instrukcje: Ustawienie pozycji tabulatorów w rysowanym tekście</span><span class="sxs-lookup"><span data-stu-id="45703-122">How to: Set Tab Stops in Drawn Text</span></span>](how-to-set-tab-stops-in-drawn-text.md)  
 <span data-ttu-id="45703-123">Pokazuje jak rysowanie tekstu za pomocą tabulatorów za pomocą GDI +.</span><span class="sxs-lookup"><span data-stu-id="45703-123">Shows how draw text with tab stops with GDI+.</span></span>  
  
 [<span data-ttu-id="45703-124">Instrukcje: Wyliczanie zainstalowanych czcionek</span><span class="sxs-lookup"><span data-stu-id="45703-124">How to: Enumerate Installed Fonts</span></span>](how-to-enumerate-installed-fonts.md)  
 <span data-ttu-id="45703-125">Wyjaśnia, jak wyświetlić listę nazw zainstalowanych czcionek.</span><span class="sxs-lookup"><span data-stu-id="45703-125">Explains how to list the names of installed fonts.</span></span>  
  
 [<span data-ttu-id="45703-126">Instrukcje: Tworzenie prywatnej kolekcji czcionek</span><span class="sxs-lookup"><span data-stu-id="45703-126">How to: Create a Private Font Collection</span></span>](how-to-create-a-private-font-collection.md)  
 <span data-ttu-id="45703-127">W tym artykule opisano sposób tworzenia <xref:System.Drawing.Text.PrivateFontCollection> obiektu.</span><span class="sxs-lookup"><span data-stu-id="45703-127">Describes how to create a <xref:System.Drawing.Text.PrivateFontCollection> object.</span></span>  
  
 [<span data-ttu-id="45703-128">Instrukcje: Uzyskiwanie miar czcionek</span><span class="sxs-lookup"><span data-stu-id="45703-128">How to: Obtain Font Metrics</span></span>](how-to-obtain-font-metrics.md)  
 <span data-ttu-id="45703-129">Pokazuje, jak uzyskiwanie miar czcionek, takie jak i zejścia komórki.</span><span class="sxs-lookup"><span data-stu-id="45703-129">Shows how to obtain font metrics such as cell ascent and descent.</span></span>  
  
 [<span data-ttu-id="45703-130">Instrukcje: Stosowanie antyaliasingu do tekstu</span><span class="sxs-lookup"><span data-stu-id="45703-130">How to: Use Antialiasing with Text</span></span>](how-to-use-antialiasing-with-text.md)  
 <span data-ttu-id="45703-131">Wyjaśnia, jak używać antyaliasing podczas rysowania tekstu.</span><span class="sxs-lookup"><span data-stu-id="45703-131">Explains how to use antialiasing when drawing text.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="45703-132">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="45703-132">Reference</span></span>  
 <xref:System.Drawing.Font>  
 <span data-ttu-id="45703-133">Zawiera opis tej klasy i zawiera łącza do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="45703-133">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.FontFamily>  
 <span data-ttu-id="45703-134">Zawiera opis tej klasy i zawiera łącza do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="45703-134">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 <span data-ttu-id="45703-135">Zawiera opis tej klasy i zawiera łącza do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="45703-135">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextRenderer>  
 <span data-ttu-id="45703-136">Zawiera opis tej klasy i zawiera łącza do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="45703-136">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 <span data-ttu-id="45703-137">Zawiera opis tej klasy i zawiera łącza do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="45703-137">Describes this class and contains links to all of its members.</span></span>
