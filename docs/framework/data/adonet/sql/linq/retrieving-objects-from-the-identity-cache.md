---
title: Pobieranie obiektów z pamięci podręcznej tożsamości
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96c13903-ccb6-4a0e-ab6a-8ca955ca314d
ms.openlocfilehash: 702d88f844f00b86e64404bd100fd6b3d34971c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211234"
---
# <a name="retrieving-objects-from-the-identity-cache"></a>Pobieranie obiektów z pamięci podręcznej tożsamości
W tym temacie opisano rodzaje LINQ do zapytań SQL, które zwracają obiekt z pamięci podręcznej tożsamości zarządzanych przez <xref:System.Data.Linq.DataContext>.  
  
 W składniku LINQ to SQL jednym ze sposobów, w którym <xref:System.Data.Linq.DataContext> zarządza obiektami polega rejestrowanie tożsamości obiektów w pamięci podręcznej tożsamości, gdy zapytania są wykonywane. W niektórych przypadkach LINQ to SQL będzie próbował pobrać obiekt z pamięci podręcznej tożsamości przed wykonaniem kwerendy w bazie danych.  
  
 Ogólnie rzecz biorąc dla programu LINQ do kwerendy SQL zwrócić obiekt z pamięci podręcznej tożsamości zapytania muszą być oparte na kluczu podstawowym obiektu i musi zwracać pojedynczy obiekt. W szczególności zapytanie musi być w jednym z formularzy ogólne, pokazano poniżej.  
  
> [!NOTE]
>  Wstępnie skompilowanym zapytania nie będzie zwracać obiekty z pamięci podręcznej tożsamości. Aby dowiedzieć się więcej o wstępnie skompilowanym zapytań, zobacz <xref:System.Data.Linq.CompiledQuery> i [jak: Store i ponowne użycie zapytań](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md).  
  
 Zapytanie musi mieć jedną z następujących form ogólne, aby pobrać obiekt z pamięci podręcznej tożsamości:  
  
-   <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`  
  
-   <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`  
  
 W tych formularzach ogólne `Function1`, `Function2`, i `predicate` są zdefiniowane w następujący sposób.  
  
 `Function1` może być dowolny z następujących czynności:  
  
-   <xref:System.Linq.Queryable.Where%2A>  
  
-   <xref:System.Linq.Queryable.First%2A>  
  
-   <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
-   <xref:System.Linq.Queryable.Single%2A>  
  
-   <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `Function2` może być dowolny z następujących czynności:  
  
-   <xref:System.Linq.Queryable.First%2A>  
  
-   <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
-   <xref:System.Linq.Queryable.Single%2A>  
  
-   <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `predicate` musi być wyrażeniem, w której właściwość klucza podstawowego obiektu jest ustawiony na wartość stałą. Jeśli obiekt ma zdefiniowany przez więcej niż jedną właściwość klucza podstawowego, każda właściwość klucza podstawowego musi być równa wartości stałej. Poniżej przedstawiono przykłady formularza `predicate` należy wykonać:  
  
-   `c => c.PK == constant_value`  
  
-   `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a>Przykład  
 Poniższy kod zawiera przykłady typów LINQ do zapytań SQL, które pobierają obiekt z pamięci podręcznej tożsamości.  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Pojęcia dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Tożsamość obiektu](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
- [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Tożsamość obiektu](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
