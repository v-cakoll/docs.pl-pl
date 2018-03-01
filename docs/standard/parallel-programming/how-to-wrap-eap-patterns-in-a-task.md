---
title: "Porady: zawijanie wzorów EAP w zadanie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to wrap EAP patterns
ms.assetid: f11ed467-af2f-4504-8a2e-299a6c36d44e
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9e451c3ce8bb50cb17da7fef25ae0317bcb82c3e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-wrap-eap-patterns-in-a-task"></a><span data-ttu-id="ea3eb-102">Porady: zawijanie wzorów EAP w zadanie</span><span class="sxs-lookup"><span data-stu-id="ea3eb-102">How to: Wrap EAP Patterns in a Task</span></span>
<span data-ttu-id="ea3eb-103">Poniższy przykład przedstawia sposób ujawniać przy użyciu dowolnego sekwencja operacji asynchroniczny wzorzec oparty na zdarzeniach (EAP) jako jedno zadanie <xref:System.Threading.Tasks.TaskCompletionSource%601>.</span><span class="sxs-lookup"><span data-stu-id="ea3eb-103">The following example shows how to expose an arbitrary sequence of Event-Based Asynchronous Pattern (EAP) operations as one task by using a <xref:System.Threading.Tasks.TaskCompletionSource%601>.</span></span> <span data-ttu-id="ea3eb-104">W przykładzie przedstawiono również sposób użycia <xref:System.Threading.CancellationToken> do wywoływania metod wbudowanych anulowania na <xref:System.Net.WebClient> obiektów.</span><span class="sxs-lookup"><span data-stu-id="ea3eb-104">The example also shows how to use a <xref:System.Threading.CancellationToken> to invoke the built-in cancellation methods on the <xref:System.Net.WebClient> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea3eb-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="ea3eb-105">Example</span></span>  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="ea3eb-106">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ea3eb-106">See Also</span></span>  
 [<span data-ttu-id="ea3eb-107">Programowanie asynchroniczne w modelu TPL i tradycyjnym środowisku .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ea3eb-107">TPL and Traditional .NET Framework Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)
