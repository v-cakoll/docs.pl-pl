---
title: Wielowątkowość w kontrolkach
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: 79832e12a10f02c909d2a28270594bcb4ea68656
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742144"
---
# <a name="multithreading-in-windows-forms-controls"></a>Wielowątkowość w formantach formularzy systemu Windows
W wielu aplikacjach można zwiększyć czas odpowiedzi interfejsu użytkownika, wykonując operacje czasochłonne na innym wątku. Dostępnych jest wiele narzędzi do wielowątkowości formantów Windows Forms, w tym <xref:System.Threading> przestrzeni nazw, metody <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> i składnika `BackgroundWorker`.  
  
> [!NOTE]
> Składnik `BackgroundWorker` zastępuje i dodaje funkcje do przestrzeni nazw <xref:System.Threading> i metody <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType>; Jednak są one zachowywane w celu zapewnienia zgodności z poprzednimi wersjami i użycia w przyszłości. Aby uzyskać więcej informacji, zobacz [Omówienie składnika BackgroundWorker](backgroundworker-component-overview.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: bezpieczne wątkowo wywołania kontrolek formularzy Windows Forms](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 Pokazuje, w jaki sposób zapewnić bezpieczne wątki do formantów Windows Forms.  
  
 [Instrukcje: użycie wątku w tle do wyszukiwania plików](how-to-use-a-background-thread-to-search-for-files.md)  
 Pokazuje, jak używać przestrzeni nazw <xref:System.Threading> i metody <xref:System.Windows.Forms.Control.BeginInvoke%2A> do wyszukiwania plików asynchronicznie.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ComponentModel.BackgroundWorker>  
 Dokumentuje składnik, który hermetyzuje wątek roboczy dla operacji asynchronicznych.  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 Dokumenty, jak załadować dźwięk asynchronicznie.  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 Dokumenty, jak asynchronicznie ładować obraz.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Instrukcje: uruchamianie operacji w tle](how-to-run-an-operation-in-the-background.md)  
 Pokazuje, jak wykonać czasochłonną operację za pomocą składnika <xref:System.ComponentModel.BackgroundWorker>.  
  
 [BackgroundWorker, składnik — omówienie](backgroundworker-component-overview.md)  
 Zawiera tematy opisujące, jak używać składnika <xref:System.ComponentModel.BackgroundWorker> dla operacji asynchronicznych.
