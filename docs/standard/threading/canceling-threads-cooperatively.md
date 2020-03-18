---
title: Wspólne anulowanie wątków
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threads, cancellation
ms.assetid: d2d6d5fd-e263-4fa0-847b-2fc3e0d82337
ms.openlocfilehash: 1d1433ecf39974bf9e68fe07b9d0818ac16fb544
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138128"
---
# <a name="canceling-threads-cooperatively"></a><span data-ttu-id="316b0-102">Wspólne anulowanie wątków</span><span class="sxs-lookup"><span data-stu-id="316b0-102">Canceling threads cooperatively</span></span>

<span data-ttu-id="316b0-103">Przed .NET Framework 4 .NET Framework pod warunkiem, że nie wbudowany sposób anulowania wątku wspólnie po jego uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="316b0-103">Prior to the .NET Framework 4, the .NET Framework provided no built-in way to cancel a thread cooperatively after it was started.</span></span> <span data-ttu-id="316b0-104">Jednak począwszy od .NET Framework 4, <xref:System.Threading.CancellationToken?displayProperty=nameWithType> można użyć do anulowania wątków, <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> tak jak można ich używać do anulowania obiektów lub kwerend PLINQ.</span><span class="sxs-lookup"><span data-stu-id="316b0-104">However, starting with the .NET Framework 4, you can use a <xref:System.Threading.CancellationToken?displayProperty=nameWithType> to cancel threads, just as you can use them to cancel <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or PLINQ queries.</span></span> <span data-ttu-id="316b0-105">Mimo <xref:System.Threading.Thread?displayProperty=nameWithType> że klasa nie oferuje wbudowaną obsługę tokenów anulowania, można przekazać <xref:System.Threading.Thread> token do procedury <xref:System.Threading.ParameterizedThreadStart> wątku przy użyciu konstruktora, który przyjmuje delegata.</span><span class="sxs-lookup"><span data-stu-id="316b0-105">Although the <xref:System.Threading.Thread?displayProperty=nameWithType> class does not offer built-in support for cancellation tokens, you can pass a token to a thread procedure by using the <xref:System.Threading.Thread> constructor that takes a <xref:System.Threading.ParameterizedThreadStart> delegate.</span></span> <span data-ttu-id="316b0-106">Poniższy przykład demonstruje, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="316b0-106">The following example demonstrates how to do this.</span></span>  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="316b0-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="316b0-107">See also</span></span>

- [<span data-ttu-id="316b0-108">Korzystanie z wątków i wątków</span><span class="sxs-lookup"><span data-stu-id="316b0-108">Using Threads and Threading</span></span>](using-threads-and-threading.md)
