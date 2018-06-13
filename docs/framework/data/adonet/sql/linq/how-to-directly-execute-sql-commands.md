---
title: 'Porady: bezpośrednio wykonania polecenia SQL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 04671bb0-40c0-4465-86e5-77986f454661
ms.openlocfilehash: 90fb0d7027946ce4f38c2ba4930ac3510e2a42b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351875"
---
# <a name="how-to-directly-execute-sql-commands"></a>Porady: bezpośrednio wykonania polecenia SQL
Zakładając, że <xref:System.Data.Linq.DataContext> połączenia, można użyć <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> do wykonania polecenia SQL, które niezwracanie obiektów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład powoduje, że serwer SQL do zwiększenia UnitPrice 1,00.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#3)]
 [!code-vb[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Bezpośrednie wykonywanie zapytań SQL](../../../../../../docs/framework/data/adonet/sql/linq/how-to-directly-execute-sql-queries.md)  
 [Komunikacja z bazą danych](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
