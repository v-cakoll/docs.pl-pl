---
title: ToolBar — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
f1_keywords:
- ToolBar
helpviewer_keywords:
- toolbars [Windows Forms], about toolbars
- ToolBar control [Windows Forms], about ToolBar controls
ms.assetid: d426b203-0216-4dbe-b834-1641e50a9c29
ms.openlocfilehash: c7c19783963bb315a0356979797c6f4d4e3b9e08
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929593"
---
# <a name="toolbar-control-overview-windows-forms"></a>ToolBar — Informacje o formancie [Formularze systemu Windows]
> [!NOTE]
> Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.ToolBar> do <xref:System.Windows.Forms.ToolBar> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.ToolStrip>  
  
 Formant Windows Forms <xref:System.Windows.Forms.ToolBar> jest używany w formularzach jako pasek sterowania, który wyświetla wiersz menu rozwijanego i przyciski mapy bitowej, które uaktywniają polecenia. W ten sposób kliknięcie przycisku paska narzędzi może być równoznaczne z wybraniem polecenia menu. Przyciski można skonfigurować tak, aby były wyświetlane i zachowywać się jako pozycje, menu rozwijane lub separatory. Zazwyczaj pasek narzędzi zawiera przyciski i menu odpowiadające elementom w strukturze menu aplikacji, zapewniając szybki dostęp do najczęściej używanych funkcji i poleceń aplikacji.  
  
## <a name="working-with-the-toolbar-control"></a>Praca z formantem paska narzędzi  
 <xref:System.Windows.Forms.ToolBar> Kontrolka jest zwykle "zadokowana" w górnej części okna nadrzędnego, ale może być również zadokowana do dowolnej strony okna. Pasek narzędzi może wyświetlać etykietki narzędzia, gdy użytkownik wskaże wskaźnik myszy na przycisku paska narzędzi. Etykietka narzędzia jest małym okienkiem podręcznym, która zwięźle opisuje przycisk lub menu. Aby wyświetlić etykietki narzędzi, <xref:System.Windows.Forms.ToolBar.ShowToolTips%2A> właściwość musi być ustawiona na `true`.  
  
> [!NOTE]
> Niektóre aplikacje są kontrolkami podobnymi do paska narzędzi, który ma możliwość "float" nad oknem aplikacji i jest zmieniany. Kontrolka paska narzędzi Windows Forms nie może wykonać tych czynności.  
  
 Gdy właściwość jest ustawiona na <xref:System.Windows.Forms.ToolBarAppearance>, przyciski paska narzędzi są wywoływane i trójwymiarowe. <xref:System.Windows.Forms.ToolBar.Appearance%2A> Można ustawić <xref:System.Windows.Forms.ToolBar.Appearance%2A> Właściwość paska narzędzi, aby <xref:System.Windows.Forms.ToolBarAppearance> nadać pasek narzędzi i jego przyciski płaski wygląd. Gdy wskaźnik myszy zostanie przesunięty nad płaskim przyciskiem, wygląd przycisku zmieni się na trójwymiarowy. Przyciski paska narzędzi można podzielić na grupy logiczne przy użyciu separatorów. Separatorem jest przycisk paska narzędzi z <xref:System.Windows.Forms.ToolBarButton.Style%2A> właściwością ustawioną na. <xref:System.Windows.Forms.ToolBarButtonStyle> Pojawia się jako puste miejsce na pasku narzędzi. Gdy pasek narzędzi ma płaski wygląd, separatory przycisków są wyświetlane jako linie zamiast spacji między przyciskami.  
  
 Kontrolka umożliwia tworzenie pasków narzędzi przez dodanie <xref:System.Windows.Forms.Button> obiektów do <xref:System.Windows.Forms.ToolBar.Buttons%2A> kolekcji. <xref:System.Windows.Forms.ToolBar> Za pomocą edytora kolekcji można dodawać przyciski do <xref:System.Windows.Forms.ToolBar> kontrolki; każdy <xref:System.Windows.Forms.Button> obiekt powinien mieć przypisany tekst lub obraz, chociaż można przypisać oba elementy. Obraz jest dostarczany przez skojarzony składnik [ImageList](imagelist-component-windows-forms.md) . W czasie wykonywania można dodawać lub usuwać przyciski <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection> <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Add%2A> przy użyciu metod i <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Remove%2A> . Aby <xref:System.Windows.Forms.ToolBar>programować przyciski obiektu, Dodaj kod <xref:System.Windows.Forms.ToolBar> <xref:System.Windows.Forms.ToolBar.ButtonClick> do zdarzeń obiektu, używając <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> właściwości <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> klasy w celu określenia, który przycisk został kliknięty.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolBar>
- [ToolBar, kontrolka](toolbar-control-windows-forms.md)
- [Instrukcje: Dodawanie przycisków do kontrolki paska narzędzi](how-to-add-buttons-to-a-toolbar-control.md)
- [Instrukcje: Zdefiniuj ikonę dla przycisku paska narzędzi](how-to-define-an-icon-for-a-toolbar-button.md)
- [Instrukcje: Zdarzenia menu wyzwalacza dla przycisków paska narzędzi](how-to-trigger-menu-events-for-toolbar-buttons.md)
