---
title: Kolejność wyników klauzuli join
description: Jak kolejność wyników klauzuli join.
ms.date: 12/1/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f426152e614ed9a9c4aa41d7ba7cb8ddf1cd3063
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="order-the-results-of-a-join-clause"></a>Kolejność wyników klauzuli join
Ten przykład przedstawia sposób sortowania wyników operacji tworzenia sprzężenia. Należy pamiętać, że kolejność jest wykonywane po sprzężenia. Chociaż można używać `orderby` klauzuli z co najmniej jednym źródle sekwencji przed sprzężenia, zazwyczaj nie zaleca się jej. Niektórzy dostawcy LINQ nie może zachować kolejność po sprzężenia.  
  
## <a name="example"></a>Przykład  
 To zapytanie tworzy sprzężenie grupy, a następnie sortuje oparte na element kategorii, który jest nadal w zakresie grupy. Wewnątrz inicjatora typu anonimowego podzapytania zamówień zgodnych elementów z sekwencji produktów.  
  
 [!code-csharp[csProgGuideLINQ#81](../../../samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]  
 
## <a name="see-also"></a>Zobacz także  
 [Wyrażenia zapytań LINQ](index.md)  
 [orderby, klauzula](../language-reference/keywords/orderby-clause.md)  
 [join, klauzula](../language-reference/keywords/join-clause.md) 
