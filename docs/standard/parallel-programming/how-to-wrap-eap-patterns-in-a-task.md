---
title: 'Instrukcje: Opakowywanie wzorców EAP w zadaniu'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to wrap EAP patterns
ms.assetid: f11ed467-af2f-4504-8a2e-299a6c36d44e
ms.openlocfilehash: eab94ac91be0c755a1da74e2f2220e3b76cc4249
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290788"
---
# <a name="how-to-wrap-eap-patterns-in-a-task"></a>Instrukcje: Opakowywanie wzorców EAP w zadaniu
Poniższy przykład pokazuje, jak uwidocznić dowolną sekwencję operacji asynchronicznych opartych na zdarzeniach (EAP) jako jedno zadanie przy użyciu <xref:System.Threading.Tasks.TaskCompletionSource%601> . W przykładzie pokazano również, jak użyć elementu <xref:System.Threading.CancellationToken> do wywołania wbudowanych metod anulowania dla <xref:System.Net.WebClient> obiektów.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie asynchroniczne w TPL i standardowym .NET Framework](tpl-and-traditional-async-programming.md)
