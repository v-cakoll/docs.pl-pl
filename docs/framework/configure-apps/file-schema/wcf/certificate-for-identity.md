---
title: '&lt;certificate&gt; w &lt;identity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a9eabd25712136ef98f452cc15470bce1893527e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltcertificategt-for-ltidentitygt"></a><span data-ttu-id="44325-102">&lt;certificate&gt; w &lt;identity&gt;</span><span class="sxs-lookup"><span data-stu-id="44325-102">&lt;certificate&gt; for &lt;identity&gt;</span></span>
<span data-ttu-id="44325-103">Określa certyfikat X.509 używany do sprawdzania poprawności serwera do klienta.</span><span class="sxs-lookup"><span data-stu-id="44325-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
 <span data-ttu-id="44325-104">Aby uzyskać więcej informacji na temat ustawiania wartości elementu, zobacz [uwierzytelnianie i tożsamość usługi](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="44325-104">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="44325-105">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="44325-105">\<identity></span></span>  
<span data-ttu-id="44325-106">\<certyfikat ></span><span class="sxs-lookup"><span data-stu-id="44325-106">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44325-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="44325-107">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44325-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="44325-108">Attributes and Elements</span></span>  
 <span data-ttu-id="44325-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="44325-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44325-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="44325-110">Attributes</span></span>  
  
|<span data-ttu-id="44325-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="44325-111">Attribute</span></span>|<span data-ttu-id="44325-112">Opis</span><span class="sxs-lookup"><span data-stu-id="44325-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="44325-113">encodedValue</span><span class="sxs-lookup"><span data-stu-id="44325-113">encodedValue</span></span>|<span data-ttu-id="44325-114">Kodowanie Base64 certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="44325-114">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44325-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="44325-115">Child Elements</span></span>  
 <span data-ttu-id="44325-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="44325-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44325-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="44325-117">Parent Elements</span></span>  
  
|<span data-ttu-id="44325-118">Element</span><span class="sxs-lookup"><span data-stu-id="44325-118">Element</span></span>|<span data-ttu-id="44325-119">Opis</span><span class="sxs-lookup"><span data-stu-id="44325-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44325-120">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="44325-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="44325-121">Określa tożsamość usługi uwierzytelniania przez klienta.</span><span class="sxs-lookup"><span data-stu-id="44325-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="44325-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="44325-122">Example</span></span>  
 <span data-ttu-id="44325-123">Poniższy kod określa reprezentacja zakodowany certyfikat używany do walidacji serwera do klienta.</span><span class="sxs-lookup"><span data-stu-id="44325-123">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>  
  <certificate encodedValue = " MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="44325-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="44325-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.EndpointIdentity>  
 [<span data-ttu-id="44325-125">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="44325-125">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="44325-126">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="44325-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
