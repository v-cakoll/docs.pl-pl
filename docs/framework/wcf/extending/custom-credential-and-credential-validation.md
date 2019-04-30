---
title: Niestandardowe poświadczenia i weryfikacja poświadczeń
ms.date: 03/30/2017
helpviewer_keywords:
- credentials [WCF], custom
- credentials [WCF]
- custom credentials [WCF]
- credential validation [WCF]
- credentials [WCF], validation
ms.assetid: da831bec-e281-4d44-b343-437b5eef688e
ms.openlocfilehash: 3b1ff700010f471a4d9be117f363083b6cbed493
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696447"
---
# <a name="custom-credential-and-credential-validation"></a><span data-ttu-id="77d3c-102">Niestandardowe poświadczenia i weryfikacja poświadczeń</span><span class="sxs-lookup"><span data-stu-id="77d3c-102">Custom Credential and Credential Validation</span></span>
<span data-ttu-id="77d3c-103">Zabezpieczenia w Windows Communication Foundation (WCF) opiera się na wymianie poświadczeń między usług i klientów.</span><span class="sxs-lookup"><span data-stu-id="77d3c-103">Security in Windows Communication Foundation (WCF) is based on the exchange of credentials between services and clients.</span></span> <span data-ttu-id="77d3c-104">Większość scenariuszy zabezpieczeń mogą zostać zrealizowane przy użyciu popularnych typów poświadczeń, takich jak Windows (Kerberos), nazwę użytkownika i hasła oraz certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="77d3c-104">Most security scenarios can be satisfied using common credential types, such as Windows (Kerberos), username and passwords, and certificates.</span></span> <span data-ttu-id="77d3c-105">Jednak jeśli wymagany jest nowy typ poświadczeń, tematy w tej sekcji wyjaśniono, jak obsługiwać i Zweryfikuj nowe typy.</span><span class="sxs-lookup"><span data-stu-id="77d3c-105">However, if a new type of credential is required, the topics in this section explain how to handle and validate new types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="77d3c-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="77d3c-106">In This Section</span></span>  
 [<span data-ttu-id="77d3c-107">Instrukcje: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów</span><span class="sxs-lookup"><span data-stu-id="77d3c-107">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 <span data-ttu-id="77d3c-108">Opis sposobu dostosowywania WCF weryfikacji przez dziedziczenie z <xref:System.IdentityModel.Selectors.X509CertificateValidator> klasy.</span><span class="sxs-lookup"><span data-stu-id="77d3c-108">Explains how to customize WCF validation by inheriting from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span>  
  
 [<span data-ttu-id="77d3c-109">Przewodnik: Tworzenie niestandardowego klienta i poświadczeń usługi</span><span class="sxs-lookup"><span data-stu-id="77d3c-109">Walkthrough: Creating Custom Client and Service Credentials</span></span>](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 <span data-ttu-id="77d3c-110">Pokazuje, jak rozszerzyć <xref:System.ServiceModel.Description.ClientCredentials> i <xref:System.ServiceModel.Description.ServiceCredentials> klasy w celu uwzględnienia nowych poświadczeń typów.</span><span class="sxs-lookup"><span data-stu-id="77d3c-110">Demonstrates how to extend the <xref:System.ServiceModel.Description.ClientCredentials> and <xref:System.ServiceModel.Description.ServiceCredentials> classes to accommodate new credential types.</span></span> <span data-ttu-id="77d3c-111">To jest pierwszy w szeregu tematów, które umożliwiają tworzenie typów niestandardowych poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="77d3c-111">This is first in a series of topics that enable creation of custom credential types.</span></span>  
  
 [<span data-ttu-id="77d3c-112">Instrukcje: Tworzenie niestandardowego dostawcy tokenów zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="77d3c-112">How to: Create a Custom Security Token Provider</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 <span data-ttu-id="77d3c-113">Wyjaśnia, jak utworzyć dostawcę tokenu zabezpieczającego, aby obsługiwać nowe typy poświadczeń i wrócić nowych tokenów dla poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="77d3c-113">Explains how to create a security token provider to handle new credential types and return new tokens for the credential.</span></span> <span data-ttu-id="77d3c-114">Jest to drugi tematu w serii.</span><span class="sxs-lookup"><span data-stu-id="77d3c-114">This is the second topic in the series.</span></span>  
  
 [<span data-ttu-id="77d3c-115">Instrukcje: Tworzenie wystawcy uwierzytelniania tokenu zabezpieczeń niestandardowych</span><span class="sxs-lookup"><span data-stu-id="77d3c-115">How to: Create a Custom Security Token Authenticator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 <span data-ttu-id="77d3c-116">Omówiono tworzenie niestandardowego wystawcy uwierzytelniania na nowy typ poświadczeń uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="77d3c-116">Explains how to create a custom authenticator to authenticate a new credential type.</span></span> <span data-ttu-id="77d3c-117">Jest to trzeci tematu w serii.</span><span class="sxs-lookup"><span data-stu-id="77d3c-117">This is the third topic in the series.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="77d3c-118">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="77d3c-118">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a><span data-ttu-id="77d3c-119">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="77d3c-119">Related Sections</span></span>  
 [<span data-ttu-id="77d3c-120">Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="77d3c-120">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [<span data-ttu-id="77d3c-121">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="77d3c-121">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="77d3c-122">Autoryzacja</span><span class="sxs-lookup"><span data-stu-id="77d3c-122">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="77d3c-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77d3c-123">See also</span></span>

- [<span data-ttu-id="77d3c-124">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="77d3c-124">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
