---
title: '&lt;policyImporter&gt;'
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 22d90ff9d0cd5325300cf42437836f075cbf8c31
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148490"
---
# <a name="ltpolicyimportergt"></a><span data-ttu-id="6e89c-102">&lt;policyImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="6e89c-102">&lt;policyImporter&gt;</span></span>
<span data-ttu-id="6e89c-103">Określa importera zasad, który kontroluje importowanie niestandardowych asercji zasad dotyczących powiązań.</span><span class="sxs-lookup"><span data-stu-id="6e89c-103">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="6e89c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6e89c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6e89c-105">\<Klient ></span><span class="sxs-lookup"><span data-stu-id="6e89c-105">\<client></span></span>  
<span data-ttu-id="6e89c-106">\<metadane ></span><span class="sxs-lookup"><span data-stu-id="6e89c-106">\<metadata></span></span>  
<span data-ttu-id="6e89c-107">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="6e89c-107">\<policyImporters></span></span>  
<span data-ttu-id="6e89c-108">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="6e89c-108">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e89c-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="6e89c-109">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e89c-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6e89c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6e89c-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6e89c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e89c-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6e89c-112">Attributes</span></span>  
  
|<span data-ttu-id="6e89c-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6e89c-113">Attribute</span></span>|<span data-ttu-id="6e89c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="6e89c-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="6e89c-115">Typ tego elementu.</span><span class="sxs-lookup"><span data-stu-id="6e89c-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e89c-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6e89c-116">Child Elements</span></span>  
 <span data-ttu-id="6e89c-117">Brak</span><span class="sxs-lookup"><span data-stu-id="6e89c-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6e89c-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6e89c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="6e89c-119">Element</span><span class="sxs-lookup"><span data-stu-id="6e89c-119">Element</span></span>|<span data-ttu-id="6e89c-120">Opis</span><span class="sxs-lookup"><span data-stu-id="6e89c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e89c-121">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="6e89c-121">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="6e89c-122">Określa wszystkich importerów zasad sterujących importem potwierdzeń niestandardowych zasad dotyczących powiązań.</span><span class="sxs-lookup"><span data-stu-id="6e89c-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e89c-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6e89c-123">Remarks</span></span>  
 <span data-ttu-id="6e89c-124">Importer zasad służy do wyszukiwania niestandardowych asercji zasad dotyczących powiązań funkcji, jak również dołączyć element niestandardowego powiązania, który implementuje funkcje, których wymaga potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="6e89c-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e89c-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e89c-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 [<span data-ttu-id="6e89c-126">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="6e89c-126">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="6e89c-127">Klienci</span><span class="sxs-lookup"><span data-stu-id="6e89c-127">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
