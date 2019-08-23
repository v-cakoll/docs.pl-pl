---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: cc178dcc3684ab338282acc369e0ab5c789c15e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941438"
---
# <a name="xmlelement"></a><span data-ttu-id="0d1cd-101">\<xmlElement></span><span class="sxs-lookup"><span data-stu-id="0d1cd-101">\<xmlElement></span></span>
<span data-ttu-id="0d1cd-102">Określa element XML, który jest wysyłany w treści wiadomości do usługi tokenu zabezpieczającego podczas żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="0d1cd-102">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
 <span data-ttu-id="0d1cd-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0d1cd-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="0d1cd-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="0d1cd-104">\<bindings></span></span>  
<span data-ttu-id="0d1cd-105">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="0d1cd-105">\<wsFederatedBinding></span></span>  
<span data-ttu-id="0d1cd-106">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="0d1cd-106">\<binding></span></span>  
<span data-ttu-id="0d1cd-107">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="0d1cd-107">\<security></span></span>  
<span data-ttu-id="0d1cd-108">\<message></span><span class="sxs-lookup"><span data-stu-id="0d1cd-108">\<message></span></span>  
<span data-ttu-id="0d1cd-109">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="0d1cd-109">\<tokenRequestParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d1cd-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="0d1cd-110">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d1cd-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0d1cd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0d1cd-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0d1cd-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d1cd-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0d1cd-113">Attributes</span></span>  
  
|<span data-ttu-id="0d1cd-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0d1cd-114">Attribute</span></span>|<span data-ttu-id="0d1cd-115">Opis</span><span class="sxs-lookup"><span data-stu-id="0d1cd-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0d1cd-116">xmlElement</span><span class="sxs-lookup"><span data-stu-id="0d1cd-116">xmlElement</span></span>|<span data-ttu-id="0d1cd-117">Ciąg określający element XML, który jest wysyłany w treści wiadomości do usługi tokenu zabezpieczającego podczas żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="0d1cd-117">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d1cd-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0d1cd-118">Child Elements</span></span>  
 <span data-ttu-id="0d1cd-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="0d1cd-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0d1cd-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0d1cd-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0d1cd-121">Element</span><span class="sxs-lookup"><span data-stu-id="0d1cd-121">Element</span></span>|<span data-ttu-id="0d1cd-122">Opis</span><span class="sxs-lookup"><span data-stu-id="0d1cd-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d1cd-123">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="0d1cd-123">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="0d1cd-124">Kolekcja parametrów żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="0d1cd-124">A collection of token request parameters.</span></span> <span data-ttu-id="0d1cd-125">Każdy parametr jest elementem XML.</span><span class="sxs-lookup"><span data-stu-id="0d1cd-125">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0d1cd-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d1cd-126">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="0d1cd-127">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="0d1cd-127">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="0d1cd-128">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="0d1cd-128">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="0d1cd-129">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="0d1cd-129">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="0d1cd-130">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="0d1cd-130">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="0d1cd-131">Powiązania</span><span class="sxs-lookup"><span data-stu-id="0d1cd-131">Bindings</span></span>](../../../wcf/bindings.md)
