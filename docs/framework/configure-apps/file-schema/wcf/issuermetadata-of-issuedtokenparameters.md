---
title: <issuerMetadata> dla <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
ms.openlocfilehash: fcdd66ecd162dff5be86a1d4ab1b196f50dbd445
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400341"
---
# <a name="issuermetadata-of-issuedtokenparameters"></a><span data-ttu-id="b373a-102">\<issuerMetadata> dla \<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="b373a-102">\<issuerMetadata> of \<issuedTokenParameters></span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenParameters>**](issuedtokenparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**  
  
## <a name="syntax"></a><span data-ttu-id="b373a-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="b373a-103">Syntax</span></span>  
  
```xml  
<issuerMetaData address="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b373a-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b373a-104">Attributes and Elements</span></span>  
 <span data-ttu-id="b373a-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b373a-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b373a-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b373a-106">Attributes</span></span>  
  
|<span data-ttu-id="b373a-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b373a-107">Attribute</span></span>|<span data-ttu-id="b373a-108">Opis</span><span class="sxs-lookup"><span data-stu-id="b373a-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b373a-109">adres</span><span class="sxs-lookup"><span data-stu-id="b373a-109">address</span></span>|<span data-ttu-id="b373a-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="b373a-110">Required.</span></span> <span data-ttu-id="b373a-111">Ciąg określający adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="b373a-111">A string that specifies the address of the endpoint.</span></span> <span data-ttu-id="b373a-112">Adres musi być bezwzględnym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="b373a-112">The address must be an absolute URI.</span></span> <span data-ttu-id="b373a-113">Wartością domyślną jest ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="b373a-113">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b373a-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b373a-114">Child Elements</span></span>  
  
|<span data-ttu-id="b373a-115">Element</span><span class="sxs-lookup"><span data-stu-id="b373a-115">Element</span></span>|<span data-ttu-id="b373a-116">Opis</span><span class="sxs-lookup"><span data-stu-id="b373a-116">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="b373a-117">Kolekcja nagłówków adresów.</span><span class="sxs-lookup"><span data-stu-id="b373a-117">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="b373a-118">Tożsamość, która umożliwia uwierzytelnianie punktu końcowego przez inne punkty końcowe wymieniające z nim komunikaty.</span><span class="sxs-lookup"><span data-stu-id="b373a-118">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b373a-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b373a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b373a-120">Element</span><span class="sxs-lookup"><span data-stu-id="b373a-120">Element</span></span>|<span data-ttu-id="b373a-121">Opis</span><span class="sxs-lookup"><span data-stu-id="b373a-121">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="b373a-122">Określa parametry tokenu zabezpieczającego wydanego w federacyjnym scenariuszu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="b373a-122">Specifies the parameters for an security token issued in a Federated security scenario.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b373a-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b373a-123">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="b373a-124">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="b373a-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="b373a-125">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="b373a-125">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="b373a-126">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="b373a-126">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="b373a-127">Federacja i wystawione tokeny</span><span class="sxs-lookup"><span data-stu-id="b373a-127">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="b373a-128">Powiązania</span><span class="sxs-lookup"><span data-stu-id="b373a-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b373a-129">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="b373a-129">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b373a-130">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="b373a-130">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="b373a-131">Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="b373a-131">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="b373a-132">Zabezpieczenia wiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="b373a-132">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
