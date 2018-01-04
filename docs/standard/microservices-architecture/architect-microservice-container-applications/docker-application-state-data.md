---
title: Stan i dane w aplikacjach platformy Docker
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Stan i dane w aplikacjach platformy Docker"
keywords: "Docker, Mikrousług, ASP.NET, kontenera, SQL, CosmosDB, Docker"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ef11d89c39ee02d52dab29f949d1ac6be981d87f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="state-and-data-in-docker-applications"></a>Stan i dane w aplikacjach platformy Docker

W większości przypadków można traktować jako wystąpienie procesu kontenera. Proces nie przechowuje stanu trwałego. Gdy kontener może zapisywać do jego magazynu lokalnego, przy założeniu, że wystąpienie będzie wokół nieskończoność oznaczałoby przy założeniu, że jedno miejsce w pamięci są rejestrowane. Kontener obrazów, takich jak procesy, należy przyjąć, że wielu wystąpień lub po pewnym czasie zostaną skasowane; Jeśli są one zarządzane z orchestrator kontenera, należy założyć, że może pobrać z jednego węzła lub maszyna wirtualna przeniesiona do innego.

Docker oferuje funkcję o nazwie *nakładki system plików*. Implementuje to zadanie kopii przy zapisie czy magazyny zaktualizowane informacje do kontenera systemu plików głównego. Informacje te są dodatkowo do oryginalnego obrazu, na której oparto kontenera. Jeśli kontener zostanie usunięty z systemu, te zmiany zostaną utracone. W związku z tym jest możliwe zapisanie stanu kontener w ramach jego magazynu lokalnego, projektowania systemu obejścia tego problemu spowodowałoby to konflikt z lokalną projektu kontenera, która domyślnie jest bezstanowych.

Następujące rozwiązania są używane do zarządzania trwałych danych w aplikacjach Docker:

-   [Woluminy danych](https://docs.docker.com/engine/tutorials/dockervolumes/) zainstalować hosta.

-   [Kontenery woluminów danych](https://docs.docker.com/engine/tutorials/dockervolumes/#creating-and-mounting-a-data-volume-container) zawierających magazynu współdzielonego między kontenerów przy użyciu zewnętrznego kontenera.

-   [Wolumin wtyczek](https://docs.docker.com/engine/tutorials/dockervolumes/) który instalowania woluminów do usługi zdalnej, zapewniając długoterminowej trwałości.

-   [Usługa Azure Storage](https://docs.microsoft.com/azure/storage/), zapewniające dystrybucyjnego geo magazynu, zapewniając dobre rozwiązanie trwałości długoterminowej dla kontenerów.

-   Zdalne relacyjnych baz danych, takich jak [bazy danych SQL Azure](https://azure.microsoft.com/services/sql-database/) lub bazy danych NoSQL, takich jak [bazy danych Azure rozwiązania Cosmos](https://docs.microsoft.com/azure/cosmos-db/introduction), lub buforować usług, takich jak [Redis](https://redis.io/).

Poniżej znajdują się szczegółowe informacje o tych opcji.

**Woluminy danych** jest zamapowany z systemu operacyjnego hosta do katalogów w kontenerach katalogów. Gdy kod w kontenerze ma dostęp do katalogu, który dostępu jest rzeczywiście do katalogu na systemu operacyjnego hosta. Ten katalog nie jest związana z okresu istnienia kontenera i katalogu są dostępne z kodu uruchomionego bezpośrednio na hoście systemu operacyjnego lub przy użyciu innego kontenera mapuje ten sam katalog hostów do samej siebie. W związku z tym woluminy danych zostały zaprojektowane do utrwalenia danych niezależnie od jego czas życia kontenera. Jeśli usuniesz kontener lub obrazu z hostów Docker, dane utrwalone w woluminie danych nie zostanie usunięty. Z hosta systemu operacyjnego, jak również można uzyskać dostępu do danych w woluminie.

**Kontenery woluminów danych** są ewolucji regularnych danych woluminów. Kontener woluminów danych jest proste kontener, który ma co najmniej jeden wolumin danych znajdujące się w nim. Kontener woluminów danych zapewnia dostęp do kontenerów z punktem instalacji centralnej. Ta metoda dostępu do danych jest wygodne, ponieważ jego abstracts lokalizacji oryginalnych danych. Inną niż jego zachowanie jest podobne do woluminu regularnych danych, więc danych jest trwały, w tym kontenerze dedykowanych niezależnie od cyklem życia aplikacji kontenerów.

Jak pokazano na rysunku 4-5, regularne Docker woluminy mogą być przechowywane na zewnątrz kontenerów, się, ale w granicach fizycznego serwera hosta lub maszyny Wirtualnej. Jednak kontenery Docker nie może uzyskać dostęp do woluminu z jednego hosta serwera lub maszyny Wirtualnej do innego. Innymi słowy przy użyciu tych woluminów, nie jest możliwe zarządzanie danymi współużytkowane kontenerów, które są uruchamiane na różnych hostach Docker

![](./media/image5.png)

**Rysunek 4-5**. Woluminy danych i zewnętrznych źródeł danych do aplikacji kontenera

Ponadto gdy Docker kontenery są zarządzane przez program orchestrator, kontenerów może "move" między hostami, w zależności od optymalizacje wykonywane przez klaster. W związku z tym nie zalecane użycie woluminów danych dla danych biznesowych. Ale są dobrym mechanizm do pracy z plików śledzenia, pliki danych czasowych lub podobne który nie ma wpływu spójność danych biznesowych.

**Wolumin wtyczek** jak [Flocker](https://clusterhq.com/flocker/) zapewnić dostęp do danych na wszystkich hostach w klastrze. Nie wszystkie wtyczki woluminu tworzenia jednakowo, wolumin wtyczki zwykle Podaj externalized niezawodnej magazynu trwałego z kontenerów niezmienialny.

**Zdalnych źródeł danych i pamięci podręcznej** narzędzi, takich jak bazy danych SQL Azure, Azure DB rozwiązania Cosmos lub zdalnej pamięci podręcznej, takich jak Redis mogą być używane w konteneryzowanych aplikacji są one używane podczas tworzenia bez kontenery tak samo. Jest to sprawdzonych sposób przechowywania danych aplikacji biznesowych.

**Magazyn Azure.** Dane biznesowe zwykle należy można umieścić w zewnętrznych zasobów lub baz danych, takich jak usługi Azure Storage. Usługa Azure Storage, w konkretnych, udostępnia następujące usługi w chmurze:

-   Magazyn obiektów blob przechowuje dane obiektów bez struktury. Obiekt blob może być dowolnego typu dane tekstowe lub binarne, takie jak dokument lub nośnik plików (obrazów, audio i wideo). Magazyn obiektów blob jest również nazywany magazynem obiektów.

-   Magazyn plików oferuje współużytkowany magazyn dla starszych aplikacji używających standardowego protokołu SMB. Maszyny wirtualne platformy Azure i usługi w chmurze mogą udostępniać dane między składnikami aplikacji za pośrednictwem zainstalowanych udziałów. Lokalnych aplikacji można uzyskać dostępu do danych plików w udziale za pomocą interfejsu API REST usługi plików.

-   Table storage przechowuje zestawy danych ze strukturą. Magazyn tabel to magazyn pary klucz atrybut danych NoSQL, który umożliwia szybkie opracowywanie i szybki dostęp do dużych ilości danych.

**Relacyjnych baz danych i bazy danych NoSQL.** Istnieje wiele opcji dla zewnętrznych baz danych z relacyjnych baz danych, takich jak bazy danych programu SQL Server, PostgreSQL, Oracle lub NoSQL bazy danych Azure rozwiązania Cosmos, MongoDB itd. Te bazy danych nie będą można wyjaśnić w ramach tego przewodnika, ponieważ są one w całkowicie różnych tematów.


>[!div class="step-by-step"]
[Poprzednie] (containerize wbudowanymi applications.md) [dalej] (service ukierunkowane architecture.md)
