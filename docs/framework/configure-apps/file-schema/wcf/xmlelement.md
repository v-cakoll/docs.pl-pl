---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: a72641b438801cfd493c322297e7c384e83e687c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230502"
---
# <a name="xmlelement"></a><span data-ttu-id="5fbd4-101">\<xmlElement></span><span class="sxs-lookup"><span data-stu-id="5fbd4-101">\<xmlElement></span></span>
<span data-ttu-id="5fbd4-102">Określa element XML, który będzie wysyłany w treści komunikatu do usługi tokenu zabezpieczeń, podczas żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="5fbd4-102">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
 <span data-ttu-id="5fbd4-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5fbd4-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="5fbd4-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="5fbd4-104">\<bindings></span></span>  
<span data-ttu-id="5fbd4-105">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="5fbd4-105">\<wsFederatedBinding></span></span>  
<span data-ttu-id="5fbd4-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="5fbd4-106">\<binding></span></span>  
<span data-ttu-id="5fbd4-107">\<security></span><span class="sxs-lookup"><span data-stu-id="5fbd4-107">\<security></span></span>  
<span data-ttu-id="5fbd4-108">\<message></span><span class="sxs-lookup"><span data-stu-id="5fbd4-108">\<message></span></span>  
<span data-ttu-id="5fbd4-109">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="5fbd4-109">\<tokenRequestParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fbd4-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="5fbd4-110">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5fbd4-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5fbd4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5fbd4-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5fbd4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5fbd4-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5fbd4-113">Attributes</span></span>  
  
|<span data-ttu-id="5fbd4-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5fbd4-114">Attribute</span></span>|<span data-ttu-id="5fbd4-115">Opis</span><span class="sxs-lookup"><span data-stu-id="5fbd4-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5fbd4-116">xmlElement</span><span class="sxs-lookup"><span data-stu-id="5fbd4-116">xmlElement</span></span>|<span data-ttu-id="5fbd4-117">Ciąg określający element XML, który będzie wysyłany w treści komunikatu do usługi tokenu zabezpieczeń, podczas żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="5fbd4-117">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5fbd4-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5fbd4-118">Child Elements</span></span>  
 <span data-ttu-id="5fbd4-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="5fbd4-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5fbd4-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5fbd4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="5fbd4-121">Element</span><span class="sxs-lookup"><span data-stu-id="5fbd4-121">Element</span></span>|<span data-ttu-id="5fbd4-122">Opis</span><span class="sxs-lookup"><span data-stu-id="5fbd4-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5fbd4-123">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="5fbd4-123">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="5fbd4-124">Kolekcja parametrów żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="5fbd4-124">A collection of token request parameters.</span></span> <span data-ttu-id="5fbd4-125">Każdy parametr jest elementem XML.</span><span class="sxs-lookup"><span data-stu-id="5fbd4-125">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5fbd4-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5fbd4-126">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="5fbd4-127">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="5fbd4-127">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="5fbd4-128">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="5fbd4-128">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="5fbd4-129">Możliwości zabezpieczeń wiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="5fbd4-129">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="5fbd4-130">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="5fbd4-130">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="5fbd4-131">Powiązania</span><span class="sxs-lookup"><span data-stu-id="5fbd4-131">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
