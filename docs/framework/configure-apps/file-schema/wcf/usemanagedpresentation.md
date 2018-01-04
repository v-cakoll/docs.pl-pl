---
title: '&lt;useManagedPresentation&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae9851794d77972066fb897aa76528fec86fd6f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltusemanagedpresentationgt"></a><span data-ttu-id="90fe8-102">&lt;useManagedPresentation&gt;</span><span class="sxs-lookup"><span data-stu-id="90fe8-102">&lt;useManagedPresentation&gt;</span></span>
<span data-ttu-id="90fe8-103">Element powiązania, używany do komunikacji z usługą tokenu zabezpieczeń CardSpace obsługującą profil CardSpace WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="90fe8-103">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="90fe8-104">Ten element nie ma atrybutu i są dostępne jako pusty przełącznik.</span><span class="sxs-lookup"><span data-stu-id="90fe8-104">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="90fe8-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="90fe8-105">\<system.serviceModel></span></span>  
<span data-ttu-id="90fe8-106">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="90fe8-106">\<bindings></span></span>  
<span data-ttu-id="90fe8-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="90fe8-107">\<customBinding></span></span>  
<span data-ttu-id="90fe8-108">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="90fe8-108">\<binding></span></span>  
<span data-ttu-id="90fe8-109">\<useManagedPresentation ></span><span class="sxs-lookup"><span data-stu-id="90fe8-109">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90fe8-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="90fe8-110">Syntax</span></span>  
  
```xml  
<useManagedPresentation/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90fe8-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="90fe8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="90fe8-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="90fe8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90fe8-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="90fe8-113">Attributes</span></span>  
 <span data-ttu-id="90fe8-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="90fe8-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="90fe8-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="90fe8-115">Child Elements</span></span>  
 <span data-ttu-id="90fe8-116">Brak</span><span class="sxs-lookup"><span data-stu-id="90fe8-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="90fe8-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="90fe8-117">Parent Elements</span></span>  
  
|<span data-ttu-id="90fe8-118">Element</span><span class="sxs-lookup"><span data-stu-id="90fe8-118">Element</span></span>|<span data-ttu-id="90fe8-119">Opis</span><span class="sxs-lookup"><span data-stu-id="90fe8-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90fe8-120">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="90fe8-120">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="90fe8-121">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="90fe8-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90fe8-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="90fe8-122">Remarks</span></span>  
 <span data-ttu-id="90fe8-123">Ten element jest używany przez dostawcę tożsamości można wyrazić w zasadach fakt, że aplikacja obsługuje profil CardSpace WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="90fe8-123">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="90fe8-124">Dostawców tożsamości, które publikują potwierdzenia zasad powinno być możliwe tokeny problemu w oparciu o ten profil CardSpace.</span><span class="sxs-lookup"><span data-stu-id="90fe8-124">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90fe8-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="90fe8-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>  
 <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="90fe8-126">Powiązania</span><span class="sxs-lookup"><span data-stu-id="90fe8-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="90fe8-127">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="90fe8-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="90fe8-128">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="90fe8-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="90fe8-129">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="90fe8-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
