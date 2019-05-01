---
title: Migrowanie relacyjnych baz danych na platformę azure
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów Windows | Migrowanie relacyjnych baz danych na platformę azure
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 600c47b6b0ccaf704c8e7b638c759e990acaaacf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61812784"
---
# <a name="migrate-your-relational-databases-to-azure"></a>Migrowanie relacyjnych baz danych na platformę azure

Wizja: Platforma Azure oferuje najbardziej kompleksowy migracji bazy danych.

Na platformie Azure można migrować serwery bazy danych bezpośrednio do maszyn wirtualnych IaaS (czysty lift- and -shift), lub można przeprowadzić migrację do usługi Azure SQL Database, do dodatkowych korzyści. Usługa Azure SQL Database oferuje wystąpienia zarządzanego i opcje (DBaaS) pełnej bazy danych as-a-service. Rysunek 3-1 zawiera wiele relacyjnej bazy danych ścieżki migracji jest dostępne na platformie Azure.

![Ścieżki migracji bazy danych na platformie Azure](./media/image3-1.png)

> **Rysunek 3-1.** Ścieżki migracji bazy danych na platformie Azure

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>Czas migracji do wystąpienia zarządzanego Azure SQL Database

W większości przypadków wystąpienia zarządzanego Azure SQL Database będzie najlepszym rozwiązaniem brać pod uwagę podczas migracji danych do platformy Azure. Jeśli jest przeprowadzana migracja baz danych programu SQL Server i potrzebujesz niemal gwarancji 100%, że nie trzeba będzie Przekształcanie aplikacji lub wprowadzić zmiany do danych lub kod dostępu do danych, wybierz funkcję wystąpienia zarządzanego usługi Azure SQL Database.

Wystąpienie usługi Azure SQL Database zarządzane jest najlepszym rozwiązaniem, jeśli masz dodatkowe wymagania dotyczące funkcji na poziomie wystąpienia programu SQL Server lub wymagań izolacji poza funkcji oferowanych w usługi Azure SQL Database w warstwie standardowa (model pojedynczej bazy danych). Wybór najbardziej zorientowane na PaaS jest to ostatni z nich, ale go nie oferuje te same funkcje jak w przypadku tradycyjnego programu SQL server. Migracja może powierzchni frictions.

Na przykład organizacja, która podejścia biznesowego uczyniło głębokiego inwestycji w możliwości programu SQL Server na poziomie wystąpienia używającym migracją do wystąpienia zarządzanego SQL. Przykłady możliwości programu SQL Server na poziomie wystąpienia obejmują SQL wspólnej integrację środowiska uruchomieniowego (języka wspólnego CLR), programu SQL Server Agent i wykonywania zapytań między bazami danych. Obsługa tych funkcji nie jest dostępna w standardowa usługi Azure SQL Database (model pojedynczej bazy danych).

Organizacja, która działa w branży podlegających szczegółowym regułom, które trzeba utrzymać izolację ze względów bezpieczeństwa może również korzystać z Wybieranie modelu wystąpienia zarządzanego SQL.

Wystąpienie zarządzane usługi Azure SQL Database ma następującą charakterystykę:

- Izolacja na potrzeby zabezpieczeń za pomocą usługi Azure Virtual Network

- Urządzenia surface zgodności aplikacji, za pomocą tych funkcji:

  - Agent programu SQL Server i SQL Server Profiler

  - Między bazami danych odwołania i zapytań SQL CLR replikacji, przechwytywania zmian danych (CDC) i programu Service Broker

- Baza danych o rozmiarach do 35 TB

- Minimalnym przestoju migracja tych funkcji:

  - Azure Database Migration Service

  - Natywnego wykonywania kopii zapasowych i przywracania oraz wysyłania dziennika

Dzięki takim funkcjom podczas migrowania istniejących aplikacji baz danych do usługi Azure SQL Database, model wystąpienia zarządzanego oferuje prawie 100% zalety rozwiązania paas dla programu SQL Server. Wystąpienie zarządzane to środowisko programu SQL Server, w którym będziesz nadal korzystać z funkcji na poziomie wystąpienia bez zmieniania projektu aplikacji.

Wystąpienie zarządzane jest prawdopodobnie najlepszym rozwiązaniem dla przedsiębiorstw, która obecnie używasz programu SQL Server, a które wymagają elastyczność w ich zabezpieczeń sieci w chmurze. To jak prywatnej sieci wirtualnej dla baz danych SQL.

## <a name="when-to-migrate-to-azure-sql-database"></a>Czas migracji do usługi Azure SQL Database

Jak wspomniano wcześniej, standardowa usługi Azure SQL Database jest w pełni zarządzana, relacyjna DBaaS. SQL Database zarządza aktualnie milionów produkcyjnych bazach danych, w 38 centrach danych, na całym świecie. Obsługuje ona szerokiej gamy aplikacji i obciążeń, od zarządzania proste dane transakcyjne opracowuje aplikacji najbardziej-intensywnie korzystających z danych o kluczowym znaczeniu, które wymagają zaawansowane przetwarzanie danych w skali globalnej.

Ze względu na jej funkcji pełnego PaaS lepsze ceny- i ostatecznie obniżyć koszt — należy przenieść do standardowa usługi Azure SQL Database jako ulubionego"domyślnie" Jeśli masz aplikację, że używa podstawowa, standardowa baz danych SQL i żadne funkcje dodatkowe wystąpienia. Funkcje programu SQL Server, takich jak integracja środowiska CLR programu SQL, SQL Server Agent i wykonywania zapytań między bazami danych nie są obsługiwane w standardowa usługi Azure SQL Database. Te funkcje są dostępne tylko w modelu wystąpienia zarządzanego Azure SQL Database.

Usługa Azure SQL Database to usługa bazy danych tylko w inteligentnej chmurze, która została skonstruowana na potrzeby deweloperów aplikacji. Jest również jedynym bazy danych usługi w chmurze, którą można skalować na bieżąco, bez przestojów, aby ułatwić wydajnie dostarczać wielodostępne aplikacje. Ostatecznie Azure SQL Database pozostanie na innowacjach i przyspiesza czas wprowadzenia na rynek. Można tworzyć bezpieczne aplikacje i łączenie z bazy danych SQL za pomocą języków i platform, które użytkownik sobie tego życzy.

Usługa Azure SQL Database oferuje następujące korzyści:

- Wbudowana funkcja analizy (uczenie maszynowe), która uczy się i dostosowuje się do aplikacji

- Aprowizacja bazy danych na żądanie

- Zakres oferty dla wszystkich obciążeń

- dostępność przez 99,99% umowy SLA, eliminujące potrzebę konserwacji

- Replikacja geograficzna i przywracania usługi ochrony danych

- Punkt bazy danych SQL Azure w funkcji przywracania do określonego

- Zgodność z programu SQL Server 2016, łącznie z hybrydowego i migracji

Standardowa usługi Azure SQL Database jest bliżej PaaS niż wystąpienia zarządzanego Azure SQL Database. Preferuj standardowa usługi Azure SQL Database, ponieważ uzyskasz więcej korzyści z chmury zarządzanej. Jednak usługa Azure SQL Database występują też zasadnicze różnice z regularnych i środowiska lokalnego wystąpienia programu SQL Server. W zależności od wymagań bazy danych istniejącej aplikacji i wymagań przedsiębiorstwa i zasady może nie być najlepszym wyborem podczas planowania migracji do chmury.

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>Kiedy należy przenieść swoje oryginalne RDBMS do maszyny Wirtualnej (IaaS)

Jedną z opcji migracji jest aby przenieść swoje oryginalne system zarządzania relacyjnymi bazami danych (RDBMS), w tym Oracle, IBM DB2, MySQL, PostgreSQL i SQL Server na serwerze podobne, w którym jest uruchomiona na Maszynie wirtualnej platformy Azure. Jeśli masz istniejące aplikacje, które wymagają najszybsza migracja do chmury przy minimalnych zmianach, lub jedynie minimalnych zmianach w ogóle, bezpośrednie migracji IaaS w chmurze może być opcją podejście. Może nie być najlepszym sposobem, aby móc korzystać z zalet wszystkie chmury, ale prawdopodobnie jest to najszybszy początkowej.

Obecnie usługa Microsoft Azure obsługuje maksymalnie [331 innej bazy danych serwerów](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/category/databases?page=1&subcategories=databases-all) wdrożone jako maszyny wirtualne IaaS. Obejmują one popularnych RDBMS, takich jak SQL Server, Oracle, MySQL, PostgreSQL i IBM DB2 i wiele innych baz danych NoSQL, takie jak bazy danych MongoDB, Cassandra, DataStax, MariaDB i Cloudera.

> [!NOTE]
> Mimo że przenoszenie Twojej RDBMS na Maszynie wirtualnej platformy Azure może być najszybszym sposobem na migrację danych do chmury (ponieważ jest ona IaaS), to podejście wymaga znaczących inwestycji związanych z Twój zespół IT (Administratorzy baz danych i specjalistów IT). Zespołom przedsiębiorstwa muszą mieć możliwość konfigurowania i zarządzania nią, wysoką dostępność, odzyskiwanie po awarii i stosowanie poprawek dla programu SQL Server. Ten kontekst musi także dostosowane środowisko z pełnymi prawami administracyjnymi.

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>Czas migracji do programu SQL Server jako maszyny Wirtualnej (IaaS)

Może istnieć kilka przypadków, nadal konieczne migracji programu SQL Server jako regularne maszyny Wirtualnej. Przykładowy scenariusz jest, jeśli musisz użyć programu SQL Server Reporting Services. W większości przypadków, wystąpienia zarządzanego Azure SQL Database zapewnia wszystko, czego chcesz przeprowadzić migrację z lokalnymi serwerami SQL, dlatego migracji maszyny Wirtualnej programu SQL Server powinny być usługi w ostateczności próby.

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>Azure Database Migration Service umożliwia migrowanie relacyjnych baz danych na platformę Azure 

Azure Database Migration Service służy do migrowania relacyjnych baz danych, takich jak SQL Server, Oracle i MySQL na platformie Azure, czy docelowa baza danych Azure SQL Database, wystąpienia zarządzanego Azure SQL Database lub SQL Server na Maszynie wirtualnej platformy Azure.

Zautomatyzowany przepływ pracy z raportowaniem oceny, przeprowadzi Cię przez zmiany, które należy wprowadzić przed przeprowadzeniem migracji bazy danych. Gdy wszystko będzie gotowe, usługa migruje źródłowej bazy danych na platformie Azure.

Zawsze, gdy zmiany w oryginalnym systemie RDBMS, może być konieczne sprawdź jeszcze raz. Również może być konieczne zmiany zdania SQL lub kod obiektowo-relacyjny mapowanie (ORM) w aplikacji, w zależności od wyników testów.

Jeśli masz każdej innej bazy danych (na przykład, IBM DB2) i zoptymalizowany pod kątem podejście lift- and -shift, możesz chcieć kontynuować korzystanie z tych baz danych jako maszyn wirtualnych IaaS na platformie Azure, chyba że chcesz przeprowadzić migrację danych bardziej złożone. Bardziej złożone migracji danych będzie wymagać dodatkowego nakładu pracy, ponieważ będzie migrowany do typu innej bazy danych przy użyciu nowego schematu i innej biblioteki programistyczne.

Aby dowiedzieć się, jak przeprowadzić migrację bazy danych za pomocą usługi Azure Database Migration Service, zobacz [przejść do chmury dzięki wystąpienia zarządzanego Azure SQL Database i Azure Database Migration Service](https://channel9.msdn.com/Events/Build/2017/P4008).

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Wybieranie opcji programu SQL Server w chmurze: Usługa Azure SQL Database (PaaS) lub SQL Server na maszynie Wirtualnej platformy Azure (IaaS)**

    <https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas>

- **Pobierz w chmurze, które są szybsze działanie w przypadku wystąpienia zarządzanego Azure SQL DB i Database Migration Service**

    <https://channel9.msdn.com/Events/Build/2017/P4008>

- **Migracja bazy danych programu SQL Server do bazy danych SQL w chmurze**

    <https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate>

- **Azure SQL Database**

    <https://azure.microsoft.com/services/sql-database/?v=16.50>

- **SQL Server na maszynach wirtualnych**

    <https://azure.microsoft.com/services/virtual-machines/sql-server/>

> [!div class="step-by-step"]
> [Poprzednie](lift-and-shift-existing-apps-azure-iaas.md)
> [dalej](modernize-existing-apps-to-cloud-optimized/index.md)
