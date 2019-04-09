---
title: 'Instrukcje: Przechowywanie i ponowne użycie zapytań'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a012bd79-1809-45e3-adea-0229532396cc
ms.openlocfilehash: 1aac20c3f9c421d353938a83b9e321d35abd244e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084197"
---
# <a name="how-to-store-and-reuse-queries"></a>Instrukcje: Przechowywanie i ponowne użycie zapytań
Jeśli masz aplikację, która wykonuje zapytania strukturalnie podobne wiele razy, często może zwiększyć wydajność, kompilowanie zapytania jeden raz i jej wykonanie kilka razy z różnymi parametrami. Na przykład aplikacja może mieć do pobrania wszystkich klientów, którzy należą do określonego miasta, gdzie to Miasto jest określone w czasie wykonywania przez użytkownika w postaci. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje używanie *skompilowany zapytania* do tego celu.  
  
> [!NOTE]
>  Ten wzorzec użycia reprezentuje najbardziej popularnym zastosowaniem zapytania skompilowane. Możliwe są inne podejścia. Na przykład zapytania skompilowane mogą być przechowywane jako statyczne elementy członkowskie na częściową klasą, która rozszerza kod wygenerowany przez projektanta.  
  
## <a name="example"></a>Przykład  
 W wielu scenariuszach można ponownie użyć zapytań w granicach wątku. W takich przypadkach zapisanie zapytania skompilowane w statycznych zmiennych jest szczególnie efektywna. Poniższy przykład kodu zakłada `Queries` klasę zaprojektowaną do przechowywania skompilowanych zapytań i przyjęto założenie, klasa Northwind, która reprezentuje silnie typizowaną <xref:System.Data.Linq.DataContext>.  
  
 [!code-csharp[DLinqQuerying#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#6)]
 [!code-vb[DLinqQuerying#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#6)]  
  
 [!code-csharp[DLinqQuerying#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#7)]
 [!code-vb[DLinqQuerying#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#7)]  
  
## <a name="example"></a>Przykład  
 Nie można obecnie zapytań magazynu (w zmiennych statycznych), które zwracają *typu anonimowego*, ponieważ typ nie ma nazwy można przekazać jako argument ogólny. Poniższy przykład pokazuje, jak możesz obejść ten problem, tworząc typ, który reprezentuje wynik, a następnie użyj go jako argument ogólny.  
  
 [!code-csharp[DLinqQuerying#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#8)]
 [!code-vb[DLinqQuerying#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#8)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.Linq.CompiledQuery>
- [Pojęcia dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [wykonywanie zapytania w bazie danych](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
