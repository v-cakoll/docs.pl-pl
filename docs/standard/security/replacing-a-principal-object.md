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
ms.openlocfilehash: 056bd0bbafe0e7dc84d8d0c532ff844370c59230
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291217"
---
# <a name="replacing-a-principal-object"></a>Zastępowanie obiektu głównego
Aplikacje, które zapewniają usługi uwierzytelniania, muszą być w stanie zastąpić obiekt **podmiotu zabezpieczeń** ( <xref:System.Security.Principal.IPrincipal> ) dla danego wątku. Ponadto system zabezpieczeń musi pomagać w ochronie możliwości zastąpienia obiektów **głównych** , ponieważ złośliwie podłączona, nieprawidłowa **podmiot** zabezpieczeń narusza zabezpieczenia aplikacji przez zajęcie nieprawdziwej tożsamością lub rolą. W związku z tym aplikacje, które wymagają możliwości zastąpienia obiektów **Principal** , muszą mieć przyznany <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> obiekt dla kontroli podmiotu zabezpieczeń. (Należy zauważyć, że to uprawnienie nie jest wymagane do wykonywania kontroli zabezpieczeń opartych na rolach ani do tworzenia obiektów **głównych** ).  
  
 Bieżący obiekt **Principal** można zastąpić, wykonując następujące zadania:  
  
1. Utwórz zastępujący obiekt **podmiotu zabezpieczeń** i skojarzony obiekt **tożsamości** .  
  
2. Dołącz nowy obiekt **Principal** do kontekstu wywołania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak utworzyć ogólny obiekt główny i używać go do ustawiania podmiotu zabezpieczeń wątku.  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>
- [Obiekty główne i obiekty tożsamości](principal-and-identity-objects.md)
