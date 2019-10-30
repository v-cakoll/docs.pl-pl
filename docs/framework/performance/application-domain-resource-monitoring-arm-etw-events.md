---
title: Zdarzenia ETW monitorowania zasobów domen aplikacji (ARM)
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6e1c2a38be6f2c15a118b35925570119b474f096
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040564"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a>Zdarzenia ETW monitorowania zasobów domen aplikacji (ARM)

Te zdarzenia zapewniają szczegółowe informacje diagnostyczne o stanie domeny aplikacji. Możesz użyć tych zdarzeń lub użyć funkcji monitorowania zasobów domeny aplikacji (ARM), aby uzyskać te same informacje.

## <a name="threadcreated-event"></a>Zdarzenie ThreadCreated —

To zdarzenie jest również zgłaszane w ramach dostawcy uwalniania jako `ThreadDC` (w obszarze słowa kluczowego `AppDomainResourceManagementRundownKeyword`). Jest to jedyne zdarzenie zgłaszane w ramach dostawcy uwalniania w tej kategorii.

W poniższej tabeli przedstawiono słowo kluczowe i poziom. Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md).

|Słowo kluczowe do podniesienia zdarzenia|Poziom|
|-----------------------------------|-----------|
|`AppDomainResourceManagementKeyword` (0x800)|Informacyjny (4)|
|`ThreadingKeyword` (0x10000)|Informacyjny (4)|

W poniższej tabeli przedstawiono informacje o zdarzeniu:

|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|
|-----------|--------------|-----------------|
|`ThreadCreated`|85|Utworzono wątek dla domeny aplikacji.|

W poniższej tabeli przedstawiono dane zdarzenia:

|Nazwa pola|Typ danych|Opis|
|----------------|---------------|-----------------|
|ThreadID|win: UInt64|Identyfikator utworzonego wątku.|
|AppDomainID|win: UInt64|Identyfikator domeny aplikacji, dla której jest zgłaszane działanie wątku.|
|Flagi|win: UInt32|Flagi tworzenia wątku.|
|ManagedThreadIndex|win: UInt32|Zarządzany indeks wątku, który został utworzony.|
|OSThreadID|win: UInt32|Identyfikator systemu operacyjnego wątku, który został utworzony.|
|ClrInstanceID|win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|

## <a name="appdomainmemallocated-event"></a>Zdarzenie AppDomainMemAllocated

W poniższej tabeli przedstawiono słowo kluczowe i poziom:

|Słowo kluczowe do podniesienia zdarzenia|Poziom|
|-----------------------------------|-----------|
|`AppDomainResourceManagementKeyword` (0x800)|Informacyjny (4)|

W poniższej tabeli przedstawiono informacje o zdarzeniu:

|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|
|-----------|--------------|-----------------|
|`AppDomainMemAllocated`|83|Co 4 MB pamięci (w przybliżeniu) jest przypisywany w domenie aplikacji.|

W poniższej tabeli przedstawiono dane zdarzenia:

|Nazwa pola|Typ danych|Opis|
|----------------|---------------|-----------------|
|AppDomainID|win: UInt64|Identyfikator domeny aplikacji, dla której zgłaszane jest użycie zasobów.|
|Rozdziela|win: UInt64|Całkowita liczba bajtów przydzielono w tej domenie aplikacji od momentu utworzenia domeny aplikacji (ilość zwolnionej pamięci nie jest odejmowana).|
|ClrInstanceID|win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|

## <a name="appdomainmemsurvived-event"></a>Zdarzenie AppDomainMemSurvived

W poniższej tabeli przedstawiono słowo kluczowe i poziom:

|Słowo kluczowe do podniesienia zdarzenia|Poziom|
|-----------------------------------|-----------|
|`AppDomainResourceManagementKeyword` (0x800)|Informacyjny (4)|

W poniższej tabeli przedstawiono informacje o zdarzeniu:

|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|
|-----------|--------------|-----------------|
|`AppDomainMemSurvived`|84|Wszystkie wyrzucanie elementów bezużytecznych zostało zakończone.|

W poniższej tabeli przedstawiono dane zdarzenia:

|Nazwa pola|Typ danych|Opis|
|----------------|---------------|-----------------|
|AppDomainID|win: UInt64|Identyfikator domeny, dla której zgłaszane jest użycie zasobów.|
|Ocalałe|win: UInt64|Liczba bajtów przeprowadzonych po ostatniej kolekcji i, które są znane przez tę domenę aplikacji. Ta liczba jest dokładna i kompletna po pełnej kolekcji, ale może być niekompletna po kolekcji tymczasowej.|
|ProcessSurvived|win: UInt64|Całkowita liczba bajtów przeczytanych z ostatniej kolekcji. Po pełnej kolekcji ta liczba reprezentuje liczbę bajtów przechowywanych na żywo w zarządzanych stertach. Po zakończeniu zbierania danych tymczasowych ta liczba reprezentuje liczbę bajtów przechowywanych na żywo w generacjach tymczasowych.|
|ClrInstanceID|win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|

## <a name="threadappdomainenter-event"></a>Zdarzenie ThreadAppDomainEnter

W poniższej tabeli przedstawiono słowo kluczowe i poziom:

|Słowo kluczowe do podniesienia zdarzenia|Poziom|
|-----------------------------------|-----------|
|`AppDomainResourceManagementKeyword` (0x800)|Informacyjny (4)|
|`ThreadingKeyword` (0x10000)|Informacyjny (4)|

W poniższej tabeli przedstawiono informacje o zdarzeniu:

|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|
|-----------|--------------|-----------------|
|`ThreadAppDomainEnter`|87|Wątek przechodzi do domeny aplikacji.|

W poniższej tabeli przedstawiono dane zdarzenia:

|Nazwa pola|Typ danych|Opis|
|----------------|---------------|-----------------|
|ThreadID|win: UInt64|Identyfikator wątku.|
|AppDomainID|win: UInt64|Identyfikator domeny aplikacji.|
|ClrInstanceID|win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|

## <a name="threadterminated-event"></a>Zdarzenie ThreadTerminated

W poniższej tabeli przedstawiono słowo kluczowe i poziom:

|Słowo kluczowe do podniesienia zdarzenia|Poziom|
|-----------------------------------|-----------|
|`AppDomainResourceManagementKeyword` (0x800)|Informacyjny (4)|
|`ThreadingKeyword` (0x10000)|Informacyjny (4)|

W poniższej tabeli przedstawiono informacje o zdarzeniu:

|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|
|-----------|--------------|-----------------|
|`ThreadTerminated`|86|Wątek kończy działanie.|

W poniższej tabeli przedstawiono dane zdarzenia:

|Nazwa pola|Typ danych|Opis|
|----------------|---------------|-----------------|
|ThreadID|win: UInt64|Identyfikator wątku.|
|AppDomainID|win: UInt64|Identyfikator domeny aplikacji.|
|ClrInstanceID|win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|

## <a name="see-also"></a>Zobacz także

- [Zdarzenia CLR ETW](clr-etw-events.md)
