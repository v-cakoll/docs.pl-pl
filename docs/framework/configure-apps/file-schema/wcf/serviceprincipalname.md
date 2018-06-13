---
title: '&lt;ServicePrincipalName&gt;'
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: e5c1f5a6986d57d20180560b12f5c7c5540a590d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750729"
---
# <a name="ltserviceprincipalnamegt"></a><span data-ttu-id="ceb18-102">&lt;ServicePrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="ceb18-102">&lt;servicePrincipalName&gt;</span></span>
<span data-ttu-id="ceb18-103">Określa tożsamość usługi przez jej nazwy usługi (SPN).</span><span class="sxs-lookup"><span data-stu-id="ceb18-103">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="ceb18-104">Aby uzyskać więcej informacji na temat ustawiania nazwy SPN, zobacz [uwierzytelnianie i tożsamość usługi](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ceb18-104">For more information about setting the SPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="ceb18-105">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="ceb18-105">\<identity></span></span>  
<span data-ttu-id="ceb18-106">\<servicePrincipalName ></span><span class="sxs-lookup"><span data-stu-id="ceb18-106">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceb18-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ceb18-107">Syntax</span></span>  
  
```xml  
<servicePrincipalName value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ceb18-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ceb18-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ceb18-109">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ceb18-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ceb18-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ceb18-110">Attributes</span></span>  
  
|<span data-ttu-id="ceb18-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ceb18-111">Attribute</span></span>|<span data-ttu-id="ceb18-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ceb18-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ceb18-113">value</span><span class="sxs-lookup"><span data-stu-id="ceb18-113">value</span></span>|<span data-ttu-id="ceb18-114">Nazwa, przez którą klient jednoznacznie identyfikuje wystąpienie usługi.</span><span class="sxs-lookup"><span data-stu-id="ceb18-114">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="ceb18-115">Jeśli zainstalowano wiele wystąpień usługi na komputerach w całym lesie, każde wystąpienie musi mieć własną nazwę SPN.</span><span class="sxs-lookup"><span data-stu-id="ceb18-115">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="ceb18-116">Wystąpienie danej usługi może mieć wiele nazw SPN, jeśli istnieje wiele nazw, których klienci mogą używać do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ceb18-116">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ceb18-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ceb18-117">Child Elements</span></span>  
 <span data-ttu-id="ceb18-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="ceb18-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ceb18-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ceb18-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ceb18-120">Element</span><span class="sxs-lookup"><span data-stu-id="ceb18-120">Element</span></span>|<span data-ttu-id="ceb18-121">Opis</span><span class="sxs-lookup"><span data-stu-id="ceb18-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ceb18-122">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="ceb18-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="ceb18-123">Określa tożsamość usługi uwierzytelniania przez klienta.</span><span class="sxs-lookup"><span data-stu-id="ceb18-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ceb18-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ceb18-124">Remarks</span></span>  
 <span data-ttu-id="ceb18-125">Bezpieczne łączący punkt końcowy o tej tożsamości klienta Windows Communication Foundation (WCF) używa nazwy SPN podczas przeprowadzania uwierzytelniania SSPI z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="ceb18-125">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceb18-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ceb18-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.SpnEndpointIdentity>  
 [<span data-ttu-id="ceb18-127">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="ceb18-127">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="ceb18-128">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="ceb18-128">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
