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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd32deb9c8719a12b76aaea8ec91a17471cf18f9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43885866"
---
# <a name="canceling-threads-cooperatively"></a><span data-ttu-id="c36f9-102">Wspólne anulowanie wątków</span><span class="sxs-lookup"><span data-stu-id="c36f9-102">Canceling threads cooperatively</span></span>

<span data-ttu-id="c36f9-103">Przed .NET Framework 4 .NET Framework, pod warunkiem ma wbudowane możliwości wspólne anulowanie wątków, po jego uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="c36f9-103">Prior to the .NET Framework 4, the .NET Framework provided no built-in way to cancel a thread cooperatively after it was started.</span></span> <span data-ttu-id="c36f9-104">Jednak począwszy od programu .NET Framework 4, możesz użyć <xref:System.Threading.CancellationToken?displayProperty=nameWithType> anulować wątków, tak samo, jak można je anulować <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> obiektów lub zapytania PLINQ.</span><span class="sxs-lookup"><span data-stu-id="c36f9-104">However, starting with the .NET Framework 4, you can use a <xref:System.Threading.CancellationToken?displayProperty=nameWithType> to cancel threads, just as you can use them to cancel <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or PLINQ queries.</span></span> <span data-ttu-id="c36f9-105">Mimo że <xref:System.Threading.Thread?displayProperty=nameWithType> klasy nie oferuje wbudowaną obsługę tokenów anulowania, można przekazać tokenu do procedury wątku za pomocą <xref:System.Threading.Thread> konstruktora przyjmującego <xref:System.Threading.ParameterizedThreadStart> delegować.</span><span class="sxs-lookup"><span data-stu-id="c36f9-105">Although the <xref:System.Threading.Thread?displayProperty=nameWithType> class does not offer built-in support for cancellation tokens, you can pass a token to a thread procedure by using the <xref:System.Threading.Thread> constructor that takes a <xref:System.Threading.ParameterizedThreadStart> delegate.</span></span> <span data-ttu-id="c36f9-106">Poniższy przykład demonstruje, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="c36f9-106">The following example demonstrates how to do this.</span></span>  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="c36f9-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c36f9-107">See also</span></span>

- [<span data-ttu-id="c36f9-108">Używanie wątków i wątkowości</span><span class="sxs-lookup"><span data-stu-id="c36f9-108">Using Threads and Threading</span></span>](using-threads-and-threading.md)
