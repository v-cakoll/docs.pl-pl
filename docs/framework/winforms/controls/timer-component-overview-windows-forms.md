---
title: "Timer — Informacje o składniku (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ea78cadae6e033bc54274e5428ba5e8c6410259d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="timer-component-overview-windows-forms"></a>Timer — Informacje o składniku (Formularze systemu Windows)
Formularze systemu Windows <xref:System.Windows.Forms.Timer> to składnik, który wywołuje zdarzenie w regularnych odstępach czasu. Ten składnik jest przeznaczony dla środowiska Windows Forms. Jeśli potrzebujesz czasomierza, które jest odpowiednie dla środowiska serwera, zobacz [wprowadzenie do serwerowych czasomierze](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
## <a name="key-properties-methods-and-events"></a>Właściwości klucza, metod i zdarzeń  
 Długość przedziałów jest definiowana za pomocą <xref:System.Windows.Forms.Timer.Interval%2A> właściwości, której wartość jest podana w milisekundach. Po włączeniu składnika <xref:System.Windows.Forms.Timer.Tick> zdarzenie jest zgłaszane, co interwał. Jest to, gdzie można dodać kod do wykonania. Aby uzyskać więcej informacji, zobacz [porady: uruchamianie procedur odstępach ustawić za pomocą składnika Timer formularzy systemu Windows](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md). Metody klucza <xref:System.Windows.Forms.Timer> są składnika <xref:System.Windows.Forms.Timer.Start%2A> i <xref:System.Windows.Forms.Timer.Stop%2A>, które czasomierza Włączanie i wyłączanie. Po wyłączeniu czasomierza resetuje; nie istnieje sposób wstrzymania <xref:System.Windows.Forms.Timer> składnika.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Timer>  
 [Timer — składnik](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [Ograniczenia właściwości Interval składnika Timer formularzy systemu Windows](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md)
