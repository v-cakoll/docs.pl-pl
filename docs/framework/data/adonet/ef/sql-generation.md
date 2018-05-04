---
title: Generowanie kodu SQL
ms.date: 03/30/2017
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
ms.openlocfilehash: e130fed22b9ea450c848d45195346dc717e63515
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="sql-generation"></a>Generowanie kodu SQL
Podczas zapisu dostawcę dla [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], muszą tłumaczyć [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] polecenia drzew SQL, który można zrozumieć określonej bazy danych, takich jak języka Transact-SQL dla programu SQL Server lub PL/SQL dla programu Oracle. W tej sekcji przedstawiono tworzenia składnik generowania SQL (do kwerend WYBIERAJĄCYCH) dla [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dostawcy. Informacje o wstawiania, aktualizacji i usunąć zapytania, zobacz [generowanie kodu SQL modyfikacji](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md).  
  
 Aby poznać tę sekcję, należy się zapoznać z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] i Model dostawcy ADO.NET. Należy również poznać drzew poleceń i <xref:System.Data.Common.CommandTrees.DbExpression>.  
  
## <a name="the-role-of-the-sql-generation-module"></a>Rola modułu generowania SQL  
 Moduł generowania SQL z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dostawcy przekształca poziomu drzewa poleceń określonego zapytania w jednej instrukcji SQL SELECT, przeznaczonego dla SQL:1999-zgodny z bazy danych. Wygenerowany SQL powinien mieć jako kilka zagnieżdżonych zapytania jak to możliwe. Moduł generowania SQL nie należy uprościć drzewa poleceń zapytania danych wyjściowych. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Będzie to zrobić, na przykład przez wyeliminowanie sprzężenia i zwijanie węzły kolejnych filtru.  
  
 <xref:System.Data.Common.DbProviderServices> Klasy jest punkt początkowy do uzyskiwania dostępu do warstwy generowania SQL można przekonwertować drzew poleceń w <xref:System.Data.Common.DbCommand>.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Kształt drzew poleceń](../../../../../docs/framework/data/adonet/ef/the-shape-of-the-command-trees.md)  
  
 [Generowanie kodu SQL na podstawie drzew poleceń — najlepsze praktyki](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md)  
  
 [Generowanie kodu SQL w dostawcy próbki](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie dostawcy danych programu Entity Framework](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
