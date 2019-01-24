---
title: 'Instrukcje: Reprezentuje kolumn jako sygnatura czasowa lub kolumny wersji'
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: fa9ffe01c45df3ce0342b62e12007ddf88ee412d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674573"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a>Instrukcje: Reprezentuje kolumn jako sygnatura czasowa lub kolumny wersji
Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby wyznaczyć reprezentująca kolumnę w bazie danych, który zawiera numery wersji lub sygnatur czasowych bazy danych do pola lub właściwości.  
  
 Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a>Aby wyznaczyć reprezentujący kolumnę sygnatur czasowych lub wersji pola lub właściwości  
  
1.  Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.  
  
2.  Ustaw <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> wartość właściwości `true`.  
  
## <a name="see-also"></a>Zobacz także
- [Model obiektu LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Instrukcje: Określ, której członkami są sprawdzane pod kątem konfliktów współbieżności](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
