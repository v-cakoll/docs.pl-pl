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
ms.openlocfilehash: f9267bdd19a14995851f2689651c001815812912
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291178"
---
# <a name="mutexes"></a>Muteksy
<xref:System.Threading.Mutex>Aby zapewnić wyłączny dostęp do zasobu, można użyć obiektu. <xref:System.Threading.Mutex>Klasa używa większej liczby zasobów systemowych niż <xref:System.Threading.Monitor> Klasa, ale może być organizowana między granicami domeny aplikacji, może być używana z wieloma czekami i może służyć do synchronizowania wątków w różnych procesach. Aby zapoznać się z porównaniem mechanizmów synchronizacji zarządzanej, zobacz [Omówienie elementów pierwotnych synchronizacji](overview-of-synchronization-primitives.md).  
  
 Aby zapoznać się z przykładami kodu, zobacz dokumentację referencyjną dla <xref:System.Threading.Mutex.%23ctor%2A> konstruktorów.  
  
## <a name="using-mutexes"></a>Używanie muteksów  
 Wątek wywołuje <xref:System.Threading.WaitHandle.WaitOne%2A> metodę obiektu mutex, aby zażądać własności. Bloki wywołań do momentu, gdy mutex jest dostępny, lub do momentu, gdy upłynie opcjonalny interwał limitu czasu. Stan obiektu mutex jest sygnalizowane, jeśli żaden z nich nie należy do niego.  
  
 Wątek zwalnia element mutex, wywołując jego <xref:System.Threading.Mutex.ReleaseMutex%2A> metodę. Muteksy mają koligację wątku; oznacza to, że mutex można wydać tylko przez wątek, który jest właścicielem tego elementu. Jeśli wątek zwalnia element mutex, który nie jest właścicielem, <xref:System.ApplicationException> zostanie zgłoszony w wątku.  
  
 Ponieważ <xref:System.Threading.Mutex> Klasa pochodzi od <xref:System.Threading.WaitHandle> , można również wywołać statyczne <xref:System.Threading.WaitHandle.WaitAll%2A> lub metody, <xref:System.Threading.WaitHandle.WaitAny%2A> <xref:System.Threading.WaitHandle> Aby zażądać własności <xref:System.Threading.Mutex> w połączeniu z innymi dojściami oczekiwania.  
  
 Jeśli wątek jest właścicielem <xref:System.Threading.Mutex> , ten wątek może określić te same <xref:System.Threading.Mutex> w powtarzanych wywołaniach oczekiwania na żądanie bez blokowania jego wykonywania, jednak musi wydać <xref:System.Threading.Mutex> dowolną liczbę razy, aby zwolnić własność.  
  
## <a name="abandoned-mutexes"></a>Porzucone muteksy  
 Jeśli wątek kończy się bez zwalniania <xref:System.Threading.Mutex> , element mutex zostanie wskazany jako porzucony. Często oznacza to, że ten błąd programistyczny jest niespójny, ponieważ zasób, który jest chroniony przez mutex, może pozostać w stanie niespójności. W .NET Framework w wersji 2,0, <xref:System.Threading.AbandonedMutexException> jest zgłaszany w następnym wątku, który uzyskuje mutex.  
  
> [!NOTE]
> W .NET Framework wersje 1,0 i 1,1 <xref:System.Threading.Mutex> zostanie ustawiony stan zasygnalizowania, a następny wątek oczekujący otrzymuje własność. Jeśli żaden wątek nie oczekuje, <xref:System.Threading.Mutex> pozostaje w stanie sygnalizacji. Wyjątek nie jest zgłaszany.  
  
 W przypadku obiektu mutex w całym systemie porzucony obiekt mutex może wskazywać, że aplikacja została zakończona nieoczekiwanie (na przykład za pomocą Menedżera zadań systemu Windows).  
  
## <a name="local-and-system-mutexes"></a>Lokalne i systemowe muteksy  
 Muteksy są dwa typy: lokalne muteksy i nazwane muteksy systemowe. Jeśli utworzysz <xref:System.Threading.Mutex> Obiekt przy użyciu konstruktora, który akceptuje nazwę, zostanie on skojarzony z obiektem systemu operacyjnego o tej nazwie. Nazwane muteksy systemu są widoczne w całym systemie operacyjnym i mogą służyć do synchronizowania działań procesów. Można utworzyć wiele <xref:System.Threading.Mutex> obiektów, które reprezentują ten sam nazwany obiekt mutex, i można użyć metody, <xref:System.Threading.Mutex.OpenExisting%2A> Aby otworzyć istniejący nazwany element mutex systemu.  
  
 Lokalny element mutex istnieje tylko w ramach procesu. Może być używany przez dowolny wątek w procesie, który ma odwołanie do <xref:System.Threading.Mutex> obiektu lokalnego. Każdy <xref:System.Threading.Mutex> obiekt jest osobnym lokalnym elementem mutex.  
  
### <a name="access-control-security-for-system-mutexes"></a>Access Control zabezpieczenia dla muteksów systemu  
 .NET Framework wersja 2,0 zapewnia możliwość wykonywania zapytań i ustawiania zabezpieczeń kontroli dostępu do systemu Windows dla nazwanych obiektów systemowych. Ochrona muteksów systemu od momentu utworzenia jest zalecana, ponieważ obiekty systemowe są globalne i dlatego mogą być blokowane przez kod inny niż własny.  
  
 Aby uzyskać informacje na temat zabezpieczeń kontroli dostępu dla muteksów, <xref:System.Security.AccessControl.MutexSecurity> Zobacz <xref:System.Security.AccessControl.MutexAccessRule> klasy i, <xref:System.Security.AccessControl.MutexRights> Wyliczenie,, <xref:System.Threading.Mutex.GetAccessControl%2A> <xref:System.Threading.Mutex.SetAccessControl%2A> ,, i <xref:System.Threading.Mutex.OpenExisting%2A> metody <xref:System.Threading.Mutex> klasy oraz <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29> Konstruktor.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Mutex?displayProperty=nameWithType>
- <xref:System.Threading.Mutex.%23ctor%2A>
- <xref:System.Security.AccessControl.MutexSecurity?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.MutexAccessRule?displayProperty=nameWithType>
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- [Wątkowość obiektów i funkcji](threading-objects-and-features.md)
- [Wątki i wątkowość](threads-and-threading.md)
- [Wątkowość](index.md)
