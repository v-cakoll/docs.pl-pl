---
title: 'Instrukcje: Ustawianie tekstu wyświetlanego przez Windows Forms przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], setting caption
- Windows Forms, setting the text displayed
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
ms.openlocfilehash: cea2bcdb973e1deb5e0e6cf7fcc31b7c084dc446
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510588"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer"></a><span data-ttu-id="6db9c-102">Instrukcje: Ustawianie tekstu wyświetlanego przez Windows Forms przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="6db9c-102">How to: Set the Text Displayed by a Windows Forms Control Using the Designer</span></span>
<span data-ttu-id="6db9c-103">Kontrolek formularzy Windows Forms jest zazwyczaj wyświetlane jakiś tekst, który jest powiązany z podstawową funkcją kontroli.</span><span class="sxs-lookup"><span data-stu-id="6db9c-103">Windows Forms controls typically display some text that is related to the primary function of the control.</span></span> <span data-ttu-id="6db9c-104">Na przykład <xref:System.Windows.Forms.Button> kontroli zwykle wyświetla podpis, który wskazuje, jakie działania będą wykonywane po kliknięciu przycisku.</span><span class="sxs-lookup"><span data-stu-id="6db9c-104">For example, a <xref:System.Windows.Forms.Button> control typically displays a caption that indicates what action will be performed when the button is clicked.</span></span> <span data-ttu-id="6db9c-105">Dla wszystkich kontrolek, możesz ustawić lub zwróć tekst przy użyciu <xref:System.Windows.Forms.Control.Text%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="6db9c-105">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="6db9c-106">Czcionkę można zmienić za pomocą <xref:System.Windows.Forms.Control.Font%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="6db9c-106">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>  
  
### <a name="to-set-the-text-and-font-with-the-designer"></a><span data-ttu-id="6db9c-107">Aby ustawić tekstu i czcionek, za pomocą projektanta</span><span class="sxs-lookup"><span data-stu-id="6db9c-107">To set the text and font with the designer</span></span>  
  
1.  <span data-ttu-id="6db9c-108">W oknie właściwości ustaw <xref:System.Windows.Forms.Control.Text%2A> właściwości kontrolki na odpowiedni ciąg.</span><span class="sxs-lookup"><span data-stu-id="6db9c-108">In the Properties window, set the <xref:System.Windows.Forms.Control.Text%2A> property of the control to an appropriate string.</span></span>  
  
     <span data-ttu-id="6db9c-109">Do utworzenia klawiszem skrótu podkreślony obejmuje handlowe "i" (&) przed literą, który zostanie klawisz skrótu.</span><span class="sxs-lookup"><span data-stu-id="6db9c-109">To create an underlined shortcut key, includes an ampersand (&) before the letter that will be the shortcut key.</span></span>  
  
2.  <span data-ttu-id="6db9c-110">W oknie dialogowym właściwości kliknij przycisk oznaczony wielokropkiem (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) obok pozycji <xref:System.Windows.Forms.Control.Font%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="6db9c-110">In the Properties window, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>  
  
     <span data-ttu-id="6db9c-111">W oknie dialogowym standardowa czcionkę wybierz czcionkę, styl czcionki, rozmiaru, efekty (na przykład przekreślenie lub podkreślenie) i skryptów, które mają.</span><span class="sxs-lookup"><span data-stu-id="6db9c-111">In the standard font dialog box, select the font, font style, size, effects (such as strikeout or underline), and script that you want.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6db9c-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6db9c-112">See also</span></span>
- [<span data-ttu-id="6db9c-113">Instrukcje: Ustawianie tekstu wyświetlanego przez kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6db9c-113">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="6db9c-114">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="6db9c-114">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
- [<span data-ttu-id="6db9c-115">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="6db9c-115">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
