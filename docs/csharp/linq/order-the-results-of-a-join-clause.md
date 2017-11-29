---
title: "Kolejność wyników klauzuli join"
description: "Jak kolejność wyników klauzuli join."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f948c18fb16a4f3ac02945b4a63583f1b01cad40
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="order-the-results-of-a-join-clause"></a>Kolejność wyników klauzuli join
Ten przykład przedstawia sposób sortowania wyników operacji tworzenia sprzężenia. Należy pamiętać, że kolejność jest wykonywane po sprzężenia. Chociaż można używać `orderby` klauzuli z co najmniej jednym źródle sekwencji przed sprzężenia, zazwyczaj nie zaleca się jej. Niektórzy dostawcy LINQ nie może zachować kolejność po sprzężenia.  
  
## <a name="example"></a>Przykład  
 To zapytanie tworzy sprzężenie grupy, a następnie sortuje oparte na element kategorii, który jest nadal w zakresie grupy. Wewnątrz inicjatora typu anonimowego podzapytania zamówień zgodnych elementów z sekwencji produktów.  
  
 [!code-csharp[csProgGuideLINQ#81](../../../samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]  
 
## <a name="see-also"></a>Zobacz także  
 [Wyrażenia zapytań LINQ](index.md)  
 [Klauzula OrderBy](../language-reference/keywords/orderby-clause.md)  
 [JOIN — klauzula](../language-reference/keywords/join-clause.md) 
