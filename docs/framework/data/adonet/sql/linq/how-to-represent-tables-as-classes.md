---
title: 'Instrukcje: Reprezentacja tabel jako klas'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: 1169def4e0180b1d14103d4a968ff3ed56f63d0c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781760"
---
# <a name="how-to-represent-tables-as-classes"></a>Instrukcje: Reprezentacja tabel jako klas
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Użyjatrybutu,abywyznaczyćklasęjakoklasęjednostkiskojarzonąz<xref:System.Data.Linq.Mapping.TableAttribute> tabelą bazy danych.  
  
### <a name="to-map-a-class-to-a-database-table"></a>Aby zmapować klasę do tabeli bazy danych  
  
- <xref:System.Data.Linq.Mapping.TableAttribute> Dodaj atrybut do deklaracji klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy kod tworzy `Customer` klasę jako klasę jednostki, która jest skojarzona `Customers` z tabelą bazy danych.  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 Nie trzeba określać <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> właściwości, jeśli można wywnioskować nazwę. Jeśli nie określisz nazwy, przyjmuje się, że nazwa jest taka sama jak nazwa właściwości lub pola.  
  
## <a name="see-also"></a>Zobacz także

- [Model obiektu LINQ to SQL](the-linq-to-sql-object-model.md)
- [Instrukcje: Dostosowywanie klas jednostek przy użyciu edytora kodu](how-to-customize-entity-classes-by-using-the-code-editor.md)
