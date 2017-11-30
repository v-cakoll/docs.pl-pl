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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b93a0cc24953024e265df418ec6dd738598dd0f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltuserprincipalnamegt"></a><span data-ttu-id="14cbf-102">&lt;userPrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="14cbf-102">&lt;userPrincipalName&gt;</span></span>
<span data-ttu-id="14cbf-103">Określa główną nazwę użytkownika (UPN) usługi uwierzytelniania przez klienta.</span><span class="sxs-lookup"><span data-stu-id="14cbf-103">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="14cbf-104">Aby uzyskać więcej informacji na temat ustawiania nazwy UPN, zobacz [uwierzytelnianie i tożsamość usługi](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="14cbf-104">For more information about setting the UPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="14cbf-105">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="14cbf-105">\<identity></span></span>  
<span data-ttu-id="14cbf-106">\<userPrincipalName ></span><span class="sxs-lookup"><span data-stu-id="14cbf-106">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14cbf-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="14cbf-107">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14cbf-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="14cbf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="14cbf-109">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="14cbf-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14cbf-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="14cbf-110">Attributes</span></span>  
  
|<span data-ttu-id="14cbf-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="14cbf-111">Attribute</span></span>|<span data-ttu-id="14cbf-112">Opis</span><span class="sxs-lookup"><span data-stu-id="14cbf-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="14cbf-113">value</span><span class="sxs-lookup"><span data-stu-id="14cbf-113">value</span></span>|<span data-ttu-id="14cbf-114">Nazwa konta użytkownika (czasem określana jako nazwa logowania użytkownika) i nazwa domeny identyfikującej domenę, w której znajduje się konto użytkownika.</span><span class="sxs-lookup"><span data-stu-id="14cbf-114">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="14cbf-115">Jest to standardowy używana do logowania do domeny systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="14cbf-115">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="14cbf-116">Format: someone@example.com (podobnie jak w przypadku adresu e-mail).</span><span class="sxs-lookup"><span data-stu-id="14cbf-116">The format is: someone@example.com (as for an e-mail address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14cbf-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="14cbf-117">Child Elements</span></span>  
 <span data-ttu-id="14cbf-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="14cbf-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="14cbf-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="14cbf-119">Parent Elements</span></span>  
  
|<span data-ttu-id="14cbf-120">Element</span><span class="sxs-lookup"><span data-stu-id="14cbf-120">Element</span></span>|<span data-ttu-id="14cbf-121">Opis</span><span class="sxs-lookup"><span data-stu-id="14cbf-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14cbf-122">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="14cbf-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="14cbf-123">Określa tożsamość usługi uwierzytelniania przez klienta.</span><span class="sxs-lookup"><span data-stu-id="14cbf-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14cbf-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="14cbf-124">Remarks</span></span>  
 <span data-ttu-id="14cbf-125">Bezpieczny [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] klient łączący punkt końcowy o tej tożsamości używa nazwy UPN, gdy z punktem końcowym uwierzytelniania SSPI.</span><span class="sxs-lookup"><span data-stu-id="14cbf-125">A secure [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14cbf-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="14cbf-126">Example</span></span>  
 <span data-ttu-id="14cbf-127">Poniższy kod konfiguracji określa nazwę UPN usługi uwierzytelniania przez klienta.</span><span class="sxs-lookup"><span data-stu-id="14cbf-127">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>  
  <userPrincipalName value="someone@cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="14cbf-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="14cbf-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.UpnEndpointIdentity>  
 [<span data-ttu-id="14cbf-129">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="14cbf-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="14cbf-130">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="14cbf-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
