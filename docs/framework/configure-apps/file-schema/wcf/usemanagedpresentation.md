---
title: '&lt;useManagedPresentation&gt;'
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: 35af7f5e10594617807384c20ab706ad675d11ef
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755295"
---
# <a name="ltusemanagedpresentationgt"></a><span data-ttu-id="c0f22-102">&lt;useManagedPresentation&gt;</span><span class="sxs-lookup"><span data-stu-id="c0f22-102">&lt;useManagedPresentation&gt;</span></span>
<span data-ttu-id="c0f22-103">Element powiązania, używany do komunikacji z usługą tokenu zabezpieczeń CardSpace obsługującą profil CardSpace WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="c0f22-103">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="c0f22-104">Ten element nie ma atrybutu i są dostępne jako pusty przełącznik.</span><span class="sxs-lookup"><span data-stu-id="c0f22-104">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="c0f22-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c0f22-105">\<system.serviceModel></span></span>  
<span data-ttu-id="c0f22-106">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="c0f22-106">\<bindings></span></span>  
<span data-ttu-id="c0f22-107">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c0f22-107">\<customBinding></span></span>  
<span data-ttu-id="c0f22-108">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="c0f22-108">\<binding></span></span>  
<span data-ttu-id="c0f22-109">\<useManagedPresentation ></span><span class="sxs-lookup"><span data-stu-id="c0f22-109">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0f22-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="c0f22-110">Syntax</span></span>  
  
```xml  
<useManagedPresentation/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0f22-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c0f22-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c0f22-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c0f22-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0f22-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c0f22-113">Attributes</span></span>  
 <span data-ttu-id="c0f22-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="c0f22-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c0f22-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c0f22-115">Child Elements</span></span>  
 <span data-ttu-id="c0f22-116">Brak</span><span class="sxs-lookup"><span data-stu-id="c0f22-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c0f22-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c0f22-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c0f22-118">Element</span><span class="sxs-lookup"><span data-stu-id="c0f22-118">Element</span></span>|<span data-ttu-id="c0f22-119">Opis</span><span class="sxs-lookup"><span data-stu-id="c0f22-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0f22-120">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="c0f22-120">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="c0f22-121">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="c0f22-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0f22-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c0f22-122">Remarks</span></span>  
 <span data-ttu-id="c0f22-123">Ten element jest używany przez dostawcę tożsamości można wyrazić w zasadach fakt, że aplikacja obsługuje profil CardSpace WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="c0f22-123">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="c0f22-124">Dostawców tożsamości, które publikują potwierdzenia zasad powinno być możliwe tokeny problemu w oparciu o ten profil CardSpace.</span><span class="sxs-lookup"><span data-stu-id="c0f22-124">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0f22-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0f22-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>  
 <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="c0f22-126">Powiązania</span><span class="sxs-lookup"><span data-stu-id="c0f22-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="c0f22-127">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="c0f22-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="c0f22-128">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="c0f22-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="c0f22-129">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c0f22-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
