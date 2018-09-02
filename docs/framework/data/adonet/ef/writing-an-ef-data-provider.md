---
title: Pisanie dostawcy danych programu Entity Framework
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 50c0555d84c5b5f180c8c49a8419e8a414a4befe
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401464"
---
# <a name="writing-an-entity-framework-data-provider"></a>Pisanie dostawcy danych programu Entity Framework
W tej sekcji omówiono sposób pisania [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dostawcy w celu obsługi źródła danych inne niż SQL Server. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Obejmuje dostawcę, który obsługuje program SQL Server.  
  
## <a name="introducing-the-entity-framework-provider-model"></a>Wprowadzenie do modelu dostawcy programu Entity Framework  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Zależy od bazy danych i dostawcę można pisać przy użyciu modelu dostawcy ADO.NET połączyć się z różnorodnych źródeł danych.  
  
 Dostawca danych programu Entity Framework (utworzone przy użyciu modelu dostawcy danych ADO.NET) wykonuje następujące funkcje:  
  
-   Mapuje typy dostawców typów pierwotnych modelu Entity Data Model (EDM).  
  
-   Uwidacznia funkcje właściwe dla dostawcy.  
  
-   Generuje polecenia specyficzne dla dostawcy dla danego DbQueryCommandTree do obsługi [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zapytania.  
  
-   Generuje polecenia aktualizacji specyficzne dla dostawcy dla danego DbModificationCommandTree do obsługi aktualizacji za pośrednictwem [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
-   Udostępnia mapowanie plików dla definicji schematu magazynu do obsługi generowania modelu, w oparciu o bazę danych.  
  
-   Udostępnia metadane (tabele i widoki, na przykład) za pośrednictwem modelu koncepcyjnego.  
  
 ![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")  
  
## <a name="sample"></a>Przykład  
 Zobacz [dostawcy programu Entity Framework przykładowe](https://go.microsoft.com/fwlink/?LinkId=180616) przykładowego [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dostawcy, który obsługuje źródła danych inne niż SQL Server.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Generowanie kodu SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md)  
  
 [Modyfikowanie generowania kodu SQL](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)  
  
 [Specyfikacja manifestu dostawcy](../../../../../docs/framework/data/adonet/ef/provider-manifest-specification.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z dostawcami danymi](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)
