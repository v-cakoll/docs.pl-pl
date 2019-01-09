---
title: '&lt;XmlElement&gt;'
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 6a197f7aa29645a08a581bcee103eb94c0e20179
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147021"
---
# <a name="ltxmlelementgt"></a><span data-ttu-id="b6f05-102">&lt;XmlElement&gt;</span><span class="sxs-lookup"><span data-stu-id="b6f05-102">&lt;xmlElement&gt;</span></span>
<span data-ttu-id="b6f05-103">Określa element XML, który będzie wysyłany w treści komunikatu do usługi tokenu zabezpieczeń, podczas żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="b6f05-103">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
 <span data-ttu-id="b6f05-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b6f05-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b6f05-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="b6f05-105">\<bindings></span></span>  
<span data-ttu-id="b6f05-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="b6f05-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="b6f05-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="b6f05-107">\<binding></span></span>  
<span data-ttu-id="b6f05-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="b6f05-108">\<security></span></span>  
<span data-ttu-id="b6f05-109">\<message></span><span class="sxs-lookup"><span data-stu-id="b6f05-109">\<message></span></span>  
<span data-ttu-id="b6f05-110">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="b6f05-110">\<tokenRequestParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6f05-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6f05-111">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6f05-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b6f05-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b6f05-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b6f05-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6f05-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b6f05-114">Attributes</span></span>  
  
|<span data-ttu-id="b6f05-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b6f05-115">Attribute</span></span>|<span data-ttu-id="b6f05-116">Opis</span><span class="sxs-lookup"><span data-stu-id="b6f05-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b6f05-117">xmlElement</span><span class="sxs-lookup"><span data-stu-id="b6f05-117">xmlElement</span></span>|<span data-ttu-id="b6f05-118">Ciąg określający element XML, który będzie wysyłany w treści komunikatu do usługi tokenu zabezpieczeń, podczas żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="b6f05-118">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6f05-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b6f05-119">Child Elements</span></span>  
 <span data-ttu-id="b6f05-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="b6f05-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b6f05-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b6f05-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b6f05-122">Element</span><span class="sxs-lookup"><span data-stu-id="b6f05-122">Element</span></span>|<span data-ttu-id="b6f05-123">Opis</span><span class="sxs-lookup"><span data-stu-id="b6f05-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6f05-124">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="b6f05-124">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="b6f05-125">Kolekcja parametrów żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="b6f05-125">A collection of token request parameters.</span></span> <span data-ttu-id="b6f05-126">Każdy parametr jest elementem XML.</span><span class="sxs-lookup"><span data-stu-id="b6f05-126">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b6f05-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6f05-127">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>  
 [<span data-ttu-id="b6f05-128">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="b6f05-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="b6f05-129">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="b6f05-129">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="b6f05-130">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="b6f05-130">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="b6f05-131">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="b6f05-131">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="b6f05-132">Powiązania</span><span class="sxs-lookup"><span data-stu-id="b6f05-132">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
