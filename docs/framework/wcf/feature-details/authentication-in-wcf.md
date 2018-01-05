---
title: Uwierzytelnianie w programie WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 432ed9debeffad82125b567508ed46b46d4b8821
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="36773-102">Uwierzytelnianie w programie WCF</span><span class="sxs-lookup"><span data-stu-id="36773-102">Authentication in WCF</span></span>
<span data-ttu-id="36773-103">W następujących tematach opisano szereg różnych mechanizmów w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zawierających uwierzytelniania, na przykład, uwierzytelnianie systemu Windows, certyfikaty X.509 i nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="36773-103">The following topics show a number of different mechanisms in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="36773-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="36773-104">In This Section</span></span>  
 [<span data-ttu-id="36773-105">Instrukcje: użycie dostawcy członkostwa platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="36773-105">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="36773-106">Funkcje platformy ASP.NET to członkostwa i dostawcy ról, bazę danych do przechowywania par nazwa/hasło użytkownika do uwierzytelniania i autoryzacji ról użytkownika.</span><span class="sxs-lookup"><span data-stu-id="36773-106">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="36773-107">W tym temacie opisano sposób [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi można użyć tej samej bazy danych do uwierzytelniania i autoryzacji użytkowników.</span><span class="sxs-lookup"><span data-stu-id="36773-107">This topic explains how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="36773-108">Instrukcje: używanie niestandardowej nazwy użytkownika i modułu weryfikacji hasła</span><span class="sxs-lookup"><span data-stu-id="36773-108">How to: Use a Custom User Name and Password Validator</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="36773-109">Pokazuje, jak zintegrować moduł weryfikacji nazwy i hasła użytkownika.</span><span class="sxs-lookup"><span data-stu-id="36773-109">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="36773-110">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="36773-110">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 <span data-ttu-id="36773-111">Jako dodatkowe zabezpieczenia, klient może uwierzytelnić usługę, określając oczekiwanej *tożsamości* usługi.</span><span class="sxs-lookup"><span data-stu-id="36773-111">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="36773-112">Oczekiwana tożsamość i tożsamości zwrócona przez usługę nie są zgodne, uwierzytelnianie nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="36773-112">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="36773-113">Negocjacje i limity czasu dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="36773-113">Security Negotiation and Timeouts</span></span>](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 <span data-ttu-id="36773-114">Informacje dotyczące używania <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> właściwości w <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> klasy.</span><span class="sxs-lookup"><span data-stu-id="36773-114">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="36773-115">Debugowanie błędów uwierzytelniania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="36773-115">Debugging Windows Authentication Errors</span></span>](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 <span data-ttu-id="36773-116">Skupiono się na typowe problemy występujące podczas korzystania z uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="36773-116">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="36773-117">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="36773-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="36773-118">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="36773-118">Related Sections</span></span>  
 [<span data-ttu-id="36773-119">Typowe scenariusze zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="36773-119">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="36773-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36773-120">See Also</span></span>  
 [<span data-ttu-id="36773-121">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="36773-121">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="36773-122">Model zabezpieczeń systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="36773-122">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
