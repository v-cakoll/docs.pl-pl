---
title: Dostosowywanie operacji przy użyciu wyłącznie procedur składowanych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
ms.openlocfilehash: 61230ffc5cd055ee64de9d519cdfb4d76c856ca3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59128651"
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a>Dostosowywanie operacji przy użyciu wyłącznie procedur składowanych
Dostęp do danych przy użyciu wyłącznie procedur składowanych jest typowym scenariuszem.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Możesz zmodyfikować przykładu w [Dostosowywanie operacje, przy użyciu procedur składowanych](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md) , zastępując wywołania metody, która otacza procedury składowanej nawet pierwsze zapytanie (co powoduje, że dynamiczne wykonanie instrukcji SQL).  
  
 Załóżmy `CustomersByCity` jest metodą, jak w poniższym przykładzie.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 Poniższy kod wykonuje bez żadnych dynamiczny język SQL.  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- [Obowiązki dewelopera podczas zastępowania domyślnego zachowania](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
