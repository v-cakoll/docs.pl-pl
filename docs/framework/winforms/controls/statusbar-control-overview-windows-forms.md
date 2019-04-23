---
title: StatusBar — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: 5fdefa7d7e7c7ef543f677be7beb61dfee54e077
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077319"
---
# <a name="statusbar-control-overview-windows-forms"></a><span data-ttu-id="d3e8d-102">StatusBar — Informacje o formancie [Formularze systemu Windows]</span><span class="sxs-lookup"><span data-stu-id="d3e8d-102">StatusBar Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="d3e8d-103"><xref:System.Windows.Forms.StatusStrip> i <xref:System.Windows.Forms.ToolStripStatusLabel> kontrolki Zastąp i dodawania funkcjonalności do <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> kontroluje; jednak <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> kontrolek zostaną zachowane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli możesz Wybierz.</span><span class="sxs-lookup"><span data-stu-id="d3e8d-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="d3e8d-104">Formularze Windows [StatusBar, kontrolka](statusbar-control-windows-forms.md) jest używana w formularzach jako obszar, zwykle są wyświetlane w dolnej części okna, w którym aplikacja może wyświetlać różne rodzaje informacji o stanie.</span><span class="sxs-lookup"><span data-stu-id="d3e8d-104">The Windows Forms [StatusBar Control](statusbar-control-windows-forms.md) is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="d3e8d-105"><xref:System.Windows.Forms.StatusBar> Formanty mogą mieć paneli paska stanu na nich, które wyświetlania tekstu lub ikony wskazujące stan lub szeregu ikony w animacji, które wskazują, że proces działa; na przykład [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] wskazująca, że dokument jest zapisywany.</span><span class="sxs-lookup"><span data-stu-id="d3e8d-105"><xref:System.Windows.Forms.StatusBar> controls can have status bar panels on them that display text or icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] indicating that the document is being saved.</span></span>  
  
## <a name="using-the-statusbar-control"></a><span data-ttu-id="d3e8d-106">Używanie formantu StatusBar</span><span class="sxs-lookup"><span data-stu-id="d3e8d-106">Using the StatusBar Control</span></span>  
 <span data-ttu-id="d3e8d-107">Program Internet Explorer używa pasek stanu, aby wskazać adres URL strony, po najechaniu kursorem myszy nad hiperłącze. [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] zawiera informacje dotyczące Lokalizacja strony, Lokalizacja sekcji i tryby edycji, takie jak zastępowania i śledzenie poprawek; i programu Visual Studio używa pasek stanu, co zapewnia kontekstowe informacje, takie jak informujące sposoby manipulowania dokowalnych jak zadokowany lub przestawny.</span><span class="sxs-lookup"><span data-stu-id="d3e8d-107">Internet Explorer uses a status bar to indicate the URL of a page when the mouse rolls over the hyperlink; [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] gives you information on page location, section location, and editing modes such as overtype and revision tracking; and Visual Studio uses the status bar to give context-sensitive information, such as telling you how to manipulate dockable windows as either docked or floating.</span></span>  
  
 <span data-ttu-id="d3e8d-108">Jeden komunikat o można wyświetlić na pasku stanu, ustawiając <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> właściwości `false` (ustawienie domyślne) i ustawienie <xref:System.Windows.Forms.StatusBar.Text%2A> właściwości paska stanu w tekście, które mają być wyświetlane na pasku stanu.</span><span class="sxs-lookup"><span data-stu-id="d3e8d-108">You can display a single message on the status bar by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `false` (the default) and setting the <xref:System.Windows.Forms.StatusBar.Text%2A> property of the status bar to the text you want to appear in the status bar.</span></span> <span data-ttu-id="d3e8d-109">Na pasku stanu można podzielić paneli, aby wyświetlić więcej niż jeden typ informacji przez ustawienie <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> właściwości `true` i przy użyciu <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> metody <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span><span class="sxs-lookup"><span data-stu-id="d3e8d-109">You can divide the status bar into panels to display more than one type of information by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true` and using the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> method of <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3e8d-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3e8d-110">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="d3e8d-111">Instrukcje: Określanie, które panelu w formancie StatusBar formularzy Windows został kliknięty</span><span class="sxs-lookup"><span data-stu-id="d3e8d-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
