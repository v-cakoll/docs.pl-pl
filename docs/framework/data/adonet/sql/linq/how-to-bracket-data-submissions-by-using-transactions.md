---
title: 'Instrukcje: Przesyłanie danych nawiasów za pomocą transakcji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
ms.openlocfilehash: 2cbb50cc8762780849c337b597bbb36631c6ac1b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54584535"
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a>Instrukcje: Przesyłanie danych nawiasów za pomocą transakcji
Możesz użyć <xref:System.Transactions.TransactionScope> do dopasowywanie materiałów przesłanych do bazy danych. Aby uzyskać więcej informacji, zobacz [Obsługa transakcji](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod zawiera przesyłania bazy danych w <xref:System.Transactions.TransactionScope>.  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także
- [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [Tworzenie i przesyłanie zmian danych](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [Obsługa transakcji](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md)
