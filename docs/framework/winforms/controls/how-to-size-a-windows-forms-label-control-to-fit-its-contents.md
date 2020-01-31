---
title: Dopasuj rozmiar kontrolki etykiety do jej zawartości
ms.date: 03/30/2017
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
ms.openlocfilehash: 6a563693feaa5074f5d13f0b82cc4d0305a79c23
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743775"
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a><span data-ttu-id="e05cc-102">Porady: rozmiar formantu etykiety (Formularze systemu Windows) pasujący do jego zawartości</span><span class="sxs-lookup"><span data-stu-id="e05cc-102">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>
<span data-ttu-id="e05cc-103">Formant Windows Forms <xref:System.Windows.Forms.Label> może być jednowierszowy lub Wielowierszowy i może być ustalony w rozmiarze lub może automatycznie zmieniać rozmiar w celu dopasowania go do podpisu.</span><span class="sxs-lookup"><span data-stu-id="e05cc-103">The Windows Forms <xref:System.Windows.Forms.Label> control can be single-line or multi-line, and it can be either fixed in size or can automatically resize itself to accommodate its caption.</span></span> <span data-ttu-id="e05cc-104">Właściwość <xref:System.Windows.Forms.Label.AutoSize%2A> ułatwia dopasowanie rozmiaru formantów do większych lub mniejszych napisów, co jest szczególnie przydatne, gdy podpis zostanie zmieniony w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e05cc-104">The <xref:System.Windows.Forms.Label.AutoSize%2A> property helps you size the controls to fit larger or smaller captions, which is particularly useful if the caption will change at run time.</span></span>  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a><span data-ttu-id="e05cc-105">Aby dopasować rozmiar kontrolki etykiety dynamicznie do jej zawartości</span><span class="sxs-lookup"><span data-stu-id="e05cc-105">To make a label control resize dynamically to fit its contents</span></span>  
  
1. <span data-ttu-id="e05cc-106">Ustaw jej Właściwość <xref:System.Windows.Forms.Label.AutoSize%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="e05cc-106">Set its <xref:System.Windows.Forms.Label.AutoSize%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="e05cc-107">Jeśli <xref:System.Windows.Forms.Label.AutoSize%2A> jest ustawiona na `false`, słowa określone we właściwości <xref:System.Windows.Forms.Label.Text%2A> zostaną zawinięte do następnego wiersza, jeśli jest to możliwe, ale formant nie zostanie powiększony.</span><span class="sxs-lookup"><span data-stu-id="e05cc-107">If <xref:System.Windows.Forms.Label.AutoSize%2A> is set to `false`, the words specified in the <xref:System.Windows.Forms.Label.Text%2A> property will wrap to the next line if possible, but the control will not grow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e05cc-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e05cc-108">See also</span></span>

- [<span data-ttu-id="e05cc-109">Instrukcje: tworzenie klawiszy dostępu za pomocą kontrolek Label formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e05cc-109">How to: Create Access Keys with Windows Forms Label Controls</span></span>](how-to-create-access-keys-with-windows-forms-label-controls.md)
- [<span data-ttu-id="e05cc-110">Label, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="e05cc-110">Label Control Overview</span></span>](label-control-overview-windows-forms.md)
- [<span data-ttu-id="e05cc-111">Label, kontrolka</span><span class="sxs-lookup"><span data-stu-id="e05cc-111">Label Control</span></span>](label-control-windows-forms.md)
