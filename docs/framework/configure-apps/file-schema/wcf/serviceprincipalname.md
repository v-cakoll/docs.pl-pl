---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: 28ae27481ea9cb86c31b5be1f12b5491f8ca143e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936154"
---
# <a name="serviceprincipalname"></a><span data-ttu-id="61434-101">\<servicePrincipalName></span><span class="sxs-lookup"><span data-stu-id="61434-101">\<servicePrincipalName></span></span>
<span data-ttu-id="61434-102">Określa tożsamość usługi za pomocą nazwy głównej usługi (SPN).</span><span class="sxs-lookup"><span data-stu-id="61434-102">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="61434-103">Aby uzyskać więcej informacji na temat ustawiania nazwy SPN, zobacz [tożsamość usługi i uwierzytelnianie](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="61434-103">For more information about setting the SPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="61434-104">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="61434-104">\<identity></span></span>  
<span data-ttu-id="61434-105">\<servicePrincipalName></span><span class="sxs-lookup"><span data-stu-id="61434-105">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61434-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="61434-106">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61434-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="61434-107">Attributes and Elements</span></span>  
 <span data-ttu-id="61434-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="61434-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61434-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="61434-109">Attributes</span></span>  
  
|<span data-ttu-id="61434-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="61434-110">Attribute</span></span>|<span data-ttu-id="61434-111">Opis</span><span class="sxs-lookup"><span data-stu-id="61434-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="61434-112">value</span><span class="sxs-lookup"><span data-stu-id="61434-112">value</span></span>|<span data-ttu-id="61434-113">Nazwa, przez którą klient jednoznacznie identyfikuje wystąpienie usługi.</span><span class="sxs-lookup"><span data-stu-id="61434-113">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="61434-114">W przypadku instalowania wielu wystąpień usługi na komputerach w lesie, każde wystąpienie musi mieć własną nazwę SPN.</span><span class="sxs-lookup"><span data-stu-id="61434-114">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="61434-115">Dana nazwa wystąpienia usługi może mieć wiele nazw SPN, jeśli istnieje wiele nazwy, których klienci mogą używać na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="61434-115">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61434-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="61434-116">Child Elements</span></span>  
 <span data-ttu-id="61434-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="61434-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="61434-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="61434-118">Parent Elements</span></span>  
  
|<span data-ttu-id="61434-119">Element</span><span class="sxs-lookup"><span data-stu-id="61434-119">Element</span></span>|<span data-ttu-id="61434-120">Opis</span><span class="sxs-lookup"><span data-stu-id="61434-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61434-121">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="61434-121">\<identity></span></span>](identity.md)|<span data-ttu-id="61434-122">Określa tożsamość usługi do uwierzytelnienia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="61434-122">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61434-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="61434-123">Remarks</span></span>  
 <span data-ttu-id="61434-124">Bezpieczny Windows Communication Foundation (WCF), który nawiązuje połączenie z punktem końcowym z tą tożsamością używa nazwy SPN podczas uwierzytelniania SSPI przy użyciu punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="61434-124">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61434-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61434-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="61434-126">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="61434-126">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="61434-127">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="61434-127">\<identity></span></span>](identity.md)
