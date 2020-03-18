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
# <a name="canceling-threads-cooperatively"></a>Wspólne anulowanie wątków

Przed .NET Framework 4 .NET Framework pod warunkiem, że nie wbudowany sposób anulowania wątku wspólnie po jego uruchomieniu. Jednak począwszy od .NET Framework 4, <xref:System.Threading.CancellationToken?displayProperty=nameWithType> można użyć do anulowania wątków, <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> tak jak można ich używać do anulowania obiektów lub kwerend PLINQ. Mimo <xref:System.Threading.Thread?displayProperty=nameWithType> że klasa nie oferuje wbudowaną obsługę tokenów anulowania, można przekazać <xref:System.Threading.Thread> token do procedury <xref:System.Threading.ParameterizedThreadStart> wątku przy użyciu konstruktora, który przyjmuje delegata. Poniższy przykład demonstruje, jak to zrobić.  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a>Zobacz też

- [Korzystanie z wątków i wątków](using-threads-and-threading.md)
