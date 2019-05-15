---
title: 'Instrukcje: implementowanie formularza korzystającego z operacji w tle'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- background threads
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9f483f93-1613-4be1-a021-b4934e9c78f3
ms.openlocfilehash: df7c6caf7b23824a596e94e1bd62205907b0b56a
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592410"
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a>Instrukcje: implementowanie formularza korzystającego z operacji w tle
Poniższy przykład program tworzy formularz, który oblicza Fibonacci liczb. Obliczenie jest uruchamiane w wątku, który jest oddzielony od wątku interfejsu użytkownika, dzięki czemu interfejs użytkownika będzie nadal działać bez opóźnień w trakcie wykonywania obliczeń.  
  
 Brak zaawansowaną obsługę dla tego zadania w programie Visual Studio.  
  
 Zobacz też [instruktażu: Implementowanie formularza korzystającego z operacji w tle](walkthrough-implementing-a-form-that-uses-a-background-operation.md).  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
  
> [!CAUTION]
>  Korzystając z wielowątkowością jakiegokolwiek rodzaju, możesz potencjalnie się narazić na bardzo poważne i złożone usterek. Zapoznaj się z [zarządzana wątkowość najlepsze](../../../standard/threading/managed-threading-best-practices.md) przed zaimplementowaniem dowolne rozwiązanie, który używa wielowątkowości.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [Asynchroniczny wzorzec oparty na zdarzeniach — omówienie](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Zarządzana wątkowość — najlepsze rozwiązania](../../../standard/threading/managed-threading-best-practices.md)
