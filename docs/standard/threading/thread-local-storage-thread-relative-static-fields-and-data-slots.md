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
ms.openlocfilehash: b5a7c4b78f8599f64aa11f1c98c033866e582933
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127520"
---
# <a name="thread-local-storage-thread-relative-static-fields-and-data-slots"></a>Pamięć lokalna wątku: powiązane z wątkiem pola statyczne i gniazda danych
Za pomocą lokalnego magazynu wątków (TLS) można przechowywać dane, które są unikatowe dla wątku i domeny aplikacji. .NET Framework zapewnia dwa sposoby użycia zarządzanej TLS: pól statycznych względnych dla wątków i miejsc danych.  
  
- Używaj pól statycznych względnych dla wątków (`Shared` względnych dla wątków w Visual Basic), jeśli możesz przewidzieć dokładne potrzeby w czasie kompilacji. Pola statyczne względne dla wątków zapewniają najlepszą wydajność. Zapewniają również korzyści wynikające z sprawdzania typu w czasie kompilacji.  
  
- Używaj miejsc danych, gdy rzeczywiste wymagania mogą być wykrywane tylko w czasie wykonywania. Gniazda danych są wolniejsze i więcej niewygodna niż pola statyczne powiązane z wątkiem, a dane są przechowywane jako typ <xref:System.Object>, dlatego należy rzutować je na prawidłowy typ przed użyciem go.  
  
 W niezarządzanych C++`TlsAlloc` do przydzielania miejsc dynamicznie i `__declspec(thread)` do deklarowania, że zmienna powinna zostać przydzielona w magazynie względnym wątków. Pola statyczne powiązane z wątkiem i gniazda danych zapewniają zarządzaną wersję tego zachowania.  
  
 W .NET Framework 4 można użyć klasy <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> do tworzenia obiektów lokalnych wątków, które są inicjowane opóźnieniem, gdy obiekt jest po raz pierwszy zużyty. Aby uzyskać więcej informacji, zobacz [Inicjalizacja z opóźnieniem](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="uniqueness-of-data-in-managed-tls"></a>Unikatowość danych w zarządzanym protokole TLS  
 Niezależnie od tego, czy używasz pól statycznych względnych dla wątków czy miejsc danych, dane w zarządzanej protokole TLS są unikatowe dla połączenia wątku i domeny aplikacji.  
  
- W ramach domeny aplikacji jeden wątek nie może modyfikować danych z innego wątku, nawet jeśli oba wątki używają tego samego pola lub gniazda.  
  
- Gdy wątek uzyskuje dostęp do tego samego pola lub gniazda z wielu domen aplikacji, w każdej domenie aplikacji jest utrzymywana oddzielna wartość.  
  
 Na przykład jeśli wątek ustawi wartość pola statycznego względem wątku, wprowadza inną domenę aplikacji, a następnie pobiera wartość pola, wartość pobrana w drugiej domenie aplikacji różni się od wartości w pierwszej domenie aplikacji. Ustawienie nowej wartości dla pola w drugiej domenie aplikacji nie wpływa na wartość pola w pierwszej domenie aplikacji.  
  
 Podobnie, gdy wątek pobiera takie samo nazwane miejsce danych w dwóch różnych domenach aplikacji, dane w pierwszej domenie aplikacji pozostają niezależne od danych w drugiej domenie aplikacji.  
  
## <a name="thread-relative-static-fields"></a>Pola statyczne względne dla wątków  
 Jeśli wiesz, że element danych jest zawsze unikatowy dla połączenia wątku i aplikacji, zastosuj atrybut <xref:System.ThreadStaticAttribute> do pola statycznego. Użyj pola jako użycia dowolnego innego pola statycznego. Dane w polu są unikatowe dla każdego wątku, który go używa.  
  
 Pola statyczne względne dla wątków zapewniają lepszą wydajność niż miejsca na danych i korzystają z sprawdzania typu w czasie kompilacji.  
  
 Należy pamiętać, że każdy kod konstruktora klasy zostanie uruchomiony na pierwszym wątku w pierwszym kontekście, który uzyskuje dostęp do pola. We wszystkich innych wątkach lub kontekstach w tej samej domenie aplikacji pola zostaną zainicjowane do `null` (`Nothing` w Visual Basic), jeśli są to typy odwołań, lub do ich wartości domyślnych, jeśli są to typy wartości. W związku z tym nie należy polegać na konstruktorach klas w celu zainicjowania pól statycznych względnych dla wątków. Zamiast tego należy unikać inicjowania pól statycznych względnych dla wątków i założenie, że są one inicjowane do `null` (`Nothing`) lub do ich wartości domyślnych.  
  
## <a name="data-slots"></a>Gniazda danych  
 .NET Framework zapewnia dynamiczne gniazda danych, które są unikatowe dla kombinacji wątków i domen aplikacji. Istnieją dwa typy miejsc danych: nazwane gniazda i nienazwane gniazda. Oba są implementowane przy użyciu struktury <xref:System.LocalDataStoreSlot>.  
  
- Aby utworzyć nazwane gniazdo danych, użyj metody <xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=nameWithType> lub <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>. Aby uzyskać odwołanie do istniejącego, nazwane gniazdo, Przekaż jego nazwę do metody <xref:System.Threading.Thread.GetNamedDataSlot%2A>.  
  
- Aby utworzyć nienazwane gniazdo danych, użyj metody <xref:System.Threading.Thread.AllocateDataSlot%2A?displayProperty=nameWithType>.  
  
 Dla gniazd nazwanych i nienazwanych Użyj metod <xref:System.Threading.Thread.SetData%2A?displayProperty=nameWithType> i <xref:System.Threading.Thread.GetData%2A?displayProperty=nameWithType>, aby ustawić i pobrać informacje w gnieździe. Są to metody statyczne, które zawsze działają na danych wątku, który jest aktualnie wykonywany.  
  
 Nazwane gniazda mogą być wygodne, ponieważ można pobrać miejsce, gdy jest ono potrzebne, przekazując jego nazwę do metody <xref:System.Threading.Thread.GetNamedDataSlot%2A>, zamiast utrzymywać odwołanie do nienazwanego gniazda. Jeśli jednak inny składnik używa tej samej nazwy do przechowywania względem wątku, a wątek wykonuje kod zarówno ze składnika, jak i drugiego składnika, te dwa składniki mogą uszkodzić dane. (W tym scenariuszu przyjęto założenie, że oba składniki są uruchomione w tej samej domenie aplikacji i nie są przeznaczone do udostępniania tych samych danych).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ContextStaticAttribute>
- <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>
- <xref:System.ThreadStaticAttribute>
- <xref:System.Runtime.Remoting.Messaging.CallContext>
- [Wątkowość](../../../docs/standard/threading/index.md)
