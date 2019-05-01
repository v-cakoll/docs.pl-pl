---
title: 'Instrukcje: Wyświetlanie zestawu zmian'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 126e7245-c5a0-4ebf-800d-cc1fcf9cd0ab
ms.openlocfilehash: 92acee0d36634ea09c245418fcc7a8b97d208aa6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903113"
---
# <a name="how-to-display-a-changeset"></a>Instrukcje: Wyświetlanie zestawu zmian
Możesz wyświetlić zmiany śledzone przez <xref:System.Data.Linq.DataContext> przy użyciu <xref:System.Data.Linq.DataContext.GetChangeSet%2A>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera klientów, których Miasto jest Londyn, zmienia nazwę miasta do Paryża i przesyła zmiany z powrotem do bazy danych.  
  
 [!code-csharp[DLinqDebuggingSupport#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#2)]
 [!code-vb[DLinqDebuggingSupport#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#2)]  
  
 Dane wyjściowe z tego kodu pojawi się podobne do następujących. Pamiętaj, że podsumowanie na końcu pokazuje, że ośmiu zmiany zostały wprowadzone.  

 ```console
CustomerID: AROUT
   Original value: London
   Updated value: Paris
CustomerID: BSBEV
   Original value: London
   Updated value: Paris
CustomerID: CONSH
   Original value: London
   Updated value: Paris
CustomerID: EASTC
   Original value: London
   Updated value: Paris
CustomerID: NORTS
    Original value: London
    Updated value: Paris
CustomerID: PARIS
    Original value: London
    Updated value: Paris
CustomerID: SEVES
    Original value: London
    Updated value: Paris
CustomerID: SPECD
    Original value: London
    Updated value: Paris
Total changes: {Added: 0, Removed: 0, Modified: 8}
```
  
## <a name="see-also"></a>Zobacz także

- [Obsługa debugowania](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)
