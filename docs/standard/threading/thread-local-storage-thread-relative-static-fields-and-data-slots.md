---
title: 'Pamięć lokalna wątku: powiązane z wątkiem pola statyczne i gniazda danych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], local storage
- threading [.NET Framework], thread-relative static fields
- local thread storage
- TLS
ms.assetid: c633a4dc-a790-4ed1-96b5-f72bd968b284
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a17bc509c8c82bfb30811ec3511207ca2d823e5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="thread-local-storage-thread-relative-static-fields-and-data-slots"></a>Pamięć lokalna wątku: powiązane z wątkiem pola statyczne i gniazda danych
Można użyć zarządzanej lokalny magazyn wątków (TLS) do przechowywania danych, która jest unikatowa w domenie wątku i aplikacji. .NET Framework udostępnia dwa sposoby używania zarządzanych TLS: statyczne miejsc pola i dane powiązane z wątkiem.  
  
-   Użyj powiązane z wątkiem pola statyczne (powiązane z wątkiem `Shared` pola w języku Visual Basic), jeśli przewidujesz potrzeby użytkowników w czasie kompilacji. Względne wątkom pola statyczne zapewniają najlepszą wydajność. One również zapewniają korzyści sprawdzania typu kompilacji.  
  
-   Użyj miejsc danych po rzeczywiste wymagania mogą być tylko w czasie wykonywania. Gniazda danych są wolniejszy i bardziej nieodpowiednich w użyciu niż powiązane z wątkiem pola statyczne i dane są przechowywane jako typ <xref:System.Object>, więc należy rzutować go do poprawnego typu przed jego użyciem.  
  
 W języku C++ niezarządzane, użyj `TlsAlloc` może dynamicznie przydzielać miejsc i `__declspec(thread)` Aby zadeklarować, że zmienna powinna zostać przydzielona w magazynie powiązane z wątkiem. Względne wątkom statycznego pola i danych umożliwiają zarządzanej wersji tego zachowania.  
  
 W [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], można użyć <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> klasy w celu utworzenia obiektów wątków lokalnych, które są inicjowane opóźnieniem, gdy obiekt jest najpierw używane. Aby uzyskać więcej informacji, zobacz [Incjalizacji](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="uniqueness-of-data-in-managed-tls"></a>Unikatowość danych w protokole TLS zarządzanych  
 Czy można używać powiązane z wątkiem pola statyczne i gniazda danych, danych w protokole TLS zarządzanych jest unikatowy dla kombinacji domeny wątku i aplikacji.  
  
-   W domenie aplikacji jeden wątek nie może modyfikować danych z innego wątku, nawet wtedy, gdy oba wątki używają tego samego pola lub gniazda.  
  
-   Gdy wątek uzyskuje dostęp do tego samego pola lub miejscem z wielu domen aplikacji, oddzielne wartość jest zachowywana w każdej domenie aplikacji.  
  
 Na przykład jeśli wątek ustawia wartość powiązane z wątkiem pola statyczne, przechodzi do innej domeny aplikacji, a następnie pobiera wartość pola, pobraną w drugiej domenie aplikacji różni się od wartości w pierwszej domeny aplikacji. Ustawienie nową wartość dla pola w drugiej domenie aplikacji nie ma wpływu na wartości pola w pierwszej domeny aplikacji.  
  
 Podobnie gdy wątek pobiera tego samego miejsca danych o podanej nazwie w dwóch różnych domenach aplikacji, dane w pierwszej domeny aplikacji pozostaje niezależnie od danych w drugiej domenie aplikacji.  
  
## <a name="thread-relative-static-fields"></a>Względne wątkom pola statyczne  
 Jeśli znasz element danych jest zawsze unikatowa dla wątku i kombinacja domena aplikacji, zastosuj <xref:System.ThreadStaticAttribute> atrybutu pola statycznego. Użyj pola, jak w przypadku innych pola statycznego. Dane w polu jest unikatowy dla każdego wątku, który korzysta z niego.  
  
 Względne wątkom pola statyczne zapewnić lepszą wydajność niż gniazda danych i korzystać z sprawdzanie typów w czasie kompilacji.  
  
 Należy pamiętać, że każdy kod konstruktora klasy będzie uruchamiany na pierwszym wątkiem w kontekście pierwszy, który uzyskuje dostęp do pola. We wszystkich innych wątków i konteksty w tej samej domenie aplikacji, zostanie zainicjowana pola w celu `null` (`Nothing` w języku Visual Basic) są typy odwołań, czy do ich domyślnych wartości, jeśli są one typów wartości. W związku z tym nie należy polegać na konstruktorów klas zainicjować powiązane z wątkiem pola statyczne. Zamiast tego uniknąć, inicjowanie powiązane z wątkiem pola statyczne i założono, że są one inicjowane `null` (`Nothing`) lub do wartości domyślnych.  
  
## <a name="data-slots"></a>Gniazda danych  
 .NET Framework zapewnia miejsc danych dynamicznych, które są unikatowe dla kombinacji wątku i domeny aplikacji. Istnieją dwa typy danych gniazd: o nazwie gniazda i gniazda bez nazwy. Zarówno są implementowane za pomocą <xref:System.LocalDataStoreSlot> struktury.  
  
-   Aby utworzyć miejsca danych o podanej nazwie, użyj <xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=nameWithType> lub <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType> metody. Aby odwołać się do istniejącego o nazwie miejsca, podać jego nazwę, aby <xref:System.Threading.Thread.GetNamedDataSlot%2A> metody.  
  
-   Aby utworzyć gniazda nienazwane danych, użyj <xref:System.Threading.Thread.AllocateDataSlot%2A?displayProperty=nameWithType> metody.  
  
 Zarówno nazwanych i nienazwanych gniazda, użyj <xref:System.Threading.Thread.SetData%2A?displayProperty=nameWithType> i <xref:System.Threading.Thread.GetData%2A?displayProperty=nameWithType> metody do ustawiania i pobierania informacji w miejscu. Są to metody statyczne, które zawsze działają w wątku, który jest aktualnie wykonywany ich danych.  
  
 Nazwane miejsc może być wygodne, ponieważ można pobrać gniazda, gdy będziesz potrzebować przez przekazanie jej nazwę, aby <xref:System.Threading.Thread.GetNamedDataSlot%2A> metody, zamiast utrzymywanie odwołania do gniazda bez nazwy. Jednak jeśli inny składnik używa tej samej nazwy dla jego magazynu powiązane z wątkiem wątek wykonuje kod z składnika i innych składników, dwa składniki może spowodować uszkodzenie danych siebie nawzajem. (W tym scenariuszu założono, że oba te składniki są uruchomione w tej samej domenie aplikacji, a nie są zaprojektowane do udostępniania tych samych danych.)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ContextStaticAttribute>  
 <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>  
 <xref:System.ThreadStaticAttribute>  
 <xref:System.Runtime.Remoting.Messaging.CallContext>  
 [Wątkowość](../../../docs/standard/threading/index.md)
