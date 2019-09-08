---
title: 'Instrukcje: Wyświetlanie zestawu zmian'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 126e7245-c5a0-4ebf-800d-cc1fcf9cd0ab
ms.openlocfilehash: 5f49e123e6e980501d330eeecf2719023cdff8e7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781968"
---
# <a name="how-to-display-a-changeset"></a><span data-ttu-id="3ea05-102">Instrukcje: Wyświetlanie zestawu zmian</span><span class="sxs-lookup"><span data-stu-id="3ea05-102">How to: Display a ChangeSet</span></span>
<span data-ttu-id="3ea05-103">Zmiany śledzone przez <xref:System.Data.Linq.DataContext> program można wyświetlić za pomocą <xref:System.Data.Linq.DataContext.GetChangeSet%2A>polecenia.</span><span class="sxs-lookup"><span data-stu-id="3ea05-103">You can view changes tracked by a <xref:System.Data.Linq.DataContext> by using <xref:System.Data.Linq.DataContext.GetChangeSet%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ea05-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3ea05-104">Example</span></span>  
 <span data-ttu-id="3ea05-105">Poniższy przykład pobiera klientów, których miasto jest Londyn, zmienia miasto na Paryż i przesyła zmiany z powrotem do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="3ea05-105">The following example retrieves customers whose city is London, changes the city to Paris, and submits the changes back to the database.</span></span>  
  
 [!code-csharp[DLinqDebuggingSupport#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#2)]
 [!code-vb[DLinqDebuggingSupport#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#2)]  
  
 <span data-ttu-id="3ea05-106">Dane wyjściowe z tego kodu są podobne do poniższych.</span><span class="sxs-lookup"><span data-stu-id="3ea05-106">Output from this code appears similar to the following.</span></span> <span data-ttu-id="3ea05-107">Należy zauważyć, że podsumowanie na końcu pokazuje, że wprowadzono osiem zmian.</span><span class="sxs-lookup"><span data-stu-id="3ea05-107">Note that the summary at the end shows that eight changes were made.</span></span>  

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
  
## <a name="see-also"></a><span data-ttu-id="3ea05-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ea05-108">See also</span></span>

- [<span data-ttu-id="3ea05-109">Obsługa debugowania</span><span class="sxs-lookup"><span data-stu-id="3ea05-109">Debugging Support</span></span>](debugging-support.md)
