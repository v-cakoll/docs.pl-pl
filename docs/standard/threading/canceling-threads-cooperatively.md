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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138128"
---
# <a name="canceling-threads-cooperatively"></a><span data-ttu-id="2acbc-102">Wspólne anulowanie wątków</span><span class="sxs-lookup"><span data-stu-id="2acbc-102">Canceling threads cooperatively</span></span>

<span data-ttu-id="2acbc-103">Przed rozpoczęciem .NET Framework 4 .NET Framework nie miał wbudowanego sposobu anulowania wątku po jego uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="2acbc-103">Prior to the .NET Framework 4, the .NET Framework provided no built-in way to cancel a thread cooperatively after it was started.</span></span> <span data-ttu-id="2acbc-104">Jednak rozpoczynając od .NET Framework 4, można użyć <xref:System.Threading.CancellationToken?displayProperty=nameWithType>, aby anulować wątki, tak jak można je użyć do anulowania obiektów <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> lub zapytań PLINQ.</span><span class="sxs-lookup"><span data-stu-id="2acbc-104">However, starting with the .NET Framework 4, you can use a <xref:System.Threading.CancellationToken?displayProperty=nameWithType> to cancel threads, just as you can use them to cancel <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or PLINQ queries.</span></span> <span data-ttu-id="2acbc-105">Chociaż Klasa <xref:System.Threading.Thread?displayProperty=nameWithType> nie oferuje wbudowanej obsługi tokenów anulowania, można przekazać token do procedury wątku za pomocą konstruktora <xref:System.Threading.Thread>, który pobiera <xref:System.Threading.ParameterizedThreadStart> delegat.</span><span class="sxs-lookup"><span data-stu-id="2acbc-105">Although the <xref:System.Threading.Thread?displayProperty=nameWithType> class does not offer built-in support for cancellation tokens, you can pass a token to a thread procedure by using the <xref:System.Threading.Thread> constructor that takes a <xref:System.Threading.ParameterizedThreadStart> delegate.</span></span> <span data-ttu-id="2acbc-106">Poniższy przykład demonstruje, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="2acbc-106">The following example demonstrates how to do this.</span></span>  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="2acbc-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2acbc-107">See also</span></span>

- [<span data-ttu-id="2acbc-108">Używanie wątków i wątkowości</span><span class="sxs-lookup"><span data-stu-id="2acbc-108">Using Threads and Threading</span></span>](using-threads-and-threading.md)
