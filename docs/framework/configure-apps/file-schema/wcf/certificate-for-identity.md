---
title: <certificate>dla<identity>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: 1cfd207afc72cc71359d9d262e30b0696ba63d2b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850016"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="36aa8-102">\<certificate>dla\<identity></span><span class="sxs-lookup"><span data-stu-id="36aa8-102">\<certificate> for \<identity></span></span>
<span data-ttu-id="36aa8-103">Określa certyfikat X. 509 używany do sprawdzania poprawności serwera dla klienta.</span><span class="sxs-lookup"><span data-stu-id="36aa8-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
<span data-ttu-id="36aa8-104">Aby uzyskać więcej informacji na temat ustawiania wartości elementu, zobacz [tożsamość usługi i uwierzytelnianie](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="36aa8-104">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="36aa8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="36aa8-105">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36aa8-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="36aa8-106">Attributes and Elements</span></span>  
 <span data-ttu-id="36aa8-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="36aa8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36aa8-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="36aa8-108">Attributes</span></span>  
  
|<span data-ttu-id="36aa8-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="36aa8-109">Attribute</span></span>|<span data-ttu-id="36aa8-110">Opis</span><span class="sxs-lookup"><span data-stu-id="36aa8-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="36aa8-111">encodedValue</span><span class="sxs-lookup"><span data-stu-id="36aa8-111">encodedValue</span></span>|<span data-ttu-id="36aa8-112">Kodowanie Base64 certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="36aa8-112">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="36aa8-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="36aa8-113">Child Elements</span></span>  
 <span data-ttu-id="36aa8-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="36aa8-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="36aa8-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="36aa8-115">Parent Elements</span></span>  
  
|<span data-ttu-id="36aa8-116">Element</span><span class="sxs-lookup"><span data-stu-id="36aa8-116">Element</span></span>|<span data-ttu-id="36aa8-117">Opis</span><span class="sxs-lookup"><span data-stu-id="36aa8-117">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="36aa8-118">Określa tożsamość usługi do uwierzytelnienia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="36aa8-118">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="36aa8-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="36aa8-119">Example</span></span>  
 <span data-ttu-id="36aa8-120">Poniższy kod określa zakodowaną reprezentację certyfikatu służącego do sprawdzania poprawności serwera dla klienta.</span><span class="sxs-lookup"><span data-stu-id="36aa8-120">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="36aa8-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="36aa8-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="36aa8-122">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="36aa8-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
