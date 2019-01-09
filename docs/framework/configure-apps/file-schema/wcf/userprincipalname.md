---
title: '&lt;userPrincipalName&gt;'
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: ff38a6975d1ec73c1a3014b94198ba630c3fec31
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149983"
---
# <a name="ltuserprincipalnamegt"></a><span data-ttu-id="3ab90-102">&lt;userPrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="3ab90-102">&lt;userPrincipalName&gt;</span></span>
<span data-ttu-id="3ab90-103">Określa główną nazwę użytkownika (UPN) usługi uwierzytelniania przez klienta.</span><span class="sxs-lookup"><span data-stu-id="3ab90-103">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="3ab90-104">Aby uzyskać więcej informacji na temat ustawiania nazwy UPN, zobacz [uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="3ab90-104">For more information about setting the UPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="3ab90-105">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="3ab90-105">\<identity></span></span>  
<span data-ttu-id="3ab90-106">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="3ab90-106">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ab90-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ab90-107">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ab90-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3ab90-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3ab90-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3ab90-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ab90-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3ab90-110">Attributes</span></span>  
  
|<span data-ttu-id="3ab90-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3ab90-111">Attribute</span></span>|<span data-ttu-id="3ab90-112">Opis</span><span class="sxs-lookup"><span data-stu-id="3ab90-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3ab90-113">value</span><span class="sxs-lookup"><span data-stu-id="3ab90-113">value</span></span>|<span data-ttu-id="3ab90-114">Nazwa konta użytkownika (czasami określane jako nazwa loginu użytkownika) i nazwa domeny identyfikującej domenę, w którym znajduje się konto użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3ab90-114">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="3ab90-115">Jest to standardowy używana do logowania do domeny Windows.</span><span class="sxs-lookup"><span data-stu-id="3ab90-115">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="3ab90-116">Format to: someone@example.com (podobnie jak adres e-mail).</span><span class="sxs-lookup"><span data-stu-id="3ab90-116">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ab90-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3ab90-117">Child Elements</span></span>  
 <span data-ttu-id="3ab90-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="3ab90-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3ab90-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3ab90-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3ab90-120">Element</span><span class="sxs-lookup"><span data-stu-id="3ab90-120">Element</span></span>|<span data-ttu-id="3ab90-121">Opis</span><span class="sxs-lookup"><span data-stu-id="3ab90-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ab90-122">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="3ab90-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="3ab90-123">Określa tożsamość usługi, aby zostać uwierzytelnionym przez klienta.</span><span class="sxs-lookup"><span data-stu-id="3ab90-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ab90-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3ab90-124">Remarks</span></span>  
 <span data-ttu-id="3ab90-125">Bezpieczne klienta Windows Communication Foundation (WCF), który nawiązuje połączenie z punktem końcowym o tej tożsamości używa nazwy UPN, podczas przeprowadzania uwierzytelniania SSPI z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="3ab90-125">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ab90-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="3ab90-126">Example</span></span>  
 <span data-ttu-id="3ab90-127">Poniższy kod konfiguracji określa nazwy UPN usługi, aby zostać uwierzytelnionym przez klienta.</span><span class="sxs-lookup"><span data-stu-id="3ab90-127">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="3ab90-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ab90-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.UpnEndpointIdentity>  
 [<span data-ttu-id="3ab90-129">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="3ab90-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="3ab90-130">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="3ab90-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
