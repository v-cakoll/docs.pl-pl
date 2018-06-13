---
title: Uwierzytelnianie w programie WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: a4f9b719024db1334b599f0f02fe01bc083bf3c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489114"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="a376f-102">Uwierzytelnianie w programie WCF</span><span class="sxs-lookup"><span data-stu-id="a376f-102">Authentication in WCF</span></span>
<span data-ttu-id="a376f-103">W następujących tematach opisano szereg różnych mechanizmów w Windows Communication Foundation (WCF), który zapewnia uwierzytelnianie, na przykład, uwierzytelnianie systemu Windows, certyfikaty X.509 i nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="a376f-103">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a376f-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a376f-104">In This Section</span></span>  
 [<span data-ttu-id="a376f-105">Instrukcje: użycie dostawcy członkostwa platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a376f-105">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="a376f-106">Funkcje platformy ASP.NET to członkostwa i dostawcy ról, bazę danych do przechowywania par nazwa/hasło użytkownika do uwierzytelniania i autoryzacji ról użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a376f-106">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="a376f-107">W tym temacie wyjaśniono, jak użyć tej samej bazy danych do uwierzytelniania i autoryzacji użytkowników usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="a376f-107">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="a376f-108">Instrukcje: używanie niestandardowej nazwy użytkownika i modułu weryfikacji hasła</span><span class="sxs-lookup"><span data-stu-id="a376f-108">How to: Use a Custom User Name and Password Validator</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="a376f-109">Pokazuje, jak zintegrować moduł weryfikacji nazwy i hasła użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a376f-109">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="a376f-110">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="a376f-110">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 <span data-ttu-id="a376f-111">Jako dodatkowe zabezpieczenia, klient może uwierzytelnić usługę, określając oczekiwanej *tożsamości* usługi.</span><span class="sxs-lookup"><span data-stu-id="a376f-111">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="a376f-112">Oczekiwana tożsamość i tożsamości zwrócona przez usługę nie są zgodne, uwierzytelnianie nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="a376f-112">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="a376f-113">Negocjacje i limity czasu dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="a376f-113">Security Negotiation and Timeouts</span></span>](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 <span data-ttu-id="a376f-114">Informacje dotyczące używania <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> właściwości w <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> klasy.</span><span class="sxs-lookup"><span data-stu-id="a376f-114">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="a376f-115">Debugowanie błędów uwierzytelniania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a376f-115">Debugging Windows Authentication Errors</span></span>](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 <span data-ttu-id="a376f-116">Skupiono się na typowe problemy występujące podczas korzystania z uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a376f-116">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a376f-117">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="a376f-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="a376f-118">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="a376f-118">Related Sections</span></span>  
 [<span data-ttu-id="a376f-119">Typowe scenariusze zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="a376f-119">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="a376f-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a376f-120">See Also</span></span>  
 [<span data-ttu-id="a376f-121">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="a376f-121">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="a376f-122">Model zabezpieczeń systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="a376f-122">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
