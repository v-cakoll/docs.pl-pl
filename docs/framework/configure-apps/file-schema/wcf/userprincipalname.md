---
title: '&lt;userPrincipalName&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 616eb07a76da93ff1019ea7e80b5ce3151e6e8a4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltuserprincipalnamegt"></a><span data-ttu-id="13aa3-102">&lt;userPrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="13aa3-102">&lt;userPrincipalName&gt;</span></span>
<span data-ttu-id="13aa3-103">Określa główną nazwę użytkownika (UPN) usługi uwierzytelniania przez klienta.</span><span class="sxs-lookup"><span data-stu-id="13aa3-103">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="13aa3-104">Aby uzyskać więcej informacji na temat ustawiania nazwy UPN, zobacz [uwierzytelnianie i tożsamość usługi](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="13aa3-104">For more information about setting the UPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="13aa3-105">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="13aa3-105">\<identity></span></span>  
<span data-ttu-id="13aa3-106">\<userPrincipalName ></span><span class="sxs-lookup"><span data-stu-id="13aa3-106">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13aa3-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="13aa3-107">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13aa3-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="13aa3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="13aa3-109">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="13aa3-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13aa3-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="13aa3-110">Attributes</span></span>  
  
|<span data-ttu-id="13aa3-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="13aa3-111">Attribute</span></span>|<span data-ttu-id="13aa3-112">Opis</span><span class="sxs-lookup"><span data-stu-id="13aa3-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="13aa3-113">value</span><span class="sxs-lookup"><span data-stu-id="13aa3-113">value</span></span>|<span data-ttu-id="13aa3-114">Nazwa konta użytkownika (czasem określana jako nazwa logowania użytkownika) i nazwa domeny identyfikującej domenę, w której znajduje się konto użytkownika.</span><span class="sxs-lookup"><span data-stu-id="13aa3-114">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="13aa3-115">Jest to standardowy używana do logowania do domeny systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="13aa3-115">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="13aa3-116">Format: someone@example.com (podobnie jak w przypadku adresu e-mail).</span><span class="sxs-lookup"><span data-stu-id="13aa3-116">The format is: someone@example.com (as for an e-mail address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13aa3-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="13aa3-117">Child Elements</span></span>  
 <span data-ttu-id="13aa3-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="13aa3-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="13aa3-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="13aa3-119">Parent Elements</span></span>  
  
|<span data-ttu-id="13aa3-120">Element</span><span class="sxs-lookup"><span data-stu-id="13aa3-120">Element</span></span>|<span data-ttu-id="13aa3-121">Opis</span><span class="sxs-lookup"><span data-stu-id="13aa3-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13aa3-122">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="13aa3-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="13aa3-123">Określa tożsamość usługi uwierzytelniania przez klienta.</span><span class="sxs-lookup"><span data-stu-id="13aa3-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13aa3-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13aa3-124">Remarks</span></span>  
 <span data-ttu-id="13aa3-125">Bezpieczny [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] klient łączący punkt końcowy o tej tożsamości używa nazwy UPN, gdy z punktem końcowym uwierzytelniania SSPI.</span><span class="sxs-lookup"><span data-stu-id="13aa3-125">A secure [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13aa3-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="13aa3-126">Example</span></span>  
 <span data-ttu-id="13aa3-127">Poniższy kod konfiguracji określa nazwę UPN usługi uwierzytelniania przez klienta.</span><span class="sxs-lookup"><span data-stu-id="13aa3-127">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>  
  <userPrincipalName value="someone@cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="13aa3-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13aa3-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.UpnEndpointIdentity>  
 [<span data-ttu-id="13aa3-129">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="13aa3-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="13aa3-130">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="13aa3-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
