---
title: 'Instrukcje: Rozmiaru kontrolki Label formularzy Windows pasujący do jego zawartości'
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: 5771b232d77e3e5a792b179ebffd3fa0edda7c9b
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702197"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a><span data-ttu-id="46898-102">Instrukcje: Rozmiaru kontrolki Label formularzy Windows pasujący do jego zawartości</span><span class="sxs-lookup"><span data-stu-id="46898-102">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>
<span data-ttu-id="46898-103">Formularze Windows <xref:System.Windows.Forms.Label> formant może być w jednym lub wielu linii, które mogą być stałe w rozmiarze lub może automatycznie zmieniał swój rozmiar do uwzględnienia swój podpis.</span><span class="sxs-lookup"><span data-stu-id="46898-103">The Windows Forms <xref:System.Windows.Forms.Label> control can be single-line or multi-line, and it can be either fixed in size or can automatically resize itself to accommodate its caption.</span></span> <span data-ttu-id="46898-104"><xref:System.Windows.Forms.Label.AutoSize%2A> Właściwość pomaga rozmiaru formantów, aby dopasować większy lub mniejszy podpisów, która jest szczególnie przydatne, jeśli podpis zmieni się w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="46898-104">The <xref:System.Windows.Forms.Label.AutoSize%2A> property helps you size the controls to fit larger or smaller captions, which is particularly useful if the caption will change at run time.</span></span>  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a><span data-ttu-id="46898-105">Aby formant etykiety dynamicznie Zmień rozmiar pasujący do jego zawartości</span><span class="sxs-lookup"><span data-stu-id="46898-105">To make a label control resize dynamically to fit its contents</span></span>  
  
1.  <span data-ttu-id="46898-106">Ustaw jego <xref:System.Windows.Forms.Label.AutoSize%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="46898-106">Set its <xref:System.Windows.Forms.Label.AutoSize%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="46898-107">Jeśli <xref:System.Windows.Forms.Label.AutoSize%2A> ustawiono `false`, wyrazy w <xref:System.Windows.Forms.Label.Text%2A> właściwość będzie zawijany do następnego wiersza, jeśli jest to możliwe, ale formant nie będzie rosnąć.</span><span class="sxs-lookup"><span data-stu-id="46898-107">If <xref:System.Windows.Forms.Label.AutoSize%2A> is set to `false`, the words specified in the <xref:System.Windows.Forms.Label.Text%2A> property will wrap to the next line if possible, but the control will not grow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46898-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="46898-108">See also</span></span>
- [<span data-ttu-id="46898-109">Instrukcje: Tworzenie klawiszy dostępu za pomocą formantów etykiet formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="46898-109">How to: Create Access Keys with Windows Forms Label Controls</span></span>](how-to-create-access-keys-with-windows-forms-label-controls.md)
- [<span data-ttu-id="46898-110">Label, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="46898-110">Label Control Overview</span></span>](label-control-overview-windows-forms.md)
- [<span data-ttu-id="46898-111">Label, kontrolka</span><span class="sxs-lookup"><span data-stu-id="46898-111">Label Control</span></span>](label-control-windows-forms.md)
