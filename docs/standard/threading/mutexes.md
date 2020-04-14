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
ms.openlocfilehash: 3f020db49bcdcbf6ce3d573348a93b06e87db199
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242728"
---
# <a name="mutexes"></a>Muteksy
Za pomocą <xref:System.Threading.Mutex> obiektu można zapewnić wyłączny dostęp do zasobu. Klasa <xref:System.Threading.Mutex> używa więcej zasobów systemowych niż <xref:System.Threading.Monitor> klasa, ale może być organizowane przez granice domeny aplikacji, może być używany z wielu czeka i może służyć do synchronizacji wątków w różnych procesach. Aby zapoznać się z porównaniem mechanizmów synchronizacji zarządzanych, zobacz [Omówienie ćwigów synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Przykłady kodu można znaleźć w <xref:System.Threading.Mutex.%23ctor%2A> dokumentacji referencyjnej dla konstruktorów.  
  
## <a name="using-mutexes"></a>Korzystanie z muteksów  
 Wątek <xref:System.Threading.WaitHandle.WaitOne%2A> wywołuje metodę obiektu mutex do żądania własności. Wywołanie blokuje, dopóki obiekt mutex jest dostępny lub do momentu upływu opcjonalnego przedziału czasu. Stan obiektu mutex jest sygnalizowany, jeśli żaden wątek nie jest jego właścicielem.  
  
 Wątek zwalnia obiektu mutex, wywołując jego <xref:System.Threading.Mutex.ReleaseMutex%2A> metodę. Muteksy mają koligacji wątku; oznacza to, że mutex może być zwolniony tylko przez wątek, który jest jego właścicielem. Jeśli wątek zwalnia mutex nie <xref:System.ApplicationException> jest właścicielem, jest wyrzucany w wątku.  
  
 Ponieważ <xref:System.Threading.Mutex> klasa pochodzi <xref:System.Threading.WaitHandle>od , można również <xref:System.Threading.WaitHandle.WaitAll%2A> wywołać statyczne lub <xref:System.Threading.WaitHandle.WaitAny%2A> metody <xref:System.Threading.WaitHandle> żądania własności <xref:System.Threading.Mutex> w połączeniu z innymi uchwytami oczekiwania.  
  
 Jeśli wątek <xref:System.Threading.Mutex>jest właścicielem , <xref:System.Threading.Mutex> ten wątek można określić to samo w powtarzających się wywołań żądania oczekiwania bez blokowania jego wykonania; jednak musi zwolnić <xref:System.Threading.Mutex> tyle razy, aby zwolnić własność.  
  
## <a name="abandoned-mutexes"></a>Opuszczone mutexes  
 Jeśli wątek kończy się <xref:System.Threading.Mutex>bez zwalniania , mutex jest mówi się, że porzucone. Często wskazuje to na poważny błąd programowania, ponieważ zasób, który chroni obiekt mutex, może pozostać w niespójnym stanie. W .NET Framework w wersji 2.0 <xref:System.Threading.AbandonedMutexException> jest generowany w następnym wątku, który uzyskuje obiektu mutex.  
  
> [!NOTE]
> W .NET Framework w wersjach 1.0 i 1.1 porzucone <xref:System.Threading.Mutex> jest ustawiona na stan sygnalizowane i następny wątek oczekiwania pobiera własność. Jeśli żaden wątek <xref:System.Threading.Mutex> nie oczekuje, pozostaje w stanie sygnalizowanym. Wyjątek nie jest zgłaszany.  
  
 W przypadku obiektu mutex dla całego systemu porzucony obiekt mutex może wskazywać, że aplikacja została nagle zakończona (na przykład przy użyciu Menedżera zadań systemu Windows).  
  
## <a name="local-and-system-mutexes"></a>Mutexes lokalne i systemowe  
 Muteksy są dwa typy: lokalne muteksy i nazwane muteksy systemu. Jeśli tworzysz <xref:System.Threading.Mutex> obiekt przy użyciu konstruktora, który akceptuje nazwę, jest skojarzony z obiektem systemu operacyjnego o tej nazwie. Nazwane muteksy systemowe są widoczne w całym systemie operacyjnym i mogą być używane do synchronizowania działań procesów. Można utworzyć <xref:System.Threading.Mutex> wiele obiektów, które reprezentują ten sam system <xref:System.Threading.Mutex.OpenExisting%2A> mutex i można użyć metody, aby otworzyć istniejący nazwany mutex systemu.  
  
 Lokalny mutex istnieje tylko w ramach procesu. Może być używany przez dowolny wątek w procesie, który ma odwołanie do obiektu lokalnego. <xref:System.Threading.Mutex> Każdy <xref:System.Threading.Mutex> obiekt jest oddzielnym lokalnym obiektem mutex.  
  
### <a name="access-control-security-for-system-mutexes"></a>Zabezpieczenia kontroli dostępu dla mutexów systemowych  
 Program .NET Framework w wersji 2.0 umożliwia wykonywanie zapytań i ustawianie zabezpieczeń kontroli dostępu systemu Windows dla nazwanych obiektów systemowych. Ochrona muteksów systemowych od momentu utworzenia jest zalecana, ponieważ obiekty systemowe są globalne i dlatego mogą być blokowane przez kod inny niż własny.  
  
 Aby uzyskać informacje na temat zabezpieczeń kontroli <xref:System.Security.AccessControl.MutexSecurity> <xref:System.Security.AccessControl.MutexAccessRule> dostępu dla <xref:System.Security.AccessControl.MutexRights> muteksów, <xref:System.Threading.Mutex.GetAccessControl%2A> <xref:System.Threading.Mutex.SetAccessControl%2A>zobacz <xref:System.Threading.Mutex.OpenExisting%2A> i klasy, wyliczenie, , i metody <xref:System.Threading.Mutex> klasy i konstruktora. <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29>  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Mutex?displayProperty=nameWithType>
- <xref:System.Threading.Mutex.%23ctor%2A>
- <xref:System.Security.AccessControl.MutexSecurity?displayProperty=nameWithType>
- <xref:System.Security.AccessControl.MutexAccessRule?displayProperty=nameWithType>
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- [Wątkowość obiektów i funkcji](threading-objects-and-features.md)
- [Gwinty i gwintowanie](threads-and-threading.md)
- [Wątkowość](index.md)
