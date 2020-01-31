---
title: Splitter, kontrolka — omówienie
ms.date: 03/30/2017
f1_keywords:
- Splitter
helpviewer_keywords:
- Splitter control [Windows Forms], about Splitter control
ms.assetid: e2b6ab83-dfdd-40ec-9762-850702c82dcb
ms.openlocfilehash: 3d6da8daf9bb0e8df4f69554a87725a7ddb65acb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742899"
---
# <a name="splitter-control-overview-windows-forms"></a><span data-ttu-id="20b77-102">Splitter — Informacje o formancie (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="20b77-102">Splitter Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="20b77-103">Mimo że <xref:System.Windows.Forms.SplitContainer> zamienia i dodaje funkcje do kontroli <xref:System.Windows.Forms.Splitter> poprzednich wersji, <xref:System.Windows.Forms.Splitter> jest zachowywane w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości w przypadku wybrania tej opcji.</span><span class="sxs-lookup"><span data-stu-id="20b77-103">Although <xref:System.Windows.Forms.SplitContainer> replaces and adds functionality to the <xref:System.Windows.Forms.Splitter> control of previous versions, <xref:System.Windows.Forms.Splitter> is retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="20b77-104">Kontrolki <xref:System.Windows.Forms.Splitter> Windows Forms są używane do zmiany rozmiaru zadokowanych kontrolek w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="20b77-104">Windows Forms <xref:System.Windows.Forms.Splitter> controls are used to resize docked controls at run time.</span></span> <span data-ttu-id="20b77-105">Formant <xref:System.Windows.Forms.Splitter> jest często używany na formularzach z kontrolkami, które mają różne długości danych, takich jak Eksplorator Windows, którego okienka danych zawierają informacje o różnych szerokościach w różnych godzinach.</span><span class="sxs-lookup"><span data-stu-id="20b77-105">The <xref:System.Windows.Forms.Splitter> control is often used on forms with controls that have varying lengths of data to present, like Windows Explorer, whose data panes contain information of varying widths at different times.</span></span>  
  
## <a name="working-with-the-splitter-control"></a><span data-ttu-id="20b77-106">Praca z kontrolką rozdzielacza</span><span class="sxs-lookup"><span data-stu-id="20b77-106">Working with the Splitter Control</span></span>  
 <span data-ttu-id="20b77-107">Gdy użytkownik wskaże wskaźnik myszy w niezadokowanej krawędzi kontrolki, którą można zmienić rozmiar kontrolki rozdzielacza, wskaźnik zmieni swój wygląd, aby wskazać, że można zmienić rozmiar kontrolki.</span><span class="sxs-lookup"><span data-stu-id="20b77-107">When the user points the mouse pointer at the undocked edge of a control that can be resized by a splitter control, the pointer changes its appearance to indicate that the control can be resized.</span></span> <span data-ttu-id="20b77-108">Przy użyciu kontrolki rozdzielacza użytkownik może zmienić rozmiar zadokowanego formantu, który jest bezpośrednio przed nim.</span><span class="sxs-lookup"><span data-stu-id="20b77-108">With the splitter control, the user can resize the docked control that is immediately before it.</span></span> <span data-ttu-id="20b77-109">W związku z tym, aby umożliwić użytkownikowi zmianę rozmiaru zadokowanej kontrolki w czasie wykonywania, Zadokuj kontrolkę, która ma zostać zmieniony na krawędź kontenera, a następnie Zadokuj kontrolkę rozdzielacza do tej samej krawędzi tego kontenera.</span><span class="sxs-lookup"><span data-stu-id="20b77-109">Therefore, to enable the user to resize a docked control at run time, dock the control to be resized to an edge of a container, and then dock a splitter control to the same side of that container.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20b77-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20b77-110">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="20b77-111">Instrukcje: dokowanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="20b77-111">How to: Dock Controls on Windows Forms</span></span>](how-to-dock-controls-on-windows-forms.md)
- [<span data-ttu-id="20b77-112">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="20b77-112">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
