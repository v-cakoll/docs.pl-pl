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
ms.workload: dotnet
ms.openlocfilehash: 60f07a629c981eb0ad72f7c3e2d8537d5ca77515
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-database-data-types"></a>Porady: Określanie typów danych bazy danych
Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu podaj dokładny tekst, który definiuje kolumnę w deklaracji tabeli T-SQL.  
  
 Należy określić <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> właściwość tylko wtedy, gdy planujesz używać <xref:System.Data.Linq.DataContext.CreateDatabase%2A> można utworzyć wystąpienia bazy danych.  
  
 Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a>Aby określić tekst, który ma typ danych w tabeli T-SQL  
  
1.  Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> właściwości <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.  
  
2.  Ustaw wartość <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> właściwość, aby dokładnie tekst, który jest używany przez T-SQL.  
  
## <a name="see-also"></a>Zobacz też  
 [Model obiektu LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
