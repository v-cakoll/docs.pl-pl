---
title: <certificate> Aby uzyskać <identity>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: 1cfd207afc72cc71359d9d262e30b0696ba63d2b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850016"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="28fdf-102">\<> certyfikatu dla \<tożsamości ></span><span class="sxs-lookup"><span data-stu-id="28fdf-102">\<certificate> for \<identity></span></span>
<span data-ttu-id="28fdf-103">Określa certyfikat X. 509 używany do sprawdzania poprawności serwera dla klienta.</span><span class="sxs-lookup"><span data-stu-id="28fdf-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
<span data-ttu-id="28fdf-104">Aby uzyskać więcej informacji na temat ustawiania wartości elementu, zobacz [tożsamość usługi i uwierzytelnianie](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="28fdf-104">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="28fdf-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="28fdf-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="28fdf-106">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="28fdf-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="28fdf-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)</span><span class="sxs-lookup"><span data-stu-id="28fdf-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="28fdf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> punktu końcowego**](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="28fdf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="28fdf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> tożsamości**](identity.md)</span><span class="sxs-lookup"><span data-stu-id="28fdf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="28fdf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> certyfikatów**</span><span class="sxs-lookup"><span data-stu-id="28fdf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28fdf-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="28fdf-111">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28fdf-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="28fdf-112">Attributes and Elements</span></span>  
 <span data-ttu-id="28fdf-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="28fdf-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28fdf-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="28fdf-114">Attributes</span></span>  
  
|<span data-ttu-id="28fdf-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="28fdf-115">Attribute</span></span>|<span data-ttu-id="28fdf-116">Opis</span><span class="sxs-lookup"><span data-stu-id="28fdf-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="28fdf-117">encodedValue</span><span class="sxs-lookup"><span data-stu-id="28fdf-117">encodedValue</span></span>|<span data-ttu-id="28fdf-118">Kodowanie Base64 certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="28fdf-118">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28fdf-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="28fdf-119">Child Elements</span></span>  
 <span data-ttu-id="28fdf-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="28fdf-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="28fdf-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="28fdf-121">Parent Elements</span></span>  
  
|<span data-ttu-id="28fdf-122">Element</span><span class="sxs-lookup"><span data-stu-id="28fdf-122">Element</span></span>|<span data-ttu-id="28fdf-123">Opis</span><span class="sxs-lookup"><span data-stu-id="28fdf-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28fdf-124">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="28fdf-124">\<identity></span></span>](identity.md)|<span data-ttu-id="28fdf-125">Określa tożsamość usługi do uwierzytelnienia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="28fdf-125">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="28fdf-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="28fdf-126">Example</span></span>  
 <span data-ttu-id="28fdf-127">Poniższy kod określa zakodowaną reprezentację certyfikatu służącego do sprawdzania poprawności serwera dla klienta.</span><span class="sxs-lookup"><span data-stu-id="28fdf-127">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="28fdf-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28fdf-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="28fdf-129">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="28fdf-129">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="28fdf-130">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="28fdf-130">\<identity></span></span>](identity.md)
