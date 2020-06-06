---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 841331f233bb8c42c25c88ad8e9b4fb1a86faa76
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398989"
---
# \<xmlElement>
<span data-ttu-id="81a35-101">Określa element XML, który jest wysyłany w treści wiadomości do usługi tokenu zabezpieczającego podczas żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="81a35-101">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tokenRequestParameters>**](tokenrequestparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<xmlElement>**  
  
## <a name="syntax"></a><span data-ttu-id="81a35-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="81a35-102">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81a35-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="81a35-103">Attributes and Elements</span></span>  
 <span data-ttu-id="81a35-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="81a35-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81a35-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="81a35-105">Attributes</span></span>  
  
|<span data-ttu-id="81a35-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="81a35-106">Attribute</span></span>|<span data-ttu-id="81a35-107">Opis</span><span class="sxs-lookup"><span data-stu-id="81a35-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="81a35-108">xmlElement</span><span class="sxs-lookup"><span data-stu-id="81a35-108">xmlElement</span></span>|<span data-ttu-id="81a35-109">Ciąg określający element XML, który jest wysyłany w treści wiadomości do usługi tokenu zabezpieczającego podczas żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="81a35-109">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81a35-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="81a35-110">Child Elements</span></span>  
 <span data-ttu-id="81a35-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="81a35-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="81a35-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="81a35-112">Parent Elements</span></span>  
  
|<span data-ttu-id="81a35-113">Element</span><span class="sxs-lookup"><span data-stu-id="81a35-113">Element</span></span>|<span data-ttu-id="81a35-114">Opis</span><span class="sxs-lookup"><span data-stu-id="81a35-114">Description</span></span>|  
|-------------|-----------------|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="81a35-115">Kolekcja parametrów żądania tokenu.</span><span class="sxs-lookup"><span data-stu-id="81a35-115">A collection of token request parameters.</span></span> <span data-ttu-id="81a35-116">Każdy parametr jest elementem XML.</span><span class="sxs-lookup"><span data-stu-id="81a35-116">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81a35-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81a35-117">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="81a35-118">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="81a35-118">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="81a35-119">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="81a35-119">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="81a35-120">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="81a35-120">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="81a35-121">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="81a35-121">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="81a35-122">Powiązania</span><span class="sxs-lookup"><span data-stu-id="81a35-122">Bindings</span></span>](../../../wcf/bindings.md)
