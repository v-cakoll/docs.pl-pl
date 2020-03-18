---
title: Migrowanie relacyjnych baz danych na platformę Azure
description: Modernizacja istniejących aplikacji .NET za pomocą usługi Azure Cloud i kontenerów systemu Windows | migrowanie relacyjnych baz danych na platformę Azure
ms.date: 04/28/2018
ms.openlocfilehash: efd1548c3f74fc27450f4949d71a1c4d61907ba5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73093612"
---
# <a name="migrate-your-relational-databases-to-azure"></a>Migrowanie relacyjnych baz danych na platformę Azure

Wizja: Platforma Azure oferuje najbardziej kompleksową migrację bazy danych.

Na platformie Azure można migrować serwery bazy danych bezpośrednio do maszyn wirtualnych IaaS (pure lift and shift) lub można przeprowadzić migrację do usługi Azure SQL Database, aby uzyskać dodatkowe korzyści. Usługa Azure SQL Database oferuje zarządzane wystąpienie i pełne opcje bazy danych jako usługi (DBaaS). Rysunek 3-1 przedstawia wiele ścieżek migracji relacyjnych bazy danych dostępnych na platformie Azure.

![Ścieżki migracji bazy danych na platformie Azure](./media/image3-1.png)

**Rysunek 3-1.** Ścieżki migracji bazy danych na platformie Azure

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>Kiedy przeprowadzić migrację do wystąpienia zarządzanego bazy danych SQL platformy Azure

W większości przypadków wystąpienie zarządzane bazy danych SQL platformy Azure będzie najlepszym rozwiązaniem, aby wziąć pod uwagę podczas migracji danych na platformę Azure. Jeśli przeprowadzasz migrację baz danych programu SQL Server i potrzebujesz prawie 100% pewności, że nie trzeba zmieniać projektu aplikacji ani wprowadzać zmian w kodzie dostępu do danych lub danych, wybierz funkcję Wystąpienia zarządzanego bazy danych SQL platformy Azure.

Wystąpienie zarządzane bazy danych SQL platformy Azure jest najlepszym rozwiązaniem, jeśli masz dodatkowe wymagania dotyczące funkcji na poziomie wystąpienia programu SQL Server lub wymagania dotyczące izolacji wykraczające poza funkcje udostępniane w standardowej bazie danych SQL platformy Azure (model pojedynczej bazy danych). Ten ostatni jest najbardziej paas zorientowanych wybór, ale nie oferuje te same funkcje, jak w przypadku tradycyjnego serwera SQL. Migracja może pojawić się na powierzchni.

Na przykład organizacja, która dokonała głębokich inwestycji w możliwości programu SQL Server na poziomie wystąpienia, skorzystałaby z migracji do wystąpienia zarządzanego SQL. Przykłady funkcji programu SQL Server na poziomie wystąpienia obejmują integrację programu SQL common language runtime (CLR), program SQL Server Agent i kwerendy między bazami danych. Obsługa tych funkcji nie jest dostępna w standardowej bazie danych SQL platformy Azure (model pojedynczej bazy danych).

Organizacja, która działa w branży o wysokim stopniu regulacji i która musi utrzymywać izolację ze względów bezpieczeństwa, może również skorzystać z wybrania modelu wystąpienia zarządzanego SQL.

Wystąpienie zarządzane w usłudze Azure SQL Database ma następujące cechy:

- Izolacja zabezpieczeń za pośrednictwem sieci wirtualnej platformy Azure

- Zgodność powierzchni aplikacji z tymi funkcjami:

  - Agent programu SQL Server i profiler programu SQL Server

  - Odwołania i kwerendy między bazami danych, sql CLR, replikacja, przechwytywanie danych zmian (CDC) i Service Broker

- Rozmiary baz danych do 35 TB

- Migracja minimalnych przestojów z tymi funkcjami:

  - Azure Database Migration Service

  - Natywna kopia zapasowa i przywracanie oraz wysyłanie dzienników

Dzięki tym możliwościom podczas migracji istniejących baz danych aplikacji do bazy danych SQL platformy Azure model wystąpienia zarządzanego oferuje prawie 100% korzyści z paas dla programu SQL Server. Wystąpienie zarządzane to środowisko programu SQL Server, w którym nadal korzystasz z funkcji na poziomie wystąpienia bez zmiany projektu aplikacji.

Wystąpienie zarządzane jest prawdopodobnie najlepiej dopasowane dla przedsiębiorstw, które obecnie korzystają z programu SQL Server i które wymagają elastyczności w zabezpieczeniach sieci w chmurze. To jak posiadanie prywatnej sieci wirtualnej dla baz danych SQL.

## <a name="when-to-migrate-to-azure-sql-database"></a>Kiedy przeprowadzić migrację do bazy danych SQL platformy Azure

Jak wspomniano, standardowa baza danych SQL platformy Azure jest w pełni zarządzanym, relacyjnym dbaas. Baza danych SQL zarządza obecnie milionami produkcyjnych baz danych w 38 centrach danych na całym świecie. Obsługuje szeroki zakres aplikacji i obciążeń, od zarządzania prostymi danymi transakcyjnymi po dostarczanie najbardziej wymagających danych aplikacji o znaczeniu krytycznym, które wymagają zaawansowanego przetwarzania danych w skali globalnej.

Ze względu na pełne funkcje PaaS, lepsze ceny i ostatecznie niższy koszt, należy przejść do standardowej bazy danych SQL platformy Azure jako "domyślnie wybór", jeśli masz aplikację, która używa podstawowych, standardowych baz danych SQL i żadnych dodatkowych funkcji wystąpienia. Funkcje programu SQL Server, takie jak integracja z sql CLR, program SQL Server Agent i kwerendy między bazami danych, nie są obsługiwane w standardowej bazie danych SQL platformy Azure. Te funkcje są dostępne tylko w modelu wystąpienia zarządzanego bazy danych Azure SQL.

Usługa Azure SQL Database jest jedyną inteligentną usługą bazy danych w chmurze, która jest stworzona dla deweloperów aplikacji. Jest to również jedyna usługa bazy danych w chmurze, która skaluje się w locie, bez przestojów, aby pomóc Ci wydajnie dostarczać aplikacje wielodostępne. Ostatecznie usługa Azure SQL Database pozostawia więcej czasu na innowacje i skraca czas wprowadzania na rynek. Możesz tworzyć bezpieczne aplikacje i łączyć się z bazą danych SQL przy użyciu preferowanych języków i platform.

Usługa Azure SQL Database oferuje następujące korzyści:

- Wbudowana inteligencja (uczenie maszynowe), która uczy się i dostosowuje do aplikacji

- Inicjowanie obsługi administracyjnej bazy danych na żądanie

- Szeroka gama ofert dla wszystkich obciążeń

- 99.99% dostępność Umowa SLA, zero konserwacji

- Usługi replikacji i przywracania geograficznego w celu ochrony danych

- Funkcja przywracania czasu punktu bazy danych SQL platformy Azure

- Zgodność z programem SQL Server 2016, w tym hybryda i migracja

Standardowa baza danych SQL platformy Azure jest bliżej PaaS niż wystąpienie zarządzane bazy danych AZURE SQL. Preferuj standardową bazę danych SQL platformy Azure, ponieważ otrzymasz więcej korzyści z zarządzanej chmury. Jednak usługa Azure SQL Database ma pewne kluczowe różnice w porównaniu z zwykłymi i lokalnymi wystąpieniami programu SQL Server. W zależności od wymagań bazy danych istniejącej aplikacji oraz wymagań i zasad przedsiębiorstwa może to nie być najlepszy wybór podczas planowania migracji do chmury.

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>Kiedy przenieść oryginalny RDBMS na maszynę wirtualną (IaaS)

Jedną z opcji migracji jest przeniesienie oryginalnego relacyjnego systemu zarządzania bazami danych (RDBMS), w tym Oracle, IBM DB2, MySQL, PostgreSQL lub SQL Server, na podobny serwer uruchomiony na maszynie wirtualnej platformy Azure. Jeśli masz istniejące aplikacje, które wymagają najszybszej migracji do chmury przy minimalnych zmianach lub w ogóle nie wprowadzają zmian, bezpośrednia migracja do Usługi IaaS w chmurze może być uczciwą opcją. Może nie jest to najlepszy sposób na wykorzystanie wszystkich zalet chmury, ale jest to prawdopodobnie najszybsza początkowa ścieżka.

Obecnie platforma Microsoft Azure obsługuje do [331 różnych serwerów bazy danych wdrożonych](https://azuremarketplace.microsoft.com/marketplace/apps/category/databases?page=1&subcategories=databases-all) jako maszyny wirtualne IaaS. Należą do nich popularne RDBMS, takie jak SQL Server, Oracle, MySQL, PostgreSQL i IBM DB2, oraz wiele innych baz danych NoSQL, takich jak MongoDB, Cassandra, DataStax, MariaDB i Cloudera.

> [!NOTE]
> Chociaż przeniesienie rdbms do maszyny Wirtualnej platformy Azure może być najszybszym sposobem migracji danych do chmury (ponieważ jest IaaS), takie podejście wymaga znacznych inwestycji w zespoły IT (administratorzy baz danych i it proitów). Zespoły korporacyjne muszą mieć możliwość konfigurowania wysokiej dostępności, odzyskiwania po awarii i stosowania poprawek dla programu SQL Server oraz zarządzania nimi. W tym kontekście potrzebne jest również dostosowane środowisko z pełnymi prawami administracyjnymi.

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>Kiedy przeprowadzić migrację do programu SQL Server jako maszyny wirtualnej (IaaS)

Może być kilka przypadków, w których nadal trzeba przeprowadzić migrację do programu SQL Server jako zwykłej maszyny Wirtualnej. Przykładowy scenariusz jest, jeśli trzeba użyć sql server Reporting Services. W większości przypadków jednak wystąpienie zarządzane bazy danych SQL platformy Azure może zapewnić wszystko, czego potrzebujesz do migracji z lokalnych serwerów SQL, więc migracja do maszyny wirtualnej programu SQL Server powinna być ostatnią deską ratunku, aby spróbować.

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>Migracja relacyjnych baz danych platformy Azure za pomocą usługi Azure Database Migration Service

Za pomocą usługi Azure Database Migration Service można migrować relacyjne bazy danych, takie jak SQL Server, Oracle i MySQL na platformę Azure, niezależnie od tego, czy docelową bazą danych jest baza danych SQL Azure, zarządzane wystąpienie bazy danych Azure SQL lub SQL Server na maszynie wirtualnej platformy Azure.

Zautomatyzowany przepływ pracy z raportowaniem oceny prowadzi użytkownika przez zmiany, które należy wprowadzić przed migracją bazy danych. Gdy wszystko będzie gotowe, usługa przeprowadza migrację źródłowej bazy danych na platformę Azure.

Za każdym razem, gdy zmieniasz oryginalny RDBMS, może być konieczne ponowne przetestowanie. Może być również konieczna zmiana zdań SQL lub kodu mapowania obiektowego (ORM) w aplikacji, w zależności od wyników testów.

Jeśli masz inną bazę danych (na przykład IBM DB2) i zdecydujesz się na podejście podnoszenia i zmiany, możesz chcieć nadal używać tych baz danych jako maszyn wirtualnych IaaS na platformie Azure, chyba że chcesz przeprowadzić bardziej złożoną migrację danych. Bardziej złożona migracja danych będzie wymagać dodatkowego wysiłku, ponieważ migracja do innego typu bazy danych z nowym schematem i różnymi bibliotekami programowania.

Aby dowiedzieć się, jak migrować bazy danych przy użyciu usługi azure database migration service, zobacz [Szybsze dostęp do chmury dzięki wystąpieniu zarządzanemu bazy danych azure SQL i usłudze azure database migration service](https://channel9.msdn.com/Events/Build/2017/P4008).

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Wybierz opcję programu SQL Server w chmurze: Usługa Azure SQL Database (PaaS) lub SQL Server na maszynie wirtualnej platformy Azure (IaaS)**

    <https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas>

- **Szybsze dostęp do chmury dzięki zarządzanemu wystąpieniu usługi Azure SQL DB i usłudze migracji bazy danych**

    <https://channel9.msdn.com/Events/Build/2017/P4008>

- **Migracja bazy danych programu SQL Server do usługi SQL Database w chmurze**

    <https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate>

- **Baza danych SQL Azure**

    <https://azure.microsoft.com/services/sql-database/?v=16.50>

- **Program SQL Server na maszynach wirtualnych**

    <https://azure.microsoft.com/services/virtual-machines/sql-server/>

> [!div class="step-by-step"]
> [Poprzedni](lift-and-shift-existing-apps-azure-iaas.md)
> [następny](modernize-existing-apps-to-cloud-optimized/index.md) <!-- Next Chapter -->
