---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 9e7b845d39495dba1d1a19af95faf308b8b8c0fa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769814"
---
# <a name="userprincipalname"></a><span data-ttu-id="29ea6-101">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="29ea6-101">\<userPrincipalName></span></span>
<span data-ttu-id="29ea6-102">Określa główną nazwę użytkownika (UPN) usługi uwierzytelniania przez klienta.</span><span class="sxs-lookup"><span data-stu-id="29ea6-102">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="29ea6-103">Aby uzyskać więcej informacji na temat ustawiania nazwy UPN, zobacz [uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="29ea6-103">For more information about setting the UPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="29ea6-104">\<identity></span><span class="sxs-lookup"><span data-stu-id="29ea6-104">\<identity></span></span>  
<span data-ttu-id="29ea6-105">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="29ea6-105">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29ea6-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="29ea6-106">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29ea6-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="29ea6-107">Attributes and Elements</span></span>  
 <span data-ttu-id="29ea6-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="29ea6-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29ea6-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="29ea6-109">Attributes</span></span>  
  
|<span data-ttu-id="29ea6-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="29ea6-110">Attribute</span></span>|<span data-ttu-id="29ea6-111">Opis</span><span class="sxs-lookup"><span data-stu-id="29ea6-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="29ea6-112">value</span><span class="sxs-lookup"><span data-stu-id="29ea6-112">value</span></span>|<span data-ttu-id="29ea6-113">Nazwa konta użytkownika (czasami określane jako nazwa loginu użytkownika) i nazwa domeny identyfikującej domenę, w którym znajduje się konto użytkownika.</span><span class="sxs-lookup"><span data-stu-id="29ea6-113">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="29ea6-114">Jest to standardowy używana do logowania do domeny Windows.</span><span class="sxs-lookup"><span data-stu-id="29ea6-114">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="29ea6-115">Format to: someone@example.com (podobnie jak adres e-mail).</span><span class="sxs-lookup"><span data-stu-id="29ea6-115">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29ea6-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="29ea6-116">Child Elements</span></span>  
 <span data-ttu-id="29ea6-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="29ea6-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="29ea6-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="29ea6-118">Parent Elements</span></span>  
  
|<span data-ttu-id="29ea6-119">Element</span><span class="sxs-lookup"><span data-stu-id="29ea6-119">Element</span></span>|<span data-ttu-id="29ea6-120">Opis</span><span class="sxs-lookup"><span data-stu-id="29ea6-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29ea6-121">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="29ea6-121">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="29ea6-122">Określa tożsamość usługi, aby zostać uwierzytelnionym przez klienta.</span><span class="sxs-lookup"><span data-stu-id="29ea6-122">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29ea6-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="29ea6-123">Remarks</span></span>  
 <span data-ttu-id="29ea6-124">Bezpieczne klienta Windows Communication Foundation (WCF), który nawiązuje połączenie z punktem końcowym o tej tożsamości używa nazwy UPN, podczas przeprowadzania uwierzytelniania SSPI z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="29ea6-124">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29ea6-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="29ea6-125">Example</span></span>  
 <span data-ttu-id="29ea6-126">Poniższy kod konfiguracji określa nazwy UPN usługi, aby zostać uwierzytelnionym przez klienta.</span><span class="sxs-lookup"><span data-stu-id="29ea6-126">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="29ea6-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="29ea6-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="29ea6-128">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="29ea6-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="29ea6-129">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="29ea6-129">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
