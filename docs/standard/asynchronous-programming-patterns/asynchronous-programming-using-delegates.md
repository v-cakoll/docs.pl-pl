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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bad5372af1d771dc93a20e61090ef84126f3e1eb
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45746864"
---
# <a name="asynchronous-programming-using-delegates"></a>Programowanie asynchroniczne przy użyciu delegatów
Delegaty umożliwiają wywołanie metody synchronicznej w sposób asynchroniczny. Podczas wywoływania delegata synchronicznie, `Invoke` metoda wywołuje metodę docelową bezpośrednio w bieżącym wątku. Jeśli `BeginInvoke` metoda jest wywoływana, środowisko uruchomieniowe języka wspólnego (CLR) kolejkuje żądanie i natychmiast zwraca do obiektu wywołującego. Metoda docelowy jest wywoływana asynchronicznie w wątku z puli wątków. Oryginalnego wątku, który przesłał żądanie, jest bezpłatne kontynuować wykonywanie równoległe przy użyciu metody docelowej. Jeśli metoda wywołania zwrotnego zostały określone w wywołaniu `BeginInvoke` , metody wywołania zwrotnego wywoływana jest metoda po zakończeniu metody docelowej. W przypadku metody wywołania zwrotnego `EndInvoke` metoda uzyskuje wartość zwracaną oraz wszelkie parametry wejścia/wyjścia lub tylko do danych wyjściowych. Jeśli zostanie określona żadna metoda wywołania zwrotnego, podczas wywoływania `BeginInvoke`, `EndInvoke` może być wywoływana z wątku, który wywołał `BeginInvoke`.  
  
> [!IMPORTANT]
>  Kompilatory, powinny wysyłać klasy obiektów delegowanych z `Invoke`, `BeginInvoke`, i `EndInvoke` metod za pomocą podpis delegata, określone przez użytkownika. `BeginInvoke` i `EndInvoke` metody powinny być dekorowane jako natywny. Ponieważ te metody są oznaczone jako natywnego, środowisko CLR oferuje automatycznie implementacji w czasie ładowania klasy. Moduł ładujący gwarantuje, że nie są zastępowane.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wywoływanie metod synchronicznych w sposób asynchroniczny](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 W tym artykule omówiono Użyj obiektów delegowanych, wykonywanie wywołań asynchronicznych do zwykłych metod i zawiera przykłady prostego kodu, które przedstawiono cztery sposoby oczekiwania na wywołanie asynchroniczne do zwrócenia.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 W tym artykule opisano programowania asynchronicznego przy użyciu programu .NET Framework.  
  
## <a name="see-also"></a>Zobacz także

* <xref:System.Delegate>
