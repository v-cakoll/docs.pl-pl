---
title: ToolBar, kontrolka — omówienie
ms.date: 03/30/2017
f1_keywords:
- ToolBar
helpviewer_keywords:
- toolbars [Windows Forms], about toolbars
- ToolBar control [Windows Forms], about ToolBar controls
ms.assetid: d426b203-0216-4dbe-b834-1641e50a9c29
ms.openlocfilehash: f364e052258703331496f8103b48953a90aa3a9b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735482"
---
# <a name="toolbar-control-overview-windows-forms"></a>ToolBar — Informacje o formancie [Formularze systemu Windows]
> [!NOTE]
> Formant <xref:System.Windows.Forms.ToolStrip> zamienia i dodaje funkcje do kontrolki <xref:System.Windows.Forms.ToolBar>; Niemniej jednak kontrolka <xref:System.Windows.Forms.ToolBar> jest zachowywana na potrzeby zgodności z poprzednimi wersjami i w przyszłości.  
  
 Kontrolka <xref:System.Windows.Forms.ToolBar> Windows Forms jest używana w formularzach jako pasek sterowania, który wyświetla wiersz menu rozwijanego i przyciski mapy bitowej, które aktywują polecenia. W ten sposób kliknięcie przycisku paska narzędzi może być równoznaczne z wybraniem polecenia menu. Przyciski można skonfigurować tak, aby były wyświetlane i zachowywać się jako pozycje, menu rozwijane lub separatory. Zazwyczaj pasek narzędzi zawiera przyciski i menu odpowiadające elementom w strukturze menu aplikacji, zapewniając szybki dostęp do najczęściej używanych funkcji i poleceń aplikacji.  
  
## <a name="working-with-the-toolbar-control"></a>Praca z formantem paska narzędzi  
 Kontrolka <xref:System.Windows.Forms.ToolBar> jest zwykle "zadokowana" w górnej części okna nadrzędnego, ale może być również zadokowana do dowolnej strony okna. Pasek narzędzi może wyświetlać etykietki narzędzia, gdy użytkownik wskaże wskaźnik myszy na przycisku paska narzędzi. Etykietka narzędzia jest małym okienkiem podręcznym, która zwięźle opisuje przycisk lub menu. Aby wyświetlić etykietki narzędzi, właściwość <xref:System.Windows.Forms.ToolBar.ShowToolTips%2A> musi być ustawiona na `true`.  
  
> [!NOTE]
> Niektóre aplikacje są kontrolkami podobnymi do paska narzędzi, który ma możliwość "float" nad oknem aplikacji i jest zmieniany. Kontrolka paska narzędzi Windows Forms nie może wykonać tych czynności.  
  
 Gdy właściwość <xref:System.Windows.Forms.ToolBar.Appearance%2A> jest ustawiona na <xref:System.Windows.Forms.ToolBarAppearance>, przyciski paska narzędzi są wyświetlane i trójwymiarowe. Właściwość <xref:System.Windows.Forms.ToolBar.Appearance%2A> paska narzędzi można ustawić na <xref:System.Windows.Forms.ToolBarAppearance>, aby nadać pasek narzędzi i jego przyciski płaski wygląd. Gdy wskaźnik myszy zostanie przesunięty nad płaskim przyciskiem, wygląd przycisku zmieni się na trójwymiarowy. Przyciski paska narzędzi można podzielić na grupy logiczne przy użyciu separatorów. Separatorem jest przycisk paska narzędzi z właściwością <xref:System.Windows.Forms.ToolBarButton.Style%2A> ustawioną na <xref:System.Windows.Forms.ToolBarButtonStyle>. Pojawia się jako puste miejsce na pasku narzędzi. Gdy pasek narzędzi ma płaski wygląd, separatory przycisków są wyświetlane jako linie zamiast spacji między przyciskami.  
  
 Formant <xref:System.Windows.Forms.ToolBar> umożliwia tworzenie pasków narzędzi przez dodanie obiektów <xref:System.Windows.Forms.Button> do kolekcji <xref:System.Windows.Forms.ToolBar.Buttons%2A>. Aby dodać przyciski do kontrolki <xref:System.Windows.Forms.ToolBar>, można użyć edytora kolekcji. Każdy obiekt <xref:System.Windows.Forms.Button> powinien mieć przypisany tekst lub obraz, chociaż można przypisać oba elementy. Obraz jest dostarczany przez skojarzony składnik [ImageList](imagelist-component-windows-forms.md) . W czasie wykonywania można dodawać lub usuwać przyciski z <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection> przy użyciu metod <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Add%2A> i <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Remove%2A>. Aby programować przyciski <xref:System.Windows.Forms.ToolBar>, należy dodać kod do <xref:System.Windows.Forms.ToolBar.ButtonClick> zdarzeń <xref:System.Windows.Forms.ToolBar>przy użyciu właściwości <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> klasy <xref:System.Windows.Forms.ToolBarButtonClickEventArgs>, aby określić, który przycisk został kliknięty.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolBar>
- [ToolBar, kontrolka](toolbar-control-windows-forms.md)
- [Instrukcje: dodawanie przycisków do kontrolki ToolBar](how-to-add-buttons-to-a-toolbar-control.md)
- [Instrukcje: określanie ikony dla przycisku kontrolki ToolBar](how-to-define-an-icon-for-a-toolbar-button.md)
- [Instrukcje: zdarzenia wyzwalaczy menu dla przycisków kontrolki Toolbar](how-to-trigger-menu-events-for-toolbar-buttons.md)
