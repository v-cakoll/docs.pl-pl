---
title: Generowanie kodu SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 39f31e27f1e62d889df5a40a9ecb554c2547db8f
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="sql-generation"></a>Generowanie kodu SQL
Podczas zapisu dostawcę dla [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], muszą tłumaczyć [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] polecenia drzew SQL, który można zrozumieć określonej bazy danych, takich jak języka Transact-SQL dla programu SQL Server lub PL/SQL dla programu Oracle. W tej sekcji przedstawiono tworzenia składnik generowania SQL (do kwerend WYBIERAJĄCYCH) dla [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dostawcy. Informacje o wstawiania, aktualizacji i usunąć zapytania, zobacz [generowanie kodu SQL modyfikacji](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md).  
  
 Aby poznać tę sekcję, należy się zapoznać z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] i Model dostawcy ADO.NET. Należy również poznać drzew poleceń i <xref:System.Data.Common.CommandTrees.DbExpression>.  
  
## <a name="the-role-of-the-sql-generation-module"></a>Rola modułu generowania SQL  
 Moduł generowania SQL z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dostawcy przekształca poziomu drzewa poleceń określonego zapytania w jednej instrukcji SQL SELECT, przeznaczonego dla SQL:1999-zgodny z bazy danych. Wygenerowany SQL powinien mieć jako kilka zagnieżdżonych zapytania jak to możliwe. Moduł generowania SQL nie należy uprościć drzewa poleceń zapytania danych wyjściowych. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Będzie to zrobić, na przykład przez wyeliminowanie sprzężenia i zwijanie węzły kolejnych filtru.  
  
 <xref:System.Data.Common.DbProviderServices> Klasy jest punkt początkowy do uzyskiwania dostępu do warstwy generowania SQL można przekonwertować drzew poleceń w <xref:System.Data.Common.DbCommand>.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Kształt drzew poleceń](../../../../../docs/framework/data/adonet/ef/the-shape-of-the-command-trees.md)  
  
 [Generowanie SQL na podstawie drzew poleceń — najlepsze praktyki](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md)  
  
 [Generowanie kodu SQL w dostawcy próbki](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie dostawca danych programu Entity Framework](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
