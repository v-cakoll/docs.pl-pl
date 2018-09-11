---
title: 'Porady: zawijanie wzorów EAP w zadanie'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to wrap EAP patterns
ms.assetid: f11ed467-af2f-4504-8a2e-299a6c36d44e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4287879bd95f7bc1e1dc99f74fa0d7cc0fe737f
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44336462"
---
# <a name="how-to-wrap-eap-patterns-in-a-task"></a>Porady: zawijanie wzorów EAP w zadanie
Poniższy przykład pokazuje, jak udostępnić dowolne sekwencja operacji przy asynchroniczny wzorzec oparty na zdarzeniach (EAP), jako jedno zadanie przy użyciu <xref:System.Threading.Tasks.TaskCompletionSource%601>. W przykładzie pokazano również sposób użycia <xref:System.Threading.CancellationToken> do wywołania metod wbudowanych anulowania na <xref:System.Net.WebClient> obiektów.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie asynchroniczne w modelu TPL i tradycyjnym środowisku .NET Framework](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)
