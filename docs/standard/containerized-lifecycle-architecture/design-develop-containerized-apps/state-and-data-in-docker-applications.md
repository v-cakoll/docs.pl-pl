---
title: Stan i dane w aplikacjach platformy Docker
description: Dowiedz się, dostępną opcją do zapisywania stanu w konteneryzowanych aplikacji.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 30dde3ce44aa61fff3fad1841ae4a8b941573877
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57678088"
---
# <a name="state-and-data-in-docker-applications"></a>Stan i dane w aplikacjach platformy Docker

W większości przypadków można traktować jako wystąpienie procesu kontenera. Proces nie przechowuje stanu trwałego. Gdy kontener może zapisywać jej magazynu lokalnego, przy założeniu, że wystąpienie będzie wokół przez czas nieokreślony przypomina przy założeniu, że będą trwałe jednej lokalizacji w pamięci. Obrazy kontenerów, takich jak procesy, należy przyjąć, że istnieje wiele wystąpień, a po pewnym czasie zostaną skasowane; Jeśli są one zarządzane z koordynatorem kontenera, należy zakładać, że może uzyskać z jednego węzła lub maszyny Wirtualnej przeniesione do innego.

Następujące rozwiązania są używane do zarządzania trwałości danych w aplikacji platformy Docker:

Z hosta platformy Docker jako [woluminów Docker](https://docs.docker.com/engine/admin/volumes/):

- **Woluminy** są przechowywane w obszarze systemu plików hosta, który jest zarządzany przez platformę Docker.

- **Powiąż instaluje** można mapować do dowolnego folderu systemu plików hosta, więc dostępu nie mogą być kontrolowane z procesu platformy Docker i może stanowić zagrożenie bezpieczeństwa, ponieważ kontener może uzyskać dostępu do poufnych folderów systemu operacyjnego.

- **Instaluje tmpfs** są, takich jak foldery wirtualne, które tylko istnieje w pamięci hosta i nigdy nie są zapisywane w systemie plików.

Z magazynu zdalnego:

- [Usługa Azure Storage](https://azure.microsoft.com/documentation/services/storage/) zapewnia magazyn geograficznie dystrybucyjny, zapewniając dobrym rozwiązaniem długoterminowym stanów trwałych dla kontenerów.

- Zdalne relacyjnych baz danych, takich jak [usługi Azure SQL Database](https://azure.microsoft.com/services/sql-database/), bazy danych NoSQL, takie jak [usługi Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction), lub usług, takich jak buforowanie [Redis](https://redis.io/).

Z kontenera platformy Docker:

- Środowisko docker zawiera funkcję o nazwie *nakładki system plików*. Ta funkcja wykonuje zadania kopii przy zapisie czy magazyny zaktualizowane informacje do katalogu głównego systemu plików kontenera. Te informacje "Określa na górze" oryginalnego obrazu, na którym bazuje kontenera. Jeśli kontener zostanie usunięty z systemu, te zmiany zostaną utracone. W związku z tym mimo że jest możliwe do zapisywania stanu kontener w ramach jego magazynu lokalnego, projektowanie systemu, w oparciu o tę funkcję spowodowałoby to konflikt z założenia projektowania kontenera, która domyślnie jest bezstanowy.

- Jednak woluminy platformy Docker jest teraz preferowanym sposobem obsługi danych lokalnych na platformie Docker. Aby uzyskać więcej informacji na temat magazynu w kontenerach, sprawdzić [sterowników pamięci masowej Docker](https://docs.docker.com/engine/userguide/storagedriver/) i [o obrazy kontenerów i sterowniki magazynu](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/).

Poniżej zamieszczono dodatkowe informacje dotyczące tych opcji.

**Woluminy** są mapowane z systemem operacyjnym hosta do katalogów w kontenerach katalogów. Gdy kod w kontenerze ma dostęp do katalogu, dostęp jest faktycznie do katalogu na hoście systemu operacyjnego. Ten katalog nie jest związany z okresem istnienia samego kontenera, a katalog jest zarządzane przez platformę Docker i odizolowanych od podstawowych funkcji maszyny hosta. W efekcie woluminów danych są przeznaczone do utrwalenia danych niezależnie od cyklu życia kontenera. Czy usunąć kontener obrazu z hosta platformy Docker, dane utrwalone w woluminie danych nie zostanie usunięty.

Woluminy mogą być nazwane i anonimowe (ustawienie domyślne). Nazwane woluminy są dostępne w rozwój **kontenery woluminów danych** , co ułatwia udostępnianie danych między kontenerów. Woluminy obsługują także sterowników woluminów, które umożliwiają przechowywanie danych na zdalnym hosty, między innymi opcjami.

**Powiąż instaluje** były dostępne przez długi czas i pozostawić mapowanie dowolnego folderu w punkcie instalacji w kontenerze. Instaluje powiązania ma więcej ograniczeń niż woluminy i niektóre problemy dotyczące zabezpieczeń istotne, aby woluminy są to zalecana opcja.

**`tmpfs` Instaluje** są foldery wirtualne, które znajdują się tylko w pamięci hosta, a nigdy nie są zapisywane w systemie plików. Są one szybki i bezpieczny, ale użycia pamięci i są przeznaczone tylko dla danych nietrwałe.

Jak pokazano na rysunku 4-5, regularne woluminów Docker mogą być przechowywane na zewnątrz kontenerów, samodzielnie, ale w granicach fizycznego serwera hosta lub maszyny Wirtualnej. Jednak kontenerów platformy Docker nie może uzyskać dostęp do woluminu z jednego hosta serwera lub maszyny Wirtualnej do innego. Innymi słowy za pomocą tych woluminów nie jest możliwe do zarządzania danymi udostępniane między kontenerów, które można uruchomić na różnych hostach Docker, mimo że można osiągnąć za pomocą sterownika woluminu, który obsługuje hostów zdalnych.

![Woluminy mogą być współużytkowane między kontenerów, ale tylko w tym samym hoście, chyba że w przypadku używania zdalnego sterownika, która obsługuje hostów zdalnych. ](./media/image5.png)

**Rysunek 4-5**. Woluminy i zewnętrznych źródeł danych dla aplikacji opartych na kontenerach

Ponadto gdy kontenerów platformy Docker są zarządzane przez program orchestrator, kontenerów może "Przenieś" między hostami w zależności od optymalizacje wykonywane przez klaster. W związku z tym nie jest zalecane, użyć woluminów danych dla danych biznesowych. Ale są one dobrym mechanizm do pracy z plikami śledzenia, pliki danych czasowych lub podobne, który nie ma wpływu na spójność danych biznesowych.

**Zdalnych źródeł danych i pamięć podręczna** aplikacji kontenerowych nimi narzędzi, takich jak Azure SQL Database, Azure Cosmos DB lub zdalnego pamięci podręcznej, takich jak Redis można używać w taki sam sposób, są one używane podczas tworzenia bez kontenerów. To jest sprawdzonym sposobem przechowywania danych aplikacji biznesowych.

**Azure Storage.** Dane biznesowe zwykle należy umieścić w zasoby zewnętrzne lub baz danych, takich jak Azure Storage. Usługa Azure Storage udostępnia następujące usługi w chmurze:

- Magazyn obiektów blob przechowuje dane obiektów bez struktury. Obiekt blob może być dowolnego typu dane tekstowe lub binarne, takie jak dokument lub nośnik pliki (obrazy, audio i wideo). Magazyn obiektów blob jest również określany jako magazyn obiektów.

- Usługa File storage udostępnia współużytkowany magazyn dla starszych aplikacji używających standardowego protokołu SMB. Usługa Azure virtual machines i usług w chmurze mogą współużytkować dane plików między składnikami aplikacji za pośrednictwem zainstalowanych udziałów. Aplikacje lokalne mogą uzyskać dostęp do danych plików w udziale za pośrednictwem interfejsu API REST usługi plików.

- Usługa TABLE storage przechowuje zestawy danych ze strukturą. Magazyn tabel jest atrybutem klucza magazynu NoSQL, która umożliwia szybkie opracowywanie i szybki dostęp do dużych ilości danych.

**Relacyjne bazy danych i bazy danych NoSQL.** Istnieje wiele opcji dla zewnętrznych baz danych z relacyjnej bazy danych, takich jak SQL Server, PostgreSQL, Oracle lub NoSQL bazy danych, takich jak usługi Azure Cosmos DB, MongoDB itp. Te bazy danych nie będą wyjaśnione w ramach tego przewodnika, ponieważ są one różnych tematów całkowicie.

>[!div class="step-by-step"]
>[Poprzednie](monolithic-applications.md)
>[dalej](soa-applications.md)
