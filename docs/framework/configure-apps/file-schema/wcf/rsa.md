---
title: '&lt;RSA&gt;'
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 8005fd67b92cb14d82b525e7c990f9d58aef7b58
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145344"
---
# <a name="ltrsagt"></a><span data-ttu-id="c83e3-102">&lt;RSA&gt;</span><span class="sxs-lookup"><span data-stu-id="c83e3-102">&lt;rsa&gt;</span></span>
<span data-ttu-id="c83e3-103">Bezpieczny klient WCF łączący punkt końcowy o tej tożsamości weryfikuje czy wnioski przedstawione przez serwer zawierają roszczenia, który zawiera klucz publiczny RSA użyta do skonstruowania tej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="c83e3-103">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
 <span data-ttu-id="c83e3-104">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="c83e3-104">\<identity></span></span>  
<span data-ttu-id="c83e3-105">\<RSA ></span><span class="sxs-lookup"><span data-stu-id="c83e3-105">\<rsa></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c83e3-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c83e3-106">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c83e3-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c83e3-107">Attributes and Elements</span></span>  
 <span data-ttu-id="c83e3-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c83e3-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c83e3-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c83e3-109">Attributes</span></span>  
  
|<span data-ttu-id="c83e3-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c83e3-110">Attribute</span></span>|<span data-ttu-id="c83e3-111">Opis</span><span class="sxs-lookup"><span data-stu-id="c83e3-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c83e3-112">value</span><span class="sxs-lookup"><span data-stu-id="c83e3-112">value</span></span>|<span data-ttu-id="c83e3-113">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="c83e3-113">Optional String.</span></span> <span data-ttu-id="c83e3-114">Wartość klucza publicznego RSA porównana z na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="c83e3-114">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c83e3-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c83e3-115">Child Elements</span></span>  
 <span data-ttu-id="c83e3-116">Brak</span><span class="sxs-lookup"><span data-stu-id="c83e3-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c83e3-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c83e3-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c83e3-118">Element</span><span class="sxs-lookup"><span data-stu-id="c83e3-118">Element</span></span>|<span data-ttu-id="c83e3-119">Opis</span><span class="sxs-lookup"><span data-stu-id="c83e3-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c83e3-120">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="c83e3-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="c83e3-121">Określa tożsamość usługi, aby zostać uwierzytelnionym przez klienta.</span><span class="sxs-lookup"><span data-stu-id="c83e3-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c83e3-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c83e3-122">Remarks</span></span>  
 <span data-ttu-id="c83e3-123">Sprawdzanie RSA umożliwia takie ograniczenie uwierzytelniania do pojedynczego certyfikatu na podstawie jego klucza RSA lub wygenerowane swoją własną wartością klucza RSA.</span><span class="sxs-lookup"><span data-stu-id="c83e3-123">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="c83e3-124">Ten umożliwia bardziej rygorystyczne uwierzytelnianie określonego klucza RSA kosztem usługi nie jest już współpracuje z istniejącymi klientami, zmiana wartości klucza RSA.</span><span class="sxs-lookup"><span data-stu-id="c83e3-124">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="c83e3-125">Aby uzyskać więcej informacji o weryfikacji usługi do klienta za pomocą tożsamości, zobacz [uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c83e3-125">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c83e3-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="c83e3-126">Example</span></span>  
 <span data-ttu-id="c83e3-127">Poniższy kod konfiguracji określa wartość klucza publicznego certyfikatu X.509, który jest używany do uwierzytelniania serwera.</span><span class="sxs-lookup"><span data-stu-id="c83e3-127">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="c83e3-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c83e3-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.RsaEndpointIdentity>  
 [<span data-ttu-id="c83e3-129">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="c83e3-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="c83e3-130">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="c83e3-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
