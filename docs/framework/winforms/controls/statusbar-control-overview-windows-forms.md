---
title: "StatusBar — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9c26463fae5beca23026a71dd83b19bf3eb52875
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="statusbar-control-overview-windows-forms"></a>StatusBar — Informacje o formancie [Formularze systemu Windows]
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> i <xref:System.Windows.Forms.ToolStripStatusLabel> formanty Zastąp oraz dodawać funkcje do <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> steruje; jednak <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> formanty są zachowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli możesz Wybierz.  
  
 Formularze systemu Windows [formantu StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) jest używany w formularzach jako obszaru, zwykle wyświetlane w dolnej części okna, w którym aplikacja może wyświetlać różne rodzaje informacji o stanie. <xref:System.Windows.Forms.StatusBar>Formanty mogą mieć paneli paska stanu na nich zawierające tekst lub ikony, aby wskazać, stanu lub serii ikon animacji, które wskazują, czy proces działa; na przykład [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] wskazujący, że dokument jest zapisywany.  
  
## <a name="using-the-statusbar-control"></a>Używanie formantu StatusBar  
 Program Internet Explorer używa paska stanu w celu wskazywać adres URL strony, gdy wskaźnik myszy jest przesuwany nad hiperłącze. [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] dostarcza informacji o lokalizacji strony, lokalizacji sekcji i tryby, takie jak zastępowania i śledzenie; poprawek edycji i [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] używa zapewniające informacje kontekstowe, takich jak informujący sposobu modyfikowania dokującego paska stanu System Windows jako zadokowanych lub zmiennoprzecinkową.  
  
 Pojedynczym komunikacie można wyświetlić na pasku stanu, ustawiając <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> właściwości `false` (ustawienie domyślne) i ustawienie <xref:System.Windows.Forms.StatusBar.Text%2A> właściwości paska stanu tekst, który ma być wyświetlany w pasku stanu. Pasek stanu można podzielić na panele, aby wyświetlić więcej niż jeden typ informacji przez ustawienie <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> właściwości `true` i przy użyciu <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> metody <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [Porady: Określanie, które panelu w formancie StatusBar formularzy systemu Windows został kliknięty](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)
