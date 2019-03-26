---
title: 'Instrukcje: Stosowanie antyaliasingu do tekstu'
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
ms.openlocfilehash: ffd8600c730baca54a9cbd098dd2f37ce5ecb728
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464726"
---
# <a name="how-to-use-antialiasing-with-text"></a><span data-ttu-id="faf2c-102">Instrukcje: Stosowanie antyaliasingu do tekstu</span><span class="sxs-lookup"><span data-stu-id="faf2c-102">How to: Use Antialiasing with Text</span></span>
<span data-ttu-id="faf2c-103">*Antyaliasing* odwołuje się do wygładzania nierówne krawędzie rysowane grafiki i tekstu w celu zwiększenia ich wyglądu i czytelności.</span><span class="sxs-lookup"><span data-stu-id="faf2c-103">*Antialiasing* refers to the smoothing of jagged edges of drawn graphics and text to improve their appearance or readability.</span></span> <span data-ttu-id="faf2c-104">Za pomocą zarządzanych [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] klas, umożliwiający renderowanie tekstu antialiased wysokiej jakości, a także niższa jakość tekstu.</span><span class="sxs-lookup"><span data-stu-id="faf2c-104">With the managed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes, you can render high quality antialiased text, as well as lower quality text.</span></span> <span data-ttu-id="faf2c-105">Zazwyczaj wyższej jakości renderowania jest bardziej czasochłonne przetwarzania niż niższa jakość renderowania.</span><span class="sxs-lookup"><span data-stu-id="faf2c-105">Typically, higher quality rendering takes more processing time than lower quality rendering.</span></span> <span data-ttu-id="faf2c-106">Aby ustawić poziom jakości tekstu, ustaw <xref:System.Drawing.Graphics.TextRenderingHint%2A> właściwość <xref:System.Drawing.Graphics> do jednego z elementów <xref:System.Drawing.Text.TextRenderingHint> wyliczenia</span><span class="sxs-lookup"><span data-stu-id="faf2c-106">To set the text quality level, set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property of a <xref:System.Drawing.Graphics> to one of the elements of the <xref:System.Drawing.Text.TextRenderingHint> enumeration</span></span>  
  
## <a name="example"></a><span data-ttu-id="faf2c-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="faf2c-107">Example</span></span>  
 <span data-ttu-id="faf2c-108">Poniższy kod rysuje tekst za pomocą dwóch ustawień inną jakość.</span><span class="sxs-lookup"><span data-stu-id="faf2c-108">The following code example draws text with two different quality settings.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
 
 <span data-ttu-id="faf2c-109">Na poniższej ilustracji przedstawiono dane wyjściowe przykładowego kodu:</span><span class="sxs-lookup"><span data-stu-id="faf2c-109">The following illustration shows the output of the example code:</span></span>  
  
 ![Zrzut ekranu pokazujący tekstu za pomocą dwóch ustawień inną jakość.](./media/how-to-use-antialiasing-with-text/antialiasing-text-quality-settings.png)  
  
## <a name="compiling-the-code"></a><span data-ttu-id="faf2c-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="faf2c-111">Compiling the Code</span></span>  
 <span data-ttu-id="faf2c-112">W poprzednim przykładzie kodu jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="faf2c-112">The preceding code example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faf2c-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="faf2c-113">See also</span></span>
- [<span data-ttu-id="faf2c-114">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="faf2c-114">Using Fonts and Text</span></span>](using-fonts-and-text.md)
