---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: bb2989ed52a88d805510d65e1dc1740df7bb55eb
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735940"
---
# <a name="usemanagedpresentation"></a><span data-ttu-id="a5f04-101">\<useManagedPresentation ></span><span class="sxs-lookup"><span data-stu-id="a5f04-101">\<useManagedPresentation></span></span>
<span data-ttu-id="a5f04-102">Element powiązania używany do komunikowania się z usługą tokenu zabezpieczającego CardSpace obsługującą profil CardSpace usługi WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="a5f04-102">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="a5f04-103">Ten element nie ma atrybutu i jest obecny jako pusty przełącznik.</span><span class="sxs-lookup"><span data-stu-id="a5f04-103">This element has no attribute and is present as an empty switch.</span></span>  
  
<span data-ttu-id="a5f04-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="a5f04-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a5f04-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="a5f04-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a5f04-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="a5f04-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="a5f04-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**CustomBinding**](custombinding.md) ></span><span class="sxs-lookup"><span data-stu-id="a5f04-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="a5f04-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** </span><span class="sxs-lookup"><span data-stu-id="a5f04-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="a5f04-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<useManagedPresentation >**</span><span class="sxs-lookup"><span data-stu-id="a5f04-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useManagedPresentation>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5f04-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5f04-110">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5f04-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a5f04-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a5f04-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a5f04-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5f04-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a5f04-113">Attributes</span></span>  
 <span data-ttu-id="a5f04-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="a5f04-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a5f04-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a5f04-115">Child Elements</span></span>  
 <span data-ttu-id="a5f04-116">Brak</span><span class="sxs-lookup"><span data-stu-id="a5f04-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a5f04-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a5f04-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a5f04-118">Element</span><span class="sxs-lookup"><span data-stu-id="a5f04-118">Element</span></span>|<span data-ttu-id="a5f04-119">Opis</span><span class="sxs-lookup"><span data-stu-id="a5f04-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5f04-120">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="a5f04-120">\<binding></span></span>](bindings.md)|<span data-ttu-id="a5f04-121">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="a5f04-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5f04-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5f04-122">Remarks</span></span>  
 <span data-ttu-id="a5f04-123">Ten element jest używany przez dostawcę tożsamości do wyrażenia w jego zasadom faktu, że obsługuje profil CardSpace usługi WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="a5f04-123">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="a5f04-124">Dostawcy tożsamości, którzy publikują takie potwierdzenie zasad, powinni mieć możliwość wystawiania tokenów opartych na tym profilu programu CardSpace.</span><span class="sxs-lookup"><span data-stu-id="a5f04-124">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5f04-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5f04-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="a5f04-126">Powiązania</span><span class="sxs-lookup"><span data-stu-id="a5f04-126">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a5f04-127">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="a5f04-127">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a5f04-128">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="a5f04-128">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="a5f04-129">\<niestandardowebinding ></span><span class="sxs-lookup"><span data-stu-id="a5f04-129">\<customBinding></span></span>](custombinding.md)
