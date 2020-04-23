---
title: Migrowanie bazy danych programu SQL Server na platformę Azure
description: Dowiedz się, jak migrować bazę danych SQL Server z SQL Server lokalnych na platformę Azure.
ms.topic: how-to
ms.date: 11/15/2017
ms.openlocfilehash: dac35970f2d77e232c2ee1a5e3a1f6e7bfec2317
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2020
ms.locfileid: "82072096"
---
# <a name="migrate-a-sql-server-database-to-azure"></a>Migrowanie bazy danych programu SQL Server na platformę Azure

Ten krótki artykuł zawiera krótki zarys dwóch opcji migrowania bazy danych SQL Server na platformę Azure.

Na platformie Azure dostępne są dwie podstawowe opcje migrowania bazy danych SQL Server produkcyjnych:

1. [SQL Server na maszynach wirtualnych platformy Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-iaas-overview): wystąpienie SQL Server zainstalowane i hostowane na maszynie wirtualnej systemu Windows działającej na platformie Azure, znanej również jako infrastruktura jako usługa (IaaS).
2. [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview): w pełni zarządzana usługa bazy danych SQL na platformie Azure, nazywana także platformą jako usługą (PaaS).

Oba są dostarczane z zaletami i wadami, które należy oszacować przed przeprowadzeniem migracji.

## <a name="get-started"></a>Rozpoczęcie pracy

Poniższe przewodniki dotyczące migracji będą przydatne w zależności od używanej usługi:

* [Migrowanie bazy danych programu SQL Server do programu SQL Server na maszynie wirtualnej platformy Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-migrate-sql)
* [Migracja bazy danych SQL Server do usługi Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-migrate-your-sql-server-database)

Ponadto poniższe linki do zawartości koncepcyjnej pomogą lepiej zrozumieć maszyny wirtualne:

* [Wysoka dostępność i odzyskiwanie po awarii dla SQL Server na platformie Azure Virtual Machines](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-high-availability-dr)
* [Najlepsze rozwiązania w zakresie wydajności dla programu SQL Server w usłudze Azure Virtual Machines](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-performance)
* [Wzorce aplikacji i strategie programowania dla SQL Server na platformie Azure Virtual Machines](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-app-patterns-dev-strategies)

Poniższe linki ułatwią zrozumienie Azure SQL Database lepszego:

* [Tworzenie Azure SQL Database serwerów i baz danych oraz zarządzanie nimi](https://docs.microsoft.com/azure/sql-database/sql-database-servers-databases)
* [Jednostki transakcji bazy danych (DTU) i jednostki transakcji Elastic Database (jednostek eDTU)](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu)
* [Limity zasobów Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits)

## <a name="choosing-iaas-or-paas"></a>Wybieranie IaaS lub PaaS

Podczas oceniania, gdzie należy przeprowadzić migrację bazy danych, ustal, czy IaaS lub PaaS są bardziej odpowiednie dla Ciebie.

**Wybierz SQL Server na maszynach wirtualnych platformy Azure, jeśli:**

* Zamierzasz "podnieść i zmienić" swoją bazę danych i aplikacje z minimalnym brakiem zmian.
* Wolisz mieć pełną kontrolę nad serwerem bazy danych i maszyną wirtualną, na której działa.
* Masz już licencje na SQL Server i system Windows Server, których zamierzasz używać.

**Wybierz usługę Azure SQL Database, jeśli:**

* Zamierzasz przeprowadzić modernizację aplikacji i przeprowadzić migrację do korzystania z innych usług PaaS na platformie Azure.
* Nie chcesz zarządzać serwerem baz danych i maszyną wirtualną, na której jest uruchomiona.
* Nie masz licencji na SQL Server lub systemu Windows Server lub zamierzasz zezwolić na wygaśnięcie licencji.

W poniższej tabeli opisano różnice między każdą usługą opartą na zestawie scenariuszy.

| Scenariusz | SQL Server na maszynach wirtualnych platformy Azure | Azure SQL Database |
|----------|-------------------------|--------------------|
| Migracja | Wymaga minimalnej liczby zmian w bazie danych. | Mogą wymagać zmian w bazie danych, jeśli używasz funkcji niedostępnych w usłudze Azure SQL, zgodnie z opisem w [Data Migration Assistant](https://www.microsoft.com/download/details.aspx?id=53595)lub jeśli masz inne zależności, takie jak pliki wykonywalne lokalnie.|
| Zarządzanie dostępnością, odzyskiwaniem i uaktualnieniami | Dostępność i odzyskiwanie są konfigurowane ręcznie. Uaktualnienia można zautomatyzować za pomocą [VM Scale Sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade). | Automatycznie zarządzane przez Ciebie. |
| Podstawowa konfiguracja systemu operacyjnego | Konfiguracja ręczna. | Automatycznie zarządzane przez Ciebie. |
| Zarządzanie rozmiarem bazy danych | Obsługuje do 64 TB magazynu na wystąpienie SQL Server. | Program obsługuje 4 TB magazynu przed wymaganiem partycji poziomej. |
| Zarządzanie kosztami | Należy zarządzać kosztami licencji SQL Server, kosztami licencji na system Windows Server i kosztami maszyn wirtualnych (w oparciu o rdzenie, pamięć RAM i magazyn). | W przypadku korzystania z puli elastycznej należy zarządzać kosztami usług (w oparciu o [jednostek eDTU lub DTU](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu), magazyn i liczbę baz danych). Należy również zarządzać kosztami umowy SLA. |

Aby dowiedzieć się więcej o różnicach między tymi dwoma, przeczytaj temat Wybieranie opcji SQL Server [w chmurze: Azure SQL Database lub SQL Server na maszynach wirtualnych platformy Azure](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas).

## <a name="faq"></a>Często zadawane pytania

* **Czy nadal mogę używać narzędzi takich jak SQL Server Management Studio i SQL Server Reporting Services (SSRS) z SQL Server na maszynach wirtualnych platformy Azure lub w Azure SQL Database?**

    Tak! Wszystkie narzędzia Microsoft SQL działają z obiema usługami. Usługa SSRS nie jest częścią Azure SQL Database, ale zaleca się jej uruchomienie na maszynie wirtualnej platformy Azure, a następnie wskazanie jej w wystąpieniu bazy danych.

* **Chcę go PaaS, ale nie mam pewności, czy moja baza danych jest zgodna. Czy istnieją narzędzia do pomocy?**

    Tak. [Data Migration Assistant](https://www.microsoft.com/download/details.aspx?id=53595) jest narzędziem, które jest używane w ramach migracji do Azure SQL Database. [Azure Database Migration Service](https://azure.microsoft.com/campaigns/database-migration/) to usługa w wersji zapoznawczej, której można użyć dla IaaS lub PaaS.

* **Czy mogę oszacować koszty?**

    Tak. [Kalkulator cen platformy Azure](https://azure.microsoft.com/pricing/calculator/) może służyć do szacowania kosztów dla wszystkich usług platformy Azure, w tym maszyn wirtualnych i usług baz danych.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Wybierz odpowiednią opcję hostingu platformy Azure](choose.md)
