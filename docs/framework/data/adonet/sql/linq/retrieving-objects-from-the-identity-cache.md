---
title: Pobieranie obiektów z pamięci podręcznej tożsamości
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96c13903-ccb6-4a0e-ab6a-8ca955ca314d
ms.openlocfilehash: fe22dbdff0e5e9ea6bfe55fc24c492414e01cd6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357611"
---
# <a name="retrieving-objects-from-the-identity-cache"></a>Pobieranie obiektów z pamięci podręcznej tożsamości
W tym temacie opisano typy LINQ do zapytania SQL, które zwracają obiekt z pamięci podręcznej tożsamości zarządzanych przez <xref:System.Data.Linq.DataContext>.  
  
 W składniku LINQ to SQL sposoby, w którym <xref:System.Data.Linq.DataContext> zarządza obiektów jest przez funkcję rejestrowania tożsamości obiektów w pamięci podręcznej tożsamości, jak są wykonywane zapytania. W niektórych przypadkach LINQ do SQL spróbuje pobrać obiekt z pamięci podręcznej tożsamości przed wykonaniem kwerendy w bazie danych.  
  
 Ogólnie rzecz biorąc dla zapytania składnika LINQ to SQL zwrócić obiekt z pamięci podręcznej tożsamości, zapytanie musi być oparta na kluczu podstawowym obiektu i musi zwracać pojedynczego obiektu. W szczególności zapytania musi być w jednym z formularze ogólne, pokazano poniżej.  
  
> [!NOTE]
>  Wstępnie skompilowane zapytania nie zwróci obiektów z pamięci podręcznej tożsamości. Aby uzyskać więcej informacji o wstępnie skompilowanym zapytań, zobacz <xref:System.Data.Linq.CompiledQuery> i [porady: Magazyn i ponowne użycie zapytania](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md).  
  
 Zapytanie musi mieć jedną z następujących postaci ogólne można pobrać obiektu z pamięci podręcznej tożsamości:  
  
-   <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`  
  
-   <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`  
  
 W tych formularze ogólne `Function1`, `Function2`, i `predicate` są zdefiniowane w następujący sposób.  
  
 `Function1` może być jedną z następujących czynności:  
  
-   <xref:System.Linq.Queryable.Where%2A>  
  
-   <xref:System.Linq.Queryable.First%2A>  
  
-   <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
-   <xref:System.Linq.Queryable.Single%2A>  
  
-   <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `Function2` może być jedną z następujących czynności:  
  
-   <xref:System.Linq.Queryable.First%2A>  
  
-   <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
-   <xref:System.Linq.Queryable.Single%2A>  
  
-   <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `predicate` musi być wyrażeniem, w którym właściwości klucza podstawowego obiektu ma ustawioną wartość stałą. Jeśli obiekt ma zdefiniowany przez więcej niż jedną właściwość klucza podstawowego, każda właściwość klucza podstawowego musi mieć ustawioną wartość stałą. Poniżej podano przykłady formularza `predicate` należy wykonać:  
  
-   `c => c.PK == constant_value`  
  
-   `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a>Przykład  
 Poniższy kod zawiera przykłady typów LINQ do zapytań SQL, które pobrać obiekt z pamięci podręcznej tożsamości.  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [Tożsamość obiektu](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)  
 [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Tożsamość obiektu](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
