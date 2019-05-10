---
title: 'Pamięć lokalna wątku: Powiązane z wątkiem pola statyczne i gniazda danych'
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
ms.openlocfilehash: 681a9e71dcfb139c364d750383f13cdabbf33366
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64644890"
---
# <a name="thread-local-storage-thread-relative-static-fields-and-data-slots"></a>Pamięć lokalna wątku: Powiązane z wątkiem pola statyczne i gniazda danych
Można użyć lokalnego magazynu zarządzanych wątków (TLS) do przechowywania danych, która jest unikatowa w domenie aplikacji i wątku. Program .NET Framework oferuje dwa sposoby użycia zarządzanego protokołu TLS: względne wątkom statycznego miejsca pól i danych.  
  
- Użyj względne wątkom pola statyczne (względne wątkom `Shared` pól w języku Visual Basic) jeżeli można przewidzieć potrzeby użytkowników w czasie kompilacji. Względne wątkom pola statyczne zapewniają najlepszą wydajność. Również zapewniają korzyści wynikające z kontrola typów w czasie kompilacji.  
  
- Użyj miejsc danych, gdy Twoje rzeczywiste wymagania mogą zostać odnalezione tylko w czasie wykonywania. Gniazda danych są wolniejszy i bardziej niewygodna w użyciu niż względne wątkom pola statyczne, a dane są przechowywane jako typ <xref:System.Object>, więc należy rzutować go do poprawnego typu przed jego użyciem.  
  
 W języku C++ niezarządzane, użyj `TlsAlloc` można dynamicznie przydzielić miejsca i `__declspec(thread)` Aby zadeklarować, że zmienna powinna zostać przydzielona w magazynie względne wątkom. Względne wątkom statyczne pola i dane umożliwiają zarządzanej wersji to zachowanie.  
  
 W [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], możesz użyć <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> klasy w celu utworzenia obiektów wątków lokalnych, które są inicjowane opóźnieniem, gdy obiekt jest najpierw zużywane. Aby uzyskać więcej informacji, zobacz [inicjowania z opóźnieniem](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="uniqueness-of-data-in-managed-tls"></a>Unikatowość danych w zarządzany protokół TLS  
 Czy używasz względne wątkom pola statyczne i gniazda danych w zarządzany protokół TLS jest unikatowa kombinacja domeny aplikacji i wątku.  
  
- W domenie aplikacji jeden wątek nie można zmodyfikować danych z innego wątku, nawet w przypadku obu wątków za pomocą tego samego pola lub gniazda.  
  
- Gdy wątek uzyskuje dostęp do tego samego pola lub gniazda z wielu domen aplikacji, oddzielne wartość jest zachowywana w każdej domenie aplikacji.  
  
 Na przykład jeśli wątek ustawia wartości względne wątkom pola statyczne, przechodzi w innej domenie aplikacji, a następnie pobiera wartość pola, pobraną w drugiej domenie aplikacji różni się od wartości w pierwszej domeny aplikacji. Ustawianie nową wartość dla pola w drugiej domenie aplikacji nie wpływa na wartość pola w pierwszej domeny aplikacji.  
  
 Podobnie gdy wątek otrzyma zajmować tego samego miejsca danych o podanej nazwie w dwóch różnych domenach aplikacji, dane w domenie aplikacji, pierwsze pozostaje niezależnie od danych w drugiej domenie aplikacji.  
  
## <a name="thread-relative-static-fields"></a>Względne wątkom pola statyczne  
 Jeśli znasz element danych jest zawsze unikatowa kombinacja domeny aplikacji i wątku, należy zastosować <xref:System.ThreadStaticAttribute> atrybutu do pola statycznego. Użyj pola, jak w przypadku każdego innego pola statyczne. Dane w polu są unikatowe dla każdego wątku, która go używa.  
  
 Względne wątkom pola statyczne zapewnić lepszą wydajność niż gniazda danych i korzystać z kontrola typów w czasie kompilacji.  
  
 Należy pamiętać, że każdy kod konstruktora klasy będzie działać w pierwszym wątkiem w pierwszym kontekstu, który uzyskuje dostęp do pola. We wszystkich innych wątków i konteksty w tej samej domenie aplikacji, zostanie zainicjowana pola w celu `null` (`Nothing` w języku Visual Basic) są typami odwołań, czy do ich domyślnych wartości, jeśli są typami wartości. W związku z tym nie należy polegać na Konstruktory klasy, zainicjować względne wątkom pola statyczne. Zamiast tego należy unikać inicjowanie względne wątkom pola statyczne i przyjęto założenie, że są inicjowane na wartość `null` (`Nothing`) lub do wartości domyślnych.  
  
## <a name="data-slots"></a>Gniazda danych  
 .NET Framework zapewnia miejsc danych dynamicznych, które są unikatowe dla wątku i domeny aplikacji. Istnieją dwa typy danych miejsc: o nazwie gniazda i nienazwane gniazda. Oba są implementowane przy użyciu <xref:System.LocalDataStoreSlot> struktury.  
  
- Aby utworzyć miejsce danych o podanej nazwie, użyj <xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=nameWithType> lub <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType> metody. Aby uzyskać odwołanie do istniejącego o nazwie miejsca, przekazać jego nazwę na <xref:System.Threading.Thread.GetNamedDataSlot%2A> metody.  
  
- Aby utworzyć miejsce nienazwane danych, użyj <xref:System.Threading.Thread.AllocateDataSlot%2A?displayProperty=nameWithType> metody.  
  
 Zarówno nazwę i nienazwane miejsc, użyj <xref:System.Threading.Thread.SetData%2A?displayProperty=nameWithType> i <xref:System.Threading.Thread.GetData%2A?displayProperty=nameWithType> metody do ustawiania i pobierania informacji w miejscu. Są to metody statyczne, które zawsze działają w danych dla wątku, który aktualnie wykonuje je.  
  
 Gniazda o nazwie może być wygodne, ponieważ można pobrać gniazda, gdy będą potrzebne przez przekazanie jego nazwę na <xref:System.Threading.Thread.GetNamedDataSlot%2A> metody, zamiast zajmować się utrzymywaniem odwołanie do gniazda bez nazwy. Jednakże jeśli inny składnik używa tej samej nazwie do jej przechowywania względne wątkom wątek wykonuje kod zarówno składnik, jak i innych składników, dwa składniki może spowodować uszkodzenie danych siebie nawzajem. (W tym scenariuszu przyjęto założenie, że oba te składniki działają w tej samej domenie aplikacji, a nie są przeznaczone do udostępnienia tych samych danych.)  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ContextStaticAttribute>
- <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>
- <xref:System.ThreadStaticAttribute>
- <xref:System.Runtime.Remoting.Messaging.CallContext>
- [Wątkowość](../../../docs/standard/threading/index.md)
