---
title: Dodatek-gRPC dla deweloperów WCF
description: Omówienie transakcji rozproszonych i ich implementacji w nowoczesnych architekturach mikrousług.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 10c4e77794c5ffe1aa6d5a629ce0b6cdf92f4ada
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184618"
---
# <a name="appendix-a---transactions"></a>Dodatek A — transakcje

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Windows Communication Foundation (WCF) obsługiwane transakcje rozproszone, umożliwiając wykonywanie operacji niepodzielnych w wielu usługach. Ta funkcja była oparta na [Distributed Transaction Coordinator firmy Microsoft](https://docs.microsoft.com/previous-versions/windows/desktop/ms684146(v=vs.85)).

W nowoczesnych mikrousługach, ten typ zautomatyzowanego przetwarzania transakcji rozproszonych nie jest możliwy. Istnieje zbyt wiele różnych technologii podczas odtwarzania, w tym relacyjne bazy danych, magazyny danych NoSQL oraz systemy obsługi komunikatów, nie wspominając o kombinacji systemów operacyjnych, języków programowania i struktur, które mogą być używane w jednym środowisku.

Transakcja rozproszona WCF to implementacja tego, co jest znane jako [zatwierdzanie dwufazowe (2PC)](https://en.wikipedia.org/wiki/Two-phase_commit_protocol). Możliwe jest ręczne wdrożenie transakcji 2PC przez koordynowanie komunikatów między usługami, tworzenie otwartych transakcji w ramach każdej usługi i wysyłanie komunikatów "Commit" lub "wycofywania" w zależności od sukcesu lub niepowodzenia. Jednak złożoność związaną z zarządzaniem 2PC może wzrosnąć w miarę rozwoju systemów, a otwarte transakcje przechowują blokady bazy danych, które mogą mieć negatywny wpływ na wydajność, a gorszą, powodują zakleszczenia między usługami.

Jeśli to możliwe, najlepiej jest unikać transakcji rozproszonych. Jeśli dwa elementy danych są tak połączone jak w celu żądania niepodzielnych aktualizacji, należy rozważyć ich obsługę zarówno w ramach tej samej usługi, jak i zastosować te niepodzielne zmiany za pomocą pojedynczego żądania lub wiadomości do tej usługi.

Jeśli to nie jest możliwe, jedną alternatywą jest użycie [wzorca Saga](https://microservices.io/patterns/data/saga.html). W Saga aktualizacje są przetwarzane sekwencyjnie; ponieważ każda aktualizacja przebiegła pomyślnie, zostanie wyzwolona Następna. Te wyzwalacze mogą być propagowane z usługi do usługi lub zarządzane przez koordynatora Saga lub "Orchestrator". Jeśli aktualizacja nie powiedzie się w dowolnym momencie w trakcie tego procesu, usługi, które już ukończyły aktualizacje, stosują określoną logikę do odwrócenia.

Kolejną opcją jest użycie konstrukcji opartej na domenie (DDD) i polecenia/zapytania (CQRS), zgodnie z opisem w [książce elektronicznej mikrousług .NET](https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/). W szczególności użycie zdarzeń domeny lub [źródła zdarzeń](https://martinfowler.com/eaaDev/EventSourcing.html) może pomóc w zapewnieniu, że aktualizacje&mdash;są spójne,&mdash;Jeśli nie zostaną natychmiast zastosowane.

>[!div class="step-by-step"]
>[Poprzednie](application-performance-management.md)
