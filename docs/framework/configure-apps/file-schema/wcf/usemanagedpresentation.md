---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: c410967e84c9318d21ce0b3072d08b026a37b190
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399214"
---
# <a name="usemanagedpresentation"></a><span data-ttu-id="b41cf-101">\<useManagedPresentation ></span><span class="sxs-lookup"><span data-stu-id="b41cf-101">\<useManagedPresentation></span></span>
<span data-ttu-id="b41cf-102">Element powiązania używany do komunikowania się z usługą tokenu zabezpieczającego CardSpace obsługującą profil CardSpace usługi WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="b41cf-102">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="b41cf-103">Ten element nie ma atrybutu i jest obecny jako pusty przełącznik.</span><span class="sxs-lookup"><span data-stu-id="b41cf-103">This element has no attribute and is present as an empty switch.</span></span>  
  
<span data-ttu-id="b41cf-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b41cf-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b41cf-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b41cf-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b41cf-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="b41cf-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="b41cf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<niestandardowy >Binding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="b41cf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="b41cf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="b41cf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="b41cf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<useManagedPresentation >**</span><span class="sxs-lookup"><span data-stu-id="b41cf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useManagedPresentation>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b41cf-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="b41cf-110">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b41cf-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b41cf-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b41cf-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b41cf-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b41cf-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b41cf-113">Attributes</span></span>  
 <span data-ttu-id="b41cf-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="b41cf-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b41cf-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b41cf-115">Child Elements</span></span>  
 <span data-ttu-id="b41cf-116">Brak</span><span class="sxs-lookup"><span data-stu-id="b41cf-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b41cf-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b41cf-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b41cf-118">Element</span><span class="sxs-lookup"><span data-stu-id="b41cf-118">Element</span></span>|<span data-ttu-id="b41cf-119">Opis</span><span class="sxs-lookup"><span data-stu-id="b41cf-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b41cf-120">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="b41cf-120">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="b41cf-121">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="b41cf-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b41cf-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b41cf-122">Remarks</span></span>  
 <span data-ttu-id="b41cf-123">Ten element jest używany przez dostawcę tożsamości do wyrażenia w jego zasadom faktu, że obsługuje profil CardSpace usługi WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="b41cf-123">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="b41cf-124">Dostawcy tożsamości, którzy publikują takie potwierdzenie zasad, powinni mieć możliwość wystawiania tokenów opartych na tym profilu programu CardSpace.</span><span class="sxs-lookup"><span data-stu-id="b41cf-124">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b41cf-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b41cf-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="b41cf-126">Powiązania</span><span class="sxs-lookup"><span data-stu-id="b41cf-126">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b41cf-127">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="b41cf-127">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b41cf-128">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="b41cf-128">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b41cf-129">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b41cf-129">\<customBinding></span></span>](custombinding.md)
