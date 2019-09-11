---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: da865a19a91d4af6221a13b53a174637d5fb8139
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854993"
---
# <a name="serviceprincipalname"></a><span data-ttu-id="c050d-101">\<servicePrincipalName></span><span class="sxs-lookup"><span data-stu-id="c050d-101">\<servicePrincipalName></span></span>
<span data-ttu-id="c050d-102">Określa tożsamość usługi za pomocą nazwy głównej usługi (SPN).</span><span class="sxs-lookup"><span data-stu-id="c050d-102">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
<span data-ttu-id="c050d-103">Aby uzyskać więcej informacji na temat ustawiania nazwy SPN, zobacz [tożsamość usługi i uwierzytelnianie](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c050d-103">For more information about setting the SPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="c050d-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c050d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c050d-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c050d-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c050d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)</span><span class="sxs-lookup"><span data-stu-id="c050d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="c050d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> punktu końcowego**](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="c050d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="c050d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> tożsamości**](identity.md)</span><span class="sxs-lookup"><span data-stu-id="c050d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="c050d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Nazwa ServicePrincipalName >**</span><span class="sxs-lookup"><span data-stu-id="c050d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePrincipalName>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c050d-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="c050d-110">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c050d-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c050d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c050d-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c050d-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c050d-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c050d-113">Attributes</span></span>  
  
|<span data-ttu-id="c050d-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c050d-114">Attribute</span></span>|<span data-ttu-id="c050d-115">Opis</span><span class="sxs-lookup"><span data-stu-id="c050d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c050d-116">value</span><span class="sxs-lookup"><span data-stu-id="c050d-116">value</span></span>|<span data-ttu-id="c050d-117">Nazwa, przez którą klient jednoznacznie identyfikuje wystąpienie usługi.</span><span class="sxs-lookup"><span data-stu-id="c050d-117">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="c050d-118">W przypadku instalowania wielu wystąpień usługi na komputerach w lesie, każde wystąpienie musi mieć własną nazwę SPN.</span><span class="sxs-lookup"><span data-stu-id="c050d-118">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="c050d-119">Dana nazwa wystąpienia usługi może mieć wiele nazw SPN, jeśli istnieje wiele nazwy, których klienci mogą używać na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="c050d-119">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c050d-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c050d-120">Child Elements</span></span>  
 <span data-ttu-id="c050d-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="c050d-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c050d-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c050d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c050d-123">Element</span><span class="sxs-lookup"><span data-stu-id="c050d-123">Element</span></span>|<span data-ttu-id="c050d-124">Opis</span><span class="sxs-lookup"><span data-stu-id="c050d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c050d-125">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="c050d-125">\<identity></span></span>](identity.md)|<span data-ttu-id="c050d-126">Określa tożsamość usługi do uwierzytelnienia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="c050d-126">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c050d-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c050d-127">Remarks</span></span>  
 <span data-ttu-id="c050d-128">Bezpieczny Windows Communication Foundation (WCF), który nawiązuje połączenie z punktem końcowym z tą tożsamością używa nazwy SPN podczas uwierzytelniania SSPI przy użyciu punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c050d-128">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c050d-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c050d-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="c050d-130">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="c050d-130">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="c050d-131">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="c050d-131">\<identity></span></span>](identity.md)
