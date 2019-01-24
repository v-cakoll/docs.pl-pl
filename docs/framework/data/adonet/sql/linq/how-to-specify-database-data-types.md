---
title: 'Instrukcje: Określanie typów danych bazy danych'
ms.date: 03/30/2017
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
ms.openlocfilehash: 566ff545cd493eed637093c378aacc865a7f5e20
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620490"
---
# <a name="how-to-specify-database-data-types"></a>Instrukcje: Określanie typów danych bazy danych
Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby określić dokładną tekst, który definiuje kolumnę w deklaracji tabeli języka T-SQL.  
  
 Należy określić <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> właściwości tylko wtedy, gdy planujesz używać <xref:System.Data.Linq.DataContext.CreateDatabase%2A> do utworzenia wystąpienia bazy danych.  
  
 Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a>Aby określić tekst, aby zdefiniować typ danych w tabeli języka T-SQL  
  
1.  Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.  
  
2.  Ustaw wartość <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> właściwości tekstu do dokładnego dopasowania, który jest używany przez język T-SQL.  
  
## <a name="see-also"></a>Zobacz także
- [Model obiektu LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
