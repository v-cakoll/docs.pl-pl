---
title: 'Porady: stosowanie antyaliasingu do tekstu'
ms.date: 03/30/2017
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
ms.openlocfilehash: 2adb33e3d05e38ee71be8a12cdc2e20dc8c55c72
ms.sourcegitcommit: ceca5a1c027627abcca2767567703c3879f33325
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2018
ms.locfileid: "36338133"
---
# <a name="how-to-use-antialiasing-with-text"></a><span data-ttu-id="ea154-102">Porady: stosowanie antyaliasingu do tekstu</span><span class="sxs-lookup"><span data-stu-id="ea154-102">How to: Use Antialiasing with Text</span></span>
<span data-ttu-id="ea154-103">*Antyaliasing* odwołuje się do wygładzanie nieregularne krawędzi narysowanego grafiki i tekstu, aby zwiększyć ich wyglądu i czytelności.</span><span class="sxs-lookup"><span data-stu-id="ea154-103">*Antialiasing* refers to the smoothing of jagged edges of drawn graphics and text to improve their appearance or readability.</span></span> <span data-ttu-id="ea154-104">Z zarządzanego [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] klas, umożliwiający renderowanie tekstu antyaliasowany wysokiej jakości, jak również niższe jakość tekstu.</span><span class="sxs-lookup"><span data-stu-id="ea154-104">With the managed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes, you can render high quality antialiased text, as well as lower quality text.</span></span> <span data-ttu-id="ea154-105">Zazwyczaj wyższej jakości renderowania potrzebuje więcej czasu przetwarzania niż niższa jakość renderowania.</span><span class="sxs-lookup"><span data-stu-id="ea154-105">Typically, higher quality rendering takes more processing time than lower quality rendering.</span></span> <span data-ttu-id="ea154-106">Aby ustawić poziom jakość tekstu, ustaw <xref:System.Drawing.Graphics.TextRenderingHint%2A> właściwość <xref:System.Drawing.Graphics> do jednego z elementów <xref:System.Drawing.Text.TextRenderingHint> — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ea154-106">To set the text quality level, set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property of a <xref:System.Drawing.Graphics> to one of the elements of the <xref:System.Drawing.Text.TextRenderingHint> enumeration</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea154-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="ea154-107">Example</span></span>  
 <span data-ttu-id="ea154-108">Poniższy przykładowy kod rysuje tekst z dwóch różnych jakości ustawień.</span><span class="sxs-lookup"><span data-stu-id="ea154-108">The following code example draws text with two different quality settings.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
 
 <span data-ttu-id="ea154-109">Na poniższej ilustracji przedstawiono dane wyjściowe przykładowy kod:</span><span class="sxs-lookup"><span data-stu-id="ea154-109">The following illustration shows the output of the example code:</span></span>  
  
 <span data-ttu-id="ea154-110">![Czcionki tekstu](../../../../docs/framework/winforms/advanced/media/fontstext10.png "FontsText10")</span><span class="sxs-lookup"><span data-stu-id="ea154-110">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext10.png "FontsText10")</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ea154-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ea154-111">Compiling the Code</span></span>  
 <span data-ttu-id="ea154-112">W poprzednim przykładzie kodu jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="ea154-112">The preceding code example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea154-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ea154-113">See Also</span></span>  
 [<span data-ttu-id="ea154-114">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="ea154-114">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
