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
ms.openlocfilehash: 80379e46c6482a3e052c1283fb4aaba2c7df282e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45638555"
---
# <a name="mutexes"></a>Muteksy
Możesz użyć <xref:System.Threading.Mutex> obiekt, aby zapewnić wyłącznego dostępu do zasobu. <xref:System.Threading.Mutex> Klasy wykorzystuje więcej zasobów systemowych niż <xref:System.Threading.Monitor> klasy, ale mogą być organizowane poza granice domeny aplikacji, można za pomocą wielu czeka i może służyć do synchronizacji wątków w różnych procesach. Dla porównania mechanizmów synchronizacji zarządzanych, zobacz [Przegląd podstawowych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Przykłady kodu, zobacz dokumentację referencyjną <xref:System.Threading.Mutex.%23ctor%2A> konstruktorów.  
  
## <a name="using-mutexes"></a>Za pomocą muteksy  
 Wątek wywołuje <xref:System.Threading.WaitHandle.WaitOne%2A> metoda mutex na własność żądania. Blokuje wywołania do czasu udostępnienia element mutex lub do momentu opcjonalny limit czasu upłynie. Stan obiektu mutex jest sygnalizowane, jeśli żaden wątek nie jest jego właścicielem.  
  
 Wątek zwalnia mutex przez wywołanie jego <xref:System.Threading.Mutex.ReleaseMutex%2A> metody. Muteksy pozostają w koligacji wątku; oznacza to, że element mutex będą dostępne tylko przez wątek, który jest jego właścicielem. Jeśli wątek zwalnia mutex, nie jest właścicielem, <xref:System.ApplicationException> jest zgłaszany w wątku.  
  
 Ponieważ <xref:System.Threading.Mutex> klasa pochodzi od <xref:System.Threading.WaitHandle>, można również wywołać statyczną <xref:System.Threading.WaitHandle.WaitAll%2A> lub <xref:System.Threading.WaitHandle.WaitAny%2A> metody <xref:System.Threading.WaitHandle> na własność żądania <xref:System.Threading.Mutex> w połączeniu z innymi uchwyty oczekiwania.  
  
 Jeśli wątek jest właścicielem <xref:System.Threading.Mutex>, wątek może określić te same <xref:System.Threading.Mutex> w wywołaniach powtórne żądanie oczekiwania bez blokowania jej wykonanie; jednak go trzeba zwolnić <xref:System.Threading.Mutex> tyle razy, aby zwolnić własności.  
  
## <a name="abandoned-mutexes"></a>Porzucone muteksy  
 Jeśli wątek kończy działanie bez zwalniania <xref:System.Threading.Mutex>, element mutex, jest nazywany go porzucić. To często oznacza to poważny błąd programowania, ponieważ zasób, który chroni element mutex może pozostać w stanie niespójnym. W .NET Framework w wersji 2.0 <xref:System.Threading.AbandonedMutexException> jest zgłaszany w następny wątek, który uzyska element mutex.  
  
> [!NOTE]
>  W wersjach programu .NET Framework 1.0 i 1.1 opuszczoną <xref:System.Threading.Mutex> zestawu do sygnalizowanego stanu, a następnie czeka, aż wątek pobiera własności. Jeśli żaden wątek nie oczekuje się, <xref:System.Threading.Mutex> pozostaje w sygnalizowanego stanu. Jest zgłaszany żaden wyjątek.  
  
 W przypadku elementu mutex systemowe porzuconego elementu mutex może wskazywać, że aplikacji zostało zakończone nagle (na przykład przy użyciu Menedżera zadań Windows).  
  
## <a name="local-and-system-mutexes"></a>Lokalne i muteksy systemu  
 Istnieją dwa typy muteksy: lokalne muteksy i muteksy systemu o nazwie. Jeśli tworzysz <xref:System.Threading.Mutex> przy użyciu konstruktora, który przyjmuje nazwę, jest skojarzony z obiektem systemu operacyjnego o takiej nazwie. O nazwie system Muteksy są widoczne w całym systemie operacyjnym i może służyć do synchronizowania działania procesów. Możesz tworzyć wiele <xref:System.Threading.Mutex> obiekty reprezentujące takie same, o nazwie systemu element mutex i można użyć <xref:System.Threading.Mutex.OpenExisting%2A> metodę, aby otworzyć istniejący o nazwie systemu element mutex.  
  
 Lokalny element mutex istnieje tylko w ramach procesu. Mogą być używane w żadnym z wątków w procesie, który odwołuje się do lokalnej <xref:System.Threading.Mutex> obiektu. Każdy <xref:System.Threading.Mutex> obiekt jest oddzielny lokalny element mutex.  
  
### <a name="access-control-security-for-system-mutexes"></a>Kontrolę dostępu dla muteksy systemu  
 .NET Framework w wersji 2.0 zapewnia możliwość tworzenia zapytań i ustawiania Windows kontrolę dostępu do obiektów o nazwie systemu. Ochrona systemu muteksy od momentu utworzenia jest zalecane, ponieważ obiekty systemowe są globalne i może być zablokowany przez kod inny niż swoje własne.  
  
 Aby uzyskać informacji na temat kontrolę dostępu dla muteksy, zobacz <xref:System.Security.AccessControl.MutexSecurity> i <xref:System.Security.AccessControl.MutexAccessRule> klas, <xref:System.Security.AccessControl.MutexRights> wyliczenia, <xref:System.Threading.Mutex.GetAccessControl%2A>, <xref:System.Threading.Mutex.SetAccessControl%2A>, i <xref:System.Threading.Mutex.OpenExisting%2A> metody <xref:System.Threading.Mutex> klasy i <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29> konstruktora.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Mutex>  
- <xref:System.Threading.Mutex.%23ctor%2A>  
- <xref:System.Security.AccessControl.MutexSecurity>  
- <xref:System.Security.AccessControl.MutexAccessRule>  
- [Wątkowość](../../../docs/standard/threading/index.md)  
- [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)  
- [Monitory](https://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
- [Wątki i wątkowość](../../../docs/standard/threading/threads-and-threading.md)
