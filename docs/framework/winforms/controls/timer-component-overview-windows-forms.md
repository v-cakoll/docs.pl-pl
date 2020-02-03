---
title: Timer, składnik — omówienie
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: 83b52d395cdc3e3357bcf83517eab258a5c8ae08
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742782"
---
# <a name="timer-component-overview-windows-forms"></a>Timer — Informacje o składniku (Formularze systemu Windows)
<xref:System.Windows.Forms.Timer> Windows Forms jest składnikiem, który wywołuje zdarzenie w regularnych odstępach czasu. Ten składnik jest przeznaczony dla środowiska Windows Formsowego. Jeśli potrzebujesz czasomierza odpowiedniego dla środowiska serwera, zobacz [wprowadzenie do czasomierzy oparte na serwerze](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
## <a name="key-properties-methods-and-events"></a>Właściwości klucza, metody i zdarzenia  
 Długość interwałów jest definiowana przez właściwość <xref:System.Windows.Forms.Timer.Interval%2A>, której wartość jest wyrażona w milisekundach. Po włączeniu składnika <xref:System.Windows.Forms.Timer.Tick> zdarzenie jest zgłaszane każdy interwał. Jest to miejsce, w którym można dodać kod do wykonania. Aby uzyskać więcej informacji, zobacz [jak: uruchamiać procedury w określonych odstępach czasu za pomocą składnika czasomierza Windows Forms](run-procedures-at-set-intervals-with-wf-timer-component.md). Kluczowe metody składnika <xref:System.Windows.Forms.Timer> są <xref:System.Windows.Forms.Timer.Start%2A> i <xref:System.Windows.Forms.Timer.Stop%2A>, co powoduje włączenie i wyłączenie czasomierza. Gdy czasomierz zostanie wyłączony, resetuje; nie istnieje sposób, aby wstrzymywać składnik <xref:System.Windows.Forms.Timer>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Timer>
- [Timer, składnik](timer-component-windows-forms.md)
- [Ograniczenia właściwości Interval składnika Timer formularzy Windows Forms](limitations-of-the-timer-component-interval-property.md)
