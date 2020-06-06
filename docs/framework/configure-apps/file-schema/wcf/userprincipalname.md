---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 299af8c4a013d17d7c5b7285f6fb89892c4164a8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854819"
---
# \<userPrincipalName>
<span data-ttu-id="afea0-101">Określa główną nazwę użytkownika (UPN) usługi do uwierzytelnienia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="afea0-101">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
<span data-ttu-id="afea0-102">Aby uzyskać więcej informacji na temat ustawiania nazwy UPN, zobacz [tożsamość usługi i uwierzytelnianie](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="afea0-102">For more information about setting the UPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userPrincipalName>**  
  
## <a name="syntax"></a><span data-ttu-id="afea0-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="afea0-103">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="afea0-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="afea0-104">Attributes and Elements</span></span>  
 <span data-ttu-id="afea0-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="afea0-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="afea0-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="afea0-106">Attributes</span></span>  
  
|<span data-ttu-id="afea0-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="afea0-107">Attribute</span></span>|<span data-ttu-id="afea0-108">Opis</span><span class="sxs-lookup"><span data-stu-id="afea0-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="afea0-109">value</span><span class="sxs-lookup"><span data-stu-id="afea0-109">value</span></span>|<span data-ttu-id="afea0-110">Nazwa konta użytkownika (czasem określana jako nazwa logowania użytkownika) i nazwa domeny identyfikującej domenę, w której znajduje się konto użytkownika.</span><span class="sxs-lookup"><span data-stu-id="afea0-110">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="afea0-111">Jest to standardowe użycie logowania do domeny systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="afea0-111">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="afea0-112">Format to: someone@example.com (jak w przypadku adresu e-mail).</span><span class="sxs-lookup"><span data-stu-id="afea0-112">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="afea0-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="afea0-113">Child Elements</span></span>  
 <span data-ttu-id="afea0-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="afea0-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="afea0-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="afea0-115">Parent Elements</span></span>  
  
|<span data-ttu-id="afea0-116">Element</span><span class="sxs-lookup"><span data-stu-id="afea0-116">Element</span></span>|<span data-ttu-id="afea0-117">Opis</span><span class="sxs-lookup"><span data-stu-id="afea0-117">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="afea0-118">Określa tożsamość usługi do uwierzytelnienia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="afea0-118">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afea0-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="afea0-119">Remarks</span></span>  
 <span data-ttu-id="afea0-120">Bezpieczny Windows Communication Foundation (WCF), który nawiązuje połączenie z punktem końcowym z tą tożsamością używa nazwy UPN podczas uwierzytelniania SSPI przy użyciu punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="afea0-120">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afea0-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="afea0-121">Example</span></span>  
 <span data-ttu-id="afea0-122">Poniższy kod konfiguracji określa nazwę UPN usługi do uwierzytelnienia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="afea0-122">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="afea0-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="afea0-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="afea0-124">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="afea0-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
