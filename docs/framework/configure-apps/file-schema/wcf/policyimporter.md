---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: ab9193d5974ccffcbfa3e741ac4d32ff357ed372
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269240"
---
# <a name="policyimporter"></a><span data-ttu-id="76c51-101">\<policyImporter></span><span class="sxs-lookup"><span data-stu-id="76c51-101">\<policyImporter></span></span>
<span data-ttu-id="76c51-102">Określa importera zasad, który kontroluje importowanie niestandardowych asercji zasad dotyczących powiązań.</span><span class="sxs-lookup"><span data-stu-id="76c51-102">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="76c51-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="76c51-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="76c51-104">\<client></span><span class="sxs-lookup"><span data-stu-id="76c51-104">\<client></span></span>  
<span data-ttu-id="76c51-105">\<metadata></span><span class="sxs-lookup"><span data-stu-id="76c51-105">\<metadata></span></span>  
<span data-ttu-id="76c51-106">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="76c51-106">\<policyImporters></span></span>  
<span data-ttu-id="76c51-107">\<policyImporter></span><span class="sxs-lookup"><span data-stu-id="76c51-107">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76c51-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="76c51-108">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76c51-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="76c51-109">Attributes and Elements</span></span>  
 <span data-ttu-id="76c51-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="76c51-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76c51-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="76c51-111">Attributes</span></span>  
  
|<span data-ttu-id="76c51-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="76c51-112">Attribute</span></span>|<span data-ttu-id="76c51-113">Opis</span><span class="sxs-lookup"><span data-stu-id="76c51-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="76c51-114">Typ tego elementu.</span><span class="sxs-lookup"><span data-stu-id="76c51-114">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76c51-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="76c51-115">Child Elements</span></span>  
 <span data-ttu-id="76c51-116">Brak</span><span class="sxs-lookup"><span data-stu-id="76c51-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="76c51-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="76c51-117">Parent Elements</span></span>  
  
|<span data-ttu-id="76c51-118">Element</span><span class="sxs-lookup"><span data-stu-id="76c51-118">Element</span></span>|<span data-ttu-id="76c51-119">Opis</span><span class="sxs-lookup"><span data-stu-id="76c51-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76c51-120">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="76c51-120">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="76c51-121">Określa wszystkich importerów zasad sterujących importem potwierdzeń niestandardowych zasad dotyczących powiązań.</span><span class="sxs-lookup"><span data-stu-id="76c51-121">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76c51-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="76c51-122">Remarks</span></span>  
 <span data-ttu-id="76c51-123">Importer zasad służy do wyszukiwania niestandardowych asercji zasad dotyczących powiązań funkcji, jak również dołączyć element niestandardowego powiązania, który implementuje funkcje, których wymaga potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="76c51-123">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76c51-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="76c51-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="76c51-125">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="76c51-125">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="76c51-126">Klienci</span><span class="sxs-lookup"><span data-stu-id="76c51-126">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
