---
title: "Niestandardowe poświadczenia i walidacja poświadczeń"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- credentials [WCF], custom
- credentials [WCF]
- custom credentials [WCF]
- credential validation [WCF]
- credentials [WCF], validation
ms.assetid: da831bec-e281-4d44-b343-437b5eef688e
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c3ca7726f3a6a0c5faaab1cbbd0b31125ce0c1d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="custom-credential-and-credential-validation"></a><span data-ttu-id="134b4-102">Niestandardowe poświadczenia i walidacja poświadczeń</span><span class="sxs-lookup"><span data-stu-id="134b4-102">Custom Credential and Credential Validation</span></span>
<span data-ttu-id="134b4-103">Zabezpieczenia w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] jest oparte na wymianie poświadczeń między usług i klientów.</span><span class="sxs-lookup"><span data-stu-id="134b4-103">Security in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is based on the exchange of credentials between services and clients.</span></span> <span data-ttu-id="134b4-104">Większość scenariuszy zabezpieczeń można spełnić przy użyciu popularnych typów poświadczeń, takie jak Windows (Kerberos), nazwę użytkownika i hasła i certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="134b4-104">Most security scenarios can be satisfied using common credential types, such as Windows (Kerberos), username and passwords, and certificates.</span></span> <span data-ttu-id="134b4-105">Jednak jeśli nowy typ poświadczeń jest wymagane, tematy w tej sekcji opisano sposób obsługi i weryfikowanie nowych typów.</span><span class="sxs-lookup"><span data-stu-id="134b4-105">However, if a new type of credential is required, the topics in this section explain how to handle and validate new types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="134b4-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="134b4-106">In This Section</span></span>  
 [<span data-ttu-id="134b4-107">Porady: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów</span><span class="sxs-lookup"><span data-stu-id="134b4-107">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 <span data-ttu-id="134b4-108">Opis sposobu dostosowywania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] weryfikacji przez dziedziczenie z <xref:System.IdentityModel.Selectors.X509CertificateValidator> klasy.</span><span class="sxs-lookup"><span data-stu-id="134b4-108">Explains how to customize [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] validation by inheriting from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span>  
  
 [<span data-ttu-id="134b4-109">Wskazówki: Tworzenie niestandardowego klienta i poświadczeń usługi</span><span class="sxs-lookup"><span data-stu-id="134b4-109">Walkthrough: Creating Custom Client and Service Credentials</span></span>](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 <span data-ttu-id="134b4-110">Pokazuje, jak rozszerzyć <xref:System.ServiceModel.Description.ClientCredentials> i <xref:System.ServiceModel.Description.ServiceCredentials> klasy w celu uwzględnienia nowych poświadczeń typów.</span><span class="sxs-lookup"><span data-stu-id="134b4-110">Demonstrates how to extend the <xref:System.ServiceModel.Description.ClientCredentials> and <xref:System.ServiceModel.Description.ServiceCredentials> classes to accommodate new credential types.</span></span> <span data-ttu-id="134b4-111">Jest to pierwszy z serii tematów, które umożliwiają tworzenie niestandardowych poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="134b4-111">This is first in a series of topics that enable creation of custom credential types.</span></span>  
  
 [<span data-ttu-id="134b4-112">Jak: utworzyć dostawcę tokenu zabezpieczającego niestandardowych</span><span class="sxs-lookup"><span data-stu-id="134b4-112">How to: Create a Custom Security Token Provider</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 <span data-ttu-id="134b4-113">Wyjaśniono, jak utworzyć dostawcę tokenu zabezpieczającego do obsługi nowych typów poświadczeń i zwrócić nowe tokeny dla poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="134b4-113">Explains how to create a security token provider to handle new credential types and return new tokens for the credential.</span></span> <span data-ttu-id="134b4-114">Jest to drugi tematu w serii.</span><span class="sxs-lookup"><span data-stu-id="134b4-114">This is the second topic in the series.</span></span>  
  
 [<span data-ttu-id="134b4-115">Porady: tworzenie wystawcy uwierzytelnienia tokenu zabezpieczeń niestandardowych</span><span class="sxs-lookup"><span data-stu-id="134b4-115">How to: Create a Custom Security Token Authenticator</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 <span data-ttu-id="134b4-116">Wyjaśnia sposób tworzenia niestandardowego wystawcy uwierzytelnienia do nowego typu poświadczeń uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="134b4-116">Explains how to create a custom authenticator to authenticate a new credential type.</span></span> <span data-ttu-id="134b4-117">Jest to trzeci tematu w serii.</span><span class="sxs-lookup"><span data-stu-id="134b4-117">This is the third topic in the series.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="134b4-118">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="134b4-118">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a><span data-ttu-id="134b4-119">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="134b4-119">Related Sections</span></span>  
 [<span data-ttu-id="134b4-120">Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="134b4-120">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [<span data-ttu-id="134b4-121">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="134b4-121">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="134b4-122">Autoryzacji</span><span class="sxs-lookup"><span data-stu-id="134b4-122">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="134b4-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="134b4-123">See Also</span></span>  
 [<span data-ttu-id="134b4-124">Zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="134b4-124">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
