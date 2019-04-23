---
title: 'Instrukcje: Wyrównywanie narysowanego tekstu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], aligning
- Windows Forms, aligning drawn text
ms.assetid: 83c10a81-1a90-4b5c-98aa-2c6c4b280079
ms.openlocfilehash: 0e77e4d8eeb9d7a07115b89525ac80074afeb6e8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59323273"
---
# <a name="how-to-align-drawn-text"></a><span data-ttu-id="18a0b-102">Instrukcje: Wyrównywanie narysowanego tekstu</span><span class="sxs-lookup"><span data-stu-id="18a0b-102">How to: Align Drawn Text</span></span>
<span data-ttu-id="18a0b-103">Podczas wykonywania niestandardowego rysowania często warto Centrum narysowanego tekstu na formularz lub formant.</span><span class="sxs-lookup"><span data-stu-id="18a0b-103">When you perform custom drawing, you may often want to center drawn text on a form or control.</span></span> <span data-ttu-id="18a0b-104">Możesz łatwo wyrównać narysowany tekst <xref:System.Drawing.Graphics.DrawString%2A> lub <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metod, tworząc odpowiedni obiekt formatowania i ustawienie flagi w odpowiednim formacie.</span><span class="sxs-lookup"><span data-stu-id="18a0b-104">You can easily align text drawn with the <xref:System.Drawing.Graphics.DrawString%2A> or <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods by creating the correct formatting object and setting the appropriate format flags.</span></span>  
  
### <a name="to-draw-centered-text-with-gdi-drawstring"></a><span data-ttu-id="18a0b-105">Aby narysować wyśrodkowany tekst z użyciem interfejsu GDI + (sznurkiem)</span><span class="sxs-lookup"><span data-stu-id="18a0b-105">To draw centered text with GDI+ (DrawString)</span></span>  
  
1. <span data-ttu-id="18a0b-106">Użyj <xref:System.Drawing.StringFormat> z odpowiednią <xref:System.Drawing.Graphics.DrawString%2A> metodę, aby określić tekst wyśrodkowany.</span><span class="sxs-lookup"><span data-stu-id="18a0b-106">Use a <xref:System.Drawing.StringFormat> with the appropriate <xref:System.Drawing.Graphics.DrawString%2A> method to specify centered text.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#10)]
     [!code-vb[System.Drawing.AlignDrawnText#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#10)]  
  
### <a name="to-draw-centered-text-with-gdi-drawtext"></a><span data-ttu-id="18a0b-107">Aby narysować wyśrodkowany tekst z użyciem interfejsu GDI (DrawText)</span><span class="sxs-lookup"><span data-stu-id="18a0b-107">To draw centered text with GDI (DrawText)</span></span>  
  
1. <span data-ttu-id="18a0b-108">Użyj <xref:System.Windows.Forms.TextFormatFlags> wyliczenie dla zawijania, a także w pionie i poziomie wyśrodkowanie tekstu z odpowiednią <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="18a0b-108">Use the <xref:System.Windows.Forms.TextFormatFlags> enumeration for wrapping as well as vertically and horizontally centering text with the appropriate <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#20)]
     [!code-vb[System.Drawing.AlignDrawnText#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#20)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="18a0b-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="18a0b-109">Compiling the Code</span></span>  
 <span data-ttu-id="18a0b-110">W powyższych przykładach kodu są skonstruowane do użycia za pomocą interfejsu Windows Forms i wymagają one <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="18a0b-110">The preceding code examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18a0b-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="18a0b-111">See also</span></span>

- [<span data-ttu-id="18a0b-112">Instrukcje: Rysowanie tekstu za pomocą GDI</span><span class="sxs-lookup"><span data-stu-id="18a0b-112">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
- [<span data-ttu-id="18a0b-113">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="18a0b-113">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="18a0b-114">Instrukcje: Tworzenie rodzin czcionek i czcionek</span><span class="sxs-lookup"><span data-stu-id="18a0b-114">How to: Construct Font Families and Fonts</span></span>](how-to-construct-font-families-and-fonts.md)
