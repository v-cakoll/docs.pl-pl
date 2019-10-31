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
# <a name="canceling-threads-cooperatively"></a>Wspólne anulowanie wątków

Przed rozpoczęciem .NET Framework 4 .NET Framework nie miał wbudowanego sposobu anulowania wątku po jego uruchomieniu. Jednak rozpoczynając od .NET Framework 4, można użyć <xref:System.Threading.CancellationToken?displayProperty=nameWithType>, aby anulować wątki, tak jak można je użyć do anulowania obiektów <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> lub zapytań PLINQ. Chociaż Klasa <xref:System.Threading.Thread?displayProperty=nameWithType> nie oferuje wbudowanej obsługi tokenów anulowania, można przekazać token do procedury wątku za pomocą konstruktora <xref:System.Threading.Thread>, który pobiera <xref:System.Threading.ParameterizedThreadStart> delegat. Poniższy przykład demonstruje, jak to zrobić.  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a>Zobacz także

- [Używanie wątków i wątkowości](using-threads-and-threading.md)
