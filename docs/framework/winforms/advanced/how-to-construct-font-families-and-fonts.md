---
title: 'Porady: tworzenie rodzin czcionek i czcionek'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- font families [Windows Forms], constructing
- fonts [Windows Forms], constructing
ms.assetid: d3a4a223-9492-4b54-9afd-db1c31c3cefd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e152c525550554082d7d6c38a972ccc150adabb9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-construct-font-families-and-fonts"></a><span data-ttu-id="0b12d-102">Porady: tworzenie rodzin czcionek i czcionek</span><span class="sxs-lookup"><span data-stu-id="0b12d-102">How to: Construct Font Families and Fonts</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="0b12d-103">grupuje czcionek z tej samej krój, ale różnych stylów do rodziny czcionek.</span><span class="sxs-lookup"><span data-stu-id="0b12d-103"> groups fonts with the same typeface but different styles into font families.</span></span> <span data-ttu-id="0b12d-104">Na przykład rodziny czcionek Arial zawiera następujące czcionki:</span><span class="sxs-lookup"><span data-stu-id="0b12d-104">For example, the Arial font family contains the following fonts:</span></span>  
  
-   <span data-ttu-id="0b12d-105">Regularne Arial</span><span class="sxs-lookup"><span data-stu-id="0b12d-105">Arial Regular</span></span>  
  
-   <span data-ttu-id="0b12d-106">Arial Bold</span><span class="sxs-lookup"><span data-stu-id="0b12d-106">Arial Bold</span></span>  
  
-   <span data-ttu-id="0b12d-107">Arial kursywa</span><span class="sxs-lookup"><span data-stu-id="0b12d-107">Arial Italic</span></span>  
  
-   <span data-ttu-id="0b12d-108">Arial pogrubienie, kursywa</span><span class="sxs-lookup"><span data-stu-id="0b12d-108">Arial Bold Italic</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="0b12d-109">używa czterech stylów do formularza rodzin: regularne, pogrubienie, kursywa i pogrubienie, kursywa.</span><span class="sxs-lookup"><span data-stu-id="0b12d-109"> uses four styles to form families: regular, bold, italic, and bold italic.</span></span> <span data-ttu-id="0b12d-110">Określeniem, takich jak *zawęzić* i *zaokrąglona* nie są uznawane za style; a nie są one częścią nazwę rodziny.</span><span class="sxs-lookup"><span data-stu-id="0b12d-110">Adjectives such as *narrow* and *rounded* are not considered styles; rather they are part of the family name.</span></span> <span data-ttu-id="0b12d-111">Na przykład Arial Narrow jest rodzinę czcionek z następujących członków:</span><span class="sxs-lookup"><span data-stu-id="0b12d-111">For example, Arial Narrow is a font family with the following members:</span></span>  
  
-   <span data-ttu-id="0b12d-112">Arial Regular wąskie</span><span class="sxs-lookup"><span data-stu-id="0b12d-112">Arial Narrow Regular</span></span>  
  
-   <span data-ttu-id="0b12d-113">Wąskie Arial Bold</span><span class="sxs-lookup"><span data-stu-id="0b12d-113">Arial Narrow Bold</span></span>  
  
-   <span data-ttu-id="0b12d-114">Arial kursywa wąskie</span><span class="sxs-lookup"><span data-stu-id="0b12d-114">Arial Narrow Italic</span></span>  
  
-   <span data-ttu-id="0b12d-115">Arial wąskie pogrubiona kursywa</span><span class="sxs-lookup"><span data-stu-id="0b12d-115">Arial Narrow Bold Italic</span></span>  
  
 <span data-ttu-id="0b12d-116">Przed rozpoczęciem rysowania tekstu w [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], musisz utworzyć <xref:System.Drawing.FontFamily> obiektu i <xref:System.Drawing.Font> obiektu.</span><span class="sxs-lookup"><span data-stu-id="0b12d-116">Before you can draw text with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you need to construct a <xref:System.Drawing.FontFamily> object and a <xref:System.Drawing.Font> object.</span></span> <span data-ttu-id="0b12d-117"><xref:System.Drawing.FontFamily> Obiektu określa krój (na przykład Arial) i <xref:System.Drawing.Font> obiektu określa rozmiar, styl i jednostki.</span><span class="sxs-lookup"><span data-stu-id="0b12d-117">The <xref:System.Drawing.FontFamily> object specifies the typeface (for example, Arial), and the <xref:System.Drawing.Font> object specifies the size, style, and units.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b12d-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="0b12d-118">Example</span></span>  
 <span data-ttu-id="0b12d-119">Poniższy przykład tworzy regularne styl czcionki Arial o rozmiarze 16 pikseli.</span><span class="sxs-lookup"><span data-stu-id="0b12d-119">The following example constructs a regular style Arial font with a size of 16 pixels.</span></span> <span data-ttu-id="0b12d-120">W poniższym kodzie pierwszy argument przekazany do <xref:System.Drawing.Font.%23ctor%2A> Konstruktor jest <xref:System.Drawing.FontFamily> obiektu.</span><span class="sxs-lookup"><span data-stu-id="0b12d-120">In the following code, the first argument passed to the <xref:System.Drawing.Font.%23ctor%2A> constructor is the <xref:System.Drawing.FontFamily> object.</span></span> <span data-ttu-id="0b12d-121">Drugi argument określa rozmiar czcionki, mierzona w jednostkach identyfikowane przez czwarty argument.</span><span class="sxs-lookup"><span data-stu-id="0b12d-121">The second argument specifies the size of the font measured in units identified by the fourth argument.</span></span> <span data-ttu-id="0b12d-122">Trzeci argument określa styl.</span><span class="sxs-lookup"><span data-stu-id="0b12d-122">The third argument identifies the style.</span></span>  
  
 <span data-ttu-id="0b12d-123"><xref:System.Drawing.GraphicsUnit.Pixel>jest elementem członkowskim <xref:System.Drawing.GraphicsUnit> wyliczenia, i <xref:System.Drawing.FontStyle.Regular> jest elementem członkowskim <xref:System.Drawing.FontStyle> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="0b12d-123"><xref:System.Drawing.GraphicsUnit.Pixel> is a member of the <xref:System.Drawing.GraphicsUnit> enumeration, and <xref:System.Drawing.FontStyle.Regular> is a member of the <xref:System.Drawing.FontStyle> enumeration.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.FontsAndText#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0b12d-124">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="0b12d-124">Compiling the Code</span></span>  
 <span data-ttu-id="0b12d-125">Powyższy przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="0b12d-125">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b12d-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0b12d-126">See Also</span></span>  
 [<span data-ttu-id="0b12d-127">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="0b12d-127">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="0b12d-128">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0b12d-128">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
