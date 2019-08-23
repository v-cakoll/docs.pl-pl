---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 423a3249a9298675517f0cff08566c3735fa35f1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940511"
---
# <a name="userprincipalname"></a><span data-ttu-id="2a5ca-101">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="2a5ca-101">\<userPrincipalName></span></span>
<span data-ttu-id="2a5ca-102">Określa główną nazwę użytkownika (UPN) usługi do uwierzytelnienia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="2a5ca-102">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="2a5ca-103">Aby uzyskać więcej informacji na temat ustawiania nazwy UPN, zobacz [tożsamość usługi i uwierzytelnianie](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2a5ca-103">For more information about setting the UPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="2a5ca-104">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="2a5ca-104">\<identity></span></span>  
<span data-ttu-id="2a5ca-105">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="2a5ca-105">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a5ca-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a5ca-106">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a5ca-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2a5ca-107">Attributes and Elements</span></span>  
 <span data-ttu-id="2a5ca-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2a5ca-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a5ca-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2a5ca-109">Attributes</span></span>  
  
|<span data-ttu-id="2a5ca-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2a5ca-110">Attribute</span></span>|<span data-ttu-id="2a5ca-111">Opis</span><span class="sxs-lookup"><span data-stu-id="2a5ca-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2a5ca-112">value</span><span class="sxs-lookup"><span data-stu-id="2a5ca-112">value</span></span>|<span data-ttu-id="2a5ca-113">Nazwa konta użytkownika (czasem określana jako nazwa logowania użytkownika) i nazwa domeny identyfikującej domenę, w której znajduje się konto użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2a5ca-113">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="2a5ca-114">Jest to standardowe użycie logowania do domeny systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2a5ca-114">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="2a5ca-115">Format to: someone@example.com (jak w przypadku adresu e-mail).</span><span class="sxs-lookup"><span data-stu-id="2a5ca-115">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a5ca-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2a5ca-116">Child Elements</span></span>  
 <span data-ttu-id="2a5ca-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="2a5ca-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a5ca-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2a5ca-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2a5ca-119">Element</span><span class="sxs-lookup"><span data-stu-id="2a5ca-119">Element</span></span>|<span data-ttu-id="2a5ca-120">Opis</span><span class="sxs-lookup"><span data-stu-id="2a5ca-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a5ca-121">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="2a5ca-121">\<identity></span></span>](identity.md)|<span data-ttu-id="2a5ca-122">Określa tożsamość usługi do uwierzytelnienia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="2a5ca-122">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a5ca-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2a5ca-123">Remarks</span></span>  
 <span data-ttu-id="2a5ca-124">Bezpieczny Windows Communication Foundation (WCF), który nawiązuje połączenie z punktem końcowym z tą tożsamością używa nazwy UPN podczas uwierzytelniania SSPI przy użyciu punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="2a5ca-124">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a5ca-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a5ca-125">Example</span></span>  
 <span data-ttu-id="2a5ca-126">Poniższy kod konfiguracji określa nazwę UPN usługi do uwierzytelnienia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="2a5ca-126">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="2a5ca-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a5ca-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="2a5ca-128">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="2a5ca-128">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="2a5ca-129">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="2a5ca-129">\<identity></span></span>](identity.md)
