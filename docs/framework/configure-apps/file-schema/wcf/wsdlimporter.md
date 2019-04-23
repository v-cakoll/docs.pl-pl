---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 1f34486296465b3ea0b5b05bd9492062c85ad8c8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134436"
---
# <a name="wsdlimporter"></a><span data-ttu-id="04bc9-101">\<wsdlImporter></span><span class="sxs-lookup"><span data-stu-id="04bc9-101">\<wsdlImporter></span></span>
<span data-ttu-id="04bc9-102">Określa wszystkich importerów WSDL, którzy importują metadane Web Services Description Language (WSDL) 1.1 z załącznikami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="04bc9-102">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="04bc9-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="04bc9-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="04bc9-104">\<client></span><span class="sxs-lookup"><span data-stu-id="04bc9-104">\<client></span></span>  
<span data-ttu-id="04bc9-105">\<metadata></span><span class="sxs-lookup"><span data-stu-id="04bc9-105">\<metadata></span></span>  
<span data-ttu-id="04bc9-106">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="04bc9-106">\<wsdlImporters></span></span>  
<span data-ttu-id="04bc9-107">\<wsdlImporter></span><span class="sxs-lookup"><span data-stu-id="04bc9-107">\<wsdlImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04bc9-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="04bc9-108">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04bc9-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="04bc9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="04bc9-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="04bc9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04bc9-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="04bc9-111">Attributes</span></span>  
  
|<span data-ttu-id="04bc9-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="04bc9-112">Attribute</span></span>|<span data-ttu-id="04bc9-113">Opis</span><span class="sxs-lookup"><span data-stu-id="04bc9-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="04bc9-114">Typ tego elementu.</span><span class="sxs-lookup"><span data-stu-id="04bc9-114">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04bc9-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="04bc9-115">Child Elements</span></span>  
 <span data-ttu-id="04bc9-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="04bc9-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="04bc9-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="04bc9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="04bc9-118">Element</span><span class="sxs-lookup"><span data-stu-id="04bc9-118">Element</span></span>|<span data-ttu-id="04bc9-119">Opis</span><span class="sxs-lookup"><span data-stu-id="04bc9-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04bc9-120">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="04bc9-120">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="04bc9-121">Określa wszystkich importerów WSDL, którzy importują metadane Web Services Description Language (WSDL) 1.1 z załącznikami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="04bc9-121">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04bc9-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="04bc9-122">Remarks</span></span>  
 <span data-ttu-id="04bc9-123">WSDL importer umożliwia importowanie metadanych, a także przekształcać dane tej informacji do różnych klas, które reprezentują kontraktu i informacje o punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="04bc9-123">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="04bc9-124">Selektywnie można było zaimportować informacje o kontraktu i punktu końcowego i właściwości, które ujawnić błędy importowania i zaakceptuj dotyczą proces importowania i konwersji informacji o typie.</span><span class="sxs-lookup"><span data-stu-id="04bc9-124">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="04bc9-125">Obsługuje ona również importowania informacje o powiązaniu i właściwości, które zapewniają dostęp do dokumentów zasad, dokumenty WSDL, rozszerzenia WSDL i dokumentów schematu XML.</span><span class="sxs-lookup"><span data-stu-id="04bc9-125">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04bc9-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04bc9-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="04bc9-127">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="04bc9-127">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="04bc9-128">Klienci</span><span class="sxs-lookup"><span data-stu-id="04bc9-128">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
