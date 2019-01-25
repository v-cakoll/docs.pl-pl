---
title: 'Instrukcje: Wyświetlanie zestawu zmian'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 126e7245-c5a0-4ebf-800d-cc1fcf9cd0ab
ms.openlocfilehash: 773e72d52a934bc7c6fa80fe252d62e67f87a34b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596803"
---
# <a name="how-to-display-a-changeset"></a><span data-ttu-id="fa5dd-102">Instrukcje: Wyświetlanie zestawu zmian</span><span class="sxs-lookup"><span data-stu-id="fa5dd-102">How to: Display a ChangeSet</span></span>
<span data-ttu-id="fa5dd-103">Możesz wyświetlić zmiany śledzone przez <xref:System.Data.Linq.DataContext> przy użyciu <xref:System.Data.Linq.DataContext.GetChangeSet%2A>.</span><span class="sxs-lookup"><span data-stu-id="fa5dd-103">You can view changes tracked by a <xref:System.Data.Linq.DataContext> by using <xref:System.Data.Linq.DataContext.GetChangeSet%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa5dd-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa5dd-104">Example</span></span>  
 <span data-ttu-id="fa5dd-105">Poniższy przykład pobiera klientów, których Miasto jest Londyn, zmienia nazwę miasta do Paryża i przesyła zmiany z powrotem do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="fa5dd-105">The following example retrieves customers whose city is London, changes the city to Paris, and submits the changes back to the database.</span></span>  
  
 [!code-csharp[DLinqDebuggingSupport#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#2)]
 [!code-vb[DLinqDebuggingSupport#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#2)]  
  
 <span data-ttu-id="fa5dd-106">Dane wyjściowe z tego kodu pojawi się podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="fa5dd-106">Output from this code appears similar to the following.</span></span> <span data-ttu-id="fa5dd-107">Pamiętaj, że podsumowanie na końcu pokazuje, że ośmiu zmiany zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="fa5dd-107">Note that the summary at the end shows that eight changes were made.</span></span>  
  
 `CustomerID: AROUT`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: BSBEV`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: CONSH`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: EASTC`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: NORTS`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: PARIS`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: SEVES`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 `CustomerID: SPECD`  
  
 `Original value: London`  
  
 `Updated value: Paris`  
  
 ``  
  
 `Total changes: {Added: 0, Removed: 0, Modified: 8}`  
  
## <a name="see-also"></a><span data-ttu-id="fa5dd-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fa5dd-108">See also</span></span>
- [<span data-ttu-id="fa5dd-109">Obsługa debugowania</span><span class="sxs-lookup"><span data-stu-id="fa5dd-109">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)
