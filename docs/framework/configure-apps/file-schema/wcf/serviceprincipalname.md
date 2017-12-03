---
title: '&lt;servicePrincipalName&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b734a095f0c9ea9ad1bd6e78f3ef4264f4f2317e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltserviceprincipalnamegt"></a><span data-ttu-id="da927-102">&lt;servicePrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="da927-102">&lt;servicePrincipalName&gt;</span></span>
<span data-ttu-id="da927-103">Określa tożsamość usługi przez jej nazwy usługi (SPN).</span><span class="sxs-lookup"><span data-stu-id="da927-103">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="da927-104">Aby uzyskać więcej informacji na temat ustawiania nazwy SPN, zobacz [uwierzytelnianie i tożsamość usługi](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="da927-104">For more information about setting the SPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="da927-105">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="da927-105">\<identity></span></span>  
<span data-ttu-id="da927-106">\<servicePrincipalName ></span><span class="sxs-lookup"><span data-stu-id="da927-106">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da927-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="da927-107">Syntax</span></span>  
  
```xml  
<servicePrincipalName value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="da927-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="da927-108">Attributes and Elements</span></span>  
 <span data-ttu-id="da927-109">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="da927-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="da927-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="da927-110">Attributes</span></span>  
  
|<span data-ttu-id="da927-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="da927-111">Attribute</span></span>|<span data-ttu-id="da927-112">Opis</span><span class="sxs-lookup"><span data-stu-id="da927-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="da927-113">value</span><span class="sxs-lookup"><span data-stu-id="da927-113">value</span></span>|<span data-ttu-id="da927-114">Nazwa, przez którą klient jednoznacznie identyfikuje wystąpienie usługi.</span><span class="sxs-lookup"><span data-stu-id="da927-114">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="da927-115">Jeśli zainstalowano wiele wystąpień usługi na komputerach w całym lesie, każde wystąpienie musi mieć własną nazwę SPN.</span><span class="sxs-lookup"><span data-stu-id="da927-115">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="da927-116">Wystąpienie danej usługi może mieć wiele nazw SPN, jeśli istnieje wiele nazw, których klienci mogą używać do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="da927-116">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="da927-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="da927-117">Child Elements</span></span>  
 <span data-ttu-id="da927-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="da927-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="da927-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="da927-119">Parent Elements</span></span>  
  
|<span data-ttu-id="da927-120">Element</span><span class="sxs-lookup"><span data-stu-id="da927-120">Element</span></span>|<span data-ttu-id="da927-121">Opis</span><span class="sxs-lookup"><span data-stu-id="da927-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="da927-122">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="da927-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="da927-123">Określa tożsamość usługi uwierzytelniania przez klienta.</span><span class="sxs-lookup"><span data-stu-id="da927-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da927-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="da927-124">Remarks</span></span>  
 <span data-ttu-id="da927-125">Bezpieczny [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] klient łączący punkt końcowy o tej tożsamości używa główną nazwę usługi, gdy z punktem końcowym uwierzytelniania SSPI.</span><span class="sxs-lookup"><span data-stu-id="da927-125">A secure [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da927-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da927-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.SpnEndpointIdentity>  
 [<span data-ttu-id="da927-127">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="da927-127">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="da927-128">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="da927-128">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
