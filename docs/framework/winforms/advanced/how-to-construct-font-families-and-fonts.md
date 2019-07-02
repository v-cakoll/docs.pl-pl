---
title: 'Instrukcje: Tworzenie rodzin czcionek i czcionek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- font families [Windows Forms], constructing
- fonts [Windows Forms], constructing
ms.assetid: d3a4a223-9492-4b54-9afd-db1c31c3cefd
ms.openlocfilehash: 2d609525858c7a8ff77c0b86900b4fc7d6b4e39a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505947"
---
# <a name="how-to-construct-font-families-and-fonts"></a><span data-ttu-id="7493b-102">Instrukcje: Tworzenie rodzin czcionek i czcionek</span><span class="sxs-lookup"><span data-stu-id="7493b-102">How to: Construct Font Families and Fonts</span></span>
<span data-ttu-id="7493b-103">GDI + grupuje czcionki o tej samej krój czcionki, ale różnych stylów do rodziny czcionek.</span><span class="sxs-lookup"><span data-stu-id="7493b-103">GDI+ groups fonts with the same typeface but different styles into font families.</span></span> <span data-ttu-id="7493b-104">Na przykład rodziny czcionka Arial zawiera następujące czcionki:</span><span class="sxs-lookup"><span data-stu-id="7493b-104">For example, the Arial font family contains the following fonts:</span></span>  
  
- <span data-ttu-id="7493b-105">Regularne Arial</span><span class="sxs-lookup"><span data-stu-id="7493b-105">Arial Regular</span></span>  
  
- <span data-ttu-id="7493b-106">Arial pogrubienia</span><span class="sxs-lookup"><span data-stu-id="7493b-106">Arial Bold</span></span>  
  
- <span data-ttu-id="7493b-107">Kursywa Arial</span><span class="sxs-lookup"><span data-stu-id="7493b-107">Arial Italic</span></span>  
  
- <span data-ttu-id="7493b-108">Arial Bold Italic</span><span class="sxs-lookup"><span data-stu-id="7493b-108">Arial Bold Italic</span></span>  
  
 <span data-ttu-id="7493b-109">GDI + korzysta z czterech style do formularza rodzin: regularnych, pogrubienie, kursywa i pogrubiona kursywa.</span><span class="sxs-lookup"><span data-stu-id="7493b-109">GDI+ uses four styles to form families: regular, bold, italic, and bold italic.</span></span> <span data-ttu-id="7493b-110">Określeniem, takie jak *zawęzić* i *zaokrąglone* nie są uważane za style; przeciwnie są one częścią nazwę rodziny.</span><span class="sxs-lookup"><span data-stu-id="7493b-110">Adjectives such as *narrow* and *rounded* are not considered styles; rather they are part of the family name.</span></span> <span data-ttu-id="7493b-111">Na przykład Arial Narrow jest rodzinę czcionek, za pomocą następujących elementów członkowskich:</span><span class="sxs-lookup"><span data-stu-id="7493b-111">For example, Arial Narrow is a font family with the following members:</span></span>  
  
- <span data-ttu-id="7493b-112">Arial zwykłych Narrow</span><span class="sxs-lookup"><span data-stu-id="7493b-112">Arial Narrow Regular</span></span>  
  
- <span data-ttu-id="7493b-113">Wąski Arial pogrubienia</span><span class="sxs-lookup"><span data-stu-id="7493b-113">Arial Narrow Bold</span></span>  
  
- <span data-ttu-id="7493b-114">Arial wąskie kursywa</span><span class="sxs-lookup"><span data-stu-id="7493b-114">Arial Narrow Italic</span></span>  
  
- <span data-ttu-id="7493b-115">Arial wąskie pogrubiona kursywa</span><span class="sxs-lookup"><span data-stu-id="7493b-115">Arial Narrow Bold Italic</span></span>  
  
 <span data-ttu-id="7493b-116">Można rysować tekst z użyciem interfejsu GDI +, musisz najpierw utworzyć <xref:System.Drawing.FontFamily> obiektu i <xref:System.Drawing.Font> obiektu.</span><span class="sxs-lookup"><span data-stu-id="7493b-116">Before you can draw text with GDI+, you need to construct a <xref:System.Drawing.FontFamily> object and a <xref:System.Drawing.Font> object.</span></span> <span data-ttu-id="7493b-117"><xref:System.Drawing.FontFamily> Obiektu określa krój czcionki (na przykład Arial), a <xref:System.Drawing.Font> obiekt Określa rozmiar, styl i jednostek.</span><span class="sxs-lookup"><span data-stu-id="7493b-117">The <xref:System.Drawing.FontFamily> object specifies the typeface (for example, Arial), and the <xref:System.Drawing.Font> object specifies the size, style, and units.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7493b-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="7493b-118">Example</span></span>  
 <span data-ttu-id="7493b-119">Poniższy przykład tworzy stylu normalnego czcionka Arial o rozmiarze 16 pikseli.</span><span class="sxs-lookup"><span data-stu-id="7493b-119">The following example constructs a regular style Arial font with a size of 16 pixels.</span></span> <span data-ttu-id="7493b-120">W poniższym kodzie pierwszy argument przekazany do <xref:System.Drawing.Font.%23ctor%2A> Konstruktor jest <xref:System.Drawing.FontFamily> obiektu.</span><span class="sxs-lookup"><span data-stu-id="7493b-120">In the following code, the first argument passed to the <xref:System.Drawing.Font.%23ctor%2A> constructor is the <xref:System.Drawing.FontFamily> object.</span></span> <span data-ttu-id="7493b-121">Drugi argument określa rozmiar czcionki, mierzoną w jednostkach identyfikowane przez czwarty argument.</span><span class="sxs-lookup"><span data-stu-id="7493b-121">The second argument specifies the size of the font measured in units identified by the fourth argument.</span></span> <span data-ttu-id="7493b-122">Trzeci argument określa styl.</span><span class="sxs-lookup"><span data-stu-id="7493b-122">The third argument identifies the style.</span></span>  
  
 <span data-ttu-id="7493b-123"><xref:System.Drawing.GraphicsUnit.Pixel> jest elementem członkowskim <xref:System.Drawing.GraphicsUnit> wyliczenia, a <xref:System.Drawing.FontStyle.Regular> jest elementem członkowskim <xref:System.Drawing.FontStyle> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7493b-123"><xref:System.Drawing.GraphicsUnit.Pixel> is a member of the <xref:System.Drawing.GraphicsUnit> enumeration, and <xref:System.Drawing.FontStyle.Regular> is a member of the <xref:System.Drawing.FontStyle> enumeration.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.FontsAndText#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7493b-124">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7493b-124">Compiling the Code</span></span>  
 <span data-ttu-id="7493b-125">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="7493b-125">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7493b-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7493b-126">See also</span></span>

- [<span data-ttu-id="7493b-127">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="7493b-127">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="7493b-128">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7493b-128">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
