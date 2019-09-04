---
title: Pisanie dostawcy danych programu Entity Framework
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 6c5e6e2859b48db6c982862381d223a4c9deb2c5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248188"
---
# <a name="writing-an-entity-framework-data-provider"></a>Pisanie dostawcy danych programu Entity Framework
W tej sekcji omówiono sposób pisania [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dostawcy w celu obsługi źródła danych innego niż SQL Server. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Zawiera dostawcę, który obsługuje SQL Server.  
  
## <a name="introducing-the-entity-framework-provider-model"></a>Wprowadzenie do modelu dostawcy Entity Framework  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Jest niezależna od bazy danych i można napisać dostawcę przy użyciu modelu dostawcy ADO.NET, aby połączyć się z różnorodnymi źródłami danych.  
  
 Dostawca danych Entity Framework (utworzony przy użyciu modelu Dostawca danych ADO.NET) wykonuje następujące funkcje:  
  
- Mapuje typy pierwotne Entity Data Model (EDM) na typy dostawców.  
  
- Opisuje funkcje specyficzne dla dostawcy.  
  
- Generuje polecenia specyficzne dla dostawcy dla danego DbQueryCommandTree do obsługi [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zapytań.  
  
- Generuje polecenia aktualizacji specyficzne dla dostawcy dla danego DbModificationCommandTree do obsługi aktualizacji za pomocą programu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
- Przedstawia mapowanie plików dla definicji schematu magazynu w celu obsługi generowania modelu opartego na bazie danych.  
  
- Udostępnia metadane (na przykład tabele i widoki) za pośrednictwem modelu koncepcyjnego.  
  
 ![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")  
  
## <a name="sample"></a>Przykład  
 Zapoznaj się z przykładowym [dostawcą Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) , aby [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] uzyskać przykład dostawcy obsługującego źródło danych inne niż SQL Server.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Generowanie kodu SQL](sql-generation.md)  
  
 [Modyfikowanie generowania kodu SQL](modification-sql-generation.md)  
  
 [Specyfikacja manifestu dostawcy](provider-manifest-specification.md)  
  
## <a name="see-also"></a>Zobacz także

- [Praca z dostawcami danymi](working-with-data-providers.md)
