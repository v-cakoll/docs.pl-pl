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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127520"
---
# <a name="thread-local-storage-thread-relative-static-fields-and-data-slots"></a>Pamięć lokalna wątku: powiązane z wątkiem pola statyczne i gniazda danych
Za pomocą lokalnego magazynu wątku zarządzanego (TLS) można przechowywać dane unikatowe dla domeny wątków i aplikacji. Program .NET Framework udostępnia dwa sposoby używania zarządzanego protokołu TLS: pola statyczne względne wątku i gniazda danych.  
  
- Użyj względnych pól statycznych `Shared` względnych wątku (pól względnych wątku w języku Visual Basic), jeśli można przewidzieć dokładne potrzeby w czasie kompilacji. Pola statyczne względne wątku zapewniają najlepszą wydajność. Dają one również korzyści z sprawdzania typu kompilacji w czasie.  
  
- Użyj gniazd danych, gdy rzeczywiste wymagania mogą być wykrywane tylko w czasie wykonywania. Gniazda danych są wolniejsze i bardziej niewygodne w użyciu niż względne <xref:System.Object>pola statyczne dotyczące wątków, a dane są przechowywane jako typ, więc przed użyciem należy oddać je do poprawnego typu.  
  
 W niezarządzanych C++, można przydzielić `TlsAlloc` `__declspec(thread)` szczeliny dynamicznie i zadeklarować, że zmienna powinna być przydzielona w magazynie względnym wątku. Względne wątki pola statyczne i gniazda danych zapewniają zarządzaną wersję tego zachowania.  
  
 W .NET Framework 4 można <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> użyć klasy do tworzenia obiektów lokalnych wątku, które są inicjowane leniwie, gdy obiekt jest po raz pierwszy zużyty. Aby uzyskać więcej informacji, zobacz [Inicjowanie z opóźnieniem](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="uniqueness-of-data-in-managed-tls"></a>Unikatowość danych w zarządzanym tls  
 Niezależnie od tego, czy używasz pól statycznych względnych wątków, czy gniazd danych, dane w zarządzanym tls są unikatowe dla kombinacji domeny wątków i aplikacji.  
  
- W domenie aplikacji jeden wątek nie może modyfikować danych z innego wątku, nawet jeśli oba wątki używają tego samego pola lub gniazda.  
  
- Gdy wątek uzyskuje dostęp do tego samego pola lub gniazda z wielu domen aplikacji, oddzielna wartość jest zachowywana w każdej domenie aplikacji.  
  
 Na przykład jeśli wątek ustawia wartość pola statycznego względnego przez wątek, wprowadza inną domenę aplikacji, a następnie pobiera wartość pola, wartość pobrana w drugiej domenie aplikacji różni się od wartości w pierwszej domenie aplikacji. Ustawienie nowej wartości pola w drugiej domenie aplikacji nie wpływa na wartość pola w pierwszej domenie aplikacji.  
  
 Podobnie gdy wątek pobiera ten sam nazwany gniazdo danych w dwóch różnych domenaplikacji, dane w pierwszej domenie aplikacji pozostaje niezależna od danych w drugiej domenie aplikacji.  
  
## <a name="thread-relative-static-fields"></a>Względne pola statyczne względne wątku  
 Jeśli wiadomo, że fragment danych jest zawsze unikatowy dla <xref:System.ThreadStaticAttribute> kombinacji wątku i aplikacji domeny, zastosuj atrybut do pola statycznego. Użyj tego pola tak, jak w przypadku innych pól statycznych. Dane w polu jest unikatowa dla każdego wątku, który go używa.  
  
 Pola statyczne względne wątku zapewniają lepszą wydajność niż gniazda danych i mają zaletę sprawdzania typu w czasie kompilacji.  
  
 Należy pamiętać, że kod konstruktora klasy będzie uruchamiany w pierwszym wątku w pierwszym kontekście, który uzyskuje dostęp do pola. We wszystkich innych wątków lub kontekstów w tej samej domenie aplikacji pola zostaną zainicjowane do `null` (`Nothing` w języku Visual Basic), jeśli są one typy odwołań lub ich wartości domyślne, jeśli są one typy wartości. W związku z tym nie należy polegać na konstruktory klas do inicjowania pól statycznych względnych wątku. Zamiast tego należy unikać inicjowania pól statycznych względnych wątku i załóżmy, że są one inicjowane do `null` (`Nothing`) lub do ich wartości domyślnych.  
  
## <a name="data-slots"></a>Gniazda danych  
 Program .NET Framework udostępnia dynamiczne gniazda danych, które są unikatowe dla kombinacji wątków i domeny aplikacji. Istnieją dwa typy gniazd danych: nazwane gniazda i nienazwane gniazda. Oba są implementowane <xref:System.LocalDataStoreSlot> przy użyciu struktury.  
  
- Aby utworzyć nazwane gniazdo danych, <xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType> należy użyć tej lub metody. Aby uzyskać odwołanie do istniejącego gniazda o nazwie, przekaż jego nazwę <xref:System.Threading.Thread.GetNamedDataSlot%2A> do metody.  
  
- Aby utworzyć nienazwane gniazdo danych, <xref:System.Threading.Thread.AllocateDataSlot%2A?displayProperty=nameWithType> użyj tej metody.  
  
 W przypadku gniazd o nazwie i <xref:System.Threading.Thread.SetData%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.GetData%2A?displayProperty=nameWithType> bez nazwy należy użyć i metody, aby ustawić i pobrać informacje w gnieciu. Są to metody statyczne, które zawsze działają na dane dla wątku, który jest aktualnie ich wykonywania.  
  
 Nazwane gniazda mogą być wygodne, ponieważ można pobrać gniazdo, gdy jest <xref:System.Threading.Thread.GetNamedDataSlot%2A> to potrzebne, przekazując jego nazwę do metody, zamiast utrzymywać odwołanie do nienazwanego gniazda. Jeśli jednak inny składnik używa tej samej nazwy dla magazynu względnego wątku, a wątek wykonuje kod zarówno ze składnika, jak i z innego składnika, dwa składniki mogą uszkodzić nawzajem dane. (W tym scenariuszu przyjęto założenie, że oba składniki są uruchomione w tej samej domenie aplikacji i że nie są przeznaczone do udostępniania tych samych danych.)  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ContextStaticAttribute>
- <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>
- <xref:System.ThreadStaticAttribute>
- <xref:System.Runtime.Remoting.Messaging.CallContext>
- [Wątków](../../../docs/standard/threading/index.md)
