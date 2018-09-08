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
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44205857"
---
# <a name="replacing-a-principal-object"></a><span data-ttu-id="43bad-102">Zastępowanie obiektu głównego</span><span class="sxs-lookup"><span data-stu-id="43bad-102">Replacing a Principal Object</span></span>
<span data-ttu-id="43bad-103">Aplikacje, które zapewniają usługi uwierzytelniania musi być w stanie zastąpić **jednostki** obiektu (<xref:System.Security.Principal.IPrincipal>) dla danego wątku.</span><span class="sxs-lookup"><span data-stu-id="43bad-103">Applications that provide authentication services must be able to replace the **Principal** object (<xref:System.Security.Principal.IPrincipal>) for a given thread.</span></span> <span data-ttu-id="43bad-104">Ponadto system zabezpieczeń należy zabezpieczyć możliwość zastąpienia **jednostki** obiektów, ponieważ złośliwie dołączone, niepoprawny **jednostki** obniża bezpieczeństwo aplikacji, Zgłaszanie nieprawdą tożsamości lub roli.</span><span class="sxs-lookup"><span data-stu-id="43bad-104">Furthermore, the security system must help protect the ability to replace **Principal** objects because a maliciously attached, incorrect **Principal** compromises the security of your application by claiming an untrue identity or role.</span></span> <span data-ttu-id="43bad-105">W związku z tym, aplikacje, muszą mieć możliwość zastąpienia **jednostki** obiekty muszą być przyznane <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> obiekt dla formantu podmiotu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="43bad-105">Therefore, applications that require the ability to replace **Principal** objects must be granted the <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> object for principal control.</span></span> <span data-ttu-id="43bad-106">(Należy pamiętać, że to uprawnienie nie jest wymagane do wykonywania kontrole zabezpieczeń opartych na rolach lub tworzenia **jednostki** obiektów.)</span><span class="sxs-lookup"><span data-stu-id="43bad-106">(Note that this permission is not required for performing role-based security checks or for creating **Principal** objects.)</span></span>  
  
 <span data-ttu-id="43bad-107">Bieżący **jednostki** obiektu może zostać zastąpione przez wykonanie następujących zadań:</span><span class="sxs-lookup"><span data-stu-id="43bad-107">The current **Principal** object can be replaced by performing the following tasks:</span></span>  
  
1.  <span data-ttu-id="43bad-108">Utwórz zamiennik **jednostki** obiektu i skojarzone **tożsamości** obiektu.</span><span class="sxs-lookup"><span data-stu-id="43bad-108">Create the replacement **Principal** object and associated **Identity** object.</span></span>  
  
2.  <span data-ttu-id="43bad-109">Dołącz nowy **jednostki** obiektu do kontekstu wywołania.</span><span class="sxs-lookup"><span data-stu-id="43bad-109">Attach the new **Principal** object to the call context.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43bad-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="43bad-110">Example</span></span>  
 <span data-ttu-id="43bad-111">Poniższy przykład pokazuje, jak utworzyć ogólny obiekt podmiotu zabezpieczeń i użyć go, aby ustawić podmiot wątku.</span><span class="sxs-lookup"><span data-stu-id="43bad-111">The following example shows how to create a generic principal object and use it to set the principal of a thread.</span></span>  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="43bad-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43bad-112">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>  
- [<span data-ttu-id="43bad-113">Obiekty główne i obiekty tożsamości</span><span class="sxs-lookup"><span data-stu-id="43bad-113">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
