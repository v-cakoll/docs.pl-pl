---
title: StatusBar — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: bd58d4c70e3a3c88e57fe242957f669d1944fd71
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964433"
---
# <a name="statusbar-control-overview-windows-forms"></a><span data-ttu-id="e2f49-102">StatusBar — Informacje o formancie [Formularze systemu Windows]</span><span class="sxs-lookup"><span data-stu-id="e2f49-102">StatusBar Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="e2f49-103"><xref:System.Windows.Forms.StatusBarPanel> <xref:System.Windows.Forms.StatusBarPanel> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBar> Formanty i zastępują i dodają funkcje do kontrolek i, natomiast kontrolki i są zachowywane w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości. <xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.ToolStripStatusLabel> następnie.</span><span class="sxs-lookup"><span data-stu-id="e2f49-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="e2f49-104">[Formant StatusBar](statusbar-control-windows-forms.md) Windows Forms jest używany w formularzach jako obszar, zwykle wyświetlany u dołu okna, w którym aplikacja może wyświetlać różne rodzaje informacji o stanie.</span><span class="sxs-lookup"><span data-stu-id="e2f49-104">The Windows Forms [StatusBar Control](statusbar-control-windows-forms.md) is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="e2f49-105"><xref:System.Windows.Forms.StatusBar>w kontrolkach mogą znajdować się panele paska stanu, które wyświetlają tekst lub ikony wskazujące stan, lub serię ikon w animacji wskazującej, że proces działa. na przykład program Microsoft Word wskazuje, że dokument jest zapisywany.</span><span class="sxs-lookup"><span data-stu-id="e2f49-105"><xref:System.Windows.Forms.StatusBar> controls can have status bar panels on them that display text or icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, Microsoft Word indicating that the document is being saved.</span></span>  
  
## <a name="using-the-statusbar-control"></a><span data-ttu-id="e2f49-106">Korzystanie z formantu StatusBar</span><span class="sxs-lookup"><span data-stu-id="e2f49-106">Using the StatusBar Control</span></span>  
 <span data-ttu-id="e2f49-107">Program Internet Explorer używa paska stanu, aby wskazać adres URL strony, gdy wskaźnik myszy przesuwa się nad hiperłączem. Program Microsoft Word zawiera informacje o lokalizacji strony, lokalizacji sekcji i trybach edycji, takich jak zastępowanie i śledzenie poprawek; Program Visual Studio używa paska stanu, aby podać informacje kontekstowe, na przykład poinformowanie o sposobie manipulowania oknami było dokować jako zadokowanych lub zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="e2f49-107">Internet Explorer uses a status bar to indicate the URL of a page when the mouse rolls over the hyperlink; Microsoft Word gives you information on page location, section location, and editing modes such as overtype and revision tracking; and Visual Studio uses the status bar to give context-sensitive information, such as telling you how to manipulate dockable windows as either docked or floating.</span></span>  
  
 <span data-ttu-id="e2f49-108">Na pasku stanu można wyświetlić jeden komunikat, ustawiając <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> właściwość na `false` <xref:System.Windows.Forms.StatusBar.Text%2A> wartość (domyślnie) i ustawiając właściwość paska stanu na tekst, który ma być wyświetlany na pasku stanu.</span><span class="sxs-lookup"><span data-stu-id="e2f49-108">You can display a single message on the status bar by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `false` (the default) and setting the <xref:System.Windows.Forms.StatusBar.Text%2A> property of the status bar to the text you want to appear in the status bar.</span></span> <span data-ttu-id="e2f49-109">Pasek stanu można podzielić na panele, aby wyświetlić więcej niż jeden typ <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> informacji przez ustawienie właściwości na `true` <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>i przy użyciu <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e2f49-109">You can divide the status bar into panels to display more than one type of information by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true` and using the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> method of <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2f49-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e2f49-110">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="e2f49-111">Instrukcje: Określ, który panel w Windows Forms kontrolce StatusBar został kliknięty</span><span class="sxs-lookup"><span data-stu-id="e2f49-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
