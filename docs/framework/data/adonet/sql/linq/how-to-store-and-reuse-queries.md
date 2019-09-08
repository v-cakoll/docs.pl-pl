---
title: 'Instrukcje: Przechowywanie i ponowne użycie zapytań'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a012bd79-1809-45e3-adea-0229532396cc
ms.openlocfilehash: c023f7610576c017c91fdb919322acdf9003767a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781642"
---
# <a name="how-to-store-and-reuse-queries"></a>Instrukcje: Przechowywanie i ponowne użycie zapytań
W przypadku aplikacji, która wielokrotnie wykonuje podobne zapytania strukturalnie, często można zwiększyć wydajność, kompilując zapytanie jeden raz i wykonując je kilka razy z innymi parametrami. Na przykład aplikacja może wymagać pobrania wszystkich klientów, którzy znajdują się w konkretnym mieście, gdzie miasto jest określone w czasie wykonywania przez użytkownika w formularzu. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]obsługuje w tym celu użycie *skompilowanych zapytań* .  
  
> [!NOTE]
> Ten wzorzec użycia reprezentuje najczęstsze zastosowania skompilowanych zapytań. Możliwe jest inne podejście. Na przykład skompilowane zapytania mogą być przechowywane jako statyczne elementy członkowskie klasy częściowej, która rozszerza kod generowany przez projektanta.  
  
## <a name="example"></a>Przykład  
 W wielu scenariuszach możesz chcieć ponownie wykorzystać zapytania w granicach wątków. W takich przypadkach przechowywanie skompilowanych zapytań w zmiennych statycznych jest szczególnie skuteczne. W poniższym przykładzie kodu założono `Queries` klasę zaprojektowaną do przechowywania skompilowanych zapytań i przyjmujemy klasę Northwind, która reprezentuje <xref:System.Data.Linq.DataContext>silnie wpisaną wartość.  
  
 [!code-csharp[DLinqQuerying#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#6)]
 [!code-vb[DLinqQuerying#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#6)]  
  
 [!code-csharp[DLinqQuerying#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#7)]
 [!code-vb[DLinqQuerying#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#7)]  
  
## <a name="example"></a>Przykład  
 Obecnie nie można przechowywać (w zmiennych statycznych) zapytań, które zwracają *Typ anonimowy*, ponieważ typ nie ma nazwy, która ma być argumentem ogólnym. Poniższy przykład pokazuje, jak można obejść ten problem, tworząc typ, który może reprezentować wynik, a następnie użyć go jako argumentu rodzajowego.  
  
 [!code-csharp[DLinqQuerying#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#8)]
 [!code-vb[DLinqQuerying#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#8)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.Linq.CompiledQuery>
- [Pojęcia dotyczące zapytań](query-concepts.md)
- [Wykonywanie zapytania w bazie danych](querying-the-database.md)
