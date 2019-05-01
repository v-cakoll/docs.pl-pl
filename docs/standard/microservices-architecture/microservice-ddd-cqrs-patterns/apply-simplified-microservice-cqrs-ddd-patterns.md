---
title: Stosowanie uproszczonych wzorców CQRS i DDD w mikrousługach
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Informacje ogólne relacji między wzorców CQRS i DDD.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: ef3260143c91c2500becd7c8c1a6cd0b81dbf3d2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62020104"
---
# <a name="apply-simplified-cqrs-and-ddd-patterns-in-a-microservice"></a>Zastosuj uproszczone wzorców CQRS i DDD w mikrousługach

CQRS to wzorzec architektoniczny oddzielający modeli do odczytywania i zapisywania danych. Powiązane termin [polecenia zapytania separacji (CQS)](https://martinfowler.com/bliki/CommandQuerySeparation.html) została pierwotnie zdefiniowana przez Bertrand Meyer w książce *konstrukcji oprogramowania zorientowanej na obiekt*. Podstawowa koncepcja jest dzieli operacje systemu na dwie kategorie gwałtownie rozdzielonych:

- Zapytania. Te zwracają wynik i nie zmieniają swojego stanu systemu i są wolne od efektów ubocznych.

- Polecenia. Te zmiany stanu systemu.

CQS to prosta koncepcja — to kwestia metod w obrębie tego samego obiektu zapytania lub poleceń. Każda metoda zwraca stan lub mutuje stanu, ale nie oba. Nawet obiekt wzorzec jednym repozytorium może być zgodne z CQS. CQS jest uznawana za podstawowe zasady dla CQRS.

[Polecenie i podział odpowiedzialności zapytania (CQRS)](https://martinfowler.com/bliki/CQRS.html) została wprowadzona przez Grega Younga i zdecydowanie wspierane przez Udi Dahan i innym osobom. Jest ona oparta na zasadzie CQS, mimo że jest bardziej szczegółowe. Wzorzec oparty na poleceń i zdarzeń oraz opcjonalnie na wiadomości asynchronicznych mogą zostać uwzględnione. W wielu przypadkach CQRS jest powiązana z bardziej zaawansowanych scenariuszy, takich jak o innej fizycznej bazy danych dla operacji odczytu (zapytania) niż do zapisu (aktualizacje). Ponadto może zaimplementować bardziej wydzielonego system CQRS [określania źródła zdarzeń (ES)](http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/) aktualizacji bazy danych, więc można będzie tylko przechowywania zdarzeń w modelu domeny zamiast przechowywania danych w bieżącym stanie. Jednak nie jest to rozwiązanie używane w tym przewodniku; używamy najprostsza metoda CQRS, który składa się z tylko oddzielenie zapytania w poleceniach.

Aspekt separacji CQRS jest osiągana przez grupowanie operacje zapytań w jednej warstwie i polecenia w innej warstwie. Każda warstwa ma swój własny model danych (należy zauważyć, że mówimy modelu, niekoniecznie innej bazy danych) i został skompilowany przy użyciu własnej kombinację wzorców i technologii. Co ważniejsze dwie warstwy mogą być w tej samej warstwie lub mikrousług, tak jak w przykładzie (kolejność mikrousług) używane w tym przewodniku. Lub może być wdrażany na różne mikrousługi i realizowania innych procesów, dzięki czemu mogą być zoptymalizowane pod kątem i niezależnie skalowana, bez wywierania wpływu na siebie nawzajem.

Podejście CQRS oznacza, że masz dwa obiekty dla operacji odczytu/zapisu, gdzie w innych kontekstach jest jednym. Istnieją powody, aby nieznormalizowany odczyty bazy danych, można zapoznać się w bardziej zaawansowanych literaturze CQRS. Jednak firma Microsoft nie korzystają z tego podejścia, której celem jest zapewnienie mają większą swobodę w zapytaniach zamiast ograniczanie zapytań za pomocą ograniczenia na podstawie wzorców DDD, takich jak zagregowanych danych.

Przykładem tego rodzaju usługi jest szeregowania mikrousług z aplikacji referencyjnej w ramach aplikacji eShopOnContainers. Ta usługa implementuje mikrousługi opartych na podejściu CQRS uproszczone. Używa pojedynczego źródła danych lub bazy danych, ale dwa modele logiczne oraz wzorców DDD transakcyjnych domeny, jak pokazano w rysunek 7-2.

![Logiczne mikrousług porządkowanie obejmuje swojej porządkowanie bazy danych, która może być lub nie znajduje się w tej samej platformy Docker hosta. Bazy danych na tym samym hoście platformy Docker jest dobry do tworzenia aplikacji, ale nie w środowisku produkcyjnym.](./media/image2.png)

**Rysunek 7-2**. Uproszczone podejście CQRS i DDD oparte na mikrousługach

Warstwa aplikacji może być sam interfejs API sieci Web. Aspektu ważnych projektu w tym miejscu jest z poleceń, model domeny i transakcje zgodnie ze wzorcem CQRS czy mikrousług został podzielony, zapytania i modele widoków (szczególnie utworzone dla aplikacji klienckich modele danych). To podejście zapewnia zapytania niezależnie od ograniczenia i ograniczenia pochodzące z wzorców DDD, odpowiednich tylko dla transakcji i aktualizacjami, zgodnie z opisem w kolejnych sekcjach.

>[!div class="step-by-step"]
>[Poprzednie](index.md)
>[dalej](eshoponcontainers-cqrs-ddd-microservice.md)