---
title: HScrollBar i VScrollBar, kontrolki — omówienie
ms.date: 03/30/2017
f1_keywords:
- HScrollBar
- VScrollBar
helpviewer_keywords:
- ScrollBar control [Windows Forms]
- HScrollBar control [Windows Forms], about HScrollBar
- VScrollBar control [Windows Forms], about VScrollBar control
- ScrollBar control [Windows Forms], about ScrollBar control
- scroll bars [Windows Forms], about scroll bars
ms.assetid: 8b307679-1cae-41d8-99aa-3d1efd207cd6
ms.openlocfilehash: abe0c8da9723f17cb80715454f6ab7297724a21f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728164"
---
# <a name="hscrollbar-and-vscrollbar-controls-overview-windows-forms"></a>HScrollBar i VScrollBar — Informacje o formantach (Formularze systemu Windows)
Kontrolki <xref:System.Windows.Forms.ScrollBar> Windows Forms umożliwiają łatwe nawigowanie za pomocą długich list elementów lub dużej ilości informacji przez przewijanie w poziomie lub w pionie w obrębie aplikacji lub kontrolki. Paski przewijania są wspólnym elementem interfejsu systemu Windows, więc formant <xref:System.Windows.Forms.ScrollBar> jest często używany z kontrolkami, które nie pochodzą z klasy <xref:System.Windows.Forms.ScrollableControl>. Podobnie wielu deweloperów wybiera do uwzględnienia kontrolki <xref:System.Windows.Forms.ScrollBar> podczas tworzenia własnych kontrolek użytkownika.  
  
 Kontrolki <xref:System.Windows.Forms.HScrollBar> (poziome) i <xref:System.Windows.Forms.VScrollBar> (pionowe) działają niezależnie od innych kontrolek i mają własne zestawy zdarzeń, właściwości i metod. kontrolki <xref:System.Windows.Forms.ScrollBar> nie są takie same jak wbudowane paski przewijania, które są dołączone do pól tekstowych, pól listy, pól kombi lub formularzy MDI (kontrolka <xref:System.Windows.Forms.TextBox> ma właściwość <xref:System.Windows.Forms.TextBox.ScrollBars%2A>, aby pokazać lub ukryć paski przewijania, które są dołączone do kontrolki).  
  
 Kontrolki <xref:System.Windows.Forms.ScrollBar> używają zdarzenia <xref:System.Windows.Forms.ScrollBar.Scroll> do monitorowania przenoszenia pola przewijania (czasami określanego jako kciuk) wzdłuż paska przewijania. Użycie zdarzenia <xref:System.Windows.Forms.ScrollBar.Scroll> zapewnia dostęp do wartości paska przewijania w miarę przeciągania.  
  
## <a name="value-property"></a>Value — właściwość  
 Właściwość <xref:System.Windows.Forms.ScrollBar.Value%2A> (domyślnie jest równa 0) jest wartością `integer` odpowiadającą pozycji pola przewijania na pasku przewijania. Gdy pozycja pola przewijania ma wartość minimalną, przechodzi do lewej strony (w przypadku pasków przewijania poziomego) lub górnej pozycji (dla pionowych pasków przewijania). Gdy pole przewijania ma wartość maksymalną, pole przewijania jest przenoszone do prawej strony lub do dołu. Podobnie wartość środkowa między dolnym i górnym zakresem powoduje umieszczenie wiodącej krawędzi pola przewijania w środku paska przewijania.  
  
 Oprócz używania kliknięć myszą w celu zmiany wartości paska przewijania użytkownik może również przeciągnąć pole przewijania do dowolnego punktu wzdłuż paska. Wartość wyniku zależy od pozycji pola przewijania, ale zawsze w zakresie <xref:System.Windows.Forms.ScrollBar.Minimum%2A> do <xref:System.Windows.Forms.ScrollBar.Maximum%2A> właściwości ustawionych przez użytkownika.  
  
## <a name="largechange-and-smallchange-properties"></a>Właściwości LargeChange i SmallChange  
 Gdy użytkownik naciśnie klawisz PAGE UP lub PAGE DOWN lub kliknie na ścieżce paska przewijania po obu stronach pola przewijania, właściwość <xref:System.Windows.Forms.ScrollBar.Value%2A> zmienia się zgodnie z wartością ustawioną we właściwości <xref:System.Windows.Forms.ScrollBar.LargeChange%2A>.  
  
 Gdy użytkownik naciśnie jeden z klawiszy strzałek lub kliknie jeden z przycisków paska przewijania, właściwość <xref:System.Windows.Forms.ScrollBar.Value%2A> zmienia się zgodnie z wartością ustawioną we właściwości <xref:System.Windows.Forms.ScrollBar.SmallChange%2A>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.HScrollBar>
- <xref:System.Windows.Forms.VScrollBar>
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
