---
title: Uwierzytelnianie w programie WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: b513c9713bd2c04e125915d1a0a87c86ce249666
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597647"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="ac8d1-102">Uwierzytelnianie w programie WCF</span><span class="sxs-lookup"><span data-stu-id="ac8d1-102">Authentication in WCF</span></span>
<span data-ttu-id="ac8d1-103">W poniższych tematach przedstawiono szereg różnych mechanizmów programu Windows Communication Foundation (WCF), które zapewniają uwierzytelnianie, na przykład uwierzytelnianie systemu Windows, certyfikaty X. 509 oraz nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="ac8d1-103">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ac8d1-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ac8d1-104">In This Section</span></span>  
 [<span data-ttu-id="ac8d1-105">Instrukcje: użycie dostawcy członkostwa platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ac8d1-105">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="ac8d1-106">Funkcje ASP.NET obejmują członkostwo i dostawcę ról, bazę danych do przechowywania par nazw użytkowników i haseł na potrzeby uwierzytelniania oraz role użytkowników na potrzeby autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="ac8d1-106">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="ac8d1-107">W tym temacie wyjaśniono, w jaki sposób usługi WCF mogą używać tej samej bazy danych do uwierzytelniania i autoryzowania użytkowników.</span><span class="sxs-lookup"><span data-stu-id="ac8d1-107">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="ac8d1-108">Instrukcje: używanie niestandardowej nazwy użytkownika i modułu weryfikacji hasła</span><span class="sxs-lookup"><span data-stu-id="ac8d1-108">How to: Use a Custom User Name and Password Validator</span></span>](how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="ac8d1-109">Pokazuje, jak zintegrować niestandardową nazwę użytkownika/moduł sprawdzania poprawności hasła.</span><span class="sxs-lookup"><span data-stu-id="ac8d1-109">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="ac8d1-110">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="ac8d1-110">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)  
 <span data-ttu-id="ac8d1-111">Aby zapewnić dodatkową ochronę, klient może uwierzytelnić usługę, określając oczekiwaną *tożsamość* usługi.</span><span class="sxs-lookup"><span data-stu-id="ac8d1-111">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="ac8d1-112">Jeśli Oczekiwana tożsamość i tożsamość zwrócona przez usługę nie są zgodne, uwierzytelnianie kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="ac8d1-112">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="ac8d1-113">Negocjacje i limity czasu dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ac8d1-113">Security Negotiation and Timeouts</span></span>](security-negotiation-and-timeouts.md)  
 <span data-ttu-id="ac8d1-114">Opisuje sposób użycia <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> właściwości w <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> klasie.</span><span class="sxs-lookup"><span data-stu-id="ac8d1-114">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="ac8d1-115">Debugowanie błędów uwierzytelniania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ac8d1-115">Debugging Windows Authentication Errors</span></span>](debugging-windows-authentication-errors.md)  
 <span data-ttu-id="ac8d1-116">Koncentruje się na typowych problemach występujących podczas korzystania z uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ac8d1-116">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ac8d1-117">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="ac8d1-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="ac8d1-118">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="ac8d1-118">Related Sections</span></span>  
 [<span data-ttu-id="ac8d1-119">Typowe scenariusze zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ac8d1-119">Common Security Scenarios</span></span>](common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="ac8d1-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ac8d1-120">See also</span></span>

- [<span data-ttu-id="ac8d1-121">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ac8d1-121">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="ac8d1-122">[Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="ac8d1-122">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
