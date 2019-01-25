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
ms.openlocfilehash: 6f939ab90252697d09d594e4d9300ec101c8f2e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540679"
---
# <a name="how-to-construct-font-families-and-fonts"></a><span data-ttu-id="3b848-102">Instrukcje: Tworzenie rodzin czcionek i czcionek</span><span class="sxs-lookup"><span data-stu-id="3b848-102">How to: Construct Font Families and Fonts</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="3b848-103">grupuje czcionki o tej samej krój czcionki, ale różnych stylów do rodziny czcionek.</span><span class="sxs-lookup"><span data-stu-id="3b848-103">groups fonts with the same typeface but different styles into font families.</span></span> <span data-ttu-id="3b848-104">Na przykład rodziny czcionka Arial zawiera następujące czcionki:</span><span class="sxs-lookup"><span data-stu-id="3b848-104">For example, the Arial font family contains the following fonts:</span></span>  
  
-   <span data-ttu-id="3b848-105">Regularne Arial</span><span class="sxs-lookup"><span data-stu-id="3b848-105">Arial Regular</span></span>  
  
-   <span data-ttu-id="3b848-106">Arial pogrubienia</span><span class="sxs-lookup"><span data-stu-id="3b848-106">Arial Bold</span></span>  
  
-   <span data-ttu-id="3b848-107">Kursywa Arial</span><span class="sxs-lookup"><span data-stu-id="3b848-107">Arial Italic</span></span>  
  
-   <span data-ttu-id="3b848-108">Arial Bold Italic</span><span class="sxs-lookup"><span data-stu-id="3b848-108">Arial Bold Italic</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="3b848-109">używa czterech stylów do formularza rodzin: regularnych, pogrubienie, kursywa i pogrubiona kursywa.</span><span class="sxs-lookup"><span data-stu-id="3b848-109">uses four styles to form families: regular, bold, italic, and bold italic.</span></span> <span data-ttu-id="3b848-110">Określeniem, takie jak *zawęzić* i *zaokrąglone* nie są uważane za style; przeciwnie są one częścią nazwę rodziny.</span><span class="sxs-lookup"><span data-stu-id="3b848-110">Adjectives such as *narrow* and *rounded* are not considered styles; rather they are part of the family name.</span></span> <span data-ttu-id="3b848-111">Na przykład Arial Narrow jest rodzinę czcionek, za pomocą następujących elementów członkowskich:</span><span class="sxs-lookup"><span data-stu-id="3b848-111">For example, Arial Narrow is a font family with the following members:</span></span>  
  
-   <span data-ttu-id="3b848-112">Arial zwykłych Narrow</span><span class="sxs-lookup"><span data-stu-id="3b848-112">Arial Narrow Regular</span></span>  
  
-   <span data-ttu-id="3b848-113">Wąski Arial pogrubienia</span><span class="sxs-lookup"><span data-stu-id="3b848-113">Arial Narrow Bold</span></span>  
  
-   <span data-ttu-id="3b848-114">Arial wąskie kursywa</span><span class="sxs-lookup"><span data-stu-id="3b848-114">Arial Narrow Italic</span></span>  
  
-   <span data-ttu-id="3b848-115">Arial wąskie pogrubiona kursywa</span><span class="sxs-lookup"><span data-stu-id="3b848-115">Arial Narrow Bold Italic</span></span>  
  
 <span data-ttu-id="3b848-116">Zanim można rysować tekst z [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], musisz utworzyć <xref:System.Drawing.FontFamily> obiektu i <xref:System.Drawing.Font> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3b848-116">Before you can draw text with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you need to construct a <xref:System.Drawing.FontFamily> object and a <xref:System.Drawing.Font> object.</span></span> <span data-ttu-id="3b848-117"><xref:System.Drawing.FontFamily> Obiektu określa krój czcionki (na przykład Arial), a <xref:System.Drawing.Font> obiekt Określa rozmiar, styl i jednostek.</span><span class="sxs-lookup"><span data-stu-id="3b848-117">The <xref:System.Drawing.FontFamily> object specifies the typeface (for example, Arial), and the <xref:System.Drawing.Font> object specifies the size, style, and units.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b848-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="3b848-118">Example</span></span>  
 <span data-ttu-id="3b848-119">Poniższy przykład tworzy stylu normalnego czcionka Arial o rozmiarze 16 pikseli.</span><span class="sxs-lookup"><span data-stu-id="3b848-119">The following example constructs a regular style Arial font with a size of 16 pixels.</span></span> <span data-ttu-id="3b848-120">W poniższym kodzie pierwszy argument przekazany do <xref:System.Drawing.Font.%23ctor%2A> Konstruktor jest <xref:System.Drawing.FontFamily> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3b848-120">In the following code, the first argument passed to the <xref:System.Drawing.Font.%23ctor%2A> constructor is the <xref:System.Drawing.FontFamily> object.</span></span> <span data-ttu-id="3b848-121">Drugi argument określa rozmiar czcionki, mierzoną w jednostkach identyfikowane przez czwarty argument.</span><span class="sxs-lookup"><span data-stu-id="3b848-121">The second argument specifies the size of the font measured in units identified by the fourth argument.</span></span> <span data-ttu-id="3b848-122">Trzeci argument określa styl.</span><span class="sxs-lookup"><span data-stu-id="3b848-122">The third argument identifies the style.</span></span>  
  
 <span data-ttu-id="3b848-123"><xref:System.Drawing.GraphicsUnit.Pixel> jest elementem członkowskim <xref:System.Drawing.GraphicsUnit> wyliczenia, a <xref:System.Drawing.FontStyle.Regular> jest elementem członkowskim <xref:System.Drawing.FontStyle> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="3b848-123"><xref:System.Drawing.GraphicsUnit.Pixel> is a member of the <xref:System.Drawing.GraphicsUnit> enumeration, and <xref:System.Drawing.FontStyle.Regular> is a member of the <xref:System.Drawing.FontStyle> enumeration.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.FontsAndText#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3b848-124">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="3b848-124">Compiling the Code</span></span>  
 <span data-ttu-id="3b848-125">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="3b848-125">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b848-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b848-126">See also</span></span>
- [<span data-ttu-id="3b848-127">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="3b848-127">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
- [<span data-ttu-id="3b848-128">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3b848-128">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
