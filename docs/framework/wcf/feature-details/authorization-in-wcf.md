---
title: Autoryzacja w programie WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
ms.openlocfilehash: d67d64dcf0003de28775ac947f8b5f72d7c2ba2a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597634"
---
# <a name="authorization-in-wcf"></a><span data-ttu-id="b3c0f-102">Autoryzacja w programie WCF</span><span class="sxs-lookup"><span data-stu-id="b3c0f-102">Authorization in WCF</span></span>
<span data-ttu-id="b3c0f-103">Autoryzacja to proces kontroli dostępu i praw do zasobów, takich jak usługi lub pliki.</span><span class="sxs-lookup"><span data-stu-id="b3c0f-103">Authorization is the process of controlling access and rights to resources, such as services or files.</span></span> <span data-ttu-id="b3c0f-104">W tematach w tej sekcji pokazano, jak wykonać to podstawowe zadanie w programie Windows Communication Foundation (WCF) na wiele sposobów.</span><span class="sxs-lookup"><span data-stu-id="b3c0f-104">The topics in this section show you how to perform this basic task in Windows Communication Foundation (WCF) in a variety of ways.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b3c0f-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b3c0f-105">In This Section</span></span>  
 [<span data-ttu-id="b3c0f-106">Mechanizmy kontroli dostępu</span><span class="sxs-lookup"><span data-stu-id="b3c0f-106">Access Control Mechanisms</span></span>](access-control-mechanisms.md)  
 <span data-ttu-id="b3c0f-107">Zawiera krótki zarys mechanizmów autoryzacji w programie WCF oraz Sugerowane zastosowania.</span><span class="sxs-lookup"><span data-stu-id="b3c0f-107">Provides a brief outline of the authorization mechanisms in WCF, and suggested uses.</span></span>  
  
 [<span data-ttu-id="b3c0f-108">Instrukcje: ograniczanie dostępu przy użyciu klasy PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="b3c0f-108">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 <span data-ttu-id="b3c0f-109">Pokazuje proces ograniczania dostępu do usługi za pomocą programu <xref:System.Security.Permissions.PrincipalPermissionAttribute> .</span><span class="sxs-lookup"><span data-stu-id="b3c0f-109">Shows the process of restricting access to a service with the <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span></span>  
  
 [<span data-ttu-id="b3c0f-110">Instrukcje: Używanie dostawcy ról ASP.NET razem z usługą</span><span class="sxs-lookup"><span data-stu-id="b3c0f-110">How to: Use the ASP.NET Role Provider with a Service</span></span>](how-to-use-the-aspnet-role-provider-with-a-service.md)  
 <span data-ttu-id="b3c0f-111">Przeprowadzi procedurę konfigurowania usługi, aby umożliwić jej korzystanie z funkcji dostawcy roli programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b3c0f-111">Walks through the configuration of a service to enable it to use the role provider feature of ASP.NET.</span></span>  
  
 [<span data-ttu-id="b3c0f-112">Instrukcje: używanie dostawcy roli menedżera autoryzacji platformy ASP.NET za pomocą usługi</span><span class="sxs-lookup"><span data-stu-id="b3c0f-112">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>](how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 <span data-ttu-id="b3c0f-113">ASP.NET może używać Menedżera autoryzacji do zarządzania autoryzacją witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b3c0f-113">ASP.NET can use the Authorization Manager to manage authorization for a Web site.</span></span> <span data-ttu-id="b3c0f-114">Usługa WCF może w podobny sposób korzystać z kombinacji ASP.NET/Authorization Manager na potrzeby autoryzacji klientów.</span><span class="sxs-lookup"><span data-stu-id="b3c0f-114">WCF can similarly leverage the ASP.NET/Authorization Manager combination for authorization of clients.</span></span>  
  
 [<span data-ttu-id="b3c0f-115">Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości</span><span class="sxs-lookup"><span data-stu-id="b3c0f-115">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)  
 <span data-ttu-id="b3c0f-116">Wyjaśnia podstawowe informacje dotyczące korzystania z infrastruktury modelu tożsamości na potrzeby autoryzacji opartej na oświadczeniach.</span><span class="sxs-lookup"><span data-stu-id="b3c0f-116">Explains the basics of using the Identity Model infrastructure for claims-based authorization.</span></span>  
  
 [<span data-ttu-id="b3c0f-117">Delegowanie i personifikacja</span><span class="sxs-lookup"><span data-stu-id="b3c0f-117">Delegation and Impersonation</span></span>](delegation-and-impersonation-with-wcf.md)  
 <span data-ttu-id="b3c0f-118">Wyjaśnia różnicę między delegowaniem a personifikacją.</span><span class="sxs-lookup"><span data-stu-id="b3c0f-118">Explains the difference between delegation and impersonation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b3c0f-119">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="b3c0f-119">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a><span data-ttu-id="b3c0f-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="b3c0f-120">Related Sections</span></span>  
 [<span data-ttu-id="b3c0f-121">Authentication</span><span class="sxs-lookup"><span data-stu-id="b3c0f-121">Authentication</span></span>](authentication-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="b3c0f-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3c0f-122">See also</span></span>

- [<span data-ttu-id="b3c0f-123">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="b3c0f-123">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="b3c0f-124">[Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b3c0f-124">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
