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
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159393"
---
# <a name="synchronizing-data-for-multithreading"></a>Synchronizowanie danych na potrzeby wielowątkowości

Gdy wiele wątków może wykonywać wywołania do właściwości i metod pojedynczego obiektu, ma krytyczne znaczenie, aby te wywołania były synchronizowane. W przeciwnym razie jeden wątek może przerwać działanie innego wątku, a obiekt może pozostać w nieprawidłowym stanie. Klasa, której członkowie są chronieni przed takimi zakłóceniami, jest nazywana wątkowo bezpiecznym.  
  
Platforma .NET udostępnia kilka strategii do synchronizowania dostępu do wystąpienia i statycznych elementów członkowskich:  
  
- Zsynchronizowane regiony kodu. Można użyć klasy <xref:System.Threading.Monitor> lub obsługi kompilatora dla tej klasy, aby synchronizować tylko blok kodu, który go potrzebuje, co poprawia wydajność.  
  
- Ręczna synchronizacja. Możesz użyć obiektów synchronizacji dostarczonych przez bibliotekę klas .NET. Zobacz [Omówienie elementów pierwotnych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md), które zawierają omówienie klasy <xref:System.Threading.Monitor>.  
  
- Synchronizowane konteksty. W przypadku aplikacji .NET Framework i Xamarin można użyć <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>, aby włączyć prostą, automatyczną synchronizację dla obiektów <xref:System.ContextBoundObject>.  
  
- Klasy kolekcji w przestrzeni nazw <xref:System.Collections.Concurrent?displayProperty=nameWithType>. Te klasy zapewniają wbudowaną synchronizację operacji dodawania i usuwania. Aby uzyskać więcej informacji, zobacz [kolekcje bezpieczne dla wątków](../../../docs/standard/collections/thread-safe/index.md).  
  
 Środowisko uruchomieniowe języka wspólnego udostępnia model wątku, w którym klasy mieszczą się w różnych kategoriach, które można synchronizować na różne sposoby, w zależności od wymagań. W poniższej tabeli przedstawiono obsługę synchronizacji dla pól i metod z daną kategorią synchronizacji.  
  
|Kategoria|Pola globalne|Pola statyczne|Metody statyczne|Pola wystąpienia|Metody wystąpień|Określone bloki kodu|  
|--------------|-------------------|-------------------|--------------------|---------------------|----------------------|--------------------------|  
|Brak synchronizacji|Nie|Nie|Nie|Nie|Nie|Nie|  
|Zsynchronizowany kontekst|Nie|Nie|Nie|Yes|Yes|Nie|  
|Zsynchronizowane regiony kodu|Nie|Nie|Tylko wtedy, gdy oznaczono|Nie|Tylko wtedy, gdy oznaczono|Tylko wtedy, gdy oznaczono|  
|Synchronizacja ręczna|Ręcznie|Ręcznie|Ręcznie|Ręcznie|Ręcznie|Ręcznie|  
  
## <a name="no-synchronization"></a>Brak synchronizacji  
 Jest to wartość domyślna dla obiektów. Dowolny wątek może uzyskać dostęp do dowolnej metody lub pola w dowolnym momencie. Tylko jeden wątek jednocześnie powinien uzyskać dostęp do tych obiektów.  
  
## <a name="manual-synchronization"></a>Synchronizacja ręczna  
 Biblioteka klas .NET udostępnia wiele klas do synchronizowania wątków. Zobacz [Omówienie elementów pierwotnych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
## <a name="synchronized-code-regions"></a>Zsynchronizowane regiony kodu  
 Można użyć klasy <xref:System.Threading.Monitor> lub słowa kluczowego kompilatora do synchronizowania bloków kodu, metod wystąpień i metod statycznych. Nie ma obsługi zsynchronizowanych pól statycznych.  
  
 Oba Visual Basic i C# obsługują oznaczenie bloków kodu za pomocą słowa kluczowego określonego języka, instrukcji `lock` w C# lub instrukcji `SyncLock` w Visual Basic. Gdy kod jest wykonywany przez wątek, podejmowana jest próba uzyskania blokady. Jeśli blokada została już uzyskana przez inny wątek, bloki wątku do momentu udostępnienia blokady staną się dostępne. Gdy wątek opuszcza zsynchronizowany blok kodu, blokada zostaje wydana, niezależnie od tego, jak wątek opuszcza blok.  
  
> [!NOTE]
> Instrukcje `lock` i `SyncLock` są implementowane przy użyciu <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> i <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>, więc inne metody <xref:System.Threading.Monitor> mogą być używane w połączeniu z nimi w zsynchronizowanym regionie.  
  
 Można także dekorować metodę o <xref:System.Runtime.CompilerServices.MethodImplAttribute> z wartością <xref:System.Runtime.CompilerServices.MethodImplOptions.Synchronized?displayProperty=nameWithType>, która ma taki sam efekt jak użycie <xref:System.Threading.Monitor> lub jednego z słów kluczowych kompilatora do zablokowania całej treści metody.  
  
 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> może służyć do przerwania wątku poza operacje blokowania, takie jak oczekiwanie na dostęp do synchronizowanego regionu kodu. **Wątek. Interrupt** służy również do przerwania wątków operacji, takich jak <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
> Nie blokuj typu — to znaczy, `typeof(MyType)` w C#, `GetType(MyType)` w Visual Basic lub `MyType::typeid` w C++ — w celu ochrony metod `static` (`Shared` metod w Visual Basic). Zamiast tego użyj prywatnego obiektu statycznego. Podobnie nie należy używać `this` w C# (`Me` w Visual Basic) do blokowania metod wystąpienia. Zamiast tego użyj obiektu prywatnego. Klasę lub wystąpienie można zablokować za pomocą kodu innego niż własny, potencjalnie powodującego zakleszczenie lub problemy z wydajnością.  
  
### <a name="compiler-support"></a>Obsługa kompilatora  
 Obie Visual Basic i C# obsługują słowo kluczowe języka, które używa <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> i <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> do blokowania obiektu. Visual Basic obsługuje instrukcję [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) ; C# obsługuje instrukcję [Lock](../../csharp/language-reference/keywords/lock-statement.md) .  
  
 W obu przypadkach, jeśli wyjątek jest zgłaszany w bloku kodu, blokada uzyskana przez **blokadę** lub **SyncLock** jest automatycznie wydawana. Kompilatory C# i Visual Basic emitują blok **try**/**finally** z **monitorem. Wprowadź** na początku try, a **monitor. Exit** w bloku **finally** . Jeśli w bloku **blokady** lub **SyncLock** zostanie zgłoszony wyjątek, program obsługi **finally** zostanie uruchomiony w celu umożliwienia wykonania wszelkich operacji oczyszczania.  
  
## <a name="synchronized-context"></a>Zsynchronizowany kontekst  

Tylko w przypadku aplikacji .NET Framework i Xamarin, można użyć <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> na dowolnym <xref:System.ContextBoundObject> do synchronizowania wszystkich metod i pól wystąpień. Wszystkie obiekty w tej samej domenie kontekstu mają tę samą blokadę. Wiele wątków może uzyskać dostęp do metod i pól, ale tylko jeden wątek jest dozwolony w dowolnym momencie.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>
- [Wątki i wątkowość](../../../docs/standard/threading/threads-and-threading.md)
- [Przegląd elementów podstawowych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
- [SyncLock, instrukcja](../../visual-basic/language-reference/statements/synclock-statement.md)
- [lock, instrukcja](../../csharp/language-reference/keywords/lock-statement.md)
