---
title: <remove><claimTypeRequirements>elementu
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 84f4208d3f4581cf7e8c4455bf3f5d78f7e13b9f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399998"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="1934a-102">\<remove>\<claimTypeRequirements>elementu</span><span class="sxs-lookup"><span data-stu-id="1934a-102">\<remove> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="1934a-103">Określa typy oświadczeń do usunięcia w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="1934a-103">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="1934a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1934a-104">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1934a-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1934a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="1934a-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1934a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1934a-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1934a-107">Attributes</span></span>  
  
|<span data-ttu-id="1934a-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1934a-108">Attribute</span></span>|<span data-ttu-id="1934a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="1934a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1934a-110">Claim</span><span class="sxs-lookup"><span data-stu-id="1934a-110">claimType</span></span>|<span data-ttu-id="1934a-111">Identyfikator URI, który definiuje typ żądania do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="1934a-111">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1934a-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1934a-112">Child Elements</span></span>  
 <span data-ttu-id="1934a-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="1934a-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1934a-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1934a-114">Parent Elements</span></span>  
  
|<span data-ttu-id="1934a-115">Element</span><span class="sxs-lookup"><span data-stu-id="1934a-115">Element</span></span>|<span data-ttu-id="1934a-116">Opis</span><span class="sxs-lookup"><span data-stu-id="1934a-116">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="1934a-117">Określa kolekcję wymaganych typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="1934a-117">Specifies a collection of required claim types.</span></span> <span data-ttu-id="1934a-118">Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="1934a-118">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="1934a-119">W scenariuszu federacyjnym usługi określają wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="1934a-119">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="1934a-120">Na przykład poświadczenia przychodzące muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="1934a-120">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="1934a-121">Każdy element w tej kolekcji określa typy wymaganych i opcjonalnych oświadczeń, które powinny być wyświetlane w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="1934a-121">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1934a-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1934a-122">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
