---
title: 'Instrukcje: Rysowanie pionowego tekstu w formularzu systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- StringFormat.FormatFlags
- Graphics.DrawString
helpviewer_keywords:
- text [Windows Forms], drawing vertical
- strings [Windows Forms], drawing vertical
- text [Windows Forms], drawing
- text [Windows Forms], vertical text
ms.assetid: 717a6131-00f6-4373-b574-9894e8317799
ms.openlocfilehash: 660d7abae5463c976e60b7d9caeae8a798d122ca
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626173"
---
# <a name="how-to-draw-vertical-text-on-a-windows-form"></a><span data-ttu-id="3efc5-102">Instrukcje: Rysowanie pionowego tekstu w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3efc5-102">How to: Draw Vertical Text on a Windows Form</span></span>
<span data-ttu-id="3efc5-103">Poniższy przykład kodu pokazuje, jak rysowanie pionowego tekstu w formularzu za pomocą <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics>.</span><span class="sxs-lookup"><span data-stu-id="3efc5-103">The following code example shows how to draw vertical text on a form by using the <xref:System.Drawing.Graphics.DrawString%2A> method of <xref:System.Drawing.Graphics>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3efc5-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3efc5-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#8](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#8)]
 [!code-csharp[System.Drawing.ConceptualHowTos#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#8)]
 [!code-vb[System.Drawing.ConceptualHowTos#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#8)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3efc5-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="3efc5-105">Compiling the Code</span></span>  
 <span data-ttu-id="3efc5-106">Nie można wywołać tej metody w <xref:System.Windows.Forms.Form.Load> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3efc5-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="3efc5-107">Rysowane zawartość nie zostanie narysowany ponownie, gdy formularz jest zmiany rozmiaru lub zostanie przesłonięty przez inny formularz.</span><span class="sxs-lookup"><span data-stu-id="3efc5-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="3efc5-108">Aby automatycznie odświeżenia zawartości, należy zastąpić <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3efc5-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3efc5-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="3efc5-109">Robust Programming</span></span>  
 <span data-ttu-id="3efc5-110">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="3efc5-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="3efc5-111">Czcionka Arial nie jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="3efc5-111">The Arial font is not installed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3efc5-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3efc5-112">See also</span></span>

- <xref:System.Drawing.Graphics.DrawString%2A>
- <xref:System.Drawing.StringFormat.FormatFlags%2A>
- <xref:System.Drawing.StringFormatFlags>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="3efc5-113">Wprowadzenie do programowania grafiki</span><span class="sxs-lookup"><span data-stu-id="3efc5-113">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="3efc5-114">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="3efc5-114">Using Fonts and Text</span></span>](using-fonts-and-text.md)
