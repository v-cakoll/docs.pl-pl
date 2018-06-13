---
title: '&lt;RSA&gt;'
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: dbeb08e6475d4825ad442b0b264e9003bb6fc53d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749933"
---
# <a name="ltrsagt"></a><span data-ttu-id="dd788-102">&lt;RSA&gt;</span><span class="sxs-lookup"><span data-stu-id="dd788-102">&lt;rsa&gt;</span></span>
<span data-ttu-id="dd788-103">Bezpieczny klient WCF łączący punkt końcowy o tej tożsamości weryfikuje czy wnioski przedstawione przez serwer zawierają roszczenia, zawierający klucza publicznego RSA użyty do skonstruowania tej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="dd788-103">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
 <span data-ttu-id="dd788-104">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="dd788-104">\<identity></span></span>  
<span data-ttu-id="dd788-105">\<RSA ></span><span class="sxs-lookup"><span data-stu-id="dd788-105">\<rsa></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd788-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="dd788-106">Syntax</span></span>  
  
```xml  
<rsa value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd788-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="dd788-107">Attributes and Elements</span></span>  
 <span data-ttu-id="dd788-108">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="dd788-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd788-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="dd788-109">Attributes</span></span>  
  
|<span data-ttu-id="dd788-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="dd788-110">Attribute</span></span>|<span data-ttu-id="dd788-111">Opis</span><span class="sxs-lookup"><span data-stu-id="dd788-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dd788-112">value</span><span class="sxs-lookup"><span data-stu-id="dd788-112">value</span></span>|<span data-ttu-id="dd788-113">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="dd788-113">Optional String.</span></span> <span data-ttu-id="dd788-114">Wartość klucza publicznego RSA ma zostać porównane z na kliencie.</span><span class="sxs-lookup"><span data-stu-id="dd788-114">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd788-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="dd788-115">Child Elements</span></span>  
 <span data-ttu-id="dd788-116">Brak</span><span class="sxs-lookup"><span data-stu-id="dd788-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dd788-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="dd788-117">Parent Elements</span></span>  
  
|<span data-ttu-id="dd788-118">Element</span><span class="sxs-lookup"><span data-stu-id="dd788-118">Element</span></span>|<span data-ttu-id="dd788-119">Opis</span><span class="sxs-lookup"><span data-stu-id="dd788-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd788-120">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="dd788-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="dd788-121">Określa tożsamość usługi uwierzytelniania przez klienta.</span><span class="sxs-lookup"><span data-stu-id="dd788-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd788-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dd788-122">Remarks</span></span>  
 <span data-ttu-id="dd788-123">Sprawdź RSA umożliwia w szczególności ograniczyć uwierzytelnianie oparte na jego klucza RSA jeden certyfikat lub wygenerować własną wartość klucza RSA.</span><span class="sxs-lookup"><span data-stu-id="dd788-123">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="dd788-124">Ten umożliwia bardziej restrykcyjne uwierzytelnianie określonego klucza RSA kosztem usługi nie jest już współpracuje z istniejącymi klientami zmiana wartości klucza RSA.</span><span class="sxs-lookup"><span data-stu-id="dd788-124">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="dd788-125">Aby uzyskać więcej informacji o używaniu tożsamości można sprawdzić poprawności usługi do klienta, zobacz [uwierzytelnianie i tożsamość usługi](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="dd788-125">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd788-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="dd788-126">Example</span></span>  
 <span data-ttu-id="dd788-127">Poniższy kod konfiguracji określa wartość klucza publicznego certyfikatu X.509, który jest używany do uwierzytelniania serwera.</span><span class="sxs-lookup"><span data-stu-id="dd788-127">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>  
  <rsa value = "0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000"/>  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd788-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd788-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.RsaEndpointIdentity>  
 [<span data-ttu-id="dd788-129">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="dd788-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="dd788-130">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="dd788-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
