---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 299af8c4a013d17d7c5b7285f6fb89892c4164a8
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854819"
---
# <a name="userprincipalname"></a><span data-ttu-id="1d5a1-101">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="1d5a1-101">\<userPrincipalName></span></span>
<span data-ttu-id="1d5a1-102">Określa główną nazwę użytkownika (UPN) usługi do uwierzytelnienia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="1d5a1-102">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
<span data-ttu-id="1d5a1-103">Aby uzyskać więcej informacji na temat ustawiania nazwy UPN, zobacz [tożsamość usługi i uwierzytelnianie](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="1d5a1-103">For more information about setting the UPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="1d5a1-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1d5a1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1d5a1-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1d5a1-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1d5a1-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)</span><span class="sxs-lookup"><span data-stu-id="1d5a1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="1d5a1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> punktu końcowego**](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="1d5a1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="1d5a1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> tożsamości**](identity.md)</span><span class="sxs-lookup"><span data-stu-id="1d5a1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="1d5a1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> userPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="1d5a1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userPrincipalName>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d5a1-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d5a1-110">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d5a1-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1d5a1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1d5a1-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1d5a1-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d5a1-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1d5a1-113">Attributes</span></span>  
  
|<span data-ttu-id="1d5a1-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1d5a1-114">Attribute</span></span>|<span data-ttu-id="1d5a1-115">Opis</span><span class="sxs-lookup"><span data-stu-id="1d5a1-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1d5a1-116">value</span><span class="sxs-lookup"><span data-stu-id="1d5a1-116">value</span></span>|<span data-ttu-id="1d5a1-117">Nazwa konta użytkownika (czasem określana jako nazwa logowania użytkownika) i nazwa domeny identyfikującej domenę, w której znajduje się konto użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1d5a1-117">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="1d5a1-118">Jest to standardowe użycie logowania do domeny systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1d5a1-118">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="1d5a1-119">Format to: someone@example.com (jak w przypadku adresu e-mail).</span><span class="sxs-lookup"><span data-stu-id="1d5a1-119">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d5a1-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1d5a1-120">Child Elements</span></span>  
 <span data-ttu-id="1d5a1-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="1d5a1-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d5a1-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1d5a1-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1d5a1-123">Element</span><span class="sxs-lookup"><span data-stu-id="1d5a1-123">Element</span></span>|<span data-ttu-id="1d5a1-124">Opis</span><span class="sxs-lookup"><span data-stu-id="1d5a1-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d5a1-125">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="1d5a1-125">\<identity></span></span>](identity.md)|<span data-ttu-id="1d5a1-126">Określa tożsamość usługi do uwierzytelnienia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="1d5a1-126">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d5a1-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1d5a1-127">Remarks</span></span>  
 <span data-ttu-id="1d5a1-128">Bezpieczny Windows Communication Foundation (WCF), który nawiązuje połączenie z punktem końcowym z tą tożsamością używa nazwy UPN podczas uwierzytelniania SSPI przy użyciu punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="1d5a1-128">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d5a1-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d5a1-129">Example</span></span>  
 <span data-ttu-id="1d5a1-130">Poniższy kod konfiguracji określa nazwę UPN usługi do uwierzytelnienia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="1d5a1-130">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="1d5a1-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d5a1-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="1d5a1-132">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="1d5a1-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="1d5a1-133">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="1d5a1-133">\<identity></span></span>](identity.md)
