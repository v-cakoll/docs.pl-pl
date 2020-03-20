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
ms.openlocfilehash: 632ed329173d134495a424b34ca7c71e402607bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182486"
---
# <a name="how-to-use-antialiasing-with-text"></a><span data-ttu-id="1b86c-102">Porady: stosowanie antyaliasingu do tekstu</span><span class="sxs-lookup"><span data-stu-id="1b86c-102">How to: Use Antialiasing with Text</span></span>
<span data-ttu-id="1b86c-103">*Antialiasing* odnosi się do wygładzania postrzępionych krawędzi rysowanej grafiki i tekstu, aby poprawić ich wygląd lub czytelność.</span><span class="sxs-lookup"><span data-stu-id="1b86c-103">*Antialiasing* refers to the smoothing of jagged edges of drawn graphics and text to improve their appearance or readability.</span></span> <span data-ttu-id="1b86c-104">Dzięki zarządzanym klasom GDI+ można renderować wysokiej jakości tekst antyaliasowany, a także tekst niższej jakości.</span><span class="sxs-lookup"><span data-stu-id="1b86c-104">With the managed GDI+ classes, you can render high quality antialiased text, as well as lower quality text.</span></span> <span data-ttu-id="1b86c-105">Zazwyczaj renderowanie wyższej jakości zajmuje więcej czasu przetwarzania niż renderowanie niższej jakości.</span><span class="sxs-lookup"><span data-stu-id="1b86c-105">Typically, higher quality rendering takes more processing time than lower quality rendering.</span></span> <span data-ttu-id="1b86c-106">Aby ustawić poziom jakości tekstu, <xref:System.Drawing.Graphics.TextRenderingHint%2A> ustaw <xref:System.Drawing.Graphics> właściwość a na <xref:System.Drawing.Text.TextRenderingHint> jeden z elementów wyliczenia</span><span class="sxs-lookup"><span data-stu-id="1b86c-106">To set the text quality level, set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property of a <xref:System.Drawing.Graphics> to one of the elements of the <xref:System.Drawing.Text.TextRenderingHint> enumeration</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b86c-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="1b86c-107">Example</span></span>  
 <span data-ttu-id="1b86c-108">Poniższy przykład kodu rysuje tekst z dwoma różnymi ustawieniami jakości.</span><span class="sxs-lookup"><span data-stu-id="1b86c-108">The following code example draws text with two different quality settings.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  

 <span data-ttu-id="1b86c-109">Na poniższej ilustracji przedstawiono dane wyjściowe przykładowego kodu:</span><span class="sxs-lookup"><span data-stu-id="1b86c-109">The following illustration shows the output of the example code:</span></span>  
  
 ![Zrzut ekranu przedstawiający tekst z dwoma różnymi ustawieniami jakości.](./media/how-to-use-antialiasing-with-text/antialiasing-text-quality-settings.png)  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1b86c-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="1b86c-111">Compiling the Code</span></span>  
 <span data-ttu-id="1b86c-112">Poprzedni przykład kodu jest przeznaczony do użytku z <xref:System.Windows.Forms.PaintEventArgs> `e`formularzami systemu Windows <xref:System.Windows.Forms.PaintEventHandler>i wymaga , który jest parametrem .</span><span class="sxs-lookup"><span data-stu-id="1b86c-112">The preceding code example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b86c-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b86c-113">See also</span></span>

- [<span data-ttu-id="1b86c-114">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="1b86c-114">Using Fonts and Text</span></span>](using-fonts-and-text.md)
