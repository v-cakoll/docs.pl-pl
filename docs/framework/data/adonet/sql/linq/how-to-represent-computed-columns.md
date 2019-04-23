---
title: 'Instrukcje: Reprezentacja kolumn obliczanych'
ms.date: 03/30/2017
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
ms.openlocfilehash: df72562b303e5b9a7c31334df06926f157b59b05
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59324745"
---
# <a name="how-to-represent-computed-columns"></a>Instrukcje: Reprezentacja kolumn obliczanych
Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu do reprezentowania kolumny, w których zawartość jest wynik obliczenia.  
  
 Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie obsługuje kolumn obliczanych jako klucze podstawowe.  
  
### <a name="to-represent-a-computed-column"></a>Do reprezentowania kolumny obliczanej  
  
1. Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.  
  
2. Reprezentacja ciągu formułę, aby przypisać <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> właściwości.  
  
## <a name="see-also"></a>Zobacz także

- [Model obiektu LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
