---
title: Dodatek-gRPC dla deweloperów WCF
description: Omówienie transakcji rozproszonych i ich implementacji w nowoczesnych architekturach mikrousług.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: d181eb07dd50ed338d02edb1908626e6ca3fb56c
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846730"
---
# <a name="appendix-a---transactions"></a>Dodatek A — transakcje

Windows Communication Foundation (WCF) obsługiwane transakcje rozproszone, umożliwiając wykonywanie operacji niepodzielnych w wielu usługach. Ta funkcja była oparta na [Distributed Transaction Coordinator firmy Microsoft](https://docs.microsoft.com/previous-versions/windows/desktop/ms684146(v=vs.85)).

W nowoczesnych mikrousługach, ten typ zautomatyzowanego przetwarzania transakcji rozproszonych nie jest możliwy. Istnieje zbyt wiele różnych technologii podczas odtwarzania, w tym relacyjne bazy danych, magazyny danych NoSQL oraz systemy obsługi komunikatów, nie wspominając o kombinacji systemów operacyjnych, języków programowania i struktur, które mogą być używane w jednym środowisku.

Transakcja rozproszona WCF to implementacja tego, co jest znane jako [zatwierdzanie dwufazowe (2PC)](https://en.wikipedia.org/wiki/Two-phase_commit_protocol). Możliwe jest ręczne wdrożenie transakcji 2PC przez koordynowanie komunikatów między usługami, tworzenie otwartych transakcji w ramach każdej usługi i wysyłanie komunikatów "Commit" lub "wycofywania" w zależności od sukcesu lub niepowodzenia. Jednak złożoność związaną z zarządzaniem 2PC może wzrosnąć w miarę rozwoju systemów, a otwarte transakcje przechowują blokady bazy danych, które mogą mieć negatywny wpływ na wydajność, a gorszą, powodują zakleszczenia między usługami.

Jeśli to możliwe, najlepiej jest unikać transakcji rozproszonych. Jeśli dwa elementy danych są tak połączone jak w celu żądania niepodzielnych aktualizacji, należy rozważyć ich obsługę zarówno w ramach tej samej usługi, jak i zastosować te niepodzielne zmiany za pomocą pojedynczego żądania lub wiadomości do tej usługi.

Jeśli to nie jest możliwe, jedną alternatywą jest użycie [wzorca Saga](https://microservices.io/patterns/data/saga.html). W Saga aktualizacje są przetwarzane sekwencyjnie; ponieważ każda aktualizacja przebiegła pomyślnie, zostanie wyzwolona Następna. Te wyzwalacze mogą być propagowane z usługi do usługi lub zarządzane przez koordynatora Saga lub "Orchestrator". Jeśli aktualizacja nie powiedzie się w dowolnym momencie w trakcie tego procesu, usługi, które już ukończyły aktualizacje, stosują określoną logikę do odwrócenia.

Kolejną opcją jest użycie konstrukcji opartej na domenie (DDD) i polecenia/zapytania (CQRS), zgodnie z opisem w [książce elektronicznej mikrousług .NET](https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/). W szczególności użycie zdarzeń domeny lub [źródła zdarzeń](https://martinfowler.com/eaaDev/EventSourcing.html) może pomóc w zapewnieniu, że aktualizacje są stale&mdash;, jeśli nie zostaną natychmiast&mdash;zastosowane.

>[!div class="step-by-step"]
>[Ubiegł](application-performance-management.md)
