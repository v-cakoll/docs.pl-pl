---
title: Autoryzacja w programie WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 09bbbaad055447103a1153f1888dcae4a511cbeb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="authorization-in-wcf"></a><span data-ttu-id="15b65-102">Autoryzacja w programie WCF</span><span class="sxs-lookup"><span data-stu-id="15b65-102">Authorization in WCF</span></span>
<span data-ttu-id="15b65-103">Autoryzacja jest proces kontroli dostępu i uprawnienia do zasobów, takich jak usługi lub plików.</span><span class="sxs-lookup"><span data-stu-id="15b65-103">Authorization is the process of controlling access and rights to resources, such as services or files.</span></span> <span data-ttu-id="15b65-104">Tematy w tej sekcji opisano sposób wykonania tego zadania podstawowe w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="15b65-104">The topics in this section show you how to perform this basic task in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] in a variety of ways.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="15b65-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="15b65-105">In This Section</span></span>  
 [<span data-ttu-id="15b65-106">Mechanizmy kontroli dostępu</span><span class="sxs-lookup"><span data-stu-id="15b65-106">Access Control Mechanisms</span></span>](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
 <span data-ttu-id="15b65-107">Zawiera krótki konspektu mechanizmów autoryzacji w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]i Sugerowane zastosowania.</span><span class="sxs-lookup"><span data-stu-id="15b65-107">Provides a brief outline of the authorization mechanisms in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], and suggested uses.</span></span>  
  
 [<span data-ttu-id="15b65-108">Porady: ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="15b65-108">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 <span data-ttu-id="15b65-109">Przedstawia proces ograniczania dostępu do usługi za pomocą <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="15b65-109">Shows the process of restricting access to a service with the <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span></span>  
  
 [<span data-ttu-id="15b65-110">Porady: Używanie dostawcy ról ASP.NET z usługą</span><span class="sxs-lookup"><span data-stu-id="15b65-110">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 <span data-ttu-id="15b65-111">Przeprowadzi Cię przez konfigurację usługi do korzystania z funkcji dostawcy roli programu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="15b65-111">Walks through the configuration of a service to enable it to use the role provider feature of [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].</span></span>  
  
 [<span data-ttu-id="15b65-112">Porady: Używanie dostawcy ról ASP.NET Menedżera autoryzacji z usługą</span><span class="sxs-lookup"><span data-stu-id="15b65-112">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="15b65-113">można użyć Menedżera autoryzacji do zarządzania autoryzacji dla witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="15b65-113"> can use the Authorization Manager to manage authorization for a Web site.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="15b65-114">Podobnie można wykorzystać [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]kombinacja /Authorization Menedżera autoryzacji klientów.</span><span class="sxs-lookup"><span data-stu-id="15b65-114"> can similarly leverage the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]/Authorization Manager combination for authorization of clients.</span></span>  
  
 [<span data-ttu-id="15b65-115">Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości</span><span class="sxs-lookup"><span data-stu-id="15b65-115">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 <span data-ttu-id="15b65-116">Przedstawiono podstawowe do autoryzacji opartej na oświadczeniach za pomocą modelu tożsamości infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="15b65-116">Explains the basics of using the Identity Model infrastructure for claims-based authorization.</span></span>  
  
 [<span data-ttu-id="15b65-117">Delegowanie i personifikacja</span><span class="sxs-lookup"><span data-stu-id="15b65-117">Delegation and Impersonation</span></span>](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 <span data-ttu-id="15b65-118">Objaśniono różnicę między delegowanie i personifikacja.</span><span class="sxs-lookup"><span data-stu-id="15b65-118">Explains the difference between delegation and impersonation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="15b65-119">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="15b65-119">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a><span data-ttu-id="15b65-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="15b65-120">Related Sections</span></span>  
 [<span data-ttu-id="15b65-121">Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="15b65-121">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="15b65-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15b65-122">See Also</span></span>  
 [<span data-ttu-id="15b65-123">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="15b65-123">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="15b65-124">Model zabezpieczeń systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="15b65-124">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
