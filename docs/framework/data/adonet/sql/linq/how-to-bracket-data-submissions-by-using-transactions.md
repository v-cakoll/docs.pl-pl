---
title: 'Instrukcje: Przesyłanie danych nawiasów za pomocą transakcji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
ms.openlocfilehash: 6a4c5ba7c4938b48fe489e43ff4a3ff806bd8916
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793807"
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a>Instrukcje: Przesyłanie danych nawiasów za pomocą transakcji
Możesz użyć <xref:System.Transactions.TransactionScope> , aby przenawiasować przesłanie do bazy danych. Aby uzyskać więcej informacji, zobacz [Obsługa transakcji](transaction-support.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod obejmuje przesyłanie bazy danych w <xref:System.Transactions.TransactionScope>.  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Pobieranie przykładowych baz danych](downloading-sample-databases.md)
- [Tworzenie i przesyłanie zmian danych](making-and-submitting-data-changes.md)
- [Obsługa transakcji](transaction-support.md)
