---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 0e1651f563bdb2b2b24eacacf7bfe387e33a82c7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855045"
---
# \<rsa>
<span data-ttu-id="c5379-101">Bezpieczny klient WCF, który nawiązuje połączenie z punktem końcowym z tą tożsamością, sprawdza, czy oświadczenia przedstawione przez serwer zawierają oświadczenie zawierające klucz publiczny RSA użyty do skonstruowania tej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="c5379-101">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<rsa>**  
  
## <a name="syntax"></a><span data-ttu-id="c5379-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5379-102">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5379-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c5379-103">Attributes and Elements</span></span>  
 <span data-ttu-id="c5379-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c5379-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5379-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c5379-105">Attributes</span></span>  
  
|<span data-ttu-id="c5379-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c5379-106">Attribute</span></span>|<span data-ttu-id="c5379-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c5379-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c5379-108">value</span><span class="sxs-lookup"><span data-stu-id="c5379-108">value</span></span>|<span data-ttu-id="c5379-109">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="c5379-109">Optional String.</span></span> <span data-ttu-id="c5379-110">Wartość klucza publicznego RSA do porównania z klientem programu.</span><span class="sxs-lookup"><span data-stu-id="c5379-110">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5379-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c5379-111">Child Elements</span></span>  
 <span data-ttu-id="c5379-112">Brak</span><span class="sxs-lookup"><span data-stu-id="c5379-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5379-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c5379-113">Parent Elements</span></span>  
  
|<span data-ttu-id="c5379-114">Element</span><span class="sxs-lookup"><span data-stu-id="c5379-114">Element</span></span>|<span data-ttu-id="c5379-115">Opis</span><span class="sxs-lookup"><span data-stu-id="c5379-115">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="c5379-116">Określa tożsamość usługi do uwierzytelnienia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="c5379-116">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5379-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c5379-117">Remarks</span></span>  
 <span data-ttu-id="c5379-118">Sprawdzanie RSA umożliwia ograniczenie uwierzytelniania do pojedynczego certyfikatu na podstawie jego klucza RSA lub wygenerowanie własnej wartości klucza RSA.</span><span class="sxs-lookup"><span data-stu-id="c5379-118">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="c5379-119">Pozwala to na bardziej rygorystyczne uwierzytelnianie określonego klucza RSA kosztem usługi nie działa już z istniejącymi klientami, jeśli wartość klucza RSA zostanie zmieniona.</span><span class="sxs-lookup"><span data-stu-id="c5379-119">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="c5379-120">Aby uzyskać więcej informacji o używaniu tożsamości do sprawdzania poprawności usługi dla klienta, zobacz [tożsamość usługi i uwierzytelnianie](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c5379-120">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5379-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="c5379-121">Example</span></span>  
 <span data-ttu-id="c5379-122">Poniższy kod konfiguracji określa wartość klucza publicznego certyfikatu X. 509, który jest używany do uwierzytelniania serwera.</span><span class="sxs-lookup"><span data-stu-id="c5379-122">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="c5379-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5379-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="c5379-124">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="c5379-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
