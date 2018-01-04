---
title: "Wielowątkowość w formantach formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2b9c0a7b19df62867a4148b60e24b7d3ba9bcce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="multithreading-in-windows-forms-controls"></a>Wielowątkowość w formantach formularzy systemu Windows
W wielu aplikacjach możesz wprowadzić interfejsu użytkownika (UI) poprawę reakcji, wykonując czas operacji w innym wątku. Wiele narzędzi dostępnych dla wielowątkowości formantów formularzy systemu Windows, w tym <xref:System.Threading> przestrzeni nazw, <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> metody i `BackgroundWorker` składnika.  
  
> [!NOTE]
>  `BackgroundWorker` Składnika zastępuje i dodaje funkcje do <xref:System.Threading> przestrzeni nazw i <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> metody, jednak te pozostają dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana. Aby uzyskać więcej informacji, zobacz [BackgroundWorker — informacje o składniku](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: bezpieczne wątkowo wywołania kontrolek formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 Pokazuje, jak nawiązać bezpieczne wątkowo wywołania formantów formularzy systemu Windows.  
  
 [Instrukcje: użycie wątku w tle do wyszukiwania plików](../../../../docs/framework/winforms/controls/how-to-use-a-background-thread-to-search-for-files.md)  
 Przedstawia sposób użycia <xref:System.Threading> przestrzeni nazw i <xref:System.Windows.Forms.Control.BeginInvoke%2A> metody do wyszukiwania plików asynchronicznie.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ComponentModel.BackgroundWorker>  
 Dokumenty składnik, który hermetyzuje wątku roboczego dla operacji asynchronicznych.  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 Dokumenty jak ładowanie dźwięku asynchronicznie.  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 Omówiono sposób asynchronicznie ładowania obrazu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Instrukcje: uruchamianie operacji w tle](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 Pokazuje, jak wykonać czasochłonna operacja z <xref:System.ComponentModel.BackgroundWorker> składnika.  
  
 [BackgroundWorker, składnik — omówienie](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 Udostępnia tematy, które opisują sposób użycia <xref:System.ComponentModel.BackgroundWorker> składnika dla operacji asynchronicznych.
