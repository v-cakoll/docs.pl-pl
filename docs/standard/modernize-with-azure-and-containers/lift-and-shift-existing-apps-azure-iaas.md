---
title: Lift- and -shift istniejących aplikacji .NET do usługi Azure IaaS (obsługa infrastruktury chmury)
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów Windows.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 2b987d43f476f261bfdbd1b2af6ca7f792178cf8
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266627"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a>Lift- and -shift istniejących aplikacji .NET do usługi Azure IaaS (obsługa infrastruktury chmury)

> Wizja: Pierwszym krokiem do zmniejszenia inwestycji w środowisku lokalnym, a całkowity koszt sprzętu oraz sieci konserwacji, po prostu ponowne hostowanie istniejących aplikacji w chmurze.

Przed przejściem do *jak* do migrowania istniejących aplikacji do infrastruktury platformy Azure jako usługa (IaaS), jest ważne, aby analizować przyczyny *Dlaczego* chcesz migrować bezpośrednio do modelu IaaS na platformie Azure. Scenariusz na tym poziomie dojrzałości modernizacji zasadniczo jest uruchomienie, przy użyciu maszyn wirtualnych w chmurze, zamiast nadal zarządzane przy użyciu bieżącej, infrastruktury lokalnej.

Jest inny punkt do analizowania *Dlaczego* chcesz przeprowadzić migrację do czystych chmury IaaS zamiast po prostu dodać więcej zaawansowanych usług zarządzanych na platformie Azure. Określić przypadki mogą wymagać IaaS w pierwszej kolejności.

Rysunek 2-1 powoduje umieszczenie aplikacji gotowych do infrastruktury chmury poziomy dojrzałości modernizacji:

![Pozycjonowanie obsługujących metodykę infrastruktury chmury](./media/image2-1.png)

> **Rysunek 2-1.** Pozycjonowanie obsługujących metodykę infrastruktury chmury

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>Dlaczego warto przeprowadzić migrację istniejących aplikacji sieci web platformy .NET do modelu IaaS platformy Azure

Głównym celem migracji do chmury, a nawet w przypadku poziomu początkowej IaaS jest uzyskanie redukcji kosztów. Za pomocą większej liczby usług zarządzana infrastruktura, Twoja organizacja może obniżyć jej inwestycji w sprzęt konserwacja, serwera lub aprowizacją maszyny Wirtualnej i wdrażania i zarządzania infrastrukturą.

Po podjęciu decyzji o przeniesieniu aplikacji w chmurze, głównym powodem, dlaczego możesz wybrać modelu IaaS zamiast bardziej zaawansowane opcje, takie jak PaaS jest po prostu środowiska IaaS będzie lepiej. W środowisku lokalnym, przenoszenie do środowiska, która jest podobna do bieżących, oferuje niższe nauki, co czyni ją najszybszą do chmury.

Biorąc najszybszą do chmury nie oznacza to jednak, uzyskają największe korzyści z konieczności działających w chmurze. Każda organizacja będzie najbardziej znaczące korzyści z migracji do chmury na poziomach już wprowadzone dojrzałości zoptymalizowane pod kątem chmury i natywnych dla chmury.

Również stało się jasne, że aplikacje są łatwiejsze do modernizacji i przekształcanie w przyszłości już działające w chmurze, nawet w przypadku modelu IaaS. Osiągnięto już migracji danych aplikacji. Ponadto Twoja organizacja będzie ma zdobytych umiejętności wymagane do pracy w chmurze ani wprowadzone zmiany w "kultury chmury".

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>Czas migracji do modelu IaaS zamiast do PaaS

W kolejnych sekcjach omówiono w nim aplikacje zoptymalizowane pod kątem chmury, które najczęściej są oparte na PaaS, platform i usług. Aplikacje te zapewniają więcej korzyści z migracji do chmury. 

Jeśli celem jest po prostu przenieść istniejące aplikacje do chmury, najpierw należy zidentyfikować istniejące aplikacje, które nie wymagają znacznej modyfikacji do uruchamiania w usłudze Azure App Service. Te aplikacje, powinien być pierwszy kandydatami do zoptymalizowane pod kątem chmury. 

Następnie dla aplikacji, nadal nie można przenieść do Windows kontenery i PaaS, takich jak usługi App Service lub koordynatorów, takich jak usługi Azure Service Fabric, migracja tych, które mają zwykły prostych maszyn wirtualnych (IaaS). 

Jednak należy pamiętać, że poprawnie Konfigurowanie, zabezpieczanie i obsługa maszyn wirtualnych wymaga znacznie więcej czasu i doświadczenia w zakresie IT w porównaniu do korzystania z usług PaaS platformy Azure. Jeśli rozważasz usługę Azure Virtual Machines, upewnij się, czy należy wziąć pod uwagę rutynowej konserwacji pracę wymaganą do dostarczenia poprawek, aktualizacji, a także zarządzać środowiskiem maszyny Wirtualnej. Usługa Azure Virtual Machines jest IaaS.

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>Usługa Azure Migrate analiza i migracja istniejących aplikacji na platformie Azure

Migracja do chmury nie musi być trudne. Ale w wielu organizacjach wystąpić problemy rozpocząć pracę, aby uzyskać szczegółowy wgląd w środowisku i ścisłej zależności między aplikacje, obciążenia i dane. Bez tego widoczność może być trudne do zaplanowania ścieżka do przodu. Bez szczegółowych informacji dotyczących co to są wymagane do pomyślnej migracji nie może mieć prawo konwersacje w Twojej organizacji. Nie wiem, wystarczy o potencjalnych korzyści, lub czy obciążeń można po prostu lift-and-shift będzie wymagać znaczących dużo przeróbek, aby zostały pomyślnie poddane migracji. Nic dziwnego, że wahaj w wielu organizacjach.

[Usługa Azure Migrate](https://aka.ms/azuremigrate) Nowa usługa, która zawiera wskazówki, szczegółowe informacje i mechanizmy potrzebne, aby pomóc w migracji do platformy Azure. Usługa Azure Migrate oferuje:

- Odnajdowanie i ocenę maszyn wirtualnych w środowisku lokalnym

- Mapowanie zależności wbudowanych odnajdywania o wysokim poziomie pewności aplikacji wielowarstwowych

- Inteligentne, określenie prawidłowego rozmiaru maszyn wirtualnych platformy Azure

- Raportowanie za pomocą wytycznych dotyczących korygowanie działań na podstawie potencjalnych problemów ze zgodnością

- Integracja z usługą Azure Service Management bazy danych dla bazy danych, odnajdowanie i Migrowanie

Usługa Azure Migrate daje pewność, że obciążenia można migracja z minimalnym wpływem na firmy i działają zgodnie z oczekiwaniami na platformie Azure. Za pomocą odpowiednich narzędzi i wskazówek można uzyskać maksymalny zwrot z inwestycji przy jednoczesnym zapewnieniu, że wydajności i niezawodności są spełnione.

Rysunek 2-2 zawiera mapowanie wbudowanych zależności dla wszystkich połączeń serwera i aplikacji, wykonywane przez usługę Azure Migrate.

![Pozycjonowanie obsługujących metodykę infrastruktury chmury](./media/image2-2.png)

> **Rysunek 2-2.** Pozycjonowanie obsługujących metodykę infrastruktury chmury

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>Usługa Azure Site Recovery umożliwia migrowanie istniejących maszyn wirtualnych do maszyn wirtualnych platformy Azure

Jako część end-to-end [usługi Azure Migrate](https://aka.ms/azuremigrate), [usługi Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) to narzędzie, które mogą być łatwo przeprowadzić migrację aplikacji sieci web do maszyn wirtualnych na platformie Azure. Replikowanie lokalnych maszyn wirtualnych i serwerów fizycznych do platformy Azure lub replikować je do lokalizacji dodatkowej w środowisku lokalnym, można użyć Usługa Site Recovery. Możesz nawet replikować obciążenia, uruchomioną na obsługiwanej maszynie Wirtualnej platformy Azure, lokalnie *funkcji Hyper-V* maszyny Wirtualnej na *VMware* maszyny Wirtualnej, lub na serwerze fizycznym Windows lub Linux. Replikacja do platformy Azure, który eliminuje koszt i złożoność obsługi pomocniczego centrum danych.

Usługa Site Recovery jest również specjalnie dla środowisk hybrydowych, które są częściowo lokalnie i częściowo na platformie Azure. Usługa Site Recovery pomaga zapewnić ciągłość przez zapewnienie niezawodnego działania aplikacji, które są uruchomione na maszynach wirtualnych i lokalnych serwerów fizycznych, które są dostępne w przypadku wyłączenia witryny. Replikuje obciążenia, które są uruchomione na maszynach wirtualnych i serwerów fizycznych, co pozwoli im pozostać dostępne w lokalizacji dodatkowej, jeśli lokacja podstawowa jest niedostępna. Obciążenia zostaną odzyskane w lokacji głównej, po upłynięciu i ponowne uruchomienie.

Rysunek 2 – 3 pokazuje wykonywanie wielu migracji maszyn wirtualnych przy użyciu usługi Azure Site Recovery.

![Pozycjonowanie obsługujących metodykę infrastruktury chmury](./media/image2-3.png)

> **Rysunek 2-3.** Pozycjonowanie obsługujących metodykę infrastruktury chmury

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Usługa Azure Migrate arkusz danych**

    [https://aka.ms/azuremigration\_datasheet](https://aka.ms/azuremigration\_datasheet)

- **Usługa Azure Migrate**

    [https://aka.ms/azuremigrate](https://aka.ms/azuremigrate)

- **Centrum migracji platformy Azure**

    [https://azure.microsoft.com/migration/](https://azure.microsoft.com/migration/)

- **Migrowanie na platformę Azure z usługą Site Recovery**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure)

- **Omówienie usługi w usłudze Azure Site Recovery**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-overview](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)

- **Migrowanie maszyn wirtualnych na platformie AWS do maszyn wirtualnych platformy Azure**

    [https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure)

>[!div class="step-by-step"]
>[Poprzednie](index.md)
>[dalej](migrate-your-relational-databases-to-azure.md)
