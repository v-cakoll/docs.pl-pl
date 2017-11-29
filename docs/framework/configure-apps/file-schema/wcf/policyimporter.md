---
title: '&lt;policyImporter&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 99bb7c6be02bad85792dfce9de1f6ef8ba1dcd17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltpolicyimportergt"></a><span data-ttu-id="c3130-102">&lt;policyImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="c3130-102">&lt;policyImporter&gt;</span></span>
<span data-ttu-id="c3130-103">Określa importera zasad, która kontroluje, importowanie niestandardowych asercji zasad dotyczących powiązań.</span><span class="sxs-lookup"><span data-stu-id="c3130-103">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="c3130-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c3130-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c3130-105">\<Klient ></span><span class="sxs-lookup"><span data-stu-id="c3130-105">\<client></span></span>  
<span data-ttu-id="c3130-106">\<metadane ></span><span class="sxs-lookup"><span data-stu-id="c3130-106">\<metadata></span></span>  
<span data-ttu-id="c3130-107">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="c3130-107">\<policyImporters></span></span>  
<span data-ttu-id="c3130-108">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="c3130-108">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3130-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3130-109">Syntax</span></span>  
  
```xml  
<metadata>  
   <policyImporters>  
      <policyImporter type="string" />  
   </policyImporters>  
</metadata>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3130-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c3130-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c3130-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c3130-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3130-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c3130-112">Attributes</span></span>  
  
|<span data-ttu-id="c3130-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c3130-113">Attribute</span></span>|<span data-ttu-id="c3130-114">Opis</span><span class="sxs-lookup"><span data-stu-id="c3130-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="c3130-115">Typ tego elementu.</span><span class="sxs-lookup"><span data-stu-id="c3130-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c3130-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c3130-116">Child Elements</span></span>  
 <span data-ttu-id="c3130-117">Brak</span><span class="sxs-lookup"><span data-stu-id="c3130-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c3130-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c3130-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c3130-119">Element</span><span class="sxs-lookup"><span data-stu-id="c3130-119">Element</span></span>|<span data-ttu-id="c3130-120">Opis</span><span class="sxs-lookup"><span data-stu-id="c3130-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c3130-121">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="c3130-121">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="c3130-122">Określa wszystkich importerów zasad sterujących importem potwierdzeń niestandardowych zasad dotyczących powiązań.</span><span class="sxs-lookup"><span data-stu-id="c3130-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3130-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3130-123">Remarks</span></span>  
 <span data-ttu-id="c3130-124">Importer zasad służy do wyszukiwania niestandardowych asercji zasad dotyczących powiązanie funkcji, jak również dołączyć element niestandardowego powiązania, który implementuje funkcje, które wymaga potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="c3130-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3130-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c3130-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 [<span data-ttu-id="c3130-126">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="c3130-126">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="c3130-127">Klienci</span><span class="sxs-lookup"><span data-stu-id="c3130-127">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
