---
title: 'Instrukcje: Reprezentacja kolumn jako elementów członkowskich klas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
ms.openlocfilehash: 009da2579a6fe15cea3913ae5844fc886da2586c
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2019
ms.locfileid: "64910742"
---
# <a name="how-to-represent-columns-as-class-members"></a>Instrukcje: Reprezentacja kolumn jako elementów członkowskich klas
Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby skojarzyć pola lub właściwości z kolumną bazy danych.  
  
### <a name="to-map-a-field-or-property-to-a-database-column"></a>Do mapowania pola lub właściwości kolumny bazy danych  
  
- Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu deklaracji właściwości lub pola.  
  
## <a name="example"></a>Przykład  
 Poniższy kod mapy `CustomerID` pole `Customer` klasy `CustomerID` kolumny w `Customers` tabeli bazy danych.  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 Nie trzeba określać <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> nazwę można wywnioskować właściwość. Jeśli nie określisz nazwy, nazwa jest uznawana za tę taką samą nazwę jak właściwość lub pole.  
  
## <a name="see-also"></a>Zobacz także

- [Model obiektu LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
