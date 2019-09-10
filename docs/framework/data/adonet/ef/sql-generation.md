---
title: Generowanie kodu SQL
ms.date: 03/30/2017
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
ms.openlocfilehash: 9c5301d3f4d5bc2e0db4a138c6d8ceb06d3a7845
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854356"
---
# <a name="sql-generation"></a>Generowanie kodu SQL
Podczas pisania dostawcy dla Entity Framework należy przetłumaczyć drzewa poleceń Entity Framework na SQL, które mogą zrozumieć konkretną bazę danych, na przykład Transact-SQL dla SQL Server lub PL/SQL dla firmy Oracle. W tej sekcji dowiesz się, jak opracowywać składnik generacji SQL (dla wybranych zapytań) dla dostawcy Entity Framework. Aby uzyskać informacje na temat zapytań INSERT, Update i DELETE, zobacz [Modyfikowanie generacji SQL](modification-sql-generation.md).  
  
 Aby zrozumieć tę sekcję, należy zapoznać się z Entity Framework i modelem dostawcy ADO.NET. Należy również zrozumieć drzewa poleceń i <xref:System.Data.Common.CommandTrees.DbExpression>.  
  
## <a name="the-role-of-the-sql-generation-module"></a>Rola modułu generacji SQL  
 Moduł generowania kodu SQL dostawcy Entity Framework tłumaczy określone drzewo poleceń zapytania na pojedynczą instrukcję SQL SELECT, która jest przeznaczona dla bazy danych zgodnej z programem SQL: 1999. Wygenerowany kod SQL powinien zawierać co najmniej kilka zagnieżdżonych zapytań. Moduł generowania kodu SQL nie powinien uprościć drzewa poleceń kwerendy wyjściowej. Entity Framework wykona to na przykład przez wyeliminowanie sprzężeń i zwijanie kolejnych węzłów filtru.  
  
 Klasa jest punktem początkowym uzyskiwania dostępu do warstwy generowania kodu SQL w celu konwertowania drzew poleceń <xref:System.Data.Common.DbCommand>na. <xref:System.Data.Common.DbProviderServices>  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Kształt drzew poleceń](the-shape-of-the-command-trees.md)  
  
 [Generowanie kodu SQL na podstawie drzew poleceń — najlepsze praktyki](generating-sql-from-command-trees-best-practices.md)  
  
 [Generowanie kodu SQL w dostawcy próbki](sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a>Zobacz także

- [Pisanie dostawcy danych programu Entity Framework](writing-an-ef-data-provider.md)
