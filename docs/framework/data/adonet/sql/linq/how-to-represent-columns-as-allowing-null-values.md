---
title: 'Instrukcje: Reprezentacja kolumn jako dopuszczających wartości Null'
ms.date: 03/30/2017
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
ms.openlocfilehash: ef8fa87963b91ef7140fbaefb657fc7904604b5b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902918"
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a>Instrukcje: Reprezentacja kolumn jako dopuszczających wartości Null
Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby określić, że kolumny skojarzonej bazy danych może zawierać wartości null.  
  
 Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a>Aby wyznaczyć kolumn jako dopuszczających wartości null  
  
1. Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.  
  
2. Ustaw <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> wartość właściwości `true`.  
  
## <a name="see-also"></a>Zobacz także

- [Model obiektu LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
