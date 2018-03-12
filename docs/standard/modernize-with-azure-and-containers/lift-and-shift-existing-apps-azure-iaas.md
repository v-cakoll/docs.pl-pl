---
title: "Podnieś i przesunięcie istniejące aplikacje IaaS platformy Azure"
description: "Modernizacji istniejących aplikacji .NET z chmury Azure i kontenery systemu Windows."
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6811da4b59531e27f2d832c102d37ba1383b15ab
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2018
---
# <a name="lift-and-shift-existing-apps-azure-iaas"></a>Podnieś i przesunięcie istniejące aplikacje IaaS platformy Azure

> Wizja: jako pierwszy krok, aby zmniejszyć z lokalnymi inwestycji i całkowitego kosztu sprzętu i sieci konserwacji, po prostu rehost istniejących aplikacji w chmurze.

Przed przejściem do *jak* Aby przeprowadzić migrację istniejących aplikacji do infrastruktury platformy Azure jako usługa (IaaS) platformy, ważne jest, aby analizować przyczyny *Dlaczego* chcesz przeprowadzić migrację bezpośrednio do IaaS na platformie Azure. Scenariusz na tym poziomie dojrzałości modernizacji jest zasadniczo aby rozpocząć korzystanie z maszyn wirtualnych w chmurze, a nie przechodzić do użyć bieżącej infrastruktury lokalnej.

Jest inny punkt do analizowania *Dlaczego* można przeprowadzić migrację do czystych chmury IaaS, a nie tylko dodanie więcej zaawansowanych usług zarządzanych na platformie Azure. Musisz określić przypadków może wymagać IaaS w pierwszej kolejności.

Rysunek 2-1 powoduje umieszczenie poziomów modernizacji aplikacje gotowe infrastruktury chmury:

![Pozycjonowanie aplikacje infrastruktury chmury gotowe do wydania](./media/image2-1.png)

> **Rysunek 2-1.** Pozycjonowanie aplikacje infrastruktury chmury gotowe do wydania

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>Dlaczego migracji istniejącej aplikacji sieci web .NET Azure IaaS

Głównym celem migrację do chmury, nawet na poziomie początkowej IaaS, jest umożliwia redukcję kosztów. Za pomocą więcej usług infrastruktury zarządzanych, organizacji można obniżyć inwestycji w sprzęt konserwacja, serwera lub obsługę maszyny Wirtualnej i wdrożenia i zarządzanie infrastrukturą.

Po wprowadzeniu decyzji o przeniesieniu aplikacji w chmurze główną przyczyną Dlaczego możesz wybrać IaaS zamiast bardziej zaawansowane opcje, takie jak PaaS jest po prostu środowiska IaaS będzie bardziej znane. Przeniesienie na podobny do bieżące środowisko, w środowisku lokalnym oferuje niższe nauki, dzięki czemu najszybszy ścieżki do chmury.

Jednak biorąc najszybszy ścieżki do chmury nie oznacza uzyska największe korzyści z o aplikacji w chmurze. Każda organizacja będzie najbardziej znaczących korzyści z migracji chmury poziomach już wprowadzone gotowe do chmury DevOps i PaaS dojrzałości (zoptymalizowana chmury).

Również stało się widoczne, czy aplikacje są łatwiejsze do modernizacji i ponownego projektowania w przyszłości już działające w chmurze, nawet w przypadku IaaS. Dotyczy to częściowo, ponieważ osiągnięto już migracji danych aplikacji. Ponadto organizacji będzie ma zdobytych umiejętności wymaganych do pracy w chmurze, a wprowadzone zmiany w "Kultura chmury".

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>Podczas migracji do IaaS zamiast do PaaS

Kolejnych sekcjach omówiono w nim aplikacje DevOps gotowe do chmury, które najczęściej są oparte na różnych platformach PaaS i usług. Te aplikacje zapewniają większości korzyści wynikające z migracji do chmury.

Jeśli celem jest po prostu przenoszenia istniejących aplikacji w chmurze, najpierw należy zidentyfikować istniejące aplikacje, które wymagają znacznej modyfikacji do uruchamiania w usłudze Azure App Service. Te aplikacje powinny być pierwszym kandydatów.

Następnie jeśli nie chcesz lub nadal nie można przenieść do kontenerów systemu Windows i orchestrators, takich jak sieć szkieletowa usług Azure lub Kubernetes jeszcze, wówczas gdy używasz zwykły VMs (IaaS).

Jednak należy pamiętać, że poprawnie konfigurowania, zabezpieczania i obsługi maszyn wirtualnych wymaga znacznie więcej czasu i doświadczenia IT w porównaniu do na platformie Azure przy użyciu usługi PaaS. Planując maszynach wirtualnych platformy Azure, upewnij się, wziąć pod uwagę nakładu rutynowej konserwacji wymagane do stosowania poprawek, aktualizacji i zarządzania środowiskiem maszyny Wirtualnej. Maszyny wirtualne platformy Azure jest IaaS.

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>Użyj Azure migracji do analizowania i migracji istniejącej aplikacji Azure

Migracja do chmury nie musi być trudne. Jednak w wielu organizacjach mieć trudności z Rozpoczynanie pracy — Aby uzyskać dokładną widoczność do środowiska oraz ścisłej zależności między aplikacje, obciążenia i dane. Bez tego widoczność może być trudne do zaplanowania ścieżkę do przodu. Bez szczegółowych informacji dotyczących co jest wymagane do pomyślnej migracji nie może mieć prawo konwersacje w danej organizacji. Nie wiadomo, wystarczająco o potencjalnie koszt korzyści, lub czy obciążeń można po prostu przyrostu i shift lub wymagają przeróbek istotne, aby pomyślnie przeprowadzić migrację. Nie swoje się, że niechętnie w wielu organizacjach.

[Azure migracji](https://aka.ms/azuremigrate) jest nową usługę, która zawiera wskazówki, szczegółowych informacji i mechanizmów konieczne jest pomocne podczas migracji do usługi Azure. Udostępnia Azure migracji:

- Odnajdywanie i oceny dla lokalnych maszyn wirtualnych

- Mapowanie wbudowanych zależności dla odnajdywania wysokiego zaufania aplikacji wielowarstwowych

- Inteligentnego restrukturyzujące do maszyn wirtualnych platformy Azure

- Raportowania z wytycznymi dotyczącymi korygując potencjalnych problemów ze zgodnością

- Integracja z usługi Azure Management bazy danych dla bazy danych odnajdywania i migracji

Azure migracji daje pewność, że obciążeń można migrować przy minimalnym wpływie biznesową i działają zgodnie z oczekiwaniami na platformie Azure. Wskazówki i odpowiednie narzędzia można uzyskać maksymalny zwrot z inwestycji przy jednoczesnym zapewnieniu, że wydajności i niezawodności wymagania zostały spełnione.

Rysunek 2-2 zawiera wbudowane zależności mapowanie dla wszystkich połączeń serwera i aplikacji z zastosowaniem migracji Azure.

![Pozycjonowanie aplikacje infrastruktury chmury gotowe do wydania](./media/image2-2.png)

> **Rysunek 2-2.** Pozycjonowanie aplikacje infrastruktury chmury gotowe do wydania

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>Użyj usługi Azure Site Recovery, aby przeprowadzić migrację istniejących maszyn wirtualnych do maszyn wirtualnych platformy Azure

W ramach end-to-end [migracji Azure](https://aka.ms/azuremigrate), [usługi Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) to narzędzie, które można łatwo przeprowadzić migrację aplikacji sieci web do maszyn wirtualnych na platformie Azure. Replikowanie lokalnych maszyn wirtualnych i serwerów fizycznych do platformy Azure lub replikować je do lokalizacji lokalnego pomocniczego, można użyć usługi Site Recovery. Możesz nawet replikować obciążeń, do których jest uruchomione na obsługiwanej maszynie Wirtualnej Azure, na lokalnych *funkcji Hyper-V* maszyny Wirtualnej na *VMware* maszyny Wirtualnej, lub na serwerze fizycznym z systemem Windows lub Linux. Replikacji do platformy Azure eliminuje koszty i złożoność obsługi dodatkowego centrum danych.

Usługa Site Recovery jest również specjalnie dla środowisk hybrydowych, które są częściowo lokalne i częściowo na platformie Azure. Usługa Site Recovery pomaga zapewnić ciągłość prowadzenia działalności biznesowej, przechowując aplikacji uruchomionych na maszynach wirtualnych i lokalnych serwerów fizycznych, które są dostępne w przypadku awarii lokacji. Replikowanych obciążeń, które są uruchomione na maszynach wirtualnych i serwerów fizycznych, dzięki czemu są one nadal dostępne w lokalizacji dodatkowej, jeśli lokacja podstawowa jest niedostępna. Odzyskuje obciążeń do lokacji głównej, gdy jest i ponowne uruchomienie.

Rysunek 2 – 3 przedstawiono wykonywanie wielu migracji maszyny Wirtualnej za pomocą usługi Azure Site Recovery.

![Pozycjonowanie aplikacje infrastruktury chmury gotowe do wydania](./media/image2-3.png)

> **Rysunek 2-3.** Pozycjonowanie aplikacje infrastruktury chmury gotowe do wydania

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Arkusz danych migracji Azure**

    [https://aka.ms/azuremigration\_datasheet](https://aka.ms/azuremigration\_datasheet)

- **Migrowanie Azure**

    [http://azuremigrationcenter.com/](http://azuremigrationcenter.com/)

- **Migracja do usługi Azure z usługą Site Recovery**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure)

- **Usług Azure Site Recovery — omówienie**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-overview](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)

- **Migrowanie maszyn wirtualnych w AWS na maszynach wirtualnych platformy Azure**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure)

>[!div class="step-by-step"]
[Poprzednie](index.md)
[dalej](migrate-your-relational-databases-to-azure.md)
