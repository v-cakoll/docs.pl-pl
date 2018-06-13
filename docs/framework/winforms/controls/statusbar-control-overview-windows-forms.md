---
title: StatusBar — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: 6dd5b45b38ec4fb04d9a53a1648cfe6e5a5b9f20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535132"
---
# <a name="statusbar-control-overview-windows-forms"></a>StatusBar — Informacje o formancie [Formularze systemu Windows]
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> i <xref:System.Windows.Forms.ToolStripStatusLabel> formanty Zastąp oraz dodawać funkcje do <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> steruje; jednak <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> formanty są zachowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli możesz Wybierz.  
  
 Formularze systemu Windows [formantu StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) jest używany w formularzach jako obszaru, zwykle wyświetlane w dolnej części okna, w którym aplikacja może wyświetlać różne rodzaje informacji o stanie. <xref:System.Windows.Forms.StatusBar> Formanty mogą mieć paneli paska stanu na nich zawierające tekst lub ikony, aby wskazać, stanu lub serii ikon animacji, które wskazują, czy proces działa; na przykład [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] wskazujący, że dokument jest zapisywany.  
  
## <a name="using-the-statusbar-control"></a>Używanie formantu StatusBar  
 Program Internet Explorer używa paska stanu w celu wskazywać adres URL strony, gdy wskaźnik myszy jest przesuwany nad hiperłącze. [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] dostarcza informacji o lokalizacji strony, Lokalizacja sekcji i tryby edycji, takie jak zastępowania i śledzenie poprawki; i Visual Studio wykorzystuje pasek stanu do udzielenia kontekstowa informacje, takie jak informujący sposobu modyfikowania okna dokowalne jak zadokowanych lub zmiennoprzecinkową.  
  
 Pojedynczym komunikacie można wyświetlić na pasku stanu, ustawiając <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> właściwości `false` (ustawienie domyślne) i ustawienie <xref:System.Windows.Forms.StatusBar.Text%2A> właściwości paska stanu tekst, który ma być wyświetlany w pasku stanu. Pasek stanu można podzielić na panele, aby wyświetlić więcej niż jeden typ informacji przez ustawienie <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> właściwości `true` i przy użyciu <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> metody <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [Instrukcje: ustalanie, który panel został kliknięty w kontrolce StatusBar formularzy Windows Forms](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)
