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
# <a name="statusbar-control-overview-windows-forms"></a>StatusBar — Informacje o formancie [Formularze systemu Windows]
> [!IMPORTANT]
> <xref:System.Windows.Forms.StatusBarPanel> <xref:System.Windows.Forms.StatusBarPanel> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBar> Formanty i zastępują i dodają funkcje do kontrolek i, natomiast kontrolki i są zachowywane w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości. <xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.ToolStripStatusLabel> następnie.  
  
 [Formant StatusBar](statusbar-control-windows-forms.md) Windows Forms jest używany w formularzach jako obszar, zwykle wyświetlany u dołu okna, w którym aplikacja może wyświetlać różne rodzaje informacji o stanie. <xref:System.Windows.Forms.StatusBar>w kontrolkach mogą znajdować się panele paska stanu, które wyświetlają tekst lub ikony wskazujące stan, lub serię ikon w animacji wskazującej, że proces działa. na przykład program Microsoft Word wskazuje, że dokument jest zapisywany.  
  
## <a name="using-the-statusbar-control"></a>Korzystanie z formantu StatusBar  
 Program Internet Explorer używa paska stanu, aby wskazać adres URL strony, gdy wskaźnik myszy przesuwa się nad hiperłączem. Program Microsoft Word zawiera informacje o lokalizacji strony, lokalizacji sekcji i trybach edycji, takich jak zastępowanie i śledzenie poprawek; Program Visual Studio używa paska stanu, aby podać informacje kontekstowe, na przykład poinformowanie o sposobie manipulowania oknami było dokować jako zadokowanych lub zmiennoprzecinkowych.  
  
 Na pasku stanu można wyświetlić jeden komunikat, ustawiając <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> właściwość na `false` <xref:System.Windows.Forms.StatusBar.Text%2A> wartość (domyślnie) i ustawiając właściwość paska stanu na tekst, który ma być wyświetlany na pasku stanu. Pasek stanu można podzielić na panele, aby wyświetlić więcej niż jeden typ <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> informacji przez ustawienie właściwości na `true` <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>i przy użyciu <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> metody.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Instrukcje: Określ, który panel w Windows Forms kontrolce StatusBar został kliknięty](determine-which-panel-wf-statusbar-control-was-clicked.md)
