---
title: Model programowania asynchronicznego (APM)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- ending asynchronous operations
- starting asynchronous operations
- beginning asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming
- stopping asynchronous operations
- asynchronous programming, beginning operations
ms.assetid: c9b3501e-6bc6-40f9-8efd-4b6d9e39ccf0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c03a6dadae98d75b06b96bb3cde67db4747b8c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950868"
---
# <a name="asynchronous-programming-model-apm"></a>Model programowania asynchronicznego (APM)
Asynchroniczna operacja, która używa <xref:System.IAsyncResult> wzorca projektowego, jest implementowana jako `BeginOperationName` dwie `EndOperationName` metody o nazwie i, która rozpoczyna i kończy odpowiednio *operację* asynchroniczną. Na przykład <xref:System.IO.FileStream> Klasa <xref:System.IO.FileStream.BeginRead%2A> zawiera metody i <xref:System.IO.FileStream.EndRead%2A> , aby asynchronicznie odczytywać bajty z pliku. Te metody implementują wersję <xref:System.IO.FileStream.Read%2A> asynchroniczną metody.  
  
> [!NOTE]
> Począwszy od .NET Framework 4, Biblioteka zadań równoległych udostępnia nowy model dla programowania asynchronicznego i równoległego. Aby uzyskać więcej informacji, zobacz [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md) i [wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)).  
  
 Po wywołaniu `BeginOperationName`aplikacja może kontynuować wykonywanie instrukcji w wątku wywołującym, gdy operacja asynchroniczna odbywa się w innym wątku. Dla każdego wywołania do `BeginOperationName`, aplikacja powinna również wywołać `EndOperationName` , aby uzyskać wyniki operacji.  
  
## <a name="beginning-an-asynchronous-operation"></a>Rozpoczynanie operacji asynchronicznej  
 Metoda rozpoczyna wykonywanie operacji asynchronicznej i zwraca <xref:System.IAsyncResult> obiekt, który implementuje interfejs. `BeginOperationName` <xref:System.IAsyncResult>obiekty przechowują informacje o operacji asynchronicznej. W poniższej tabeli przedstawiono informacje na temat operacji asynchronicznej.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|<xref:System.IAsyncResult.AsyncState%2A>|Opcjonalny obiekt specyficzny dla aplikacji, który zawiera informacje o operacji asynchronicznej.|  
|<xref:System.IAsyncResult.AsyncWaitHandle%2A>|<xref:System.Threading.WaitHandle> , Który może służyć do blokowania wykonywania aplikacji do momentu zakończenia operacji asynchronicznej.|  
|<xref:System.IAsyncResult.CompletedSynchronously%2A>|Wartość wskazująca, czy operacja asynchroniczna została zakończona na wątku używanym do `BeginOperationName` wywoływania zamiast wykonywania w osobnym <xref:System.Threading.ThreadPool> wątku.|  
|<xref:System.IAsyncResult.IsCompleted%2A>|Wartość wskazująca, czy operacja asynchroniczna została ukończona.|  
  
 `BeginOperationName` Metoda przyjmuje wszystkie parametry zadeklarowane w sygnaturze synchronicznej wersji metody, która jest przenoszona przez wartość lub przez odwołanie. Wszystkie parametry out nie są częścią `BeginOperationName` sygnatury metody. Sygnatura `BeginOperationName` metody również zawiera dwa dodatkowe parametry. Pierwszy z nich definiuje <xref:System.AsyncCallback> delegata, który odwołuje się do metody, która jest wywoływana po zakończeniu operacji asynchronicznej. Obiekt wywołujący może `null` określić`Nothing` (w Visual Basic), jeśli nie ma metody wywoływanej po zakończeniu operacji. Drugi dodatkowy parametr jest obiektem zdefiniowanym przez użytkownika. Ten obiekt może służyć do przekazywania informacji o stanie specyficznym dla aplikacji do metody wywoływanej po zakończeniu operacji asynchronicznej. Jeśli metoda przyjmuje dodatkowe parametry specyficzne dla operacji, takie jak tablica bajtowa do przechowywania bajtów odczytanych z pliku <xref:System.AsyncCallback> , obiekt stanu aplikacji jest ostatnim parametrem w `BeginOperationName` podpisie metody. `BeginOperationName`  
  
 `BeginOperationName`zwraca bezpośrednio formant do wywołującego wątku. `BeginOperationName` Jeśli metoda zgłasza wyjątki, wyjątki są zgłaszane przed rozpoczęciem operacji asynchronicznej. `BeginOperationName` Jeśli metoda zgłasza wyjątki, metoda wywołania zwrotnego nie jest wywoływana.  
  
## <a name="ending-an-asynchronous-operation"></a>Kończenie operacji asynchronicznej  
 Metoda spowoduje zakończenie operacji asynchronicznej. `EndOperationName` Wartość `EndOperationName` zwracana metody jest tego samego typu zwracanego przez jego odpowiednik synchroniczny i jest specyficzna dla operacji asynchronicznej. Na przykład <xref:System.IO.FileStream.EndRead%2A> Metoda zwraca liczbę bajtów odczytanych <xref:System.IO.FileStream> z <xref:System.Net.IPHostEntry> i, a <xref:System.Net.Dns.EndGetHostByName%2A> Metoda zwraca obiekt, który zawiera informacje o komputerze hosta. `EndOperationName` Metoda przyjmuje wszystkie parametry out lub ref zadeklarowane w sygnaturze synchronicznej wersji metody. Oprócz parametrów z metody synchronicznej, `EndOperationName` Metoda <xref:System.IAsyncResult> zawiera również parametr. Obiekty wywołujące muszą przekazać wystąpienie zwrócone przez odpowiednie wywołanie do `BeginOperationName`.  
  
 Jeśli operacja asynchroniczna reprezentowana przez <xref:System.IAsyncResult> obiekt nie została ukończona, gdy `EndOperationName` jest wywoływana `EndOperationName` , blokuje wątek wywołujący do momentu ukończenia operacji asynchronicznej. Wyjątki zgłoszone przez operację asynchroniczną są generowane `EndOperationName` przez metodę. Efekt wywołania `EndOperationName` metody wiele razy z tą samą <xref:System.IAsyncResult> nie jest zdefiniowany. Podobnie wywołanie `EndOperationName` metody <xref:System.IAsyncResult> z, która nie została zwrócona przez powiązaną metodę Begin, nie jest również zdefiniowane.  
  
> [!NOTE]
> Dla każdego z niezdefiniowanych scenariuszy implementujących należy rozważyć Przerzucanie <xref:System.InvalidOperationException>.  
  
> [!NOTE]
> Implementujący ten Wzorzec projektowy powinien poinformować wywołującego, że operacja asynchroniczna została zakończona <xref:System.IAsyncResult.IsCompleted%2A> przez ustawienie wartości true, wywołanie asynchronicznej metody wywołania zwrotnego (jeśli została określona) i <xref:System.IAsyncResult.AsyncWaitHandle%2A>sygnalizowanie.  
  
 Deweloperzy aplikacji mają kilka opcji projektowania do uzyskiwania dostępu do wyników operacji asynchronicznej. Prawidłowy wybór zależy od tego, czy aplikacja zawiera instrukcje, które mogą być wykonywane, gdy operacja zostanie ukończona. Jeśli aplikacja nie może wykonać żadnej dodatkowej pracy, dopóki nie odbierze wyników operacji asynchronicznej, aplikacja musi zablokować, dopóki wyniki nie będą dostępne. Aby zablokować do momentu zakończenia operacji asynchronicznej, można użyć jednej z następujących metod:  
  
- Wywołaj `EndOperationName` z głównego wątku aplikacji, blokując wykonywanie aplikacji do momentu ukończenia operacji. Przykład ilustrujący tę technikę można znaleźć w temacie [blokowanie wykonywania aplikacji przez zakończenie operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
- Użyj, <xref:System.IAsyncResult.AsyncWaitHandle%2A> aby zablokować wykonywanie aplikacji, dopóki nie zostanie ukończona co najmniej jedna operacja. Przykład ilustrujący tę technikę można znaleźć w temacie [blokowanie wykonywania aplikacji przy użyciu AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Aplikacje, które nie muszą blokować podczas kończenia operacji asynchronicznej, mogą korzystać z jednej z następujących metod:  
  
- Sondowanie stanu ukończenia operacji przez sprawdzenie <xref:System.IAsyncResult.IsCompleted%2A> właściwości okresowo i wywołanie `EndOperationName` po zakończeniu operacji. Przykład ilustrujący tę technikę można znaleźć w temacie [sondowanie stanu operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
- <xref:System.AsyncCallback> Użyj delegata, aby określić metodę, która ma być wywoływana po zakończeniu operacji. Aby zapoznać się z przykładem, który ilustruje tę technikę, zobacz [Używanie delegata AsyncCallback do kończenia operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Zobacz także

- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Wywoływanie metod synchronicznych w sposób asynchroniczny](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)
- [Używanie delegata AsyncCallback i obiektu stanu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
