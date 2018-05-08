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
ms.openlocfilehash: 998e159cceded6da2e9c3068680c45bc1c9345a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="synchronizing-data-for-multithreading"></a>Synchronizowanie danych na potrzeby wielowątkowości
Wiele wątków może wykonywać wywołania do właściwości i metod pojedynczego obiektu, jest krytyczne zsynchronizowania wywołań. W przeciwnym razie jeden wątek może przerwać czynności inny wątek, a obiekt może pozostać w nieprawidłowym stanie. Klasa, której członkami są chronione przed przerw w zasilaniu nosi nazwę wątkowo.  
  
 Wspólna infrastruktura języka udostępnia kilka strategii synchronizujący dostęp do wystąpienia i statyczne składniki:  
  
-   Regiony zsynchronizowane kodu. Można użyć <xref:System.Threading.Monitor> klasy lub kompilatora pomocy technicznej dla tej klasy zsynchronizować tylko zablokować kod, który musi, poprawa wydajności.  
  
-   Ręczną synchronizację. Można użyć obiektów synchronizacji podał w bibliotece klas programu .NET Framework. Zobacz [podstawowych Omówienie synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md), który zawiera omówienie <xref:System.Threading.Monitor> klasy.  
  
-   Konteksty zsynchronizowane. Można użyć <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute> Włącz synchronizację proste, automatyczne dla <xref:System.ContextBoundObject> obiektów.  
  
-   Kolekcja klas w <xref:System.Collections.Concurrent?displayProperty=nameWithType> przestrzeni nazw. Podaj te klasy wbudowanych synchronizowane dodawania i usuwania działań. Aby uzyskać więcej informacji, zobacz [kolekcje obsługujące wielowątkowość](../../../docs/standard/collections/thread-safe/index.md).  
  
 Środowisko uruchomieniowe języka wspólnego zapewnia modelu wątku, w którym klasy można podzielić na wiele kategorii, które mogą być synchronizowane na różne sposoby, w zależności od wymagań. W poniższej tabeli przedstawiono, jakie synchronizacji jest obsługiwane dla pól i metod z kategorią danego synchronizacji.  
  
|Kategoria|Globalne pól|Pola statyczne|Metody statyczne|Pola wystąpienia|Wystąpienie metody|Bloki kodu określonych|  
|--------------|-------------------|-------------------|--------------------|---------------------|----------------------|--------------------------|  
|Nie synchronizacji|Nie|Nie|Nie|Nie|Nie|Nie|  
|Kontekst zsynchronizowane|Nie|Nie|Nie|Tak|Tak|Nie|  
|Regiony zsynchronizowane kodu|Nie|Nie|Tylko wtedy, gdy oznaczone|Nie|Tylko wtedy, gdy oznaczone|Tylko wtedy, gdy oznaczone|  
|Ręczna synchronizacja|Ręcznie|Ręcznie|Ręcznie|Ręcznie|Ręcznie|Ręcznie|  
  
## <a name="no-synchronization"></a>Nie synchronizacji  
 Jest to wartość domyślna dla obiektów. Którymkolwiek wątku można uzyskać dostępu do dowolnej metody lub pola w dowolnym momencie. Tylko jeden wątek jednocześnie powinien uzyskiwać dostęp do tych obiektów.  
  
## <a name="manual-synchronization"></a>Ręczna synchronizacja  
 Biblioteka klas programu .NET Framework zapewnia szereg klas synchronizacja wątków. Zobacz [Przegląd elementów podstawowych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
## <a name="synchronized-code-regions"></a>Regiony zsynchronizowane kodu  
 Można użyć <xref:System.Threading.Monitor> klasy lub słowem kluczowym kompilatora, aby zsynchronizować bloki kodu, metody wystąpienia i metod statycznych. Nie jest obsługiwane dla pola statyczne zsynchronizowane.  
  
 Zarówno Visual Basic i C# obsługuje oznakowania bloki kodu ze słowem kluczowym konkretnego języka `lock` instrukcji w języku C# lub `SyncLock` instrukcji w języku Visual Basic. Gdy kod jest wykonywana przez wątek, podejmowana jest próba uzyskania blokady. Jeśli blokady ustawił została już przez inny wątek, bloki wątku, dopóki blokada staje się dostępny. Gdy wątek jest kończona bloku zsynchronizowanego kodu, blokada jest wydane niezależnie od tego, jak wątek opuszcza blok.  
  
> [!NOTE]
>  `lock` i `SyncLock` instrukcje są implementowane za pomocą <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> i <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>, więc innych metod <xref:System.Threading.Monitor> można użyć w połączeniu z nimi w obrębie regionu zsynchronizowane.  
  
 Można również dekoracji metodę o **MethodImplAttribute** i **MethodImplOptions.Synchronized**, który zawiera ten sam efekt co przy użyciu **Monitor** lub jednego z kompilatora słowa kluczowe do blokowania całej treści metody.  
  
 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> można przerwać wątek poza blokowania operacji, takich jak oczekiwania na dostęp do regionu zsynchronizowane kodu. **Thread.Interrupt** służy również do przerywanie wątków poza operacje, takie jak <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.  
  
> [!IMPORTANT]
>  Nie należy blokować typ — oznacza to, `typeof(MyType)` w języku C# `GetType(MyType)` w języku Visual Basic lub `MyType::typeid` w języku C++ — aby chronić `static` metod (`Shared` metod w języku Visual Basic). W zamian użyj prywatnego statycznego obiektu. Podobnie, nie używaj `this` w języku C# (`Me` w języku Visual Basic) do metody wystąpienia blokady. W zamian użyj prywatnego obiektu. Klasy lub wystąpienia może być zablokowane przez kodu innego niż własny, może powodować zakleszczenie lub problemów z wydajnością.  
  
### <a name="compiler-support"></a>Obsługa kompilatora  
 Zarówno Visual Basic i C# obsługuje słowem kluczowym języka, który używa <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> i <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> można zablokować obiektu. Obsługa języka Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) instrukcji; C# obsługuje [blokady](~/docs/csharp/language-reference/keywords/lock-statement.md) instrukcji.  
  
 W obu przypadkach, jeśli wyjątek w kodzie należy go zablokować, blokadę uzyskaną przez **blokady** lub **SyncLock** zwolnieniu automatycznie. Emituj Kompilatory języka C# i Visual Basic **spróbuj**/**koniec** zablokować z **Monitor.Enter** na początku try, i **Monitor.Exit**  w **koniec** bloku. Jeśli wyjątek wewnątrz **blokady** lub **SyncLock** bloku, **koniec** program obsługi działa co pozwala na pracę czyszczenia.  
  
## <a name="synchronized-context"></a>Kontekst zsynchronizowane  
 Można użyć **SynchronizationAttribute** na dowolnym **ContextBoundObject** do synchronizowania wszystkich pól i metody wystąpienia. Wszystkie obiekty w tej samej domenie kontekstu udostępnianie tego samego blokady. Wiele wątków mogą uzyskiwać dostęp do metod i pól, ale tylko jednego wątku jest dozwolona w dowolnym momencie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>  
 [Wątki i wątkowość](../../../docs/standard/threading/threads-and-threading.md)  
 [Przegląd elementów podstawowych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 [SyncLock, instrukcja](~/docs/visual-basic/language-reference/statements/synclock-statement.md)  
 [lock, instrukcja](~/docs/csharp/language-reference/keywords/lock-statement.md)
