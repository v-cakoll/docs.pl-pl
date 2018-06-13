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
# <a name="replacing-a-principal-object"></a><span data-ttu-id="465af-102">Zastępowanie obiektu głównego</span><span class="sxs-lookup"><span data-stu-id="465af-102">Replacing a Principal Object</span></span>
<span data-ttu-id="465af-103">Aplikacje, które udostępniają usługi uwierzytelniania musi mieć możliwość zastąpienia **główna** obiektu (<xref:System.Security.Principal.IPrincipal>) dla danego wątku.</span><span class="sxs-lookup"><span data-stu-id="465af-103">Applications that provide authentication services must be able to replace the **Principal** object (<xref:System.Security.Principal.IPrincipal>) for a given thread.</span></span> <span data-ttu-id="465af-104">Ponadto system zabezpieczeń należy zabezpieczyć możliwość zastąpienia **główna** obiektów, ponieważ złośliwy dołączone, niepoprawny **główna** obniża bezpieczeństwo aplikacji, przejmowania nieprawdą tożsamości lub roli.</span><span class="sxs-lookup"><span data-stu-id="465af-104">Furthermore, the security system must help protect the ability to replace **Principal** objects because a maliciously attached, incorrect **Principal** compromises the security of your application by claiming an untrue identity or role.</span></span> <span data-ttu-id="465af-105">W związku z tym aplikacje wymagające możliwość zastąpienia **główna** obiekty muszą być przyznane <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> obiekt dla formantu podmiotu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="465af-105">Therefore, applications that require the ability to replace **Principal** objects must be granted the <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> object for principal control.</span></span> <span data-ttu-id="465af-106">(Należy pamiętać, że to uprawnienie nie jest wymagane do wykonywania kontroli zabezpieczeń opartych na rolach lub tworzenia **główna** obiektów.)</span><span class="sxs-lookup"><span data-stu-id="465af-106">(Note that this permission is not required for performing role-based security checks or for creating **Principal** objects.)</span></span>  
  
 <span data-ttu-id="465af-107">Bieżący **główna** obiektu mogą zostać zastąpione przez wykonanie następujących zadań:</span><span class="sxs-lookup"><span data-stu-id="465af-107">The current **Principal** object can be replaced by performing the following tasks:</span></span>  
  
1.  <span data-ttu-id="465af-108">Utwórz zastąpienie **główna** obiektu i skojarzone **tożsamości** obiektu.</span><span class="sxs-lookup"><span data-stu-id="465af-108">Create the replacement **Principal** object and associated **Identity** object.</span></span>  
  
2.  <span data-ttu-id="465af-109">Dołącz nowy **główna** obiektu do kontekstu wywołania.</span><span class="sxs-lookup"><span data-stu-id="465af-109">Attach the new **Principal** object to the call context.</span></span>  
  
## <a name="example"></a><span data-ttu-id="465af-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="465af-110">Example</span></span>  
 <span data-ttu-id="465af-111">Poniższy przykład przedstawia sposób tworzenia ogólnego obiekt główny i użyj go, aby ustawić podmiot zabezpieczeń wątku.</span><span class="sxs-lookup"><span data-stu-id="465af-111">The following example shows how to create a generic principal object and use it to set the principal of a thread.</span></span>  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="465af-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="465af-112">See Also</span></span>  
 <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>  
 [<span data-ttu-id="465af-113">Obiekty główne i obiekty tożsamości</span><span class="sxs-lookup"><span data-stu-id="465af-113">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
