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
ms.openlocfilehash: 0a9ea3c8c9c589bb5954fa9771ffd1bb095f6d73
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140143"
---
# <a name="asynchronous-programming-model-apm"></a>Model programowania asynchronicznego (APM)
Operacja asynchroniczna, która używa wzorca projektowego <xref:System.IAsyncResult>, jest implementowana jako dwie metody o nazwie `BeginOperationName` i `EndOperationName`, która rozpoczyna i *kończy odpowiednio operację asynchroniczną operacji.* Na przykład Klasa <xref:System.IO.FileStream> dostarcza metody <xref:System.IO.FileStream.BeginRead%2A> i <xref:System.IO.FileStream.EndRead%2A>, aby asynchronicznie odczytywać bajty z pliku. Te metody implementują asynchroniczną wersję metody <xref:System.IO.FileStream.Read%2A>.  
  
> [!NOTE]
> Począwszy od .NET Framework 4, Biblioteka zadań równoległych udostępnia nowy model dla programowania asynchronicznego i równoległego. Aby uzyskać więcej informacji, zobacz [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md) i [wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)).  
  
 Po wywołaniu `BeginOperationName`aplikacja może kontynuować wykonywanie instrukcji w wątku wywołującym, gdy operacja asynchroniczna jest wykonywana w innym wątku. Dla każdego wywołania `BeginOperationName`aplikacja powinna również wywołać `EndOperationName`, aby uzyskać wyniki operacji.  
  
## <a name="beginning-an-asynchronous-operation"></a>Rozpoczynanie operacji asynchronicznej  
 Metoda `BeginOperationName` rozpoczyna *asynchroniczne operacje operacji i zwraca* obiekt implementujący interfejs <xref:System.IAsyncResult>. <xref:System.IAsyncResult> obiekty przechowują informacje o operacji asynchronicznej. W poniższej tabeli przedstawiono informacje na temat operacji asynchronicznej.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|<xref:System.IAsyncResult.AsyncState%2A>|Opcjonalny obiekt specyficzny dla aplikacji, który zawiera informacje o operacji asynchronicznej.|  
|<xref:System.IAsyncResult.AsyncWaitHandle%2A>|<xref:System.Threading.WaitHandle>, która może służyć do blokowania wykonywania aplikacji do momentu zakończenia operacji asynchronicznej.|  
|<xref:System.IAsyncResult.CompletedSynchronously%2A>|Wartość wskazująca, czy operacja asynchroniczna została zakończona na wątku używanym do wywoływania `BeginOperationName` zamiast wykonywania na osobnym wątku <xref:System.Threading.ThreadPool>.|  
|<xref:System.IAsyncResult.IsCompleted%2A>|Wartość wskazująca, czy operacja asynchroniczna została ukończona.|  
  
 Metoda `BeginOperationName` przyjmuje wszystkie parametry zadeklarowane w sygnaturze synchronicznej wersji metody, która jest przenoszona przez wartość lub przez odwołanie. Wszystkie parametry out nie są częścią sygnatury metody `BeginOperationName`. Sygnatura metody `BeginOperationName` również zawiera dwa dodatkowe parametry. Pierwszy z nich definiuje delegata <xref:System.AsyncCallback>, który odwołuje się do metody, która jest wywoływana po zakończeniu operacji asynchronicznej. Obiekt wywołujący może określić `null` (`Nothing` w Visual Basic), jeśli nie ma metody wywoływanej po zakończeniu operacji. Drugi dodatkowy parametr jest obiektem zdefiniowanym przez użytkownika. Ten obiekt może służyć do przekazywania informacji o stanie specyficznym dla aplikacji do metody wywoływanej po zakończeniu operacji asynchronicznej. Jeśli `BeginOperationName` Metoda przyjmuje dodatkowe parametry specyficzne dla operacji, takie jak tablica bajtowa do przechowywania bajtów odczytanych z pliku, <xref:System.AsyncCallback> i obiekt stanu aplikacji są ostatnimi parametrami w podpisie metody `BeginOperationName`.  
  
 `BeginOperationName` zwraca bezpośrednio sterowanie do wątku wywołującego. Jeśli metoda `BeginOperationName` zgłasza wyjątki, wyjątki są zgłaszane przed rozpoczęciem operacji asynchronicznej. Jeśli metoda `BeginOperationName` zgłasza wyjątki, metoda wywołania zwrotnego nie zostanie wywołana.  
  
## <a name="ending-an-asynchronous-operation"></a>Kończenie operacji asynchronicznej  
 Metoda `EndOperationName`a zakończyła *operację*asynchroniczną. Wartość zwracana metody `EndOperationName` jest tego samego typu zwracanego przez jego odpowiednik synchroniczny i jest specyficzna dla operacji asynchronicznej. Na przykład Metoda <xref:System.IO.FileStream.EndRead%2A> zwraca liczbę bajtów odczytanych z <xref:System.IO.FileStream>, a metoda <xref:System.Net.Dns.EndGetHostByName%2A> zwraca obiekt <xref:System.Net.IPHostEntry>, który zawiera informacje o komputerze hosta. Metoda `EndOperationName` przyjmuje wszystkie parametry out lub ref zadeklarowane w sygnaturze synchronicznej wersji metody. Oprócz parametrów z metody synchronicznej, Metoda `EndOperationName` również zawiera parametr <xref:System.IAsyncResult>. Obiekty wywołujące muszą przekazać wystąpienie zwrócone przez odpowiednie wywołanie do `BeginOperationName`.  
  
 Jeśli operacja asynchroniczna reprezentowana przez obiekt <xref:System.IAsyncResult> nie została ukończona po wywołaniu `EndOperationName`, `EndOperationName` blokuje wątek wywołujący do momentu ukończenia operacji asynchronicznej. Wyjątki zgłoszone przez operację asynchroniczną są generowane z metody `EndOperationName`. Efekt wywołania metody `EndOperationName` wiele razy z tą samą <xref:System.IAsyncResult> nie jest zdefiniowany. Podobnie wywołanie metody `EndOperationName` z <xref:System.IAsyncResult>, która nie została zwrócona przez pokrewną metodę Begin, nie jest również zdefiniowane.  
  
> [!NOTE]
> W przypadku jednego z niezdefiniowanych scenariuszy implementujące powinny rozważyć przegenerowanie <xref:System.InvalidOperationException>.  
  
> [!NOTE]
> Implementujący ten Wzorzec projektowy powinien poinformować wywołującego, że operacja asynchroniczna została ukończona przez ustawienie <xref:System.IAsyncResult.IsCompleted%2A> na true, wywołanie asynchronicznej metody wywołania zwrotnego (jeśli została określona) i sygnalizowanie <xref:System.IAsyncResult.AsyncWaitHandle%2A>.  
  
 Deweloperzy aplikacji mają kilka opcji projektowania do uzyskiwania dostępu do wyników operacji asynchronicznej. Prawidłowy wybór zależy od tego, czy aplikacja zawiera instrukcje, które mogą być wykonywane, gdy operacja zostanie ukończona. Jeśli aplikacja nie może wykonać żadnej dodatkowej pracy, dopóki nie odbierze wyników operacji asynchronicznej, aplikacja musi zablokować, dopóki wyniki nie będą dostępne. Aby zablokować do momentu zakończenia operacji asynchronicznej, można użyć jednej z następujących metod:  
  
- Wywołaj `EndOperationName` z głównego wątku aplikacji, blokując wykonywanie aplikacji do momentu ukończenia operacji. Przykład ilustrujący tę technikę można znaleźć w temacie [blokowanie wykonywania aplikacji przez zakończenie operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
- Użyj <xref:System.IAsyncResult.AsyncWaitHandle%2A>, aby zablokować wykonywanie aplikacji, dopóki nie zostanie ukończona co najmniej jedna operacja. Przykład ilustrujący tę technikę można znaleźć w temacie [blokowanie wykonywania aplikacji przy użyciu AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Aplikacje, które nie muszą blokować podczas kończenia operacji asynchronicznej, mogą korzystać z jednej z następujących metod:  
  
- Sprawdź stan ukończenia operacji, sprawdzając Właściwość <xref:System.IAsyncResult.IsCompleted%2A> okresowo i wywołując `EndOperationName` po zakończeniu operacji. Przykład ilustrujący tę technikę można znaleźć w temacie [sondowanie stanu operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
- Użyj delegata <xref:System.AsyncCallback>, aby określić metodę, która ma być wywoływana po zakończeniu operacji. Aby zapoznać się z przykładem, który ilustruje tę technikę, zobacz [Używanie delegata AsyncCallback do kończenia operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Zobacz także

- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Wywoływanie metod synchronicznych w sposób asynchroniczny](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)
- [Używanie delegata AsyncCallback i obiektu stanu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
