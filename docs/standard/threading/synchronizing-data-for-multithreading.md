---
title: Synchronizowanie danych na potrzeby wielowątkowości
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET Framework], synchronizing threads
- managed threading
ms.assetid: b980eb4c-71d5-4860-864a-6dfe3692430a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb44fad991c8184686fcda90878bae2ec53260c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769151"
---
# <a name="synchronizing-data-for-multithreading"></a>Synchronizowanie danych na potrzeby wielowątkowości
Gdy wiele wątków może wykonywać wywołania do właściwości i metody pojedynczy obiekt, ważne jest, można zsynchronizować te wywołania. W przeciwnym razie jeden wątek może spowodować zakłócenie działania innego wątku, a obiekt może pozostać w nieprawidłowym stanie. Klasy, której członkami są chronione przed przerw w zasilaniu nazywa się metodą o bezpiecznych wątkach.  
  
 Common Language Infrastructure udostępnia kilka strategii do synchronizowania dostępu do wystąpienia i statyczne elementy członkowskie:  
  
- Regiony kodu zsynchronizowane. Możesz użyć <xref:System.Threading.Monitor> klasy lub kompilatora pomocy technicznej dla tej klasy zsynchronizować tylko Blokuj kod, który ich potrzebuje, poprawa wydajności.  
  
- Ręcznej synchronizacji. Można użyć dla obiektów synchronizacji zawartym w bibliotece klas programu .NET Framework. Zobacz [Przegląd podstawowych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md), który zawiera omówienie <xref:System.Threading.Monitor> klasy.  
  
- Konteksty zsynchronizowane. Możesz użyć <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> Aby włączyć synchronizację prostego, automatyczne dla <xref:System.ContextBoundObject> obiektów.  
  
- Klasy kolekcji w <xref:System.Collections.Concurrent?displayProperty=nameWithType> przestrzeni nazw. Te klasy oferują synchronizowane wbudowane Dodawanie i usuwanie operacji. Aby uzyskać więcej informacji, zobacz [kolekcje obsługujące wielowątkowość](../../../docs/standard/collections/thread-safe/index.md).  
  
 Środowisko uruchomieniowe języka wspólnego udostępnia model wątku, w którym klasy można podzielić na wiele kategorii, które mogą być synchronizowane na różne sposoby w zależności od wymagań. W poniższej tabeli przedstawiono, jakie pomoc techniczna synchronizacji jest dostępna dla pola i metody z kategorią danego synchronizacji.  
  
|Kategoria|Globalne pola|Pola statyczne|Metody statyczne|Pola wystąpienia|Metody wystąpienia|Bloki kodu określonych|  
|--------------|-------------------|-------------------|--------------------|---------------------|----------------------|--------------------------|  
|Brak synchronizacji|Nie|Nie|Nie|Nie|Nie|Nie|  
|Kontekst zsynchronizowane|Nie|Nie|Nie|Yes|Yes|Nie|  
|Regiony kodu zsynchronizowane|Nie|Nie|Tylko wtedy, gdy zaznaczone|Nie|Tylko wtedy, gdy zaznaczone|Tylko wtedy, gdy zaznaczone|  
|Ręcznej synchronizacji|Ręcznie|Ręcznie|Ręcznie|Ręcznie|Ręcznie|Ręcznie|  
  
## <a name="no-synchronization"></a>Brak synchronizacji  
 Jest to wartość domyślna dla obiektów. Wątek może uzyskać dostęp do dowolnej metody pól w dowolnym momencie. Tylko jeden wątek jednocześnie powinien uzyskać dostęp do tych obiektów.  
  
## <a name="manual-synchronization"></a>Ręcznej synchronizacji  
 Biblioteka klas .NET Framework oferuje pewną liczbę klas synchronizacji wątków. Zobacz [Przegląd elementów podstawowych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
## <a name="synchronized-code-regions"></a>Regiony kodu zsynchronizowane  
 Możesz użyć <xref:System.Threading.Monitor> klasy lub słowem kluczowym kompilatora, aby zsynchronizować bloki kodu, wystąpienia metod i metod statycznych. Nie jest obsługiwane dla zsynchronizowanej pola statyczne.  
  
 Visual Basic i C# obsługują znakowanie bloki kodu ze słowem kluczowym konkretnego języka `lock` instrukcji w języku C# lub `SyncLock` instrukcji w języku Visual Basic. Gdy kod jest wykonywany przez wątek, podejmowana jest próba uzyskania blokady. Jeśli blokada nabyła została już przez inny wątek, bloków wątku, dopóki blokada staje się dostępna. Jeśli wątek kończy działanie zsynchronizowane bloku kodu, blokada jest zwalniana, niezależnie od tego, jak wątek zamyka blok.  
  
> [!NOTE]
>  `lock` i `SyncLock` instrukcje są implementowane za pomocą <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> i <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>, więc inne metody <xref:System.Threading.Monitor> mogą być używane w połączeniu z nimi w ramach zsynchronizowane regionu.  
  
 Można również dekoracji metody z **MethodImplAttribute** i **MethodImplOptions.Synchronized**, który ma ten sam efekt jak użycie **Monitor** lub jednego z kompilatora słowa kluczowe do zablokowania całej treści metody.  
  
 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> można podzielić wątku z blokowaniem operacje, takie jak oczekiwanie na dostęp do synchronizowanych obszar kodu. **Thread.Interrupt** również służy do dzielenia wątków poza operacje, takie jak <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
>  Nie blokuj typu — oznacza to, `typeof(MyType)` w języku C# `GetType(MyType)` w języku Visual Basic lub `MyType::typeid` języka C++ — w celu ochrony `static` metody (`Shared` metod w języku Visual Basic). Zamiast tego użyj prywatnego obiektu statycznego. Podobnie, nie używaj `this` w języku C# (`Me` w języku Visual Basic) do metod wystąpienia blokady. Zamiast tego użyj prywatnego obiektu. Klasy lub wystąpienia mogą być zablokowane przez kod inny niż własny, powodując zakleszczenia lub problemy z wydajnością.  
  
### <a name="compiler-support"></a>Obsługa kompilatora  
 Visual Basic i C# obsługuje słowem kluczowym języka, który używa <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> i <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> można zablokować obiektu. Obsługa języka Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) instrukcję C# obsługuje [blokady](~/docs/csharp/language-reference/keywords/lock-statement.md) instrukcji.  
  
 W obu przypadkach, jeśli wyjątek jest zgłaszany w kodzie należy go zablokować, blokadę uzyskaną przez **blokady** lub **SyncLock** zwolnieniu automatycznie. Kompilatory C# i Visual Basic emisji **spróbuj**/**na koniec** zablokować za pomocą **Monitor.Enter** na początku try, i **Monitor.Exit**  w **na koniec** bloku. Jeśli wyjątek jest generowany wewnątrz **blokady** lub **SyncLock** bloku, **na koniec** uruchamia program obsługi pozwala wykonać pracę oczyszczania.  
  
## <a name="synchronized-context"></a>Kontekst zsynchronizowane  
 Możesz użyć **SynchronizationAttribute** na dowolnym **ContextBoundObject** zsynchronizować wszystkie wystąpienia metod i pól. Wszystkie obiekty w tej samej domenie kontekstu udostępnianie tego samego blokady. Wiele wątków może uzyskiwać dostęp do metod i pól, ale tylko jednego wątku jest dozwolona w dowolnym momencie.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>
- [Wątki i wątkowość](../../../docs/standard/threading/threads-and-threading.md)
- [Przegląd elementów podstawowych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
- [SyncLock, instrukcja](~/docs/visual-basic/language-reference/statements/synclock-statement.md)
- [lock, instrukcja](~/docs/csharp/language-reference/keywords/lock-statement.md)
