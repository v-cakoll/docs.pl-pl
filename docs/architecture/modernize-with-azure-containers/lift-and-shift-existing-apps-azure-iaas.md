---
title: Podnieś i Przenieś istniejące aplikacje .NET do usługi Azure IaaS (infrastruktura chmury — gotowe)
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows.
ms.date: 04/28/2018
ms.openlocfilehash: e25ddbf9b6e62c264f3f4d4580d7df3553d262ea
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660739"
---
# <a name="lift-and-shift-existing-net-apps-to-azure-iaas-cloud-infrastructure-ready"></a>Podnieś i Przenieś istniejące aplikacje .NET do usługi Azure IaaS (infrastruktura chmury — gotowe)

> Została Pierwszym krokiem jest zredukowanie inwestycji lokalnych i łącznego kosztu konserwacji sprzętu i sieci, a po prostu ponowne hostowanie istniejących aplikacji w chmurze.

Przed przystąpieniem do migrowania istniejących aplikacji do platformy Azure infrastruktura jako usługa (IaaS), ważne jest przeanalizowanie przyczyn, dla których chcesz migrować bezpośrednio do IaaS na platformie Azure. Scenariusz na tym poziomie operacji modernizacji zasadniczo ma rozpocząć korzystanie z maszyn wirtualnych w chmurze, zamiast korzystać z bieżącej infrastruktury lokalnej.

Innym punktem do przeanalizowania jest to, że warto przeprowadzić migrację do czystego IaaS chmury, zamiast dodawać bardziej zaawansowane usługi zarządzane na platformie Azure. Określ, które przypadki mogą wymagać IaaS w pierwszym miejscu.

Rysunek 2-1. pozycje infrastruktury chmurowej — gotowe aplikacje na poziomach dojrzałości modernizacji:

![Pozycjonowanie aplikacji gotowych do infrastruktury chmurowej](./media/image2-1.png)

> **Rysunek 2-1.** Pozycjonowanie aplikacji gotowych do infrastruktury chmurowej

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>Dlaczego należy migrować istniejące aplikacje sieci Web platformy .NET do usługi Azure IaaS

Głównym powodem migracji do chmury nawet na początkowym poziomie IaaS jest osiągnięcie obniżenia kosztów. Korzystając z większej liczby zarządzanych usług infrastruktury, organizacja może obniżyć swoją inwestycję w konserwację sprzętu, Inicjowanie obsługi administracyjnej serwera lub maszyny wirtualnej oraz zarządzanie infrastrukturą.

Po podjęciu decyzji o przeniesieniu aplikacji do chmury główną przyczyną może być wybranie IaaS zamiast bardziej zaawansowanych opcji, takich jak PaaS, że środowisko IaaS będzie bardziej znane. Przejście do środowiska podobnego do bieżącego środowiska lokalnego oferuje niższą krzywą uczenia, co sprawia, że jest to najszybsza ścieżka do chmury.

Korzystanie z najszybszych ścieżek do chmury nie oznacza jednak, że będziesz mieć największe korzyści z używania aplikacji w chmurze. Każda organizacja uzyska najbardziej znaczące korzyści z migracji do chmury w już wprowadzonych poziomach płatności w chmurze zoptymalizowanych pod kątem chmury i w chmurze.

Okazało się również, że aplikacje są łatwiejsze do modernizacji i w przyszłości, gdy są już uruchomione w chmurze, nawet w IaaS. Migracja danych aplikacji została już osiągnięta. Ponadto organizacja uzyska umiejętności wymagane do pracy w chmurze i przeprowadzi zmianę w działaniu w "kulturze chmurowej".

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>Kiedy należy migrować do IaaS zamiast PaaS

W następnych sekcjach omówiono aplikacje zoptymalizowane pod kątem chmury, które są głównie oparte na platformach i usługach PaaS. Te aplikacje zapewniają największą korzyść z migracji do chmury. 

Jeśli celem jest po prostu przeniesienie istniejących aplikacji do chmury, najpierw Zidentyfikuj istniejące aplikacje, które nie wymagają znaczącej modyfikacji do uruchomienia w Azure App Service. Aplikacje te powinny być pierwszymi kandydatami do zoptymalizowania pod kątem chmury. 

Następnie w przypadku aplikacji, które nadal nie mogą przejść do kontenerów systemu Windows i PaaS takich jak App Service lub Orchestrator, takich jak usługa Azure Kubernetes, należy przeprowadzić migrację do prostych zwykłych maszyn wirtualnych (IaaS). 

Należy jednak pamiętać, że prawidłowe Konfigurowanie, zabezpieczanie i konserwowanie maszyn wirtualnych wymaga znacznie więcej czasu i wiedza IT w porównaniu z użyciem usług PaaS Services na platformie Azure. Jeśli rozważasz platformę Azure Virtual Machines, pamiętaj, aby wziąć pod uwagę trwającą pracę konserwacyjną wymaganą na potrzeby poprawek, aktualizacji i zarządzania środowiskiem maszyn wirtualnych. Virtual Machines platformy Azure to IaaS.

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>Używanie Azure Migrate do analizowania i migrowania istniejących aplikacji na platformę Azure

Migrowanie do chmury nie musi być trudne. Jednak wiele organizacji bardzo się zapoznaje z rozpoczęciem — Aby uzyskać wgląd w środowisko i ścisłe współzależności między aplikacjami, obciążeniami i danymi. Bez tego widoczność może być trudne do zaplanowania ścieżki do przodu. Bez szczegółowych informacji o tym, co jest wymagane do pomyślnej migracji, nie możesz mieć odpowiednich konwersacji w organizacji. Nie masz wystarczającej pewności dotyczącej potencjalnych korzyści z kosztów lub czy obciążenia mogą jedynie podnieść i przesunąć lub wymagać znaczącej ponownej migracji. Nie niechętnie zezwalają wielu organizacji.

[Azure Migrate](https://aka.ms/azuremigrate) to nowa usługa, która zapewnia wskazówki, szczegółowe informacje i mechanizmy potrzebne do przeprowadzenia migracji do platformy Azure. Azure Migrate zapewnia:

- Odnajdywanie i ocenianie lokalnych maszyn wirtualnych

- Wbudowane mapowanie zależności dla odnajdywania aplikacji wielowarstwowych

- Inteligentne Ustawianie wielkości dla maszyn wirtualnych platformy Azure

- Raportowanie zgodności z wytycznymi dotyczącymi potencjalnych problemów korygowaniem

- Integracja z usługą zarządzania bazami danych platformy Azure na potrzeby odnajdywania i migracji bazy danych

Azure Migrate zapewnia pewność, że obciążenia mogą być migrowane z minimalnym wpływem na firmę i działają zgodnie z oczekiwaniami na platformie Azure. Dzięki odpowiednim narzędziom i wskazówkom można osiągnąć maksymalne zwroty inwestycji przy jednoczesnym zapewnieniu spełnienia krytycznych wymagań dotyczących wydajności i niezawodności.

Na rysunku 2-2 przedstawiono wbudowane mapowanie zależności dla wszystkich połączeń serwera i aplikacji wykonywanych przez Azure Migrate.

![Pozycjonowanie aplikacji gotowych do infrastruktury chmurowej](./media/image2-2.png)

> **Rysunek 2-2.** Pozycjonowanie aplikacji gotowych do infrastruktury chmurowej

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>Używanie Azure Site Recovery do migrowania istniejących maszyn wirtualnych do maszyn wirtualnych platformy Azure

W ramach kompleksowej [Azure Migrate](https://aka.ms/azuremigrate) [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) jest narzędziem, za pomocą którego można łatwo migrować aplikacje sieci Web do maszyn wirtualnych na platformie Azure. Za pomocą Site Recovery można replikować lokalne maszyny wirtualne i serwery fizyczne do platformy Azure lub replikować je do pomocniczej lokalizacji lokalnej. Można nawet replikować obciążenia uruchomione na obsługiwanej maszynie wirtualnej platformy Azure, na lokalnej maszynie wirtualnej *funkcji Hyper-V* , na maszynie wirtualnej *VMware* lub na serwerze fizycznym z systemem Windows lub Linux. Replikacja na platformę Azure eliminuje koszt i złożoność utrzymywania dodatkowego centrum danych.

Site Recovery jest również przeznaczony dla środowisk hybrydowych, które są częściowo lokalne i częściowo na platformie Azure. Site Recovery pomaga zapewnić ciągłość działania, utrzymując aplikacje działające na maszynach wirtualnych i lokalnych serwerach fizycznych, gdy lokacja ulegnie awarii. Replikuje obciążenia działające na maszynach wirtualnych i serwerach fizycznych, dzięki czemu są one nadal dostępne w lokalizacji dodatkowej, Jeśli lokacja główna jest niedostępna. Program odzyskuje obciążenia do lokacji głównej, gdy zostanie ona uruchomiona ponownie.

Rysunek 2-3 przedstawia wykonywanie wielu migracji maszyn wirtualnych przy użyciu Azure Site Recovery.

![Pozycjonowanie aplikacji gotowych do infrastruktury chmurowej](./media/image2-3.png)

> **Rysunek 2-3.** Pozycjonowanie aplikacji gotowych do infrastruktury chmurowej

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Arkusz danych Azure Migrate**

    <https://aka.ms/azuremigration\_datasheet>

- **Azure Migrate**

    <https://aka.ms/azuremigrate>

- **centrum migracji platformy Azure**

    <https://azure.microsoft.com/migration/>

- **Migrowanie na platformę Azure za pomocą Site Recovery**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure>

- **Przegląd usługi Azure Site Recovery**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-overview>

- **Migrowanie maszyn wirtualnych w AWS do maszyn wirtualnych platformy Azure**

    <https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure>

>[!div class="step-by-step"]
>[Poprzedni](index.md)Następny
>[](migrate-your-relational-databases-to-azure.md) <!-- Next Chapter -->
