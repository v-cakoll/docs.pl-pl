---
title: "HScrollBar i VScrollBar — Informacje o formantach (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 80ec592bf83969ae57495b0df2af110b5622ea11
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="hscrollbar-and-vscrollbar-controls-overview-windows-forms"></a>HScrollBar i VScrollBar — Informacje o formantach (Formularze systemu Windows)
Formularze systemu Windows <xref:System.Windows.Forms.ScrollBar> formantów służą do zapewniania nawigację za pośrednictwem długą listę elementów lub duża ilość informacji, albo przewijanie w poziomie lub pionie w aplikacji lub kontrolki. Paski przewijania są wspólnego elementu interfejsu systemu Windows, więc <xref:System.Windows.Forms.ScrollBar> kontroli jest często używana z formantami, które nie pochodzą z <xref:System.Windows.Forms.ScrollableControl> klasy. Podobnie wielu deweloperów wybierz uwzględnienie <xref:System.Windows.Forms.ScrollBar> sterowania w przypadku tworzenia własne kontrolki użytkownika.  
  
 <xref:System.Windows.Forms.HScrollBar> (Poziomy) i <xref:System.Windows.Forms.VScrollBar> formantów (pionową) działać niezależnie od innych kontrolek i mieć własny zestaw zdarzeń, właściwości i metod. <xref:System.Windows.Forms.ScrollBar>formanty nie są takie same, jak paski przewijania wbudowanych, które są dołączone do pól tekstowych, pola listy, pola kombi lub formularze MDI ( <xref:System.Windows.Forms.TextBox> formant ma <xref:System.Windows.Forms.TextBox.ScrollBars%2A> właściwości, aby pokazać lub ukryć paski przewijania, które są dołączone do formantu).  
  
 <xref:System.Windows.Forms.ScrollBar> Steruje użyciem <xref:System.Windows.Forms.ScrollBar.Scroll> zdarzenia do monitorowania przepływu suwaka (nazywane czasami stronie przycisku suwaka) na pasku przewijania. Przy użyciu <xref:System.Windows.Forms.ScrollBar.Scroll> zdarzeń zapewnia dostęp do wartości paska przewijania, jak przeciągania.  
  
## <a name="value-property"></a>Value — właściwość  
 <xref:System.Windows.Forms.ScrollBar.Value%2A> Właściwości (która domyślnie wynosi 0) jest `integer` wartość odpowiadającą pozycja pola przewijania na pasku przewijania. Pozycja pola przewijania znajduje się na wartość minimalna, powoduje przeniesienie do lewej położenie (paski przewijania w poziomie) lub górnej pozycji (w przypadku pionowe paski przewijania). Gdy pole przewijania znajduje się na wartość maksymalna, przenosi pole przewijania, do prawej krawędzi lub dolną pozycję. Podobnie wartość środek między dolnej i górnej części zakresu umieszcza wiodące krawędzi pola przewijania w środku paska przewijania.  
  
 Oprócz za pomocą kliknięć myszą, aby zmienić wartość paska przewijania, użytkownika można również przeciągnij suwak do dowolnego punktu przy pasku. Wartość wynikową zależy pozycja pola przewijania, ale jest zawsze w zakresie <xref:System.Windows.Forms.ScrollBar.Minimum%2A> do <xref:System.Windows.Forms.ScrollBar.Maximum%2A> właściwości ustawione przez użytkownika.  
  
## <a name="largechange-and-smallchange-properties"></a>LargeChange i SmallChange właściwości  
 Gdy użytkownik naciśnie klawisz PAGE UP lub PAGE DOWN lub kliknie śledzenia pasek przewijania po obu stronach pole przewijania <xref:System.Windows.Forms.ScrollBar.Value%2A> zmiany właściwości zgodnie z wartością <xref:System.Windows.Forms.ScrollBar.LargeChange%2A> właściwości.  
  
 Gdy użytkownik naciśnie jedną strzałkę kluczy lub kliknie jeden z przycisków paska przewijania, <xref:System.Windows.Forms.ScrollBar.Value%2A> zmiany właściwości zgodnie z wartością <xref:System.Windows.Forms.ScrollBar.SmallChange%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.HScrollBar>  
 <xref:System.Windows.Forms.VScrollBar>  
 [Dodawanie do formularzy systemu Windows dla programu .NET Framework 2.0](http://msdn.microsoft.com/en-us/c61a923d-3d6a-4c8c-820c-e94c83f3f9a8)  
 [Formanty do użycia w formularzach systemu Windows](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
