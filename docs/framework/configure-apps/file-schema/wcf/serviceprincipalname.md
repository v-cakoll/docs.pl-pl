---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: 75e95bcbaee229f19bdfdd119b548ed612f4ddaa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204409"
---
# <a name="serviceprincipalname"></a><span data-ttu-id="4d9b4-101">\<servicePrincipalName></span><span class="sxs-lookup"><span data-stu-id="4d9b4-101">\<servicePrincipalName></span></span>
<span data-ttu-id="4d9b4-102">Określa tożsamość usługi przez jego głównej nazwy usługi (SPN).</span><span class="sxs-lookup"><span data-stu-id="4d9b4-102">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="4d9b4-103">Aby uzyskać więcej informacji na temat ustawiania nazwy SPN, zobacz [uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="4d9b4-103">For more information about setting the SPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="4d9b4-104">\<identity></span><span class="sxs-lookup"><span data-stu-id="4d9b4-104">\<identity></span></span>  
<span data-ttu-id="4d9b4-105">\<servicePrincipalName></span><span class="sxs-lookup"><span data-stu-id="4d9b4-105">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d9b4-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d9b4-106">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d9b4-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4d9b4-107">Attributes and Elements</span></span>  
 <span data-ttu-id="4d9b4-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4d9b4-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d9b4-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4d9b4-109">Attributes</span></span>  
  
|<span data-ttu-id="4d9b4-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4d9b4-110">Attribute</span></span>|<span data-ttu-id="4d9b4-111">Opis</span><span class="sxs-lookup"><span data-stu-id="4d9b4-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4d9b4-112">value</span><span class="sxs-lookup"><span data-stu-id="4d9b4-112">value</span></span>|<span data-ttu-id="4d9b4-113">Nazwa, przez którą klient jednoznacznie identyfikuje wystąpienie usługi.</span><span class="sxs-lookup"><span data-stu-id="4d9b4-113">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="4d9b4-114">Jeśli zainstalowano wiele wystąpień usługi na komputerach w całym lesie, każde wystąpienie musi mieć własną nazwę SPN.</span><span class="sxs-lookup"><span data-stu-id="4d9b4-114">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="4d9b4-115">Wystąpienie danej usługi może mieć wiele nazw SPN, jeśli istnieje kilka nazw, które klienci mogą korzystać z uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="4d9b4-115">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d9b4-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4d9b4-116">Child Elements</span></span>  
 <span data-ttu-id="4d9b4-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="4d9b4-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4d9b4-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4d9b4-118">Parent Elements</span></span>  
  
|<span data-ttu-id="4d9b4-119">Element</span><span class="sxs-lookup"><span data-stu-id="4d9b4-119">Element</span></span>|<span data-ttu-id="4d9b4-120">Opis</span><span class="sxs-lookup"><span data-stu-id="4d9b4-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d9b4-121">\<identity></span><span class="sxs-lookup"><span data-stu-id="4d9b4-121">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="4d9b4-122">Określa tożsamość usługi, aby zostać uwierzytelnionym przez klienta.</span><span class="sxs-lookup"><span data-stu-id="4d9b4-122">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d9b4-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d9b4-123">Remarks</span></span>  
 <span data-ttu-id="4d9b4-124">Bezpieczne klienta Windows Communication Foundation (WCF), który nawiązuje połączenie z punktem końcowym o tej tożsamości używa nazwy SPN podczas przeprowadzania uwierzytelniania SSPI z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="4d9b4-124">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d9b4-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d9b4-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="4d9b4-126">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="4d9b4-126">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="4d9b4-127">\<identity></span><span class="sxs-lookup"><span data-stu-id="4d9b4-127">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
