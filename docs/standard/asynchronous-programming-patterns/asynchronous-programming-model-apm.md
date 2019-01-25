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
ms.openlocfilehash: cff235fe45c75fda51e04d5b0b54bb3ee03051b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654311"
---
# <a name="asynchronous-programming-model-apm"></a>Model programowania asynchronicznego (APM)
Operacja asynchroniczna, która używa <xref:System.IAsyncResult> wzorzec projektowy jest implementowany jako dwie metody o nazwie `BeginOperationName` i `EndOperationName` , rozpoczęcia i zakończenia operacji asynchronicznej *OperationName* odpowiednio. Na przykład <xref:System.IO.FileStream> klasa udostępnia <xref:System.IO.FileStream.BeginRead%2A> i <xref:System.IO.FileStream.EndRead%2A> metody do asynchronicznego odczytu bajtów z pliku. Te metody wdrożenia to wersja asynchroniczna elementu <xref:System.IO.FileStream.Read%2A> metody.  
  
> [!NOTE]
>  Począwszy od programu .NET Framework 4 w bibliotece zadań równoległych przewiduje nowy model programowania asynchronicznego i równoległego. Aby uzyskać więcej informacji, zobacz [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md) i [opartego na zadaniach asynchronicznej wzorca (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)).  
  
 Po wywołaniu `BeginOperationName`, aplikacja może kontynuować wykonywania instrukcji na wątku wywołania, gdy operacja asynchroniczna odbywa się w innym wątku. Dla każdego wywołania `BeginOperationName`, aplikacja powinna również wywołać `EndOperationName` można pobrać wyniki operacji.  
  
## <a name="beginning-an-asynchronous-operation"></a>Rozpoczynanie operacji asynchronicznych  
 `BeginOperationName` Metoda rozpoczyna operację asynchroniczną *OperationName* i zwraca obiekt, który implementuje <xref:System.IAsyncResult> interfejsu. <xref:System.IAsyncResult> obiekty są przechowywane informacje o operacji asynchronicznej. W poniższej tabeli przedstawiono informacje o operacji asynchronicznej.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|<xref:System.IAsyncResult.AsyncState%2A>|Opcjonalne obiekt specyficzne dla aplikacji, który zawiera informacje o operacji asynchronicznej.|  
|<xref:System.IAsyncResult.AsyncWaitHandle%2A>|Element <xref:System.Threading.WaitHandle> można zablokować wykonywanie aplikacji do momentu ukończenia operacji asynchronicznej.|  
|<xref:System.IAsyncResult.CompletedSynchronously%2A>|Wartość, która wskazuje, czy operacja asynchroniczna została zakończona na wątek używany do wywoływania `BeginOperationName` zamiast kończenie na osobnym <xref:System.Threading.ThreadPool> wątku.|  
|<xref:System.IAsyncResult.IsCompleted%2A>|Wartość, która wskazuje, czy operacja asynchroniczna została zakończona.|  
  
 A `BeginOperationName` metoda przyjmuje parametry zadeklarowane w podpisie to wersja synchroniczna metody, które są przekazywane przez wartość lub przez odwołanie. Dowolne parametry wyjściowe nie są częścią `BeginOperationName` podpis metody. `BeginOperationName` Podpis metody zawiera także dwie dodatkowe parametry. Pierwsze zachowanie definiuje <xref:System.AsyncCallback> delegata, który odwołuje się do metody, która jest wywoływana po zakończeniu operacji asynchronicznej. Można określić obiekt wywołujący `null` (`Nothing` w języku Visual Basic) jeżeli chcesz metody wywoływane po zakończeniu operacji. Drugi dodatkowy parametr znajduje obiekt zdefiniowany przez użytkownika. Ten obiekt może służyć do przekazywania informacji o stanie specyficzne dla aplikacji do metody wywoływane, gdy operacja asynchroniczna. Jeśli `BeginOperationName` metoda przyjmuje dodatkowych parametrów określonych operacji, takich jak tablica bajtów do przechowywania bajtów odczytanych z pliku, <xref:System.AsyncCallback> i obiektu stanu aplikacji są ostatnimi parametrami w `BeginOperationName` podpis metody.  
  
 `BeginOperationName` Zwraca kontroli do wywołanego wątku od razu. Jeśli `BeginOperationName` metoda zgłasza wyjątek wyjątków, wyjątki są zgłaszane, przed rozpoczęciem operacji asynchronicznej. Jeśli `BeginOperationName` metoda zgłasza wyjątki, metody wywołania zwrotnego nie jest wywoływany.  
  
## <a name="ending-an-asynchronous-operation"></a>Zakończenie operacji asynchronicznej  
 `EndOperationName` Metoda kończy się operacja asynchroniczna *OperationName*. Wartość zwracana przez `EndOperationName` metoda jest ten sam typ zwracany przez jej synchronicznego odpowiednika i jest specyficzne dla operacji asynchronicznej. Na przykład <xref:System.IO.FileStream.EndRead%2A> metoda zwraca liczbę bajtów odczytanych z <xref:System.IO.FileStream> i <xref:System.Net.Dns.EndGetHostByName%2A> metoda zwraca <xref:System.Net.IPHostEntry> obiekt, który zawiera informacje o komputerze hosta. `EndOperationName` Metoda przyjmuje żadnego lub ref parametry zadeklarowane w podpisie to wersja synchroniczna metody. Oprócz parametrów z metody synchronicznej `EndOperationName` metoda obejmuje także <xref:System.IAsyncResult> parametru. Obiekty wywołujące muszą przekazywać wystąpienie zwrócone przez wywołanie odpowiedniej `BeginOperationName`.  
  
 Jeśli operacja asynchroniczna jest reprezentowane przez <xref:System.IAsyncResult> obiektu nie zostało zakończone, kiedy `EndOperationName` jest wywoływana, `EndOperationName` blokuje wątek wywołujący, aż do zakończenia operacji asynchronicznej. Wyjątki generowane przez operację asynchroniczną są generowane przez `EndOperationName` metody. Efekt wywoływania `EndOperationName` metoda wiele razy z takimi samymi <xref:System.IAsyncResult> nie został zdefiniowany. Podobnie wywołanie `EndOperationName` metody z <xref:System.IAsyncResult> który nie został zwrócony przez Begin powiązane, metoda również nie zdefiniowano.  
  
> [!NOTE]
>  W obu scenariuszach niezdefiniowane implementacji należy wziąć pod uwagę zgłaszanie <xref:System.InvalidOperationException>.  
  
> [!NOTE]
>  Implementacje tym wzorcu projektowym należy powiadomić obiekt wywołujący, zakończenia operacji asynchronicznej, ustawiając <xref:System.IAsyncResult.IsCompleted%2A> na wartość true, wywołanie metody asynchroniczne wywołanie zwrotne (jeśli został określony) i sygnalizowanie <xref:System.IAsyncResult.AsyncWaitHandle%2A>.  
  
 Deweloperzy aplikacji mają kilka uzasadnienie wyboru tych elementów do uzyskiwania dostępu do wyników operacji asynchronicznej. Odpowiedni wybór zależy od tego, czy aplikacja ma instrukcje, które mogą być wykonywane podczas kończenia operacji. Jeśli aplikacja nie może wykonać żadnych dodatkowych działań, dopóki nie odbierze wyniki operacji asynchronicznej, aplikację należy zablokować, dopóki wyniki są dostępne. Aby zablokować dopiero po zakończeniu operacji asynchronicznej, można użyć jednej z następujących metod:  
  
-   Wywołaj `EndOperationName` z wątku głównego aplikacji, blokowanie wykonania aplikacji do momentu operacji zostało zakończone. Na przykład, który ilustruje tej techniki, zobacz [blokowanie wykonywania aplikacji poprzez zakończenie operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
-   Użyj <xref:System.IAsyncResult.AsyncWaitHandle%2A> do bloku aplikacji wykonanie dopiero po zakończeniu co najmniej jednej operacji. Na przykład, który ilustruje tej techniki, zobacz [blokowania aplikacji wykonywania za pomocą właściwości AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Aplikacje, które nie muszą blokować podczas kończenia operacji asynchronicznej może użyć jednej z następujących metod:  
  
-   Sondowanie dotyczące stanu ukończenia operacji, sprawdzając <xref:System.IAsyncResult.IsCompleted%2A> właściwość okresowo i wywoływania `EndOperationName` po zakończeniu operacji. Na przykład, który ilustruje tej techniki, zobacz [sondowanie stanu operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
-   Użyj <xref:System.AsyncCallback> delegata, aby określić metodę do wywołania po ukończeniu operacji. Na przykład, który ilustruje tej techniki, zobacz [używanie delegata AsyncCallback do kończenia operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Zobacz także

- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Wywoływanie metod synchronicznych w sposób asynchroniczny](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)
- [Używanie delegata AsyncCallback i obiektu stanu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
