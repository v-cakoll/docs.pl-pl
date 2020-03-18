---
title: Synchronizowanie danych na potrzeby wielowątkowości
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET], synchronizing threads
- managed threading
ms.assetid: b980eb4c-71d5-4860-864a-6dfe3692430a
ms.openlocfilehash: a70bd3070d8b1dcd06e55d330a01d29071293f6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159393"
---
# <a name="synchronizing-data-for-multithreading"></a>Synchronizowanie danych dla wielowątkowości

Gdy wiele wątków można wywołać właściwości i metody pojedynczego obiektu, ważne jest, że te wywołania być synchronizowane. W przeciwnym razie jeden wątek może przerwać, co robi inny wątek, a obiekt może pozostać w nieprawidłowym stanie. Klasa, której elementy członkowskie są chronione przed takimi przerwami jest nazywany thread-safe.  
  
.NET udostępnia kilka strategii synchronizacji dostępu do elementów członkowskich wystąpienia i statycznych:  
  
- Zsynchronizowane regiony kodu. Można użyć <xref:System.Threading.Monitor> obsługi klasy lub kompilatora dla tej klasy, aby zsynchronizować tylko blok kodu, który go potrzebuje, poprawiając wydajność.  
  
- Synchronizacja ręczna. Można użyć obiektów synchronizacji dostarczonych przez bibliotekę klas .NET. Zobacz [Przegląd elementów pierwotnych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md), który <xref:System.Threading.Monitor> zawiera dyskusję na temat klasy.  
  
- Zsynchronizowane konteksty. W przypadku aplikacji .NET Framework i Xamarin można użyć opcji umożliwiającej <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> prostą, automatyczną synchronizację <xref:System.ContextBoundObject> obiektów.  
  
- Klasy kolekcji <xref:System.Collections.Concurrent?displayProperty=nameWithType> w przestrzeni nazw. Klasy te zapewniają wbudowane zsynchronizowane operacje dodawania i usuwania. Aby uzyskać więcej informacji, zobacz [Kolekcje bezpieczne dla wątków](../../../docs/standard/collections/thread-safe/index.md).  
  
 Czas wykonywania języka wspólnego zapewnia model wątku, w którym klasy należą do wielu kategorii, które mogą być synchronizowane na wiele różnych sposobów w zależności od wymagań. W poniższej tabeli przedstawiono, jakie wsparcie synchronizacji jest przewidziane dla pól i metod z danej kategorii synchronizacji.  
  
|Kategoria|Pola globalne|Pola statyczne|Metody statyczne|Pola wystąpienia|Metody Instance|Określone bloki kodu|  
|--------------|-------------------|-------------------|--------------------|---------------------|----------------------|--------------------------|  
|Brak synchronizacji|Nie|Nie|Nie|Nie|Nie|Nie|  
|Kontekst zsynchronizowany|Nie|Nie|Nie|Tak|Tak|Nie|  
|Regiony kodu zsynchronizowane|Nie|Nie|Tylko wtedy, gdy zaznaczono|Nie|Tylko wtedy, gdy zaznaczono|Tylko wtedy, gdy zaznaczono|  
|Synchronizacja ręczna|Ręcznie|Ręcznie|Ręcznie|Ręcznie|Ręcznie|Ręcznie|  
  
## <a name="no-synchronization"></a>Brak synchronizacji  
 Jest to wartość domyślna dla obiektów. Każdy wątek może uzyskać dostęp do dowolnej metody lub pola w dowolnym momencie. Tylko jeden wątek naraz powinien uzyskać dostęp do tych obiektów.  
  
## <a name="manual-synchronization"></a>Synchronizacja ręczna  
 Biblioteka klas .NET zawiera szereg klas do synchronizowania wątków. Zobacz Omówienie elementów [pierwotnych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
## <a name="synchronized-code-regions"></a>Regiony kodu zsynchronizowane  
 Za pomocą <xref:System.Threading.Monitor> słowa kluczowego klasy lub kompilatora można synchronizować bloki kodu, metody wystąpienia i metody statyczne. Nie ma obsługi zsynchronizowanych pól statycznych.  
  
 Zarówno Visual Basic i C# obsługuje znakowanie bloków kodu `lock` z określonego języka `SyncLock` słowa kluczowego, instrukcji w języku C# lub instrukcji w języku Visual Basic. Gdy kod jest wykonywany przez wątek, podejmowana jest próba uzyskania blokady. Jeśli blokada została już nabyta przez inny wątek, bloki wątku, dopóki blokada nie stanie się dostępna. Po zamknięciu wątku zsynchronizowanego bloku kodu, blokada jest zwalniana, bez względu na to, jak wątek kończy blok.  
  
> [!NOTE]
> I `lock` `SyncLock` instrukcje są implementowane przy użyciu <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> i <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>, więc inne metody <xref:System.Threading.Monitor> mogą być używane w połączeniu z nimi w zsynchronizowanym regionie.  
  
 Można również ozdobić <xref:System.Runtime.CompilerServices.MethodImplAttribute> metodę o <xref:System.Runtime.CompilerServices.MethodImplOptions.Synchronized?displayProperty=nameWithType>wartości , która ma <xref:System.Threading.Monitor> taki sam efekt jak za pomocą lub jednego ze słów kluczowych kompilatora, aby zablokować całą treść metody.  
  
 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>może służyć do przerwania wątku z operacji blokowania, takich jak oczekiwanie na dostęp do zsynchronizowanego regionu kodu. **Thread.Interrupt** jest również używany do przerywania <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>wątków z operacji, takich jak .  
  
> [!IMPORTANT]
> Nie należy blokować tego `typeof(MyType)` typu — `GetType(MyType)` czyli w języku C#, w języku Visual Basic lub `MyType::typeid` w języku C++ — w celu ochrony `static` metod (metody`Shared` w języku Visual Basic). Zamiast tego użyj prywatnego obiektu statycznego. Podobnie nie należy `this` używać w`Me` języku C# (w języku Visual Basic) do blokowania metod wystąpienia. Zamiast tego użyj obiektu prywatnego. Klasa lub wystąpienie mogą być zablokowane przez kod inny niż własne, potencjalnie powodując zakleszczenia lub problemy z wydajnością.  
  
### <a name="compiler-support"></a>Obsługa kompilatora  
 Zarówno Visual Basic i C# obsługuje <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> język słowa kluczowego, który używa i zablokować obiekt. Visual Basic obsługuje [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) instrukcji; C# obsługuje [lock](../../csharp/language-reference/keywords/lock-statement.md) instrukcji.  
  
 W obu przypadkach, jeśli wyjątek jest zgłaszany w bloku kodu, blokada nabyta przez **blokadę** lub **SyncLock** jest zwalniana automatycznie. Kompilatory Języka C# i Visual Basic emitują**wreszcie** blok **try**/z **Monitor.Enter** na początku try i **Monitor.Exit** w **końcu** bloku. Jeśli wyjątek jest zgłaszany wewnątrz **lock** lub **SyncLock** bloku, **finally** program obsługi uruchamia, aby umożliwić wykonanie wszelkich prac oczyszczania.  
  
## <a name="synchronized-context"></a>Kontekst zsynchronizowany  

Tylko w aplikacjach .NET Framework i Xamarin można użyć <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> na dowolny, <xref:System.ContextBoundObject> aby zsynchronizować wszystkie metody wystąpienia i pola. Wszystkie obiekty w tej samej domenie kontekstu mają tę samą blokadę. Wiele wątków mogą uzyskać dostęp do metod i pól, ale tylko jeden wątek jest dozwolone w dowolnym momencie.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>
- [Wątki i wątkowość](../../../docs/standard/threading/threads-and-threading.md)
- [Omówienie elementów pierwotnych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
- [SyncLock, instrukcja](../../visual-basic/language-reference/statements/synclock-statement.md)
- [lock — Instrukcja](../../csharp/language-reference/keywords/lock-statement.md)
