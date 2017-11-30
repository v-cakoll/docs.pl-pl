---
title: 'Porady: stosowanie antyaliasingu do tekstu'
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
- strings [Windows Forms], smoothing drawn
- antialiasing [Windows Forms], using with text
- text [Windows Forms], smoothing
- text [Windows Forms], antialiasing
- strings [Windows Forms], antialiasing when drawing
ms.assetid: 48fc34f3-f236-4b01-a0cb-f0752e6d22ae
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb5a57f8bcbdc1edad78dcd48ad495a187bbb44a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-use-antialiasing-with-text"></a><span data-ttu-id="c9213-102">Porady: stosowanie antyaliasingu do tekstu</span><span class="sxs-lookup"><span data-stu-id="c9213-102">How to: Use Antialiasing with Text</span></span>
<span data-ttu-id="c9213-103">*Antyaliasing* odwołuje się do wygładzanie nieregularne krawędzi narysowanego grafiki i tekstu, aby zwiększyć ich wyglądu i czytelności.</span><span class="sxs-lookup"><span data-stu-id="c9213-103">*Antialiasing* refers to the smoothing of jagged edges of drawn graphics and text to improve their appearance or readability.</span></span> <span data-ttu-id="c9213-104">Z zarządzanego [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] klas, umożliwiający renderowanie tekstu antyaliasowany wysokiej jakości, jak również niższe jakość tekstu.</span><span class="sxs-lookup"><span data-stu-id="c9213-104">With the managed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes, you can render high quality antialiased text, as well as lower quality text.</span></span> <span data-ttu-id="c9213-105">Zazwyczaj wyższej jakości renderowania potrzebuje więcej czasu przetwarzania niż niższa jakość renderowania.</span><span class="sxs-lookup"><span data-stu-id="c9213-105">Typically, higher quality rendering takes more processing time than lower quality rendering.</span></span> <span data-ttu-id="c9213-106">Aby ustawić poziom jakość tekstu, ustaw <xref:System.Drawing.Graphics.TextRenderingHint%2A> właściwość <xref:System.Drawing.Graphics> do jednego z elementów <xref:System.Drawing.Text.TextRenderingHint> — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c9213-106">To set the text quality level, set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property of a <xref:System.Drawing.Graphics> to one of the elements of the <xref:System.Drawing.Text.TextRenderingHint> enumeration</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9213-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="c9213-107">Example</span></span>  
 <span data-ttu-id="c9213-108">Poniższy przykładowy kod rysuje tekst z dwóch różnych jakości ustawień.</span><span class="sxs-lookup"><span data-stu-id="c9213-108">The following code example draws text with two different quality settings.</span></span>  
  
 <span data-ttu-id="c9213-109">Na poniższej ilustracji przedstawiono dane wyjściowe cod przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="c9213-109">The following illustration shows the output of the cod example code.</span></span>  
  
 <span data-ttu-id="c9213-110">![Czcionki tekstu](../../../../docs/framework/winforms/advanced/media/fontstext10.png "FontsText10")</span><span class="sxs-lookup"><span data-stu-id="c9213-110">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext10.png "FontsText10")</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c9213-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c9213-111">Compiling the Code</span></span>  
 <span data-ttu-id="c9213-112">W poprzednim przykładzie kodu jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="c9213-112">The preceding code example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9213-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9213-113">See Also</span></span>  
 [<span data-ttu-id="c9213-114">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="c9213-114">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
