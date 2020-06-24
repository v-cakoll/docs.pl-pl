---
title: Uwierzytelnianie w programie WCF
description: Poznaj kilka mechanizmów w programie WCF, które zapewniają uwierzytelnianie, takie jak uwierzytelnianie systemu Windows, certyfikaty X. 509 i nazwa użytkownika i hasło.
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: 4c3348cfb84b8571dc1f24b774ffcd691aaa5001
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247523"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="9d3cb-103">Uwierzytelnianie w programie WCF</span><span class="sxs-lookup"><span data-stu-id="9d3cb-103">Authentication in WCF</span></span>
<span data-ttu-id="9d3cb-104">W poniższych tematach przedstawiono szereg różnych mechanizmów programu Windows Communication Foundation (WCF), które zapewniają uwierzytelnianie, na przykład uwierzytelnianie systemu Windows, certyfikaty X. 509 oraz nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="9d3cb-104">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9d3cb-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9d3cb-105">In This Section</span></span>  
 [<span data-ttu-id="9d3cb-106">Instrukcje: użycie dostawcy członkostwa platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9d3cb-106">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="9d3cb-107">Funkcje ASP.NET obejmują członkostwo i dostawcę ról, bazę danych do przechowywania par nazw użytkowników i haseł na potrzeby uwierzytelniania oraz role użytkowników na potrzeby autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="9d3cb-107">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="9d3cb-108">W tym temacie wyjaśniono, w jaki sposób usługi WCF mogą używać tej samej bazy danych do uwierzytelniania i autoryzowania użytkowników.</span><span class="sxs-lookup"><span data-stu-id="9d3cb-108">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="9d3cb-109">Instrukcje: używanie niestandardowej nazwy użytkownika i modułu weryfikacji hasła</span><span class="sxs-lookup"><span data-stu-id="9d3cb-109">How to: Use a Custom User Name and Password Validator</span></span>](how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="9d3cb-110">Pokazuje, jak zintegrować niestandardową nazwę użytkownika/moduł sprawdzania poprawności hasła.</span><span class="sxs-lookup"><span data-stu-id="9d3cb-110">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="9d3cb-111">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="9d3cb-111">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)  
 <span data-ttu-id="9d3cb-112">Aby zapewnić dodatkową ochronę, klient może uwierzytelnić usługę, określając oczekiwaną *tożsamość* usługi.</span><span class="sxs-lookup"><span data-stu-id="9d3cb-112">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="9d3cb-113">Jeśli Oczekiwana tożsamość i tożsamość zwrócona przez usługę nie są zgodne, uwierzytelnianie kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="9d3cb-113">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="9d3cb-114">Negocjacje i limity czasu dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="9d3cb-114">Security Negotiation and Timeouts</span></span>](security-negotiation-and-timeouts.md)  
 <span data-ttu-id="9d3cb-115">Opisuje sposób użycia <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> właściwości w <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> klasie.</span><span class="sxs-lookup"><span data-stu-id="9d3cb-115">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="9d3cb-116">Debugowanie błędów uwierzytelniania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9d3cb-116">Debugging Windows Authentication Errors</span></span>](debugging-windows-authentication-errors.md)  
 <span data-ttu-id="9d3cb-117">Koncentruje się na typowych problemach występujących podczas korzystania z uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="9d3cb-117">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9d3cb-118">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="9d3cb-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="9d3cb-119">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="9d3cb-119">Related Sections</span></span>  
 [<span data-ttu-id="9d3cb-120">Typowe scenariusze zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="9d3cb-120">Common Security Scenarios</span></span>](common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="9d3cb-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d3cb-121">See also</span></span>

- [<span data-ttu-id="9d3cb-122">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="9d3cb-122">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="9d3cb-123">[Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="9d3cb-123">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
