---
title: Muteksy
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wait handles
- threading [.NET Framework], Mutex class
- Mutex class, about Mutex class
- threading [.NET Framework], cross-process synchronization
ms.assetid: 9dd06e25-12c0-4a9e-855a-452dc83803e2
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2804d0c60657623b558d86386c5e1043422b648c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="mutexes"></a>Muteksy
Można użyć <xref:System.Threading.Mutex> obiektu zapewnienie wyłącznego dostępu do zasobu. <xref:System.Threading.Mutex> Klasy wykorzystuje więcej zasobów systemowych niż <xref:System.Threading.Monitor> klasy, ale mogą być przekazywane między granicami domeny aplikacji, można z wielu czeka i może służyć do synchronizowania wątków w różnych procesów. Porównanie mechanizmów synchronizacji zarządzanych, zobacz [podstawowych Omówienie synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md).  
  
 Przykłady kodu, w dokumentacji odwołania dla <xref:System.Threading.Mutex.%23ctor%2A> konstruktorów.  
  
## <a name="using-mutexes"></a>Przy użyciu muteksy  
 Wywołuje wątku <xref:System.Threading.WaitHandle.WaitOne%2A> metody obiektu mutex własności żądania. Bloki wywołania obiektu mutex jest dostępny, lub do momentu opcjonalne limit czasu upłynie. Stan obiektu mutex jest sygnalizowane, jeśli wątek nie jest jego właścicielem.  
  
 Wątek zwalnia obiektu mutex przez wywołanie jego <xref:System.Threading.Mutex.ReleaseMutex%2A> metody. Muteksy mają koligacji wątku; oznacza to będą dostępne tylko w wątku, który jest jego właścicielem obiektu mutex. Jeśli wątek zwalnia obiektu mutex nie jest właścicielem, <xref:System.ApplicationException> jest zgłaszany w wątku.  
  
 Ponieważ <xref:System.Threading.Mutex> pochodną klasy <xref:System.Threading.WaitHandle>, możesz także wywołać statycznych <xref:System.Threading.WaitHandle.WaitAll%2A> lub <xref:System.Threading.WaitHandle.WaitAny%2A> metody <xref:System.Threading.WaitHandle> własności żądania <xref:System.Threading.Mutex> w połączeniu z innymi uchwyty oczekiwania.  
  
 Jeśli właścicielem wątku <xref:System.Threading.Mutex>, Wątek można określić ten sam <xref:System.Threading.Mutex> w wywołaniach powtórne żądanie oczekiwania bez blokowania jej wykonanie; jednak go trzeba zwolnić <xref:System.Threading.Mutex> tyle razy, aby zwolnić własności.  
  
## <a name="abandoned-mutexes"></a>Porzucone muteksy  
 Jeśli wątek zakończy się bez zwolnienia <xref:System.Threading.Mutex>, obiektu mutex jest określany za porzucone. Często oznacza to poważny błąd programistyczny, ponieważ zasób, który chroni obiektu mutex może pozostać w niespójnym stanie. W programie .NET Framework w wersji 2.0 <xref:System.Threading.AbandonedMutexException> jest zgłaszany w następnym wątku, który uzyskuje obiektu mutex.  
  
> [!NOTE]
>  W wersji systemu .NET Framework 1.0 i 1.1, porzuconego <xref:System.Threading.Mutex> ustawioną sygnałowego stan i następne oczekuje własność pobiera wątku. Jeśli nie wątek oczekuje, <xref:System.Threading.Mutex> pozostaje w stanie sygnałowego. Nie wyjątek.  
  
 W przypadku obiektu mutex systemowe porzuconego elementu mutex może wskazywać, że aplikacji zostało zakończone nagle (na przykład za pomocą Menedżera zadań systemu Windows).  
  
## <a name="local-and-system-mutexes"></a>Lokalne i muteksy systemu  
 Istnieją dwa typy muteksy: muteksy lokalnych i muteksy systemu o nazwie. W przypadku utworzenia <xref:System.Threading.Mutex> przy użyciu konstruktora akceptującego nazwy, jest on skojarzony z obiektem systemu operacyjnego o tej nazwie. O nazwie system Muteksy są widoczne w systemie operacyjnym i może służyć do synchronizowania działania procesów. Możesz utworzyć wiele <xref:System.Threading.Mutex> obiektów, które reprezentują takie same nazwanego obiektu mutex systemu i może używać <xref:System.Threading.Mutex.OpenExisting%2A> metodę, aby otworzyć istniejące nazwanego obiektu mutex systemu.  
  
 Mutex lokalny istnieje tylko w ramach procesu. Może służyć za którymkolwiek wątku w procesie, który zawiera odwołanie do lokalnej <xref:System.Threading.Mutex> obiektu. Każdy <xref:System.Threading.Mutex> obiekt jest oddzielny lokalny obiektu mutex.  
  
### <a name="access-control-security-for-system-mutexes"></a>Kontrolę dostępu dla muteksy systemu  
 .NET Framework w wersji 2.0 zapewnia możliwość wykonywania zapytań i ustawić Windows kontrolę dostępu do obiektów o nazwie systemu. Ochrona w czasie tworzenia muteksy systemu jest zalecane, ponieważ obiektów systemowych są globalne i w związku z tym może być zablokowane przez kodu innego niż własny.  
  
 Aby uzyskać informacje na kontrolę dostępu dla muteksy, zobacz <xref:System.Security.AccessControl.MutexSecurity> i <xref:System.Security.AccessControl.MutexAccessRule> klas, <xref:System.Security.AccessControl.MutexRights> wyliczenia, <xref:System.Threading.Mutex.GetAccessControl%2A>, <xref:System.Threading.Mutex.SetAccessControl%2A>, i <xref:System.Threading.Mutex.OpenExisting%2A> metody <xref:System.Threading.Mutex> klasy i <xref:System.Threading.Mutex.%23ctor%28System.Boolean%2CSystem.String%2CSystem.Boolean%40%2CSystem.Security.AccessControl.MutexSecurity%29> konstruktora.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.Mutex.%23ctor%2A>  
 <xref:System.Security.AccessControl.MutexSecurity>  
 <xref:System.Security.AccessControl.MutexAccessRule>  
 [Wątkowość](../../../docs/standard/threading/index.md)  
 [Wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Monitory](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 [Wątki i wątkowość](../../../docs/standard/threading/threads-and-threading.md)
