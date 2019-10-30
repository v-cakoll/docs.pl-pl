---
title: Migrowanie relacyjnych baz danych do platformy Azure
description: Modernizacja istniejących aplikacji .NET za pomocą chmury platformy Azure i kontenerów systemu Windows | Migrowanie relacyjnych baz danych do platformy Azure
ms.date: 04/28/2018
ms.openlocfilehash: efd1548c3f74fc27450f4949d71a1c4d61907ba5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73093612"
---
# <a name="migrate-your-relational-databases-to-azure"></a>Migrowanie relacyjnych baz danych do platformy Azure

Wizja: platforma Azure oferuje najbardziej kompleksową migrację bazy danych.

Na platformie Azure można migrować serwery baz danych bezpośrednio do maszyn wirtualnych IaaS (czysty dźwig i Shift) lub można migrować do Azure SQL Database, aby uzyskać dodatkowe korzyści. Azure SQL Database oferuje dostępne wystąpienia zarządzane i pełne bazy danych jako usługi (DBaaS). Rysunek 3-1 przedstawia wiele ścieżek migracji relacyjnej bazy danych dostępnych na platformie Azure.

![Ścieżki migracji bazy danych na platformie Azure](./media/image3-1.png)

**Rysunek 3-1.** Ścieżki migracji bazy danych na platformie Azure

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>Kiedy przeprowadzić migrację do Azure SQL Database wystąpienia zarządzanego

W większości przypadków, Azure SQL Database wystąpienie zarządzane będzie najlepszą opcją do uwzględnienia podczas migrowania danych na platformę Azure. Jeśli przeprowadzasz migrację SQL Server baz danych i potrzebujesz niemal 100% gwarancji, aby nie trzeba było zmienić architektury aplikacji ani wprowadzać zmian w kodzie dostępu do danych lub w programie, wybierz funkcję wystąpienia zarządzanego Azure SQL Database.

Azure SQL Database wystąpienie zarządzane jest najlepszą opcją, jeśli masz dodatkowe wymagania dotyczące SQL Server funkcjonalności poziomu wystąpienia lub wymagania dotyczące izolacji poza funkcjami dostępnymi w standardowym Azure SQL Database (pojedynczym modelu bazy danych). Ostatnim z nich jest PaaS wybór, ale nie oferuje on takich samych funkcji, jak w przypadku tradycyjnego programu SQL Server. Migracja może napotkać tarcie.

Na przykład organizacja, która wprowadziła głębokie inwestycje w możliwości SQL Server na poziomie wystąpienia, może korzystać z migracji do wystąpienia zarządzanego SQL. Przykłady możliwości SQL Server na poziomie wystąpienia obejmują integrację środowiska uruchomieniowego języka wspólnego (CLR) SQL, agenta SQL Server i zapytań między bazami danych. Obsługa tych funkcji nie jest dostępna w standardowym Azure SQL Database (model pojedynczej bazy danych).

Organizacja, która działa w branży wysoce regulowanej, i która musi zachować izolację ze względów bezpieczeństwa, może także skorzystać z wyboru modelu wystąpienia zarządzanego SQL.

Wystąpienie zarządzane w Azure SQL Database ma następującą charakterystykę:

- Izolacja zabezpieczeń za pomocą usługi Azure Virtual Network

- Zgodność urządzeń aplikacji z następującymi funkcjami:

  - Agent SQL Server i SQL Server Profiler

  - Odwołania między bazami danych i zapytania, SQL CLR, replikacja, przechwytywanie zmian danych (reprzechwytywania) i Service Broker

- Rozmiary baz danych do 35 TB

- Migracja z minimalnym przestojem z następującymi funkcjami:

  - Azure Database Migration Service

  - Natywna kopia zapasowa i przywracanie oraz wysyłanie dziennika

Dzięki tym funkcjom podczas migrowania istniejących baz danych aplikacji do Azure SQL Database model wystąpienia zarządzanego oferuje niemal 100% korzyści z PaaS dla SQL Server. Wystąpienie zarządzane to środowisko SQL Server, w którym można nadal korzystać z możliwości na poziomie wystąpienia bez konieczności zmiany projektu aplikacji.

Wystąpienie zarządzane jest prawdopodobnie najlepszym rozwiązaniem dla przedsiębiorstw, które obecnie używają SQL Server, i które wymagają elastyczności w zakresie zabezpieczeń sieci w chmurze. Lubisz mieć prywatną sieć wirtualną dla baz danych SQL.

## <a name="when-to-migrate-to-azure-sql-database"></a>Kiedy należy migrować do Azure SQL Database

Jak wspomniano, standardowa Azure SQL Database jest w pełni zarządzana, relacyjna DBaaS. SQL Database obecnie zarządza milionów produkcyjnych baz danych, w tym na całym świecie 38. Obsługuje szeroką gamę aplikacji i obciążeń, od zarządzania prostymi danymi transakcyjnymi, co pozwala na przeprowadzenie większości ważnych dla działalności aplikacji wymagających zaawansowanego przetwarzania danych w skali globalnej.

Ze względu na pełne funkcje PaaS, lepszą cenę i ostatecznie niższy koszt — należy przenieść do standardowej Azure SQL Database jako wybór "według domyślnych", jeśli masz aplikację korzystającą z podstawowych, standardowych baz danych SQL i bez dodatkowych funkcji wystąpienia. SQL Server funkcje, takie jak integracja z programem SQL CLR, Agent SQL Server i zapytania obejmujące wiele baz danych, nie są obsługiwane w standardowej Azure SQL Database. Te funkcje są dostępne tylko w modelu wystąpienia zarządzanego Azure SQL Database.

Azure SQL Database jest jedyną usługą inteligentnej bazy danych w chmurze skompilowaną dla deweloperów aplikacji. Jest to również jedyna usługa bazy danych w chmurze, która skaluje się na bieżąco bez przestojów, aby ułatwić wydajne dostarczanie aplikacji wielodostępnych. Ostatecznie Azure SQL Database pozostawać więcej czasu na innowacje i skrócić czas wprowadzania na rynek. Możesz tworzyć bezpieczne aplikacje i łączyć się z bazą danych SQL przy użyciu preferowanych języków i platform.

Azure SQL Database oferuje następujące korzyści:

- Wbudowana inteligencja (Uczenie maszynowe), która uczy się i dostosowuje do aplikacji

- Inicjowanie obsługi bazy danych na żądanie

- Zakres ofert dla wszystkich obciążeń

- dostępność na 99,99% umowy SLA, obsługa zero

- Usługi replikacji geograficznej i przywracania na potrzeby ochrony danych

- Funkcja przywracania do punktu Azure SQL Database w czasie

- Zgodność z SQL Server 2016, w tym hybrydowej i migracji

Standardowa Azure SQL Database jest bliżej PaaS niż Azure SQL Database wystąpienia zarządzanego. Preferuj standardową Azure SQL Database, ponieważ uzyskasz więcej korzyści z chmury zarządzanej. Jednak Azure SQL Database ma pewne kluczowe różnice od zwykłych i lokalnych wystąpień SQL Server. W zależności od wymagań dotyczących bazy danych aplikacji oraz wymagań i zasad przedsiębiorstwa może nie być najlepszym wyborem w przypadku planowania migracji do chmury.

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>Kiedy przenieść oryginalny RDBMS do maszyny wirtualnej (IaaS)

Jedną z opcji migracji jest przeniesienie oryginalnego systemu zarządzania relacyjnymi bazami danych (RDBMS), w tym Oracle, IBM DB2, MySQL, PostgreSQL lub SQL Server, do podobnego serwera, który działa na maszynie wirtualnej platformy Azure. Jeśli masz istniejące aplikacje wymagające najszybszej migracji do chmury z minimalnymi zmianami lub nie wszystkie zmiany w ogóle, bezpośrednia migracja do IaaS w chmurze może być opcją godziwą. Może nie być najlepszym sposobem na skorzystanie z zalet wszystkich korzyści z chmury, ale prawdopodobnie najszybszą ścieżką początkową.

Obecnie Microsoft Azure obsługuje do [331 różnych serwerów baz danych](https://azuremarketplace.microsoft.com/marketplace/apps/category/databases?page=1&subcategories=databases-all) wdrożonych jako maszyny wirtualne IaaS. Obejmują one popularne RDBMS, takie jak SQL Server, Oracle, MySQL, PostgreSQL i IBM DB2, oraz wiele innych baz danych NoSQL, takich jak MongoDB, Cassandra, DataStax, MariaDB i Cloudera.

> [!NOTE]
> Mimo że przeniesienie RDBMS na maszynę wirtualną platformy Azure może być najszybszym sposobem na migrację danych do chmury (ponieważ jest to IaaS), to podejście wymaga znaczącej inwestycji w zespoły IT (Administratorzy baz danych i informatyków). Zespoły korporacyjne muszą mieć możliwość skonfigurowania wysokiej dostępności, odzyskiwania po awarii i zastosowania poprawek dla SQL Server. Ten kontekst wymaga również środowiska niestandardowego z pełnymi prawami administracyjnymi.

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>Kiedy należy migrować do SQL Server jako maszynę wirtualną (IaaS)

Może istnieć kilka przypadków, w których nadal trzeba przeprowadzić migrację do SQL Server jako zwykłej maszyny wirtualnej. Przykładowy scenariusz jest potrzebny do użycia SQL Server Reporting Services. W większości przypadków, Azure SQL Database wystąpienie zarządzane może zapewnić wszystko, czego potrzebujesz do migracji z lokalnych serwerów SQL, aby migracja do maszyny wirtualnej SQL Server powinna być ostatnią możliwością.

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>Migrowanie relacyjnych baz danych do platformy Azure za pomocą Azure Database Migration Service

Za pomocą Azure Database Migration Service można migrować relacyjne bazy danych, takie jak SQL Server, Oracle i MySQL na platformę Azure, niezależnie od tego, czy docelowa baza danych jest Azure SQL Database, Azure SQL Database wystąpieniem zarządzanym lub SQL Server na maszynie wirtualnej platformy Azure.

Zautomatyzowany przepływ pracy, z raportowaniem oceny, prowadzi użytkownika przez zmiany, które należy wykonać przed migracją bazy danych. Gdy wszystko będzie gotowe, usługa migruje źródłową bazę danych do platformy Azure.

Za każdym razem, gdy zmienisz oryginalny RDBMS, może być konieczne ponowne przetestowanie. W zależności od wyników testów może być również konieczne zmodyfikowanie w aplikacji kodu zdań SQL lub mapowania obiektu (ORM).

Jeśli masz inną bazę danych (na przykład IBM DB2) i zdecydujesz się na podejście i przesunięcia, możesz chcieć nadal korzystać z tych baz danych jako maszyn wirtualnych IaaS na platformie Azure, chyba że chcesz przeprowadzić bardziej złożoną migrację danych. Bardziej złożona migracja danych będzie wymagała dodatkowego wysiłku, ponieważ przejdziesz do migracji do innego typu bazy danych z nowym schematem i różnymi bibliotekami programistycznymi.

Aby dowiedzieć się, jak migrować bazy danych za pomocą Azure Database Migration Service, zobacz szybsze korzystanie z [chmury za pomocą Azure SQL Database wystąpienia zarządzanego i Azure Database Migration Service](https://channel9.msdn.com/Events/Build/2017/P4008).

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Wybierz opcję SQL Server w chmurze: Azure SQL Database (PaaS) lub SQL Server na maszynie wirtualnej platformy Azure (IaaS)**

    <https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas>

- **Szybciej Rozpocznij działanie w chmurze dzięki wystąpieniu zarządzanym usługi Azure SQL DB i Database Migration Service**

    <https://channel9.msdn.com/Events/Build/2017/P4008>

- **SQL Server migrację bazy danych do SQL Database w chmurze**

    <https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate>

- **Azure SQL Database**

    <https://azure.microsoft.com/services/sql-database/?v=16.50>

- **SQL Server na maszynach wirtualnych**

    <https://azure.microsoft.com/services/virtual-machines/sql-server/>

> [!div class="step-by-step"]
> [Poprzedni](lift-and-shift-existing-apps-azure-iaas.md)
> [Następny](modernize-existing-apps-to-cloud-optimized/index.md) <!-- Next Chapter -->
