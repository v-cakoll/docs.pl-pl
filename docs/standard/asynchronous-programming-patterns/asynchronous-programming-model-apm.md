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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140143"
---
# <a name="asynchronous-programming-model-apm"></a>Model programowania asynchronicznego (APM)
Operacja asynchroniczna, <xref:System.IAsyncResult> która używa wzorca projektu jest `BeginOperationName` `EndOperationName` implementowana jako dwie metody o nazwie i które rozpoczynają i kończą operację asynchroniczną *OperationName* odpowiednio. Na przykład <xref:System.IO.FileStream> klasa zapewnia <xref:System.IO.FileStream.BeginRead%2A> <xref:System.IO.FileStream.EndRead%2A> i metody asynchronicznie odczytywane bajty z pliku. Metody te implementują asynchroniczną <xref:System.IO.FileStream.Read%2A> wersję metody.  
  
> [!NOTE]
> Począwszy od .NET Framework 4, biblioteka równoległa zadania zapewnia nowy model programowania asynchronicznego i równoległego. Aby uzyskać więcej informacji, zobacz [Biblioteka równoległa zadań (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md) i [asynchroniczny wzorzec (TAP) oparty na zadaniach).](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
  
 Po `BeginOperationName`wywołaniu , aplikacja może kontynuować wykonywanie instrukcji w wątku wywołującego, podczas gdy operacja asynchroniczna odbywa się w innym wątku. Dla każdego `BeginOperationName`wywołania , aplikacja `EndOperationName` powinna również wywołać, aby uzyskać wyniki operacji.  
  
## <a name="beginning-an-asynchronous-operation"></a>Rozpoczynanie operacji asynchronicznej  
 Metoda `BeginOperationName` rozpoczyna operację asynchroniczną *OperationName* i zwraca <xref:System.IAsyncResult> obiekt, który implementuje interfejs. <xref:System.IAsyncResult>obiekty przechowują informacje o operacji asynchronicznej. W poniższej tabeli przedstawiono informacje o operacji asynchronicznej.  
  
|Członek|Opis|  
|------------|-----------------|  
|<xref:System.IAsyncResult.AsyncState%2A>|Opcjonalny obiekt specyficzny dla aplikacji, który zawiera informacje o operacji asynchronicznej.|  
|<xref:System.IAsyncResult.AsyncWaitHandle%2A>|A, <xref:System.Threading.WaitHandle> który może służyć do blokowania wykonywania aplikacji, dopóki operacja asynchroniczna zostanie zakończona.|  
|<xref:System.IAsyncResult.CompletedSynchronously%2A>|Wartość, która wskazuje, czy operacja asynchroniczna została `BeginOperationName` ukończona w wątku używanym do wywoływania zamiast wypełniania w oddzielnym <xref:System.Threading.ThreadPool> wątku.|  
|<xref:System.IAsyncResult.IsCompleted%2A>|Wartość, która wskazuje, czy operacja asynchroniczna została ukończona.|  
  
 Metoda `BeginOperationName` przyjmuje wszystkie parametry zadeklarowane w podpisie synchronicznej wersji metody, które są przekazywane przez wartość lub przez odwołanie. Wszelkie parametry out nie są `BeginOperationName` częścią podpisu metody. Podpis `BeginOperationName` metody zawiera również dwa dodatkowe parametry. Pierwszy z nich definiuje <xref:System.AsyncCallback> delegata, który odwołuje się do metody, która jest wywoływana po zakończeniu operacji asynchronicznej. Obiekt wywołujący `null` `Nothing` można określić ( w języku Visual Basic), jeśli nie ma metody wywoływane po zakończeniu operacji. Drugi parametr dodatkowy jest obiektem zdefiniowanym przez użytkownika. Ten obiekt może służyć do przekazywania informacji o stanie specyficznych dla aplikacji do metody wywoływanej po zakończeniu operacji asynchronicznej. Jeśli `BeginOperationName` metoda przyjmuje dodatkowe parametry specyficzne dla operacji, takie jak tablica bajtów <xref:System.AsyncCallback> do przechowywania bajtów odczytanych `BeginOperationName` z pliku, obiekt stanu i aplikacji są ostatnimi parametrami w podpisie metody.  
  
 `BeginOperationName`natychmiast zwraca kontrolę do wątku wywołującego. Jeśli `BeginOperationName` metoda zgłasza wyjątki, wyjątki są generowane przed rozpoczęciem operacji asynchronicznej. Jeśli `BeginOperationName` metoda zgłasza wyjątki, metoda wywołania wywołania nie jest wywoływana.  
  
## <a name="ending-an-asynchronous-operation"></a>Zakończenie operacji asynchronicznej  
 Metoda `EndOperationName` kończy operację asynchroniczną *OperationName*. Wartość zwracana `EndOperationName` metody jest tego samego typu zwracanego przez jej synchroniczny odpowiednik i jest specyficzne dla operacji asynchronicznej. Na przykład <xref:System.IO.FileStream.EndRead%2A> metoda zwraca liczbę bajtów odczytanych <xref:System.Net.Dns.EndGetHostByName%2A> z <xref:System.Net.IPHostEntry> a, <xref:System.IO.FileStream> a metoda zwraca obiekt zawierający informacje o komputerze-hoście. Metoda `EndOperationName` pobiera wszelkie out lub ref parametry zadeklarowane w podpisie synchronicznej wersji metody. Oprócz parametrów z metody synchronicznej `EndOperationName` metoda zawiera również <xref:System.IAsyncResult> parametr. Obiekty wywołujące muszą przekazać wystąpienie zwrócone przez odpowiednie wywołanie do `BeginOperationName`.  
  
 Jeśli operacja asynchroniczna reprezentowana przez <xref:System.IAsyncResult> obiekt `EndOperationName` nie została `EndOperationName` ukończona, gdy jest wywoływana, blokuje wątek wywołujący, dopóki operacja asynchroniczna nie zostanie ukończona. Wyjątki generowane przez operację asynchroniczną `EndOperationName` są generowane z metody. Efekt wywołania `EndOperationName` metody wiele razy <xref:System.IAsyncResult> z tym samym nie jest zdefiniowany. Podobnie wywołanie `EndOperationName` metody <xref:System.IAsyncResult> z, który nie został zwrócony przez pokrewną Begin metody również nie jest zdefiniowany.  
  
> [!NOTE]
> Dla jednego z niezdefiniowanych scenariuszy realizatorów należy rozważyć rzucanie <xref:System.InvalidOperationException>.  
  
> [!NOTE]
> Realizatory tego wzorca projektu należy powiadomić obiekt wywołujący, <xref:System.IAsyncResult.IsCompleted%2A> że operacja asynchroniczna zakończone przez ustawienie true, wywołanie <xref:System.IAsyncResult.AsyncWaitHandle%2A>metody wywołania asynchronicznego (jeśli został określony) i sygnalizacji .  
  
 Deweloperzy aplikacji mają kilka opcji projektowania dostępu do wyników operacji asynchronicznej. Właściwy wybór zależy od tego, czy aplikacja ma instrukcje, które można wykonać po zakończeniu operacji. Jeśli aplikacja nie może wykonać żadnej dodatkowej pracy, dopóki nie otrzyma wyników operacji asynchronicznej, aplikacja musi blokować, dopóki wyniki nie będą dostępne. Aby zablokować do zakończenia operacji asynchronicznej, można użyć jednej z następujących metod:  
  
- Wywołanie `EndOperationName` z głównego wątku aplikacji, blokowanie wykonywania aplikacji, dopóki operacja nie zostanie zakończona. Na przykład, który ilustruje tę technikę, zobacz [Blokowanie wykonywania aplikacji przez zakończenie operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
- Użyj <xref:System.IAsyncResult.AsyncWaitHandle%2A> do blokowania wykonywania aplikacji, dopóki nie zostanie ukończona jedna lub więcej operacji. Na przykład, który ilustruje tę technikę, zobacz [Blokowanie wykonywania aplikacji przy użyciu AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Aplikacje, które nie muszą blokować po zakończeniu operacji asynchronicznej, mogą używać jednej z następujących metod:  
  
- Sonduj stan ukończenia <xref:System.IAsyncResult.IsCompleted%2A> operacji, sprawdzając właściwość okresowo i wywołując `EndOperationName` po zakończeniu operacji. Na przykład, który ilustruje tę technikę, zobacz [Sondowanie stanu operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
- Użyj <xref:System.AsyncCallback> pełnomocnika, aby określić metodę, która ma być wywoływana po zakończeniu operacji. Na przykład, który ilustruje tę technikę, zobacz [Za pomocą delegata AsyncCallback do zakończenia operacji asynchronicznej](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Zobacz też

- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Wywołanie metod synchronicznych w sposób asynchroniczny](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)
- [Używanie delegata AsyncCallback i obiektu stanu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
