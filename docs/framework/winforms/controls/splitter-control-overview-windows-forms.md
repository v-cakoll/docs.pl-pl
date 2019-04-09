---
title: Splitter — Informacje o formancie (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- Splitter
helpviewer_keywords:
- Splitter control [Windows Forms], about Splitter control
ms.assetid: e2b6ab83-dfdd-40ec-9762-850702c82dcb
ms.openlocfilehash: 0477f68aaf67d4b29c491052999ff7784e736669
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176413"
---
# <a name="splitter-control-overview-windows-forms"></a><span data-ttu-id="a4e36-102">Splitter — Informacje o formancie (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="a4e36-102">Splitter Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="a4e36-103">Mimo że <xref:System.Windows.Forms.SplitContainer> zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.Splitter> kontrolki z poprzednich wersji <xref:System.Windows.Forms.Splitter> został zachowany na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości wybranie opcji.</span><span class="sxs-lookup"><span data-stu-id="a4e36-103">Although <xref:System.Windows.Forms.SplitContainer> replaces and adds functionality to the <xref:System.Windows.Forms.Splitter> control of previous versions, <xref:System.Windows.Forms.Splitter> is retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="a4e36-104">Windows Forms <xref:System.Windows.Forms.Splitter> formantów służą do zmiany rozmiaru zadokowanych formantów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a4e36-104">Windows Forms <xref:System.Windows.Forms.Splitter> controls are used to resize docked controls at run time.</span></span> <span data-ttu-id="a4e36-105"><xref:System.Windows.Forms.Splitter> Kontroli jest często używana w formularzach za pomocą formantów, które mają różne długości danych, aby zaprezentować, takich jak Eksplorator Windows, którego okienka danych zawierają informacje o różnych szerokościach w różnym czasie.</span><span class="sxs-lookup"><span data-stu-id="a4e36-105">The <xref:System.Windows.Forms.Splitter> control is often used on forms with controls that have varying lengths of data to present, like Windows Explorer, whose data panes contain information of varying widths at different times.</span></span>  
  
## <a name="working-with-the-splitter-control"></a><span data-ttu-id="a4e36-106">Praca z Splitter — formant</span><span class="sxs-lookup"><span data-stu-id="a4e36-106">Working with the Splitter Control</span></span>  
 <span data-ttu-id="a4e36-107">Gdy użytkownik wskaże wskaźnik myszy na niezadokowane krawędzi kontrolki, która może zmienić rozmiar Splitter — formant, kursor zmienia jego wygląd, aby wskazać, że można zmienić rozmiar kontrolki.</span><span class="sxs-lookup"><span data-stu-id="a4e36-107">When the user points the mouse pointer at the undocked edge of a control that can be resized by a splitter control, the pointer changes its appearance to indicate that the control can be resized.</span></span> <span data-ttu-id="a4e36-108">Za pomocą kontrolki rozdzielacz użytkownika można zmienić rozmiar zadokowany formant, który jest bezpośrednio przed.</span><span class="sxs-lookup"><span data-stu-id="a4e36-108">With the splitter control, the user can resize the docked control that is immediately before it.</span></span> <span data-ttu-id="a4e36-109">W związku z tym aby umożliwić użytkownikowi na zmienianie rozmiaru kontrolki zadokowany w czasie wykonywania, zadokować kontroli rozmiaru krawędzią kontenera, a następnie Zadokuj Splitter — formant do tej samej stronie tego kontenera.</span><span class="sxs-lookup"><span data-stu-id="a4e36-109">Therefore, to enable the user to resize a docked control at run time, dock the control to be resized to an edge of a container, and then dock a splitter control to the same side of that container.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4e36-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4e36-110">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="a4e36-111">Instrukcje: dokowanie kontrolek w Formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a4e36-111">How to: Dock Controls on Windows Forms</span></span>](how-to-dock-controls-on-windows-forms.md)
- [<span data-ttu-id="a4e36-112">Formanty do użycia w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a4e36-112">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
