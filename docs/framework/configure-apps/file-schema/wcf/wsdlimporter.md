---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 13c9400874f1e02fac3ce0c3010153ad7806288c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915186"
---
# <a name="wsdlimporter"></a><span data-ttu-id="37fdc-101">\<wsdlImporter></span><span class="sxs-lookup"><span data-stu-id="37fdc-101">\<wsdlImporter></span></span>
<span data-ttu-id="37fdc-102">Określa wszystkich importerów WSDL, którzy importują metadane Web Services Description Language (WSDL) 1,1 przy użyciu załączników WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="37fdc-102">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="37fdc-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="37fdc-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="37fdc-104">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="37fdc-104">\<client></span></span>  
<span data-ttu-id="37fdc-105">\<> metadanych</span><span class="sxs-lookup"><span data-stu-id="37fdc-105">\<metadata></span></span>  
<span data-ttu-id="37fdc-106">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="37fdc-106">\<wsdlImporters></span></span>  
<span data-ttu-id="37fdc-107">\<wsdlImporter></span><span class="sxs-lookup"><span data-stu-id="37fdc-107">\<wsdlImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37fdc-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="37fdc-108">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37fdc-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="37fdc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="37fdc-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="37fdc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37fdc-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="37fdc-111">Attributes</span></span>  
  
|<span data-ttu-id="37fdc-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="37fdc-112">Attribute</span></span>|<span data-ttu-id="37fdc-113">Opis</span><span class="sxs-lookup"><span data-stu-id="37fdc-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="37fdc-114">Typ tego elementu.</span><span class="sxs-lookup"><span data-stu-id="37fdc-114">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37fdc-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="37fdc-115">Child Elements</span></span>  
 <span data-ttu-id="37fdc-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="37fdc-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="37fdc-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="37fdc-117">Parent Elements</span></span>  
  
|<span data-ttu-id="37fdc-118">Element</span><span class="sxs-lookup"><span data-stu-id="37fdc-118">Element</span></span>|<span data-ttu-id="37fdc-119">Opis</span><span class="sxs-lookup"><span data-stu-id="37fdc-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37fdc-120">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="37fdc-120">\<wsdlImporters></span></span>](wsdlimporters.md)|<span data-ttu-id="37fdc-121">Określa wszystkich importerów WSDL, którzy importują metadane Web Services Description Language (WSDL) 1,1 przy użyciu załączników WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="37fdc-121">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37fdc-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37fdc-122">Remarks</span></span>  
 <span data-ttu-id="37fdc-123">Importer WSDL jest używany do importowania metadanych, a także konwertowania tych informacji na różne klasy, które reprezentują informacje o kontrakcie i punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="37fdc-123">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="37fdc-124">Umożliwia selektywne importowanie informacji o kontraktach i punktach końcowych oraz właściwości, które uwidaczniają błędy importu i akceptują informacje o typie odpowiednie dla procesu importu i konwersji.</span><span class="sxs-lookup"><span data-stu-id="37fdc-124">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="37fdc-125">Obsługuje ona również importowanie informacji o powiązaniach i właściwości, które zapewniają dostęp do dowolnych dokumentów zasad, dokumentów WSDL, rozszerzeń WSDL i dokumentów schematu XML.</span><span class="sxs-lookup"><span data-stu-id="37fdc-125">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37fdc-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37fdc-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="37fdc-127">Konfiguracja klienta programu WCF</span><span class="sxs-lookup"><span data-stu-id="37fdc-127">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="37fdc-128">Klienci</span><span class="sxs-lookup"><span data-stu-id="37fdc-128">Clients</span></span>](../../../wcf/feature-details/clients.md)
