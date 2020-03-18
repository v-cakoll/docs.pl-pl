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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121746"
---
# <a name="asynchronous-programming-using-delegates"></a>Programowanie asynchroniczne przy użyciu delegatów
Delegaci umożliwiają wywołanie metody synchronicznej w sposób asynchroniczny. Podczas wywoływania delegata synchronicznie, `Invoke` metoda wywołuje metodę docelową bezpośrednio w bieżącym wątku. Jeśli `BeginInvoke` metoda jest wywoływana, program runtime języka wspólnego (CLR) kolejki żądania i zwraca natychmiast do obiektu wywołującego. Metoda docelowa jest wywoływana asynchronicznie w wątku z puli wątków. Oryginalny wątek, który przesłał żądanie, może kontynuować wykonywanie równolegle z metodą docelową. Jeśli metoda wywołania wywołania został określony `BeginInvoke` w wywołaniu metody, metoda wywołania wywołania wywołania jest wywoływana po zakończeniu metody docelowej. W metodzie wywołania `EndInvoke` zwrotnego metoda uzyskuje wartość zwracaną i wszelkie parametry wejścia/wyjścia lub tylko do wyjścia. Jeśli podczas wywoływania nie określono `BeginInvoke` `EndInvoke` żadnej metody wywołania wywołania, można wywołać z wątku, który o nazwie `BeginInvoke`.  
  
> [!IMPORTANT]
> Kompilatory powinny emitować `BeginInvoke`klasy `EndInvoke` delegata z `Invoke`, i metody przy użyciu podpisu delegata określonego przez użytkownika. I `BeginInvoke` `EndInvoke` metody powinny być urządzone jako rodzime. Ponieważ te metody są oznaczone jako macierzyste, CLR automatycznie zapewnia implementację w czasie ładowania klasy. Moduł ładujący zapewnia, że nie są one zastępowane.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wywołanie metod synchronicznych w sposób asynchroniczny](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 W tym artykule omówiono użycie delegatów do wywoływania asynchronicznego zwykłych metod i zawiera proste przykłady kodu, które pokazują cztery sposoby oczekiwania na asynchroniczne wywołanie do zwrócenia.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 Opisuje programowanie asynchroniczne z .NET Framework.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Delegate>
