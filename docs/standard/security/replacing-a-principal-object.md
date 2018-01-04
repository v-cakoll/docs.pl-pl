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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c53064ae12889df09b5259fbb7c8159cfdcd07aa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="replacing-a-principal-object"></a><span data-ttu-id="60cf8-102">Zastępowanie obiektu głównego</span><span class="sxs-lookup"><span data-stu-id="60cf8-102">Replacing a Principal Object</span></span>
<span data-ttu-id="60cf8-103">Aplikacje, które udostępniają usługi uwierzytelniania musi mieć możliwość zastąpienia **główna** obiektu (<xref:System.Security.Principal.IPrincipal>) dla danego wątku.</span><span class="sxs-lookup"><span data-stu-id="60cf8-103">Applications that provide authentication services must be able to replace the **Principal** object (<xref:System.Security.Principal.IPrincipal>) for a given thread.</span></span> <span data-ttu-id="60cf8-104">Ponadto system zabezpieczeń należy zabezpieczyć możliwość zastąpienia **główna** obiektów, ponieważ złośliwy dołączone, niepoprawny **główna** obniża bezpieczeństwo aplikacji, przejmowania nieprawdą tożsamości lub roli.</span><span class="sxs-lookup"><span data-stu-id="60cf8-104">Furthermore, the security system must help protect the ability to replace **Principal** objects because a maliciously attached, incorrect **Principal** compromises the security of your application by claiming an untrue identity or role.</span></span> <span data-ttu-id="60cf8-105">W związku z tym aplikacje wymagające możliwość zastąpienia **główna** obiekty muszą być przyznane <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> obiekt dla formantu podmiotu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="60cf8-105">Therefore, applications that require the ability to replace **Principal** objects must be granted the <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> object for principal control.</span></span> <span data-ttu-id="60cf8-106">(Należy pamiętać, że to uprawnienie nie jest wymagane do wykonywania kontroli zabezpieczeń opartych na rolach lub tworzenia **główna** obiektów.)</span><span class="sxs-lookup"><span data-stu-id="60cf8-106">(Note that this permission is not required for performing role-based security checks or for creating **Principal** objects.)</span></span>  
  
 <span data-ttu-id="60cf8-107">Bieżący **główna** obiektu mogą zostać zastąpione przez wykonanie następujących zadań:</span><span class="sxs-lookup"><span data-stu-id="60cf8-107">The current **Principal** object can be replaced by performing the following tasks:</span></span>  
  
1.  <span data-ttu-id="60cf8-108">Utwórz zastąpienie **główna** obiektu i skojarzone **tożsamości** obiektu.</span><span class="sxs-lookup"><span data-stu-id="60cf8-108">Create the replacement **Principal** object and associated **Identity** object.</span></span>  
  
2.  <span data-ttu-id="60cf8-109">Dołącz nowy **główna** obiektu do kontekstu wywołania.</span><span class="sxs-lookup"><span data-stu-id="60cf8-109">Attach the new **Principal** object to the call context.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60cf8-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="60cf8-110">Example</span></span>  
 <span data-ttu-id="60cf8-111">Poniższy przykład przedstawia sposób tworzenia ogólnego obiekt główny i użyj go, aby ustawić podmiot zabezpieczeń wątku.</span><span class="sxs-lookup"><span data-stu-id="60cf8-111">The following example shows how to create a generic principal object and use it to set the principal of a thread.</span></span>  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="60cf8-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="60cf8-112">See Also</span></span>  
 <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>  
 [<span data-ttu-id="60cf8-113">Obiekty główne i obiekty tożsamości</span><span class="sxs-lookup"><span data-stu-id="60cf8-113">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
