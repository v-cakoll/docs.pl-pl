---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 841331f233bb8c42c25c88ad8e9b4fb1a86faa76
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398989"
---
# <a name="xmlelement"></a><span data-ttu-id="1695c-101">\<xmlElement></span><span class="sxs-lookup"><span data-stu-id="1695c-101">\<xmlElement></span></span>
<span data-ttu-id="1695c-102">Określa element XML, który jest wysyłany w treści wiadomości do usługi tokenu zabezpieczającego podczas żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="1695c-102">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
<span data-ttu-id="1695c-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1695c-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1695c-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1695c-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1695c-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="1695c-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="1695c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="1695c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="1695c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="1695c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="1695c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpieczeń**](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="1695c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="1695c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> komunikatu**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="1695c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="1695c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<tokenRequestParameters >** ](tokenrequestparameters.md)</span><span class="sxs-lookup"><span data-stu-id="1695c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tokenRequestParameters>**](tokenrequestparameters.md)</span></span>\
<span data-ttu-id="1695c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Element XmlElement >**</span><span class="sxs-lookup"><span data-stu-id="1695c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<xmlElement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1695c-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="1695c-112">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1695c-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1695c-113">Attributes and Elements</span></span>  
 <span data-ttu-id="1695c-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1695c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1695c-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1695c-115">Attributes</span></span>  
  
|<span data-ttu-id="1695c-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1695c-116">Attribute</span></span>|<span data-ttu-id="1695c-117">Opis</span><span class="sxs-lookup"><span data-stu-id="1695c-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1695c-118">xmlElement</span><span class="sxs-lookup"><span data-stu-id="1695c-118">xmlElement</span></span>|<span data-ttu-id="1695c-119">Ciąg określający element XML, który jest wysyłany w treści wiadomości do usługi tokenu zabezpieczającego podczas żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="1695c-119">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1695c-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1695c-120">Child Elements</span></span>  
 <span data-ttu-id="1695c-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="1695c-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1695c-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1695c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1695c-123">Element</span><span class="sxs-lookup"><span data-stu-id="1695c-123">Element</span></span>|<span data-ttu-id="1695c-124">Opis</span><span class="sxs-lookup"><span data-stu-id="1695c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1695c-125">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="1695c-125">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="1695c-126">Kolekcja parametrów żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="1695c-126">A collection of token request parameters.</span></span> <span data-ttu-id="1695c-127">Każdy parametr jest elementem XML.</span><span class="sxs-lookup"><span data-stu-id="1695c-127">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1695c-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1695c-128">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="1695c-129">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="1695c-129">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="1695c-130">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="1695c-130">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="1695c-131">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="1695c-131">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="1695c-132">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="1695c-132">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="1695c-133">Powiązania</span><span class="sxs-lookup"><span data-stu-id="1695c-133">Bindings</span></span>](../../../wcf/bindings.md)
