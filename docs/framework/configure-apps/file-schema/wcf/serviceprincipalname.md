---
title: '&lt;Element servicePrincipalName&gt;'
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: a22a905744980d0b370023e6236734a9bb0d6357
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150646"
---
# <a name="ltserviceprincipalnamegt"></a><span data-ttu-id="7118f-102">&lt;Element servicePrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="7118f-102">&lt;servicePrincipalName&gt;</span></span>
<span data-ttu-id="7118f-103">Określa tożsamość usługi przez jego głównej nazwy usługi (SPN).</span><span class="sxs-lookup"><span data-stu-id="7118f-103">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="7118f-104">Aby uzyskać więcej informacji na temat ustawiania nazwy SPN, zobacz [uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="7118f-104">For more information about setting the SPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="7118f-105">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="7118f-105">\<identity></span></span>  
<span data-ttu-id="7118f-106">\<Element servicePrincipalName ></span><span class="sxs-lookup"><span data-stu-id="7118f-106">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7118f-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="7118f-107">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7118f-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7118f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7118f-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7118f-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7118f-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7118f-110">Attributes</span></span>  
  
|<span data-ttu-id="7118f-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7118f-111">Attribute</span></span>|<span data-ttu-id="7118f-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7118f-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7118f-113">value</span><span class="sxs-lookup"><span data-stu-id="7118f-113">value</span></span>|<span data-ttu-id="7118f-114">Nazwa, przez którą klient jednoznacznie identyfikuje wystąpienie usługi.</span><span class="sxs-lookup"><span data-stu-id="7118f-114">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="7118f-115">Jeśli zainstalowano wiele wystąpień usługi na komputerach w całym lesie, każde wystąpienie musi mieć własną nazwę SPN.</span><span class="sxs-lookup"><span data-stu-id="7118f-115">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="7118f-116">Wystąpienie danej usługi może mieć wiele nazw SPN, jeśli istnieje kilka nazw, które klienci mogą korzystać z uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7118f-116">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7118f-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7118f-117">Child Elements</span></span>  
 <span data-ttu-id="7118f-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="7118f-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7118f-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7118f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7118f-120">Element</span><span class="sxs-lookup"><span data-stu-id="7118f-120">Element</span></span>|<span data-ttu-id="7118f-121">Opis</span><span class="sxs-lookup"><span data-stu-id="7118f-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7118f-122">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="7118f-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="7118f-123">Określa tożsamość usługi, aby zostać uwierzytelnionym przez klienta.</span><span class="sxs-lookup"><span data-stu-id="7118f-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7118f-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7118f-124">Remarks</span></span>  
 <span data-ttu-id="7118f-125">Bezpieczne klienta Windows Communication Foundation (WCF), który nawiązuje połączenie z punktem końcowym o tej tożsamości używa nazwy SPN podczas przeprowadzania uwierzytelniania SSPI z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="7118f-125">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7118f-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7118f-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.SpnEndpointIdentity>  
 [<span data-ttu-id="7118f-127">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="7118f-127">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="7118f-128">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="7118f-128">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
