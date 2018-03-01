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
# <a name="how-to-wrap-eap-patterns-in-a-task"></a>Porady: zawijanie wzorów EAP w zadanie
Poniższy przykład przedstawia sposób ujawniać przy użyciu dowolnego sekwencja operacji asynchroniczny wzorzec oparty na zdarzeniach (EAP) jako jedno zadanie <xref:System.Threading.Tasks.TaskCompletionSource%601>. W przykładzie przedstawiono również sposób użycia <xref:System.Threading.CancellationToken> do wywoływania metod wbudowanych anulowania na <xref:System.Net.WebClient> obiektów.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie asynchroniczne w modelu TPL i tradycyjnym środowisku .NET Framework](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)
