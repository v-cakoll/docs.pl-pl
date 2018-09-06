---
title: Autoryzacja w programie WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
ms.openlocfilehash: 8e7632dda1a1bd2b60b71c385ad58c23e4207534
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43749583"
---
# <a name="authorization-in-wcf"></a><span data-ttu-id="adb95-102">Autoryzacja w programie WCF</span><span class="sxs-lookup"><span data-stu-id="adb95-102">Authorization in WCF</span></span>
<span data-ttu-id="adb95-103">Autoryzacja to proces nadzoru nad dostępu i uprawnień do zasobów, takich jak usługi lub plików.</span><span class="sxs-lookup"><span data-stu-id="adb95-103">Authorization is the process of controlling access and rights to resources, such as services or files.</span></span> <span data-ttu-id="adb95-104">Tematy w tej sekcji pokazano, jak wykonać to zadanie podstawowe w Windows Communication Foundation (WCF) na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="adb95-104">The topics in this section show you how to perform this basic task in Windows Communication Foundation (WCF) in a variety of ways.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="adb95-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="adb95-105">In This Section</span></span>  
 [<span data-ttu-id="adb95-106">Mechanizmy kontroli dostępu</span><span class="sxs-lookup"><span data-stu-id="adb95-106">Access Control Mechanisms</span></span>](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
 <span data-ttu-id="adb95-107">Zawiera krótki zarys mechanizmów autoryzacji usługi WCF i sugerowane używa.</span><span class="sxs-lookup"><span data-stu-id="adb95-107">Provides a brief outline of the authorization mechanisms in WCF, and suggested uses.</span></span>  
  
 [<span data-ttu-id="adb95-108">Instrukcje: ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="adb95-108">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 <span data-ttu-id="adb95-109">Przedstawia proces ograniczanie dostępu do usługi za pomocą <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="adb95-109">Shows the process of restricting access to a service with the <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span></span>  
  
 [<span data-ttu-id="adb95-110">Instrukcje: używanie dostawcy ról ASP.NET razem z usługą</span><span class="sxs-lookup"><span data-stu-id="adb95-110">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 <span data-ttu-id="adb95-111">Omawia konfigurację usługi, aby włączyć go do użycia funkcję dostawcy roli [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="adb95-111">Walks through the configuration of a service to enable it to use the role provider feature of [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].</span></span>  
  
 [<span data-ttu-id="adb95-112">Instrukcje: używanie dostawcy roli menedżera autoryzacji platformy ASP.NET za pomocą usługi</span><span class="sxs-lookup"><span data-stu-id="adb95-112">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="adb95-113"> można użyć Menedżera autoryzacji do zarządzania autoryzacji dla witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="adb95-113"> can use the Authorization Manager to manage authorization for a Web site.</span></span> <span data-ttu-id="adb95-114">Podobnie można korzystać z usługi WCF [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]kombinacja /Authorization Menedżera autoryzacji klientów.</span><span class="sxs-lookup"><span data-stu-id="adb95-114">WCF can similarly leverage the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]/Authorization Manager combination for authorization of clients.</span></span>  
  
 [<span data-ttu-id="adb95-115">Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości</span><span class="sxs-lookup"><span data-stu-id="adb95-115">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 <span data-ttu-id="adb95-116">Objaśnia podstawy przy użyciu infrastruktury modelu tożsamości do autoryzacji opartej na oświadczeniach.</span><span class="sxs-lookup"><span data-stu-id="adb95-116">Explains the basics of using the Identity Model infrastructure for claims-based authorization.</span></span>  
  
 [<span data-ttu-id="adb95-117">Delegowanie i personifikacja</span><span class="sxs-lookup"><span data-stu-id="adb95-117">Delegation and Impersonation</span></span>](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 <span data-ttu-id="adb95-118">Wyjaśnia różnicę pomiędzy delegowanie i personifikacja.</span><span class="sxs-lookup"><span data-stu-id="adb95-118">Explains the difference between delegation and impersonation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="adb95-119">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="adb95-119">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a><span data-ttu-id="adb95-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="adb95-120">Related Sections</span></span>  
 [<span data-ttu-id="adb95-121">Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="adb95-121">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="adb95-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="adb95-122">See Also</span></span>  
 [<span data-ttu-id="adb95-123">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="adb95-123">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="adb95-124">Model zabezpieczeń dla systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="adb95-124">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
