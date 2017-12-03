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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b56c431c0e8dbab7bd4680a6e692d9b4f6e0eec4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltpolicyimportergt"></a><span data-ttu-id="e34c9-102">&lt;policyImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="e34c9-102">&lt;policyImporter&gt;</span></span>
<span data-ttu-id="e34c9-103">Określa importera zasad, która kontroluje, importowanie niestandardowych asercji zasad dotyczących powiązań.</span><span class="sxs-lookup"><span data-stu-id="e34c9-103">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="e34c9-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e34c9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e34c9-105">\<Klient ></span><span class="sxs-lookup"><span data-stu-id="e34c9-105">\<client></span></span>  
<span data-ttu-id="e34c9-106">\<metadane ></span><span class="sxs-lookup"><span data-stu-id="e34c9-106">\<metadata></span></span>  
<span data-ttu-id="e34c9-107">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="e34c9-107">\<policyImporters></span></span>  
<span data-ttu-id="e34c9-108">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="e34c9-108">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e34c9-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="e34c9-109">Syntax</span></span>  
  
```xml  
<metadata>  
   <policyImporters>  
      <policyImporter type="string" />  
   </policyImporters>  
</metadata>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e34c9-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e34c9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e34c9-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e34c9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e34c9-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e34c9-112">Attributes</span></span>  
  
|<span data-ttu-id="e34c9-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e34c9-113">Attribute</span></span>|<span data-ttu-id="e34c9-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e34c9-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="e34c9-115">Typ tego elementu.</span><span class="sxs-lookup"><span data-stu-id="e34c9-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e34c9-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e34c9-116">Child Elements</span></span>  
 <span data-ttu-id="e34c9-117">Brak</span><span class="sxs-lookup"><span data-stu-id="e34c9-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e34c9-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e34c9-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e34c9-119">Element</span><span class="sxs-lookup"><span data-stu-id="e34c9-119">Element</span></span>|<span data-ttu-id="e34c9-120">Opis</span><span class="sxs-lookup"><span data-stu-id="e34c9-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e34c9-121">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="e34c9-121">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="e34c9-122">Określa wszystkich importerów zasad sterujących importem potwierdzeń niestandardowych zasad dotyczących powiązań.</span><span class="sxs-lookup"><span data-stu-id="e34c9-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e34c9-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e34c9-123">Remarks</span></span>  
 <span data-ttu-id="e34c9-124">Importer zasad służy do wyszukiwania niestandardowych asercji zasad dotyczących powiązanie funkcji, jak również dołączyć element niestandardowego powiązania, który implementuje funkcje, które wymaga potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="e34c9-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e34c9-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e34c9-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 [<span data-ttu-id="e34c9-126">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="e34c9-126">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="e34c9-127">Klienci</span><span class="sxs-lookup"><span data-stu-id="e34c9-127">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
