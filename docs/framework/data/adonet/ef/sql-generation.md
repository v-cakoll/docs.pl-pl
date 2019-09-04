---
title: Generowanie kodu SQL
ms.date: 03/30/2017
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
ms.openlocfilehash: 2c18e88967fcba2b8414bfc171412eba908002b3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248401"
---
# <a name="sql-generation"></a>Generowanie kodu SQL
Podczas pisania dostawcy dla programu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]należy przetłumaczyć [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] drzewa poleceń na SQL, które może zrozumieć konkretna baza danych, na przykład Transact-SQL dla SQL Server lub pl/SQL dla firmy Oracle. W tej sekcji dowiesz się, jak opracowywać składnik generacji SQL (dla wybranych zapytań) dla [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dostawcy. Aby uzyskać informacje na temat zapytań INSERT, Update i DELETE, zobacz [Modyfikowanie generacji SQL](modification-sql-generation.md).  
  
 Aby zrozumieć tę sekcję, należy zapoznać się z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] modelem dostawcy usług i ADO.NET. Należy również zrozumieć drzewa poleceń i <xref:System.Data.Common.CommandTrees.DbExpression>.  
  
## <a name="the-role-of-the-sql-generation-module"></a>Rola modułu generacji SQL  
 Moduł generowania kodu SQL [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dostawcy tłumaczy określone drzewo poleceń zapytania na pojedynczą instrukcję SQL SELECT, która jest przeznaczona dla bazy danych zgodnej z programem SQL: 1999. Wygenerowany kod SQL powinien zawierać co najmniej kilka zagnieżdżonych zapytań. Moduł generowania kodu SQL nie powinien uprościć drzewa poleceń kwerendy wyjściowej. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Wykona to na przykład przez wyeliminowanie sprzężeń i zwijanie kolejnych węzłów filtru.  
  
 Klasa jest punktem początkowym uzyskiwania dostępu do warstwy generowania kodu SQL w celu konwertowania drzew poleceń <xref:System.Data.Common.DbCommand>na. <xref:System.Data.Common.DbProviderServices>  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Kształt drzew poleceń](the-shape-of-the-command-trees.md)  
  
 [Generowanie kodu SQL na podstawie drzew poleceń — najlepsze praktyki](generating-sql-from-command-trees-best-practices.md)  
  
 [Generowanie kodu SQL w dostawcy próbki](sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a>Zobacz także

- [Pisanie dostawcy danych programu Entity Framework](writing-an-ef-data-provider.md)
