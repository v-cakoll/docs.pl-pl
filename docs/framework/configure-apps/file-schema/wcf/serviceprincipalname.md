---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: da865a19a91d4af6221a13b53a174637d5fb8139
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854993"
---
# \<servicePrincipalName>
<span data-ttu-id="e1f9e-101">Określa tożsamość usługi za pomocą nazwy głównej usługi (SPN).</span><span class="sxs-lookup"><span data-stu-id="e1f9e-101">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
<span data-ttu-id="e1f9e-102">Aby uzyskać więcej informacji na temat ustawiania nazwy SPN, zobacz [tożsamość usługi i uwierzytelnianie](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e1f9e-102">For more information about setting the SPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePrincipalName>**  
  
## <a name="syntax"></a><span data-ttu-id="e1f9e-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1f9e-103">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1f9e-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e1f9e-104">Attributes and Elements</span></span>  
 <span data-ttu-id="e1f9e-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e1f9e-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1f9e-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e1f9e-106">Attributes</span></span>  
  
|<span data-ttu-id="e1f9e-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e1f9e-107">Attribute</span></span>|<span data-ttu-id="e1f9e-108">Opis</span><span class="sxs-lookup"><span data-stu-id="e1f9e-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e1f9e-109">value</span><span class="sxs-lookup"><span data-stu-id="e1f9e-109">value</span></span>|<span data-ttu-id="e1f9e-110">Nazwa, przez którą klient jednoznacznie identyfikuje wystąpienie usługi.</span><span class="sxs-lookup"><span data-stu-id="e1f9e-110">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="e1f9e-111">W przypadku instalowania wielu wystąpień usługi na komputerach w lesie, każde wystąpienie musi mieć własną nazwę SPN.</span><span class="sxs-lookup"><span data-stu-id="e1f9e-111">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="e1f9e-112">Dana nazwa wystąpienia usługi może mieć wiele nazw SPN, jeśli istnieje wiele nazwy, których klienci mogą używać na potrzeby uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="e1f9e-112">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e1f9e-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e1f9e-113">Child Elements</span></span>  
 <span data-ttu-id="e1f9e-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="e1f9e-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e1f9e-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e1f9e-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e1f9e-116">Element</span><span class="sxs-lookup"><span data-stu-id="e1f9e-116">Element</span></span>|<span data-ttu-id="e1f9e-117">Opis</span><span class="sxs-lookup"><span data-stu-id="e1f9e-117">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="e1f9e-118">Określa tożsamość usługi do uwierzytelnienia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="e1f9e-118">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1f9e-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e1f9e-119">Remarks</span></span>  
 <span data-ttu-id="e1f9e-120">Bezpieczny Windows Communication Foundation (WCF), który nawiązuje połączenie z punktem końcowym z tą tożsamością używa nazwy SPN podczas uwierzytelniania SSPI przy użyciu punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="e1f9e-120">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1f9e-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1f9e-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="e1f9e-122">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="e1f9e-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
