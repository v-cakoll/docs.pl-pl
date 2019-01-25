---
title: '&lt;policyImporter&gt;'
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 4075f7fcb1c65da3d9e2e5e5dab52452ca2c9b60
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632169"
---
# <a name="ltpolicyimportergt"></a><span data-ttu-id="cfd00-102">&lt;policyImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="cfd00-102">&lt;policyImporter&gt;</span></span>
<span data-ttu-id="cfd00-103">Określa importera zasad, który kontroluje importowanie niestandardowych asercji zasad dotyczących powiązań.</span><span class="sxs-lookup"><span data-stu-id="cfd00-103">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="cfd00-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cfd00-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cfd00-105">\<client></span><span class="sxs-lookup"><span data-stu-id="cfd00-105">\<client></span></span>  
<span data-ttu-id="cfd00-106">\<metadata></span><span class="sxs-lookup"><span data-stu-id="cfd00-106">\<metadata></span></span>  
<span data-ttu-id="cfd00-107">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="cfd00-107">\<policyImporters></span></span>  
<span data-ttu-id="cfd00-108">\<policyImporter></span><span class="sxs-lookup"><span data-stu-id="cfd00-108">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfd00-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="cfd00-109">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cfd00-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cfd00-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cfd00-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cfd00-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cfd00-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cfd00-112">Attributes</span></span>  
  
|<span data-ttu-id="cfd00-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cfd00-113">Attribute</span></span>|<span data-ttu-id="cfd00-114">Opis</span><span class="sxs-lookup"><span data-stu-id="cfd00-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="cfd00-115">Typ tego elementu.</span><span class="sxs-lookup"><span data-stu-id="cfd00-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cfd00-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cfd00-116">Child Elements</span></span>  
 <span data-ttu-id="cfd00-117">Brak</span><span class="sxs-lookup"><span data-stu-id="cfd00-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cfd00-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cfd00-118">Parent Elements</span></span>  
  
|<span data-ttu-id="cfd00-119">Element</span><span class="sxs-lookup"><span data-stu-id="cfd00-119">Element</span></span>|<span data-ttu-id="cfd00-120">Opis</span><span class="sxs-lookup"><span data-stu-id="cfd00-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cfd00-121">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="cfd00-121">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="cfd00-122">Określa wszystkich importerów zasad sterujących importem potwierdzeń niestandardowych zasad dotyczących powiązań.</span><span class="sxs-lookup"><span data-stu-id="cfd00-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfd00-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cfd00-123">Remarks</span></span>  
 <span data-ttu-id="cfd00-124">Importer zasad służy do wyszukiwania niestandardowych asercji zasad dotyczących powiązań funkcji, jak również dołączyć element niestandardowego powiązania, który implementuje funkcje, których wymaga potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="cfd00-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfd00-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cfd00-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="cfd00-126">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="cfd00-126">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="cfd00-127">Klienci</span><span class="sxs-lookup"><span data-stu-id="cfd00-127">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
