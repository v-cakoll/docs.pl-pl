---
title: '&lt;Element xmlElement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d1efe32121bc5744c305ff8ef8eefabd8a9d19e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltxmlelementgt"></a><span data-ttu-id="a9faa-102">&lt;Element xmlElement&gt;</span><span class="sxs-lookup"><span data-stu-id="a9faa-102">&lt;xmlElement&gt;</span></span>
<span data-ttu-id="a9faa-103">Określa element XML, który jest wysyłany w treści wiadomości do usługi tokenu zabezpieczeń, jeśli żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="a9faa-103">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
 <span data-ttu-id="a9faa-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a9faa-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a9faa-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="a9faa-105">\<bindings></span></span>  
<span data-ttu-id="a9faa-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="a9faa-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="a9faa-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="a9faa-107">\<binding></span></span>  
<span data-ttu-id="a9faa-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="a9faa-108">\<security></span></span>  
<span data-ttu-id="a9faa-109">\<komunikat ></span><span class="sxs-lookup"><span data-stu-id="a9faa-109">\<message></span></span>  
<span data-ttu-id="a9faa-110">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="a9faa-110">\<tokenRequestParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9faa-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="a9faa-111">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>  
      <xmlElement xmlElement="String" />  
</tokenRequestParameters>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a9faa-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a9faa-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a9faa-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a9faa-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a9faa-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a9faa-114">Attributes</span></span>  
  
|<span data-ttu-id="a9faa-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a9faa-115">Attribute</span></span>|<span data-ttu-id="a9faa-116">Opis</span><span class="sxs-lookup"><span data-stu-id="a9faa-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a9faa-117">xmlElement</span><span class="sxs-lookup"><span data-stu-id="a9faa-117">xmlElement</span></span>|<span data-ttu-id="a9faa-118">Ciąg określający element XML, który jest wysyłany w treści wiadomości do usługi tokenu zabezpieczeń, jeśli żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="a9faa-118">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a9faa-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a9faa-119">Child Elements</span></span>  
 <span data-ttu-id="a9faa-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="a9faa-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a9faa-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a9faa-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a9faa-122">Element</span><span class="sxs-lookup"><span data-stu-id="a9faa-122">Element</span></span>|<span data-ttu-id="a9faa-123">Opis</span><span class="sxs-lookup"><span data-stu-id="a9faa-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a9faa-124">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="a9faa-124">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="a9faa-125">Kolekcja parametrów żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="a9faa-125">A collection of token request parameters.</span></span> <span data-ttu-id="a9faa-126">Każdy parametr jest elementem XML.</span><span class="sxs-lookup"><span data-stu-id="a9faa-126">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a9faa-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a9faa-127">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>  
 [<span data-ttu-id="a9faa-128">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="a9faa-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="a9faa-129">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="a9faa-129">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="a9faa-130">Możliwości zabezpieczeń wiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="a9faa-130">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="a9faa-131">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="a9faa-131">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="a9faa-132">Powiązania</span><span class="sxs-lookup"><span data-stu-id="a9faa-132">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
