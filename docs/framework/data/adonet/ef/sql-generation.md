---
title: Generowanie kodu SQL
ms.date: 03/30/2017
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
ms.openlocfilehash: 108a68f74849c7fa1418775c2a37db06d9d947ff
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180579"
---
# <a name="sql-generation"></a>Generowanie kodu SQL
Podczas wpisywania dostawcę dla [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], musi przetłumaczyć [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] polecenia drzewa w SQL Server, który może zrozumieć konkretnej bazy danych, takich jak języka Transact-SQL dla programu SQL Server lub PL/SQL dla bazy danych Oracle. W tej sekcji dowiesz sposobu tworzenia składnika generowania SQL (dla zapytań SELECT) dla [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dostawcy. Dla informacji na temat wstawiania, aktualizacji i usuwanie zapytań, zobacz [modyfikowanie generowania kodu SQL](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md).  
  
 Aby dowiedzieć się w tej sekcji, należy się zapoznać z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] i Model dostawcy ADO.NET. Należy również mieć świadomość drzew poleceń i <xref:System.Data.Common.CommandTrees.DbExpression>.  
  
## <a name="the-role-of-the-sql-generation-module"></a>Rola modułu generowania SQL  
 Moduł generowania SQL z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dostawca tłumaczy drzewo poleceń danego zapytania na pojedynczą instrukcję SQL SELECT, który jest przeznaczony dla SQL:1999-zgodności bazy danych. Wygenerowany SQL powinna few zagnieżdżać zapytań jak to możliwe. Moduł generowania SQL nie uprościć drzewo poleceń danych wyjściowych zapytania. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Będziesz to robić, na przykład przez wyeliminowanie sprzężenia i zwijanie filtr kolejnych węzłów.  
  
 <xref:System.Data.Common.DbProviderServices> Klasa jest punktem wyjścia do uzyskiwania dostępu do warstwy generowania SQL, aby przekonwertować drzew poleceń do <xref:System.Data.Common.DbCommand>.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Kształt drzew poleceń](../../../../../docs/framework/data/adonet/ef/the-shape-of-the-command-trees.md)  
  
 [Generowanie kodu SQL na podstawie drzew poleceń — najlepsze praktyki](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md)  
  
 [Generowanie kodu SQL w dostawcy próbki](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a>Zobacz także

- [Pisanie dostawcy danych programu Entity Framework](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
