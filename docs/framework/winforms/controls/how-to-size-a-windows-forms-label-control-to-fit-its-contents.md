---
title: 'Porady: rozmiar formantu etykiety (Formularze systemu Windows) pasujący do jego zawartości'
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: e067966b606d77ceb9d11d2784c0d5f73ad332a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533731"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a><span data-ttu-id="795c7-102">Porady: rozmiar formantu etykiety (Formularze systemu Windows) pasujący do jego zawartości</span><span class="sxs-lookup"><span data-stu-id="795c7-102">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>
<span data-ttu-id="795c7-103">Formularze systemu Windows <xref:System.Windows.Forms.Label> formant może być jednym lub wielu linii, które mogą być stałym rozmiarze lub można automatycznie zmieniany aby zmieścił się w jego podpis.</span><span class="sxs-lookup"><span data-stu-id="795c7-103">The Windows Forms <xref:System.Windows.Forms.Label> control can be single-line or multi-line, and it can be either fixed in size or can automatically resize itself to accommodate its caption.</span></span> <span data-ttu-id="795c7-104"><xref:System.Windows.Forms.Label.AutoSize%2A> Właściwość pomaga rozmiaru formantów w celu dopasowania większy lub mniejszy podpisów, która jest szczególnie przydatne, jeśli zmieni podpis w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="795c7-104">The <xref:System.Windows.Forms.Label.AutoSize%2A> property helps you size the controls to fit larger or smaller captions, which is particularly useful if the caption will change at run time.</span></span>  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a><span data-ttu-id="795c7-105">Aby utworzyć etykietę kontroli dynamicznie Zmień rozmiar pasujący do jego zawartości</span><span class="sxs-lookup"><span data-stu-id="795c7-105">To make a label control resize dynamically to fit its contents</span></span>  
  
1.  <span data-ttu-id="795c7-106">Ustaw jego <xref:System.Windows.Forms.Label.AutoSize%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="795c7-106">Set its <xref:System.Windows.Forms.Label.AutoSize%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="795c7-107">Jeśli <xref:System.Windows.Forms.Label.AutoSize%2A> ustawiono `false`, wyrazy w <xref:System.Windows.Forms.Label.Text%2A> właściwości będzie zawijany do następnego wiersza, jeśli to możliwe, ale kontrolka nie będzie rosnąć.</span><span class="sxs-lookup"><span data-stu-id="795c7-107">If <xref:System.Windows.Forms.Label.AutoSize%2A> is set to `false`, the words specified in the <xref:System.Windows.Forms.Label.Text%2A> property will wrap to the next line if possible, but the control will not grow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="795c7-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="795c7-108">See Also</span></span>  
 [<span data-ttu-id="795c7-109">Instrukcje: tworzenie klawiszy dostępu za pomocą kontrolek Label formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="795c7-109">How to: Create Access Keys with Windows Forms Label Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)  
 [<span data-ttu-id="795c7-110">Label, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="795c7-110">Label Control Overview</span></span>](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [<span data-ttu-id="795c7-111">Label, kontrolka</span><span class="sxs-lookup"><span data-stu-id="795c7-111">Label Control</span></span>](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)
