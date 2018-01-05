---
title: "Wyłącznie Dostosowywanie operacje przy użyciu procedur składowanych"
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
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: eba9e4462c1a71708173994dfb3efaf4199248c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a>Wyłącznie Dostosowywanie operacje przy użyciu procedur składowanych
Dostęp do danych za pomocą tylko procedury składowane jest typowym scenariuszem.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Można zmodyfikować w przykładzie [Dostosowywanie operacji przez przy użyciu procedur składowanych](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md) zamieniając wywołania metody, która opakowuje procedury składowanej nawet pierwszego zapytania (co powoduje, że dynamiczne wykonywania instrukcji SQL).  
  
 Załóżmy `CustomersByCity` to metoda, jak w poniższym przykładzie.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 Poniższy kod wykonuje bez żadnych dynamiczne SQL.  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Zobacz też  
 [Obowiązki dewelopera podczas zastępowania domyślnego zachowania](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
