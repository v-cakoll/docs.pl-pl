---
title: 'Instrukcje: Reprezentacja kluczy podstawowych'
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: 5df82292f000d7f5e61cab699237b86de30bda70
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793434"
---
# <a name="how-to-represent-primary-keys"></a>Instrukcje: Reprezentacja kluczy podstawowych
Użyj właściwości w atrybucie, <xref:System.Data.Linq.Mapping.ColumnAttribute> aby wyznaczyć właściwość lub pole reprezentujące klucz podstawowy dla kolumny bazy danych. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
 Aby zapoznać się z przykładami kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Program nie obsługuje kolumn obliczanych jako kluczy podstawowych.  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a>Aby wyznaczyć właściwość lub pole jako klucz podstawowy  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> Dodaj Właściwość<xref:System.Data.Linq.Mapping.ColumnAttribute> do atrybutu.  
  
2. Określ wartość jako `true`.  
  
## <a name="see-also"></a>Zobacz także

- [Model obiektu LINQ to SQL](the-linq-to-sql-object-model.md)
- [Instrukcje: Dostosowywanie klas jednostek przy użyciu edytora kodu](how-to-customize-entity-classes-by-using-the-code-editor.md)
