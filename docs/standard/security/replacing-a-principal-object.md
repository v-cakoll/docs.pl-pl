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
ms.openlocfilehash: d5193756861f407315ec82e4419f1d04495c7dd2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606036"
---
# <a name="replacing-a-principal-object"></a><span data-ttu-id="f4e3e-102">Zastępowanie obiektu głównego</span><span class="sxs-lookup"><span data-stu-id="f4e3e-102">Replacing a Principal Object</span></span>
<span data-ttu-id="f4e3e-103">Aplikacje, które zapewniają usługi uwierzytelniania musi być w stanie zastąpić **jednostki** obiektu (<xref:System.Security.Principal.IPrincipal>) dla danego wątku.</span><span class="sxs-lookup"><span data-stu-id="f4e3e-103">Applications that provide authentication services must be able to replace the **Principal** object (<xref:System.Security.Principal.IPrincipal>) for a given thread.</span></span> <span data-ttu-id="f4e3e-104">Ponadto system zabezpieczeń należy zabezpieczyć możliwość zastąpienia **jednostki** obiektów, ponieważ złośliwie dołączone, niepoprawny **jednostki** obniża bezpieczeństwo aplikacji, Zgłaszanie nieprawdą tożsamości lub roli.</span><span class="sxs-lookup"><span data-stu-id="f4e3e-104">Furthermore, the security system must help protect the ability to replace **Principal** objects because a maliciously attached, incorrect **Principal** compromises the security of your application by claiming an untrue identity or role.</span></span> <span data-ttu-id="f4e3e-105">W związku z tym, aplikacje, muszą mieć możliwość zastąpienia **jednostki** obiekty muszą być przyznane <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> obiekt dla formantu podmiotu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f4e3e-105">Therefore, applications that require the ability to replace **Principal** objects must be granted the <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> object for principal control.</span></span> <span data-ttu-id="f4e3e-106">(Należy pamiętać, że to uprawnienie nie jest wymagane do wykonywania kontrole zabezpieczeń opartych na rolach lub tworzenia **jednostki** obiektów.)</span><span class="sxs-lookup"><span data-stu-id="f4e3e-106">(Note that this permission is not required for performing role-based security checks or for creating **Principal** objects.)</span></span>  
  
 <span data-ttu-id="f4e3e-107">Bieżący **jednostki** obiektu może zostać zastąpione przez wykonanie następujących zadań:</span><span class="sxs-lookup"><span data-stu-id="f4e3e-107">The current **Principal** object can be replaced by performing the following tasks:</span></span>  
  
1.  <span data-ttu-id="f4e3e-108">Utwórz zamiennik **jednostki** obiektu i skojarzone **tożsamości** obiektu.</span><span class="sxs-lookup"><span data-stu-id="f4e3e-108">Create the replacement **Principal** object and associated **Identity** object.</span></span>  
  
2.  <span data-ttu-id="f4e3e-109">Dołącz nowy **jednostki** obiektu do kontekstu wywołania.</span><span class="sxs-lookup"><span data-stu-id="f4e3e-109">Attach the new **Principal** object to the call context.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4e3e-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="f4e3e-110">Example</span></span>  
 <span data-ttu-id="f4e3e-111">Poniższy przykład pokazuje, jak utworzyć ogólny obiekt podmiotu zabezpieczeń i użyć go, aby ustawić podmiot wątku.</span><span class="sxs-lookup"><span data-stu-id="f4e3e-111">The following example shows how to create a generic principal object and use it to set the principal of a thread.</span></span>  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f4e3e-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4e3e-112">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>
- [<span data-ttu-id="f4e3e-113">Obiekty główne i obiekty tożsamości</span><span class="sxs-lookup"><span data-stu-id="f4e3e-113">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
