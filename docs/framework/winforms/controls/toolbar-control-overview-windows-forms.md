---
title: ToolBar — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- ToolBar
helpviewer_keywords:
- toolbars [Windows Forms], about toolbars
- ToolBar control [Windows Forms], about ToolBar controls
ms.assetid: d426b203-0216-4dbe-b834-1641e50a9c29
ms.openlocfilehash: 42c3d9c681da9ca87125a274fa12af623269bd70
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745251"
---
# <a name="toolbar-control-overview-windows-forms"></a>ToolBar — Informacje o formancie [Formularze systemu Windows]
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.ToolBar> kontrolować; jednak <xref:System.Windows.Forms.ToolBar> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.  
  
 Formularze Windows <xref:System.Windows.Forms.ToolBar> formant jest używany w formularzach jako pasek sterowania, który wyświetla wiersz w rozwijanych menu i przycisków mapy bitowej, który aktywować poleceń. W związku z tym klikając przycisk paska narzędzi może być równoważne polecenie menu. Można skonfigurować przyciski są wyświetlane i zachowują się jak przyciski, menu rozwijane lub separatorów. Zazwyczaj pasek narzędzi zawiera przyciski i menu, które odpowiadają elementom struktury menu aplikacji, zapewniając szybki dostęp do aplikacji z najczęściej używanych funkcji i poleceń.  
  
## <a name="working-with-the-toolbar-control"></a>Praca z formantem paska narzędzi  
 A <xref:System.Windows.Forms.ToolBar> formant jest zwykle "zadokowany" wzdłuż górnej części okna nadrzędnego, ale może być zadokowane także na dowolnej stronie okna. Pasek narzędzi można wyświetlać etykietek narzędzi, gdy użytkownik wskaże wskaźnik myszy na przycisku paska narzędzi. Etykietka narzędzia jest niewielkie okno podręczne, stanowiącą zwięzły opis przycisku lub menu Cel. Aby wyświetlić etykietki narzędzi, <xref:System.Windows.Forms.ToolBar.ShowToolTips%2A> właściwość musi być równa `true`.  
  
> [!NOTE]
>  Niektóre aplikacje są wyposażone w formantów bardzo podobne do paska narzędzi, które mają możliwość "float" nad oknem aplikacji i można zmieniać pozycji. Kontrolki Windows Forms z paska narzędzi nie jest w stanie umożliwia wykonywanie tych czynności.  
  
 Gdy <xref:System.Windows.Forms.ToolBar.Appearance%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.ToolBarAppearance>, przyciski paska narzędzi są wyświetlane podniesione i trójwymiarowych. Możesz ustawić <xref:System.Windows.Forms.ToolBar.Appearance%2A> właściwości paska narzędzi, aby <xref:System.Windows.Forms.ToolBarAppearance> aby dać płaski wygląd paska narzędzi i jej przyciski. Gdy wskaźnik myszy porusza się nad przyciskiem prostego, wyglądu przycisku zmienia trójwymiarowej. Przyciski paska narzędzi można podzielić na logiczne grupy za pomocą separatorów. Separator znajduje się przycisk paska narzędzi <xref:System.Windows.Forms.ToolBarButton.Style%2A> właściwością <xref:System.Windows.Forms.ToolBarButtonStyle>. Będzie ono wyświetlane jako puste miejsce na pasku narzędzi. Gdy pasek narzędzi znajdują się płaski wygląd, przycisk separatory pojawiają się jako wiersze, a nie spacje między przyciskami.  
  
 <xref:System.Windows.Forms.ToolBar> Kontroli pozwala na tworzenie pasków narzędzi, dodając <xref:System.Windows.Forms.Button> obiekty do <xref:System.Windows.Forms.ToolBar.Buttons%2A> kolekcji. Edytor kolekcji można użyć, aby dodać przyciski do <xref:System.Windows.Forms.ToolBar> formantu; każdy <xref:System.Windows.Forms.Button> obiektu powinien mieć tekst lub obraz, który został przypisany, chociaż można przypisać obu. Obraz, który jest dostarczany przez skojarzony [ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) składnika. W czasie wykonywania, można dodawać i usuwać przycisków z <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection> przy użyciu <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Add%2A> i <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Remove%2A> metody. Program przycisków <xref:System.Windows.Forms.ToolBar>, Dodaj kod, aby <xref:System.Windows.Forms.ToolBar.ButtonClick> zdarzenia <xref:System.Windows.Forms.ToolBar>przy użyciu <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> właściwość <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> klasę, aby określić, której przycisk został kliknięty.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.ToolBar>
- [ToolBar, kontrolka](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)
- [Instrukcje: Dodawanie przycisków do formantu ToolBar](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)
- [Instrukcje: Określanie ikony dla przycisku kontrolki ToolBar](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)
- [Instrukcje: Wyzwalacz zdarzenia Menu dla przycisków paska narzędzi](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)
