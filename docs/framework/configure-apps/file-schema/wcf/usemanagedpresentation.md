---
title: '&lt;useManagedPresentation&gt;'
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: 96490421addfadd9cef6b65bddaed0aae3370d15
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720278"
---
# <a name="ltusemanagedpresentationgt"></a><span data-ttu-id="39f87-102">&lt;useManagedPresentation&gt;</span><span class="sxs-lookup"><span data-stu-id="39f87-102">&lt;useManagedPresentation&gt;</span></span>
<span data-ttu-id="39f87-103">Element powiązania, używany do komunikacji z usługi tokenów zabezpieczeń CardSpace obsługującego profil CardSpace WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="39f87-103">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="39f87-104">Ten element nie ma atrybutu i ma jako pustego przełącznika.</span><span class="sxs-lookup"><span data-stu-id="39f87-104">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="39f87-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="39f87-105">\<system.serviceModel></span></span>  
<span data-ttu-id="39f87-106">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="39f87-106">\<bindings></span></span>  
<span data-ttu-id="39f87-107">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="39f87-107">\<customBinding></span></span>  
<span data-ttu-id="39f87-108">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="39f87-108">\<binding></span></span>  
<span data-ttu-id="39f87-109">\<useManagedPresentation></span><span class="sxs-lookup"><span data-stu-id="39f87-109">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39f87-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="39f87-110">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39f87-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="39f87-111">Attributes and Elements</span></span>  
 <span data-ttu-id="39f87-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="39f87-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39f87-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="39f87-113">Attributes</span></span>  
 <span data-ttu-id="39f87-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="39f87-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="39f87-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="39f87-115">Child Elements</span></span>  
 <span data-ttu-id="39f87-116">Brak</span><span class="sxs-lookup"><span data-stu-id="39f87-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="39f87-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="39f87-117">Parent Elements</span></span>  
  
|<span data-ttu-id="39f87-118">Element</span><span class="sxs-lookup"><span data-stu-id="39f87-118">Element</span></span>|<span data-ttu-id="39f87-119">Opis</span><span class="sxs-lookup"><span data-stu-id="39f87-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39f87-120">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="39f87-120">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="39f87-121">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="39f87-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39f87-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="39f87-122">Remarks</span></span>  
 <span data-ttu-id="39f87-123">Ten element jest używany przez dostawcę tożsamości do wyrażenia w zasadach fakt, że obsługuje ona profil CardSpace WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="39f87-123">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="39f87-124">Dostawcy tożsamości, których publikowanie asercję zasad powinno być możliwe do tokenów problem, w oparciu o ten profil CardSpace.</span><span class="sxs-lookup"><span data-stu-id="39f87-124">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39f87-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39f87-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="39f87-126">Powiązania</span><span class="sxs-lookup"><span data-stu-id="39f87-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="39f87-127">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="39f87-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="39f87-128">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="39f87-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="39f87-129">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="39f87-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
