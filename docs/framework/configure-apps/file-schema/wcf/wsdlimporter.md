---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: bd6c8661f94610d932ffee631aee7ad060f04c6b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269318"
---
# <a name="wsdlimporter"></a><span data-ttu-id="405ab-101">\<wsdlImporter></span><span class="sxs-lookup"><span data-stu-id="405ab-101">\<wsdlImporter></span></span>
<span data-ttu-id="405ab-102">Określa wszystkich importerów WSDL, którzy importują metadane Web Services Description Language (WSDL) 1.1 z załącznikami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="405ab-102">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="405ab-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="405ab-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="405ab-104">\<client></span><span class="sxs-lookup"><span data-stu-id="405ab-104">\<client></span></span>  
<span data-ttu-id="405ab-105">\<metadata></span><span class="sxs-lookup"><span data-stu-id="405ab-105">\<metadata></span></span>  
<span data-ttu-id="405ab-106">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="405ab-106">\<wsdlImporters></span></span>  
<span data-ttu-id="405ab-107">\<wsdlImporter></span><span class="sxs-lookup"><span data-stu-id="405ab-107">\<wsdlImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="405ab-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="405ab-108">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="405ab-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="405ab-109">Attributes and Elements</span></span>  
 <span data-ttu-id="405ab-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="405ab-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="405ab-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="405ab-111">Attributes</span></span>  
  
|<span data-ttu-id="405ab-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="405ab-112">Attribute</span></span>|<span data-ttu-id="405ab-113">Opis</span><span class="sxs-lookup"><span data-stu-id="405ab-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="405ab-114">Typ tego elementu.</span><span class="sxs-lookup"><span data-stu-id="405ab-114">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="405ab-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="405ab-115">Child Elements</span></span>  
 <span data-ttu-id="405ab-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="405ab-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="405ab-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="405ab-117">Parent Elements</span></span>  
  
|<span data-ttu-id="405ab-118">Element</span><span class="sxs-lookup"><span data-stu-id="405ab-118">Element</span></span>|<span data-ttu-id="405ab-119">Opis</span><span class="sxs-lookup"><span data-stu-id="405ab-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="405ab-120">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="405ab-120">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="405ab-121">Określa wszystkich importerów WSDL, którzy importują metadane Web Services Description Language (WSDL) 1.1 z załącznikami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="405ab-121">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="405ab-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="405ab-122">Remarks</span></span>  
 <span data-ttu-id="405ab-123">WSDL importer umożliwia importowanie metadanych, a także przekształcać dane tej informacji do różnych klas, które reprezentują kontraktu i informacje o punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="405ab-123">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="405ab-124">Selektywnie można było zaimportować informacje o kontraktu i punktu końcowego i właściwości, które ujawnić błędy importowania i zaakceptuj dotyczą proces importowania i konwersji informacji o typie.</span><span class="sxs-lookup"><span data-stu-id="405ab-124">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="405ab-125">Obsługuje ona również importowania informacje o powiązaniu i właściwości, które zapewniają dostęp do dokumentów zasad, dokumenty WSDL, rozszerzenia WSDL i dokumentów schematu XML.</span><span class="sxs-lookup"><span data-stu-id="405ab-125">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="405ab-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="405ab-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="405ab-127">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="405ab-127">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="405ab-128">Klienci</span><span class="sxs-lookup"><span data-stu-id="405ab-128">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
