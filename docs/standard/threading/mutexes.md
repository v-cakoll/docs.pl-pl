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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b2edf1f06873796bd63fceaca9a4bb99e509589
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910348"
---
# <a name="mutexes"></a>Muteksy
Aby zapewnić wyłączny <xref:System.Threading.Mutex> dostęp do zasobu, można użyć obiektu. Klasa używa większej liczby zasobów systemowych <xref:System.Threading.Monitor> niż Klasa, ale może być organizowana między granicami domeny aplikacji, może być używana z wieloma czekami i może służyć do synchronizowania wątków w różnych procesach. <xref:System.Threading.Mutex> Aby zapoznać się z porównaniem mechanizmów synchronizacji zarządzanej, zobacz [Omówienie elementów pierwotnych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Aby zapoznać się z przykładami kodu, zobacz dokumentację <xref:System.Threading.Mutex.%23ctor%2A> referencyjną dla konstruktorów.  
  
## <a name="using-mutexes"></a>Używanie muteksów  
 Wątek wywołuje metodę obiektu <xref:System.Threading.WaitHandle.WaitOne%2A> mutex, aby zażądać własności. Bloki wywołań do momentu, gdy mutex jest dostępny, lub do momentu, gdy upłynie opcjonalny interwał limitu czasu. Stan obiektu mutex jest sygnalizowane, jeśli żaden z nich nie należy do niego.  
  
 Wątek zwalnia element mutex, wywołując jego <xref:System.Threading.Mutex.ReleaseMutex%2A> metodę. Muteksy mają koligację wątku; oznacza to, że mutex można wydać tylko przez wątek, który jest właścicielem tego elementu. Jeśli wątek zwalnia element mutex, który nie <xref:System.ApplicationException> jest właścicielem, zostanie zgłoszony w wątku.  
  
 <xref:System.Threading.WaitHandle.WaitAny%2A> <xref:System.Threading.WaitHandle.WaitAll%2A> <xref:System.Threading.WaitHandle> Ponieważ Klasa pochodzi od <xref:System.Threading.WaitHandle>, można również wywołać statyczne<xref:System.Threading.Mutex> lub metody, aby zażądać własności w połączeniu z innymi dojściami oczekiwania. <xref:System.Threading.Mutex>  
  
 Jeśli wątek jest właścicielem <xref:System.Threading.Mutex>, ten wątek może określić te same <xref:System.Threading.Mutex> w powtarzanych wywołaniach oczekiwania na żądanie bez blokowania jego wykonywania, jednak musi wydać <xref:System.Threading.Mutex> dowolną liczbę razy, aby zwolnić własność.  
  
## <a name="abandoned-mutexes"></a>Porzucone muteksy  
 Jeśli wątek kończy się bez zwalniania <xref:System.Threading.Mutex>, element mutex zostanie wskazany jako porzucony. Często oznacza to, że ten błąd programistyczny jest niespójny, ponieważ zasób, który jest chroniony przez mutex, może pozostać w stanie niespójności. W .NET Framework w wersji 2,0, <xref:System.Threading.AbandonedMutexException> jest zgłaszany w następnym wątku, który uzyskuje mutex.  
  
> [!NOTE]
> W .NET Framework wersje 1,0 i 1,1 <xref:System.Threading.Mutex> zostanie ustawiony stan zasygnalizowania, a następny wątek oczekujący otrzymuje własność. Jeśli żaden wątek nie oczekuje, <xref:System.Threading.Mutex> pozostaje w stanie sygnalizacji. Nie zgłoszono żadnego wyjątku.  
  
 W przypadku obiektu mutex w całym systemie porzucony obiekt mutex może wskazywać, że aplikacja została zakończona nieoczekiwanie (na przykład za pomocą Menedżera zadań systemu Windows).  
  
## <a name="local-and-system-mutexes"></a>Lokalne i systemowe muteksy  
 Muteksy są dwa typy: lokalne muteksy i nazwane muteksy systemowe. Jeśli utworzysz <xref:System.Threading.Mutex> Obiekt przy użyciu konstruktora, który akceptuje nazwę, zostanie on skojarzony z obiektem systemu operacyjnego o tej nazwie. Nazwane muteksy systemu są widoczne w całym systemie operacyjnym i mogą służyć do synchronizowania działań procesów. Można utworzyć wiele <xref:System.Threading.Mutex> obiektów, które reprezentują ten sam nazwany obiekt mutex, i można <xref:System.Threading.Mutex.OpenExisting%2A> użyć metody, aby otworzyć istniejący nazwany element mutex systemu.  
  
 Lokalny element mutex istnieje tylko w ramach procesu. Może być używany przez dowolny wątek w procesie, który ma odwołanie do obiektu lokalnego <xref:System.Threading.Mutex> . Każdy <xref:System.Threading.Mutex> obiekt jest osobnym lokalnym elementem mutex.  
  
### <a name="access-control-security-for-system-mutexes"></a>Access Control zabezpieczenia dla muteksów systemu  
 .NET Framework wersja 2,0 zapewnia możliwość wykonywania zapytań i ustawiania zabezpieczeń kontroli dostępu do systemu Windows dla nazwanych obiektów systemowych. Ochrona muteksów systemu od momentu utworzenia jest zalecana, ponieważ obiekty systemowe są globalne i dlatego mogą być blokowane przez kod inny niż własny.  
  
 Aby uzyskać informacje na temat zabezpieczeń kontroli dostępu dla muteksów, <xref:System.Security.AccessControl.MutexSecurity> zobacz <xref:System.Security.AccessControl.MutexAccessRule> klasy i <xref:System.Threading.Mutex.GetAccessControl%2A>, <xref:System.Security.AccessControl.MutexRights> Wyliczenie <xref:System.Threading.Mutex> , <xref:System.Threading.Mutex.SetAccessControl%2A>,,, i <xref:System.Threading.Mutex.OpenExisting%2A> metody klasy oraz <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29> Konstruktor.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Mutex?displayProperty=nameWithType>
- <xref:System.Threading.Mutex.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.MutexSecurity?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.MutexAccessRule?displayProperty=nameWithType>
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- [Wątkowość obiektów i funkcji](threading-objects-and-features.md)
- [Wątki i wątkowość](threads-and-threading.md)
- [Wątkowość](index.md)
