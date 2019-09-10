---
title: Pisanie dostawcy danych programu Entity Framework
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 29aa8cb1c6b31d9ada6b01860d76bcf03d37416c
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854161"
---
# <a name="writing-an-entity-framework-data-provider"></a>Pisanie dostawcy danych programu Entity Framework
W tej sekcji omówiono sposób pisania Entity Framework dostawcy w celu obsługi źródła danych innego niż SQL Server. Entity Framework zawiera dostawcę obsługującego SQL Server.  
  
## <a name="introducing-the-entity-framework-provider-model"></a>Wprowadzenie do modelu dostawcy Entity Framework  
 Entity Framework jest niezależna od bazy danych i można napisać dostawcę przy użyciu modelu dostawcy ADO.NET w celu nawiązania połączenia z różnorodnym zestawem źródeł danych.  
  
 Dostawca danych Entity Framework (utworzony przy użyciu modelu Dostawca danych ADO.NET) wykonuje następujące funkcje:  
  
- Mapuje typy pierwotne Entity Data Model (EDM) na typy dostawców.  
  
- Opisuje funkcje specyficzne dla dostawcy.  
  
- Generuje polecenia specyficzne dla dostawcy dla danego DbQueryCommandTree do obsługi zapytań Entity Framework.  
  
- Generuje polecenia aktualizacji specyficzne dla dostawcy dla danego DbModificationCommandTree do obsługi aktualizacji za pomocą Entity Framework.  
  
- Przedstawia mapowanie plików dla definicji schematu magazynu w celu obsługi generowania modelu opartego na bazie danych.  
  
- Udostępnia metadane (na przykład tabele i widoki) za pośrednictwem modelu koncepcyjnego.  
  
 ![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")  
  
## <a name="sample"></a>Przykład  
 Zapoznaj się Entity Framework z przykładowym [dostawcą](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) Entity Framework, który obsługuje źródło danych inne niż SQL Server.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Generowanie kodu SQL](sql-generation.md)  
  
 [Modyfikowanie generowania kodu SQL](modification-sql-generation.md)  
  
 [Specyfikacja manifestu dostawcy](provider-manifest-specification.md)  
  
## <a name="see-also"></a>Zobacz także

- [Praca z dostawcami danymi](working-with-data-providers.md)
