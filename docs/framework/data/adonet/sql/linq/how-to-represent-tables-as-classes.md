---
title: 'Porady: reprezentuje tabele jako klasy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: 363efa4e4a6e3e7cfb757ee554e24a7963882278
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362980"
---
# <a name="how-to-represent-tables-as-classes"></a>Porady: reprezentuje tabele jako klasy
Użyj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> atrybutu, aby wyznaczyć klasy klasę jednostki skojarzonej z tabelą bazy danych.  
  
### <a name="to-map-a-class-to-a-database-table"></a>Do mapowania klasy tabeli bazy danych  
  
-   Dodaj <xref:System.Data.Linq.Mapping.TableAttribute> atrybutu deklaracji klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy kod ustanawia `Customer` jak klasa jednostki, z którym skojarzony jest `Customers` tabeli bazy danych.  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 Nie trzeba określać <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> właściwości, jeśli można wywnioskować nazwy. Jeśli nie określisz nazwy, nazwa jest uznawany za taką samą nazwę jak właściwości lub pola.  
  
## <a name="see-also"></a>Zobacz też  
 [Model obiektu LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
