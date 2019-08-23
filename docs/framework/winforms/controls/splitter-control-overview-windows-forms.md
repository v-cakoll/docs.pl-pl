---
title: Splitter — Informacje o formancie (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- Splitter
helpviewer_keywords:
- Splitter control [Windows Forms], about Splitter control
ms.assetid: e2b6ab83-dfdd-40ec-9762-850702c82dcb
ms.openlocfilehash: 934efd707f2a52da5ba604139c8e4510aad4606b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964458"
---
# <a name="splitter-control-overview-windows-forms"></a><span data-ttu-id="ee5e7-102">Splitter — Informacje o formancie (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="ee5e7-102">Splitter Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="ee5e7-103">Mimo <xref:System.Windows.Forms.SplitContainer> że program zamienia i dodaje funkcje <xref:System.Windows.Forms.Splitter> kontroli nad poprzednimi wersjami, <xref:System.Windows.Forms.Splitter> jest zachowywany w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="ee5e7-103">Although <xref:System.Windows.Forms.SplitContainer> replaces and adds functionality to the <xref:System.Windows.Forms.Splitter> control of previous versions, <xref:System.Windows.Forms.Splitter> is retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="ee5e7-104">Kontrolki Windows Forms <xref:System.Windows.Forms.Splitter> są używane do zmiany rozmiaru zadokowanych kontrolek w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ee5e7-104">Windows Forms <xref:System.Windows.Forms.Splitter> controls are used to resize docked controls at run time.</span></span> <span data-ttu-id="ee5e7-105"><xref:System.Windows.Forms.Splitter> Kontrolka jest często używana w formularzach z kontrolkami, które mają różne długości danych, takich jak Eksplorator Windows, którego okienka danych zawierają informacje o różnych szerokościach w różnych godzinach.</span><span class="sxs-lookup"><span data-stu-id="ee5e7-105">The <xref:System.Windows.Forms.Splitter> control is often used on forms with controls that have varying lengths of data to present, like Windows Explorer, whose data panes contain information of varying widths at different times.</span></span>  
  
## <a name="working-with-the-splitter-control"></a><span data-ttu-id="ee5e7-106">Praca z kontrolką rozdzielacza</span><span class="sxs-lookup"><span data-stu-id="ee5e7-106">Working with the Splitter Control</span></span>  
 <span data-ttu-id="ee5e7-107">Gdy użytkownik wskaże wskaźnik myszy w niezadokowanej krawędzi kontrolki, którą można zmienić rozmiar kontrolki rozdzielacza, wskaźnik zmieni swój wygląd, aby wskazać, że można zmienić rozmiar kontrolki.</span><span class="sxs-lookup"><span data-stu-id="ee5e7-107">When the user points the mouse pointer at the undocked edge of a control that can be resized by a splitter control, the pointer changes its appearance to indicate that the control can be resized.</span></span> <span data-ttu-id="ee5e7-108">Przy użyciu kontrolki rozdzielacza użytkownik może zmienić rozmiar zadokowanego formantu, który jest bezpośrednio przed nim.</span><span class="sxs-lookup"><span data-stu-id="ee5e7-108">With the splitter control, the user can resize the docked control that is immediately before it.</span></span> <span data-ttu-id="ee5e7-109">W związku z tym, aby umożliwić użytkownikowi zmianę rozmiaru zadokowanej kontrolki w czasie wykonywania, Zadokuj kontrolkę, która ma zostać zmieniony na krawędź kontenera, a następnie Zadokuj kontrolkę rozdzielacza do tej samej krawędzi tego kontenera.</span><span class="sxs-lookup"><span data-stu-id="ee5e7-109">Therefore, to enable the user to resize a docked control at run time, dock the control to be resized to an edge of a container, and then dock a splitter control to the same side of that container.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee5e7-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee5e7-110">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="ee5e7-111">Instrukcje: Zadokuj kontrolki na Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ee5e7-111">How to: Dock Controls on Windows Forms</span></span>](how-to-dock-controls-on-windows-forms.md)
- [<span data-ttu-id="ee5e7-112">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ee5e7-112">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
