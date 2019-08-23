---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 273bd0d5e68a661c639b82264b440b83d8127427
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933788"
---
# <a name="policyimporter"></a><span data-ttu-id="b3ed4-101">\<policyImporter></span><span class="sxs-lookup"><span data-stu-id="b3ed4-101">\<policyImporter></span></span>
<span data-ttu-id="b3ed4-102">Określa importera zasad kontrolujących Importowanie potwierdzeń niestandardowych zasad dotyczących powiązań.</span><span class="sxs-lookup"><span data-stu-id="b3ed4-102">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="b3ed4-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b3ed4-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="b3ed4-104">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="b3ed4-104">\<client></span></span>  
<span data-ttu-id="b3ed4-105">\<> metadanych</span><span class="sxs-lookup"><span data-stu-id="b3ed4-105">\<metadata></span></span>  
<span data-ttu-id="b3ed4-106">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="b3ed4-106">\<policyImporters></span></span>  
<span data-ttu-id="b3ed4-107">\<policyImporter></span><span class="sxs-lookup"><span data-stu-id="b3ed4-107">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3ed4-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="b3ed4-108">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3ed4-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b3ed4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b3ed4-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b3ed4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3ed4-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b3ed4-111">Attributes</span></span>  
  
|<span data-ttu-id="b3ed4-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b3ed4-112">Attribute</span></span>|<span data-ttu-id="b3ed4-113">Opis</span><span class="sxs-lookup"><span data-stu-id="b3ed4-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="b3ed4-114">Typ tego elementu.</span><span class="sxs-lookup"><span data-stu-id="b3ed4-114">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b3ed4-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b3ed4-115">Child Elements</span></span>  
 <span data-ttu-id="b3ed4-116">Brak</span><span class="sxs-lookup"><span data-stu-id="b3ed4-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b3ed4-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b3ed4-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b3ed4-118">Element</span><span class="sxs-lookup"><span data-stu-id="b3ed4-118">Element</span></span>|<span data-ttu-id="b3ed4-119">Opis</span><span class="sxs-lookup"><span data-stu-id="b3ed4-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b3ed4-120">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="b3ed4-120">\<policyImporters></span></span>](policyimporters.md)|<span data-ttu-id="b3ed4-121">Określa wszystkich importerów zasad kontrolujących Importowanie potwierdzeń niestandardowych zasad dotyczących powiązań.</span><span class="sxs-lookup"><span data-stu-id="b3ed4-121">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3ed4-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b3ed4-122">Remarks</span></span>  
 <span data-ttu-id="b3ed4-123">Importer zasad jest używany do wyszukiwania potwierdzeń niestandardowych zasad dotyczących funkcji powiązania, a także do dołączania niestandardowego elementu powiązania, który implementuje funkcje wymagane przez potwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="b3ed4-123">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3ed4-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3ed4-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="b3ed4-125">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="b3ed4-125">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="b3ed4-126">Klienci</span><span class="sxs-lookup"><span data-stu-id="b3ed4-126">Clients</span></span>](../../../wcf/feature-details/clients.md)
