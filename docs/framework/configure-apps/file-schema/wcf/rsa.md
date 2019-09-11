---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 0e1651f563bdb2b2b24eacacf7bfe387e33a82c7
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855045"
---
# <a name="rsa"></a><span data-ttu-id="19518-101">\<> RSA</span><span class="sxs-lookup"><span data-stu-id="19518-101">\<rsa></span></span>
<span data-ttu-id="19518-102">Bezpieczny klient WCF, który nawiązuje połączenie z punktem końcowym z tą tożsamością, sprawdza, czy oświadczenia przedstawione przez serwer zawierają oświadczenie zawierające klucz publiczny RSA użyty do skonstruowania tej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="19518-102">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
<span data-ttu-id="19518-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="19518-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="19518-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="19518-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="19518-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)</span><span class="sxs-lookup"><span data-stu-id="19518-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="19518-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> punktu końcowego**](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="19518-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="19518-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> tożsamości**](identity.md)</span><span class="sxs-lookup"><span data-stu-id="19518-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="19518-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> RSA**</span><span class="sxs-lookup"><span data-stu-id="19518-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<rsa>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19518-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="19518-109">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19518-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="19518-110">Attributes and Elements</span></span>  
 <span data-ttu-id="19518-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="19518-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19518-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="19518-112">Attributes</span></span>  
  
|<span data-ttu-id="19518-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="19518-113">Attribute</span></span>|<span data-ttu-id="19518-114">Opis</span><span class="sxs-lookup"><span data-stu-id="19518-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="19518-115">value</span><span class="sxs-lookup"><span data-stu-id="19518-115">value</span></span>|<span data-ttu-id="19518-116">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="19518-116">Optional String.</span></span> <span data-ttu-id="19518-117">Wartość klucza publicznego RSA do porównania z klientem programu.</span><span class="sxs-lookup"><span data-stu-id="19518-117">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19518-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="19518-118">Child Elements</span></span>  
 <span data-ttu-id="19518-119">Brak</span><span class="sxs-lookup"><span data-stu-id="19518-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="19518-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="19518-120">Parent Elements</span></span>  
  
|<span data-ttu-id="19518-121">Element</span><span class="sxs-lookup"><span data-stu-id="19518-121">Element</span></span>|<span data-ttu-id="19518-122">Opis</span><span class="sxs-lookup"><span data-stu-id="19518-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="19518-123">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="19518-123">\<identity></span></span>](identity.md)|<span data-ttu-id="19518-124">Określa tożsamość usługi do uwierzytelnienia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="19518-124">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19518-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="19518-125">Remarks</span></span>  
 <span data-ttu-id="19518-126">Sprawdzanie RSA umożliwia ograniczenie uwierzytelniania do pojedynczego certyfikatu na podstawie jego klucza RSA lub wygenerowanie własnej wartości klucza RSA.</span><span class="sxs-lookup"><span data-stu-id="19518-126">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="19518-127">Pozwala to na bardziej rygorystyczne uwierzytelnianie określonego klucza RSA kosztem usługi nie działa już z istniejącymi klientami, jeśli wartość klucza RSA zostanie zmieniona.</span><span class="sxs-lookup"><span data-stu-id="19518-127">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="19518-128">Aby uzyskać więcej informacji o używaniu tożsamości do sprawdzania poprawności usługi dla klienta, zobacz [tożsamość usługi i uwierzytelnianie](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="19518-128">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="19518-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="19518-129">Example</span></span>  
 <span data-ttu-id="19518-130">Poniższy kod konfiguracji określa wartość klucza publicznego certyfikatu X. 509, który jest używany do uwierzytelniania serwera.</span><span class="sxs-lookup"><span data-stu-id="19518-130">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="19518-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19518-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="19518-132">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="19518-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="19518-133">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="19518-133">\<identity></span></span>](identity.md)
