---
title: Timer — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: a13afba026f1f9eed095817c65637bb6a091c7f0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725288"
---
# <a name="timer-component-overview-windows-forms"></a>Timer — Informacje o składniku (Formularze systemu Windows)
Formularze Windows <xref:System.Windows.Forms.Timer> jest składnikiem, który wywołuje zdarzenie w regularnych odstępach czasu. Ten składnik jest przeznaczony dla środowiska Windows Forms. Jeśli potrzebujesz czasomierza, która jest odpowiednia w środowisku serwera, zobacz [wprowadzenie do serwerowych czasomierzy](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
## <a name="key-properties-methods-and-events"></a>Kluczowe właściwości, metody i zdarzenia  
 Długość przedziałów jest definiowany przez <xref:System.Windows.Forms.Timer.Interval%2A> właściwość, której wartość jest podana w milisekundach. Po włączeniu składnika <xref:System.Windows.Forms.Timer.Tick> zdarzenie jest zgłaszane w każdym interwale. Jest to, gdzie można dodać kod do wykonania. Aby uzyskać więcej informacji, zobacz [jak: Uruchamianie procedur w ustalonych odstępach czasu za pomocą składnika Timer formularzy Windows](run-procedures-at-set-intervals-with-wf-timer-component.md). Metody klucza <xref:System.Windows.Forms.Timer> składnik to <xref:System.Windows.Forms.Timer.Start%2A> i <xref:System.Windows.Forms.Timer.Stop%2A>, który czasomierza włączać i wyłączać. Po wyłączeniu czasomierza resetuje; nie ma możliwości wstrzymania <xref:System.Windows.Forms.Timer> składnika.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.Timer>
- [Timer, składnik](timer-component-windows-forms.md)
- [Ograniczenia właściwości Interval składnika Timer formularzy Windows Forms](limitations-of-the-timer-component-interval-property.md)
