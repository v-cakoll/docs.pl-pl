---
title: Stan i dane w aplikacjach platformy Docker
description: Poznaj dostępną opcję zapisywania stanu w aplikacjach kontenerowych.
ms.date: 02/15/2019
ms.openlocfilehash: bc171a419632f2ac61c7c9bf6b201b84e0691c3a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295692"
---
# <a name="state-and-data-in-docker-applications"></a>Stan i dane w aplikacjach platformy Docker

W większości przypadków można traktować kontener jako wystąpienie procesu. Proces nie zachowuje trwałego stanu. Kontener może zapisywać do magazynu lokalnego, przy założeniu, że wystąpienie będzie się znajdować w nieskończoność, tak jak przy założeniu, że pojedyncza lokalizacja w pamięci będzie trwała. W przypadku obrazów kontenerów, takich jak procesy, należy założyć, że ma wiele wystąpień i ostatecznie zostanie zamknięty. Jeśli są one zarządzane przy użyciu koordynatora kontenerów, należy założyć, że mogą one zostać przeniesione z jednego węzła lub maszyny wirtualnej do innego.

Następujące rozwiązania służą do zarządzania trwałymi danymi w aplikacjach platformy Docker:

Z poziomu hosta platformy Docker jako [woluminów platformy Docker](https://docs.docker.com/engine/admin/volumes/):

- **Woluminy** są przechowywane w obszarze systemu plików hosta, który jest zarządzany przez platformę Docker.

- **Instalacje bind** można mapować do dowolnego folderu w systemie plików hosta, dlatego nie można sterować dostępem z procesu platformy Docker i może stanowić zagrożenie bezpieczeństwa, ponieważ kontener może uzyskać dostęp do poufnych folderów systemu operacyjnego.

- **instalacje tmpfs** są podobne do folderów wirtualnych, które znajdują się tylko w pamięci hosta i nigdy nie są zapisywane w systemie plików.

Z magazynu zdalnego:

- [Usługa Azure Storage](https://azure.microsoft.com/documentation/services/storage/) zapewnia magazyn z systemem geograficznym, co zapewnia dobre długoterminowe rozwiązanie trwałości dla kontenerów.

- Zdalne relacyjne bazy danych, takie jak [Azure SQL Database](https://azure.microsoft.com/services/sql-database/), bazy danych NoSQL, takie jak [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction)lub usługi pamięci podręcznej, takie jak [Redis](https://redis.io/)

Z kontenera Docker:

- Platforma Docker udostępnia funkcję o nazwie *system plików nakładki*. Ta funkcja implementuje zadanie kopiowania przy zapisie, które przechowuje zaktualizowane informacje do głównego systemu plików kontenera. Te informacje "stanowią na początku" oryginalny obraz, na którym bazuje kontener. Jeśli kontener zostanie usunięty z systemu, te zmiany zostaną utracone. W związku z tym, chociaż istnieje możliwość zapisania stanu kontenera w magazynie lokalnym, projektowanie systemu opartego na tej funkcji byłoby w konflikcie z założeniami projektu kontenera, który domyślnie jest bezstanowy.

- Jednak woluminy platformy Docker są teraz preferowanym sposobem obsługi danych lokalnych w platformie Docker. Jeśli potrzebujesz więcej informacji na temat magazynu w kontenerach, zapoznaj się z tematem [sterowniki magazynu Docker](https://docs.docker.com/engine/userguide/storagedriver/) i [obrazy, kontenery oraz sterowniki magazynu](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/).

Poniżej znajdują się dodatkowe szczegółowe informacje na temat tych opcji.

**Woluminy** są katalogami mapowanymi z systemu operacyjnego hosta do katalogów w kontenerach. Gdy kod w kontenerze ma dostęp do katalogu, dostęp jest w rzeczywistości do katalogu w systemie operacyjnym hosta. Ten katalog nie jest powiązany z okresem istnienia samego kontenera, a katalog jest zarządzany przez platformę Docker i izolowany od podstawowych funkcji komputera hosta. Z tego względu woluminy danych są przeznaczone do utrwalania danych niezależnie od okresu istnienia kontenera. Po usunięciu kontenera lub obrazu z hosta platformy Docker dane utrwalane w woluminie danych nie zostaną usunięte.

Woluminy mogą mieć nazwy lub anonimowe (domyślnie). Nazwane woluminy są ewolucją **kontenerów woluminów danych** i ułatwiają udostępnianie danych między kontenerami. Woluminy obsługują również sterowniki woluminów umożliwiające przechowywanie danych na hostach zdalnych między innymi opcjami.

**Instalacje wiązania** są dostępne przez długi czas i umożliwiają mapowanie dowolnego folderu do punktu instalacji w kontenerze. Instalacje powiązań mają więcej ograniczeń niż woluminy i niektóre ważne problemy z zabezpieczeniami, dlatego zalecaną opcją są woluminy.

instalacje są folderami wirtualnymi, które znajdują się na żywo tylko w pamięci hosta i nigdy nie są zapisywane w systemie plików. **`tmpfs`** Są one szybkie i bezpieczne, ale wykorzystują pamięć i są przeznaczone wyłącznie dla danych nietrwałych.

Jak pokazano na rysunku 4-5, regularne woluminy platformy Docker mogą być przechowywane poza kontenerami, ale w granicach fizycznych serwera hosta lub maszyny wirtualnej. Kontenery platformy Docker nie mogą jednak uzyskać dostępu do woluminu z jednego serwera hosta lub maszyny wirtualnej do innej. Innymi słowy, z tymi woluminami nie jest możliwe zarządzanie danymi udostępnionymi między kontenerami, które działają na różnych hostach platformy Docker, chociaż można je osiągnąć za pomocą sterownika woluminu obsługującego hosty zdalne.

![Woluminy mogą być udostępniane między kontenerami, ale tylko na tym samym hoście, chyba że używany jest sterownik zdalny obsługujący hosty zdalne. ](./media/image5.png)

**Rysunek 4-5**. Woluminy i zewnętrzne źródła danych dla aplikacji opartych na kontenerach

Ponadto, gdy kontenery platformy Docker są zarządzane przez program Orchestrator, kontenery mogą "przenosić" między hostami, w zależności od optymalizacji wykonywanych przez klaster. W związku z tym nie zaleca się używania woluminów danych dla danych firmowych. Jednak są dobrym mechanizmem do pracy z plikami śledzenia, plikami czasowymi lub podobnymi, które nie wpłyną na spójność danych firmy.

**Zdalne źródła danych i narzędzia pamięci podręcznej** , takie jak Azure SQL Database, Azure Cosmos DB lub zdalna pamięć podręczna, takie jak Redis, mogą być używane w aplikacjach kontenerowych w taki sam sposób, w jaki są używane podczas tworzenia bez kontenerów. Jest to sprawdzona metoda przechowywania danych aplikacji biznesowej.

**Usługa Azure Storage.** Dane biznesowe zwykle muszą być umieszczane w zasobach zewnętrznych lub bazach danych, takich jak usługa Azure Storage. Usługa Azure Storage udostępnia następujące usługi w chmurze:

- Magazyn obiektów BLOB przechowuje dane obiektu bez struktury. Obiekt BLOB może być dowolnego typu danych tekstowych lub binarnych, takich jak pliki dokumentów lub plików multimedialnych (obrazy, pliki audio i wideo). Magazyn obiektów BLOB jest również określany jako Storage Object.

- Magazyn plików oferuje udostępniony magazyn dla starszych aplikacji przy użyciu standardowego protokołu SMB. Usługa Azure Virtual Machines i usługi w chmurze mogą udostępniać dane plików między składnikami aplikacji za pośrednictwem zainstalowanych udziałów. Aplikacje lokalne mogą uzyskiwać dostęp do danych plików w udziale za pośrednictwem interfejsu API REST usługi plików.

- Magazyn tabel przechowuje zestawy danych ze strukturą. Table Storage to NoSQLy magazyn danych, który umożliwia szybkie tworzenie i szybki dostęp do dużych ilości danych.

**Relacyjne bazy danych i bazy danych NoSQL.** Istnieje wiele opcji zewnętrznych baz danych, z relacyjnych baz danych, takich jak SQL Server, PostgreSQL, Oracle lub NoSQL, takich jak Azure Cosmos DB, MongoDB itd. Te bazy danych nie są wyjaśnione jako część tego przewodnika, ponieważ są one jeszcze inne.

>[!div class="step-by-step"]
>[Poprzedni](monolithic-applications.md)Następny
>[](soa-applications.md)
