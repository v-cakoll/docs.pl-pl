---
title: Muteksy
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- wait handles
- threading [.NET Framework], Mutex class
- Mutex class, about Mutex class
- threading [.NET Framework], cross-process synchronization
ms.assetid: 9dd06e25-12c0-4a9e-855a-452dc83803e2
ms.openlocfilehash: 874f879697db0b47c73626350eeb05a01b38e1bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127554"
---
# <a name="mutexes"></a>Muteksy
Obiekt służy <xref:System.Threading.Mutex> do zapewnienia wyłącznego dostępu do zasobu. Klasa <xref:System.Threading.Mutex> używa więcej zasobów <xref:System.Threading.Monitor> systemowych niż klasa, ale może być organizowane przez granice domeny aplikacji, może być używany z wieloma oczekiwaniami i może służyć do synchronizowania wątków w różnych procesach. Aby uzyskać porównanie zarządzanych mechanizmów synchronizacji, zobacz [Omówienie podstawowych elementów synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Przykłady kodu można znaleźć w dokumentacji referencyjnej <xref:System.Threading.Mutex.%23ctor%2A> dla konstruktorów.  
  
## <a name="using-mutexes"></a>Korzystanie z muteksów  
 Wątek wywołuje <xref:System.Threading.WaitHandle.WaitOne%2A> metodę obiektu mutex do żądania własności. Bloki wywołania, dopóki mutex jest dostępna lub dopóki nie upływa opcjonalny przedział czasu. Stan obiektu mutex jest sygnalizowany, jeśli żaden wątek nie jest jego właścicielem.  
  
 Wątek zwalnia obiektu mutex, <xref:System.Threading.Mutex.ReleaseMutex%2A> wywołując jego metody. Muteksy mają koligacji wątku; oznacza to, że mutex może zostać zwolniony tylko przez wątek, który jest jego właścicielem. Jeśli wątek zwalnia mutex nie jest właścicielem, an <xref:System.ApplicationException> jest wyrzucany w wątku.  
  
 Ponieważ <xref:System.Threading.Mutex> klasa pochodzi <xref:System.Threading.WaitHandle>z , można również <xref:System.Threading.WaitHandle.WaitAll%2A> <xref:System.Threading.WaitHandle.WaitAny%2A> <xref:System.Threading.WaitHandle> wywołać statyczne lub metody <xref:System.Threading.Mutex> żądania własności w połączeniu z innymi uchwytami oczekiwania.  
  
 Jeśli wątek jest <xref:System.Threading.Mutex>właścicielem , ten <xref:System.Threading.Mutex> wątek można określić to samo w powtarzających się wywołań żądania oczekiwania bez blokowania jego wykonywania; jednak musi zwolnić <xref:System.Threading.Mutex> tyle razy, aby zwolnić własność.  
  
## <a name="abandoned-mutexes"></a>Opuszczone śluzy  
 Jeśli wątek kończy się bez <xref:System.Threading.Mutex>zwalniania , mutex mówi się, że porzucone. Często oznacza to poważny błąd programowania, ponieważ zasób, który chroni obiekt mutex, może pozostać w niespójnym stanie. W .NET Framework w wersji <xref:System.Threading.AbandonedMutexException> 2.0 jest generowany w następnym wątku, który uzyskuje obiektu mutex.  
  
> [!NOTE]
> W wersji .NET Framework 1.0 i 1.1 porzucony <xref:System.Threading.Mutex> jest ustawiony na stan sygnalizowany, a następny wątek oczekiwania pobiera własność. Jeśli żaden wątek nie <xref:System.Threading.Mutex> oczekuje, pozostaje w stanie sygnalizowanym. Wyjątek nie jest zgłaszany.  
  
 W przypadku obiektu mutex dla całego systemu porzucone mutex może wskazywać, że aplikacja została nagle zakończona (na przykład za pomocą Menedżera zadań systemu Windows).  
  
## <a name="local-and-system-mutexes"></a>Śluzy lokalne i systemowe  
 Muteksy są dwa typy: lokalne muteksy i nazwane mutexes systemu. Jeśli obiekt <xref:System.Threading.Mutex> zostanie utworzony przy użyciu konstruktora, który akceptuje nazwę, jest skojarzony z obiektem systemu operacyjnego o tej nazwie. Nazwane muteksy systemowe są widoczne w całym systemie operacyjnym i mogą być używane do synchronizowania działań procesów. Można utworzyć <xref:System.Threading.Mutex> wiele obiektów, które reprezentują ten sam nazwany <xref:System.Threading.Mutex.OpenExisting%2A> mutex systemu i można użyć metody, aby otworzyć istniejące nazwane mutex systemu.  
  
 Lokalny obiekt mutex istnieje tylko w ramach procesu. Może być używany przez dowolny wątek w procesie, <xref:System.Threading.Mutex> który ma odwołanie do obiektu lokalnego. Każdy <xref:System.Threading.Mutex> obiekt jest oddzielnym lokalnym obiektu mutex.  
  
### <a name="access-control-security-for-system-mutexes"></a>Zabezpieczenia kontroli dostępu dla muteksów systemu  
 .NET Framework w wersji 2.0 zapewnia możliwość wykonywania zapytań i ustawiania zabezpieczeń kontroli dostępu systemu Windows dla nazwanych obiektów systemowych. Ochrona obiektów mutexes systemu od momentu utworzenia jest zalecane, ponieważ obiekty systemu są globalne i dlatego mogą być zablokowane przez kod inny niż własny.  
  
 Aby uzyskać informacje na temat zabezpieczeń kontroli <xref:System.Security.AccessControl.MutexSecurity> <xref:System.Security.AccessControl.MutexAccessRule> dostępu dla <xref:System.Security.AccessControl.MutexRights> muteksów, <xref:System.Threading.Mutex.GetAccessControl%2A> <xref:System.Threading.Mutex.SetAccessControl%2A>zobacz <xref:System.Threading.Mutex.OpenExisting%2A> i klas, <xref:System.Threading.Mutex> wyliczenie, , , i metody klasy i <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29> konstruktora.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Mutex?displayProperty=nameWithType>
- <xref:System.Threading.Mutex.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.MutexSecurity?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.MutexAccessRule?displayProperty=nameWithType>
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- [Wątkowość obiektów i funkcji](threading-objects-and-features.md)
- [Wątki i gwintowanie](threads-and-threading.md)
- [Wątków](index.md)
