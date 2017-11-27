---
title: '&lt;RSA&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ab07508c4cab32cb2a60d37af368c345a0f12d88
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltrsagt"></a><span data-ttu-id="22bae-102">&lt;RSA&gt;</span><span class="sxs-lookup"><span data-stu-id="22bae-102">&lt;rsa&gt;</span></span>
<span data-ttu-id="22bae-103">Bezpieczny klient WCF łączący punkt końcowy o tej tożsamości weryfikuje czy wnioski przedstawione przez serwer zawierają roszczenia, zawierający klucza publicznego RSA użyty do skonstruowania tej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="22bae-103">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
 <span data-ttu-id="22bae-104">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="22bae-104">\<identity></span></span>  
<span data-ttu-id="22bae-105">\<RSA ></span><span class="sxs-lookup"><span data-stu-id="22bae-105">\<rsa></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22bae-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="22bae-106">Syntax</span></span>  
  
```xml  
<rsa value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22bae-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="22bae-107">Attributes and Elements</span></span>  
 <span data-ttu-id="22bae-108">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="22bae-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22bae-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="22bae-109">Attributes</span></span>  
  
|<span data-ttu-id="22bae-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="22bae-110">Attribute</span></span>|<span data-ttu-id="22bae-111">Opis</span><span class="sxs-lookup"><span data-stu-id="22bae-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="22bae-112">value</span><span class="sxs-lookup"><span data-stu-id="22bae-112">value</span></span>|<span data-ttu-id="22bae-113">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="22bae-113">Optional String.</span></span> <span data-ttu-id="22bae-114">Wartość klucza publicznego RSA ma zostać porównane z na kliencie.</span><span class="sxs-lookup"><span data-stu-id="22bae-114">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="22bae-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="22bae-115">Child Elements</span></span>  
 <span data-ttu-id="22bae-116">Brak</span><span class="sxs-lookup"><span data-stu-id="22bae-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="22bae-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="22bae-117">Parent Elements</span></span>  
  
|<span data-ttu-id="22bae-118">Element</span><span class="sxs-lookup"><span data-stu-id="22bae-118">Element</span></span>|<span data-ttu-id="22bae-119">Opis</span><span class="sxs-lookup"><span data-stu-id="22bae-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22bae-120">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="22bae-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="22bae-121">Określa tożsamość usługi uwierzytelniania przez klienta.</span><span class="sxs-lookup"><span data-stu-id="22bae-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22bae-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="22bae-122">Remarks</span></span>  
 <span data-ttu-id="22bae-123">Sprawdź RSA umożliwia w szczególności ograniczyć uwierzytelnianie oparte na jego klucza RSA jeden certyfikat lub wygenerować własną wartość klucza RSA.</span><span class="sxs-lookup"><span data-stu-id="22bae-123">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="22bae-124">Ten umożliwia bardziej restrykcyjne uwierzytelnianie określonego klucza RSA kosztem usługi nie jest już współpracuje z istniejącymi klientami zmiana wartości klucza RSA.</span><span class="sxs-lookup"><span data-stu-id="22bae-124">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="22bae-125">Aby uzyskać więcej informacji o używaniu tożsamości można sprawdzić poprawności usługi do klienta, zobacz [uwierzytelnianie i tożsamość usługi](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="22bae-125">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="22bae-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="22bae-126">Example</span></span>  
 <span data-ttu-id="22bae-127">Poniższy kod konfiguracji określa wartość klucza publicznego certyfikatu X.509, który jest używany do uwierzytelniania serwera.</span><span class="sxs-lookup"><span data-stu-id="22bae-127">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>  
  <rsa value = "0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000"/>  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="22bae-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22bae-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.RsaEndpointIdentity>  
 [<span data-ttu-id="22bae-129">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="22bae-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="22bae-130">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="22bae-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
