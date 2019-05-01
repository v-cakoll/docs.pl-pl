---
title: Wielowątkowość w formantach formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: cc7f358a62c8057abb77e1f5a28544bb6c858d98
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012727"
---
# <a name="multithreading-in-windows-forms-controls"></a>Wielowątkowość w formantach formularzy systemu Windows
W wielu aplikacjach możesz wprowadzić interfejsu użytkownika (UI) zwiększyć szybkość reakcji, wykonywanie operacji czasochłonne na inny wątek. Wiele narzędzi dostępnych dla wielowątkowości formantów Windows Forms, w tym <xref:System.Threading> przestrzeni nazw, <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> metody i `BackgroundWorker` składnika.  
  
> [!NOTE]
>  `BackgroundWorker` Składnika zastępuje i dodaje funkcjonalność do <xref:System.Threading> przestrzeni nazw i <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> metody; jednak te są przechowywane zarówno w przypadku zgodności z poprzednimi wersjami, jak i użycia w przyszłości, jeśli wybierzesz. Aby uzyskać więcej informacji, zobacz [BackgroundWorker, składnik — omówienie](backgroundworker-component-overview.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Bezpieczne wątkowo wywołania kontrolek formularzy Windows Forms](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 Pokazuje, jak bezpieczne wątkowo wywołania kontrolek formularzy Windows Forms.  
  
 [Instrukcje: Użycie wątku w tle do wyszukiwania plików](how-to-use-a-background-thread-to-search-for-files.md)  
 Ilustruje sposób używania <xref:System.Threading> przestrzeni nazw i <xref:System.Windows.Forms.Control.BeginInvoke%2A> metody należy szukać plików asynchronicznie.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ComponentModel.BackgroundWorker>  
 Dokumenty składnika, który hermetyzuje wątku roboczego dla operacji asynchronicznych.  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 Dokumentują sposób ładowanie dźwięku asynchronicznie.  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 Dokumenty, jak załadować obraz asynchronicznie.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Instrukcje: Uruchamianie operacji w tle](how-to-run-an-operation-in-the-background.md)  
 Pokazuje, jak wykonywać czasochłonne operację, podając <xref:System.ComponentModel.BackgroundWorker> składnika.  
  
 [BackgroundWorker, składnik — omówienie](backgroundworker-component-overview.md)  
 Zawiera tematy, które opisują sposób używania <xref:System.ComponentModel.BackgroundWorker> składnika dla operacji asynchronicznych.
