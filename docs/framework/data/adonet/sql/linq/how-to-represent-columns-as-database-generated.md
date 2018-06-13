---
title: 'Porady: reprezentuje kolumn jako baza danych wygenerowała'
ms.date: 03/30/2017
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
ms.openlocfilehash: f6b127208ae359b43f273f54d7b5c72933c2eba6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353744"
---
# <a name="how-to-represent-columns-as-database-generated"></a>Porady: reprezentuje kolumn jako baza danych wygenerowała
Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby wyznaczyć reprezentująca kolumnę baza danych wygenerowała pola lub właściwości.  
  
 Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a>Aby wyznaczyć reprezentujący kolumny bazy danych, wygenerowane pole lub właściwość  
  
1.  Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> właściwości <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.  
  
2.  Ustaw wartość właściwości `true`.  
  
## <a name="see-also"></a>Zobacz też  
 [Model obiektu LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
