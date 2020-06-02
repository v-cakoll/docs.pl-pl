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
ms.openlocfilehash: 82e0a57c3d8e180456aed48886e38ca466db16c8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289970"
---
# <a name="asynchronous-programming-using-delegates"></a>Programowanie asynchroniczne przy użyciu delegatów
Delegaty umożliwiają wywoływanie metody synchronicznej w sposób asynchroniczny. W przypadku wywołania delegata synchronicznie `Invoke` Metoda wywołuje metodę docelową bezpośrednio w bieżącym wątku. Jeśli `BeginInvoke` Metoda jest wywoływana, środowisko uruchomieniowe języka wspólnego (CLR) kolejkuje żądanie i natychmiast wraca do obiektu wywołującego. Metoda docelowa jest wywoływana asynchronicznie w wątku z puli wątków. Oryginalny wątek, który przesłał żądanie, jest bezpłatny, aby kontynuować wykonywanie równolegle z metodą docelową. Jeśli metoda wywołania zwrotnego została określona w wywołaniu `BeginInvoke` metody, metoda wywołania zwrotnego jest wywoływana, gdy metoda docelowa zostanie zakończona. W metodzie wywołania zwrotnego `EndInvoke` metoda uzyskuje wartość zwracaną oraz wszystkie parametry wejściowe/wyjściowe lub wyjściowe. Jeśli metoda wywołania zwrotnego nie zostanie określona podczas wywoływania `BeginInvoke` , `EndInvoke` można wywołać z wątku, który wywołał `BeginInvoke` .  
  
> [!IMPORTANT]
> Kompilatory powinny emitować klasy delegatów `Invoke` z `BeginInvoke` `EndInvoke` metodami, i przy użyciu podpisu delegata określonego przez użytkownika. `BeginInvoke`Metody i `EndInvoke` powinny być dekoracyjne. Ponieważ te metody są oznaczone jako natywne, środowisko CLR automatycznie udostępnia implementację w czasie ładowania klasy. Moduł ładujący gwarantuje, że nie są one zastępowane.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wywołanie metod synchronicznych w sposób asynchroniczny](calling-synchronous-methods-asynchronously.md)  
 W tym artykule omówiono użycie delegatów do wykonywania wywołań asynchronicznych metod zwykłych i przedstawiono proste przykłady kodu, które pokazują cztery sposoby oczekiwania na zwrócenie wywołania asynchronicznego.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](event-based-asynchronous-pattern-eap.md)  
 Opisuje programowanie asynchroniczne przy użyciu .NET Framework.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Delegate>
