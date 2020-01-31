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
# <a name="statusbar-control-overview-windows-forms"></a>StatusBar — Informacje o formancie [Formularze systemu Windows]
> [!IMPORTANT]
> Kontrolki <xref:System.Windows.Forms.StatusStrip> i <xref:System.Windows.Forms.ToolStripStatusLabel> zastępują i dodają funkcje do kontrolek <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel>; jednak kontrolki <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> są zachowywane w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję.  
  
 [Formant StatusBar](statusbar-control-windows-forms.md) Windows Forms jest używany w formularzach jako obszar, zwykle wyświetlany u dołu okna, w którym aplikacja może wyświetlać różne rodzaje informacji o stanie. kontrolki <xref:System.Windows.Forms.StatusBar> mogą mieć na nich panele paska stanu, które wyświetlają tekst lub ikony wskazujące stan, lub serię ikon w animacji wskazującej, że proces działa. na przykład program Microsoft Word wskazuje, że dokument jest zapisywany.  
  
## <a name="using-the-statusbar-control"></a>Korzystanie z formantu StatusBar  
 Program Internet Explorer używa paska stanu, aby wskazać adres URL strony, gdy wskaźnik myszy przesuwa się nad hiperłączem. Program Microsoft Word zawiera informacje o lokalizacji strony, lokalizacji sekcji i trybach edycji, takich jak zastępowanie i śledzenie poprawek; Program Visual Studio używa paska stanu, aby podać informacje kontekstowe, na przykład poinformowanie o sposobie manipulowania oknami było dokować jako zadokowanych lub zmiennoprzecinkowych.  
  
 Na pasku stanu można wyświetlić jeden komunikat, ustawiając właściwość <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> na `false` (wartość domyślna) i ustawiając właściwość <xref:System.Windows.Forms.StatusBar.Text%2A> paska stanu na tekst, który ma być wyświetlany na pasku stanu. Pasek stanu można podzielić na panele, aby wyświetlić więcej niż jeden typ informacji, ustawiając właściwość <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> na `true` i używając metody <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Instrukcje: ustalanie, który panel został kliknięty w kontrolce StatusBar formularzy Windows Forms](determine-which-panel-wf-statusbar-control-was-clicked.md)
