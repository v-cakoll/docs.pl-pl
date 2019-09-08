---
title: 'Instrukcje: Reprezentacja kolumn jako elementów członkowskich klas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
ms.openlocfilehash: 515a8477b3a9c72934e0ad11d7b1bf599e8b16a2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793514"
---
# <a name="how-to-represent-columns-as-class-members"></a>Instrukcje: Reprezentacja kolumn jako elementów członkowskich klas
Użyj atrybutu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , <xref:System.Data.Linq.Mapping.ColumnAttribute> aby skojarzyć pole lub właściwość z kolumną bazy danych.  
  
### <a name="to-map-a-field-or-property-to-a-database-column"></a>Aby zmapować pole lub właściwość do kolumny bazy danych  
  
- <xref:System.Data.Linq.Mapping.ColumnAttribute> Dodaj atrybut do deklaracji właściwości lub pola.  
  
## <a name="example"></a>Przykład  
 Poniższy kod mapuje `CustomerID` pole `Customer` w klasie `Customers` do `CustomerID` kolumny w tabeli bazy danych.  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 Nie trzeba określać <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> właściwości, jeśli można wywnioskować nazwę. Jeśli nie określisz nazwy, przyjmuje się, że nazwa jest taka sama jak nazwa właściwości lub pola.  
  
## <a name="see-also"></a>Zobacz także

- [Model obiektu LINQ to SQL](the-linq-to-sql-object-model.md)
- [Instrukcje: Dostosowywanie klas jednostek przy użyciu edytora kodu](how-to-customize-entity-classes-by-using-the-code-editor.md)
