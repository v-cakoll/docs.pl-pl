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
ms.openlocfilehash: 15d99ef6ef3ae089216e586fe873043fa03b0d7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567292"
---
# <a name="asynchronous-programming-using-delegates"></a>Programowanie asynchroniczne przy użyciu delegatów
Obiekty delegowane umożliwiają wywołania metody synchroniczne w sposób asynchroniczny. Gdy delegata należy wywołać synchronicznie, `Invoke` metoda wywołuje metodę docelowego bezpośrednio w bieżącym wątku. Jeśli `BeginInvoke` metoda jest wywoływana, środowisko uruchomieniowe języka wspólnego (CLR) kolejkuje żądanie i natychmiast zwraca do obiektu wywołującego. Metoda docelowy jest wywoływana asynchronicznie w wątku z puli wątków. Oryginalnego wątku przesłane żądanie, będzie mógł kontynuować równolegle z metodą docelową. Jeśli metoda wywołania zwrotnego został określony w wywołaniu `BeginInvoke` , metody wywołania zwrotnego wywoływana jest metoda po zakończeniu metody docelowej. W przypadku metody wywołania zwrotnego `EndInvoke` metoda uzyskuje wartość zwracaną i wszelkie parametry wejścia/wyjścia lub w trybie tylko do danych wyjściowych. Jeśli zostanie określona żadna metoda wywołania zwrotnego, podczas wywoływania metody `BeginInvoke`, `EndInvoke` można wywołać z wątku, który wywołuje `BeginInvoke`.  
  
> [!IMPORTANT]
>  Kompilatory powinien Emituj klasy obiektów delegowanych z `Invoke`, `BeginInvoke`, i `EndInvoke` metody za pomocą podpisu delegata określone przez użytkownika. `BeginInvoke` i `EndInvoke` metody powinny być dekorowane jako natywne. Ponieważ te metody są oznaczone jako natywną, CLR automatycznie udostępnia implementację w czasie ładowania klasy. Moduł ładujący gwarantuje, że nie zostały zastąpione.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wywoływanie metod synchronicznych w sposób asynchroniczny](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Omówiono korzystanie z obiektów delegowanych z wywołań asynchronicznych metod zwykłej i przykłady kodu, które przedstawiono cztery sposoby oczekiwania na wywołanie asynchroniczne do zwrócenia.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 W tym artykule opisano programowanie asynchroniczne z programu .NET Framework.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Delegate>
