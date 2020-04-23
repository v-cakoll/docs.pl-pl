---
title: Migrowanie bazy danych programu SQL Server na platformę Azure
description: Dowiedz się, jak przeprowadzić migrację bazy danych programu SQL Server z lokalnego programu SQL Server na platformę Azure.
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

Ten krótki artykuł zawiera krótki zarys dwóch opcji migracji bazy danych programu SQL Server na platformę Azure.

Platforma Azure ma dwie podstawowe opcje migracji produkcyjnej bazy danych programu SQL Server:

1. [SQL Server na maszynach wirtualnych platformy Azure: wystąpienie](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-iaas-overview)programu SQL Server zainstalowane i hostowane na maszynie wirtualnej systemu Windows uruchomionej na platformie Azure, znanej również jako Infrastruktura jako usługa (IaaS).
2. [Usługa Azure SQL Database:](https://docs.microsoft.com/azure/sql-database/sql-database-technical-overview)w pełni zarządzana usługa platformy Azure bazy danych SQL, znana również jako Platforma jako usługa (PaaS).

Oba pochodzą z plusy i minusy, które trzeba będzie ocenić przed migracją.

## <a name="get-started"></a>Rozpoczęcie pracy

Przydatne będą następujące przewodniki dotyczące migracji, w zależności od używanej usługi:

* [Migrowanie bazy danych programu SQL Server do programu SQL Server na maszynie wirtualnej platformy Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-migrate-sql)
* [Migracja bazy danych SQL Server do usługi Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-migrate-your-sql-server-database)

Ponadto następujące łącza do zawartości koncepcyjnej pomogą Ci lepiej zrozumieć maszyny wirtualne:

* [Wysoka dostępność i odzyskiwanie po awarii dla programu SQL Server na maszynach wirtualnych platformy Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-high-availability-dr)
* [Najlepsze rozwiązania w zakresie wydajności dla programu SQL Server w usłudze Azure Virtual Machines](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-performance)
* [Wzorce aplikacji i strategie rozwoju dla programu SQL Server w maszynach wirtualnych platformy Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-app-patterns-dev-strategies)

Poniższe łącza pomogą Ci lepiej zrozumieć usługę Azure SQL Database:

* [Tworzenie serwerów i baz danych usługi Azure SQL Database i zarządzanie nimi](https://docs.microsoft.com/azure/sql-database/sql-database-servers-databases)
* [Jednostki transakcji bazy danych (DTU) i elastyczne jednostki transakcyjne bazy danych (eDTU)](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu)
* [Limity zasobów usługi Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-resource-limits)

## <a name="choosing-iaas-or-paas"></a>Wybór IaaS lub PaaS

Podczas oceny, gdzie należy przeprowadzić migrację bazy danych, należy określić, czy usługi IaaS lub PaaS są dla Ciebie bardziej odpowiednie.

**Wybierz program SQL Server na maszynach wirtualnych platformy Azure, jeśli:**

* Szukasz "lift and shift" bazy danych i aplikacji z minimalnym lub bez zmian.
* Wolisz mieć pełną kontrolę nad serwerem bazy danych i maszyną wirtualną, na której działa.
* Masz już licencje SQL Server i Windows Server, których zamierzasz używać.

**Wybierz usługę Azure SQL Database, jeśli:**

* Chcesz zmodernizować aplikacje i migracji do korzystania z innych usług PaaS na platformie Azure.
* Nie chcesz zarządzać serwerem bazy danych i maszyną wirtualną, na której działa.
* Nie masz licencji sql server lub windows server lub zamierzasz pozwolić licencjom, które wygasły.

W poniższej tabeli opisano różnice między każdą usługą na podstawie zestawu scenariuszy.

| Scenariusz | Sql Server na maszynach wirtualnych platformy Azure | Azure SQL Database |
|----------|-------------------------|--------------------|
| Migracja | Wymaga minimalnych zmian w bazie danych. | Może wymagać zmian w bazie danych, jeśli używasz funkcji niedostępnych w usłudze Azure SQL, zgodnie z [ustaleniami Asystenta migracji danych](https://www.microsoft.com/download/details.aspx?id=53595)lub jeśli masz inne zależności, takie jak lokalnie zainstalowane pliki wykonywalne.|
| Zarządzanie dostępnością, odzyskiwaniem i uaktualnieniami | Dostępność i odzyskiwanie są konfigurowane ręcznie. Uaktualnienia można zautomatyzować za pomocą [zestawów skalowania maszyn wirtualnych.](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade) | Automatycznie zarządzane dla Ciebie. |
| Podstawowa konfiguracja systemu operacyjnego | Konfiguracja ręczna. | Automatycznie zarządzane dla Ciebie. |
| Zarządzanie rozmiarem bazy danych | Obsługuje do 64 TB magazynu na wystąpienie programu SQL Server. | Obsługuje 4 TB pamięci masowej przed koniecznością partycji poziomej. |
| Zarządzanie kosztami | Musisz zarządzać kosztami licencji programu SQL Server, kosztami licencji systemu Windows Server i kosztami maszyn wirtualnych (na podstawie rdzeni, pamięci RAM i magazynu). | Należy zarządzać kosztami usługi (na podstawie [eDTU lub DTU](https://docs.microsoft.com/azure/sql-database/sql-database-what-is-a-dtu), magazynu i liczby baz danych, jeśli używasz puli elastycznej). Należy również zarządzać kosztem dowolnej umowy SLA. |

Aby dowiedzieć się więcej o różnicach między tymi dwoma, przeczytaj artykuł Wybieranie opcji programu SQL Server w chmurze: [Usługa Azure SQL Database lub SQL Server na maszynach wirtualnych platformy Azure.](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas)

## <a name="faq"></a>Często zadawane pytania

* **Czy nadal można używać narzędzi, takich jak SQL Server Management Studio i SQL Server Reporting Services (SSRS) z programem SQL Server na maszynach wirtualnych platformy Azure lub w bazie danych SQL Azure?**

    Tak! Wszystkie narzędzia SQL firmy Microsoft działają z obiema usługami. SSRS nie jest częścią usługi Azure SQL Database, choć i zaleca się, aby uruchomić go w maszynie Wirtualnej platformy Azure, a następnie wskaż go do wystąpienia bazy danych.

* **Chcę iść PaaS, ale nie jestem pewien, czy moja baza danych jest zgodna. Czy istnieją narzędzia, które pomogą?**

    Tak. [Asystent migracji danych](https://www.microsoft.com/download/details.aspx?id=53595) to narzędzie używane jako część migracji do bazy danych SQL platformy Azure. [Usługa migracji bazy danych azure](https://azure.microsoft.com/campaigns/database-migration/) to usługa w wersji zapoznawczej, której można używać w usługach IaaS lub PaaS.

* **Czy mogę oszacować koszty?**

    Tak. [Kalkulator cen platformy Azure](https://azure.microsoft.com/pricing/calculator/) może służyć do szacowania kosztów dla wszystkich usług platformy Azure, w tym maszyn wirtualnych i usług bazy danych.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Wybierz odpowiednią opcję hostingu platformy Azure](choose.md)
