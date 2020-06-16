---
title: Model programowania asynchronicznego (APM)
description: Dowiedz się więcej o modelu programowania asynchronicznego (APM) w programie .NET. Dowiedz się, jak rozpocząć i zakończyć operację asynchroniczną.
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
ms.openlocfilehash: 5ab5d15d24aac80ef4a31c039f7af9dacce4a8d8
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769187"
---
# <a name="asynchronous-programming-model-apm"></a>Model programowania asynchronicznego (APM)
Asynchroniczna operacja, która używa <xref:System.IAsyncResult> wzorca projektowego, jest implementowana jako dwie metody o nazwie `BeginOperationName` i `EndOperationName` , która rozpoczyna i kończy odpowiednio *operację* asynchroniczną. Na przykład <xref:System.IO.FileStream> Klasa zawiera <xref:System.IO.FileStream.BeginRead%2A> metody i, <xref:System.IO.FileStream.EndRead%2A> Aby asynchronicznie odczytywać bajty z pliku. Te metody implementują wersję asynchroniczną <xref:System.IO.FileStream.Read%2A> metody.  
  
> [!NOTE]
> Począwszy od .NET Framework 4, Biblioteka zadań równoległych udostępnia nowy model dla programowania asynchronicznego i równoległego. Aby uzyskać więcej informacji, zobacz [Biblioteka zadań równoległych (TPL)](../parallel-programming/task-parallel-library-tpl.md) i [wzorzec asynchroniczny oparty na zadaniach (TAP)](task-based-asynchronous-pattern-tap.md)).  
  
 Po wywołaniu `BeginOperationName` aplikacja może kontynuować wykonywanie instrukcji w wątku wywołującym, gdy operacja asynchroniczna odbywa się w innym wątku. Dla każdego wywołania do `BeginOperationName` , aplikacja powinna również wywołać, `EndOperationName` Aby uzyskać wyniki operacji.  
  
## <a name="beginning-an-asynchronous-operation"></a>Rozpoczynanie operacji asynchronicznej  
 `BeginOperationName`Metoda rozpoczyna *wykonywanie operacji* asynchronicznej i zwraca obiekt, który implementuje <xref:System.IAsyncResult> interfejs. <xref:System.IAsyncResult>obiekty przechowują informacje o operacji asynchronicznej. W poniższej tabeli przedstawiono informacje na temat operacji asynchronicznej.  
  
|Członek|Opis|  
|------------|-----------------|  
|<xref:System.IAsyncResult.AsyncState%2A>|Opcjonalny obiekt specyficzny dla aplikacji, który zawiera informacje o operacji asynchronicznej.|  
|<xref:System.IAsyncResult.AsyncWaitHandle%2A>|<xref:System.Threading.WaitHandle>, Który może służyć do blokowania wykonywania aplikacji do momentu zakończenia operacji asynchronicznej.|  
|<xref:System.IAsyncResult.CompletedSynchronously%2A>|Wartość wskazująca, czy operacja asynchroniczna została zakończona na wątku używanym do wywoływania `BeginOperationName` zamiast wykonywania w osobnym <xref:System.Threading.ThreadPool> wątku.|  
|<xref:System.IAsyncResult.IsCompleted%2A>|Wartość wskazująca, czy operacja asynchroniczna została ukończona.|  
  
 `BeginOperationName`Metoda przyjmuje wszystkie parametry zadeklarowane w sygnaturze synchronicznej wersji metody, która jest przenoszona przez wartość lub przez odwołanie. Wszystkie parametry out nie są częścią `BeginOperationName` sygnatury metody. `BeginOperationName`Sygnatura metody również zawiera dwa dodatkowe parametry. Pierwszy z nich definiuje <xref:System.AsyncCallback> delegata, który odwołuje się do metody, która jest wywoływana po zakończeniu operacji asynchronicznej. Obiekt wywołujący może określić `null` ( `Nothing` w Visual Basic), jeśli nie ma metody wywoływanej po zakończeniu operacji. Drugi dodatkowy parametr jest obiektem zdefiniowanym przez użytkownika. Ten obiekt może służyć do przekazywania informacji o stanie specyficznym dla aplikacji do metody wywoływanej po zakończeniu operacji asynchronicznej. Jeśli `BeginOperationName` Metoda przyjmuje dodatkowe parametry specyficzne dla operacji, takie jak tablica bajtowa do przechowywania bajtów odczytanych z pliku, <xref:System.AsyncCallback> obiekt stanu aplikacji jest ostatnim parametrem w `BeginOperationName` podpisie metody.  
  
 `BeginOperationName`zwraca bezpośrednio formant do wywołującego wątku. Jeśli `BeginOperationName` Metoda zgłasza wyjątki, wyjątki są zgłaszane przed rozpoczęciem operacji asynchronicznej. Jeśli `BeginOperationName` Metoda zgłasza wyjątki, metoda wywołania zwrotnego nie jest wywoływana.  
  
## <a name="ending-an-asynchronous-operation"></a>Kończenie operacji asynchronicznej  
 `EndOperationName`Metoda spowoduje zakończenie operacji asynchronicznej. *OperationName* Wartość zwracana `EndOperationName` metody jest tego samego typu zwracanego przez jego odpowiednik synchroniczny i jest specyficzna dla operacji asynchronicznej. Na przykład <xref:System.IO.FileStream.EndRead%2A> Metoda zwraca liczbę bajtów odczytanych z <xref:System.IO.FileStream> i, a <xref:System.Net.Dns.EndGetHostByName%2A> Metoda zwraca <xref:System.Net.IPHostEntry> obiekt, który zawiera informacje o komputerze hosta. `EndOperationName`Metoda przyjmuje wszystkie parametry out lub ref zadeklarowane w sygnaturze synchronicznej wersji metody. Oprócz parametrów z metody synchronicznej, `EndOperationName` Metoda zawiera również <xref:System.IAsyncResult> parametr. Obiekty wywołujące muszą przekazać wystąpienie zwrócone przez odpowiednie wywołanie do `BeginOperationName` .  
  
 Jeśli operacja asynchroniczna reprezentowana przez <xref:System.IAsyncResult> obiekt nie została ukończona `EndOperationName` , gdy jest wywoływana, `EndOperationName` blokuje wątek wywołujący do momentu ukończenia operacji asynchronicznej. Wyjątki zgłoszone przez operację asynchroniczną są generowane przez `EndOperationName` metodę. Efekt wywołania `EndOperationName` metody wiele razy z tą samą <xref:System.IAsyncResult> nie jest zdefiniowany. Podobnie wywołanie `EndOperationName` metody z <xref:System.IAsyncResult> , która nie została zwrócona przez powiązaną metodę Begin, nie jest również zdefiniowane.  
  
> [!NOTE]
> Dla każdego z niezdefiniowanych scenariuszy implementujących należy rozważyć Przerzucanie <xref:System.InvalidOperationException> .  
  
> [!NOTE]
> Implementujący ten Wzorzec projektowy powinien poinformować wywołującego, że operacja asynchroniczna została zakończona przez ustawienie <xref:System.IAsyncResult.IsCompleted%2A> wartości true, wywołanie asynchronicznej metody wywołania zwrotnego (jeśli została określona) i sygnalizowanie <xref:System.IAsyncResult.AsyncWaitHandle%2A> .  
  
 Deweloperzy aplikacji mają kilka opcji projektowania do uzyskiwania dostępu do wyników operacji asynchronicznej. Prawidłowy wybór zależy od tego, czy aplikacja zawiera instrukcje, które mogą być wykonywane, gdy operacja zostanie ukończona. Jeśli aplikacja nie może wykonać żadnej dodatkowej pracy, dopóki nie odbierze wyników operacji asynchronicznej, aplikacja musi zablokować, dopóki wyniki nie będą dostępne. Aby zablokować do momentu zakończenia operacji asynchronicznej, można użyć jednej z następujących metod:  
  
- Wywołaj `EndOperationName` z głównego wątku aplikacji, blokując wykonywanie aplikacji do momentu ukończenia operacji. Przykład ilustrujący tę technikę można znaleźć w temacie [blokowanie wykonywania aplikacji przez zakończenie operacji asynchronicznej](blocking-application-execution-by-ending-an-async-operation.md).  
  
- Użyj, <xref:System.IAsyncResult.AsyncWaitHandle%2A> Aby zablokować wykonywanie aplikacji, dopóki nie zostanie ukończona co najmniej jedna operacja. Przykład ilustrujący tę technikę można znaleźć w temacie [blokowanie wykonywania aplikacji przy użyciu AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Aplikacje, które nie muszą blokować podczas kończenia operacji asynchronicznej, mogą korzystać z jednej z następujących metod:  
  
- Sondowanie stanu ukończenia operacji przez sprawdzenie <xref:System.IAsyncResult.IsCompleted%2A> Właściwości okresowo i wywołanie `EndOperationName` po zakończeniu operacji. Przykład ilustrujący tę technikę można znaleźć w temacie [sondowanie stanu operacji asynchronicznej](polling-for-the-status-of-an-asynchronous-operation.md).  
  
- Użyj <xref:System.AsyncCallback> delegata, aby określić metodę, która ma być wywoływana po zakończeniu operacji. Aby zapoznać się z przykładem, który ilustruje tę technikę, zobacz [Używanie delegata AsyncCallback do kończenia operacji asynchronicznej](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Zobacz też

- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](event-based-asynchronous-pattern-eap.md)
- [Wywołanie metod synchronicznych w sposób asynchroniczny](calling-synchronous-methods-asynchronously.md)
- [Używanie delegata AsyncCallback i obiektu stanu](using-an-asynccallback-delegate-and-state-object.md)
