---
title: StatusBar — Informacje o formancie
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: b0b97bc3cb0291871e1fd113d82d0b480b53cdba
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742862"
---
# <a name="statusbar-control-overview-windows-forms"></a><span data-ttu-id="ef3b3-102">StatusBar — Informacje o formancie [Formularze systemu Windows]</span><span class="sxs-lookup"><span data-stu-id="ef3b3-102">StatusBar Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="ef3b3-103">Kontrolki <xref:System.Windows.Forms.StatusStrip> i <xref:System.Windows.Forms.ToolStripStatusLabel> zastępują i dodają funkcje do kontrolek <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel>; jednak kontrolki <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> są zachowywane w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="ef3b3-104">[Formant StatusBar](statusbar-control-windows-forms.md) Windows Forms jest używany w formularzach jako obszar, zwykle wyświetlany u dołu okna, w którym aplikacja może wyświetlać różne rodzaje informacji o stanie.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-104">The Windows Forms [StatusBar Control](statusbar-control-windows-forms.md) is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="ef3b3-105">kontrolki <xref:System.Windows.Forms.StatusBar> mogą mieć na nich panele paska stanu, które wyświetlają tekst lub ikony wskazujące stan, lub serię ikon w animacji wskazującej, że proces działa. na przykład program Microsoft Word wskazuje, że dokument jest zapisywany.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-105"><xref:System.Windows.Forms.StatusBar> controls can have status bar panels on them that display text or icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, Microsoft Word indicating that the document is being saved.</span></span>  
  
## <a name="using-the-statusbar-control"></a><span data-ttu-id="ef3b3-106">Korzystanie z formantu StatusBar</span><span class="sxs-lookup"><span data-stu-id="ef3b3-106">Using the StatusBar Control</span></span>  
 <span data-ttu-id="ef3b3-107">Program Internet Explorer używa paska stanu, aby wskazać adres URL strony, gdy wskaźnik myszy przesuwa się nad hiperłączem. Program Microsoft Word zawiera informacje o lokalizacji strony, lokalizacji sekcji i trybach edycji, takich jak zastępowanie i śledzenie poprawek; Program Visual Studio używa paska stanu, aby podać informacje kontekstowe, na przykład poinformowanie o sposobie manipulowania oknami było dokować jako zadokowanych lub zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-107">Internet Explorer uses a status bar to indicate the URL of a page when the mouse rolls over the hyperlink; Microsoft Word gives you information on page location, section location, and editing modes such as overtype and revision tracking; and Visual Studio uses the status bar to give context-sensitive information, such as telling you how to manipulate dockable windows as either docked or floating.</span></span>  
  
 <span data-ttu-id="ef3b3-108">Na pasku stanu można wyświetlić jeden komunikat, ustawiając właściwość <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> na `false` (wartość domyślna) i ustawiając właściwość <xref:System.Windows.Forms.StatusBar.Text%2A> paska stanu na tekst, który ma być wyświetlany na pasku stanu.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-108">You can display a single message on the status bar by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `false` (the default) and setting the <xref:System.Windows.Forms.StatusBar.Text%2A> property of the status bar to the text you want to appear in the status bar.</span></span> <span data-ttu-id="ef3b3-109">Pasek stanu można podzielić na panele, aby wyświetlić więcej niż jeden typ informacji, ustawiając właściwość <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> na `true` i używając metody <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span><span class="sxs-lookup"><span data-stu-id="ef3b3-109">You can divide the status bar into panels to display more than one type of information by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true` and using the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> method of <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef3b3-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef3b3-110">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="ef3b3-111">Instrukcje: ustalanie, który panel został kliknięty w kontrolce StatusBar formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ef3b3-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
