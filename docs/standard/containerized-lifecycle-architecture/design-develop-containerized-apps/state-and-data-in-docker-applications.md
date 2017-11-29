---
title: Stan i dane w aplikacjach platformy Docker
description: "Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 61cd88ca8dd7e51759111d6a9357c008458ee41a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="state-and-data-in-docker-applications"></a>Stan i dane w aplikacjach platformy Docker

Podstawowy kontenerów jest immutability. W porównaniu z maszyną wirtualną, kontenery nie znikają jako wystąpienie wspólnej. Maszyna wirtualna może się nie powieść w różnych formach martwy procesów, przeciążone procesora CPU lub dysk pełny lub nie powiodło się. Jeszcze oczekujemy, maszyna wirtualna może być dostępna i RAID dyski są typowe, aby mieć pewność, że obsługa awarii dysku danych.

Jednakże kontenery są uznawane za wystąpień procesów. Proces nie zachowują stan trwały. Mimo że kontener może zapisywać do jego magazynu lokalnego, przy założeniu, że to wystąpienie będzie wokół nieskończoność będą odpowiednikiem przy założeniu, że pamięć jedną kopię są rejestrowane. Należy założono, że są duplikowane kontenerów, takich jak procesów, zostały zakończone, lub gdy zarządzanych za pomocą orchestrator kontenera, mogą być przeniesione.

Docker używa funkcji znany jako *nakładki system plików* do zaimplementowania proces kopiowania przy zapisie, który przechowuje wszelkie zaktualizowane informacje do katalogu głównego systemu plików kontenera, w porównaniu do oryginalnego obrazu, na którym jest oparty. Te zmiany zostaną utracone, jeśli kontener są usuwane z systemu. Kontener, w związku z tym nie ma magazynu trwałego domyślnie. Chociaż można zapisać stanu kontenera, projektowania systemu obejścia tego problemu jest pozostają w konflikcie z zasadą architektura kontenera.

Aby zarządzać trwałych danych w aplikacjach Docker, są typowe rozwiązania:

-   [**Woluminy danych**](https://docs.docker.com/engine/tutorials/dockervolumes/) je zainstalować na hoście, jak tylko zanotowane.

-   [**Kontenery woluminów danych**](https://docs.docker.com/engine/tutorials/dockervolumes/#/creating-and-mounting-a-data-volume-container) określają one magazyn udostępniony przez kontenery, za pomocą zewnętrznego kontenera, w którym można przechodzić.

-   [**Wolumin wtyczek**](https://docs.docker.com/engine/tutorials/dockervolumes/#/mount-a-shared-storage-volume-as-a-data-volume) je zainstalować woluminów do lokalizacji zdalnych, zapewniając długoterminowej trwałości.

-   **Zdalnych źródeł danych** przykłady obejmują baz danych SQL i programu SQL nie lub pamięci podręcznej usługi, takie jak Redis.

-   [**Usługa Azure Storage**](https://docs.microsoft.com/azure/storage/) to zapewnia platformę dystrybucyjnego geograficznie jako magazynu usługa (PaaS), udostępnia najlepszy kontenery jako długoterminowej trwałości.

Woluminy danych specjalnie są wyznaczone katalogów w kontenerach pomijające [Unii System plików](https://docs.docker.com/v1.8/reference/glossary#union-file-system). Woluminy danych są przeznaczone do przechowywania danych, niezależnie od cyklu życia kontenera. Docker w związku z tym nigdy nie automatycznie usuwa woluminy gdy usunąć kontener ani zostanie "zbieranie pamięci" woluminów, które nie są już używane przez kontener. System operacyjny hosta można przeglądać i edytowanie danych w każdym woluminie za darmo, która jest po prostu kolejny powód, aby oszczędnie korzystać woluminów danych.

A [kontenera woluminów danych](https://docs.docker.com/v1.8/userguide/dockervolumes/) jest ulepszeniem regularnych danych woluminów. Jest zasadniczo nieaktywni kontener, który został utworzony w nim (zgodnie z wcześniejszym opisem) jeden lub więcej woluminów danych. Kontener woluminów danych zapewnia dostęp do kontenerów z punktem instalacji centralnej. Zaletą tej metody dostępu jest, że abstracts jego lokalizacji oryginalnych danych, co punkt instalacji logicznej kontenera danych. Umożliwia także dostęp do kontenera woluminów danych utworzona i zniszczona przy zachowaniu danych trwałych w kontenerze dedykowanych kontenery "aplikacji".

Rysunek 4-5 zawiera można umieścić w magazynie poza kontenery samodzielnie, ale w granicach fizycznego hosta maszyny Wirtualnej i server regularne woluminów Docker. *Docker woluminy nie mają możliwość używania woluminu z jednego hosta serwera/maszyny Wirtualnej do innego*.

![](./media/image5.png)

Rysunek 4-5: woluminów danych i zewnętrznych źródeł danych dla kontenerów aplikacji/kontenerów

Ze względu na brak możliwości zarządzania danymi współużytkowane przez kontenery działające na oddzielnych hostach fizycznych, zalecane jest, aby nie używać woluminów danych biznesowych, chyba że Docker host jest stałe hosta/maszyny Wirtualnej, ponieważ podczas korzystania z kontenerów Docker w orchestrator kontenery powinny zostać przeniesiona z jednego do innego hosta, w zależności od optymalizacje wykonywane przez klaster.

W związku z tym regularnych danych woluminy są w dobrym mechanizm do pracy z plików śledzenia, pliki danych czasowych lub żadnych koncepcji podobne, które nie mają wpływu na spójność danych biznesowych lub w przypadku kontenerów zostaną przeniesione na wielu hostach.

Wolumin dodatków plug-in, takich jak [Flocker](https://clusterhq.com/flocker/) dostarczania danych na wszystkich hostach w klastrze. Mimo że nie wszystkie wtyczki woluminu są tworzone w równym stopniu, wolumin wtyczki zwykle przechowywanie externalized trwałe niezawodnej z kontenerów niezmienne.

Zdalnych źródeł danych i pamięci podręczne, takie jak bazy danych SQL usługi DocumentDB i zdalnego pamięci podręcznej, takich jak Redis będzie taki sam, jak projektowanie bez kontenerów. To jest preferowany i sprawdzonych, sposoby do przechowywania danych aplikacji biznesowych.


>[!div class="step-by-step"]
[Poprzednie] (wbudowanymi applications.md) [dalej] (soa applications.md)
