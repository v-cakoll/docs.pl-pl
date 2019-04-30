---
title: <certificate> Aby uzyskać <identity>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: 76bdcb40d5016d7fcbff6c0d9769819f710065fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673360"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="fd7cd-102">\<certyfikat > dla \<identity ></span><span class="sxs-lookup"><span data-stu-id="fd7cd-102">\<certificate> for \<identity></span></span>
<span data-ttu-id="fd7cd-103">Określa certyfikat X.509 używany do walidacji serwera do klienta.</span><span class="sxs-lookup"><span data-stu-id="fd7cd-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
 <span data-ttu-id="fd7cd-104">Aby uzyskać więcej informacji na temat ustawienia wartości elementu, zobacz [uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fd7cd-104">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="fd7cd-105">\<identity></span><span class="sxs-lookup"><span data-stu-id="fd7cd-105">\<identity></span></span>  
<span data-ttu-id="fd7cd-106">\<certificate></span><span class="sxs-lookup"><span data-stu-id="fd7cd-106">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd7cd-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd7cd-107">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd7cd-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fd7cd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fd7cd-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fd7cd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd7cd-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fd7cd-110">Attributes</span></span>  
  
|<span data-ttu-id="fd7cd-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fd7cd-111">Attribute</span></span>|<span data-ttu-id="fd7cd-112">Opis</span><span class="sxs-lookup"><span data-stu-id="fd7cd-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fd7cd-113">encodedValue</span><span class="sxs-lookup"><span data-stu-id="fd7cd-113">encodedValue</span></span>|<span data-ttu-id="fd7cd-114">Kodowanie Base64 certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="fd7cd-114">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd7cd-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fd7cd-115">Child Elements</span></span>  
 <span data-ttu-id="fd7cd-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="fd7cd-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd7cd-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fd7cd-117">Parent Elements</span></span>  
  
|<span data-ttu-id="fd7cd-118">Element</span><span class="sxs-lookup"><span data-stu-id="fd7cd-118">Element</span></span>|<span data-ttu-id="fd7cd-119">Opis</span><span class="sxs-lookup"><span data-stu-id="fd7cd-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd7cd-120">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="fd7cd-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="fd7cd-121">Określa tożsamość usługi, aby zostać uwierzytelnionym przez klienta.</span><span class="sxs-lookup"><span data-stu-id="fd7cd-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fd7cd-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="fd7cd-122">Example</span></span>  
 <span data-ttu-id="fd7cd-123">Poniższy kod określa reprezentację zakodowany certyfikat używany do walidacji serwera do klienta.</span><span class="sxs-lookup"><span data-stu-id="fd7cd-123">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="fd7cd-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fd7cd-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="fd7cd-125">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="fd7cd-125">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="fd7cd-126">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="fd7cd-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
