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
ms.openlocfilehash: eb00928205a318b068d49ea3f6f71c398f77bbcd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072496"
---
# <a name="how-to-draw-vertical-text-on-a-windows-form"></a><span data-ttu-id="165ad-102">Instrukcje: Rysowanie pionowego tekstu w formularzu systemu Windows</span><span class="sxs-lookup"><span data-stu-id="165ad-102">How to: Draw Vertical Text on a Windows Form</span></span>
<span data-ttu-id="165ad-103">Poniższy przykład kodu pokazuje, jak rysowanie pionowego tekstu w formularzu za pomocą <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics>.</span><span class="sxs-lookup"><span data-stu-id="165ad-103">The following code example shows how to draw vertical text on a form by using the <xref:System.Drawing.Graphics.DrawString%2A> method of <xref:System.Drawing.Graphics>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="165ad-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="165ad-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#8](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#8)]
 [!code-csharp[System.Drawing.ConceptualHowTos#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#8)]
 [!code-vb[System.Drawing.ConceptualHowTos#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#8)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="165ad-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="165ad-105">Compiling the Code</span></span>  
 <span data-ttu-id="165ad-106">Nie można wywołać tej metody w <xref:System.Windows.Forms.Form.Load> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="165ad-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="165ad-107">Rysowane zawartość nie zostanie narysowany ponownie, gdy formularz jest zmiany rozmiaru lub zostanie przesłonięty przez inny formularz.</span><span class="sxs-lookup"><span data-stu-id="165ad-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="165ad-108">Aby automatycznie odświeżenia zawartości, należy zastąpić <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="165ad-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="165ad-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="165ad-109">Robust Programming</span></span>  
 <span data-ttu-id="165ad-110">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="165ad-110">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="165ad-111">Czcionka Arial nie jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="165ad-111">The Arial font is not installed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="165ad-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="165ad-112">See also</span></span>

- <xref:System.Drawing.Graphics.DrawString%2A>
- <xref:System.Drawing.StringFormat.FormatFlags%2A>
- <xref:System.Drawing.StringFormatFlags>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="165ad-113">Wprowadzenie do programowania grafiki</span><span class="sxs-lookup"><span data-stu-id="165ad-113">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="165ad-114">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="165ad-114">Using Fonts and Text</span></span>](using-fonts-and-text.md)
