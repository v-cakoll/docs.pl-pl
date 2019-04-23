---
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: eedf0ce6cf75b8fb56daf98f2005e66162ce10d8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59155658"
---
# <a name="usemanagedpresentation"></a><span data-ttu-id="434cb-101">\<useManagedPresentation></span><span class="sxs-lookup"><span data-stu-id="434cb-101">\<useManagedPresentation></span></span>
<span data-ttu-id="434cb-102">Element powiązania, używany do komunikacji z usługi tokenów zabezpieczeń CardSpace obsługującego profil CardSpace WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="434cb-102">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="434cb-103">Ten element nie ma atrybutu i ma jako pustego przełącznika.</span><span class="sxs-lookup"><span data-stu-id="434cb-103">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="434cb-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="434cb-104">\<system.serviceModel></span></span>  
<span data-ttu-id="434cb-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="434cb-105">\<bindings></span></span>  
<span data-ttu-id="434cb-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="434cb-106">\<customBinding></span></span>  
<span data-ttu-id="434cb-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="434cb-107">\<binding></span></span>  
<span data-ttu-id="434cb-108">\<useManagedPresentation></span><span class="sxs-lookup"><span data-stu-id="434cb-108">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="434cb-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="434cb-109">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="434cb-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="434cb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="434cb-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="434cb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="434cb-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="434cb-112">Attributes</span></span>  
 <span data-ttu-id="434cb-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="434cb-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="434cb-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="434cb-114">Child Elements</span></span>  
 <span data-ttu-id="434cb-115">Brak</span><span class="sxs-lookup"><span data-stu-id="434cb-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="434cb-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="434cb-116">Parent Elements</span></span>  
  
|<span data-ttu-id="434cb-117">Element</span><span class="sxs-lookup"><span data-stu-id="434cb-117">Element</span></span>|<span data-ttu-id="434cb-118">Opis</span><span class="sxs-lookup"><span data-stu-id="434cb-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="434cb-119">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="434cb-119">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="434cb-120">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="434cb-120">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="434cb-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="434cb-121">Remarks</span></span>  
 <span data-ttu-id="434cb-122">Ten element jest używany przez dostawcę tożsamości do wyrażenia w zasadach fakt, że obsługuje ona profil CardSpace WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="434cb-122">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="434cb-123">Dostawcy tożsamości, których publikowanie asercję zasad powinno być możliwe do tokenów problem, w oparciu o ten profil CardSpace.</span><span class="sxs-lookup"><span data-stu-id="434cb-123">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="434cb-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="434cb-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="434cb-125">Powiązania</span><span class="sxs-lookup"><span data-stu-id="434cb-125">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="434cb-126">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="434cb-126">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="434cb-127">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="434cb-127">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="434cb-128">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="434cb-128">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
