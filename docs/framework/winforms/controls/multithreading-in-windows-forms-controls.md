---
title: Wielowątkowość w formantach formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: cf6790172b7445ad154eead5d17f8efddd78ffee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952686"
---
# <a name="multithreading-in-windows-forms-controls"></a>Wielowątkowość w formantach formularzy systemu Windows
W wielu aplikacjach można zwiększyć czas odpowiedzi interfejsu użytkownika, wykonując operacje czasochłonne na innym wątku. Dostępnych jest wiele narzędzi do wielowątkowości formantów Windows Forms, takich jak <xref:System.Threading> przestrzeń nazw <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> , Metoda i `BackgroundWorker` składnik.  
  
> [!NOTE]
> Składnik zastępuje i dodaje funkcje <xref:System.Threading> do przestrzeni nazw i <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> metodę, jednak są one zachowywane w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. `BackgroundWorker` Aby uzyskać więcej informacji, zobacz [Omówienie składnika BackgroundWorker](backgroundworker-component-overview.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Ustaw bezpieczne dla wątków wywołania formantów Windows Forms](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 Pokazuje, w jaki sposób zapewnić bezpieczne wątki do formantów Windows Forms.  
  
 [Instrukcje: Użyj wątku w tle do wyszukiwania plików](how-to-use-a-background-thread-to-search-for-files.md)  
 Pokazuje, jak używać <xref:System.Threading> przestrzeni nazw <xref:System.Windows.Forms.Control.BeginInvoke%2A> i metody do wyszukiwania plików asynchronicznie.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ComponentModel.BackgroundWorker>  
 Dokumentuje składnik, który hermetyzuje wątek roboczy dla operacji asynchronicznych.  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 Dokumenty, jak załadować dźwięk asynchronicznie.  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 Dokumenty, jak asynchronicznie ładować obraz.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Instrukcje: Uruchamianie operacji w tle](how-to-run-an-operation-in-the-background.md)  
 Pokazuje, jak wykonać czasochłonną operację za pomocą <xref:System.ComponentModel.BackgroundWorker> składnika.  
  
 [BackgroundWorker, składnik — omówienie](backgroundworker-component-overview.md)  
 Zawiera tematy opisujące, jak używać <xref:System.ComponentModel.BackgroundWorker> składnika dla operacji asynchronicznych.
