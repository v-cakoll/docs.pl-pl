---
title: 'Instrukcje: Reprezentacja kolumn jako dopuszczających wartości Null'
ms.date: 03/30/2017
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
ms.openlocfilehash: 00a837467010c2d8a9f0ca16d6aba2fc5f4c973f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781811"
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a>Instrukcje: Reprezentacja kolumn jako dopuszczających wartości Null
Użyj właściwości w<xref:System.Data.Linq.Mapping.ColumnAttribute> atrybucie, aby określić, że skojarzona kolumna bazy danych może zawierać wartości null. <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
 Aby zapoznać się z przykładami kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a>Aby wyznaczyć kolumnę jako zezwalającą na wartości null  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> Dodaj Właściwość<xref:System.Data.Linq.Mapping.ColumnAttribute> do atrybutu.  
  
2. `true`Ustaw wartość <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> właściwości na.  
  
## <a name="see-also"></a>Zobacz także

- [Model obiektu LINQ to SQL](the-linq-to-sql-object-model.md)
- [Instrukcje: Dostosowywanie klas jednostek przy użyciu edytora kodu](how-to-customize-entity-classes-by-using-the-code-editor.md)
