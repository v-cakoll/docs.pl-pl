---
title: Migrowanie relacyjnych baz danych na platformie azure
description: Modernizacji istniejących aplikacji .NET z chmury Azure i kontenery systemu Windows | Migrowanie relacyjnych baz danych na platformie azure
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: fe1bf5820c2306beb380749b34d5a56964e016e4
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="migrate-your-relational-databases-to-azure"></a>Migrowanie relacyjnych baz danych na platformie azure

Wizja: Azure oferuje najbardziej kompleksowe migracja bazy danych.

Na platformie Azure można przeprowadzić migrację serwerów bazy danych bezpośrednio do maszyn wirtualnych IaaS (przyrostu czysty i shift), lub można przeprowadzić migrację do bazy danych SQL Azure, aby uzyskać dodatkowe korzyści. Baza danych SQL Azure oferuje pełnej bazy danych jako — usługa (DBaaS) opcje i zarządzane wystąpienia. Rysunek 3-1 zawiera wiele relacyjnej bazy danych ścieżki migracji dostępnej na platformie Azure.

![Ścieżki migracji bazy danych na platformie Azure](./media/image3-1.png)

> **Rysunek 3-1.** Ścieżki migracji bazy danych na platformie Azure

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>Podczas migracji do wystąpienia zarządzane bazy danych SQL Azure

W większości przypadków wystąpienia zarządzane bazy danych SQL Azure będzie najlepiej możliwość należy wziąć pod uwagę podczas migracji danych do platformy Azure. Jeśli jest przeprowadzana migracja bazy danych programu SQL Server i musisz niemal gwarantują 100%, że nie będzie konieczne rearchitect aplikacji lub wprowadzić zmiany w danych lub kod dostępu do danych, wybierz funkcję zarządzane wystąpienia bazy danych SQL Azure.

Azure wystąpienia bazy danych SQL zarządzanych jest najlepszym rozwiązaniem w przypadku dodatkowe wymagania dotyczące funkcji na poziomie wystąpienia programu SQL Server lub wymagania dotyczące izolacji poza funkcje zawarte w standardowe usługi Azure SQL Database (model pojedynczej bazy danych). Wybór najbardziej zorientowane na PaaS jest to ostatni z nich, ale nie oferuje te same funkcje co tradycyjnych programu SQL server. Migracja może powierzchni frictions.

Na przykład organizacja, która wprowadził bezpośrednich inwestycji w poziomie wystąpienia programu SQL Server możliwości będzie korzystać z migracji do zarządzanego wystąpienia serwera SQL. Przykłady poziomie wystąpienia programu SQL Server możliwości obejmują SQL integrację środowiska uruchomieniowego (języka wspólnego CLR), programu SQL Server Agent i między bazami danych zapytań. Obsługa tych funkcji nie jest dostępna w standardowej bazy danych SQL Azure (model pojedynczej bazy danych).

Organizacja, która działa w branży wysokiej podlegającymi ochronie, które trzeba zachować izolacji ze względów bezpieczeństwa może również korzystać z Wybieranie modelu zarządzane wystąpienia serwera SQL.

Zarządzane wystąpienie w bazie danych SQL Azure ma następującą charakterystykę:

- Izolacji zabezpieczeń za pośrednictwem sieci wirtualnej platformy Azure

- Powierzchni zgodności aplikacji, z tych funkcji:

  - Agenta programu SQL Server i SQL Server Profiler

  - Między bazami danych odwołania i kwerend SQL CLR replikacji, przechwytywania zmian danych (CDC) i programu Service Broker

- Do 35 TB rozmiar bazy danych

- Co najmniej przestoju migracji tych funkcji:

  - Usługa migracji bazy danych Azure

  - Natywnego wykonywania kopii zapasowych i przywracania oraz wysyłania dziennika

Dzięki takim funkcjom podczas migracji istniejącej bazy danych aplikacji do usługi Azure SQL Database, model zarządzanego wystąpienia oferuje prawie 100% zalet Paas dla programu SQL Server. Wystąpienie zarządzanych jest środowisko programu SQL Server, gdzie kontynuować przy użyciu funkcji na poziomie wystąpienia bez zmiany projektu aplikacji.

Wystąpienie zarządzanych prawdopodobnie jest najlepszym rozwiązaniem dla przedsiębiorstw, który obecnie korzystają z programu SQL Server, a które wymagają elastyczność ich zabezpieczeń sieciowych w chmurze. Przypomina o wirtualnej sieci prywatnej dla bazy danych SQL.

## <a name="when-to-migrate-to-azure-sql-database"></a>Podczas migracji do bazy danych SQL Azure

Jak wspomniano, standardowe bazy danych SQL Azure jest DBaaS pełni zarządzany i relacyjny. Baza danych SQL obecnie zarządza miliony produkcyjnych baz danych, centrów 38 na świecie. Obsługuje szeroką gamę aplikacji i obciążeń, zarządzanie bezpośrednie danych transakcyjnych kierowania najbardziej dużą ilością danych, kluczowych aplikacji, które wymagają zaawansowane przetwarzania danych w skali globalnej.

Ze względu na jego pełny funkcji PaaS lepiej cennik- i ostatecznie niższy koszt — należy przenieść do standardowej bazy danych SQL Azure jako "wybranym domyślnie" Jeśli masz aplikację tego używa podstawowa, standardowa baz danych i żadne funkcje dodatkowe wystąpienia. Funkcje programu SQL Server, takie jak integrację środowiska CLR SQL, SQL Server Agent i badania między bazami danych nie są obsługiwane w standardowej bazy danych SQL Azure. Te funkcje są dostępne tylko w modelu wystąpienia zarządzane bazy danych SQL Azure.

Bazy danych SQL Azure to usługa bazy danych w chmurze tylko inteligentnego, która została skompilowana dla projektantów aplikacji. Istnieje również tylko bazy danych usługi w chmurze skaluje na bieżąco, bez przestojów, ułatwiające Dostarcz wielodostępnych aplikacji. Ostatecznie baza danych SQL Azure pozostawia więcej czasu na innowacji, a jego przyspiesza czas na rynek. Można tworzyć aplikacje bezpieczne i połączenia z bazą danych SQL przy użyciu języków i platform, które chcesz.

Baza danych SQL Azure oferuje następujące korzyści:

- Wbudowane analizy (uczenie maszynowe), które uzyskuje informacje o i dostosowuje się do aplikacji

- Inicjowanie obsługi administracyjnej bazy danych na żądanie

- Zakres oferty, dla wszystkich obciążeń

- dostępność 99,99% SLA, zero konserwacji

- Replikacja geograficzna i przywracania usługi ochrony danych

- Punkt bazy danych SQL Azure w funkcji czasu przywracania

- Zgodność z SQL Server 2016, łącznie z hybrydowego i migracji

Standardowa baza danych SQL Azure jest bliżej PaaS niż wystąpienia zarządzane bazy danych SQL Azure. Preferowane standardowa baza danych SQL Azure, ponieważ uzyskasz więcej korzyści z chmury zarządzanych. Niemniej jednak bazy danych SQL Azure ma niektóre podstawowe różnice w regularnych i lokalnego wystąpienia programu SQL Server. W zależności od wymagań bazy danych istniejącej aplikacji i wymagań przedsiębiorstwa i zasady może nie być najlepszym wyborem podczas planowania migracji do chmury.

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>Kiedy można przenosić z oryginalnej RDBMS do maszyn wirtualnych (IaaS)

Jedną z opcji migracji jest przeniesienie oryginalnego systemu zarządzania relacyjnej bazy danych (RDBMS), w tym Oracle, IBM DB2, MySQL, PostgreSQL lub SQL Server na serwerze podobne, który działa na maszynie Wirtualnej platformy Azure. Jeśli masz istniejące aplikacje, które wymagają najszybszą migrację do chmury przy minimalnych zmianach lub żadnych zmian na wszystkich bezpośrednich migracji do IaaS w chmurze może być odpowiedniej opcji. Może nie być najlepszy sposób, aby skorzystać z zalet wszystkie chmury, ale prawdopodobnie jest najszybszym ścieżki początkowej.

Obecnie usługa Microsoft Azure obsługuje maksymalnie [331 innej bazy danych serwerów](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/category/databases?page=1&subcategories=databases-all) wdrażane jako maszyny wirtualne IaaS. Obejmują one popularnych RDBMS, takich jak SQL Server, Oracle, MySQL, PostgreSQL i IBM DB2 i wiele innych bazy danych NoSQL, takie jak bazy danych MongoDB, Cassandra DataStax, MariaDB i Cloudera.

> [!NOTE]
> Mimo że przenoszenie RDBMS sieci na maszynie Wirtualnej platformy Azure może być to najszybszy sposób migrację danych do chmury (ponieważ jest IaaS), to rozwiązanie wymaga znaczącą inwestycję w zespołów IT (administratorów bazy danych i specjalistów IT). Zespoły przedsiębiorstwa muszą mieć możliwość konfigurowania i zarządzania wysokiej dostępności, odzyskiwania po awarii i stosowanie poprawek dla programu SQL Server. Ten kontekst musi także dostosowane środowisko, z pełnymi prawami administracyjnymi.

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>Podczas migracji do programu SQL Server jako maszyny Wirtualnej (IaaS)

Może istnieć kilka przypadków, w których nadal należy przeprowadzić migrację do programu SQL Server jako regularne maszyna wirtualna. Przykładowy scenariusz jest, jeśli należy użyć programu SQL Server Reporting Services. W większości przypadków, wystąpienia zarządzane bazy danych SQL Azure oferuje wszystko, co jest potrzebne do migracji z lokalnych serwerów SQL, więc migracji z maszyną wirtualną serwera SQL powinno być użytkownika w ostateczności próby.

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>Za pomocą usługi migracji bazy danych Azure można migrować relacyjnych baz danych na platformie Azure 

Usługa migracji bazy danych Azure służy do migrowania relacyjnych baz danych, takich jak SQL Server, Oracle i MySQL na platformie Azure, czy docelowej bazy danych jest baza danych SQL Azure, wystąpienia zarządzane bazy danych SQL Azure lub programu SQL Server na maszynie Wirtualnej platformy Azure.

Automatyczne przepływu pracy z raportowaniem oceny, przeprowadzi Cię przez zmiany, które należy upewnić się, przed przeprowadzeniem migracji bazy danych. Gdy wszystko będzie gotowe, usługa migruje źródłowej bazy danych do platformy Azure.

Przy każdej zmianie oryginalnego RDBMS, konieczne może być sprawdź jeszcze raz. Należy również zmienić zdania SQL lub kodu aplikacji, w zależności od wyników testowania obiektów relacyjnych mapowania ORM ().

Jeśli masz przykładowej bazy danych (na przykład IBM DB2) i wybrać podejście przyrostu i shift, można nadal używać tych baz danych jako maszyny wirtualne IaaS platformy Azure, chyba że chcesz przeprowadzić migrację danych bardziej złożonych. Bardziej złożone migracji danych będzie wymagać dodatkowego nakładu pracy, ponieważ czy migracji do innej bazy danych typu z nowym schematem i różnych biblioteki programistyczne.

Aby dowiedzieć się, jak przeprowadzić migrację bazy danych przy użyciu usługi migracji bazy danych Azure, zobacz [uzyskać dostęp do chmury dzięki wystąpienia zarządzane bazy danych SQL Azure i usługi migracji bazy danych Azure](https://channel9.msdn.com/Events/Build/2017/P4008).

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Wybierz chmurę programu SQL Server option: Azure SQL Database (PaaS) lub SQL Server na maszynie Wirtualnej Azure (IaaS)**

    [https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas)

- **Uzyskanie dostępu do chmury dzięki wystąpienia zarządzane bazy danych SQL Azure i usługi migracji bazy danych**

    [https://channel9.msdn.com/Events/Build/2017/P4008](https://channel9.msdn.com/Events/Build/2017/P4008)

- **Migracja bazy danych programu SQL Server z bazą danych SQL w chmurze**

    [https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate](https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate)

- **Baza danych Azure SQL**

    [https://azure.microsoft.com/services/sql-database/?v=16.50](https://azure.microsoft.com/services/sql-database/?v=16.50)

- **SQL Server na maszynach wirtualnych**

    [https://azure.microsoft.com/services/virtual-machines/sql-server/](https://azure.microsoft.com/services/virtual-machines/sql-server/)

>[!div class="step-by-step"]
[Poprzednie](lift-and-shift-existing-apps-azure-iaas.md)
[dalej](modernize-existing-apps-to-cloud-optimized/index.md)