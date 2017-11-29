---
title: "Porady: Określanie typów danych bazy danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d46c63f5944895311e73524a0ba31a126d768522
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-database-data-types"></a>Porady: Określanie typów danych bazy danych
Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu podaj dokładny tekst, który definiuje kolumnę w deklaracji tabeli T-SQL.  
  
 Należy określić <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> właściwość tylko wtedy, gdy planujesz używać <xref:System.Data.Linq.DataContext.CreateDatabase%2A> można utworzyć wystąpienia bazy danych.  
  
 Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a>Aby określić tekst, który ma typ danych w tabeli T-SQL  
  
1.  Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> właściwości <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.  
  
2.  Ustaw wartość <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> właściwość, aby dokładnie tekst, który jest używany przez T-SQL.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do SQL modelu obiektów](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Porady: dostosowywanie klas jednostek za pomocą edytora kodu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
