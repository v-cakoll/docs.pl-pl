---
title: '&lt;Element wsdlImporter&gt;'
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 43c1a50c740cd9c75ee641e4ac4d0fa8ea3ca36b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54144993"
---
# <a name="ltwsdlimportergt"></a><span data-ttu-id="dcb1b-102">&lt;Element wsdlImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="dcb1b-102">&lt;wsdlImporter&gt;</span></span>
<span data-ttu-id="dcb1b-103">Określa wszystkich importerów WSDL, którzy importują metadane Web Services Description Language (WSDL) 1.1 z załącznikami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="dcb1b-103">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="dcb1b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dcb1b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="dcb1b-105">\<Klient ></span><span class="sxs-lookup"><span data-stu-id="dcb1b-105">\<client></span></span>  
<span data-ttu-id="dcb1b-106">\<metadane ></span><span class="sxs-lookup"><span data-stu-id="dcb1b-106">\<metadata></span></span>  
<span data-ttu-id="dcb1b-107">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="dcb1b-107">\<wsdlImporters></span></span>  
<span data-ttu-id="dcb1b-108">\<Element wsdlImporter ></span><span class="sxs-lookup"><span data-stu-id="dcb1b-108">\<wsdlImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcb1b-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="dcb1b-109">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dcb1b-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="dcb1b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dcb1b-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="dcb1b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dcb1b-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="dcb1b-112">Attributes</span></span>  
  
|<span data-ttu-id="dcb1b-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="dcb1b-113">Attribute</span></span>|<span data-ttu-id="dcb1b-114">Opis</span><span class="sxs-lookup"><span data-stu-id="dcb1b-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="dcb1b-115">Typ tego elementu.</span><span class="sxs-lookup"><span data-stu-id="dcb1b-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dcb1b-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="dcb1b-116">Child Elements</span></span>  
 <span data-ttu-id="dcb1b-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="dcb1b-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dcb1b-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="dcb1b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="dcb1b-119">Element</span><span class="sxs-lookup"><span data-stu-id="dcb1b-119">Element</span></span>|<span data-ttu-id="dcb1b-120">Opis</span><span class="sxs-lookup"><span data-stu-id="dcb1b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dcb1b-121">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="dcb1b-121">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="dcb1b-122">Określa wszystkich importerów WSDL, którzy importują metadane Web Services Description Language (WSDL) 1.1 z załącznikami WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="dcb1b-122">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dcb1b-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dcb1b-123">Remarks</span></span>  
 <span data-ttu-id="dcb1b-124">WSDL importer umożliwia importowanie metadanych, a także przekształcać dane tej informacji do różnych klas, które reprezentują kontraktu i informacje o punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="dcb1b-124">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="dcb1b-125">Selektywnie można było zaimportować informacje o kontraktu i punktu końcowego i właściwości, które ujawnić błędy importowania i zaakceptuj dotyczą proces importowania i konwersji informacji o typie.</span><span class="sxs-lookup"><span data-stu-id="dcb1b-125">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="dcb1b-126">Obsługuje ona również importowania informacje o powiązaniu i właściwości, które zapewniają dostęp do dokumentów zasad, dokumenty WSDL, rozszerzenia WSDL i dokumentów schematu XML.</span><span class="sxs-lookup"><span data-stu-id="dcb1b-126">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcb1b-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dcb1b-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [<span data-ttu-id="dcb1b-128">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="dcb1b-128">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="dcb1b-129">Klienci</span><span class="sxs-lookup"><span data-stu-id="dcb1b-129">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
