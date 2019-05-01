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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794930"
---
# <a name="canceling-threads-cooperatively"></a>Wspólne anulowanie wątków

Przed .NET Framework 4 .NET Framework, pod warunkiem ma wbudowane możliwości wspólne anulowanie wątków, po jego uruchomienia. Jednak począwszy od programu .NET Framework 4, możesz użyć <xref:System.Threading.CancellationToken?displayProperty=nameWithType> anulować wątków, tak samo, jak można je anulować <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> obiektów lub zapytania PLINQ. Mimo że <xref:System.Threading.Thread?displayProperty=nameWithType> klasy nie oferuje wbudowaną obsługę tokenów anulowania, można przekazać tokenu do procedury wątku za pomocą <xref:System.Threading.Thread> konstruktora przyjmującego <xref:System.Threading.ParameterizedThreadStart> delegować. Poniższy przykład demonstruje, jak to zrobić.  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a>Zobacz także

- [Używanie wątków i wątkowości](using-threads-and-threading.md)
