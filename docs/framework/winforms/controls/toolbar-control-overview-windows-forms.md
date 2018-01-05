---
title: "ToolBar — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ToolBar
helpviewer_keywords:
- toolbars [Windows Forms], about toolbars
- ToolBar control [Windows Forms], about ToolBar controls
ms.assetid: d426b203-0216-4dbe-b834-1641e50a9c29
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eac54e18f397cf455ffd5fa33c2e000d87b917a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="toolbar-control-overview-windows-forms"></a>ToolBar — Informacje o formancie [Formularze systemu Windows]
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.ToolBar> kontrolować; jednak <xref:System.Windows.Forms.ToolBar> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.  
  
 Formularze systemu Windows <xref:System.Windows.Forms.ToolBar> formant jest używany w formularzach jako pasek sterowania z wiersza menu rozwijanych i mapy bitowej przycisków aktywować poleceń. W związku z tym kliknięcie przycisku paska narzędzi można równoważne wybraniu polecenia menu. Przyciski można skonfigurować i zachowywać się jako przyciski, menu rozwijane lub separatorów. Zwykle pasek narzędzi zawiera przyciski i menu, które odpowiadają do elementów w strukturze menu aplikacja, szybkie dostępowi do najczęściej używane funkcje i polecenia aplikacji.  
  
## <a name="working-with-the-toolbar-control"></a>Praca z formantem paska narzędzi  
 A <xref:System.Windows.Forms.ToolBar> kontroli jest zazwyczaj "zadokowane" u góry okna nadrzędnego, ale również może być zadokowany do dowolnej krawędzi okna. Pasek narzędzi można wyświetlić etykietki narzędzi, gdy użytkownik wskaże wskaźnik myszy na przycisku paska narzędzi. Etykietka narzędzia jest mała okno podręczne krótko opisano przycisk lub menu Cel. Aby wyświetlić etykietki narzędzi, <xref:System.Windows.Forms.ToolBar.ShowToolTips%2A> musi mieć ustawioną właściwość `true`.  
  
> [!NOTE]
>  Niektóre aplikacje funkcji formantów bardzo podobne do paska narzędzi, które mają możliwość "float" powyżej okna aplikacji i można zmienić ich pozycji. Formantu ToolBar formularzy systemu Windows nie będzie mógł wykonać tych czynności.  
  
 Gdy <xref:System.Windows.Forms.ToolBar.Appearance%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.ToolBarAppearance>, przycisków paska narzędzi są wyświetlane podniesione i trójwymiarowych. Można ustawić <xref:System.Windows.Forms.ToolBar.Appearance%2A> właściwości narzędzi, aby <xref:System.Windows.Forms.ToolBarAppearance> decyzję o nadaniu pasku narzędzi i jej przyciski wygląd płaski. Wskaźnik myszy porusza się nad przyciskiem płaski wygląd przycisku zmienia się trójwymiarowych. Przyciski paska narzędzi można podzielić na logiczne grupy przy użyciu separatorów. Separator znajduje się przycisk paska narzędzi <xref:System.Windows.Forms.ToolBarButton.Style%2A> ustawioną właściwość <xref:System.Windows.Forms.ToolBarButtonStyle>. Wygląda na to, jak pusty obszar na pasku narzędzi. Gdy pasek narzędzi ma wygląd płaski, separatory przycisk są wyświetlane jako wiersze, a nie odstępów między przyciskami.  
  
 <xref:System.Windows.Forms.ToolBar> Kontroli umożliwia utworzenie pasków narzędzi dodając <xref:System.Windows.Forms.Button> obiekty do <xref:System.Windows.Forms.ToolBar.Buttons%2A> kolekcji. Edytor kolekcji umożliwia dodawanie przycisków do <xref:System.Windows.Forms.ToolBar> formantu; każdego <xref:System.Windows.Forms.Button> obiekt powinien mieć tekst lub obraz przypisany, chociaż można przypisać jednocześnie. Obraz jest dostarczany przez skojarzony [ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) składnika. W czasie wykonywania, można dodawać i usuwać przycisków z <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection> przy użyciu <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Add%2A> i <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Remove%2A> metody. Do programu przycisków <xref:System.Windows.Forms.ToolBar>, Dodaj kod, aby <xref:System.Windows.Forms.ToolBar.ButtonClick> zdarzenia <xref:System.Windows.Forms.ToolBar>za pomocą <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> właściwość <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> klasę, aby określić, który przycisk został kliknięty.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ToolBar>  
 [ToolBar, kontrolka](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)  
 [Instrukcje: dodawanie przycisków do kontrolki ToolBar](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)  
 [Instrukcje: określanie ikony dla przycisku kontrolki ToolBar](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 [Instrukcje: zdarzenia wyzwalaczy menu dla przycisków kontrolki Toolbar](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)
