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
ms.openlocfilehash: 992cc1f60ee3f08131b478d2336321bf87d7ef89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="asynchronous-programming-model-apm"></a>Model programowania asynchronicznego (APM)
Operacja asynchroniczna, która używa <xref:System.IAsyncResult> wzorca projektowego jest zaimplementowany jako dwie metody o nazwie **Begin *** OperationName* i **zakończenia *** OperationName* który rozpoczęcia i zakończenia asynchroniczną Operacja *OperationName* odpowiednio. Na przykład <xref:System.IO.FileStream> klasa udostępnia <xref:System.IO.FileStream.BeginRead%2A> i <xref:System.IO.FileStream.EndRead%2A> metody do asynchronicznego odczytywania bajtów z pliku. Te metody wdrożenia to wersja asynchroniczna elementu <xref:System.IO.FileStream.Read%2A> metody.  
  
> [!NOTE]
>  Począwszy od programu .NET Framework 4, biblioteka zadań równoległych zapewnia nowy model programowania asynchronicznego i równolegle. Aby uzyskać więcej informacji, zobacz [zadań biblioteki równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md) i [opartego na zadaniach asynchronicznej wzorca (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)).  
  
 Po wywołaniu **rozpocząć *** OperationName*, aplikacja może kontynuować wykonywania instrukcji w wątku wywołującym, gdy operacja asynchroniczna odbywa się w innym wątku. Dla każdego wywołania **rozpocząć *** OperationName*, również powinny wywoływać aplikacji **zakończenia *** OperationName* Aby uzyskać wyniki operacji.  
  
## <a name="beginning-an-asynchronous-operation"></a>Rozpoczyna operację asynchroniczną  
 **Rozpocząć *** OperationName* metoda rozpoczyna operację asynchroniczną *OperationName* i zwraca obiekt, który implementuje <xref:System.IAsyncResult> interfejsu. <xref:System.IAsyncResult> obiekty przechowywane informacje o operacji asynchronicznej. W poniższej tabeli przedstawiono informacje o operacji asynchronicznej.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|<xref:System.IAsyncResult.AsyncState%2A>|Opcjonalne obiekt specyficzne dla aplikacji, który zawiera informacje o operacji asynchronicznej.|  
|<xref:System.IAsyncResult.AsyncWaitHandle%2A>|A <xref:System.Threading.WaitHandle> można zablokować wykonywanie aplikacji przed zakończeniem operacji asynchronicznej.|  
|<xref:System.IAsyncResult.CompletedSynchronously%2A>|Wartość, która wskazuje, czy asynchroniczne operacja została wykonana w wątku używane do wywoływania **rozpocząć *** OperationName* zamiast kończenie na osobnym <xref:System.Threading.ThreadPool> wątku.|  
|<xref:System.IAsyncResult.IsCompleted%2A>|Wartość, która wskazuje, czy operacja asynchroniczna została ukończona.|  
  
 A **rozpocząć *** OperationName* metoda przyjmuje żadnych parametrów zadeklarowany w podpisie synchroniczną wersję metody, które są przekazywane przez wartości lub według odwołania. Dowolne parametry wyjściowe nie są częścią **rozpocząć *** OperationName* podpis metody. **Rozpocząć *** OperationName* podpis metody zawiera również dwie dodatkowe parametry. Określa pierwszy <xref:System.AsyncCallback> delegata, który odwołuje się do metody, która jest wywoływana po zakończeniu operacji asynchronicznej. Można określić obiektu wywołującego `null` (`Nothing` w języku Visual Basic) Jeśli chcesz metody wywoływane po zakończeniu operacji. Drugi dodatkowy parametr jest obiektem zdefiniowane przez użytkownika. Ten obiekt może służyć do przekazywania informacji o stanie specyficzne dla aplikacji do metody wywoływane po zakończeniu operacji asynchronicznej. Jeśli **rozpocząć *** OperationName* metoda przyjmuje dodatkowych parametrów specyficzne dla operacji, takich jak tablica bajtów do przechowywania Bajty odczytane z pliku, <xref:System.AsyncCallback> i obiektu stanu aplikacji są ostatniego parametru w **Rozpocząć *** OperationName* podpis metody.  
  
 **Rozpocznij *** OperationName* natychmiast zwraca sterowania do wywołania wątku. Jeśli **rozpocząć *** OperationName* metoda zgłasza wyjątków, wyjątki są zgłaszane przed uruchomieniem operacji asynchronicznej. Jeśli **rozpocząć *** OperationName* metoda zgłasza wyjątki, nie jest wywoływana metoda wywołania zwrotnego.  
  
## <a name="ending-an-asynchronous-operation"></a>Kończenie operacji asynchronicznej  
 **Zakończenia *** OperationName* metoda kończy operację asynchroniczną *OperationName*. Wartość zwracana **zakończenia *** OperationName* metody jest ten sam typ zwracany przez partnera synchroniczne i jest specyficzna dla operacji asynchronicznej. Na przykład <xref:System.IO.FileStream.EndRead%2A> metoda zwraca liczbę bajtów odczytanych z <xref:System.IO.FileStream> i <xref:System.Net.Dns.EndGetHostByName%2A> metoda zwraca <xref:System.Net.IPHostEntry> obiekt, który zawiera informacje o komputerze hosta. **Zakończenia *** OperationName* metoda przyjmuje żadnego lub parametry ref zadeklarowany w podpisie synchroniczną wersję metody. Oprócz parametry z metoda synchroniczna **zakończenia *** OperationName* zawiera również metody <xref:System.IAsyncResult> parametru. Obiekty wywołujące należy przekazać wystąpienia zwrócony przez odpowiedniego wywołania **rozpocząć *** OperationName*.  
  
 Jeśli operacja asynchroniczna reprezentowany przez <xref:System.IAsyncResult> obiektu nie zostało ukończone, kiedy **zakończenia *** OperationName* jest wywoływana **zakończenia *** OperationName* blokuje wątek wywołujący do Operacja asynchroniczna jest pełny. Wyjątki generowane przez operację asynchroniczną są generowane z **zakończenia *** OperationName* metody. Efekt wywołania metody **zakończenia *** OperationName* metody wiele razy z tym samym <xref:System.IAsyncResult> nie jest zdefiniowany. Podobnie wywołanie **zakończenia *** OperationName* metody z <xref:System.IAsyncResult> nie został zwrócony przez Begin powiązane, metoda również nie zdefiniowano.  
  
> [!NOTE]
>  W obu Niezdefiniowany scenariuszy implementacji należy wziąć pod uwagę zgłaszanie <xref:System.InvalidOperationException>.  
  
> [!NOTE]
>  Implementacje tego wzorca projektowego powiadomić wywołującego, który zakończył operację asynchroniczną, ustawiając <xref:System.IAsyncResult.IsCompleted%2A> na wartość true, wywołanie metody asynchroniczne wywołanie zwrotne (jeśli został określony) i sygnalizowania <xref:System.IAsyncResult.AsyncWaitHandle%2A>.  
  
 Deweloperzy aplikacji ma kilka decyzji projektowych do uzyskiwania dostępu do wyników operacji asynchronicznej. Poprawny wybór zależy od tego, czy aplikacja ma instrukcje, które mogą być wykonywane podczas operacji. Jeśli aplikacja nie może wykonać żadnych dodatkowych działań, dopóki nie odbierze wyniki operacji asynchronicznej, aplikacja musi zablokować dopóki wyniki są dostępne. Aby zablokować dopiero po zakończeniu operacji asynchronicznej, można użyć jednej z następujących metod:  
  
-   Wywołaj **zakończenia *** OperationName* z wątku głównego aplikacji, blokowanie wykonania aplikacji do operacji jest pełny. Na przykład, która ilustruje tej metody, zobacz [blokowanie wykonywania aplikacji poprzez zakończenie operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
-   Użyj <xref:System.IAsyncResult.AsyncWaitHandle%2A> do wykonywania aplikacji bloku dopiero po zakończeniu jednego lub więcej operacji. Na przykład, która ilustruje tej metody, zobacz [blokowania aplikacji wykonywania za pomocą właściwości AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Aplikacje, które nie mają być blokowane podczas operacji asynchronicznej można użyć jednej z następujących metod:  
  
-   Sondowania stanu ukończenia operacji sprawdzając <xref:System.IAsyncResult.IsCompleted%2A> właściwość okresowo i wywoływania **zakończenia *** OperationName* po zakończeniu operacji. Na przykład, która ilustruje tej metody, zobacz [sondowanie stanu operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
-   Użyj <xref:System.AsyncCallback> pełnomocnika, aby określić metodę do wywołania po zakończeniu operacji. Na przykład, która ilustruje tej metody, zobacz [używanie delegata AsyncCallback do kończenia operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Wywoływanie metod synchronicznych w sposób asynchroniczny](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 [Używanie delegata AsyncCallback i obiektu stanu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
