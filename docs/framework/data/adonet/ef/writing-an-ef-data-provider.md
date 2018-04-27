---
title: Pisanie dostawca danych programu Entity Framework
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: cb969589afd4474d9bdfa3a475d8325c1717ab13
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="writing-an-entity-framework-data-provider"></a>Pisanie dostawca danych programu Entity Framework
W tej sekcji omówiono sposób zapisania [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dostawcy do obsługi źródła danych inne niż SQL Server. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Obejmuje dostawcę, który obsługuje program SQL Server.  
  
## <a name="introducing-the-entity-framework-provider-model"></a>Wprowadzenie do modelu dostawcy programu Entity Framework  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Jest niezależna bazy danych i może zapisywać dostawcę przy użyciu modelu dostawcy ADO.NET nawiązać połączenia z różnorodnych źródeł danych.  
  
 Dostawca danych programu Entity Framework (utworzona przy użyciu dostawcy danych ADO.NET modelu) wykonuje następujące funkcje:  
  
-   Mapuje typy dostawców typów pierwotnych modelu danych jednostki (EDM).  
  
-   Opisuje funkcje właściwe dla dostawcy.  
  
-   Generuje poleceń specyficznych dla dostawcy dla danego DbQueryCommandTree do obsługi [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zapytania.  
  
-   Generuje poleceń specyficznych dla dostawcy aktualizacji dla danego DbModificationCommandTree do obsługi aktualizacji za pomocą [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
-   Udostępnia mapowanie plików dla definicji schematu magazynu do obsługi generowania modelu na podstawie bazy danych.  
  
-   Przedstawia metadanych (tabele i widoki, na przykład) za pomocą modelu koncepcyjnego.  
  
 ![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")  
  
## <a name="sample"></a>Przykład  
 Zobacz [Entity Framework próbki dostawcy](http://go.microsoft.com/fwlink/?LinkId=180616) przykładowe [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dostawcy, który obsługuje źródła danych inne niż SQL Server.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Generowanie kodu SQL](../../../../../docs/framework/data/adonet/ef/sql-generation.md)  
  
 [Modyfikowanie generowania kodu SQL](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)  
  
 [Specyfikacja manifestu dostawcy](../../../../../docs/framework/data/adonet/ef/provider-manifest-specification.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z dostawcami danymi](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)
