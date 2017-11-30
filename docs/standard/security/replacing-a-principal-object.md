---
title: "Zastępowanie obiektu głównego"
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
- principal objects, replacing
- security [.NET Framework], replacing principal objects
- security [.NET Framework], principals
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 066176d39f04165d7882a3c295387847a46c8e6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="replacing-a-principal-object"></a>Zastępowanie obiektu głównego
Aplikacje, które udostępniają usługi uwierzytelniania musi mieć możliwość zastąpienia **główna** obiektu (<xref:System.Security.Principal.IPrincipal>) dla danego wątku. Ponadto system zabezpieczeń należy zabezpieczyć możliwość zastąpienia **główna** obiektów, ponieważ złośliwy dołączone, niepoprawny **główna** obniża bezpieczeństwo aplikacji, przejmowania nieprawdą tożsamości lub roli. W związku z tym aplikacje wymagające możliwość zastąpienia **główna** obiekty muszą być przyznane <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> obiekt dla formantu podmiotu zabezpieczeń. (Należy pamiętać, że to uprawnienie nie jest wymagane do wykonywania kontroli zabezpieczeń opartych na rolach lub tworzenia **główna** obiektów.)  
  
 Bieżący **główna** obiektu mogą zostać zastąpione przez wykonanie następujących zadań:  
  
1.  Utwórz zastąpienie **główna** obiektu i skojarzone **tożsamości** obiektu.  
  
2.  Dołącz nowy **główna** obiektu do kontekstu wywołania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób tworzenia ogólnego obiekt główny i użyj go, aby ustawić podmiot zabezpieczeń wątku.  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>  
 [Główne i obiekty tożsamości](../../../docs/standard/security/principal-and-identity-objects.md)
