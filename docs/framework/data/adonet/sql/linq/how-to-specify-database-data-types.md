---
title: 'Instrukcje: Określanie typów danych bazy danych'
ms.date: 03/30/2017
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
ms.openlocfilehash: 09ca8dc6fa440138523bcd2905335a04517dd806
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793272"
---
# <a name="how-to-specify-database-data-types"></a>Instrukcje: Określanie typów danych bazy danych
Użyj właściwości dla<xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby określić dokładny tekst, który definiuje kolumnę w deklaracji tabeli T-SQL. <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> Właściwość należy określić tylko wtedy, gdy planujesz użyć <xref:System.Data.Linq.DataContext.CreateDatabase%2A> , aby utworzyć wystąpienie bazy danych.  
  
 Aby zapoznać się z przykładami kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a>Aby określić tekst definiujący typ danych w tabeli T-SQL  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> Dodaj Właściwość<xref:System.Data.Linq.Mapping.ColumnAttribute> do atrybutu.  
  
2. Ustaw wartość <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> właściwości na dokładny tekst, który jest używany przez język T-SQL.  
  
## <a name="see-also"></a>Zobacz także

- [Model obiektu LINQ to SQL](the-linq-to-sql-object-model.md)
- [Instrukcje: Dostosowywanie klas jednostek przy użyciu edytora kodu](how-to-customize-entity-classes-by-using-the-code-editor.md)
