---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: dd8e5ab11a7c019a8fe967f1c14b88a922a16c33
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934735"
---
# <a name="rsa"></a><span data-ttu-id="b84dc-101">\<> RSA</span><span class="sxs-lookup"><span data-stu-id="b84dc-101">\<rsa></span></span>
<span data-ttu-id="b84dc-102">Bezpieczny klient WCF, który nawiązuje połączenie z punktem końcowym z tą tożsamością, sprawdza, czy oświadczenia przedstawione przez serwer zawierają oświadczenie zawierające klucz publiczny RSA użyty do skonstruowania tej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="b84dc-102">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
 <span data-ttu-id="b84dc-103">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="b84dc-103">\<identity></span></span>  
<span data-ttu-id="b84dc-104">\<> RSA</span><span class="sxs-lookup"><span data-stu-id="b84dc-104">\<rsa></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b84dc-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b84dc-105">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b84dc-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b84dc-106">Attributes and Elements</span></span>  
 <span data-ttu-id="b84dc-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b84dc-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b84dc-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b84dc-108">Attributes</span></span>  
  
|<span data-ttu-id="b84dc-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b84dc-109">Attribute</span></span>|<span data-ttu-id="b84dc-110">Opis</span><span class="sxs-lookup"><span data-stu-id="b84dc-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b84dc-111">value</span><span class="sxs-lookup"><span data-stu-id="b84dc-111">value</span></span>|<span data-ttu-id="b84dc-112">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="b84dc-112">Optional String.</span></span> <span data-ttu-id="b84dc-113">Wartość klucza publicznego RSA do porównania z klientem programu.</span><span class="sxs-lookup"><span data-stu-id="b84dc-113">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b84dc-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b84dc-114">Child Elements</span></span>  
 <span data-ttu-id="b84dc-115">Brak</span><span class="sxs-lookup"><span data-stu-id="b84dc-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b84dc-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b84dc-116">Parent Elements</span></span>  
  
|<span data-ttu-id="b84dc-117">Element</span><span class="sxs-lookup"><span data-stu-id="b84dc-117">Element</span></span>|<span data-ttu-id="b84dc-118">Opis</span><span class="sxs-lookup"><span data-stu-id="b84dc-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b84dc-119">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="b84dc-119">\<identity></span></span>](identity.md)|<span data-ttu-id="b84dc-120">Określa tożsamość usługi do uwierzytelnienia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="b84dc-120">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b84dc-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b84dc-121">Remarks</span></span>  
 <span data-ttu-id="b84dc-122">Sprawdzanie RSA umożliwia ograniczenie uwierzytelniania do pojedynczego certyfikatu na podstawie jego klucza RSA lub wygenerowanie własnej wartości klucza RSA.</span><span class="sxs-lookup"><span data-stu-id="b84dc-122">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="b84dc-123">Pozwala to na bardziej rygorystyczne uwierzytelnianie określonego klucza RSA kosztem usługi nie działa już z istniejącymi klientami, jeśli wartość klucza RSA zostanie zmieniona.</span><span class="sxs-lookup"><span data-stu-id="b84dc-123">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="b84dc-124">Aby uzyskać więcej informacji o używaniu tożsamości do sprawdzania poprawności usługi dla klienta, zobacz [tożsamość usługi i uwierzytelnianie](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b84dc-124">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b84dc-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="b84dc-125">Example</span></span>  
 <span data-ttu-id="b84dc-126">Poniższy kod konfiguracji określa wartość klucza publicznego certyfikatu X. 509, który jest używany do uwierzytelniania serwera.</span><span class="sxs-lookup"><span data-stu-id="b84dc-126">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="b84dc-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b84dc-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="b84dc-128">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="b84dc-128">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="b84dc-129">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="b84dc-129">\<identity></span></span>](identity.md)
