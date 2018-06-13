---
title: 'Porady: reprezentuje kluczy podstawowych'
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: dae8603a18318f45182c7148b10b8194e67fd017
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352593"
---
# <a name="how-to-represent-primary-keys"></a>Porady: reprezentuje kluczy podstawowych
Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu do wyznaczenia, właściwości lub pola do reprezentowania klucza podstawowego dla kolumny bazy danych.  
  
 Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie obsługuje kolumn obliczanych jako klucze podstawowe.  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a>Aby określić właściwości lub pola klucza podstawowego  
  
1.  Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> właściwości <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.  
  
2.  Określ wartość jako `true`.  
  
## <a name="see-also"></a>Zobacz też  
 [Model obiektu LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
