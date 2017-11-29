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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f99879ab80acddf1d50f5e5c734b8d6c975cb348
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltusemanagedpresentationgt"></a><span data-ttu-id="a5666-102">&lt;useManagedPresentation&gt;</span><span class="sxs-lookup"><span data-stu-id="a5666-102">&lt;useManagedPresentation&gt;</span></span>
<span data-ttu-id="a5666-103">Element powiązania, używany do komunikacji z usługą tokenu zabezpieczeń CardSpace obsługującą profil CardSpace WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="a5666-103">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="a5666-104">Ten element nie ma atrybutu i są dostępne jako pusty przełącznik.</span><span class="sxs-lookup"><span data-stu-id="a5666-104">This element has no attribute and is present as an empty switch.</span></span>  
  
 <span data-ttu-id="a5666-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="a5666-105">\<system.serviceModel></span></span>  
<span data-ttu-id="a5666-106">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="a5666-106">\<bindings></span></span>  
<span data-ttu-id="a5666-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a5666-107">\<customBinding></span></span>  
<span data-ttu-id="a5666-108">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="a5666-108">\<binding></span></span>  
<span data-ttu-id="a5666-109">\<useManagedPresentation ></span><span class="sxs-lookup"><span data-stu-id="a5666-109">\<useManagedPresentation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5666-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5666-110">Syntax</span></span>  
  
```xml  
<useManagedPresentation/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5666-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a5666-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a5666-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a5666-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5666-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a5666-113">Attributes</span></span>  
 <span data-ttu-id="a5666-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="a5666-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a5666-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a5666-115">Child Elements</span></span>  
 <span data-ttu-id="a5666-116">Brak</span><span class="sxs-lookup"><span data-stu-id="a5666-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a5666-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a5666-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a5666-118">Element</span><span class="sxs-lookup"><span data-stu-id="a5666-118">Element</span></span>|<span data-ttu-id="a5666-119">Opis</span><span class="sxs-lookup"><span data-stu-id="a5666-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5666-120">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="a5666-120">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a5666-121">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="a5666-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5666-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5666-122">Remarks</span></span>  
 <span data-ttu-id="a5666-123">Ten element jest używany przez dostawcę tożsamości można wyrazić w zasadach fakt, że aplikacja obsługuje profil CardSpace WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="a5666-123">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="a5666-124">Dostawców tożsamości, które publikują potwierdzenia zasad powinno być możliwe tokeny problemu w oparciu o ten profil CardSpace.</span><span class="sxs-lookup"><span data-stu-id="a5666-124">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5666-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5666-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>  
 <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="a5666-126">Powiązania</span><span class="sxs-lookup"><span data-stu-id="a5666-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a5666-127">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="a5666-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="a5666-128">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="a5666-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="a5666-129">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a5666-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
