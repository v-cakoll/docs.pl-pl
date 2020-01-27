---
title: Ograniczenia właściwości interwału składnika czasomierza
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: 15626a53f0541ff79e2098377d9dfdb4626ac155
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745235"
---
# <a name="limitations-of-the-windows-forms-timer-components-interval-property"></a>Ograniczenia właściwości Interval składnika Timer formularzy systemu Windows
Składnik <xref:System.Windows.Forms.Timer> Windows Forms ma właściwość <xref:System.Windows.Forms.Timer.Interval%2A>, która określa liczbę milisekund, które przechodzą między zdarzenie czasomierza a następnym. O ile składnik nie jest wyłączony, czasomierz nadal otrzymuje zdarzenie <xref:System.Windows.Forms.Timer.Tick> w mniej równych odstępach czasu.  
  
 Ten składnik jest przeznaczony dla środowiska Windows Formsowego. Jeśli potrzebujesz czasomierza odpowiedniego dla środowiska serwera, zobacz [wprowadzenie do czasomierzy oparte na serwerze](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
## <a name="the-interval-property"></a>Właściwość Interval  
 Właściwość <xref:System.Windows.Forms.Timer.Interval%2A> ma kilka ograniczeń, które należy wziąć pod uwagę podczas programowania składnika <xref:System.Windows.Forms.Timer>:  
  
- Jeśli aplikacja lub inna aplikacja wykonuje duże wymagania w systemie, takich jak długotrwałe pętle, obliczenia intensywnie korzystające z dysku, sieci lub dostępu do portów, aplikacja może nie pobierać zdarzeń czasomierza tak często, jak określa właściwość <xref:System.Windows.Forms.Timer.Interval%2A>.  
  
- Interwał nie jest gwarantowany do upływu czasu. Aby zapewnić dokładność, czasomierz powinien sprawdzić zegar systemu zgodnie z wymaganiami, zamiast próbować śledzić skumulowany czas wewnętrznie.  
  
- Precyzja właściwości <xref:System.Windows.Forms.Timer.Interval%2A> jest w milisekundach. Niektóre komputery zapewniają licznik o wysokiej rozdzielczości o rozdzielczości większej niż milisekundy. Dostępność takiego licznika zależy od sprzętu procesora komputera.
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Timer>
- [Timer, składnik](timer-component-windows-forms.md)
- [Timer, składnik — omówienie](timer-component-overview-windows-forms.md)
