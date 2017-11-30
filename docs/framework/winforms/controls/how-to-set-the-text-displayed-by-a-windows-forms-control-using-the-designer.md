---
title: "Porady: ustawianie tekstu wyświetlanego przez formant formularzy systemu Windows przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], setting caption
- Windows Forms, setting the text displayed
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 59d66df2c6f18ad28ad4b912c00e35f786d773da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer"></a><span data-ttu-id="575dd-102">Porady: ustawianie tekstu wyświetlanego przez formant formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="575dd-102">How to: Set the Text Displayed by a Windows Forms Control Using the Designer</span></span>
<span data-ttu-id="575dd-103">Formanty formularzy systemu Windows zazwyczaj wyświetlić tekst związany z podstawowej funkcji formantu.</span><span class="sxs-lookup"><span data-stu-id="575dd-103">Windows Forms controls typically display some text that is related to the primary function of the control.</span></span> <span data-ttu-id="575dd-104">Na przykład <xref:System.Windows.Forms.Button> kontroli zwykle zawiera nagłówek, wskazującą, jakie działania zostaną wykonane, po kliknięciu przycisku.</span><span class="sxs-lookup"><span data-stu-id="575dd-104">For example, a <xref:System.Windows.Forms.Button> control typically displays a caption that indicates what action will be performed when the button is clicked.</span></span> <span data-ttu-id="575dd-105">Dla wszystkich kontrolek, można ustawić lub zwróć tekst za pomocą <xref:System.Windows.Forms.Control.Text%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="575dd-105">For all controls, you can set or return the text by using the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="575dd-106">Czcionkę można zmienić za pomocą <xref:System.Windows.Forms.Control.Font%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="575dd-106">You can change the font by using the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>  
  
### <a name="to-set-the-text-and-font-with-the-designer"></a><span data-ttu-id="575dd-107">Aby ustawić tekst i czcionki przy użyciu projektanta</span><span class="sxs-lookup"><span data-stu-id="575dd-107">To set the text and font with the designer</span></span>  
  
1.  <span data-ttu-id="575dd-108">W oknie właściwości ustaw <xref:System.Windows.Forms.Control.Text%2A> właściwości formantu odpowiedni ciąg.</span><span class="sxs-lookup"><span data-stu-id="575dd-108">In the Properties window, set the <xref:System.Windows.Forms.Control.Text%2A> property of the control to an appropriate string.</span></span>  
  
     <span data-ttu-id="575dd-109">Można utworzyć klucza podkreślony skrótów obejmuje handlowego "i" (&) przed literą, która będzie można użyć klawisza skrótu.</span><span class="sxs-lookup"><span data-stu-id="575dd-109">To create an underlined shortcut key, includes an ampersand (&) before the letter that will be the shortcut key.</span></span>  
  
2.  <span data-ttu-id="575dd-110">W oknie właściwości kliknij przycisk oznaczony wielokropkiem (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) obok pozycji <xref:System.Windows.Forms.Control.Font%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="575dd-110">In the Properties window, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.Control.Font%2A> property.</span></span>  
  
     <span data-ttu-id="575dd-111">W oknie dialogowym czcionki standardowej wybierz czcionki, styl czcionki, rozmiaru, efekty (na przykład przekreślenia lub podkreślenie) i skryptu żądane.</span><span class="sxs-lookup"><span data-stu-id="575dd-111">In the standard font dialog box, select the font, font style, size, effects (such as strikeout or underline), and script that you want.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="575dd-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="575dd-112">See Also</span></span>  
 [<span data-ttu-id="575dd-113">Porady: Ustawianie tekstu wyświetlanego przez formant formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="575dd-113">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [<span data-ttu-id="575dd-114">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="575dd-114">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="575dd-115">Etykietowanie formantów formularzy systemu Windows poszczególnych i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="575dd-115">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
