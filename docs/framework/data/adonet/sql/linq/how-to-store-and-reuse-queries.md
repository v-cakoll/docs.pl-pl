---
title: "Porady: przechowywanie i ponowne użycie zapytań"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a012bd79-1809-45e3-adea-0229532396cc
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a1d0e0a094148e609dddcb703bd3840d091af8d3
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-store-and-reuse-queries"></a>Porady: przechowywanie i ponowne użycie zapytań
Jeśli masz aplikację, która wykonuje zapytania strukturę podobną tyle razy, często może zwiększyć wydajność kompilacji zapytania jeden raz i jej wykonanie kilka razy z innymi parametrami. Na przykład aplikacja może mieć można pobrać wszystkich klientów, którzy są określonego miasta, w którym miasta jest określone w czasie wykonywania przez użytkownika w postaci. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]obsługuje korzystanie z *skompilowane zapytania* w tym celu.  
  
> [!NOTE]
>  Ten wzorzec użycia reprezentuje najbardziej popularnym zastosowaniem zapytań skompilowany. Możliwe są inne podejścia. Na przykład skompilowane zapytania mogą być przechowywane jako statyczne elementy członkowskie dla częściowej klasy, która rozszerza kod wygenerowany przez projektanta.  
  
## <a name="example"></a>Przykład  
 W wielu scenariuszach można ponownie użyć zapytania w granicach wątku. W takich przypadkach zapisanie skompilowane zapytania w zmienne statyczne jest szczególnie użyteczna. Poniższy przykład kodu zakłada `Queries` klasy przeznaczone do przechowywania skompilowanych zapytania i przyjęto założenie, reprezentujący silnie typizowaną klasę Northwind <xref:System.Data.Linq.DataContext>.  
  
 [!code-csharp[DLinqQuerying#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#6)]
 [!code-vb[DLinqQuerying#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#6)]  
  
 [!code-csharp[DLinqQuerying#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#7)]
 [!code-vb[DLinqQuerying#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#7)]  
  
## <a name="example"></a>Przykład  
 Nie można obecnie zapytań magazynu (w zmiennych statycznych), które zwracają *typu anonimowego*, ponieważ typ nie ma nazwy zapewnienie jako argument rodzajowy. W poniższym przykładzie pokazano, jak można obejść ten problem, tworząc typu, który reprezentuje wynik, a następnie użyć jej jako argument rodzajowy.  
  
 [!code-csharp[DLinqQuerying#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#8)]
 [!code-vb[DLinqQuerying#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#8)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Data.Linq.CompiledQuery>  
 [Pojęcia dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [Wykonywanie zapytania w bazie danych](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
