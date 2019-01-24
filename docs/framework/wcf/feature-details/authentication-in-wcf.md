---
title: Uwierzytelnianie w programie WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: 22bfd7edf0ca0e9eb57e63c168c783f25782d607
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523925"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="5489b-102">Uwierzytelnianie w programie WCF</span><span class="sxs-lookup"><span data-stu-id="5489b-102">Authentication in WCF</span></span>
<span data-ttu-id="5489b-103">Poniższe tematy przedstawiają szeregu różnych mechanizmów w Windows Communication Foundation (WCF) zapewniające uwierzytelniania, na przykład Windows uwierzytelniania certyfikatów X.509 i nazwa użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="5489b-103">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5489b-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="5489b-104">In This Section</span></span>  
 [<span data-ttu-id="5489b-105">Instrukcje: Użycie dostawcy członkostwa platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5489b-105">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="5489b-106">Funkcje platformy ASP.NET obejmują członkostwa i dostawcy ról, bazę danych do przechowywania par nazwa/hasło użytkownika do uwierzytelniania i ról użytkownika o zezwolenie.</span><span class="sxs-lookup"><span data-stu-id="5489b-106">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="5489b-107">W tym temacie wyjaśniono, jak użyć tej samej bazy danych do uwierzytelniania i autoryzowania użytkowników usług WCF.</span><span class="sxs-lookup"><span data-stu-id="5489b-107">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="5489b-108">Instrukcje: Używanie niestandardowej nazwy użytkownika i modułu weryfikacji hasła</span><span class="sxs-lookup"><span data-stu-id="5489b-108">How to: Use a Custom User Name and Password Validator</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="5489b-109">Pokazuje, jak zintegrować moduł weryfikacji nazwy i hasła użytkownika niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="5489b-109">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="5489b-110">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="5489b-110">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 <span data-ttu-id="5489b-111">Jako dodatkowego bezpieczeństwa, klient może uwierzytelnić usługi, określając oczekiwanej *tożsamości* usługi.</span><span class="sxs-lookup"><span data-stu-id="5489b-111">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="5489b-112">Oczekiwaną tożsamość i tożsamości, zwracane przez usługę nie są zgodne, uwierzytelnianie nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="5489b-112">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="5489b-113">Negocjacje i limity czasu dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="5489b-113">Security Negotiation and Timeouts</span></span>](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 <span data-ttu-id="5489b-114">Opisuje sposób używania <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> właściwość <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> klasy.</span><span class="sxs-lookup"><span data-stu-id="5489b-114">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="5489b-115">Debugowanie błędów uwierzytelniania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5489b-115">Debugging Windows Authentication Errors</span></span>](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 <span data-ttu-id="5489b-116">Koncentruje się na typowe problemy występujące podczas korzystania z uwierzytelniania Windows.</span><span class="sxs-lookup"><span data-stu-id="5489b-116">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5489b-117">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="5489b-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="5489b-118">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="5489b-118">Related Sections</span></span>  
 [<span data-ttu-id="5489b-119">Typowe scenariusze zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="5489b-119">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="5489b-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5489b-120">See also</span></span>
- [<span data-ttu-id="5489b-121">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="5489b-121">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="5489b-122">Model zabezpieczeń dla systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="5489b-122">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
