---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 81f38d2a163163ca7255ca546bbddbbb58fa3a1b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094180"
---
# <a name="policyimporter"></a><span data-ttu-id="6c71d-101">\<policyImporter></span><span class="sxs-lookup"><span data-stu-id="6c71d-101">\<policyImporter></span></span>
<span data-ttu-id="6c71d-102">Określa importera zasad, który kontroluje importowanie niestandardowych asercji zasad dotyczących powiązań.</span><span class="sxs-lookup"><span data-stu-id="6c71d-102">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="6c71d-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6c71d-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="6c71d-104">\<client></span><span class="sxs-lookup"><span data-stu-id="6c71d-104">\<client></span></span>  
<span data-ttu-id="6c71d-105">\<metadata></span><span class="sxs-lookup"><span data-stu-id="6c71d-105">\<metadata></span></span>  
<span data-ttu-id="6c71d-106">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="6c71d-106">\<policyImporters></span></span>  
<span data-ttu-id="6c71d-107">\<policyImporter></span><span class="sxs-lookup"><span data-stu-id="6c71d-107">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c71d-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c71d-108">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c71d-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6c71d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6c71d-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6c71d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c71d-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6c71d-111">Attributes</span></span>  
  
|<span data-ttu-id="6c71d-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6c71d-112">Attribute</span></span>|<span data-ttu-id="6c71d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="6c71d-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="6c71d-114">Typ tego elementu.</span><span class="sxs-lookup"><span data-stu-id="6c71d-114">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c71d-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6c71d-115">Child Elements</span></span>  
 <span data-ttu-id="6c71d-116">Brak</span><span class="sxs-lookup"><span data-stu-id="6c71d-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6c71d-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6c71d-117">Parent Elements</span></span>  
  
|<span data-ttu-id="6c71d-118">Element</span><span class="sxs-lookup"><span data-stu-id="6c71d-118">Element</span></span>|<span data-ttu-id="6c71d-119">Opis</span><span class="sxs-lookup"><span data-stu-id="6c71d-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c71d-120">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="6c71d-120">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="6c71d-121">Określa wszystkich importerów zasad sterujących importem potwierdzeń niestandardowych zasad dotyczących powiązań.</span><span class="sxs-lookup"><span data-stu-id="6c71d-121">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c71d-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6c71d-122">Remarks</span></span>  
 <span data-ttu-id="6c71d-123">Importer zasad służy do wyszukiwania niestandardowych asercji zasad dotyczących powiązań funkcji, jak również dołączyć element niestandardowego powiązania, który implementuje funkcje, których wymaga potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="6c71d-123">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c71d-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c71d-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="6c71d-125">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="6c71d-125">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="6c71d-126">Klienci</span><span class="sxs-lookup"><span data-stu-id="6c71d-126">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
