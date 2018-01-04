---
title: "Stosowanie uproszczony CQRS i DDD wzorce w mikrousługi"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Stosowanie uproszczony CQRS i DDD wzorce w mikrousługi"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5369ff73a0614170b220177f1e5d388483ca19f8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="applying-simplified-cqrs-and-ddd-patterns-in-a-microservice"></a>Stosowanie uproszczony CQRS i DDD wzorce w mikrousługi

CQRS jest wzorzec architektury, która oddziela modeli do odczytywania i zapisywania danych. Powiązane termin [polecenia separacja zapytania (CQS)](https://martinfowler.com/bliki/CommandQuerySeparation.html) została pierwotnie zdefiniowana przez Bertrand Meyer w jego książce *konstrukcji oprogramowania przeznaczonych dla obiektów*. Podstawową koncepcją jest podzielenie operacje systemu na dwie kategorie znacznie rozdzielonych:

-   Zapytania. Te zwrócony wynik i nie należy zmieniać stanu systemu i są wolne od efekty uboczne.

-   Polecenia. Te zmiany stanu systemu.

CQS to pojęcie proste — jest o metod w ramach tego samego obiektu zapytania lub poleceń. Każda metoda zwraca stan lub mutuje stanu, ale nie oba. Nawet obiektu wzorzec jednym repozytorium może być zgodne z CQS. CQS mogą zostać uwzględnione w CQRS podstawowych zasady.

[Polecenie i podział odpowiedzialności kwerendy (CQRS)](https://martinfowler.com/bliki/CQRS.html) została wprowadzona przez małych Gregowi i silnie awansowane przez Udi Dahan i inne osoby. Mimo że jest bardziej szczegółowe jest oparty na zasadzie CQS. Można uważać wzorzec oparty na poleceń i zdarzeń, oraz opcjonalnie w wiadomościach asynchronicznych. W wielu przypadkach CQRS powiązany jest bardziej zaawansowanych scenariuszy, takich jak o innej fizycznej bazy danych dla odczytów (queries) niż w przypadku zapisów (aktualizacji). Ponadto może zastosować bardziej wydzielonego systemu CQRS [źródłem zdarzeń (ES)](http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/) aktualizacje bazy danych, więc będzie tylko są przechowywane zdarzeń w modelu domeny zamiast zapisywania danych w bieżącym stanie. Jednak nie jest to rozwiązanie używane w tym przewodniku; użyto najprostsza metoda CQRS, która składa się z tylko oddzielanie zapytania z poleceniami.

Aspekt separacji CQRS jest to osiągane przez grupowanie operacje kwerend w jednej warstwy i polecenia w innej warstwie. Każda warstwa ma własny model danych (Zauważ, że możemy powiedzieć modelu, niekoniecznie innej bazy danych) i jest utworzony przy użyciu własnego kombinację wzorców i technologii. Co więcej dwie warstwy może być w tej samej warstwie lub mikrousługi, jak pokazano w przykładzie (kolejność mikrousługi) używany dla tego przewodnika. Lub może można zaimplementować w różnych mikrousług lub procesów, dlatego może być zoptymalizowany i skalowanie oddzielnie bez wpływu na siebie.

CQRS oznacza o dwa obiekty pod kątem operacji odczytu/zapisu, gdy w innych kontekstach istnieje. Brak powodów do bazy danych nieznormalizowany odczytów, którym można zapoznać się w bardziej zaawansowanym materiały CQRS. Ale nie używamy tego podejścia, której celem jest uzyskuje się większą elastyczność w zapytaniach zamiast ograniczanie zapytań dotyczących ograniczenia na podstawie wzorców DDD, takie jak wartości zagregowanych.

Przykładem tego rodzaju usługi jest porządkowania mikrousługi z eShopOnContainers odwołania aplikacji. Ta usługa implementuje mikrousługi, oparty na uproszczonej podejście CQRS. Używa pojedynczego źródła danych lub bazy danych, ale dwa modele logiczne oraz wzorce DDD transakcyjne domeny, jak pokazano na rysunku 9-2.

![](./media/image2.png)

**Rysunek 9-2**. Uproszczone na podstawie CQRS i DDD mikrousługi

Warstwa aplikacji może być interfejsu API sieci Web, do samej siebie. Aspekt ważne projektu w tym miejscu jest czy mikrousługi została podzielona, zapytań i ViewModels (szczególnie utworzone dla aplikacji klienckich modeli danych) z poleceń, model domeny i po wzorzec CQRS transakcji. Takie podejście pozwala zapytania niezależnie od ograniczeń i ograniczenia pochodzące z wzorców DDD, które warto tylko transakcje i aktualizacji, zgodnie z objaśnieniem w kolejnych sekcjach.


>[!div class="step-by-step"]
[Poprzednie] (index.md) [dalej] (eshoponcontainers-cqrs-ddd-microservice.md)
