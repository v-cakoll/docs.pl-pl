---
title: Stan i dane w aplikacjach platformy Docker
description: Zarządzanie stanem i danymi w aplikacjach platformy Docker. Wystąpienia mikrousług są zbędne, ale dane nie jest, jak obsługiwać to z mikrousług.
ms.date: 09/20/2018
ms.openlocfilehash: 1157ea3c4ca8fc389769308cc0a1141b5f92bb88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72771439"
---
# <a name="state-and-data-in-docker-applications"></a>Stan i dane w aplikacjach platformy Docker

W większości przypadków można myśleć o kontenerze jako wystąpienie procesu. Proces nie utrzymuje stanu trwałego. Podczas gdy kontener można zapisać do lokalnego magazynu, przy założeniu, że wystąpienie będzie wokół przez czas nieokreślony będzie jak przy założeniu, że pojedyncza lokalizacja w pamięci będzie trwałe. Należy założyć, że obrazy kontenera, takie jak procesy, mają wiele wystąpień lub ostatecznie zostaną zabite. Jeśli są one zarządzane za pomocą koordynatora kontenera, należy założyć, że mogą zostać przeniesione z jednego węzła lub maszyny Wirtualnej do innego.

Następujące rozwiązania są używane do zarządzania danymi w aplikacjach platformy Docker:

Z hosta platformy Docker jako [woluminy platformy Docker:](https://docs.docker.com/engine/admin/volumes/)

- **Woluminy** są przechowywane w obszarze systemu plików hosta, który jest zarządzany przez platformę Docker.

- **Powiększe montuje** można mapować do dowolnego folderu w systemie plików hosta, więc dostęp nie może być kontrolowane z procesu platformy Docker i może stanowić zagrożenie bezpieczeństwa jako kontener może uzyskać dostęp do poufnych folderów systemu operacyjnego.

- **montuje tmpfs** są jak foldery wirtualne, które istnieją tylko w pamięci hosta i nigdy nie są zapisywane w systemie plików.

Z magazynu zdalnego:

- [Usługa Azure Storage](https://azure.microsoft.com/documentation/services/storage/), która zapewnia magazyn geograficzny, zapewniając dobre długoterminowe rozwiązanie trwałości dla kontenerów.

- Zdalne relacyjne bazy danych, takie jak [baza danych SQL Azure SQL](https://azure.microsoft.com/services/sql-database/) lub bazy danych NoSQL, takie jak usługa Azure [Cosmos DB,](https://docs.microsoft.com/azure/cosmos-db/introduction)lub usługi pamięci podręcznej, takie jak [Redis](https://redis.io/).

Z kontenera platformy Docker:

- **Nakładki systemu plików**. Ta funkcja platformy Docker implementuje zadanie kopiowania przy zapisie, które przechowuje zaktualizowane informacje w głównym systemie plików kontenera. Informacje te są "na wierzchu" oryginalnego obrazu, na którym znajduje się kontener. Jeśli kontener zostanie usunięty z systemu, te zmiany zostaną utracone. W związku z tym, gdy jest możliwe, aby zapisać stan kontenera w jego lokalnej pamięci masowej, projektowanie systemu wokół tego będzie w konflikcie z założenia projektu kontenera, który domyślnie jest bezstanowy.

Jednak przy użyciu woluminów platformy Docker jest teraz preferowanym sposobem obsługi danych lokalnych w platformie Docker. Jeśli potrzebujesz więcej informacji na temat magazynu w kontenerach sprawdź [sterowniki magazynu platformy Docker](https://docs.docker.com/storage/storagedriver/select-storage-driver/) i [Informacje o sterownikach magazynu](https://docs.docker.com/storage/storagedriver/).

Poniżej przedstawiono więcej szczegółów na temat tych opcji:

**Woluminy** są katalogami mapowanymi z systemu operacyjnego hosta na katalogi w kontenerach. Gdy kod w kontenerze ma dostęp do katalogu, ten dostęp jest faktycznie do katalogu w os hosta. Ten katalog nie jest powiązany z okresem istnienia samego kontenera, a katalog jest zarządzany przez platformę Docker i odizolowany od podstawowej funkcjonalności komputera hosta. W związku z tym woluminy danych są przeznaczone do utrwalania danych niezależnie od żywotności kontenera. Jeśli usuniesz kontener lub obraz z hosta platformy Docker, dane utrwalione w woluminie danych nie zostaną usunięte.

Woluminy mogą być nazwane lub anonimowe (domyślnie). Nazwane woluminy są ewolucją **kontenerów woluminów danych** i ułatwiają udostępnianie danych między kontenerami. Woluminy obsługują również sterowniki woluminów, które umożliwiają przechowywanie danych na hostach zdalnych, między innymi.

**Powiększe są** dostępne od dawna temu i umożliwiają mapowanie dowolnego folderu do punktu instalacji w kontenerze. Iniwady powiązań mają więcej ograniczeń niż woluminy i niektóre ważne problemy z zabezpieczeniami, więc woluminy są zalecaną opcją.

**montuje tmpfs** są w zasadzie wirtualnymi folderami, które żyją tylko w pamięci hosta i nigdy nie są zapisywane w systemie plików. Są szybkie i bezpieczne, ale używają pamięci i są przeznaczone tylko dla tymczasowych, nietrwałych danych.

Jak pokazano na rysunku 4-5, regularne woluminy platformy Docker mogą być przechowywane poza kontenerami, ale w granicach fizycznych serwera hosta lub maszyny Wirtualnej. Jednak kontenery platformy Docker nie można uzyskać dostępu do woluminu z jednego serwera hosta lub maszyny Wirtualnej do innego. Innymi słowy z tych woluminów nie jest możliwe zarządzanie danymi współużytkowane między kontenerami, które są uruchamiane na różnych hostach platformy Docker, chociaż można to osiągnąć za pomocą sterownika woluminu, który obsługuje hosty zdalne.

![Diagram przedstawiający woluminy i zewnętrzne źródła danych dla aplikacji opartych na kontenerach.](./media/docker-application-state-data/volumes-external-data-sources.png)

**Rysunek 4-5**. Woluminy i zewnętrzne źródła danych dla aplikacji opartych na kontenerach

Woluminy mogą być współużytkowane między kontenerami, ale tylko w tym samym hoście, chyba że używasz sterownika zdalnego obsługującego hosty zdalne. Ponadto gdy kontenery platformy Docker są zarządzane przez koordynatora, kontenery mogą "przenosić się" między hostami, w zależności od optymalizacji wykonywanych przez klaster. W związku z tym nie zaleca się używania woluminów danych dla danych biznesowych. Ale są one dobrym mechanizmem do pracy z plikami śledzenia, plikami czasowymi lub podobnymi, które nie będą miały wpływu na spójność danych biznesowych.

Zdalne źródła danych i narzędzia **pamięci podręcznej,** takie jak usługa Azure SQL Database, usługa Azure Cosmos DB lub zdalna pamięć podręczna, taka jak Redis, mogą być używane w aplikacjach konteneryzowanych w taki sam sposób, w jaki są używane podczas tworzenia bez kontenerów. Jest to sprawdzony sposób przechowywania danych aplikacji biznesowych.

**Azure Storage.** Dane biznesowe zwykle muszą być umieszczone w zasobach zewnętrznych lub bazach danych, takich jak usługa Azure Storage. Usługa Azure Storage, w sposób konkretny, zapewnia następujące usługi w chmurze:

- Magazyn obiektów blob przechowuje nieustrukturyzowane dane obiektów. Obiekt blob może być dowolnym rodzajem tekstu lub danych binarnych, takich jak pliki dokumentów lub plików multimedialnych (obrazy, pliki audio i wideo). Magazyn obiektów Blob jest także nazywany magazynem obiektów.

- Magazyn plików oferuje magazyn udostępniony dla starszych aplikacji przy użyciu standardowego protokołu SMB. Maszyny wirtualne platformy Azure i usługi w chmurze mogą udostępniać dane plików między składnikami aplikacji za pośrednictwem zainstalowanych udziałów. Aplikacje lokalne mogą uzyskiwać dostęp do danych plików w udziale za pośrednictwem interfejsu API REST usługi plików.

- Table Storage — przechowuje zestawy danych ze strukturą. Magazyn tabel to magazyn danych kluczy noSQL, który umożliwia szybki rozwój i szybki dostęp do dużych ilości danych.

**Relacyjne bazy danych i bazy danych NoSQL.** Istnieje wiele opcji dla zewnętrznych baz danych, z relacyjnych baz danych, takich jak SQL Server, PostgreSQL, Oracle lub NoSQL baz danych, takich jak Azure Cosmos DB, MongoDB, itp. Te bazy danych nie będą wyjaśnione jako część tego przewodnika, ponieważ są one w zupełnie innym temacie.

>[!div class="step-by-step"]
>[Poprzedni](containerize-monolithic-applications.md)
>[następny](service-oriented-architecture.md)
