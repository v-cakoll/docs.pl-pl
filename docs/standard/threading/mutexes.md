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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127554"
---
# <a name="mutexes"></a>Muteksy
Aby zapewnić wyłączny dostęp do zasobu, można użyć obiektu <xref:System.Threading.Mutex>. Klasa <xref:System.Threading.Mutex> zużywa więcej zasobów systemowych niż Klasa <xref:System.Threading.Monitor>, ale może być organizowana między granicami domeny aplikacji, może być używana z wieloma czekami i może służyć do synchronizowania wątków w różnych procesach. Aby zapoznać się z porównaniem mechanizmów synchronizacji zarządzanej, zobacz [Omówienie elementów pierwotnych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Aby zapoznać się z przykładami kodu, zobacz dokumentację referencyjną dla konstruktorów <xref:System.Threading.Mutex.%23ctor%2A>.  
  
## <a name="using-mutexes"></a>Używanie muteksów  
 Wątek wywołuje metodę <xref:System.Threading.WaitHandle.WaitOne%2A> obiektu mutex, aby zażądać własności. Bloki wywołań do momentu, gdy mutex jest dostępny, lub do momentu, gdy upłynie opcjonalny interwał limitu czasu. Stan obiektu mutex jest sygnalizowane, jeśli żaden z nich nie należy do niego.  
  
 Wątek zwalnia element mutex, wywołując jego metodę <xref:System.Threading.Mutex.ReleaseMutex%2A>. Muteksy mają koligację wątku; oznacza to, że mutex można wydać tylko przez wątek, który jest właścicielem tego elementu. Jeśli wątek zwalnia element mutex, który nie jest właścicielem, w wątku zostanie wygenerowany <xref:System.ApplicationException>.  
  
 Ponieważ Klasa <xref:System.Threading.Mutex> pochodzi od <xref:System.Threading.WaitHandle>, można również wywołać statyczne <xref:System.Threading.WaitHandle.WaitAll%2A> lub <xref:System.Threading.WaitHandle.WaitAny%2A> metod <xref:System.Threading.WaitHandle>, aby zażądać własności <xref:System.Threading.Mutex> w połączeniu z innymi dojściami oczekiwania.  
  
 Jeśli wątek jest własnością <xref:System.Threading.Mutex>, ten wątek może określać ten sam <xref:System.Threading.Mutex> w powtarzanych wywołaniach oczekiwania na żądanie bez blokowania jego wykonywania; należy jednak zwolnić <xref:System.Threading.Mutex> jak wiele razy, aby zwolnić własność.  
  
## <a name="abandoned-mutexes"></a>Porzucone muteksy  
 Jeśli wątek kończy się bez zwalniania <xref:System.Threading.Mutex>, element mutex zostanie porzucony. Często oznacza to, że ten błąd programistyczny jest niespójny, ponieważ zasób, który jest chroniony przez mutex, może pozostać w stanie niespójności. W .NET Framework w wersji 2,0 <xref:System.Threading.AbandonedMutexException> jest generowany w następnym wątku, który uzyskuje mutex.  
  
> [!NOTE]
> W .NET Framework wersje 1,0 i 1,1 porzucona <xref:System.Threading.Mutex> jest ustawiona na stan sygnalizujący, a następny wątek oczekujący pobiera własność. Jeśli żaden wątek nie oczekuje, <xref:System.Threading.Mutex> pozostaje w stanie zasygnalizować. Nie zgłoszono żadnego wyjątku.  
  
 W przypadku obiektu mutex w całym systemie porzucony obiekt mutex może wskazywać, że aplikacja została zakończona nieoczekiwanie (na przykład za pomocą Menedżera zadań systemu Windows).  
  
## <a name="local-and-system-mutexes"></a>Lokalne i systemowe muteksy  
 Muteksy są dwa typy: lokalne muteksy i nazwane muteksy systemowe. Jeśli utworzysz obiekt <xref:System.Threading.Mutex> przy użyciu konstruktora, który akceptuje nazwę, jest on kojarzony z obiektem systemu operacyjnego o tej nazwie. Nazwane muteksy systemu są widoczne w całym systemie operacyjnym i mogą służyć do synchronizowania działań procesów. Można utworzyć wiele obiektów <xref:System.Threading.Mutex>, które reprezentują ten sam nazwany obiekt mutex, i można użyć metody <xref:System.Threading.Mutex.OpenExisting%2A>, aby otworzyć istniejący nazwany element mutex systemu.  
  
 Lokalny element mutex istnieje tylko w ramach procesu. Może być używany przez dowolny wątek w procesie, który ma odwołanie do lokalnego obiektu <xref:System.Threading.Mutex>. Każdy obiekt <xref:System.Threading.Mutex> jest osobnym lokalnym elementem mutex.  
  
### <a name="access-control-security-for-system-mutexes"></a>Access Control zabezpieczenia dla muteksów systemu  
 .NET Framework wersja 2,0 zapewnia możliwość wykonywania zapytań i ustawiania zabezpieczeń kontroli dostępu do systemu Windows dla nazwanych obiektów systemowych. Ochrona muteksów systemu od momentu utworzenia jest zalecana, ponieważ obiekty systemowe są globalne i dlatego mogą być blokowane przez kod inny niż własny.  
  
 Aby uzyskać informacje na temat zabezpieczeń kontroli dostępu dla muteksów, zobacz klasy <xref:System.Security.AccessControl.MutexSecurity> i <xref:System.Security.AccessControl.MutexAccessRule>, Wyliczenie <xref:System.Security.AccessControl.MutexRights>, <xref:System.Threading.Mutex.GetAccessControl%2A>, <xref:System.Threading.Mutex.SetAccessControl%2A>i <xref:System.Threading.Mutex.OpenExisting%2A> metod klasy <xref:System.Threading.Mutex> oraz Konstruktor <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Mutex?displayProperty=nameWithType>
- <xref:System.Threading.Mutex.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.MutexSecurity?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.MutexAccessRule?displayProperty=nameWithType>
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- [Wątkowość obiektów i funkcji](threading-objects-and-features.md)
- [Wątki i wątkowość](threads-and-threading.md)
- [Wątkowość](index.md)
