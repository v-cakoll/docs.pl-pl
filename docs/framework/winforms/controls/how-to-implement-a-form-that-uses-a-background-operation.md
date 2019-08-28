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
ms.openlocfilehash: e06b18558f6b3fa3cef47613bbaef16fb7c740f0
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046193"
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a>Instrukcje: implementowanie formularza korzystającego z operacji w tle
Poniższy przykładowy program tworzy formularz, który oblicza numery Fibonacci. Obliczenie jest wykonywane w wątku, który jest oddzielony od wątku interfejsu użytkownika, dzięki czemu interfejs użytkownika będzie nadal działać bez opóźnień w miarę kontynuowania obliczeń.  
  
 W programie Visual Studio jest dostępna szeroka pomoc techniczna dla tego zadania.  
  
 Zobacz [również przewodnik: Implementowanie formularza korzystającego z operacji](walkthrough-implementing-a-form-that-uses-a-background-operation.md)w tle.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Drawing i system. Windows. Forms.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
  
> [!CAUTION]
> W przypadku korzystania z wielowątkowości dowolnego sortowania użytkownik może ujawnić sobie bardzo poważne i złożone usterki. Przed zaimplementowaniem dowolnego rozwiązania, które używa wielowątkowości, należy zapoznać się z [zarządzanymi wątkami](../../../standard/threading/managed-threading-best-practices.md) .  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [Asynchroniczny wzorzec oparty na zdarzeniach — omówienie](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Zarządzana wątkowość — najlepsze rozwiązania](../../../standard/threading/managed-threading-best-practices.md)
