---
title: Programowanie asynchroniczne przy użyciu delegatów
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- BeginInvoke method
- asynchronous programming, delegates
- asynchronous delegates
- calling synchronous methods in asynchronous manner
- EndInvoke method
- calling asynchronous methods
- delegates [.NET Framework], asynchronous
- synchronous calling in asynchronous manner
ms.assetid: 38a345ca-6963-4436-9608-5c9defef9c64
ms.openlocfilehash: 4e17e6a96a12b705cf455d70add7e12a30f5fa90
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121746"
---
# <a name="asynchronous-programming-using-delegates"></a>Programowanie asynchroniczne przy użyciu delegatów
Delegaty umożliwiają wywoływanie metody synchronicznej w sposób asynchroniczny. W przypadku wywołania delegata synchronicznie Metoda `Invoke` wywołuje metodę docelową bezpośrednio w bieżącym wątku. Jeśli metoda `BeginInvoke` jest wywoływana, środowisko uruchomieniowe języka wspólnego (CLR) kolejkuje żądanie i natychmiast wraca do obiektu wywołującego. Metoda docelowa jest wywoływana asynchronicznie w wątku z puli wątków. Oryginalny wątek, który przesłał żądanie, jest bezpłatny, aby kontynuować wykonywanie równolegle z metodą docelową. Jeśli metoda wywołania zwrotnego została określona w wywołaniu metody `BeginInvoke`, metoda wywołania zwrotnego jest wywoływana, gdy metoda docelowa zostanie zakończona. W metodzie wywołania zwrotnego Metoda `EndInvoke` uzyskuje wartość zwracaną oraz wszystkie parametry wejściowe/wyjściowe lub wyjściowe. Jeśli podczas wywoływania `BeginInvoke`nie zostanie określona metoda wywołania zwrotnego, `EndInvoke` można wywołać z wątku, który wywołał `BeginInvoke`.  
  
> [!IMPORTANT]
> Kompilatory powinny emitować klasy delegatów z metodami `Invoke`, `BeginInvoke`i `EndInvoke` przy użyciu podpisu delegata określonego przez użytkownika. Metody `BeginInvoke` i `EndInvoke` powinny być oznaczone jako natywne. Ponieważ te metody są oznaczone jako natywne, środowisko CLR automatycznie udostępnia implementację w czasie ładowania klasy. Moduł ładujący gwarantuje, że nie są one zastępowane.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wywoływanie metod synchronicznych w sposób asynchroniczny](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 W tym artykule omówiono użycie delegatów do wykonywania wywołań asynchronicznych metod zwykłych i przedstawiono proste przykłady kodu, które pokazują cztery sposoby oczekiwania na zwrócenie wywołania asynchronicznego.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 Opisuje programowanie asynchroniczne przy użyciu .NET Framework.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Delegate>
