---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 0e307069bd3a98153cc66147ba7bcf511cf13a8e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091658"
---
# <a name="rsa"></a><span data-ttu-id="762be-101">\<rsa></span><span class="sxs-lookup"><span data-stu-id="762be-101">\<rsa></span></span>
<span data-ttu-id="762be-102">Bezpieczny klient WCF łączący punkt końcowy o tej tożsamości weryfikuje czy wnioski przedstawione przez serwer zawierają roszczenia, który zawiera klucz publiczny RSA użyta do skonstruowania tej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="762be-102">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
 <span data-ttu-id="762be-103">\<identity></span><span class="sxs-lookup"><span data-stu-id="762be-103">\<identity></span></span>  
<span data-ttu-id="762be-104">\<rsa></span><span class="sxs-lookup"><span data-stu-id="762be-104">\<rsa></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="762be-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="762be-105">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="762be-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="762be-106">Attributes and Elements</span></span>  
 <span data-ttu-id="762be-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="762be-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="762be-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="762be-108">Attributes</span></span>  
  
|<span data-ttu-id="762be-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="762be-109">Attribute</span></span>|<span data-ttu-id="762be-110">Opis</span><span class="sxs-lookup"><span data-stu-id="762be-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="762be-111">value</span><span class="sxs-lookup"><span data-stu-id="762be-111">value</span></span>|<span data-ttu-id="762be-112">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="762be-112">Optional String.</span></span> <span data-ttu-id="762be-113">Wartość klucza publicznego RSA porównana z na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="762be-113">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="762be-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="762be-114">Child Elements</span></span>  
 <span data-ttu-id="762be-115">Brak</span><span class="sxs-lookup"><span data-stu-id="762be-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="762be-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="762be-116">Parent Elements</span></span>  
  
|<span data-ttu-id="762be-117">Element</span><span class="sxs-lookup"><span data-stu-id="762be-117">Element</span></span>|<span data-ttu-id="762be-118">Opis</span><span class="sxs-lookup"><span data-stu-id="762be-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="762be-119">\<identity></span><span class="sxs-lookup"><span data-stu-id="762be-119">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="762be-120">Określa tożsamość usługi, aby zostać uwierzytelnionym przez klienta.</span><span class="sxs-lookup"><span data-stu-id="762be-120">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="762be-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="762be-121">Remarks</span></span>  
 <span data-ttu-id="762be-122">Sprawdzanie RSA umożliwia takie ograniczenie uwierzytelniania do pojedynczego certyfikatu na podstawie jego klucza RSA lub wygenerowane swoją własną wartością klucza RSA.</span><span class="sxs-lookup"><span data-stu-id="762be-122">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="762be-123">Ten umożliwia bardziej rygorystyczne uwierzytelnianie określonego klucza RSA kosztem usługi nie jest już współpracuje z istniejącymi klientami, zmiana wartości klucza RSA.</span><span class="sxs-lookup"><span data-stu-id="762be-123">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="762be-124">Aby uzyskać więcej informacji o weryfikacji usługi do klienta za pomocą tożsamości, zobacz [uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="762be-124">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="762be-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="762be-125">Example</span></span>  
 <span data-ttu-id="762be-126">Poniższy kod konfiguracji określa wartość klucza publicznego certyfikatu X.509, który jest używany do uwierzytelniania serwera.</span><span class="sxs-lookup"><span data-stu-id="762be-126">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="762be-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="762be-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="762be-128">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="762be-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="762be-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="762be-129">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
