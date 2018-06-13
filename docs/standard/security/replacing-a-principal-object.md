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
ms.openlocfilehash: 94391471fecd92aeadec4da39cdd5b6f80bb6949
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581167"
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
 [Obiekty główne i obiekty tożsamości](../../../docs/standard/security/principal-and-identity-objects.md)
