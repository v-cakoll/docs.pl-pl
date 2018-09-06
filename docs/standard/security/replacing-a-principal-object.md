---
title: Zastępowanie obiektu głównego
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- principal objects, replacing
- security [.NET Framework], replacing principal objects
- security [.NET Framework], principals
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bfcd912fc16aa8d4b89a4f455d65b0294593cead
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43886529"
---
# <a name="replacing-a-principal-object"></a>Zastępowanie obiektu głównego
Aplikacje, które zapewniają usługi uwierzytelniania musi być w stanie zastąpić **jednostki** obiektu (<xref:System.Security.Principal.IPrincipal>) dla danego wątku. Ponadto system zabezpieczeń należy zabezpieczyć możliwość zastąpienia **jednostki** obiektów, ponieważ złośliwie dołączone, niepoprawny **jednostki** obniża bezpieczeństwo aplikacji, Zgłaszanie nieprawdą tożsamości lub roli. W związku z tym, aplikacje, muszą mieć możliwość zastąpienia **jednostki** obiekty muszą być przyznane <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> obiekt dla formantu podmiotu zabezpieczeń. (Należy pamiętać, że to uprawnienie nie jest wymagane do wykonywania kontrole zabezpieczeń opartych na rolach lub tworzenia **jednostki** obiektów.)  
  
 Bieżący **jednostki** obiektu może zostać zastąpione przez wykonanie następujących zadań:  
  
1.  Utwórz zamiennik **jednostki** obiektu i skojarzone **tożsamości** obiektu.  
  
2.  Dołącz nowy **jednostki** obiektu do kontekstu wywołania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak utworzyć ogólny obiekt podmiotu zabezpieczeń i użyć go, aby ustawić podmiot wątku.  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>  
- [Obiekty główne i obiekty tożsamości](../../../docs/standard/security/principal-and-identity-objects.md)
