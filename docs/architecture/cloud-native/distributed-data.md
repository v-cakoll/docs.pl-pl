---
title: Rozproszone dane
description: Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure | Rozproszone dane dla natywnych aplikacji w chmurze
ms.date: 06/30/2019
ms.openlocfilehash: 92086c52b02360e90461aea9ad23a2068224e187
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183134"
---
# <a name="distributed-data-for-cloud-native-apps"></a>Rozproszone dane dla aplikacji natywnych w chmurze

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Podczas konstruowania systemu natywnego w chmurze, który składa się z wielu niezależnych mikrousług, w zależności od tego, jak sądzisz o zmianach w magazynie danych.

Tradycyjne aplikacje monolityczne preferują scentralizowany magazyn danych przedstawiony na rysunku 5-1. 

![Pojedyncza monolityczna baza danych](./media/single-monolithic-database.png)

**Rysunek 5-1**. Pojedyncza monolityczna baza danych

Zwróć uwagę na powyższym rysunku, w jaki sposób wszystkie składniki aplikacji używają pojedynczej relacyjnej bazy danych.

Ta metoda ma wiele zalet. Wykonywanie zapytań dotyczących rozmieszczenia danych w wielu tabelach jest proste i jest to proste w zaimplementowanie [transakcji kwaśnych](https://docs.microsoft.com/windows/desktop/cossdk/acid-properties) , które zapewniają spójność danych. Zawsze możesz mieć *natychmiastową spójność*: wszystkie aktualizacje danych lub żadne z nich nie są używane.

Systemy natywne w chmurze preferują architekturę danych pokazaną na rysunku 5-2, w której każda mikrousługa jest właścicielem i hermetyzuje własne dane.

![Wiele baz danych w mikrousługach](./media/data-across-microservices.png)

**Rysunek 5-2**. Wiele baz danych w mikrousługach

Zwróć uwagę na to, jak na poprzedniej ilustracji każda mikrousługa posiada i hermetyzuje magazyn danych IT i udostępnia tylko dane na świecie zewnętrznym ze swojego publicznego interfejsu API.
 
Ten model umożliwia samodzielne rozdzielenie każdej mikrousług bez konieczności koordynowania zmian schematu danych z innymi mikrousługami. Każda mikrousługa jest bezpłatna do wdrożenia magazynu danych (relacyjnej bazy danych, bazy danych dokumentów, magazynu klucz-wartość), który najlepiej odpowiada potrzebom. W czasie wykonywania każda mikrousługa może odpowiednio skalować swoje dane. Jest to pokazane na rysunku 5-3:

![Trwałość danych Polyglot](./media/polyglot-data-persistence.png)

**Rysunek 5-3**. Trwałość danych Polyglot

Zwróć uwagę na to, jak na poprzedniej ilustracji, w jaki sposób katalog produktów i mikrousługi spisu przyjmują relacyjne bazy danych, mikrousługa do porządkowania, baza danych dokumentów NoSql oraz mikrousługa koszyka zakupów, który jest zewnętrznym magazynem wartości. Relacyjne bazy danych pozostają istotne dla mikrousług z danymi złożonymi, jednak bazy danych NoSQL uzyskały znaczną popularność, zapewniając możliwość adaptacji, szybkie wyszukiwanie i wysoką dostępność. Ich charakter bez schematu pozwala deweloperom poruszać się od architektury klas danych z określonym typem i ORMs, co sprawia, że zmiany są kosztowne i czasochłonne.

>[!div class="step-by-step"]
>[Poprzedni](service-mesh-communication-infrastructure.md)
>[Następny](data-patterns.md)
