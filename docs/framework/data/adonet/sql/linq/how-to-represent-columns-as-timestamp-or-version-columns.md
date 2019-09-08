---
title: 'Instrukcje: Reprezentacja kolumn jako kolumn znacznika czasu lub wersji'
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: ef99e0420b328f94686e08256ecf229000467810
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793503"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a>Instrukcje: Reprezentacja kolumn jako kolumn znacznika czasu lub wersji
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Użyj<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> właściwości atrybutu<xref:System.Data.Linq.Mapping.ColumnAttribute> , aby wyznaczyć pole lub właściwość w postaci kolumny bazy danych zawierającej sygnatury czasowe bazy danych lub numery wersji.  
  
 Aby zapoznać się z przykładami kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a>Aby wyznaczyć pole lub właściwość jako kolumnę sygnatury czasowej lub wersji  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> Dodaj Właściwość<xref:System.Data.Linq.Mapping.ColumnAttribute> do atrybutu.  
  
2. `true`Ustaw wartość <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> właściwości na.  
  
## <a name="see-also"></a>Zobacz także

- [Model obiektu LINQ to SQL](the-linq-to-sql-object-model.md)
- [Instrukcje: Określ, które składowe są testowane pod kątem konfliktów współbieżności](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [Instrukcje: Dostosowywanie klas jednostek przy użyciu edytora kodu](how-to-customize-entity-classes-by-using-the-code-editor.md)
