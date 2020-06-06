---
title: <clear><claimTypeRequirements>elementu
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: 01f101f7d0dd5da6a834a4ffb2c7e09df0e23cd8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400528"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="e91b8-102">\<clear>\<claimTypeRequirements>elementu</span><span class="sxs-lookup"><span data-stu-id="e91b8-102">\<clear> of \<claimTypeRequirements> element</span></span>
<span data-ttu-id="e91b8-103">Określa, że wszystkie typy roszczeń mają być usunięte w poświadczeniu federacyjnym.</span><span class="sxs-lookup"><span data-stu-id="e91b8-103">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="e91b8-104">Dzięki temu zbieranie danych jest puste.</span><span class="sxs-lookup"><span data-stu-id="e91b8-104">This ensures that the collection starts empty.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="e91b8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e91b8-105">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e91b8-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e91b8-106">Attributes and Elements</span></span>  
 <span data-ttu-id="e91b8-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e91b8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e91b8-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e91b8-108">Attributes</span></span>  
 <span data-ttu-id="e91b8-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="e91b8-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e91b8-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e91b8-110">Child Elements</span></span>  
 <span data-ttu-id="e91b8-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="e91b8-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e91b8-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e91b8-112">Parent Elements</span></span>  
  
|<span data-ttu-id="e91b8-113">Element</span><span class="sxs-lookup"><span data-stu-id="e91b8-113">Element</span></span>|<span data-ttu-id="e91b8-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e91b8-114">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="e91b8-115">Określa kolekcję wymaganych typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="e91b8-115">Specifies a collection of required claim types.</span></span> <span data-ttu-id="e91b8-116">Każdy element jest typu <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="e91b8-116">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="e91b8-117">W scenariuszu federacyjnym usługi określają wymagania dotyczące poświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="e91b8-117">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="e91b8-118">Na przykład poświadczenia przychodzące muszą mieć określony zestaw typów roszczeń.</span><span class="sxs-lookup"><span data-stu-id="e91b8-118">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="e91b8-119">Każdy element w tej kolekcji określa typy wymaganych i opcjonalnych oświadczeń, które powinny być wyświetlane w federacyjnym poświadczeniu.</span><span class="sxs-lookup"><span data-stu-id="e91b8-119">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e91b8-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e91b8-120">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
