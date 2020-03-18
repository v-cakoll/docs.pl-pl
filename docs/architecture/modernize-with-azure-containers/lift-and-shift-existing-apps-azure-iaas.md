---
title: Przenoszenie i przenoszenie istniejących aplikacji .NET do usługi Azure IaaS (Cloud Infrastructure-Ready)
description: Zmodernizuj istniejące aplikacje .NET za pomocą usługi Azure Cloud i kontenerów systemu Windows.
ms.date: 04/28/2018
ms.openlocfilehash: c7638a034dbb27baea1b097bdb66175bfb5a71f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73089636"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a>Przenoszenie i przenoszenie istniejących aplikacji .NET do usługi Azure IaaS (Cloud Infrastructure-Ready)

> Wizja: W pierwszej kolejności, aby zmniejszyć inwestycje lokalne i całkowity koszt konserwacji sprzętu i sieci, po prostu ponownie hostuj istniejące aplikacje w chmurze.

Przed *przejściem* do sposobu migracji istniejących aplikacji do platformy infrastruktury platformy Azure jako usługi (IaaS), ważne jest, aby przeanalizować *przyczyny, dla których* chcesz przeprowadzić migrację bezpośrednio do usługi IaaS na platformie Azure. Scenariusz na tym poziomie dojrzałości modernizacji zasadniczo jest rozpoczęcie korzystania z maszyn wirtualnych w chmurze, zamiast nadal używać bieżącej infrastruktury lokalnej.

Innym punktem do analizy jest *dlaczego* warto przeprowadzić migrację do czystej chmury IaaS zamiast po prostu dodawać bardziej zaawansowane usługi zarządzane na platformie Azure. Określ, jakie przypadki mogą wymagać IaaS w pierwszej kolejności.

Rysunek 2-1 umieszcza aplikacje gotowe do pracy w chmurze na poziomie dojrzałości modernizacji:

![Pozycjonowanie aplikacji gotowych do pracy w chmurze](./media/image2-1.png)

**Rysunek 2-1.** Pozycjonowanie aplikacji gotowych do pracy w chmurze

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>Dlaczego migracja istniejących aplikacji sieci Web .NET do usługi Azure IaaS

Głównym powodem migracji do chmury, nawet na początkowym poziomie IaaS, jest osiągnięcie redukcji kosztów. Korzystając z bardziej zarządzanych usług infrastruktury, organizacja może obniżyć swoje inwestycje w konserwację sprzętu, inicjowanie obsługi administracyjnej i wdrażania serwerów lub maszyn wirtualnych oraz zarządzanie infrastrukturą.

Po podjęciu decyzji o przeniesieniu aplikacji do chmury, głównym powodem, dla którego możesz wybrać IaaS zamiast bardziej zaawansowanych opcji, takich jak PaaS, jest po prostu to, że środowisko IaaS będzie bardziej znane. Przejście do środowiska podobnego do bieżącego środowiska lokalnego oferuje niższą krzywą uczenia się, co sprawia, że jest to najszybsza ścieżka do chmury.

Jednak podjęcie najszybszej ścieżki do chmury nie oznacza, że uzyskasz największe korzyści z uruchamiania aplikacji w chmurze. Każda organizacja uzyska największe korzyści z migracji do chmury na już wprowadzonych poziomach dojrzałości zoptymalizowanych pod kątem chmury i cloud-native.

Stało się również oczywiste, że aplikacje są łatwiejsze do modernizacji i rearchitect w przyszłości, gdy są one już uruchomione w chmurze, nawet na IaaS. Migracja danych aplikacji została już osiągnięta. Ponadto twoja organizacja zdobędzie umiejętności wymagane do pracy w chmurze i przeszła do pracy w "kulturze chmury".

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>Kiedy przeprowadzić migrację do IaaS zamiast do PaaS

W następnych sekcjach omówiono aplikacje zoptymalizowane pod kątem chmury, które są głównie oparte na platformach i usługach PaaS. Te aplikacje dają największe korzyści z migracji do chmury.

Jeśli twoim celem jest po prostu przenieść istniejące aplikacje do chmury, najpierw zidentyfikować istniejące aplikacje, które nie wymagają znacznych modyfikacji do uruchomienia w usłudze Azure App Service. Te aplikacje powinny być pierwszymi kandydatami do zoptymalizowane pod kątem chmury.

Następnie w przypadku aplikacji, które nadal nie mogą przenosić się do kontenerów systemu Windows i paaS, takich jak usługa aplikacji lub koordynatorów, takich jak usługa Azure Kubernetes, migruj te do prostych zwykłych maszyn wirtualnych (IaaS).

Należy jednak pamiętać, że prawidłowe konfigurowanie, zabezpieczanie i obsługa maszyn wirtualnych wymaga znacznie więcej czasu i wiedzy inwakcesji IT w porównaniu z korzystaniem z usług PaaS na platformie Azure. Jeśli rozważasz maszyny wirtualne platformy Azure, upewnij się, że bierzesz pod uwagę bieżące wysiłki związane z konserwacją wymagane do stosowania poprawek, aktualizacji i zarządzania środowiskiem maszyn wirtualnych. Maszyny wirtualne platformy Azure to IaaS.

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>Program Azure Migrate umożliwia analizowanie i migrowanie istniejących aplikacji na platformę Azure

Migracja do chmury nie musi być trudna. Jednak wiele organizacji ma trudności z rozpoczęciem pracy — aby uzyskać głęboki wgląd w środowisko i ścisłe współzależności między aplikacjami, obciążeniami i danymi. Bez tej widoczności planowanie ścieżki do przodu może być trudne. Bez szczegółowych informacji na temat tego, co jest wymagane do pomyślnej migracji, nie można mieć odpowiednich konwersacji w organizacji. Nie wiesz wystarczająco dużo o potencjalnych korzyściach kosztowych lub czy obciążenia mogą po prostu podnieść i zmienić lub wymagać znacznych przeróbek, aby pomyślnie przeprowadzić migrację. Nic dziwnego, że wiele organizacji waha się.

[Azure Migrate](https://aka.ms/azuremigrate) to nowa usługa, która zapewnia wskazówki, szczegółowe informacje i mechanizmy potrzebne do pomocy w migracji na platformę Azure. Usługa Azure Migrate zapewnia:

- Odnajdowanie i ocena lokalnych maszyn wirtualnych

- Wbudowane mapowanie zależności dla odnajdowania aplikacji wielowarstwowych o wysokim poziomie zaufania

- Inteligentne odpowiednie dostosowywanie maszyn wirtualnych platformy Azure

- Raportowanie zgodności z wytycznymi dotyczącymi rozwiązywania potencjalnych problemów

- Integracja z usługą Azure Database Management Service do odnajdowania i migracji baz danych

Usługa Azure Migrate daje pewność, że obciążenia mogą być migrowane przy minimalnym wpływie na firmę i działać zgodnie z oczekiwaniami na platformie Azure. Dzięki odpowiednim narzędziom i wskazówkom można osiągnąć maksymalny zwrot z inwestycji, zapewniając jednocześnie, że krytyczne potrzeby w zakresie wydajności i niezawodności są zaspokojone.

Rysunek 2-2 przedstawia wbudowane mapowanie zależności dla wszystkich połączeń serwera i aplikacji wykonywanych przez usługę Azure Migrate.

![Pozycjonowanie aplikacji gotowych do pracy w chmurze](./media/image2-2.png)

**Rysunek 2-2.** Pozycjonowanie aplikacji gotowych do pracy w chmurze

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>Użyj usługi Azure Site Recovery do migracji istniejących maszyn wirtualnych na maszyny wirtualne platformy Azure

W ramach end-to-end [Azure Migrate,](https://aka.ms/azuremigrate) [Usługa Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) to narzędzie, za pomocą którego można łatwo migrować aplikacje sieci web do maszyn wirtualnych na platformie Azure. Za pomocą usługi Site Recovery można replikować lokalne maszyny wirtualne i serwery fizyczne na platformie Azure lub replikować je do lokalizacji dodatkowej w środowisku lokalnym. Można nawet replikować obciążenie uruchomione na obsługiwanej maszynie wirtualnej platformy Azure, lokalnej maszynie *wirtualnej funkcji Hyper-V,* na maszynie wirtualnej *VMware* lub na serwerze fizycznym systemu Windows lub Linux. Replikacja do platformy Azure pozwala wyeliminować koszty i złożoność związane z utrzymywaniem dodatkowego centrum danych.

Usługa Site Recovery jest również specjalnie dla środowisk hybrydowych, które są częściowo lokalne, a częściowo na platformie Azure. Usługa Site Recovery pomaga zapewnić ciągłość działania, udostępniając aplikacje uruchomione na maszynach wirtualnych i lokalnych serwerach fizycznych, jeśli witryna uniewinnie. Replikuje obciążeń, które są uruchomione na maszynach wirtualnych i serwerach fizycznych, dzięki czemu pozostają one dostępne w lokalizacji dodatkowej, jeśli lokacja główna nie jest dostępna. Gdy lokacja główna zostanie ponowne uruchomiona, obciążenia zostaną odzyskane w tej lokacji.

Rysunek 2-3 przedstawia wykonywanie wielu migracji maszyn wirtualnych przy użyciu usługi Azure Site Recovery.

![Pozycjonowanie aplikacji gotowych do pracy w chmurze](./media/image2-3.png)

**Rysunek 2-3.** Pozycjonowanie aplikacji gotowych do pracy w chmurze

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Arkusz danych migracji platformy Azure**

    <https://aka.ms/azuremigration\_datasheet>

- **Azure Migrate**

    <https://aka.ms/azuremigrate>

- **Centrum migracji platformy Azure**

    <https://azure.microsoft.com/migration/>

- **Migrowanie na platformę Azure za pomocą usługi Site Recovery**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure>

- **Omówienie usługi Azure Site Recovery**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-overview>

- **Migrowanie maszyn wirtualnych w usłudze AWS do maszyn wirtualnych platformy Azure**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure>

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[następny](migrate-your-relational-databases-to-azure.md) <!-- Next Chapter -->
