---
title: <pnrpPeerResolver>
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: d7c6c8efa971fb60f0257cc1c74ceda72e31cb84
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400057"
---
# <a name="pnrppeerresolver"></a><span data-ttu-id="77524-101">\<pnrpPeerResolver></span><span class="sxs-lookup"><span data-stu-id="77524-101">\<pnrpPeerResolver></span></span>
<span data-ttu-id="77524-102">Określa, że program rozpoznawania nazw PNRP (Peer Name Resolution Protocol) ma być używany jako program rozpoznawania nazw.</span><span class="sxs-lookup"><span data-stu-id="77524-102">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="77524-103">Ten element jest opcjonalny, ponieważ protokół PNRP jest domyślnym programem rozpoznawania nazw.</span><span class="sxs-lookup"><span data-stu-id="77524-103">This element is optional because PNRP is the default resolver.</span></span>  
  
<span data-ttu-id="77524-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="77524-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="77524-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="77524-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="77524-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="77524-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="77524-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<niestandardowy >Binding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="77524-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="77524-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="77524-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="77524-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<pnrpResolver >**</span><span class="sxs-lookup"><span data-stu-id="77524-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<pnrpResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77524-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="77524-110">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77524-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="77524-111">Attributes and Elements</span></span>  
 <span data-ttu-id="77524-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="77524-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77524-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="77524-113">Attributes</span></span>  
  
|<span data-ttu-id="77524-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="77524-114">Attribute</span></span>|<span data-ttu-id="77524-115">Opis</span><span class="sxs-lookup"><span data-stu-id="77524-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="77524-116">resolverType</span><span class="sxs-lookup"><span data-stu-id="77524-116">resolverType</span></span>|<span data-ttu-id="77524-117">Ciąg określający, który mechanizm rozwiązywania konfliktów ma być używany.</span><span class="sxs-lookup"><span data-stu-id="77524-117">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="77524-118">Ten atrybut jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="77524-118">This attribute is optional.</span></span> <span data-ttu-id="77524-119">Jeśli nie jest ustawiona, lub jeśli jest ustawiona na pusty ciąg, używany jest protokół PNRP.</span><span class="sxs-lookup"><span data-stu-id="77524-119">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="77524-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="77524-120">Child Elements</span></span>  
 <span data-ttu-id="77524-121">Brak</span><span class="sxs-lookup"><span data-stu-id="77524-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="77524-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="77524-122">Parent Elements</span></span>  
  
|<span data-ttu-id="77524-123">Element</span><span class="sxs-lookup"><span data-stu-id="77524-123">Element</span></span>|<span data-ttu-id="77524-124">Opis</span><span class="sxs-lookup"><span data-stu-id="77524-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="77524-125">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="77524-125">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="77524-126">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="77524-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="77524-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="77524-127">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />
```  
  
## <a name="see-also"></a><span data-ttu-id="77524-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77524-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>
- <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="77524-129">Powiązania</span><span class="sxs-lookup"><span data-stu-id="77524-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="77524-130">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="77524-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="77524-131">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="77524-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="77524-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="77524-132">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="77524-133">Mechanizmy rozpoznawania elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="77524-133">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
