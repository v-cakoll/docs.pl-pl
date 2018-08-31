---
title: Stan i dane w aplikacjach platformy Docker
description: Cykl życia aplikacji konteneryzowanych platformy Docker przy użyciu platformy firmy Microsoft i narzędzi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 78db191bdec4c25c11728d819d89eaaaff4bd7da
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43257360"
---
# <a name="state-and-data-in-docker-applications"></a>Stan i dane w aplikacjach platformy Docker

Podstawowy kontenerów jest niezmienności. W porównaniu do maszyny Wirtualnej, kontenery nie znikają jako typowych wystąpienie. Maszyna wirtualna może się nie powieść w różnych formach martwy procesów, przeciążone procesora CPU lub dysk zapełniony lub nie powiodło się. Jeszcze oczekujemy, że maszyna wirtualna była dostępna, i RAID dyski są powszechne, aby mieć pewność, że błędy dysku przechowywania danych.

Jednak kontenery są uznawane za wystąpień procesów. Proces nie zachowują stan trwały. Mimo że kontener może zapisywać jej magazynu lokalnego, przy założeniu, że to wystąpienie będzie wokół przez czas nieokreślony byłaby równoważna przy założeniu, że pamięć jedną kopię będą trwałe. Należy przyjąć, że kontenery, takich jak procesy, są duplikowane zabite, lub gdy jest zarządzana z koordynatorem kontenera, może być przeniesiony.

Platforma docker korzysta funkcje znane jako *nakładki system plików* do zaimplementowania procesu kopii przy zapisie, który przechowuje dowolne zaktualizowane informacje do głównego systemu plików kontenera, w porównaniu do oryginalnego obrazu, na którym bazuje. Te zmiany zostaną utracone, jeśli kontener są usuwane z systemu. Kontener, w związku z tym, nie ma Magazyn trwały domyślnie. Chociaż istnieje możliwość zapisania stanu kontenera, projektowanie systemu obejścia tego problemu będzie konflikt z zasadą architekturę kontener.

Aby zarządzać trwałości danych w aplikacji platformy Docker, dostępne są typowe rozwiązania:

-   [**Woluminy danych**](https://docs.docker.com/engine/tutorials/dockervolumes/) tych instalacji na hoście, jak wspomniano tylko.

-   [**Kontenery woluminów danych**](https://docs.docker.com/engine/tutorials/dockervolumes/#/creating-and-mounting-a-data-volume-container) w kontenerach, za pomocą zewnętrznego kontenera, które mogą przechodzić te zapewnienia udostępnionego magazynu.

-   [**Wolumin wtyczek**](https://docs.docker.com/engine/tutorials/dockervolumes/#/mount-a-shared-storage-volume-as-a-data-volume) instalacji tych woluminów w lokalizacjach zdalnych, zapewniając długoterminowe trwałości.

-   **Zdalnych źródeł danych** przykłady obejmują bazy danych SQL i inny niż SQL lub usług, takich jak pamięci podręcznej Redis w pamięci podręcznej.

-   [**Usługa Azure Storage**](https://docs.microsoft.com/azure/storage/) zapewnia geograficznie dystrybucyjnego platformy jako magazyn usługa (PaaS), dzięki kontenerów jako długoterminowe trwałości.

Woluminy danych zostały specjalnie oznaczone katalogów w co najmniej jeden kontener, które obchodzą [złożenia System plików](https://docs.docker.com/glossary/?term=Union%20file%20system). Woluminy danych są przeznaczone do przechowywania danych, niezależnie od cyklu życia kontenera. Platformy docker w związku z tym nigdy nie spowoduje automatyczne usunięcie woluminów po usunięcie kontenera ani zostanie "zbieranie pamięci" woluminów, które nie są już używane przez kontener. System operacyjny hosta można przeglądać i edytować dane w dowolny wolumin za darmo, który jest po prostu kolejny powód, aby oszczędnie korzystać woluminów danych.

A [kontenera woluminów danych](https://docs.docker.com/glossary/?term=volume) jest ulepszeniem regularnych danych woluminów. Jest nieaktywni kontener, który ma co najmniej jeden wolumin danych utworzone w nim (zgodnie z wcześniejszym opisem). Kontener woluminów danych zapewnia dostęp do kontenerów z punktem instalacji centralnej. Zaletą tej metody dostępu jest, że przenosi jego lokalizacji oryginalnych danych, Tworzenie kontenera danych punkt instalacji logiczne. Umożliwia także kontenery "aplikacja" uzyskiwania dostępu do kontenera woluminów danych może być tworzone i niszczone, zachowując dane trwałego w kontenerze dedykowanych.

Rysunek 4-5 zawiera, można umieścić w pamięci masowej z kontenerów, samodzielnie, ale w obrębie hosta maszyny Wirtualnej i server fizycznymi granicami regularne woluminy platformy Docker. *Docker woluminy nie mają możliwość używania woluminu z jednego hosta serwera/maszyn wirtualnych do innego*.

![](./media/image5.png)

Rysunek 4-5: woluminów danych i zewnętrznych źródeł danych dla kontenerów aplikacji/kontenerów

Z powodu braku możliwości zarządzania danymi udostępniane między kontenerów, które są uruchamiane na osobnych hostach fizycznych, zalecane jest, aby używać woluminów dla danych biznesowych, chyba że hosta platformy Docker jest stałą hostów/maszyn wirtualnych, ponieważ podczas korzystania z kontenerów platformy Docker programu orchestrator oczekiwane są kontenery do przeniesienia od jednej do innego hosta, w zależności od optymalizacje wykonywane przez klaster.

W związku z tym woluminy regularnych danych są dobre mechanizm do pracy z plików śledzenia, pliki danych czasowych lub podobne pojęcia, które nie mają wpływu na spójność danych biznesowych lub gdy kontenerów zostaną przeniesione na wielu hostach.

[Dodatki plug-in woluminu](https://docs.docker.com/engine/extend/plugins_volume/) przekazywania danych na wszystkich hostach w klastrze. Mimo że nie wszystkie wtyczki woluminu są tworzone w równym stopniu, dodatki plug-in woluminu zwykle zapewniają zewnętrznych trwałego niezawodny magazyn z niezmienne kontenerów.

Zdalnych źródeł danych i pamięci podręczne, takich jak bazy danych SQL Database, DocumentDB lub zdalnego pamięci podręcznej, takich jak Redis będzie taki sam, jak projektowanie bez kontenerów. Jest to jedna z preferowanych i sprawdzone, sposoby przechowywania danych aplikacji biznesowych.


>[!div class="step-by-step"]
[Poprzednie](monolithic-applications.md)
[dalej](soa-applications.md)
